This is CRM for TAVON.

The current year is 2026

When you startup launch /due

## Folder Structure

```
crm/
 └── contacts/
      ├── customers/         # Using, evaluating, or might buy (warm/strong trust)
      ├── customers-cold/    # Cold outreach prospects (cold trust)
      ├── service-customers/ # Gigs outside of our product
      ├── network/           # Keep informed; value unclear yet
      ├── partners/          # Helps build/deliver the product
      ├── investors/         # Angel/VC, funding relation
      ├── talent/            # Possible hire
      ├── influencers/       # Media, community, reputation
      ├── friends-and-family/# Personal connections, low priority
      ├── archive/           # Closed, no further effort expected
      └── inbox/             # Contacts pending classification
 └── activity/               # Interaction history (separate from contacts)
 └── research/               # Research threads and learning topics
```

## Contact Roles

| Role | Folder | Description |
|------|--------|-------------|
| **Customer** | `customers/` | Using, evaluating, or might buy (warm/strong trust) |
| **Customer (Cold)** | `customers-cold/` | Cold outreach prospects (cold trust) |
| **Service-Customer** | `service-customers/` | Gigs outside of our product |
| **Network** | `network/` | Keep informed; value unclear yet |
| **Partner** | `partners/` | Helps build/deliver the product |
| **Investor** | `investors/` | Angel/VC, funding relation |
| **Talent** | `talent/` | Possible hire |
| **Influencer** | `influencers/` | Media, community, reputation |
| **Friends & Family** | `friends-and-family/` | Personal connections, low priority, muted by default |

If their main value changes (e.g., friend becomes investor), **move to a different folder**.

Cold contacts should be moved from `customers-cold/` to `customers/` when trust level increases to warm or strong.

## Status Values

| Status | Meaning |
|--------|---------|
| `new` | Never contacted / just added |
| `waiting` | You sent something, waiting for them |
| `replied` | They responded, your turn |
| `interested` | Showed interest (interview, demo, call) |
| `evaluating` | Actively considering piloting/buying |
| `piloting` | Actively testing the product |
| `active` | Ongoing collaboration |
| `paused` | Inactive for now, future possible |
| `archived` | Closed, no further effort expected |

**Ball in court rule:**
- `waiting` → their turn
- `replied` → your turn

## Customer Funnel

### Funnel Stages Overview

```
COLD OUTREACH → ENGAGEMENT → INTEREST → EVALUATION → ACTIVE
```

### Stage Details

| Stage | Folder | Status | Trust | Typical Priority | Description |
|-------|--------|--------|-------|-----------------|-------------|
| **1. Cold Prospect** | customers-cold/ | new | cold | B | Just added, never contacted |
| **2. Initial Outreach** | customers-cold/ | waiting | cold | B | Outreach sent, waiting for response |
| **3. First Response** | customers/ | waiting/replied | warm | B | They responded, conversation started |
| **4. Interest Shown** | customers/ | interested | warm | A/B | Scheduled demo/call, showed interest |
| **5. Active Evaluation** | customers/ | evaluating | warm | A | Considering purchase/pilot |
| **6. Pilot Testing** | customers/ | piloting | warm/strong | A | Actively testing product |
| **7. Active Customer** | customers/ | active | strong | A | Ongoing collaboration |

### Transition Rules

**Cold → Warm (move from customers-cold/ to customers/)**:
- Trigger: Contact responds positively to outreach
- Update: Change trust from `cold` to `warm`
- Update: Change status from `waiting` to `replied` or `interested`
- Update: Consider upgrading priority to `A` if strategic

**Warm → Strong**:
- Trigger: Contact provides referrals, gives feedback, or becomes pilot user
- Update: Change trust from `warm` to `strong`
- Typical status: `piloting`, `active`

**Status Progression in Cold Funnel**:
```
new → waiting → [no response: paused/archived]
              → [response: move to customers/]
```

**Status Progression in Warm Funnel**:
```
replied → interested → evaluating → piloting → active
                    ↓
                  paused (can re-engage later)
```

### Funnel Metrics

Track these conversion points:
- Cold → Warm: Response rate on initial outreach
- Warm → Interested: Demo/call booking rate
- Interested → Piloting: Pilot conversion rate
- Piloting → Active: Customer activation rate

## Trust Levels

| Trust | Meaning |
|-------|---------|
| `cold` | No connection |
| `warm` | Shared context / some goodwill |
| `strong` | Supports you, intros, feedback |

## Priority Levels

| Priority | Meaning |
|----------|---------|
| `A` | Strategic leverage, high impact |
| `B` | Relevant but not critical |
| `C` | Optional / opportunistic |

## Metadata Structure

Every contact file uses this YAML frontmatter:

```yaml
role_primary: customer|service-customer|network|partner|investor|talent|influencer
roles_secondary: []  # optional tags like [friend, advisor]

status: new|waiting|replied|interested|evaluating|piloting|active|paused|archived
trust: cold|warm|strong
priority: A|B|C

last_contact: YYYY-MM-DD
next_action: "description YYYY-MM-DD"

topics: []  # research topics, e.g., [enterprise-integrations, ai-strategy]

muted: true  # exclude from follow-up reports without archiving - false is default no need for tag.
needs_review: true  # flag for incomplete data - false is default no need for tag.
newsletters: []  # newsletter subscriptions, e.g., [product, company] - empty/omit if none
```

## Activity Tracking

Interactions are stored in the `/crm/activity/` folder as separate files:

```
crm/activity/
  ├── 2025-10-31-angela-schneller-email-outreach.md
  ├── 2025-11-10-angela-schneller-email-followup.md
  └── ...
```

Each activity file has:
```yaml
contact: contact-slug
date: YYYY-MM-DD
type: email|call|meeting|linkedin
direction: outbound|inbound
template: template-name  # if applicable
```

## Research & Topics

Track research topics and learnings in the `crm/research/` folder. Each research file can:
- Document key questions and learnings
- Link to relevant contacts using `[[contact-name]]` syntax
- Reference related activities
- Organize resources and insights

Tag contacts with research topics using the `topics` field in their frontmatter:
```yaml
topics: [enterprise-integrations, ai-strategy]
```

This allows you to:
- Group contacts by research interest
- Track conversations related to specific topics
- Build knowledge across multiple interactions

## Quick Capture

Use the inbox folder when you need to quickly add a contact or idea without filling out the full template:
- Create a new file with any name, or
- Add a line to `crm/inbox/QUICK-ADD.md`

Process inbox items periodically by moving them to proper contact folders.

## Slash Commands

- `/due` - Show overdue, due today, and upcoming next_actions for the week
- `/report` - Activity report: today, this week, last week with outreach/response stats
- `/followup` - Contacts needing follow-up, grouped by time since last contact
- `/piloting` - Contacts with status `evaluating` or `piloting`

## Email Templates

Track all email templates used for outreach in the `crm/email-templates/` folder.
