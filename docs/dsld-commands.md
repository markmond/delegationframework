# Domain-Specific Language for Delegation (DSLD)
## Key Commands Reference Sheet

This quick reference guide provides essential commands and syntax for the Domain-Specific Language for Delegation.

---

## Core Commands

| Command | Purpose | Example |
|---------|---------|---------|
| `TASK` | Define a unit of work | `TASK "Write quarterly report"` |
| `ASSIGN TO` | Specify who/what executes the task | `ASSIGN TO "Marketing Team"` |
| `DEADLINE` | Set due date/time | `DEADLINE "2025-04-15"` |
| `PRIORITY` | Set task importance | `PRIORITY "High"` |
| `STATUS` | Define current task state | `STATUS "In Progress"` |
| `CHECKINS` | Specify update frequency | `CHECKINS "Weekly on Friday"` |

## Dependencies & Workflows

| Command | Purpose | Example |
|---------|---------|---------|
| `DEPENDS_ON` | Define prerequisites | `DEPENDS_ON ["Task1", "Task2"]` |
| `WORKFLOW` | Define sequence of related tasks | `WORKFLOW "Product Launch"` |
| `STEP` | Define workflow stage | `STEP 1: "Research" ASSIGN TO "Team"` |
| `PARALLEL_EXECUTION` | Execute tasks simultaneously | `PARALLEL_EXECUTION ["Task1", "Task2"]` |
| `SEQUENTIAL_EXECUTION` | Execute tasks in order | `SEQUENTIAL_EXECUTION ["Task1", "Task2"]` |
| `TRIGGER_ON` | Start task based on event | `TRIGGER_ON "Form submission"` |

## Escalation & Notification

| Command | Purpose | Example |
|---------|---------|---------|
| `ESCALATE_IF` | Define when to elevate issues | `ESCALATE_IF "Overdue by 2 days" TO "Manager"` |
| `NOTIFY` | Specify who to inform | `NOTIFY "Stakeholders" WHEN "Completed"` |
| `NOTIFY_ON_ERROR` | Alert on failures | `NOTIFY_ON_ERROR "Support Team"` |

## Conditional Logic

| Command | Purpose | Example |
|---------|---------|---------|
| `IF...THEN...ELSE` | Implement conditions | `IF "Budget > $10k" THEN "Assign to Director"` |
| `EXECUTE_IF` | Make task execution conditional | `EXECUTE_IF "User count > 1000"` |

## Templates & Reusability

| Command | Purpose | Example |
|---------|---------|---------|
| `TEMPLATE` | Create reusable task pattern | `TEMPLATE "Monthly Report"` |
| `USE TEMPLATE` | Apply template with values | `USE TEMPLATE "Monthly Report"` |
| `EXTENDS` | Inherit from another template | `TEMPLATE "Financial" EXTENDS "Report"` |

## Role Management

| Command | Purpose | Example |
|---------|---------|---------|
| `ROLE` | Define responsibilities | `ROLE "Approver" DESCRIPTION "..."` |
| `RESPONSIBLE` | Define task executor | `RESPONSIBLE "Team Lead"` |
| `ACCOUNTABLE` | Define decision maker | `ACCOUNTABLE "Department Head"` |
| `CONSULTED` | Define advisors | `CONSULTED ["Expert1", "Expert2"]` |
| `INFORMED` | Define who to keep updated | `INFORMED ["Stakeholders"]` |
| `AUTONOMY_LEVEL` | Set independence level | `AUTONOMY_LEVEL "High"` |

## Security & Compliance

| Command | Purpose | Example |
|---------|---------|---------|
| `CONFIDENTIAL` | Mark sensitive tasks | `CONFIDENTIAL "Yes"` |
| `VISIBLE_TO` | Restrict task visibility | `VISIBLE_TO ["HR", "Finance"]` |
| `EDIT_RIGHTS` | Control task modification | `EDIT_RIGHTS ["Managers"]` |
| `MUST_COMPLY_WITH` | Link to standards | `MUST_COMPLY_WITH "GDPR"` |
| `LOG_HISTORY` | Track all changes | `LOG_HISTORY "Complete"` |

## AI & Automation

| Command | Purpose | Example |
|---------|---------|---------|
| `AI_PROMPT` | Instructions for AI systems | `AI_PROMPT "Summarize findings..."` |
| `CONTEXT` | Provide background info | `CONTEXT "Previous research data"` |
| `REVIEW_BY` | Require human oversight | `REVIEW_BY "Senior Manager"` |
| `FACT_CHECK` | Verify against sources | `FACT_CHECK "Company database"` |

## Error Handling

| Command | Purpose | Example |
|---------|---------|---------|
| `RETRY_IF` | Handle temporary failures | `RETRY_IF "Connection fails" UP_TO "3 times"` |
| `FALLBACK` | Define alternative actions | `FALLBACK "Assign to human operator"` |

## Integration

| Command | Purpose | Example |
|---------|---------|---------|
| `SYNC_WITH` | Connect with external tools | `SYNC_WITH "Jira" CONNECTION_DETAILS "..."` |
| `ADD_TO_CALENDAR` | Create calendar entries | `ADD_TO_CALENDAR "Team Calendar"` |

---

## Common Syntax Patterns

- **String values**: Enclosed in double quotes `"like this"`
- **Lists**: Enclosed in square brackets with commas `["item1", "item2"]`
- **Comments**: Single line `// Comment` or multi-line `/* Comment */`
- **Dates**: ISO format `YYYY-MM-DD` or descriptive `"Every Monday"`

## Best Practices

1. Give tasks clear, specific descriptions
2. Use consistent naming conventions
3. Define explicit dependencies
4. Include reasonable deadlines and escalation paths
5. Add comments for complex workflows
6. Use templates for recurring task patterns

---

*For the complete language specification, refer to the DSLD Documentation.*
