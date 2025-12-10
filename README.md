# 做一个多智能体的代码审查助手

        ## Must Have
        - Core multi-agent code review workflow: at least two Python agents (e.g., StyleAgent and BugHunterAgent) that sequentially analyze a pasted code snippet and return a combined review summary via a simple Flask API.
- Basic static analysis capabilities: integrate lightweight Python linters or AST-based checks (e.g., PEP8/style, unused variables, obvious bugs) that each agent can call to ground its feedback.
- Clear role separation between agents: define distinct prompts/behaviors (e.g., one focuses on readability and style, another on potential bugs and edge cases) to demonstrate the value of multi-agent collaboration.
- Minimal web UI in Flask: a single-page form to paste code, trigger review, and display per-agent comments plus an overall consolidated recommendation.
- Simple architecture and logging: straightforward Python modules for agents with basic logging of each agent’s output for debugging and demo purposes.

        ## Optional
        - ArchitectAgent that summarizes and comments on code structure, modularity, and potential refactors for maintainability.
- Knowledge-based suggestions: a small, hard-coded ruleset or FAQ that lets agents suggest best practices (e.g., error handling, input validation, docstrings) based on detected patterns.
- Basic severity tagging: classify each finding as info/warning/error and group them in the UI for easier scanning.
- Lightweight diff support: allow users to paste ‘before’ and ‘after’ code and have agents comment on whether the changes improve quality or introduce risks.
- Simple Slack or webhook integration: send the consolidated review to a channel or URL to simulate CI-style feedback without building full CI/CD.

        ## Insights
        - Focusing on just Python code review keeps scope manageable for beginners and allows reuse of existing linting tools instead of building analyzers from scratch.
- Distinct, narrow agent roles make the multi-agent aspect visible in the demo and easier to implement than a complex planner/caller system.
- A text-area based Flask UI is enough to showcase value; investing heavily in frontend or cross-platform deployment will likely hurt progress within 31 hours.
- Predefining a few example code snippets (good, bad, mixed) will make it easier to test and demo the system under time pressure.
- Designing the agents as plain Python classes/functions now will make it easier to later plug into more advanced orchestration frameworks if the project continues after the hackathon.

        ## Warnings
        - Overly complex multi-agent orchestration (planners, schedulers, dynamic routing) is risky for a 31-hour, beginner-level team and may prevent having a working demo.
- Trying to support multiple languages or deep architectural analysis (full project understanding, dependency graphs) will likely exceed the time and experience constraints.
- Building integrations like full CI/CD pipelines, IDE plugins, or enterprise-grade dashboards can quickly consume time without improving the core multi-agent review story.
- Relying on heavy external services or complex deployments (Kubernetes, edge devices, cross-platform clients) may introduce debugging overhead that beginners struggle to resolve.
- Insufficient test coverage of the agent logic can lead to confusing or contradictory feedback during the demo; at least a few hard-coded test cases should be run before presenting.
