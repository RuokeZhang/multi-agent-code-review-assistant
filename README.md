# 做一个多智能体的代码审查助手

        ## Insights
        - Limit the initial scope to one or two languages (e.g., Python and JavaScript) so you can ship a robust end-to-end multi-agent flow within 64 hours
- Use a single orchestrator in Flask that fans out the same code payload to each agent function and then merges responses; avoid complex planner/caller hierarchies for the hackathon
- Design agent outputs with a shared schema (severity, category, line range, message, suggestion) so the frontend can render them consistently and you can add new agents later with minimal changes
- Start with a paste-or-upload UX instead of full repo analysis; this drastically reduces complexity around parsing, indexing, and performance
- Prepare a few small sample repos/snippets with known issues to demo how different agents surface complementary insights (style vs. bugs vs. architecture)

        ## Warnings
        - Overly ambitious multi-agent orchestration (dynamic planning, tool-calling chains, long-context reasoning) can consume most of the 64 hours and leave you with a fragile demo
- Full CI/CD integration, IDE plugins, or deep GitHub App workflows are likely out of scope for a 3-person intermediate team in this timeframe
- Supporting many languages or complex build systems will require language-specific tooling and may cause frequent failures during the demo
- Running heavy static analysis tools synchronously on large files can cause timeouts and poor UX; keep file sizes small and provide clear limits
- Be careful with any auto-fix or code-edit features; incorrect edits can break code and may require more validation logic than you have time to implement

        ## TODO (start here)
        - [MUST] Core multi-agent code review workflow with at least 2 specialized agents (e.g., StyleAgent and BugRiskAgent) that each take a code snippet + diff as input and return separate analyses
- [MUST] Web UI (Next.js + minimal Flask backend API) where a user can paste code or upload a file, select language, and see per-agent comments in separate panels
- [MUST] Basic static checks integrated into one agent (e.g., running flake8 or a simple linter for Python/JS) and surfacing the findings in human-readable form
- [MUST] SummarizerAgent that aggregates all agent outputs into a concise, prioritized review summary (top issues, suggested fixes)
- [MUST] Simple project-level context handling: allow user to provide a short README or description that is passed to agents so they can tailor feedback to the repo’s goals
- [OPTIONAL] ArchitectAgent that focuses on architectural and design-level feedback (modularity, layering, naming, dependency boundaries)
- [OPTIONAL] LearningAgent that detects recurring mistakes across multiple reviews in a session and suggests a short personalized learning checklist
- [OPTIONAL] GitHub/Git integration to fetch a specific diff or PR and run the multi-agent review automatically, returning a single review page
- [OPTIONAL] Inline annotation view that shows agent comments side-by-side with code lines (basic read-only code viewer, no full IDE)
- [OPTIONAL] Simple configuration panel to toggle which agents are active and adjust their strictness level (e.g., style-only vs. bug-focused)
