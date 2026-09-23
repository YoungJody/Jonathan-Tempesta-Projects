# On The Hitlist

**Full-stack web platform for music producers** · Sole developer · Invite-only preview at [onthehitlist.com](https://onthehitlist.com)

On The Hitlist is a discovery platform for music producers. Members submit records for evaluation and ranking, with subscriptions, merchandise fulfillment, and Discord integration. I designed and built it alone, from the front end through the infrastructure, for a producer community I grew to 500+ members.

## At a glance

| | |
|---|---|
| Code | ~19,000 lines of TypeScript |
| Database | PostgreSQL, 16 tables |
| API | 18 REST routes |
| Infrastructure | AWS |
| Integrations | Stripe, Discord, EasyPost |

## Stack

| Layer | Technologies |
|---|---|
| Front end | React, Next.js, TypeScript, Tailwind CSS |
| Back end | Node.js, REST API |
| Data | PostgreSQL, Drizzle ORM (relations, constraints, indexes, migrations) |
| Auth | AWS Cognito, OAuth 2.0, JWT sessions |
| Infrastructure | AWS EC2, VPC, S3, CloudFront, RDS, IAM, Secrets Manager, SES, Route 53, Certificate Manager |
| Integrations | Stripe (payments, webhooks), Discord API, EasyPost (shipping) |

## Engineering highlights

**Payment fulfillment that can't lose or duplicate an order.** Orders are fulfilled on two independent paths, a Stripe webhook and a post-checkout verification, so a missed webhook never loses a paid order. Every write is idempotent, so the two paths can safely race, and inventory is decremented inside the SQL predicate so simultaneous buyers can't oversell.

**Server-side validation on every route.** The API treats the client as untrusted. For example, shipping cost is recalculated from the carrier's API, so a tampered request can't ship an order for free.

**Security and AWS access.**
- Found and fixed an account-takeover gap: identity tokens stayed valid for up to an hour after account deletion, which could let a deleted user reclaim another user's record. The fix is a tombstone table written only after deletion is confirmed.
- Moved deployment off static access keys to scoped IAM roles, with credentials in AWS Secrets Manager and separate application and admin identities to limit blast radius.
- Organized member files by owner in S3 behind CloudFront, so exporting or deleting one member's data is a single operation.

**Discord role sync.** Discord's endpoint replaces a member's entire role list, so a naive update would strip moderator and subscriber roles. The sync computes each member's full desired role set and applies only the difference, preserving any role outside its allowlist.

**Test tooling.** Developer tooling resets and verifies test state across the database, auth, storage, and payments, with guards that refuse to run against production credentials.

## Background

The community came first. I grew it from zero to 500+ members in three weeks through direct outreach and ran its online beat battles by hand. I prototyped the membership site in Webflow and Memberstack. When it was clear the member load would outgrow no-code tools, I taught myself to program and built the platform from scratch.

## Status

In active development, with an invite-only preview live at [onthehitlist.com](https://onthehitlist.com). The source code is private.

[← Back to portfolio](../README.md)
