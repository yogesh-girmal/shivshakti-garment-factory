# shivshakti-garment-factory

# GARMENT OS
## Complete Product Requirements & Developer Handover

**Project:** Garment Factory Production, Workforce & Cost Management System  
**Version:** 1.0  
**Application type:** Android-first Progressive Web Application (PWA)  
**Primary development agent:** Kilo Code  
**Frontend:** React + TypeScript  
**Database:** Firebase Cloud Firestore  
**Authentication:** Firebase Authentication  
**Hosting:** Firebase Hosting  
**Initial deployment:** Single garment unit, one supervisor, one Android device  
**Primary timezone:** Asia/Kolkata (IST)  
**Initial product:** Formal shirts  
**Future products:** Casual shirts, kurtas and uniforms

---

# 1. PROJECT VISION

Build a comprehensive garment manufacturing management system that provides granular visibility into every employee, machine, production operation, cutting batch, component, stock movement, quality issue and labour cost.

The primary business objective is to control manufacturing costs and improve workforce utilisation.

The application must help management answer:

1. Which employees attended work?
2. Which employees were late or absent?
3. What work was assigned to each employee?
4. Which machine was used?
5. Which product and cutting batch was involved?
6. How many components were issued?
7. How many components were completed and accepted?
8. How many were rejected or sent for rework?
9. How much internal production value did each employee generate?
10. How does that production value compare with their fixed daily salary?
11. Which operations are creating production bottlenecks?
12. Which components are unavailable and need to be supplied next?
13. How much labour cost is attributable to each production order?
14. Which employees, machines and processes are underutilised?

## Fundamental operating principle

**All production allocation, completion, approval and stock movement must be controlled by the supervisor.**

Operators will NOT:
- Log into the application.
- Scan QR codes.
- Enter their production quantities.
- Approve their own output.
- Modify stock records.
- Modify production allocations.

The supervisor will use one Android device to perform these actions.

Employees will have permanent identification QR cards. Machines will have permanent identification QR stickers.

Cutting batches will have automatically generated internal component-bundle IDs. Physical QR labels for every component bundle are not required initially.

The system must remain configurable so that additional workflows, products, machines, integrations and employees can be supported later.

---

# 2. INITIAL BUSINESS CONTEXT

The factory manufactures:

- Formal shirts
- Casual shirts
- Kurtas
- Uniforms

Formal shirts are the first product family to implement.

Two initial formal-shirt variants:

1. Full-sleeve formal shirt.
2. Half-sleeve formal shirt.

The factory has different categories of employees:

- Stitching operators
- Helpers
- Supervisors
- Cutting operators
- Quality checkers, where applicable
- Finishing employees, where applicable

Stitching operators generally specialise in particular operations.

The same operator may perform finishing operations when assigned.

Employee compensation is primarily fixed salary or fixed daily wages, rather than piece-rate wages.

However, management wants to assign an internal standard labour value to every operation and compare completed production value against employee salary.

Example internal operation rates supplied for initial design:

| Operation | Internal standard value |
|---|---:|
| Collar attachment | ₹2.50 per collar |
| Sleeve attachment | ₹1.20 per sleeve side |
| Pocket attachment | ₹1.50 per pocket |

These are illustrative configuration values supplied by the business and are not externally validated market rates.

The application must allow all rates to be edited without code changes.

---

# 3. TECHNOLOGY ARCHITECTURE

## 3.1 Primary technology stack

| Layer | Technology |
|---|---|
| Frontend | React |
| Language | TypeScript |
| Build tool | Vite |
| UI styling | Tailwind CSS |
| Component library | shadcn/ui or equivalent |
| Application format | Progressive Web Application |
| PWA support | vite-plugin-pwa |
| QR scanning | @zxing/browser |
| QR generation | qrcode |
| Database | Firebase Cloud Firestore |
| Authentication | Firebase Authentication |
| Hosting | Firebase Hosting |
| Offline cache | Service Worker + IndexedDB |
| State management | Zustand or React Context where appropriate |
| Form validation | Zod |
| Date handling | date-fns |
| Charts | Recharts |
| AI integration | Firebase AI Logic + Gemini, later phase |
| Source control | GitHub |
| Coding agent | Kilo Code |

Use stable, mutually compatible package versions. Record all dependencies and versions in package.json and package-lock.json.

## 3.2 Application deployment

The application must initially be deployed on Firebase Hosting.

Expected initial URL:

https://YOUR-PROJECT-ID.web.app

Custom domain can be configured later:

https://factory.YOURDOMAIN.in

The supervisor should be able to:

1. Open the web application on an Android phone.
2. Log in using the authorised Google account.
3. Select Add to Home Screen.
4. Launch it like a normal installed application.
5. Use the phone camera to scan employee and machine QR codes.

No Google Play Store publication is required for the initial PWA.

Future Android packaging can be explored using Trusted Web Activity or Capacitor, without rewriting the business application.

## 3.3 Development agent

Kilo Code is the primary development agent.

Kilo Code should be responsible for:

- Creating the project structure.
- Implementing React components.
- Creating Firestore data models.
- Implementing application workflows.
- Writing business calculations.
- Creating QR-scanning functionality.
- Writing unit and integration tests.
- Running the application locally.
- Fixing errors.
- Preparing production builds.
- Preparing Firebase deployment configuration.

The project owner will manually create Firebase resources and provide the Firebase web configuration locally.

Do not assume that the Google AI Pro subscription automatically provides Gemini API credits for Kilo Code.

Kilo Code is the coding agent; its model usage is controlled by the selected provider and its applicable limits.

---

# 4. DEVELOPMENT AND APPLICATION PHASES

Development must be incremental.

Do not attempt to generate the entire platform in one step.

## Phase 1: Application foundation

Build:

- React and TypeScript project.
- Responsive mobile-first layout.
- PWA manifest.
- Service worker.
- Firebase configuration.
- Google authentication.
- Supervisor dashboard.
- Application navigation.
- Basic Firestore integration.

Deliverable: A deployed PWA with secure supervisor login.

## Phase 2: Employee and machine master

Build:

- Employee registration.
- Employee designation.
- Employee salary configuration.
- Employee QR code generation.
- Machine registration.
- Machine QR code generation.
- Machine types and capabilities.
- Employee skill matrix.

Deliverable: The supervisor can register employees and machines and print their QR identification labels.

## Phase 3: Product engineering

Build:

- Product families.
- Product variants.
- Component master.
- Unit-of-measure master.
- BOM templates.
- Operation master.
- Product routing templates.
- Operation-rate configuration.
- Template versioning.

Deliverable: Formal-shirt manufacturing templates can be created and reused.

## Phase 4: Cutting and inventory

Build:

- Production orders.
- Cutting batches.
- Size-wise and colour-wise quantities.
- Component stock generation.
- Automatic component-bundle ID generation.
- Bundle splitting.
- Bundle merging.
- Stock issue and return.
- Stock movement ledger.

Deliverable: The complete journey of cut pieces can be tracked.

## Phase 5: Supervisor production management

Build:

- Employee QR scanning.
- Machine QR scanning.
- Batch selection.
- Component-bundle selection.
- Operation selection.
- Quantity allocation.
- Start and completion records.
- Partial completion.
- Quality acceptance.
- Rejection and rework.
- Employee reassignment.

Deliverable: Complete supervisor-controlled production tracking.

## Phase 6: Labour accounting and reporting

Build:

- Employee daily salary cost.
- Production value calculations.
- Salary recovery dashboard.
- Employee-wise productivity.
- Operation-wise output.
- Order-wise labour cost.
- Helper cost allocation.
- Supervisor cost allocation.
- Downtime analytics.
- Production bottleneck analysis.

Deliverable: Complete labour-cost and production analytics.

## Phase 7: Attendance integration

Build:

- Attendance imports.
- Daily attendance reports.
- Late-arrival calculations.
- Early-departure calculations.
- Missing punch exceptions.
- Shift configuration.
- Overtime approval records.
- Payroll adjustment reports.

Initially support CSV import from a compatible fingerprint device.

Direct device integration can be implemented later after obtaining the device's API, SDK or communication protocol.

## Phase 8: AI assistant

Implement an AI assistant that can answer analytical questions using authorised, aggregated factory data.

Examples:

- Which employees have the lowest output relative to salary?
- Why is collar production delayed?
- Which batch has pending components?
- Which operations have the highest rework?
- What should the supervisor allocate next?
- What is today's total labour cost?
- Which production order has the highest labour cost per accepted garment?

The AI assistant must initially be read-only.

It must not independently change production records, approve output, allocate work or modify payroll.

---

# 5. PRODUCT AND VARIANT MASTER

Create a configurable product architecture.

## Product families

| Product family ID | Product |
|---|---|
| PF-001 | Formal shirt |
| PF-002 | Casual shirt |
| PF-003 | Kurta |
| PF-004 | Uniform |

## Initial formal-shirt variants

| Variant ID | Description |
|---|---|
| FS-LS-001 | Formal shirt, full sleeve |
| FS-SS-001 | Formal shirt, half sleeve |

Additional style attributes must be configurable:

- Sleeve length.
- Pocket count.
- Collar type.
- Collar band type.
- Cuff type.
- Sleeve placket type.
- Front placket construction.
- Fabric type.
- Size range.
- Button configuration.
- Special stitching requirements.

Do not hardcode the above as fixed application constraints.

A product should be configurable without changing React components or application logic.

---

# 6. COMPONENT MASTER AND BILL OF MATERIALS

Create a master of reusable garment components.

Initial component examples:

| Component ID | Component |
|---|---|
| CMP-001 | Front panel |
| CMP-002 | Back panel |
| CMP-003 | Yoke |
| CMP-004 | Collar |
| CMP-005 | Collar band |
| CMP-006 | Sleeve panel |
| CMP-007 | Cuff |
| CMP-008 | Sleeve placket |
| CMP-009 | Pocket |
| CMP-010 | Front placket |
| CMP-011 | Interlining |
| CMP-012 | Button |
| CMP-013 | Buttonhole |

The component master must support:

- Component name.
- Component category.
- Base unit.
- Unit conversions.
- Product compatibility.
- Active/inactive status.
- Optional components.
- Component-specific quality requirements.

## 6.1 Formal full-sleeve shirt BOM

Initial illustrative BOM:

| Component | Quantity per garment |
|---|---:|
| Front/back body set | 1 set |
| Collar set | 1 set |
| Collar band set | 1 set |
| Sleeve panels | 2 panels |
| Cuff pieces | 2 pieces |
| Sleeve placket sets | 2 sets |
| Pocket | 1, configurable |
| Buttons | Style-dependent |

## 6.2 Formal half-sleeve shirt BOM

| Component | Quantity per garment |
|---|---:|
| Front/back body set | 1 set |
| Collar set | 1 set |
| Collar band set | 1 set |
| Sleeve panels | 2 panels |
| Pocket | 1, configurable |
| Sleeve hem allowance | As per pattern |
| Buttons | Style-dependent |

Half-sleeve styles must not automatically receive full-sleeve cuff and placket operations.

The BOM is a template, not an immutable definition.

## 6.3 Unit-of-measure flexibility

This requirement is critical.

The word "sleeve" may mean:

- One sleeve panel.
- One pair of sleeve panels.
- One garment's complete sleeve set.

The system must not assume that these are equivalent.

Each component must have:

- `baseUom`
- `displayUom`
- `conversionFactor`
- `quantityPerGarment`
- `garmentEquivalentQuantity`

Example:

25 shirts require 50 individual sleeve panels.

The system may display this as:

- 50 sleeve panels; or
- 25 sleeve pairs.

Both representations must map to the same inventory quantity.

The supervisor should be able to select the preferred unit of measurement for handling bundles.

---

# 7. CUTTING BATCH AND COMPONENT BUNDLE MANAGEMENT

## 7.1 Parent cutting batch

A cutting batch represents the original production cutting quantity.

Example:

```text
Production Order: ORD-001
Product: Formal Shirt
Variant: Full Sleeve
Cutting Batch: CB-2026-0001
Cutting Quantity: 25 Garments
```

The cutting batch remains the parent record.

Do not create a new cutting batch when components are separated.

## 7.2 Automatically generated component-bundle IDs

From the parent cutting batch, generate component-bundle records automatically.

Illustrative output:

```text
CB-2026-0001
    |
    |--- CB-2026-0001-COLLAR-001
    |
    |--- CB-2026-0001-SLEEVE-001
    |
    |--- CB-2026-0001-CUFF-001
    |
    |--- CB-2026-0001-POCKET-001
    |
    |--- CB-2026-0001-BODY-001
```

For example:

| Component bundle | Quantity |
|---|---:|
| Collars | 25 collar units |
| Sleeve panels | 50 panels, or 25 pairs |
| Cuffs | 50 cuff pieces |
| Pockets | 25 pockets |
| Body sets | 25 garment sets |

The above quantities are examples, subject to the selected BOM and construction.

## 7.3 Bundle size

The usual target bundle size is 25 units.

However, implement bundle size as a configurable field.

Different components may have different handling quantities.

Example:

- Collar bundle: 25 collars.
- Sleeve bundle: 25 sleeve pairs or 50 individual panels.
- Pocket bundle: 25 pockets.
- Body bundle: 25 garment sets.

The supervisor should be able to adjust bundle size.

## 7.4 Bundle splitting

Allow the supervisor to split a bundle.

Example:

```text
Original bundle:
CB-2026-0001-COLLAR-001
Quantity: 25

Split into:

CB-2026-0001-COLLAR-001-A
Quantity: 10

CB-2026-0001-COLLAR-001-B
Quantity: 15
```

The original bundle must be marked as split or partially consumed.

Its quantity must not remain available for another allocation.

## 7.5 Bundle merging

Allow compatible bundles to be merged when:

- They contain the same component.
- They belong to compatible product variants.
- They have matching sizes.
- Their colour and fabric lot are compatible.
- Quality status is compatible.

Maintain references to original bundles.

Never delete parent-child lineage.

## 7.6 No physical bundle QR requirement initially

Internal bundle IDs are enough.

The supervisor selects the batch and component bundle from the application.

Physical QR labels may be introduced later if inventory volume justifies them.

---

# 8. OPERATION MASTER

Create a global operation master.

Each operation should have:

| Field | Description |
|---|---|
| operationId | Unique identifier |
| operationCode | Unique business code |
| operationName | Display name |
| operationCategory | Cutting, preparation, assembly, finishing |
| outputUom | Collar, sleeve panel, shirt, etc. |
| defaultStandardMinutes | Expected operation time |
| defaultRate | Internal standard labour value |
| requiredMachineTypes | Compatible machine categories |
| requiredSkills | Required operator skills |
| qualityCheckpoint | Whether quality approval is required |
| isActive | Active/inactive |
| description | Operation instructions |

Operation rate and standard time must be configurable separately.

## 8.1 Initial formal shirt operation library

The following is a proposed operation library. Validate every operation against the actual factory workflow before enabling it for production.

### Cutting and preparation

| Operation | Output unit |
|---|---|
| Fabric spreading | Lay |
| Pattern marking | Lay |
| Fabric cutting | Garment set |
| Component sorting | Component |
| Numbering and bundling | Garment set |
| Interlining fusing | Component |
| Collar preparation | Collar set |
| Collar turning and trimming | Collar |
| Collar topstitching | Collar |
| Pocket folding/hemming | Pocket |
| Sleeve placket preparation | Placket set |
| Cuff preparation | Cuff set |
| Front placket preparation | Front panel |
| Yoke preparation | Yoke |

### Body construction

| Operation | Output unit |
|---|---|
| Shoulder joining | Shirt |
| Yoke attachment | Shirt |
| Front placket finishing | Front panel |
| Pocket attachment | Pocket |
| Body preparation | Shirt |

### Main assembly

| Operation | Output unit |
|---|---|
| Collar band attachment | Shirt |
| Collar attachment | Collar / shirt |
| Sleeve attachment | Sleeve side |
| Sleeve topstitching | Sleeve side |
| Side joining | Shirt |
| Cuff attachment | Cuff |
| Bottom hemming | Shirt |
| Half-sleeve hemming | Sleeve side |

### Finishing

| Operation | Output unit |
|---|---|
| Buttonhole stitching | Buttonhole |
| Button attachment | Button |
| Thread trimming | Shirt |
| Bartacking | Location |
| Pressing and ironing | Shirt |
| Measurement inspection | Shirt |
| Final quality inspection | Shirt |
| Folding | Shirt |
| Packing | Shirt |

## 8.2 Product routing templates

Create separately versioned routing templates.

Example:

```text
ROUTING-FS-LS-001-V1
Formal Shirt - Full Sleeve

ROUTING-FS-SS-001-V1
Formal Shirt - Half Sleeve
```

Routing templates must support:

- Required operations.
- Optional operations.
- Parallel operations.
- Operation dependencies.
- Different operation sequences.
- Variant-specific operations.
- Style-specific changes.
- Reusable templates.
- Version history.
- Effective dates.

Do not implement production routing as a hardcoded single sequential list.

Use operation dependencies and a configurable directed acyclic graph (DAG), so collar preparation, pocket preparation and sleeve preparation can happen independently.

Only operations whose dependencies have been satisfied should be available for allocation.

A supervisor must be able to create a revised routing template for a new shirt style without changing application code.

## 8.3 Rate versioning

If collar attachment changes from ₹2.50 to ₹2.75:

- New production orders should use the new rate.
- Existing production orders should retain their original rate snapshot.
- Historical production value must not be recalculated using the new rate.

Every production order should retain its template and operation-rate version.

---

# 9. EMPLOYEE MASTER

Each employee should have:

- Employee ID.
- Employee name.
- Designation.
- Department.
- Employment status.
- Joining date.
- Salary basis.
- Monthly salary or daily wage.
- Daily cost calculation settings.
- Assigned supervisor.
- Skill profile.
- Eligible machine types.
- QR identifier.
- Shift schedule.

Example employee categories:

```text
STITCHING_OPERATOR
HELPER
CUTTING_OPERATOR
SUPERVISOR
QUALITY_CHECKER
FINISHING_OPERATOR
PACKING_OPERATOR
```

The employee master must support custom designations.

## 9.1 Skill matrix

An employee may be authorised to perform more than one operation.

Example:

| Employee | Collar attachment | Sleeve attachment | Pocket attachment |
|---|---|---|---|
| EMP-001 | Expert | No | Basic |
| EMP-002 | No | Expert | Basic |
| EMP-003 | Basic | No | Expert |

The application must check employee skills when allocating work.

## 9.2 Employee QR

Each employee receives one permanent QR ID.

Example:

```text
EMP-001
```

Do not encode salary, personal details or sensitive information inside the QR code.

The QR code is an identification mechanism, not an authentication mechanism.

Only the supervisor can use the application.

---

# 10. MACHINE MASTER

Each machine must have:

- Machine ID.
- Machine type.
- Machine category.
- Location.
- Capabilities.
- Operational status.
- Maintenance status.
- QR identifier.

Example:

```text
MCH-001
Single Needle Machine

MCH-002
Overlock Machine

MCH-003
Buttonhole Machine

MCH-004
Button Attaching Machine
```

Each machine receives a permanent QR sticker.

The QR scan identifies the machine.

The allocation engine checks machine-operation compatibility.

One machine must not have multiple conflicting active allocations unless explicitly permitted by configuration.

---

# 11. SUPERVISOR-CONTROLLED ALLOCATION WORKFLOW

This is the core workflow of the PWA.

## 11.1 Allocation sequence

1. Supervisor logs in.
2. Opens Allocate Work.
3. Scans employee QR.
4. Application retrieves employee information.
5. Scans machine QR.
6. Application checks machine availability.
7. Supervisor selects production order.
8. Supervisor selects cutting batch.
9. Supervisor selects component bundle.
10. Supervisor selects operation.
11. Application retrieves operation rate.
12. Supervisor enters quantity to issue.
13. Application calculates expected production value.
14. Supervisor confirms allocation.
15. Allocation is saved.
16. Stock movement is recorded.

## 11.2 Allocation validation

Before accepting an allocation, check:

- Employee is active.
- Employee has checked in.
- Employee is eligible for the selected operation.
- Machine is operational.
- Machine is compatible with the operation.
- Machine has no conflicting active allocation.
- Employee has no prohibited overlapping assignment.
- Selected batch is available.
- Component bundle has sufficient available stock.
- Previous required operations are complete.
- Operation rate is configured.
- Required product variant matches the batch.

## 11.3 Allocation record

Example:

```json
{
  "allocationId": "ALLOC-0001",
  "employeeId": "EMP-001",
  "machineId": "MCH-001",
  "productionOrderId": "ORD-001",
  "cuttingBatchId": "CB-2026-0001",
  "componentBundleId": "CB-2026-0001-COLLAR-001",
  "operationId": "OP-COLLAR-ATTACH",
  "allocatedQuantity": 25,
  "unit": "COLLAR",
  "rateSnapshot": 2.5,
  "expectedProductionValue": 62.5,
  "status": "ISSUED",
  "allocatedAt": "SERVER_TIMESTAMP",
  "supervisorUid": "AUTHENTICATED_UID"
}
```

Use server timestamps where possible.

## 11.4 Allocation states

Support:

```text
DRAFT
RESERVED
ISSUED
IN_PROGRESS
PARTIALLY_COMPLETED
RETURNED
COMPLETED
CANCELLED
```

Do not silently overwrite completed allocations.

Corrections must be recorded as adjustment events.

---

# 12. PRODUCTION COMPLETION

Only the supervisor can record completion.

Example:

Employee EMP-001 receives 25 collars.

After checking the completed work, the supervisor records:

| Status | Quantity |
|---|---:|
| Accepted | 22 |
| Rework | 2 |
| Rejected | 1 |
| Pending / returned unprocessed | 0 |

The quantities must reconcile:

25 issued = 22 accepted + 2 rework + 1 rejected.

If rework is later accepted, update the quality and stock state through a new event.

Do not generate production value twice for the same originally assigned work.

## Completion workflow

- Select active allocation.
- Enter completed quantity.
- Enter accepted quantity.
- Enter rejected quantity.
- Enter rework quantity.
- Enter returned quantity.
- Select rejection reason where required.
- Supervisor confirms.
- Update stock movement ledger.
- Update production summary.
- Update employee production-value summary.

## Quality reasons

Allow configurable reasons:

- Stitching defect.
- Incorrect measurement.
- Component damage.
- Fabric defect.
- Incorrect attachment.
- Broken thread.
- Incorrect colour or size.
- Other.

---

# 13. LABOUR COSTING ENGINE

This is the central financial functionality.

The factory pays fixed salary or fixed daily wages.

The application must compare employee production value against their labour cost.

Important distinction:

Operation values are internal standard labour values. They are not automatically the employee's contractual piece-rate wages.

## 13.1 Employee daily cost

For employees paid daily:

```text
Daily Labour Cost = Configured Daily Wage
```

For monthly salary employees:

```text
Daily Labour Cost =
Monthly Salary / Configured Standard Paid Days
```

Do not hardcode the number of monthly working days.

Store the applicable salary divisor, working calendar and paid-leave policy in configuration.

## 13.2 Production value

```text
Production Value =
SUM(Accepted Quantity × Applicable Operation Rate)
```

Only approved accepted output counts towards standard production value.

Rework and rejects must be separately recorded.

## 13.3 Salary recovery

```text
Salary Recovery Percentage =
Production Value / Daily Labour Cost × 100
```

Example:

```text
Employee daily cost: ₹200

Collar attachment:
40 × ₹2.50 = ₹100

Sleeve attachment:
50 × ₹1.20 = ₹60

Pocket attachment:
10 × ₹1.50 = ₹15

Total production value: ₹175

Salary recovery: 87.5%
```

## 13.4 Employee daily dashboard

Show:

- Employee name and ID.
- Attendance status.
- Daily salary cost.
- Total assigned quantity.
- Total accepted quantity.
- Rejected quantity.
- Rework quantity.
- Production value.
- Salary recovery percentage.
- Pending allocations.
- Downtime.
- Reason for unproductive time.

## 13.5 Important financial distinction

Display the following as separate metrics:

**A. Standard production value**

Accepted quantity multiplied by internal operation rate.

**B. Actual employee labour cost**

Employee salary attributable to the production day or assigned order.

**C. Salary recovery ratio**

Standard production value divided by actual daily salary cost.

**D. Actual order labour cost**

The actual attributable labour expense of the production order.

**E. Labour cost per accepted completed garment**

Attributable labour cost divided by complete accepted garment quantity.

Do not label production value as actual revenue or profit.

## 13.6 Operation rate calibration

Allow management to enter:

- Standard minutes per operation.
- Internal operation rate.
- Effective date.
- Product applicability.
- Rate version.

Where reliable standard time information is available:

```text
Standard Operation Value =
Standard Minutes × Target Labour Value Per Minute
```

This provides a consistent methodology for checking whether the sum of operation values represents the desired standard direct-labour value per garment.

Do not impose one universal target multiplier.

---

# 14. HELPERS AND SUPERVISOR COST ALLOCATION

Helpers do not necessarily generate independent garment completion value.

Track their support activities.

Examples:

- Bundle preparation.
- Material movement.
- Supporting an assigned operator.
- Thread and accessory distribution.
- Machine assistance.
- Workstation preparation.

A helper may support multiple operators.

Record:

- Helper ID.
- Supported employee or production line.
- Production order.
- Activity.
- Start time.
- End time.
- Supervisor confirmation.

Do not double-count completed garments as production generated by both operator and helper.

## Helper cost allocation

For order-level costing, allocate helper salary based on recorded support time or a configured line-level allocation methodology.

## Supervisor cost

Track supervisor cost separately.

Suggested supervisor performance metrics:

- Team salary recovery.
- Employee allocation coverage.
- Unallocated employee minutes.
- Material shortage downtime.
- Machine breakdown downtime.
- Quality rejection percentage.
- Pending production.
- Unexplained stock differences.

Allocate supervisor cost across supervised production orders through a configurable rule, such as supervised direct labour hours.

---

# 15. DOWNTIME MANAGEMENT

Create a supervisor-controlled downtime module.

Reasons:

```text
MACHINE_BREAKDOWN
MATERIAL_SHORTAGE
POWER_FAILURE
OPERATOR_ABSENCE
SUPERVISOR_DELAY
WAITING_FOR_PREVIOUS_OPERATION
QUALITY_REWORK
APPROVED_BREAK
OTHER
```

Fields:

- Employee.
- Machine.
- Production order.
- Start time.
- End time.
- Duration.
- Downtime reason.
- Notes.
- Supervisor approval.

The application must not classify every non-production minute as employee idleness.

Distinguish employee-controlled delays from production-management or machine-related constraints.

Machine sensor integration can be introduced later.

---

# 16. ATTENDANCE MANAGEMENT

Initial shift:

```text
Shift Start: 09:30 AM
Shift End: 06:00 PM
Timezone: Asia/Kolkata
```

Make shift timing configurable.

Attendance should support:

- Fingerprint device check-in.
- Fingerprint device check-out.
- Late arrival.
- Early departure.
- Missing punches.
- Absence.
- Overtime.
- Shift exceptions.
- Manual supervisor correction with audit history.

The application should initially support attendance CSV imports.

Do not assume that any biometric device has a compatible API.

Obtain the machine's model, export format and SDK/API before implementing live integration.

Do not store fingerprint images or biometric templates in Firebase.

## Late attendance

Calculate:

```text
Late Minutes =
MAX(0, Actual Check-in - Shift Start - Grace Period)
```

The grace period must be configurable.

Generate late-arrival reports.

Do not automatically impose a fixed ₹50 wage deduction for five minutes of lateness.

Any wage deduction or fine policy must be independently checked for applicable labour-law compliance and authorised before payroll processing.

The system should initially record lateness and provide an exception report.

---

# 17. FIREBASE DATA MODEL

Use Cloud Firestore.

Keep the schema flexible, but use consistent document references and immutable transaction records.

Recommended collections:

```text
appUsers
employees
employeeSkills
machines
departments

productFamilies
productVariants
components
unitsOfMeasure

bomTemplates
bomTemplateVersions
routingTemplates
routingVersions
operationMaster
operationRates

productionOrders
cuttingBatches
componentBundles
stockBalances
stockMovements

allocations
workTransactions
qualityEvents
downtimeEvents

attendanceEvents
attendanceImports

labourCostLedger
dailyEmployeeSummaries
dailyProductionSummaries

systemSettings
auditLogs
```

## Important schema design rules

1. Use unique identifiers.
2. Store references to parent records.
3. Keep historical snapshots of operation rates.
4. Use server timestamps for confirmed transactions.
5. Maintain immutable event histories.
6. Avoid deleting transactions.
7. Maintain current status separately from transaction history.
8. Use Firestore indexes for common queries.
9. Use explicit units of measure.
10. Support configurable product operations.

## Stock movement ledger

Every inventory change must generate a stock movement record.

Example:

```json
{
  "movementId": "MOVE-0001",
  "cuttingBatchId": "CB-2026-0001",
  "componentBundleId": "CB-2026-0001-COLLAR-001",
  "componentId": "CMP-004",
  "movementType": "ISSUE_TO_OPERATOR",
  "quantity": 25,
  "unit": "COLLAR",
  "employeeId": "EMP-001",
  "allocationId": "ALLOC-0001",
  "timestamp": "SERVER_TIMESTAMP",
  "supervisorUid": "AUTHENTICATED_UID"
}
```

Movement types:

```text
CUTTING_RECEIPT
BUNDLE_CREATED
BUNDLE_SPLIT
BUNDLE_MERGED
RESERVE
ISSUE_TO_OPERATOR
PARTIAL_RETURN
COMPLETION_RECEIPT
QUALITY_REJECTION
REWORK_ISSUE
REWORK_RECEIPT
SCRAP
MANUAL_ADJUSTMENT
```

Stock balances must be derived or reconciled against movements.

Do not allow a user interface to update stock balances without recording the corresponding movement.

## Audit records

Every important change must record:

- Entity type.
- Entity ID.
- Previous state where applicable.
- New state.
- Action.
- User UID.
- Timestamp.
- Reason for correction.

---

# 18. USER ACCESS AND SECURITY

Only one supervisor will initially use the application.

Use Firebase Authentication with an authorised Google account.

Do not create login accounts for operators.

Employee QR codes identify employees but do not grant application access.

Initial user role:

```text
SUPERVISOR
```

Keep the architecture ready for later roles:

```text
ADMIN
SUPERVISOR
MANAGEMENT_VIEWER
```

The initial supervisor may also administer configuration.

Security requirements:

- Restrict access to the authorised Google UID.
- Default-deny Firestore security rules.
- Prevent unauthenticated reads and writes.
- Restrict access to salary information.
- Do not store authentication passwords in Firestore.
- Do not expose service-account credentials.
- Do not commit secrets to GitHub.
- Add Firebase App Check before production rollout.
- Require supervisor confirmation for sensitive transactions.

Firebase configuration used in a browser is not a substitute for Firestore security rules.

Service-account JSON and private keys must never be placed inside React code or frontend environment variables.

---

# 19. PWA OFFLINE AND SYNCHRONISATION

The application should be designed to support unreliable factory internet connectivity.

Requirements:

- Installable PWA.
- Cached application shell.
- Cached employee, machine and product master data.
- Clear online/offline indicator.
- Clear last-sync timestamp.
- Offline viewing of previously loaded records.
- Synchronisation status.
- Retry failed requests.
- Prevent duplicate submissions.

For the first version, stock-changing operations should require connectivity.

Specifically:

- Work allocation.
- Stock issue.
- Stock return.
- Production completion.
- Stock adjustment.

These operations affect shared stock balances and should not be falsely shown as committed when the device is offline.

If offline production transactions are required later, introduce a proper IndexedDB transaction outbox with unique idempotency IDs, reconciliation and conflict handling.

Firestore web offline persistence must be configured explicitly.

Do not assume offline reads and writes automatically make all inventory operations transaction-safe.

---

# 20. DASHBOARDS AND ANALYTICS

## Dashboard 1: Factory overview

Show:

- Employees present.
- Employees absent.
- Late employees.
- Active assignments.
- Available machines.
- Completed pieces.
- Accepted pieces.
- Rejected pieces.
- Pending production.
- Total production value.
- Total labour cost.

## Dashboard 2: Employee productivity

Show:

- Employee ID and name.
- Designation.
- Salary.
- Assigned operations.
- Accepted quantity by operation.
- Production value.
- Salary recovery percentage.
- Rework.
- Downtime.
- Current assignment.

## Dashboard 3: Production order

Show:

- Customer order.
- Product.
- Product variant.
- Order quantity.
- Cutting quantity.
- Component availability.
- Operation-wise completion.
- Work in progress.
- Quality rejection.
- Final accepted garments.

## Dashboard 4: Inventory

Show:

- Component.
- Cutting batch.
- Size.
- Colour.
- Available quantity.
- Issued quantity.
- Reserved quantity.
- WIP quantity.
- Rework quantity.
- Rejected quantity.

## Dashboard 5: Labour cost

Show:

- Operator salaries.
- Helper salaries.
- Supervisor cost.
- Operation production value.
- Daily salary recovery.
- Order-level labour cost.
- Labour cost per accepted garment.

## Dashboard 6: Bottleneck detection

Show:

- Operations with pending stock.
- Components unavailable.
- Employees waiting for stock.
- Machines idle.
- Work-in-progress accumulation.
- Repeated quality defects.
- Orders behind schedule.

---

# 21. AI ASSISTANT INSIDE THE APPLICATION

AI is a future application feature, separate from Kilo Code.

Use Firebase AI Logic with a supported Gemini model through the Gemini Developer API when enabled.

The first AI implementation should be read-only.

## Example questions

"Give me today's production report."

"Which operators are below their daily production-value target?"

"Which component should the supervisor issue next?"

"How many collars remain available?"

"Which batch has the most pending work?"

"Which product has the highest direct labour cost?"

"Why is sleeve production delayed?"

"Compare production efficiency over the last seven working days."

## AI implementation principles

1. AI must use actual database-derived information.
2. Do not allow AI to invent production figures.
3. Use read-only data access initially.
4. Do not send unnecessary employee personal information.
5. Do not expose payroll details to an unauthorised user.
6. Do not let AI execute stock movements.
7. Do not let AI modify operation rates.
8. Do not let AI approve attendance or payroll deductions.
9. Display the date range and data source of analytical answers.
10. Clearly indicate when information is unavailable.

AI can suggest which employee might perform the next available operation, but supervisor confirmation is mandatory.

Do not expose Gemini API keys or unrestricted backend credentials in the frontend.

Use Firebase App Check and appropriate API restrictions.

The AI feature is not a prerequisite for the initial production-management release.

---

# 22. FIREBASE ACCOUNT AND RESOURCE SETUP

The project owner will create the Firebase resources manually.

Kilo Code should prepare the application and provide setup instructions, but must not assume access to the owner's Google account.

## Step 1: Create Firebase project

Visit:

https://console.firebase.google.com/

Create a project.

Suggested project name:

```text
garment-factory-os
```

Project ID must be globally unique, so choose an available ID.

Start with the Firebase Spark plan.

## Step 2: Register a web application

Inside Firebase project:

1. Open Project Overview.
2. Select Add App.
3. Choose Web.
4. Enter application name: Garment OS.
5. Register the application.
6. Copy the Firebase web configuration.

Configuration structure:

```javascript
{
  apiKey: "...",
  authDomain: "...",
  projectId: "...",
  storageBucket: "...",
  messagingSenderId: "...",
  appId: "..."
}
```

These web configuration identifiers are not service-account secrets. Firestore rules and Authentication settings must still secure the project.

## Step 3: Enable Firebase Authentication

Open:

Build → Authentication.

Enable Google sign-in.

Add the supervisor's Google email.

Configure authorised domains.

Initially allow only the intended supervisor account.

## Step 4: Create Cloud Firestore

Open:

Build → Firestore Database.

Create a database using Native mode.

Recommended location: an India region such as `asia-south1`, if offered for the selected database mode and product configuration.

Check region availability carefully before creating the database because the database location cannot be changed later.

Do not enable unrestricted test-mode access for production.

## Step 5: Firebase Hosting

Enable Firebase Hosting.

The application will be deployed to the generated Firebase domain.

## Step 6: Firebase App Check

Configure App Check for the web application before production rollout.

Use the appropriate reCAPTCHA-based provider and verify the app's actual domain.

Configure a development debug provider only for local development.

Never distribute production debug tokens.

## Step 7: Firebase AI Logic

This is optional and belongs to the later AI phase.

When required:

1. Open Firebase AI Logic.
2. Follow the setup wizard.
3. Select Gemini Developer API for initial experimentation.
4. Configure App Check.
5. Test with anonymised production data first.
6. Review current usage limits and data-handling terms.

The free Gemini Developer API tier has separate usage and data-handling terms. Do not send employee-sensitive payroll information without reviewing those terms.

## Step 8: Billing controls

Remain on Spark initially.

The documented Firestore no-cost quota for the Standard edition includes:

- 1 GiB stored data.
- 50,000 document reads per day.
- 20,000 document writes per day.
- 20,000 document deletes per day.
- 10 GiB monthly outbound transfer.

Firebase Hosting currently provides 10 GB of no-cost stored hosting content and 10 GB monthly data transfer.

If a Spark product quota is exceeded, the affected product may stop serving requests until the next billing cycle.

Monitor usage before increasing activity.

Official documentation:

https://firebase.google.com/docs/projects/billing/firebase-pricing-plans

https://firebase.google.com/docs/firestore/quotas

https://firebase.google.com/docs/hosting/usage-quotas-pricing

Do not enable paid billing automatically.

If an implementation requires Cloud Functions or other Blaze-only resources, inform the owner and explain the cost implication before proceeding.

---

# 23. LOCAL DEVELOPMENT ENVIRONMENT

The owner will install:

1. Node.js LTS: https://nodejs.org/
2. Git: https://git-scm.com/
3. Visual Studio Code: https://code.visualstudio.com/
4. Kilo Code: https://kilo.ai/
5. Firebase CLI: https://firebase.google.com/docs/cli

GitHub repository:

https://github.com/

Suggested repository name:

```text
garment-factory-os
```

## Initial project structure

Recommended:

```text
garment-factory-os/
│
├── public/
│   ├── icons/
│   ├── manifest.webmanifest
│   └── favicon.ico
│
├── src/
│   ├── app/
│   │   ├── App.tsx
│   │   ├── routes.tsx
│   │   └── providers.tsx
│   │
│   ├── components/
│   │   ├── layout/
│   │   ├── forms/
│   │   ├── tables/
│   │   ├── scanner/
│   │   └── charts/
│   │
│   ├── features/
│   │   ├── authentication/
│   │   ├── employees/
│   │   ├── machines/
│   │   ├── products/
│   │   ├── operations/
│   │   ├── inventory/
│   │   ├── cutting/
│   │   ├── allocations/
│   │   ├── production/
│   │   ├── quality/
│   │   ├── attendance/
│   │   ├── costing/
│   │   ├── analytics/
│   │   └── ai-assistant/
│   │
│   ├── lib/
│   │   ├── firebase.ts
│   │   ├── auth.ts
│   │   ├── firestore.ts
│   │   └── scanner.ts
│   │
│   ├── services/
│   ├── hooks/
│   ├── types/
│   ├── utils/
│   ├── validations/
│   └── styles/
│
├── docs/
│   ├── PROJECT_HANDOVER.md
│   ├── DATABASE_SCHEMA.md
│   ├── BUSINESS_RULES.md
│   └── DEPLOYMENT.md
│
├── tests/
│
├── .env.example
├── .gitignore
├── firebase.json
├── firestore.rules
├── firestore.indexes.json
├── package.json
├── package-lock.json
├── tsconfig.json
├── vite.config.ts
└── README.md
```

The precise structure can evolve, but business logic must remain modular.

## Local environment configuration

Create `.env.local` on the owner's machine.

Example:

```env
VITE_FIREBASE_API_KEY=
VITE_FIREBASE_AUTH_DOMAIN=
VITE_FIREBASE_PROJECT_ID=
VITE_FIREBASE_STORAGE_BUCKET=
VITE_FIREBASE_MESSAGING_SENDER_ID=
VITE_FIREBASE_APP_ID=
```

Never commit `.env.local`.

Create `.env.example` with placeholders only.

Never include Firebase Admin service-account credentials in browser-side variables.

Kilo Code must not read, print or transmit service-account private keys or other secret files.

---

# 24. DEPLOYMENT PROCESS

Use Firebase CLI.

Install:

```bash
npm install -g firebase-tools
```

Authenticate:

```bash
firebase login
```

Initial Firebase project setup:

```bash
firebase init
```

Choose Hosting and Firestore configuration.

For a Vite production build:

```bash
npm install
npm run build
```

The Vite output directory is normally:

```text
dist/
```

Deploy:

```bash
firebase deploy --only hosting
```

The production application will be available through the Firebase Hosting domain.

The developer agent should prepare Firebase configuration files and explain each command before executing deployment.

Production deployment should only happen after tests and an owner review.

---

# 25. DATA BACKUP AND EXPORT

The application must provide an administrative export function.

Support CSV/JSON exports for:

- Employees.
- Machines.
- Products.
- BOMs.
- Operation templates.
- Cutting batches.
- Component bundles.
- Stock movements.
- Allocations.
- Production transactions.
- Attendance.
- Labour-cost ledgers.

Provide:

- Daily export.
- Date-range export.
- Full master-data export.

Do not assume that Firestore managed backup and restore are available at no cost. These have separate billing requirements.

Maintain periodic downloadable backups outside the Firebase project.

Do not rely solely on Google Sheets as the primary database.

---

# 26. IMPORTANT BUSINESS RULES

The following rules must be implemented consistently.

1. Only the supervisor records production activity.
2. Only the supervisor scans employee and machine QR codes.
3. Employee and machine QR identifiers are permanent.
4. Cutting batch is the parent of all component bundles.
5. Component bundles are created automatically from BOM quantities.
6. Bundle quantities must retain explicit units.
7. All component splitting and merging must preserve lineage.
8. No stock issue can exceed available quantity.
9. Production completion must reconcile issued, accepted, rejected, rework and returned quantities.
10. Employee production value must use the applicable rate snapshot.
11. Historical production values must not change when master rates change.
12. Reworked items must not be counted twice.
13. Employee production value must not be confused with revenue or profit.
14. Helper output must not duplicate operator production value.
15. Supervisor labour cost must be included in order-level cost calculations.
16. Material shortages and machine breakdowns must be distinguished from employee downtime.
17. All manual adjustments must record who made them and why.
18. Payroll penalties must not be automatically imposed based on internal productivity figures.
19. AI must not independently change inventory, production or payroll.
20. All important business records must remain exportable.

---

# 27. QUALITY ASSURANCE AND ACCEPTANCE TESTS

Kilo Code must write tests for the business rules.

## Employee and QR tests

- Employee QR identifies the correct employee.
- Inactive employee cannot receive an allocation.
- Unknown QR displays a useful error.
- Duplicate allocation is prevented where prohibited.

## Machine tests

- Machine QR identifies the correct machine.
- Inactive machine cannot receive an allocation.
- Incompatible operation is blocked.

## Cutting and BOM tests

Given 25 full-sleeve shirts:

- Create one parent cutting batch.
- Generate BOM component requirements.
- Generate component-bundle IDs.
- Verify component quantities against the BOM.
- Preserve separate units of measurement.

Test full-sleeve and half-sleeve variants independently.

## Bundle tests

Given 25 collars:

- Allocate 10.
- Return 3 unprocessed.
- Complete 12.
- Reject 0.
- Leave 0 pending.

Reconcile the total:

```text
25 = 10 originally issued

10 = 12 accepted + 3 returned
```

The correct example for that reconciliation is:

```text
25 originally available
10 issued
12 cannot be completed from 10 issued
```

Therefore the test must instead use a valid quantity set, for example:

```text
25 originally issued

22 accepted
2 rework
1 rejected

22 + 2 + 1 = 25
```

All quantities must reconcile exactly.

## Stock tests

- Prevent negative stock.
- Prevent duplicate issuance.
- Prevent double consumption.
- Preserve parent-child bundle relationships.
- Record every stock movement.
- Reconcile stock ledger to available balances.

## Labour-cost tests

Given:

```text
Daily salary = ₹200

Collar accepted = 40
Collar rate = ₹2.50

Sleeve accepted = 50
Sleeve rate = ₹1.20

Pocket accepted = 10
Pocket rate = ₹1.50
```

Expected production value:

```text
₹100 + ₹60 + ₹15 = ₹175
```

Expected salary recovery:

```text
87.5%
```

The automated test must validate both values.

## Security tests

- Unauthenticated users cannot access Firestore.
- Unauthorised Google accounts cannot log in to the protected application.
- Operators cannot access the application through employee QR IDs.
- No unrestricted write rules are used.
- Payroll data is accessible only to authorised roles.

## PWA tests

- Installable on Android.
- Camera permission works.
- QR scanning works over HTTPS.
- Application survives page refresh.
- Offline status is visible.
- Offline stock-changing transactions are not falsely marked as committed.
- Duplicate submissions are detected.

---

# 28. FUTURE ENHANCEMENTS

Do not build these before the core workflow is reliable.

Potential future additions:

1. Biometric attendance device API integration.
2. ESP32 machine activity sensors.
3. AI camera-based workstation occupancy.
4. Machine utilisation analytics.
5. Computer vision quality inspection.
6. Automated garment counting at inspection stations.
7. Fabric consumption and wastage tracking.
8. Accessory inventory.
9. Electricity consumption tracking.
10. Order profitability analytics.
11. Production scheduling.
12. Predictive bottleneck analysis.
13. Multi-factory and multi-supervisor support.
14. Native Android packaging.
15. Supplier and purchase management.
16. Customer order management.

AI camera analytics must be implemented with appropriate employee notice, restricted access to recordings, retention rules and privacy controls.

AI detection must not automatically determine misconduct or apply salary penalties.

---

# 29. FIRST DEVELOPMENT TASK FOR KILO CODE

Kilo Code must read the entire PROJECT_HANDOVER.md before making code changes.

Use the following initial task prompt.

## Kilo Code initial prompt

You are the lead full-stack engineer responsible for developing Garment OS.

Read PROJECT_HANDOVER.md completely.

This application is a real garment factory management system. Business accuracy, inventory traceability and financial correctness are more important than quickly generating a large number of screens.

Your first task is NOT to develop the entire application.

First:

1. Analyse the requirements.
2. Identify missing business decisions.
3. Propose the final frontend and Firebase architecture.
4. Design the Firestore schema.
5. Define TypeScript interfaces for all major business entities.
6. Define the business calculation modules.
7. Define Firestore security rules.
8. Identify which functionality can work on the Firebase Spark plan.
9. Identify any functionality requiring Blaze billing or paid APIs.
10. Produce a detailed implementation plan.

After reviewing the architecture, create the application foundation:

- React.
- TypeScript.
- Vite.
- Tailwind CSS.
- PWA configuration.
- Firebase initialisation.
- Firebase Authentication.
- Protected application routes.
- Mobile-first application shell.
- Supervisor dashboard placeholder.
- QR scanner component.
- Firestore service layer.

Do not invent production operation rates.

Do not assume that each sleeve equals one panel or one pair.

Do not hardcode garment construction rules.

All product components, units, BOM quantities, operations, rates and dependencies must be configurable.

All inventory transactions must maintain traceability.

All financial calculations must be deterministic, testable and independent of AI.

All sensitive operations must be auditable.

Do not use a Firebase service-account credential in frontend code.

Do not create publicly readable or publicly writable Firestore collections.

Do not enable billing or paid services without the owner's explicit approval.

Start by producing the architecture plan and Firestore data model for review. Wait for approval before making large-scale code changes.

---

# 30. REFERENCES AND OFFICIAL DOCUMENTATION

Kilo Code:
https://kilo.ai/

Kilo Code documentation:
https://kilo.ai/docs/

Kilo Code free model options:
https://kilo.ai/docs/getting-started/using-kilo-for-free

Kilo Code AI provider configuration:
https://kilo.ai/docs/getting-started/setup-authentication

Firebase:
https://firebase.google.com/

Firebase Authentication:
https://firebase.google.com/docs/auth

Cloud Firestore:
https://firebase.google.com/docs/firestore

Firestore security rules:
https://firebase.google.com/docs/firestore/security/get-started

Firebase Hosting:
https://firebase.google.com/docs/hosting

Firebase pricing:
https://firebase.google.com/docs/projects/billing/firebase-pricing-plans

Firestore quotas:
https://firebase.google.com/docs/firestore/quotas

Firebase AI Logic:
https://firebase.google.com/docs/ai-logic

Firebase AI Logic web SDK:
https://firebase.google.com/docs/ai-logic/get-started?api=web

Vite:
https://vite.dev/

React:
https://react.dev/

ZXing:
https://github.com/zxing-js/browser

PWA:
https://web.dev/learn/pwa/

---

# END OF PROJECT HANDOVER

## Project success definition

The first usable release should allow one supervisor to:

1. Log in securely.
2. Register employees and machines.
3. Generate and print employee and machine QR codes.
4. Create formal-shirt products and variants.
5. Configure reusable manufacturing operations.
6. Configure operation rates.
7. Create cutting orders and batches.
8. Automatically generate component bundles.
9. Allocate components to employees through QR scanning.
10. Record accepted, rejected, rework and returned quantities.
11. Track all stock movements.
12. Calculate employee production value.
13. Compare production value with daily salary cost.
14. See production bottlenecks.
15. Export daily production and labour-cost reports.

**The long-term objective is to have complete financial and operational visibility of every garment, employee, machine, component and production order.**
