<!-- Copy this content when creating a new GitHub issue -->

## Summary

Investigation into triggering the `claude.yml` workflow when users react with 👍 on specific PR comments.

## Current Limitation

**GitHub Actions does not support emoji reaction events as workflow triggers.** While GitHub's webhook API includes reaction events (`issue_comment_reaction`, `pull_request_review_comment_reaction`), these are not exposed as available workflow triggers.

### What We Currently Have

The `.github/workflows/claude.yml` workflow currently triggers on:

- `issue_comment` (when comments are created)
- `pull_request_review_comment` (when review comments are created)
- `issues` (when issues are opened/assigned)
- `pull_request_review` (when reviews are submitted)

### What We Cannot Do

- ❌ Trigger workflows when emoji reactions are added to comments
- ❌ Trigger workflows when emoji reactions are added to PR review comments
- ❌ Use native GitHub Actions events for any reaction-based triggers

## Research Findings

This is a known limitation that has been requested by the community since at least October 2022:

- [GitHub Community Discussion #37901](https://github.com/orgs/community/discussions/37901)
- Multiple users have requested this feature for approval workflows
- No official support or timeline has been provided by GitHub

## Potential Workarounds

### Option 1: Comment-Based Triggers (Recommended)

Instead of emoji reactions, use specific comment text to trigger workflows:

**Implementation:**

- Users comment with `/implement` or `👍 implement this` on PR comments
- Workflow triggers on `issue_comment.created` or `pull_request_review_comment.created`
- Parse comment body to detect trigger phrases
- Optionally add a reaction emoji to acknowledge detection

**Pros:**

- Works with existing GitHub Actions infrastructure
- No additional services required
- Can include additional context in the comment
- Can be implemented immediately

**Cons:**

- Slightly more friction than a simple emoji reaction
- Requires documentation for users

### Option 2: Scheduled Polling

Set up a scheduled workflow to periodically check for new reactions via GitHub API:

**Pros:**

- Can detect actual emoji reactions

**Cons:**

- Delay between reaction and execution
- API rate limits
- Complex implementation
- Resource inefficient

### Option 3: External Webhook Server

Set up an external service to receive GitHub webhooks for reaction events and trigger workflows:

**Pros:**

- Real-time reaction detection

**Cons:**

- Requires infrastructure and maintenance
- Security considerations
- Additional complexity
- Cost

## Recommendation

Implement **Option 1: Comment-Based Triggers** as the most practical solution:

1. Document that users should comment with specific trigger phrases
2. Use existing `issue_comment` and `pull_request_review_comment` triggers
3. Optionally add reaction acknowledgment to improve UX

Example workflow modification:

```yaml
on:
  issue_comment:
    types: [created]
  pull_request_review_comment:
    types: [created]
```

The workflow job can then check if the comment contains trigger phrases like:

- `/claude implement`
- `/implement`
- `@claude implement this`

## Next Steps

- [ ] Decide on preferred trigger phrase(s)
- [ ] Document the trigger mechanism for users
- [ ] Optionally implement comment parsing logic
- [ ] Add reaction acknowledgment to improve UX

## References

- [Emoji Event Trigger for GitHub Actions Discussion](https://github.com/orgs/community/discussions/37901)
- [Pull Request Comment Trigger Action](https://github.com/marketplace/actions/pull-request-comment-trigger)
- [Comment Reaction Action](https://github.com/marketplace/actions/comment-reaction)
