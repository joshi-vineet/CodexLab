# Product Concept v0.2 — My Payment Reminders (Synchrony)

**Concept ID:** synchrony-payment-reminders  
**Status:** Draft — submitted for product manager review (not approved)  
**Version:** 0.2  
**Date:** 2026-10-25  
**Target users:** Eligible U.S. Synchrony credit cardholders  
**Decision requested:** Validate scope, dependencies, and pilot authorization. No implementation approval is implied.

## Problem and opportunity
Cardholders differ in how far ahead of a credit-card payment due date they want to be reminded, and in how they prefer to receive reminders. Generic reminder schedules may be inconvenient or redundant after a payment is made. Synchrony already publicly documents online account alerts and payment-management features, so the proposal is an enhancement, not a new standalone notification platform. The extent of existing timing customization and payment-aware suppression needs validation.

## Customer outcome
Give eligible cardholders easy, understandable control over optional payment-reminder timing and authorized communication channels, without changing their contractual due date or required notices. Reduce unnecessary reminders after a qualifying payment is confirmed.

## Public market context (reviewed 2026-10-25)
- Synchrony public account help: https://www.synchrony.com/help/faqs
- Synchrony app overview: https://www.synchrony.com/mobile-app
- Synchrony historical digital feature discussion: https://www.synchrony.com/contenthub/newsroom/2016-synchrony-financial-sixth-annual-digital-study.html
- Benchmark hypothesis: major U.S. card issuers provide various payment alerts and channel preferences. Specific feature parity, arbitrary delivery-hour scheduling, and suppression behavior should be validated through current product walkthroughs.

**Evidence limitation:** Public materials do not establish current capabilities for every Synchrony card program, app version, or cardholder. No internal or confidential documentation is included here.

## Options
| Option | Scope | Benefits | Tradeoffs |
|---|---|---|---|
| A — Configurable lead times | Offer 7/3/1-day offsets using existing notification channels | Limited changes, simpler pilot | May duplicate existing alert controls |
| B — Personalized reminder scheduling **(recommended)** | Multiple offsets; available email/SMS selection; edit preferences; suppress obsolete reminders when minimum payment obligation is confirmed satisfied | Better usefulness and relevance; testable effect | Depends on payment-state integration and dispatch rules |
| C — Intelligent engagement | Behavior-based suggestions, AutoPay coordination, cross-account experience | Potential future differentiation | Greater privacy, compliance, operational and engineering complexity |

## Recommended MVP: Phase 1 of Option B
1. Present existing optional reminder preferences in an established authenticated account-management flow.
2. Offer 7, 3, and 1 days before due date as selectable reminder intervals, subject to validation of existing options.
3. Allow eligible cardholders to select available authorized email and/or SMS delivery.
4. Allow preferences to be updated or optional reminders disabled; show confirmation and next expected reminder.
5. Evaluate current-cycle payment state before each scheduled dispatch; suppress optional reminders when a qualifying minimum payment obligation is confirmed satisfied.
6. Maintain an auditable record of preference changes, eligibility, suppression decisions and delivery outcomes.

**MVP exclusions:** AI personalization, changing payment due dates, new notification vendors, push alerts unless current capability is verified, preferred exact delivery hours (follow-on if infrastructure permits), new payment methods, and portfolio-wide AutoPay orchestration.

**Policy separation:** Optional reminders do not override mandatory contractual, legal, collections, fraud or servicing notices. Eligibility, messaging consent, contact windows, and payment-status handling require legal/compliance approval.

## Requirements
| ID | Requirement | Priority |
|---|---|---|
| REQ-001 | Show existing optional payment-reminder preferences | Must |
| REQ-002 | Configure one or more eligible pre-due-date intervals | Must |
| REQ-003 | Select authorized delivery channels | Must |
| REQ-004 | Modify or disable optional reminders | Must |
| REQ-005 | Check current-cycle qualifying payment status before dispatch | Must |
| REQ-006 | Prevent obsolete or duplicate optional reminders | Must |
| REQ-007 | Record preference and dispatch decisions for audit and support | Must |
| REQ-008 | Offer a preferred delivery hour, if feasible | Should / later |
| REQ-009 | AutoPay-aware reminder coordination | Later |

## Pilot and proposed success metrics
Run a limited, eligible-portfolio pilot with a comparable control group. Baselines are **not yet known**. The following are **proposed and unvalidated** thresholds:
- Preference setup completion: >=70% of users who start.
- Eligible notification dispatch success: >=98%.
- Reminders sent after confirmed qualifying payment: <0.5%.
- On-time minimum-payment rate: positive experimental lift vs. control (minimum meaningful lift to be set after baseline study).
- Notification-related complaints: no adverse change vs. control.

Track opt-outs, bounce/failure rates, late-payment outcomes, AutoPay enrollment, and customer segments; avoid attributing causality without experimentation.

## Risks and dependencies
- **Duplication risk:** Current authenticated account experience may already support some suggested controls.
- **Payment-state ambiguity:** Scheduled, submitted, pending, posted, reversed, and returned payments must be distinguished. Define qualifying-satisfaction semantics with Payments and Risk.
- **Channel permissions:** Verified contact details, SMS permission, opt-outs, time zones, and permissible sending hours.
- **Program variability:** Capabilities may differ by card partner and portfolio.
- **Systems:** Access to preference configuration, cycle due dates, payment status, scheduling/dispatch, and delivery audit events.
- **Trust:** Avoid implying that a reminder replaces account statements or responsibility to pay.

## Discovery gates before implementation
1. Perform current authenticated walkthrough on representative Synchrony card programs.
2. Inventory existing configurable timing and channel capabilities; identify overlaps.
3. Confirm payment event sources, timing/latency and minimum-payment satisfaction semantics.
4. Obtain Servicing, Payments, Compliance, Privacy, Security and Partner-Program review.
5. Establish baseline metrics, pilot sample design and a rollback plan.

## Product manager review questions
- Is the incremental value compelling beyond current alert controls?
- Which eligible portfolio is suitable for the first pilot?
- Should payment-aware suppression be in MVP, given data latency and exceptions?
- Is optional preferred delivery-hour scheduling valuable enough for phase 1?
- Are success metrics and safeguards adequate to proceed to discovery/PRD?

## Version history
- **v0.1:** Generic configurable credit-card payment reminders.
- **v0.2 (2026-10-25):** Synchrony-specific scope; existing alert capability acknowledged; option B recommended; MVP, exclusions, hypotheses, safeguards and validation gates defined.

## Publication and source boundary
This is a public-safe concept draft based on product hypotheses and cited publicly available resources. It contains no internal SharePoint content, internal file references, private architecture claims, or confidential customer information. Manager approval must be recorded against the saved version through an authorized review action.
