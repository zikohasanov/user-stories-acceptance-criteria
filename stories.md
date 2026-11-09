# Stories and Acceptance Criteria

| ID | User story | Priority | Outcome / requirement |
|---|---|---|---|
| US-01 | As a customer, I want to browse current items and prices so I can decide what to order. | Must | BR-01 |
| US-02 | As a customer, I want to choose configured options and quantities so my request is specific. | Must | BR-02 |
| US-03 | As a customer, I want to review the amount and pickup terms before submitting so I understand what I am requesting. | Must | BR-02 |
| US-04 | As a customer, I want a reference and honest pending status so I know the request was received without mistaking it for acceptance. | Must | BR-03 |
| US-05 | As a shift lead, I want to accept feasible requests and reject others with a reason so the kitchen controls its commitments. | Must | BR-03, BR-05 |
| US-06 | As kitchen staff, I want to update preparation state so the customer view reflects progress. | Must | BR-06 |
| US-07 | As a customer, I want to check status with a secure verification step so I can avoid calling while keeping order details private. | Must | BR-04 |
| US-08 | As an owner, I want to compare pilot measures to a recorded baseline so I can decide whether to improve the workflow. | Should | BR-08 |

## US-01 — Browse menu

**Given** the restaurant is accepting online orders  
**When** the customer opens the menu  
**Then** published items show current price, options, and availability  
**And** unpublished items are not exposed.

## US-02 — Configure cart

**Given** an item is available and has required options  
**When** the customer selects all required options and a quantity from 1 through 20  
**Then** the cart shows the chosen configuration and calculated line amount.

**Given** a required option is missing or quantity is outside the permitted range  
**When** the customer tries to add the item  
**Then** the item is not added and the specific correction is explained.

## US-03 — Review before submit

**Given** the cart contains valid items  
**When** the customer reaches checkout  
**Then** an itemized amount and configured tax/charge treatment are shown  
**And** the customer can return to edit the cart before submission.

## US-04 — Submit request

**Given** all required details are valid and items remain available  
**When** the customer submits the request  
**Then** one order is created in `AwaitingReview`  
**And** a unique reference is shown  
**And** the confirmation explains that staff acceptance is pending.

**Given** the same submission is retried with the same idempotency key  
**When** the original request has been processed  
**Then** the existing reference is returned and no duplicate is created.

## US-05 — Decide request

**Given** a request is awaiting review  
**When** authorized staff accept it  
**Then** it moves to `Accepted`, records actor and time, and queues a customer update.

**Given** staff reject a request  
**When** no rejection reason is provided  
**Then** the action is blocked until a reason is selected.

## US-06 — Update fulfilment

**Given** an order is accepted  
**When** staff advance it through `Preparing`, `Ready`, and `Collected`  
**Then** each valid transition is recorded and visible to the customer.

**Given** an order is accepted  
**When** staff attempt to mark it collected directly  
**Then** the transition is rejected because intermediate states were skipped.

## US-07 — Check status

**Given** the reference and one-time verification are valid  
**When** the customer requests status  
**Then** the current state and pickup guidance are shown without staff-only notes.

**Given** verification fails or expires  
**When** the customer tries to view status  
**Then** no order details are disclosed and a safe retry or support option is provided.

## Ready and done

**Ready:** outcome and actor are clear; examples cover main and exception paths; dependencies, data, and state changes have an owner; unresolved decisions are listed.  
**Done:** acceptance examples pass; keyboard and screen-reader behavior is reviewed; privacy/security changes are checked; logs exclude secrets; product owner accepts the result; user-facing and support guidance is current.
