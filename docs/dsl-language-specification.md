# Domain-Specific Language for Delegation (DSLD)
## Complete Formal Language Specification v1.0

## Table of Contents

1. [Introduction](#1-introduction)
2. [Lexical Elements](#2-lexical-elements)
3. [Syntax Definition](#3-syntax-definition)
4. [Core Commands](#4-core-commands)
5. [Task Management](#5-task-management)
6. [Actor Management](#6-actor-management)
7. [Workflow Constructs](#7-workflow-constructs)
8. [Conditional Logic](#8-conditional-logic)
9. [Templates and Reusability](#9-templates-and-reusability)
10. [Integration Directives](#10-integration-directives)
11. [Security and Compliance](#11-security-and-compliance)
12. [AI and Automation](#12-ai-and-automation)
13. [Error Handling](#13-error-handling)
14. [Comments and Documentation](#14-comments-and-documentation)
15. [Examples](#15-examples)
16. [Appendix](#16-appendix)

---

## 1. Introduction

The Domain-Specific Language for Delegation (DSLD) is a formal language designed to express delegation instructions, workflows, and responsibilities in a structured, machine-readable format. The language serves as a standardized way to:

- Define tasks and their properties
- Assign responsibilities to humans, teams, or automated systems
- Express workflows, dependencies, and conditions
- Manage approvals, escalations, and notifications
- Support integration with various productivity and collaboration tools

This specification defines the syntax, semantics, and pragmatics of the language, serving as the definitive reference for implementers, users, and tool developers.

### 1.1 Design Principles

DSLD adheres to the following design principles:

1. **Clarity**: Constructs should be readable by both humans and machines
2. **Precision**: Instructions must be unambiguous and explicit
3. **Flexibility**: The language should accommodate various delegation scenarios
4. **Extensibility**: New constructs can be added without breaking existing scripts
5. **Integration**: Easy connection with existing tools and platforms

### 1.2 Versioning

This document specifies version 1.0 of the DSLD. Future versions will maintain backward compatibility unless explicitly noted.

---

## 2. Lexical Elements

### 2.1 Character Set

DSLD is defined using the UTF-8 character set, supporting international characters and symbols.

### 2.2 Keywords

The following keywords are reserved and cannot be used as identifiers:

```
TASK, ASSIGN, TO, DEADLINE, CHECKINS, ESCALATE, NOTIFY, IF, THEN, ELSE, WORKFLOW,
STEP, TEMPLATE, USE, PRIORITY, STATUS, CONSTRAINT, DEPENDS_ON, PARALLEL_EXECUTION,
SEQUENTIAL_EXECUTION, ROLE, CONFIDENTIAL, BUDGET_CAP, SCHEDULE, SLA, RACI, RESPONSIBLE,
ACCOUNTABLE, CONSULTED, INFORMED, TRIGGER_ON, EXECUTE_IF, AI_PROMPT, CONTEXT, FACT_CHECK
```

### 2.3 Identifiers

Identifiers name entities such as tasks, actors, or templates. They must begin with a letter and can contain letters, numbers, and underscores.

**Syntax:** `[a-zA-Z][a-zA-Z0-9_]*`

### 2.4 Strings

String literals are enclosed in double quotes and can contain any UTF-8 character. Escape sequences include:
- `\"` - double quote
- `\\` - backslash
- `\n` - newline
- `\t` - tab

**Syntax:** `"[^"\\]*(\\.[^"\\]*)*"`

### 2.5 Date and Time

Dates follow the ISO 8601 format: `YYYY-MM-DD`.
Times follow the format: `HH:MM[:SS]`.
Combined date-time follows: `YYYY-MM-DD[ T]HH:MM[:SS]`.

Relative dates and recurring schedules are also supported:
- `"Every Monday 9 AM"`
- `"Last day of every month"`
- `"In 3 days"`

### 2.6 Numbers

Integer values: `[0-9]+`
Decimal values: `[0-9]+\.[0-9]+`
Percentage values: `[0-9]+(\.[0-9]+)?%`

### 2.7 Lists

Lists are enclosed in square brackets and contain comma-separated values.

**Syntax:** `\[(value(, value)*)?]`

### 2.8 Whitespace and Comments

Whitespace (spaces, tabs, newlines) is generally insignificant except for readability.

Single-line comments begin with `//` and extend to the end of the line.
Multi-line comments are enclosed between `/*` and `*/`.

---

## 3. Syntax Definition

DSLD syntax is defined in Extended Backus-Naur Form (EBNF) notation.

### 3.1 Program Structure

```ebnf
Program ::= (Statement | Comment)*

Statement ::= TaskDefinition
           | WorkflowDefinition
           | TemplateDefinition
           | TemplateUse
           | RoleDefinition
           | ConfigStatement

Comment ::= '//' [^\n]* '\n'
         | '/*' .* '*/'
```

### 3.2 Task Definition

```ebnf
TaskDefinition ::= 'TASK' StringLiteral
                  TaskPropertyList

TaskPropertyList ::= (TaskProperty)*

TaskProperty ::= Assignment
               | Deadline
               | Checkins
               | Escalation
               | Notification
               | Status
               | Priority
               | Dependency
               | Constraint
               | Budget
               | Confidentiality
               | Other
```

---

## 4. Core Commands

### 4.1 Task Definition

The `TASK` command defines a unit of work to be delegated.

**Syntax:**
```
TASK "Task description"
[task properties...]
```

**Example:**
```
TASK "Write quarterly financial report"
ASSIGN TO "Finance Team"
DEADLINE "2025-04-15"
PRIORITY "High"
```

### 4.2 Assignment

The `ASSIGN TO` command specifies who or what is responsible for executing a task.

**Syntax:**
```
ASSIGN TO "Actor name"
```

**Example:**
```
ASSIGN TO "Marketing Team"
ASSIGN TO "AI_Content_Generator"
ASSIGN TO "John Smith"
```

### 4.3 Deadline

The `DEADLINE` command sets the due date or time for task completion.

**Syntax:**
```
DEADLINE "date/time specification"
```

**Example:**
```
DEADLINE "2025-03-31"
DEADLINE "Every Monday at 9 AM"
DEADLINE "Within 24 hours"
```

### 4.4 Status Tracking

The `STATUS` command defines the current state of a task.

**Syntax:**
```
STATUS "status value"
```

**Valid status values:** `"Planned"`, `"In Progress"`, `"Completed"`, `"Blocked"`, `"Cancelled"`, or custom values.

**Example:**
```
STATUS "In Progress"
STATUS_TRACKING ["Draft", "Review", "Approved", "Published"]
```

---

## 5. Task Management

### 5.1 Priority Levels

The `PRIORITY` command assigns importance to a task.

**Syntax:**
```
PRIORITY "priority level"
```

**Valid priority levels:** `"Critical"`, `"High"`, `"Medium"`, `"Low"`, or custom values.

**Example:**
```
PRIORITY "High"
```

### 5.2 Check-ins and Monitoring

The `CHECKINS` command defines regular updates or progress reporting requirements.

**Syntax:**
```
CHECKINS "frequency specification"
```

**Example:**
```
CHECKINS "Weekly on Friday"
CHECKINS "Daily status updates"
```

### 5.3 Dependencies

The `DEPENDS_ON` command establishes prerequisites for the current task.

**Syntax:**
```
DEPENDS_ON "task identifier"
DEPENDS_ON ["task1", "task2", ...]
```

**Example:**
```
DEPENDS_ON "Finalize budget"
DEPENDS_ON ["Research market trends", "Collect customer feedback"]
```

### 5.4 Escalation

The `ESCALATE_IF` command defines conditions for elevating task oversight.

**Syntax:**
```
ESCALATE_IF "condition" TO "actor"
```

**Example:**
```
ESCALATE_IF "Not completed within 3 days" TO "Department Manager"
ESCALATE_IF "Budget exceeded by 10%" TO "Finance Director"
```

### 5.5 Notifications

The `NOTIFY` command specifies communication requirements.

**Syntax:**
```
NOTIFY "actor" WHEN "event"
```

**Example:**
```
NOTIFY "Project Manager" WHEN "Task completed"
NOTIFY ["Marketing Team", "Sales Director"] WHEN "Campaign ready for review"
```

---

## 6. Actor Management

### 6.1 Actor Types

Actors can be individuals, groups, systems, or roles.

**Syntax:**
```
ASSIGN TO "Actor"
```

### 6.2 Role Definition

The `ROLE` command defines responsibilities that can be referenced across tasks.

**Syntax:**
```
ROLE "role name" DESCRIPTION "responsibilities"
```

**Example:**
```
ROLE "Project Sponsor" DESCRIPTION "Provides resources and executive support"
```

### 6.3 RACI Matrix

The RACI commands explicitly define the Responsible, Accountable, Consulted, and Informed roles.

**Syntax:**
```
RESPONSIBLE "actor"
ACCOUNTABLE "actor"
CONSULTED ["actor1", "actor2", ...]
INFORMED ["actor1", "actor2", ...]
```

**Example:**
```
TASK "Approve new marketing strategy"
RESPONSIBLE "Marketing Director"
ACCOUNTABLE "CMO"
CONSULTED ["Sales Director", "Product Manager"]
INFORMED ["Marketing Team", "Executive Committee"]
```

### 6.4 Autonomy Levels

The `AUTONOMY_LEVEL` command specifies the degree of independence.

**Syntax:**
```
AUTONOMY_LEVEL "level"
```

**Valid levels:** `"High"`, `"Medium"`, `"Low"`

**Example:**
```
TASK "Design new product feature"
ASSIGN TO "Senior Engineer"
AUTONOMY_LEVEL "High"
```

---

## 7. Workflow Constructs

### 7.1 Workflow Definition

The `WORKFLOW` command defines a sequence of related tasks.

**Syntax:**
```
WORKFLOW "workflow name"
[step definitions...]
```

**Example:**
```
WORKFLOW "New Product Launch"
STEP 1: "Product development" ASSIGN TO "Engineering Team"
STEP 2: "Quality assurance" ASSIGN TO "QA Team"
STEP 3: "Marketing preparation" ASSIGN TO "Marketing Team"
STEP 4: "Launch event" ASSIGN TO "Events Team"
```

### 7.2 Parallel vs. Sequential Execution

The `PARALLEL_EXECUTION` and `SEQUENTIAL_EXECUTION` commands define task ordering.

**Syntax:**
```
PARALLEL_EXECUTION ["task1", "task2", ...]
SEQUENTIAL_EXECUTION ["task1", "task2", ...]
```

**Example:**
```
PARALLEL_EXECUTION ["Develop website", "Create marketing materials"]
SEQUENTIAL_EXECUTION ["Research", "Design", "Implementation", "Testing"]
```

### 7.3 Event-Driven Execution

The `TRIGGER_ON` command initiates a task based on an event.

**Syntax:**
```
TRIGGER_ON "event"
```

**Example:**
```
TASK "Send follow-up email"
ASSIGN TO "CRM_System"
TRIGGER_ON "Customer support ticket closed"
```

---

## 8. Conditional Logic

### 8.1 Basic Conditions

The `IF-THEN-ELSE` construct implements conditional logic.

**Syntax:**
```
IF "condition" THEN "action" [ELSE "alternative action"]
```

**Example:**
```
IF "Budget request > $10,000" THEN "Assign to Finance Director" ELSE "Assign to Department Manager"
```

### 8.2 Execution Conditions

The `EXECUTE_IF` command makes task execution conditional.

**Syntax:**
```
EXECUTE_IF "condition"
```

**Example:**
```
TASK "Run additional market research"
EXECUTE_IF "Initial response rate < 30%"
```

### 8.3 Complex Conditions

Logical operators can create compound conditions.

**Syntax:**
```
IF "condition1 AND condition2" THEN "action"
IF "condition1 OR condition2" THEN "action"
IF "NOT condition" THEN "action"
```

**Example:**
```
IF "Deadline approaching AND Progress < 50%" THEN "Escalate to Manager"
```

---

## 9. Templates and Reusability

### 9.1 Template Definition

The `TEMPLATE` command creates reusable task patterns.

**Syntax:**
```
TEMPLATE "template name"
[task definition with placeholders]
```

**Example:**
```
TEMPLATE "Monthly Report"
TASK "Generate {report_name}"
ASSIGN TO "{responsible_team}"
DEADLINE "Last day of every month"
CHECKINS "Weekly progress updates"
```

### 9.2 Template Usage

The `USE TEMPLATE` command applies a template with specific values.

**Syntax:**
```
USE TEMPLATE "template name"
parameter1 = "value1"
parameter2 = "value2"
...
```

**Example:**
```
USE TEMPLATE "Monthly Report"
report_name = "Sales Performance Report"
responsible_team = "Sales Analytics Team"
```

### 9.3 Inheritance and Extension

Templates can extend other templates.

**Syntax:**
```
TEMPLATE "specialized template" EXTENDS "base template"
[additional or overriding properties]
```

**Example:**
```
TEMPLATE "Financial Report" EXTENDS "Monthly Report"
CONFIDENTIAL "Yes"
APPROVAL_REQUIRED_BY "CFO"
```

---

## 10. Integration Directives

### 10.1 Tool Integration

The `SYNC_WITH` command connects tasks with external tools.

**Syntax:**
```
SYNC_WITH "external system" [CONNECTION_DETAILS "details"]
```

**Example:**
```
TASK "Fix software bug"
ASSIGN TO "Development Team"
SYNC_WITH "Jira" CONNECTION_DETAILS "Project: CORE, Type: Bug"
```

### 10.2 Notifications and Alerts

The `NOTIFY` command can target specific platforms.

**Syntax:**
```
NOTIFY "actor" VIA "channel" WHEN "event"
```

**Example:**
```
NOTIFY "Marketing Team" VIA "Slack_Channel: #marketing" WHEN "Campaign approved"
```

### 10.3 Calendar Integration

The `ADD_TO_CALENDAR` command ensures visibility in scheduling tools.

**Syntax:**
```
ADD_TO_CALENDAR "calendar name" [OPTIONS "options"]
```

**Example:**
```
TASK "Quarterly planning meeting"
SCHEDULE "2025-04-01 13:00"
ADD_TO_CALENDAR "Company-wide" OPTIONS "Reminder: 1 day before"
```

---

## 11. Security and Compliance

### 11.1. Confidentiality

The `CONFIDENTIAL` command marks sensitive tasks.

**Syntax:**
```
CONFIDENTIAL "Yes/No"
```

**Example:**
```
TASK "Review acquisition proposal"
CONFIDENTIAL "Yes"
VISIBLE_TO ["Executive Team", "Legal Counsel"]
```

### 11.2. Access Control

The `VISIBLE_TO` and `EDIT_RIGHTS` commands manage task permissions.

**Syntax:**
```
VISIBLE_TO ["actor1", "actor2", ...]
EDIT_RIGHTS ["actor1", "actor2", ...]
```

**Example:**
```
TASK "Update salary information"
ASSIGN TO "HR Manager"
VISIBLE_TO ["HR Team", "Finance Director"]
EDIT_RIGHTS ["HR Director"]
```

### 11.3. Compliance Requirements

The `MUST_COMPLY_WITH` command links tasks to regulatory standards.

**Syntax:**
```
MUST_COMPLY_WITH "compliance standard"
```

**Example:**
```
TASK "Process customer data"
MUST_COMPLY_WITH "GDPR"
REQUIRES_SIGN_OFF_BY "Data Protection Officer"
```

### 11.4. Audit Trails

The `LOG_HISTORY` command ensures all changes are recorded.

**Syntax:**
```
LOG_HISTORY "detail level"
```

**Valid levels:** `"Basic"`, `"Detailed"`, `"Complete"`

**Example:**
```
TASK "Approve vendor payment"
LOG_HISTORY "Complete"
```

---

## 12. AI and Automation

### 12.1. AI Task Assignment

Syntax for delegating to AI systems.

**Syntax:**
```
ASSIGN TO "AI_System_Name"
```

**Example:**
```
TASK "Generate monthly sales report"
ASSIGN TO "AI_Analytics_Service"
DEADLINE "1st day of each month"
```

### 12.2. Prompt Engineering

The `AI_PROMPT` command provides specific instructions to AI systems.

**Syntax:**
```
AI_PROMPT "detailed instructions"
```

**Example:**
```
TASK "Draft blog post"
ASSIGN TO "AI_Content_Generator"
AI_PROMPT "Write a 1000-word article about workspace efficiency. Include statistics, practical tips, and a conversational tone."
REVIEW_BY "Content Manager"
```

### 12.3. Context Provision

The `CONTEXT` command supplies background information.

**Syntax:**
```
CONTEXT "relevant background information"
```

**Example:**
```
TASK "Analyze customer feedback"
ASSIGN TO "AI_Sentiment_Analyzer"
CONTEXT "Focus on product usability issues mentioned in Q2 surveys"
```

### 12.4. Human-in-the-Loop

The `REVIEW_BY` and `APPROVAL_REQUIRED_BY` commands ensure human oversight.

**Syntax:**
```
REVIEW_BY "actor"
APPROVAL_REQUIRED_BY "actor"
```

**Example:**
```
TASK "Generate marketing copy"
ASSIGN TO "AI_Copywriter"
REVIEW_BY "Brand Manager"
APPROVAL_REQUIRED_BY "Marketing Director"
```

### 12.5. Fact-Checking

The `FACT_CHECK` command verifies AI outputs against trusted sources.

**Syntax:**
```
FACT_CHECK "reference source"
```

**Example:**
```
TASK "Create product specifications"
ASSIGN TO "AI_Technical_Writer"
FACT_CHECK "Official product documentation"
```

---

## 13. Error Handling

### 13.1. Retry Logic

The `RETRY_IF` command handles temporary failures.

**Syntax:**
```
RETRY_IF "condition" UP_TO "limit"
```

**Example:**
```
TASK "Send email campaign"
ASSIGN TO "Marketing_Automation"
RETRY_IF "Delivery failure" UP_TO "3 times"
```

### 13.2. Fallback Mechanisms

The `FALLBACK` command defines alternative paths if a task fails.

**Syntax:**
```
FALLBACK "alternative action"
```

**Example:**
```
TASK "Automated data import"
ASSIGN TO "ETL_System"
FALLBACK "Assign to Data Analyst for manual processing"
```

### 13.3. Error Notifications

Specific error alerts can be defined.

**Syntax:**
```
NOTIFY_ON_ERROR "actor" [WITH_DETAILS "detail level"]
```

**Example:**
```
TASK "Process customer payments"
NOTIFY_ON_ERROR "Finance Team" WITH_DETAILS "Complete"
```

---

## 14. Comments and Documentation

### 14.1 Single Line Comments

Single line comments start with `//` and continue to the end of the line.

**Example:**
```
// This task is critical for the quarterly review
TASK "Prepare financial summary"
```

### 14.2 Multi-Line Comments

Multi-line comments are enclosed between `/*` and `*/`.

**Example:**
```
/* 
This workflow handles the entire approval process
for new marketing campaigns with a budget over $50,000
*/
WORKFLOW "High-Budget Campaign Approval"
```

### 14.3 Documentation Tags

Special tags provide structured documentation.

**Syntax:**
```
// @tag: information
```

**Supported tags:** `@author`, `@version`, `@purpose`, `@example`, `@see`

**Example:**
```
// @author: Finance Team
// @version: 1.2
// @purpose: Ensure timely payment of vendor invoices
TASK "Process vendor invoices"
```

---

## 15. Examples

### 15.1 Basic Task Assignment

```
TASK "Review quarterly financial report"
ASSIGN TO "Finance Manager"
DEADLINE "2025-04-15"
PRIORITY "High"
```

### 15.2 Task with Dependencies and Escalation

```
TASK "Finalize marketing campaign"
ASSIGN TO "Marketing Team"
DEADLINE "2025-03-20"
DEPENDS_ON ["Approve campaign budget", "Complete creative assets"]
ESCALATE_IF "Not completed by March 15" TO "Marketing Director"
```

### 15.3 Complex Workflow

```
WORKFLOW "New Product Launch"
STEP 1: "Market research" ASSIGN TO "Research Team"
STEP 2: "Product development" ASSIGN TO "Engineering Team"
STEP 3: "Quality testing" ASSIGN TO "QA Team"
STEP 4: "Marketing preparation" ASSIGN TO "Marketing Team"
PARALLEL_EXECUTION ["Create documentation", "Prepare sales materials"]
STEP 5: "Sales training" ASSIGN TO "Training Team"
DEPENDS_ON "Marketing preparation"
STEP 6: "Product launch" ASSIGN TO "Product Manager"
DEPENDS_ON ["Quality testing", "Sales training"]
```

### 15.4 Template Definition and Usage

```
TEMPLATE "Monthly Report"
TASK "Prepare {report_type} report for {department}"
ASSIGN TO "{responsible_person}"
DEADLINE "Last day of every month"
CHECKINS "Weekly on Friday"

USE TEMPLATE "Monthly Report"
report_type = "Financial"
department = "Sales"
responsible_person = "Finance Analyst"
```

### 15.5 AI Task Delegation

```
TASK "Generate customer insights report"
ASSIGN TO "AI_Analytics_Engine"
CONTEXT "Q2 customer survey data and purchase history"
AI_PROMPT "Analyze trends in customer satisfaction and purchasing patterns, highlighting top 3 action items"
REVIEW_BY "Customer Success Manager"
DEADLINE "2025-05-01"
```

---

## 16. Appendix

### 16.1 Reserved Keywords

Complete list of all reserved keywords in the language.

### 16.2 Common Error Messages

Standard errors that implementations should support.

### 16.3 Best Practices

Guidelines for effective use of the language.

### 16.4 Implementation Notes

Technical considerations for parser and interpreter development.

### 16.5 Version History

Changes and additions across language versions.

### 16.6 References

Related standards, languages, and resources.

---

© 2025 DSLD Working Group. This specification is available under the Creative Commons Attribution 4.0 International License.
