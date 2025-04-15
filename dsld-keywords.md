# Domain-Specific Language for Delegation (DSLD)
## Reserved Keywords and Their Functions

This document provides a comprehensive reference of all reserved keywords in the Domain-Specific Language for Delegation, explaining their purpose, syntax, and usage. These keywords form the foundation of the language and cannot be used as identifiers.

## Task Definition and Management

| Keyword | Function | Example Usage |
|---------|----------|---------------|
| `TASK` | Defines a unit of work to be delegated | `TASK "Complete quarterly report"` |
| `DEADLINE` | Specifies when a task must be completed | `DEADLINE "2025-03-15"` |
| `PRIORITY` | Indicates the importance level of a task | `PRIORITY "High"` |
| `STATUS` | Marks the current state of a task | `STATUS "In Progress"` |
| `STATUS_TRACKING` | Defines possible states for a task | `STATUS_TRACKING ["Draft", "Review", "Approved"]` |
| `DEPENDS_ON` | Establishes prerequisites for a task | `DEPENDS_ON "Collect data"` |
| `CHECKINS` | Defines frequency of progress updates | `CHECKINS "Weekly on Friday"` |

## Assignment and Responsibility

| Keyword | Function | Example Usage |
|---------|----------|---------------|
| `ASSIGN` | Used with TO to delegate a task | `ASSIGN TO "Marketing Team"` |
| `TO` | Used with ASSIGN to specify recipient | `ASSIGN TO "John Smith"` |
| `RESPONSIBLE` | Designates who performs the actual work | `RESPONSIBLE "Project Manager"` |
| `ACCOUNTABLE` | Identifies who has final authority/approval | `ACCOUNTABLE "Department Director"` |
| `CONSULTED` | Lists those who provide input | `CONSULTED ["Legal", "Finance"]` |
| `INFORMED` | Specifies who should be kept updated | `INFORMED ["Executive Team"]` |
| `ROLE` | Defines a standard set of responsibilities | `ROLE "Approver" DESCRIPTION "Reviews and approves work"` |
| `AUTONOMY_LEVEL` | Specifies degree of independence | `AUTONOMY_LEVEL "High"` |

## Workflow and Process Control

| Keyword | Function | Example Usage |
|---------|----------|---------------|
| `WORKFLOW` | Defines a sequence of related tasks | `WORKFLOW "New Product Launch"` |
| `STEP` | Designates an individual phase in a workflow | `STEP 1: "Research market"` |
| `PARALLEL_EXECUTION` | Tasks that can run simultaneously | `PARALLEL_EXECUTION ["Design", "Development"]` |
| `SEQUENTIAL_EXECUTION` | Tasks that must run in order | `SEQUENTIAL_EXECUTION ["Plan", "Execute", "Review"]` |
| `TRIGGER_ON` | Initiates a task based on an event | `TRIGGER_ON "Form submission"` |
| `EXECUTE_IF` | Makes task execution conditional | `EXECUTE_IF "Budget approved"` |

## Communication and Notifications

| Keyword | Function | Example Usage |
|---------|----------|---------------|
| `NOTIFY` | Specifies who to inform about events | `NOTIFY "Stakeholders" WHEN "Completed"` |
| `ESCALATE` | Elevates issues to higher authority | `ESCALATE_IF "Deadline missed" TO "Director"` |
| `WHEN` | Used with NOTIFY to specify trigger event | `NOTIFY "Team" WHEN "Status changes"` |

## Conditional Logic

| Keyword | Function | Example Usage |
|---------|----------|---------------|
| `IF` | Starts a conditional statement | `IF "Budget > $10,000"` |
| `THEN` | Defines action when condition is true | `THEN "Require VP approval"` |
| `ELSE` | Defines alternate action when false | `ELSE "Proceed with manager approval"` |
| `AND` | Logical operator requiring all conditions | `IF "Urgent AND High priority"` |
| `OR` | Logical operator requiring any condition | `IF "Legal OR Compliance"` |
| `NOT` | Logical negation operator | `IF "NOT Approved"` |

## Templates and Reusability

| Keyword | Function | Example Usage |
|---------|----------|---------------|
| `TEMPLATE` | Defines a reusable task pattern | `TEMPLATE "Monthly Report"` |
| `USE` | Applies a template with values | `USE TEMPLATE "Approval Process"` |
| `EXTENDS` | Creates template inheritance | `TEMPLATE "Finance Report" EXTENDS "Report"` |

## Security and Compliance

| Keyword | Function | Example Usage |
|---------|----------|---------------|
| `CONFIDENTIAL` | Marks sensitive information | `CONFIDENTIAL "Yes"` |
| `VISIBLE_TO` | Controls who can see the task | `VISIBLE_TO ["HR Team"]` |
| `EDIT_RIGHTS` | Controls who can modify the task | `EDIT_RIGHTS ["Task Owner"]` |
| `MUST_COMPLY_WITH` | Links to compliance requirements | `MUST_COMPLY_WITH "GDPR"` |
| `LOG_HISTORY` | Specifies audit trail detail level | `LOG_HISTORY "Complete"` |

## Constraints and Limitations

| Keyword | Function | Example Usage |
|---------|----------|---------------|
| `CONSTRAINT` | Defines restrictions on task execution | `CONSTRAINT "Must use approved vendors"` |
| `BUDGET_CAP` | Sets maximum allowed spending | `BUDGET_CAP "$5,000"` |
| `SLA` | Defines service level agreements | `SLA "Resolution within 24 hours"` |
| `MAX_DURATION` | Limits how long a task should take | `MAX_DURATION "40 hours"` |

## AI and Automation

| Keyword | Function | Example Usage |
|---------|----------|---------------|
| `AI_PROMPT` | Provides instructions to AI systems | `AI_PROMPT "Summarize quarterly data"` |
| `CONTEXT` | Supplies background information | `CONTEXT "Based on previous customer interactions"` |
| `FACT_CHECK` | Verifies AI outputs against sources | `FACT_CHECK "Company knowledge base"` |
| `REVIEW_BY` | Requires human oversight of AI output | `REVIEW_BY "Content Manager"` |
| `AUTO_APPROVE_IF` | Sets conditions for automatic approval | `AUTO_APPROVE_IF "Amount < $500"` |

## Error Handling and Recovery

| Keyword | Function | Example Usage |
|---------|----------|---------------|
| `RETRY_IF` | Attempts task again on failure | `RETRY_IF "Connection error" UP_TO "3 times"` |
| `FALLBACK` | Defines alternative action if task fails | `FALLBACK "Assign to manual processing"` |
| `NOTIFY_ON_ERROR` | Sends alerts when tasks fail | `NOTIFY_ON_ERROR "Support Team"` |

## Integration and External Systems

| Keyword | Function | Example Usage |
|---------|----------|---------------|
| `SYNC_WITH` | Connects task with external tools | `SYNC_WITH "Jira" CONNECTION_DETAILS "Project: CORE"` |
| `ADD_TO_CALENDAR` | Creates calendar events | `ADD_TO_CALENDAR "Team Calendar"` |
| `EXPORT_TO` | Sends task data to external systems | `EXPORT_TO "Reporting Dashboard"` |

## Documentation and Metadata

| Keyword | Function | Example Usage |
|---------|----------|---------------|
| `DESCRIPTION` | Provides detailed explanation | `DESCRIPTION "This task handles monthly reconciliation"` |
| `TAGS` | Adds categorization labels | `TAGS ["Finance", "Monthly", "Critical"]` |
| `VERSION` | Tracks iteration of task definition | `VERSION "1.2"` |
| `OWNER` | Designates person responsible for task definition | `OWNER "Operations Team"` |

## Best Practices for Keyword Usage

1. **Consistency**: Use keywords consistently throughout your organization to establish clear patterns
2. **Clarity**: Combine keywords to create unambiguous instructions
3. **Simplicity**: Avoid over-engineered task definitions with too many keywords
4. **Documentation**: Comment complex keyword combinations to explain their purpose
5. **Validation**: Use parsing tools to ensure correct keyword syntax before implementation

## Implementation Considerations

When implementing a system that interprets these keywords:

1. Reserved keywords should be case-sensitive and matched exactly as specified
2. Keywords should be validated against this reference to ensure compliance
3. Error messages should clearly indicate issues with keyword usage or syntax
4. Extensions to this keyword set should follow the established naming patterns

---

This reference document is part of the Domain-Specific Language for Delegation framework. For implementation examples, syntax guides, and best practices, refer to the complete DSL documentation.
