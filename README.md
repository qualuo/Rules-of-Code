# Rules-of-Code

This document outlines the rules and best practices for structuring code within **Power Platform**, specifically for **Power Apps** and **Power Automate**. Following these guidelines will help maintain code quality, improve maintainability, and ensure your apps and flows are efficient, scalable, and secure.



## Table of Contents

1. [General Best Practices](#general-best-practices)



## General Best Practices

- **Consistent Naming**: Use descriptive and consistent names for variables, functions, screens, and controls. In general, to keep it simple stick to PascalCase (e.g. `GetUserDetails`). This includes controls naming, screens, flow naming, scope-action naming (Power Automate), data tables.  Use camelCase for local/context variables that have a smaller scope.
- **Data tables**: Use singular for table names, e.g. `User`, not `Users`.
- **No display names**: To avoid confusion, use as few aliases as possible. Ideally, stick to an exact name and do not invent new ones. Using variations such as `users`, `Users`, `user`, `User`, for the same exact same entity WILL cause chaos.
- **Clear Descriptions**: Always provide meaningful comments and descriptions that help others understand the train of thought. Think of others!



## Power Apps

- **Responsive Design**: Ensure layout works across devices (mobile and desktop). Use containers to build responsive designs.
- **Minimalistic Layouts**: Focus on simplicity in design. Use whitespace effectively and avoid cluttering the screen with too many controls or data fields.
- **8-point grid system**: Use multiples of 8 to simplify alignment for anything involving pixels. This guideline may be broken if there is good reason, but stick to multiples of 8 by default.

### Formulas and Logic
- **Use Variables for State Management**: Instead of repeatedly calculating values or results within the UI, store them in variables (using `Set()` or `UpdateContext()` for local state) and reference them when needed.
- **Avoid Nested Ifs**: Use conditional statements efficiently. Avoid deeply nested `If()` functions, as they can reduce readability. Consider using `Switch()` or `Coalesce()` for more readable alternatives, or splitting it apart into simpler parts.
- **Minimize Controls**: Avoid unnecessary controls. For instance, use galleries and data tables wisely to display data without creating performance issues.

### Performance Optimization
- **Data Caching**: Consider using local variables to cache data temporarily instead of repeatedly querying a data source where possible.
- **Avoid Large Collections**: Large collections can negatively impact performance. Always consider pagination or delegation when working with large datasets.



## Power Automate

### Flow Structure and Design
- **Modular Flows**: Break down large flows into smaller, modular flows where possible. This helps with maintainability and troubleshooting.
- **Actions Grouping**: Group related actions together (e.g., data processing, external system interaction) using scope actions to keep the flow organized.
- **Naming Actions**: Name actions and conditions clearly to reflect their purpose. Keep the action name and append ` - [Description]` to make the flow easier to understand for others. Example name: `List rows - All users`. Keep in mind spaces become underscores in the logical name.
- **Minimize Polling**: Avoid frequent triggers (e.g., every minute) unless necessary. Use event-based triggers whenever possible to reduce unnecessary load.

### Error Handling
- **Configure Run After**: For actions that depend on the success or failure of previous steps, use the “Configure Run After” feature to handle different outcomes and control the flow execution.
- **Error Handling Scope**: Place critical actions inside a “Scope” and configure error handling to manage issues without affecting the entire flow.
- **Notify Users of Issues**: If an app or flow encounters an error that requires user action, display a clear error message with actionable steps to resolve the issue.
  
### Performance and Resource Management
- **Limit Actions**: Try to reduce the number of actions in your flow. Complex flows with excessive actions lead to slow performance.
- **Parallel Branching**: Use parallel branches where appropriate to reduce the execution time of your flows.
- **Throttling and Rate Limiting**: Be mindful of API limits and implement logic to avoid throttling. Add delays or check the status of previous actions when working with external systems.

### Data Protection
- **Secure Inputs/Outputs**: Hide sensitive data from logging by using "Secure Inputs" and "Secure Outputs".
- **Azure Key Vault**: Store secrets in key vaults.
- **Least Privilege Access**: Assign the least privilege to each role and flow user. Ensure that only necessary data and actions are exposed.


