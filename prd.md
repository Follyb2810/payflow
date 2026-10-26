# PRODUCT REQUIREMENTS DOCUMENT (PRD)

# PayFlow Africa
**Product:** B2B Payment Collection, Reconciliation and Receivables Management Platform

**Document version:** 1.0

**Status:** Draft — Pending Customer Validation

**Initial market:** Nigeria

**Initial target customers:** Distributors and wholesalers

**Initial payment provider:** OPay, subject to merchant eligibility and API access

**Proposed technology stack:** Next.js, TypeScript, .NET 8 Web API, PostgreSQL

---

## 1. Executive Summary

PayFlow Africa is a business-to-business financial operations platform designed to help African businesses collect payments, reconcile transactions against invoices, manage customer debts, and understand their cash position.

Many businesses selling goods on a daily basis receive payments through multiple channels. Identifying customers, matching payments to invoices, tracking partial payments, following up on outstanding balances, and producing financial reports can require substantial manual work.

PayFlow Africa will provide a centralized platform that connects customers, invoices, payment transactions, and financial records.

The first version will focus on invoice management, OPay checkout integration, secure payment verification, automatic invoice matching, outstanding balance tracking, and collection reporting.

The long-term vision is to become a trusted financial operations platform for businesses across Africa.

### Vision

To become the financial operations platform that African businesses rely on to collect, reconcile, and manage money efficiently.

### Mission

To eliminate unnecessary manual work in business payment operations and give businesses reliable visibility into their receivables and collections.

### Business ambition

Build a scalable, recurring-revenue software company with the potential to achieve a $100 million valuation or, over time, $100 million in annual revenue.

These are long-term ambitions, not forecasts or guaranteed outcomes.

---

## 2. Problem Statement

### 2.1 The primary problem

Distributors and wholesalers struggle to connect incoming payments to the invoices and customers those payments belong to.

This creates operational inefficiencies, inaccurate outstanding balances, delayed collections, and poor visibility into the company's financial position.

### 2.2 Specific problems

**Problem 1: Manual payment identification**

Finance teams inspect bank alerts, transaction records, spreadsheets, and customer messages to identify who made a payment.

**Problem 2: Manual invoice reconciliation**

Staff compare incoming payments against invoices and manually update records. This creates opportunities for missed payments, duplicate entries, and incorrect allocations.

**Problem 3: Poor outstanding balance management**

Customers may make partial payments, pay multiple invoices at once, or pay less than expected. Businesses struggle to maintain an accurate view of what each customer still owes.

**Problem 4: Delayed debt collection**

Businesses may discover overdue invoices late because they lack centralized reminders and receivables reporting.

**Problem 5: Limited financial visibility**

Business owners cannot easily determine total collections, outstanding receivables, unmatched payments, overdue invoices, and collection trends from one reliable dashboard.

**Problem 6: Disconnected business systems**

Sales, inventory, invoices, bank records, and accounting data may be stored in different applications or spreadsheets.

### 2.3 Customer problem hypothesis

We believe these problems are sufficiently costly and frequent that distributors will pay for a platform that reduces manual reconciliation and improves collections.

This hypothesis must be validated through customer interviews, workflow observation, and pilot results before major investment in the full product.

---

## 3. Target Market and User Personas

### 3.1 Initial target market

The initial market is Nigerian distributors and wholesalers that:

- Serve many retail customers.
- Issue invoices regularly.
- Accept bank transfers and electronic payments.
- Handle partial payments or customer credit.
- Employ staff to manage finance and collections.
- Use spreadsheets or disconnected business applications for reconciliation.

We should initially prioritize businesses with recurring transaction volumes and an identifiable finance or accounts receivable process.

### 3.2 Primary personas

**Persona A: Business owner**

Goals:
- Understand how much the business has collected.
- Know how much customers owe.
- Reduce financial leakage and administrative costs.
- Monitor business performance without reviewing individual transactions.

Pain points:
- Reports arrive late.
- Outstanding balances are difficult to verify.
- The owner depends heavily on individual staff members for financial information.

**Persona B: Accountant or finance officer**

Goals:
- Match incoming payments to invoices.
- Maintain accurate customer balances.
- Investigate discrepancies.
- Produce reliable collection reports.

Pain points:
- Repetitive manual reconciliation.
- Unidentified bank transfers.
- Duplicate or inconsistent records.
- Time-consuming month-end reporting.

**Persona C: Sales representative**

Goals:
- Know whether customers have paid.
- Check outstanding balances before processing new orders.
- Access customer invoice history.

Pain points:
- Delayed payment confirmations.
- Difficulty determining whether a customer has settled an invoice.
- Repeated calls to the finance team.

**Persona D: Retail customer**

Goals:
- Receive invoices.
- Pay outstanding balances conveniently.
- View payment history.
- Obtain confirmation of successful payments.

Pain points:
- Unclear payment references.
- Difficulty confirming partial payments.
- Disputes about remaining balances.

---

## 4. Product Objectives

The first release must accomplish the following:

1. Centralize customers, invoices, and payment records.
2. Allow businesses to collect eligible payments through OPay checkout.
3. Verify payments securely on the backend.
4. Automatically match verified payments to invoices when the matching rules are unambiguous.
5. Track partial payments and remaining balances.
6. Identify unmatched transactions and discrepancies.
7. Give owners and finance teams accurate collection and receivables reports.
8. Provide a secure, auditable record of payment-related actions.

### 4.1 Non-goals for the first release

The initial version will not attempt to:

- Become a bank or hold customer funds.
- Operate an independent payment processing network.
- Provide lending or credit underwriting.
- Replace a complete accounting or ERP system.
- Guarantee automated reconciliation for every bank or payment provider.
- Launch across every African country simultaneously.
- Support complex inventory, procurement, payroll, or tax management.
- Assume recurring automatic billing is available through OPay without verification.

These features may be considered later if customer demand, regulatory requirements, and commercial viability support them.

---

## 5. Product Scope

### 5.1 Business registration and onboarding

The platform must allow a business to register and establish its workspace.

Requirements:

- Register a business account.
- Capture business name, contact details, and relevant business information.
- Support email verification and secure authentication.
- Allow the business owner to invite staff.
- Configure business settings, including currency and timezone.
- Record onboarding and verification status.
- Require any applicable merchant verification before enabling live payment collection.

Business verification and OPay merchant approval are separate processes and must be represented accurately.

### 5.2 Customer management

Businesses must be able to manage their retail customers.

Requirements:

- Create and edit customer profiles.
- Store customer names, contact details, and unique customer references.
- View invoices associated with a customer.
- View payments allocated to the customer.
- Calculate outstanding balances from invoice and payment records.
- Search and filter customers.
- Import customer data from CSV files.
- Prevent accidental creation of duplicate customers where possible.

### 5.3 Invoice management

The platform must support the creation and tracking of customer invoices.

Requirements:

- Create an invoice for a customer.
- Generate a unique invoice number.
- Add line items, quantities, unit prices, and applicable discounts or taxes where configured.
- Calculate the invoice total.
- Set an issue date and due date.
- Set the invoice status.
- Generate a customer-facing invoice view.
- Generate a downloadable invoice document.
- Send invoices through supported sharing channels.
- Create payment links associated with invoices.
- Support full and partial payments.
- Display the outstanding balance.
- Maintain an invoice history and audit trail.

Initial invoice statuses:

- Draft
- Issued
- Partially Paid
- Paid
- Overdue
- Cancelled

An invoice must not be marked as paid merely because a payment link was opened or a customer claimed to have transferred money.

### 5.4 OPay payment integration

OPay will be the first supported payment provider, subject to merchant onboarding, applicable commercial terms, and confirmation of the available integration capabilities.

Requirements:

- Create a unique internal payment record.
- Generate a unique payment reference.
- Associate the payment with the business, customer, and invoice where applicable.
- Create a payment request using the documented OPay API.
- Redirect the customer to the appropriate checkout experience.
- Record the checkout initiation result.
- Receive payment notifications at a secured backend endpoint.
- Validate the notification according to OPay's documented security requirements.
- Query the transaction status when required.
- Verify the expected amount, currency, reference, and transaction identity.
- Update the payment status only after appropriate verification.
- Prevent duplicate processing of repeated notifications.
- Support transaction history and payment-status queries.
- Record failed, pending, and successful payment attempts.

Payment credentials must be stored securely on the backend and must never be exposed to the browser.

### 5.5 Payment reconciliation engine

This is the core product capability.

The reconciliation engine connects verified payment transactions to the invoices they settle.

Requirements:

- Match transactions using reliable identifiers, including payment references.
- Match verified OPay payments to their associated invoices.
- Support partial payments.
- Support one customer payment being allocated across multiple invoices when the payment evidence and allocation rules permit it.
- Support multiple payments against one invoice.
- Identify duplicate transactions.
- Identify payments that cannot be matched automatically.
- Identify overpayments and underpayments.
- Allow authorized staff to investigate and resolve exceptions.
- Record the user, timestamp, reason, and relevant before-and-after values for manual allocations.
- Recalculate outstanding balances consistently.
- Preserve the underlying transaction history.

The system must never silently discard an unmatched payment or automatically assign money to an invoice based solely on an uncertain customer-name match.

**Important limitation:** The first release can automatically reconcile transactions created through our OPay integration. Reconciliation of direct bank transfers outside that integration requires a supported bank-data connection, statement import, or another reliable source of transaction information.

### 5.6 Accounts receivable management

The platform must help businesses understand outstanding customer debts.

Requirements:

- Display total outstanding receivables.
- Display overdue invoices.
- Group receivables by customer.
- Show invoice due dates.
- Display payment history.
- Calculate remaining invoice balances.
- Provide configurable overdue reminders.
- Record reminder delivery status when supported.
- Allow staff to record collection notes.
- Provide an aging report.

Proposed aging categories:

- Not yet due
- 1–30 days overdue
- 31–60 days overdue
- 61–90 days overdue
- More than 90 days overdue

Aging must be calculated from invoice due dates and outstanding balances.

### 5.7 Dashboard and reporting

The dashboard must provide a clear summary of business collections.

Key metrics:

- Total payments received in a selected period.
- Number and value of successful transactions.
- Outstanding receivables.
- Overdue invoice value.
- Unmatched payment value.
- Partially paid invoices.
- Failed and pending payments.
- Collection trends over time.
- Customers with the largest outstanding balances.

Requirements:

- Filter by date range.
- Filter by customer.
- Filter by payment status.
- Filter by invoice status.
- Export permitted reports to CSV.
- Apply consistent definitions to all financial metrics.
- Distinguish verified collections from pending or failed transactions.

The dashboard must not describe invoice creation, checkout initiation, or payment attempts as money collected.

### 5.8 User roles and permissions

The platform must support role-based access control.

Initial roles:

**Business Owner**
- Manage business settings.
- Manage users and roles.
- View all financial reports.
- Manage invoices, payments, and reconciliation.
- Access audit logs.

**Finance Administrator**
- Manage invoices and payment records.
- Review reconciliation exceptions.
- Allocate verified payments.
- Generate financial reports.

**Sales Representative**
- View permitted customers and invoices.
- Create invoices where authorized.
- View payment status and customer balances.
- Cannot modify verified payment records or financial audit logs.

**Read-only User**
- View authorized information.
- Cannot create, edit, allocate, or reverse financial records.

**Platform Administrator**
- Manage platform-level configuration and support operations.
- Access sensitive customer information only where explicitly authorized and audited.
- Cannot silently alter business financial records.

Every business must be isolated from other businesses' data.

---

## 6. Core User Journeys

### Journey A: Create and pay an invoice

1. The business owner or finance officer signs in.
2. The user creates or selects a customer.
3. The user creates an invoice for ₦500,000.
4. The system assigns an invoice number and due date.
5. The user issues the invoice.
6. The customer receives the invoice and payment link.
7. The customer opens the link and completes payment through OPay.
8. The backend verifies the transaction.
9. The payment is allocated to the invoice.
10. The invoice balance is updated.
11. The customer and business can see the updated payment status.
12. The business can download the invoice and payment receipt where applicable.

**Expected result:** The business has an auditable record of the invoice and its verified payment.

### Journey B: Customer makes a partial payment

1. A customer owes ₦500,000.
2. The customer pays ₦200,000.
3. The backend verifies the payment.
4. The reconciliation engine allocates ₦200,000.
5. The invoice is marked Partially Paid.
6. The outstanding balance becomes ₦300,000.
7. The remaining balance appears in the customer account.
8. A reminder can be sent when the configured due-date conditions are met.

**Expected result:** The business maintains an accurate outstanding balance without manually recalculating the invoice.

### Journey C: Payment cannot be matched

1. The system receives a transaction that cannot be confidently associated with an invoice.
2. The transaction is recorded as unmatched.
3. The finance team sees it in an exception queue.
4. An authorized user investigates the transaction.
5. The user identifies the correct invoice or determines that additional information is required.
6. If appropriate, the user allocates the payment and records the reason.
7. The system recalculates the relevant invoice balance.
8. The audit log records the allocation.

**Expected result:** Uncertain transactions remain visible until they are resolved.

### Journey D: Payment notification arrives twice

1. OPay sends a notification for a transaction.
2. The backend verifies the transaction and processes it.
3. A repeated notification arrives.
4. The backend recognizes the already-processed transaction.
5. No duplicate payment or invoice allocation is created.
6. The duplicate event is logged where appropriate.

**Expected result:** Repeated notifications do not result in double-counted collections.

---

## 7. Functional Requirements and Acceptance Criteria

| ID | Requirement | Acceptance criteria |
|---|---|---|
| FR-01 | Business onboarding | An authorized owner can create and access a business workspace. |
| FR-02 | Customer management | Users can create, search, and view customers within their authorized business. |
| FR-03 | Invoice creation | A valid invoice receives a unique number and a correctly calculated total. |
| FR-04 | Payment initiation | A valid payment request creates an internal payment record and a provider checkout request. |
| FR-05 | Payment verification | An invoice is not marked paid until the required backend verification succeeds. |
| FR-06 | Reconciliation | A verified, identifiable payment is allocated to the correct invoice. |
| FR-07 | Partial payment | The outstanding balance equals the invoice total less valid allocations and applicable adjustments. |
| FR-08 | Idempotency | Reprocessing the same successful payment notification does not duplicate financial records. |
| FR-09 | Exception handling | Unmatched or ambiguous payments appear in a review queue. |
| FR-10 | Receivables reporting | Users can view outstanding and overdue invoices using consistent calculations. |
| FR-11 | Auditability | Sensitive financial changes record the actor, time, action, and relevant details. |
| FR-12 | Tenant isolation | Users cannot access another business's records without explicit platform-level authorization. |
| FR-13 | Export | Authorized users can export permitted reports for a selected period. |
| FR-14 | Payment failure | Failed or pending payments are not incorrectly counted as successful collections. |

---

## 8. Non-Functional Requirements

### Security

- Use HTTPS for all production communication.
- Secure authentication and enforce server-side authorization.
- Store provider credentials in an appropriate secret-management system.
- Validate payment callbacks using the provider's documented signature or verification mechanism.
- Never trust client-submitted amounts or payment statuses.
- Apply tenant-level data isolation to every relevant query.
- Record sensitive administrative and financial operations in audit logs.
- Apply rate limiting and appropriate input validation.
- Protect personally identifiable and financial information.

### Reliability

- Process payment notifications idempotently.
- Handle retries and temporary provider outages safely.
- Avoid inconsistent invoice balances during concurrent payment processing.
- Use database transactions where appropriate.
- Preserve sufficient transaction history for investigations.
- Provide safe recovery mechanisms for failed background jobs.

### Performance

Initial targets, to be validated through load testing:

- Typical dashboard and invoice queries should complete within two seconds under the agreed pilot workload.
- The application should remain responsive during ordinary payment-processing traffic.
- Payment notifications should be acknowledged promptly according to the provider's callback requirements.
- Slow or unreliable external payment calls should not block unrelated application operations.

### Scalability

- Use a modular monolith initially.
- Separate payment-provider logic from invoice and reconciliation business rules.
- Support background processing for reminders, reports, and retryable work.
- Design database indexes around common business and financial queries.
- Monitor transaction volume, database performance, job failures, and provider error rates.

### Availability and recovery

- Establish monitored production environments.
- Back up the database regularly.
- Test restoration procedures.
- Define recovery objectives before onboarding customers with critical financial operations.

---

## 9. Proposed Technical Architecture

### Frontend

- Next.js App Router
- TypeScript
- Tailwind CSS
- shadcn/ui
- TanStack Query
- Zustand where client-side state management is necessary
- Form validation using the project's chosen validation library

### Backend

- .NET 8 Web API
- Entity Framework Core
- PostgreSQL
- ASP.NET Core Identity or the established authentication implementation
- Hangfire for background jobs where appropriate
- Structured logging and centralized exception handling

### Proposed backend modules

```text
Features/
├── Businesses/
├── Users/
├── Customers/
├── Invoices/
├── Payments/
│   ├── CreatePayment/
│   ├── VerifyPayment/
│   ├── PaymentCallback/
│   ├── GetPaymentStatus/
│   └── Refunds/
├── Reconciliation/
├── Receivables/
├── Notifications/
├── Reports/
└── AuditLogs/

Infrastructure/
├── Persistence/
├── PaymentProviders/
│   └── OPay/
├── BackgroundJobs/
├── Security/
└── Observability/
```

These are proposed module boundaries. They should be adjusted to match the existing repository conventions if implementation begins in the current codebase.

### Payment-provider abstraction

The application should use an internal payment-provider interface so invoice and reconciliation logic do not depend directly on OPay-specific response models.

Potential operations include:

- Create payment request.
- Query payment status.
- Verify provider notification.
- Request refund where supported.
- Retrieve provider transaction information where available.

An OPay adapter implements the supported operations. Other providers can be added later without rewriting the invoice domain.

The abstraction must not pretend that every provider supports identical features. Unsupported operations must be represented explicitly.

---

## 10. Proposed Database Model

### Business

Represents a registered company.

Potential fields:

- Id
- Name
- BusinessRegistrationNumber, where applicable
- Email
- PhoneNumber
- DefaultCurrency
- TimeZone
- Status
- CreatedAt
- UpdatedAt

### BusinessUser

Associates a user with a business.

Potential fields:

- Id
- BusinessId
- UserId
- Role
- Status
- CreatedAt

This supports multiple employees within a business and establishes the basis for tenant-level authorization.

### Customer

Represents a retailer or other customer.

Potential fields:

- Id
- BusinessId
- CustomerNumber
- Name
- Email
- PhoneNumber
- Status
- CreatedAt
- UpdatedAt

### Invoice

Represents a request for payment.

Potential fields:

- Id
- BusinessId
- CustomerId
- InvoiceNumber
- IssueDate
- DueDate
- Currency
- Subtotal
- TaxAmount
- DiscountAmount
- TotalAmount
- Status
- CreatedAt
- UpdatedAt

Invoice line items should be stored separately.

### InvoiceLine

Potential fields:

- Id
- InvoiceId
- Description
- Quantity
- UnitPrice
- TaxAmount
- LineTotal

### Payment

Represents an internal payment transaction or payment attempt.

Potential fields:

- Id
- BusinessId
- CustomerId
- InvoiceId, nullable where the payment has not yet been allocated
- Provider
- ProviderTransactionReference
- InternalPaymentReference
- Amount
- Currency
- Status
- InitiatedAt
- VerifiedAt
- CreatedAt
- UpdatedAt

Provider transaction references should be uniquely constrained within the appropriate provider and merchant scope.

### PaymentAllocation

Connects a verified payment to one or more invoices.

Potential fields:

- Id
- BusinessId
- PaymentId
- InvoiceId
- AllocatedAmount
- AllocatedAt
- AllocatedByUserId
- AllocationReason

This structure supports partial payments and payments covering multiple invoices.

### PaymentEvent

Stores relevant provider events and processing history.

Potential fields:

- Id
- PaymentId
- ProviderEventReference
- EventType
- ReceivedAt
- ProcessedAt
- ProcessingStatus

Sensitive callback data must be minimized and protected. Duplicate event handling must be designed around the provider's actual event identifiers and transaction semantics.

### AuditLog

Records sensitive business operations.

Potential fields:

- Id
- BusinessId
- UserId
- Action
- EntityType
- EntityId
- Timestamp
- Details

### Important financial invariant

The invoice outstanding balance must be calculated from the invoice total, valid adjustments, and verified payment allocations. Payment attempts and pending transactions must never reduce the outstanding balance.

Payment reversals and refunds must be recorded explicitly and handled according to defined accounting rules rather than silently deleting successful payment records.

---

## 11. API Requirements

Illustrative REST endpoints:

| Method | Endpoint | Purpose |
|---|---|---|
| POST | `/api/businesses` | Create a business workspace |
| GET | `/api/customers` | List authorized customers |
| POST | `/api/customers` | Create a customer |
| GET | `/api/invoices` | List and filter invoices |
| POST | `/api/invoices` | Create an invoice |
| GET | `/api/invoices/{id}` | Retrieve invoice details |
| POST | `/api/invoices/{id}/issue` | Issue an invoice |
| POST | `/api/payments` | Initiate a payment |
| GET | `/api/payments/{id}` | Retrieve payment status |
| POST | `/api/payments/opay/callback` | Receive OPay notifications |
| GET | `/api/reconciliation/exceptions` | List unmatched transactions |
| POST | `/api/reconciliation/allocations` | Allocate a verified payment |
| GET | `/api/receivables/summary` | Retrieve receivables summary |
| GET | `/api/reports/collections` | Retrieve collection reports |
| GET | `/api/audit-logs` | Retrieve authorized audit records |

The exact callback contract, request signatures, response formats, authentication requirements, and provider status mapping must follow the current OPay documentation.

All endpoints must enforce authorization, tenant isolation, validation, and consistent error handling.

---

## 12. Payment Processing Rules

The payment lifecycle must be explicit.

Proposed internal payment statuses:

- Initiated
- Pending
- Succeeded
- Failed
- Cancelled
- Reversed
- Refund Pending
- Partially Refunded
- Refunded

The final status model must reflect the provider's actual payment and refund capabilities.

### Processing rules

1. The backend calculates or validates the amount using trusted business records.
2. The backend creates an internal payment reference.
3. The backend initiates the provider request using protected credentials.
4. The customer completes checkout.
5. The backend receives and validates provider notification or retrieves transaction status.
6. The backend verifies the transaction reference, amount, currency, and relevant merchant identity.
7. The backend records the verified payment using idempotent processing.
8. Reconciliation allocates the payment to the correct invoice.
9. The invoice balance and status are updated consistently.
10. The customer and business can view the confirmed outcome.

A customer redirect is useful for user experience, but it is not proof of payment.

The system must also define how to handle late notifications, payment reversals, partial refunds, concurrent payments, provider timeouts, and transactions whose status remains uncertain.

---

## 13. Business Model

PayFlow Africa will primarily operate as a B2B SaaS business.

### Potential revenue streams

**1. Subscription plans**

Monthly or annual charges based on business size, features, branches, or usage.

**2. Enterprise plans**

Higher-value contracts for multi-branch operations, advanced permissions, integrations, reporting, and support.

**3. Usage-based pricing**

Fees for selected platform activities, such as additional reconciliation volume or API usage, where commercially appropriate.

**4. Premium integrations**

Paid integrations with accounting, inventory, ERP, and supported bank-data systems.

Payment-related fees, referrals, or revenue sharing may be considered only where contractually permitted and compliant with applicable regulations.

### Pricing validation

Pricing must be established through customer interviews, competitor research, pilot results, and willingness-to-pay tests. We should not assume customers will pay a particular subscription price before validating the value delivered.

---

## 14. Success Metrics and KPIs

### Product metrics

- Number of businesses onboarded.
- Number of weekly and monthly active businesses.
- Number of invoices issued.
- Number and value of verified payments.
- Percentage of eligible transactions automatically matched.
- Percentage of transactions requiring manual review.
- Median time to reconcile a payment.
- Invoice payment completion rate.
- Number and value of overdue receivables.
- Customer retention and product adoption.

### Reliability metrics

- Duplicate financial processing incidents.
- Incorrect invoice allocations.
- Payment notification processing failures.
- Unresolved payment exceptions.
- API error rate.
- Payment-status verification latency.

### Business metrics

- Paying customers.
- Monthly recurring revenue.
- Annual recurring revenue.
- Customer acquisition cost.
- Gross margin.
- Customer churn.
- Net revenue retention where applicable.
- Customer lifetime value, once sufficient data exists.

### Initial pilot success criteria

Proposed targets to validate during the pilot:

- Three to five businesses participate in the pilot.
- At least three convert to paid accounts.
- Eligible OPay payments can be verified and reconciled reliably.
- No known duplicate payment processing causes double allocation.
- Pilot customers demonstrate a measurable reduction in manual reconciliation time.
- Users can investigate and resolve unmatched transactions.
- At least some customers express a clear willingness to renew.

These are proposed validation thresholds, not achieved results.

---

## 15. Go-to-Market Strategy

### Phase 1: Customer discovery

Interview 20–30 distributors and wholesalers.

Questions should investigate:

- How do they receive customer payments?
- How do they match payments to invoices?
- How many transactions require manual investigation?
- How do they track partial payments and customer debt?
- What does reconciliation cost in staff time?
- Which accounting or inventory systems do they use?
- What happens when payments cannot be identified?
- Would they pay to solve the problem, and what evidence would convince them?

The objective is to identify a specific customer segment with a frequent, costly, and solvable problem.

### Phase 2: Pilot customers

Recruit three to five businesses with sufficiently similar workflows.

Offer guided onboarding and measure the difference between their existing process and the new system.

The pilot should use actual operational workflows and appropriate safeguards for customer data.

### Phase 3: Commercial launch

Convert successful pilots into paying customers.

Develop repeatable onboarding, documentation, customer support, pricing, and sales processes.

### Phase 4: Expansion

Expand to adjacent distributor categories, multi-branch companies, and additional payment and accounting integrations based on evidence of demand.

### Phase 5: Regional growth

Evaluate other African markets individually, considering local payment systems, merchant eligibility, competition, regulations, currency requirements, and operating costs.

---

## 16. Competitive Differentiation

PayFlow Africa will compete with a combination of accounting software, payment gateways, ERP systems, invoicing tools, and reconciliation platforms.

Our proposed differentiation is:

- Designed around the payment-to-invoice workflow of distributors.
- Support for partial payments and complex receivables.
- Provider-independent reconciliation architecture.
- Integration with existing business systems rather than requiring a complete replacement.
- Clear exception handling and financial auditability.
- A focus on reducing the operational work required to collect and account for money.

These are intended differentiators, not yet proven competitive advantages. Customer research must determine which capabilities matter most and which competing products already deliver them well.

---

## 17. Risks and Mitigation

| Risk | Mitigation |
|---|---|
| Businesses do not see enough value | Validate the problem and willingness to pay before building the full platform. |
| OPay access or commercial terms are unsuitable | Confirm merchant eligibility, supported APIs, fees, settlement terms, and use-case restrictions before committing. |
| Payment notifications are duplicated or fraudulent | Verify notifications, validate transactions, enforce idempotency, and audit financial operations. |
| Direct bank transfers cannot be reconciled automatically | Add supported bank-data integrations or statement imports and clearly distinguish verified from unmatched transactions. |
| Incorrect financial balances | Use transactional database updates, explicit allocations, reconciliation tests, and immutable financial history where appropriate. |
| Customer acquisition is expensive | Start with a narrow segment, founder-led sales, and partnerships. |
| Existing products already solve the problem | Research competitors and identify a specific unmet need before differentiating on features. |
| Sensitive business data is exposed | Enforce tenant isolation, least privilege, encryption, monitoring, and incident-response procedures. |
| Regulatory requirements are misunderstood | Obtain appropriate legal and compliance advice before offering regulated payment aggregation, custody, lending, or related services. |
| The product becomes too broad | Keep the initial release focused on invoices, verified payments, reconciliation, and receivables. |

---

## 18. Development Roadmap

### Phase 0 — Validation

Deliverables:

- Customer interview findings.
- Defined initial customer segment.
- Documented existing payment workflows.
- Competitive analysis.
- OPay onboarding and API feasibility assessment.
- Pilot commitments.
- Initial willingness-to-pay evidence.

**Exit criterion:** Evidence that a specific customer segment experiences the problem frequently and is willing to test a solution.

### Phase 1 — Foundation

Deliverables:

- Application structure.
- Business and user onboarding.
- Authentication and authorization.
- Tenant isolation.
- Customer management.
- Invoice creation and management.
- Audit logging.

**Exit criterion:** An authorized business can create customers and invoices securely.

### Phase 2 — Payments

Deliverables:

- OPay provider adapter.
- Payment initiation.
- Payment reference management.
- Secure callback processing.
- Payment-status verification.
- Idempotent transaction recording.
- Payment history.

**Exit criterion:** Supported payment flows can be tested end to end with reliable verification and failure handling.

### Phase 3 — Reconciliation

Deliverables:

- Payment allocations.
- Partial-payment support.
- Invoice balance calculations.
- Unmatched transaction queue.
- Manual exception resolution.
- Reconciliation audit trail.

**Exit criterion:** The system can correctly reconcile supported transactions and handle ambiguous cases without silently misallocating money.

### Phase 4 — Receivables and reporting

Deliverables:

- Overdue invoice tracking.
- Configurable reminders.
- Receivables aging.
- Collection dashboard.
- CSV exports.
- Business-level reporting.

**Exit criterion:** Pilot customers can manage their outstanding balances and produce useful collection reports.

### Phase 5 — Pilot and commercial launch

Deliverables:

- Production deployment.
- Monitoring and backups.
- User documentation.
- Customer onboarding process.
- Pilot evaluation.
- Commercial pricing.
- Support and incident-response procedures.

**Exit criterion:** Real customers use the platform successfully, and pilot results support a sustainable paid offering.

---

## 19. Open Questions Requiring Decisions

Before finalizing the implementation plan, we must resolve the following:

1. Which distributor category should we target first: beverages, food products, electronics, building materials, pharmaceuticals, or another category?
2. How do our initial customers currently record invoices and payments?
3. What OPay merchant account and API access will be available to us?
4. Which OPay payment methods and transaction-status mechanisms are supported for our intended use case?
5. Will the first release handle only OPay-originated payments or also imported bank statements?
6. Which accounting or inventory systems do our first customers use?
7. What subscription price can the target market support?
8. What operational and legal requirements apply to our selected payment flows?
9. What measurable improvement would convince a pilot customer to pay and renew?

These decisions should be based on customer evidence and provider documentation rather than assumptions.

---

## 20. Definition of a Successful First Release

The first release will be considered successful when a real distributor can:

1. Register and configure a business workspace.
2. Add customers and create invoices.
3. Send a payment link to a customer.
4. Accept an eligible OPay payment.
5. Verify the payment securely.
6. Automatically allocate the payment to the correct invoice where the matching criteria are satisfied.
7. Track partial payments and outstanding balances.
8. Investigate unmatched transactions.
9. Review collections and overdue receivables.
10. Export relevant reports.
11. Operate with appropriate security, tenant isolation, auditability, and recovery procedures.

The release must be tested with realistic payment failures, duplicate notifications, delayed callbacks, partial payments, and unauthorized access attempts.

---

## 21. Final Product Strategy

PayFlow Africa will not attempt to compete simply by being another payment gateway.

It will begin by solving one measurable problem: **helping distributors connect incoming payments to invoices and maintain accurate customer balances without relying on excessive manual work.**

OPay will provide an initial payment integration. The value of the product will come from the software built around that payment: reconciliation, receivables management, reporting, integrations, and operational reliability.

We will validate the problem before committing to a large implementation, build a focused first release, secure paying pilot customers, and expand based on demonstrated demand.

**The first business milestone is not $100 million. It is proving that a small group of businesses will pay us repeatedly because PayFlow Africa solves a problem they cannot afford to ignore.**
