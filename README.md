# Contribution 2: Email — Sending emails does not work if the server does not have TLS

**Contribution Number:** 2  
**Student:** Chaoyang Shen  
**Issue:** https://github.com/graphql-hive/console/issues/1561  
**Status:** Phase I In Progress
Why I Chose This Issue section:


## Why I Chose This Issue

This issue asks GraphQL Hive to add an `ignoreTLS` option to its email provider
configuration so that emails can be sent through SMTP servers that don't support
TLS encryption. Right now email delivery silently fails against such servers,
which blocks anyone self-hosting Hive against a legacy or internal mail relay.
I chose it because it's labeled a "good first issue" with a clearly scoped fix
in a single file (`packages/services/emails/src/providers.ts`), making it an
approachable way to learn the codebase while shipping a change that has real
value for self-hosted deployments.

## Understanding the Issue

### Problem Description

GraphQL Hive's email service can't send email through SMTP servers that don't
support TLS. The provider configuration has no way to disable TLS, so when Hive
connects to a non-TLS server the connection negotiation fails and no email is
delivered. The fix requested is to expose an `ignoreTLS` option that gets passed
through to the underlying SMTP transport.

### Expected Behavior

When Hive is configured to use an SMTP server without TLS (for example a legacy
or internal mail relay), setting an `ignoreTLS` flag should let it connect and
send emails successfully.

### Current Behavior

There is no `ignoreTLS` setting. Against a server without TLS, email sending
fails and messages are never delivered.

### Affected Components

- **`packages/services/emails/src/providers.ts`** (around line 85) — the SMTP
  email provider configuration where the TLS-related transport options are set.
---

## Reproduction Process

### Environment Setup

[Notes on setting up your local development environment - challenges you faced, how you solved them]

### Steps to Reproduce

1. [Step 1]
2. [Step 2]
3. [Observed result]

### Reproduction Evidence

- **Commit showing reproduction:** [Link to commit in your fork]
- **Screenshots/logs:** [If applicable]
- **My findings:** [What you discovered during reproduction]

---

## Solution Approach

### Analysis

[Your analysis of the root cause - what's causing the issue?]

### Proposed Solution

[High-level description of your fix approach]

### Implementation Plan

Using UMPIRE framework (adapted):

**Understand:** [Restate the problem]

**Match:** [What similar patterns/solutions exist in the codebase?]

**Plan:** [Step-by-step implementation plan]
1. [Modify file X to do Y]
2. [Add function Z]
3. [Update tests]

**Implement:** [Link to your branch/commits as you work]

**Review:** [Self-review checklist - does it follow the project's contribution guidelines?]

**Evaluate:** [How will you verify it works?]

---

## Testing Strategy

### Unit Tests

- [ ] Test case 1: [Description]
- [ ] Test case 2: [Description]
- [ ] Test case 3: [Description]

### Integration Tests

- [ ] Integration scenario 1
- [ ] Integration scenario 2

### Manual Testing

[What you tested manually and results]

---

## Implementation Notes

### Week [X] Progress

[What you built this week, challenges faced, decisions made]

### Week [Y] Progress

[Continue documenting as you work]

### Code Changes

- **Files modified:** [List]
- **Key commits:** [Links to important commits]
- **Approach decisions:** [Why you chose certain approaches]

---

## Pull Request

**PR Link:** [GitHub PR URL when submitted]

**PR Description:** [Draft or final PR description - much of the content above can be adapted]

**Maintainer Feedback:**
- [Date]: [Summary of feedback received]
- [Date]: [How you addressed it]

**Status:** [Awaiting review / Iterating / Approved / Merged]

---

## Learnings & Reflections

### Technical Skills Gained

[What you learned technically]

### Challenges Overcome

[What was hard and how you solved it]

### What I'd Do Differently Next Time

[Reflection on your process]

---

## Resources Used

- [Link to helpful documentation]
- [Tutorial or Stack Overflow post that helped]
- [GitHub issues or discussions that helped]
