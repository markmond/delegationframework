# Notation Guidelines and Examples for Domain-Specific Language for Delegation

## Introduction

This document provides comprehensive guidelines and examples for the notation used in the Domain-Specific Language for Delegation (DSLD). These standards ensure consistency, clarity, and effective communication when writing delegation scripts across your organization.

## Basic Notation Principles

### 1. Readability First
- Write delegation scripts that are readable by both humans and machines
- Use clear language and consistent formatting
- Avoid ambiguity in task descriptions and assignments

### 2. Structure and Layout
- Use proper indentation (2 or 4 spaces) for nested elements
- Group related commands together
- Include empty lines between different tasks or sections

### 3. Naming Conventions
- Use descriptive names for tasks, roles, and workflows
- For multi-word identifiers, use either camelCase or snake_case consistently
- Be specific and concise in naming

## Core Notation Elements

### Task Definition

Tasks are the fundamental unit of delegation and should be defined with clear intent.

**Syntax:**
```
TASK "descriptive_task_name"
  [task properties...]
```

**Example:**
```
TASK "Prepare quarterly financial report"
  ASSIGN TO "Finance Manager"
  DEADLINE "2025-03-31"
  PRIORITY "High"
```

### Assignment Notation

The `ASSIGN TO` command specifies who is responsible for executing a task.

**Syntax:**
```
ASSIGN TO "actor_name"
```

Where `actor_name` can be:
- Individual person: "Jane Smith"
- Team or group: "Marketing Team"
- Role: "Project Manager"
- System or AI: "AI_Content_Generator"

**Examples:**
```
ASSIGN TO "Sales Director"
ASSIGN TO "UX Design Team"
ASSIGN TO "AI_Data_Analyzer"
```

### Deadline Notation

Deadlines must be clear and specific, using standardized formats.

**Syntax:**
```
DEADLINE "date_specification"
```

**Supported formats:**
- ISO date: `YYYY-MM-DD`
- Date and time: `YYYY-MM-DD HH:MM`
- Relative: `"In X days/weeks/months"`
- Recurring: `"Every Monday at 9 AM"`

**Examples:**
```
DEADLINE "2025-04-15"
DEADLINE "2025-04-15 14:30"
DEADLINE "In 3 days"
DEADLINE "Last day of every month"
```

## Advanced Notation

### Dependency Mapping

Dependencies establish prerequisites for task execution and should be clearly indicated.

**Syntax:**
```
DEPENDS_ON "prerequisite_task"
```

or for multiple dependencies:

```
DEPENDS_ON ["task1", "task2", "task3"]
```

**Example:**
```
TASK "Launch marketing campaign"
  ASSIGN TO "Marketing Team"
  DEPENDS_ON ["Approve campaign budget", "Finalize creative assets"]
```

### Escalation Paths

Escalation notation defines when and to whom issues should be elevated.

**Syntax:**
```
ESCALATE_IF "condition" TO "actor"
```

**Examples:**
```
ESCALATE_IF "Not completed within 2 days of deadline" TO "Department Head"
ESCALATE_IF "Budget exceeds $10,000" TO "Finance Director"
```

### Status Tracking

Status notation indicates the current state of a task and possible progress states.

**Syntax:**
```
STATUS "current_status"
STATUS_TRACKING ["state1", "state2", "state3"]
```

**Example:**
```
TASK "Review legal contract"
  STATUS "In Progress"
  STATUS_TRACKING ["Draft", "Under Review", "Approved", "Finalized"]
```

## Workflow and Sequence Notation

### Workflow Definition

Workflows represent a connected series of tasks forming a process.

**Syntax:**
```
WORKFLOW "workflow_name"
  STEP 1: "step_description" [properties]
  STEP 2: "step_description" [properties]
  ...
```

**Example:**
```
WORKFLOW "New Employee Onboarding"
  STEP 1: "Process paperwork" ASSIGN TO "HR Team"
  STEP 2: "Set up workstation" ASSIGN TO "IT Support"
  STEP 3: "Conduct orientation" ASSIGN TO "Department Manager"
  STEP 4: "Complete training" ASSIGN TO "Training Team"
```

### Execution Order

Define whether tasks can run simultaneously or must follow a specific sequence.

**Syntax:**
```
PARALLEL_EXECUTION ["task1", "task2", "task3"]
SEQUENTIAL_EXECUTION ["task1", "task2", "task3"]
```

**Example:**
```
TASK "Prepare product launch"
  PARALLEL_EXECUTION ["Update website", "Prepare press release", "Brief sales team"]
  SEQUENTIAL_EXECUTION ["Get executive approval", "Issue press release", "Launch product"]
```

## Conditional Logic Notation

### Basic Conditions

Conditions control task execution or assignment based on specified criteria.

**Syntax:**
```
IF "condition" THEN "action" [ELSE "alternative_action"]
```

**Example:**
```
TASK "Approve expense report"
  IF "Amount > $5,000" THEN "ASSIGN TO Finance Director" ELSE "ASSIGN TO Department Manager"
```

### Execution Conditions

Control whether a task should be executed based on specific conditions.

**Syntax:**
```
EXECUTE_IF "condition"
```

**Example:**
```
TASK "Conduct additional market research"
  EXECUTE_IF "Initial research results are inconclusive"
  ASSIGN TO "Research Team"
```

## RACI Matrix Notation

The RACI matrix defines roles in terms of Responsible, Accountable, Consulted, and Informed parties.

**Syntax:**
```
TASK "task_name"
  RESPONSIBLE "actor"
  ACCOUNTABLE "actor"
  CONSULTED ["actor1", "actor2"]
  INFORMED ["actor1", "actor2"]
```

**Example:**
```
TASK "Implement new CRM system"
  RESPONSIBLE "IT Implementation Team"
  ACCOUNTABLE "CIO"
  CONSULTED ["Sales Director", "Marketing Director", "Customer Service Manager"]
  INFORMED ["Executive Team", "All Department Heads"]
```

## Templates and Reusable Components

### Template Definition

Templates allow for reusable task patterns with placeholders.

**Syntax:**
```
TEMPLATE "template_name"
  TASK "task_description_with_{placeholder}"
  [properties with {placeholders}]
```

**Example:**
```
TEMPLATE "Monthly Report"
  TASK "Prepare {report_type} report"
  ASSIGN TO "{responsible_person}"
  DEADLINE "Last day of every month"
  CHECKINS "Weekly on Friday"
```

### Template Usage

Apply templates by filling in the required placeholders.

**Syntax:**
```
USE TEMPLATE "template_name"
  placeholder1 = "value1"
  placeholder2 = "value2"
```

**Example:**
```
USE TEMPLATE "Monthly Report"
  report_type = "Financial Performance"
  responsible_person = "Finance Analyst"
```

## AI and Automation Notation

### AI Task Assignment

When delegating to AI systems, include specific instructions.

**Syntax:**
```
TASK "task_name"
  ASSIGN TO "AI_System_Name"
  AI_PROMPT "detailed_instructions"
  [other properties]
```

**Example:**
```
TASK "Generate sales insights report"
  ASSIGN TO "AI_Analytics_Engine"
  AI_PROMPT "Analyze Q1 sales data to identify top-performing products, regional trends, and growth opportunities. Format as a 2-page executive summary with visual elements."
  DEADLINE "2025-04-05"
  REVIEW_BY "Sales Director"
```

### Human-in-the-Loop Controls

Ensure proper oversight for automated tasks.

**Syntax:**
```
REVIEW_BY "human_actor"
APPROVAL_REQUIRED_BY "human_actor"
```

**Example:**
```
TASK "Generate marketing email copy"
  ASSIGN TO "AI_Content_Generator" 
  REVIEW_BY "Marketing Specialist"
  APPROVAL_REQUIRED_BY "Marketing Manager"
```

## Security and Compliance Notation

### Confidentiality Markings

Indicate the sensitivity level of tasks and control access.

**Syntax:**
```
CONFIDENTIAL "Yes/No"
VISIBLE_TO ["actor1", "actor2"]
```

**Example:**
```
TASK "Review acquisition proposal"
  CONFIDENTIAL "Yes"
  VISIBLE_TO ["Executive Team", "Legal Counsel"]
  ASSIGN TO "CEO"
```

### Compliance Requirements

Specify regulatory frameworks that apply to a task.

**Syntax:**
```
MUST_COMPLY_WITH "regulation_or_policy"
```

**Example:**
```
TASK "Process customer payment information"
  ASSIGN TO "Finance Team"
  MUST_COMPLY_WITH "PCI DSS"
  MUST_COMPLY_WITH "Company Data Security Policy"
```

## Integration Notation

### External System Integration

Connect tasks to other tools and platforms.

**Syntax:**
```
SYNC_WITH "system_name" [CONNECTION_DETAILS "details"]
```

**Example:**
```
TASK "Fix software bug"
  ASSIGN TO "Development Team"
  SYNC_WITH "Jira" CONNECTION_DETAILS "Project: CORE, Issue Type: Bug"
```

### Notifications

Define how and when notifications should be sent.

**Syntax:**
```
NOTIFY "actor" VIA "channel" WHEN "event"
```

**Example:**
```
TASK "Review project proposal"
  ASSIGN TO "Project Committee"
  NOTIFY "Project Manager" VIA "Email" WHEN "Review completed"
  NOTIFY "Stakeholders" VIA "Slack_Channel: #project-updates" WHEN "Approved"
```

## Common Patterns and Examples

### Project Task Delegation

```
TASK "Design new product homepage"
  ASSIGN TO "UX Designer"
  DEADLINE "2025-03-15"
  DEPENDS_ON "Complete user research"
  CHECKINS "Bi-weekly on Tuesday"
  ESCALATE_IF "Not completed by March 10" TO "Design Director"
```

### Approval Workflow

```
WORKFLOW "Contract Approval Process"
  STEP 1: "Draft contract" ASSIGN TO "Legal Team"
  STEP 2: "Initial review" ASSIGN TO "Department Head"
  STEP 3: "Legal verification" ASSIGN TO "Legal Counsel"
  STEP 4: "Final approval" ASSIGN TO "CEO"
  STEP 5: "Contract signing" ASSIGN TO "Both Parties"
```

### AI-Assisted Task with Human Oversight

```
TASK "Generate quarterly business insights"
  ASSIGN TO "AI_Business_Analyzer"
  AI_PROMPT "Analyze Q1 2025 business performance data to identify key trends, risks, and opportunities. Include visualizations for the top 5 findings."
  CONTEXT "Q1 2025 financial reports, sales data, and market analysis"
  REVIEW_BY "Business Intelligence Team"
  APPROVAL_REQUIRED_BY "COO"
  DEADLINE "2025-04-10"
```

### Cross-Department Collaboration

```
TASK "Launch new product feature"
  RESPONSIBLE "Product Team"
  ACCOUNTABLE "Product Director"
  CONSULTED ["Engineering Team", "Marketing Team", "Sales Team"]
  INFORMED ["Customer Support", "Executive Team"]
  DEADLINE "2025-05-01"
  CHECKINS "Weekly status updates"
```

## Best Practices

1. **Be Specific**: Avoid vague task descriptions or ambiguous deadlines
2. **Use Consistent Formatting**: Adopt a single style throughout your organization
3. **Include Context**: Provide background information where helpful
4. **Define Clear Ownership**: Always specify who is responsible and accountable
5. **Set Realistic Deadlines**: Consider dependencies and resource availability
6. **Establish Escalation Paths**: Define what happens if tasks are delayed or blocked
7. **Document Assumptions**: Include relevant context that may affect task execution
8. **Review and Refine**: Regularly update templates and common patterns

## Common Mistakes to Avoid

1. **Overly Vague Descriptions**: "Update website" vs. "Update pricing page with new service tiers"
2. **Missing Dependencies**: Failing to specify which tasks must be completed first
3. **Unclear Ownership**: Not specifying who is ultimately responsible
4. **Unrealistic Deadlines**: Not accounting for dependencies or resource constraints
5. **Insufficient Context**: Omitting critical background information
6. **No Escalation Path**: Failing to define what happens if a task stalls
7. **Inconsistent Notation**: Mixing different styles and formats
8. **Overcomplicating Simple Tasks**: Adding unnecessary detail to straightforward work

## Appendix: Quick Reference

### Command Summary
| Command | Purpose | Example |
|---------|---------|---------|
| `TASK` | Define a unit of work | `TASK "Update website content"` |
| `ASSIGN TO` | Specify responsible actor | `ASSIGN TO "Content Team"` |
| `DEADLINE` | Set completion date/time | `DEADLINE "2025-03-31"` |
| `DEPENDS_ON` | Define prerequisites | `DEPENDS_ON "Approve content strategy"` |
| `ESCALATE_IF` | Set escalation criteria | `ESCALATE_IF "Delayed > 3 days" TO "Manager"` |
| `PRIORITY` | Indicate importance | `PRIORITY "High"` |
| `STATUS` | Current state | `STATUS "In Progress"` |
| `WORKFLOW` | Define process | `WORKFLOW "Customer Onboarding"` |
| `TEMPLATE` | Create reusable pattern | `TEMPLATE "Weekly Report"` |
| `CONFIDENTIAL` | Mark sensitivity | `CONFIDENTIAL "Yes"` |

### Status Values
- `Planned`
- `In Progress`
- `Blocked`
- `Completed`
- `Cancelled`

### Priority Levels
- `Critical`
- `High`
- `Medium`
- `Low`
