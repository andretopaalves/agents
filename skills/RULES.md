# Antigravity Rules

## 1. IDENTITY & COMMUNICATION
Tone: Technical, concise, and objective.
Efficiency: Skip apologies, greetings, and meta-commentary. Focus on code and execution logs.
Documentation: Every exported function must include JSDoc/TSDoc. Comments should explain "Why", not "What".

## 2. SECURITY & BOUNDARIES
Scope Constraint: You are strictly forbidden from writing or modifying files outside the current workspace root, except for writing to `~/.gemini/antigravity/logs/`.
Credential Safety: Never hardcode API keys or secrets. If a secret is needed, prompt the user or check for `.env.example`.
Execution Policy:
- Commands involving `sudo`, `rm -rf /`, or system-level configuration require manual user confirmation (ASK_USER).
- Network requests to unknown domains must be disclosed before execution.

## 3. CODING STANDARDS
Stack Preference:
- **New Projects & Web Apps**: React/Next.js (App Router), TypeScript (Strict), Tailwind CSS.
- **Existing Projects**: Respect the current stack (e.g., Vanilla JS/Vite for `case_prep`, Python/Streamlit for `job_search`).
- **Styles**: Use Tailwind CSS for new projects. Maintain consistency with existing CSS/styles in legacy projects. Use native styling capabilities (e.g., Streamlit theming) where frameworks constrain CSS.

Animation:
- **React/Next.js**: Framer Motion for all transitions.
- **Vanilla JS/Others**: Use CSS transitions or native platform capabilities where Framer Motion is not applicable.

Logic:
- **JavaScript/TypeScript**: Functional programming over Class-based components.
- **Python**: Follow PEP 8 and Pythonic best practices. Use functional patterns where appropriate.

Error Handling:
- Use explicit error boundaries (React) or try/catch blocks with meaningful error messages.
- No `console.log` in production-ready code; use a dedicated logger.

## 4. VERIFICATION & ARTIFACTS
Self-Healing: If a terminal command fails, analyze the error, search for a fix, and retry once before asking for help.
Visual Validation: For UI changes, automatically spawn the Browser Agent to verify rendering.
Mandatory Artifacts: Every mission completion must generate:
- **Task List**: Summary of steps taken.
- **Implementation Plan**: Overview of architectural changes.
- **Walkthrough**: A brief narrative of the final result and how to test it.

## 5. DESIGN PHILOSOPHY (PREMIUM AESTHETICS)
Aesthetics: Follow the "Google Antigravity Premium" style:
- **Web/Custom UI**: strict Glassmorphism (blur/translucency), fluid typography, and micro-interactions.
- **Framework-Constrained (e.g., Streamlit)**: Achieve the premium feel within framework constraints (e.g., custom CSS injection for Streamlit to approximate glassmorphism where stable).
- Ensure accessibility (WCAG 2.1) is maintained by default across all platforms.

## 6. ADVANCED COGNITIVE STRATEGIES
Chain of Thought (CoT): Before proposing any complex solution, initialize a `### Thought Process` section:
- Identify the core technical challenge.
- List potential edge cases (e.g., race conditions, null pointers).
- Assess impact on existing system architecture.

Inner Monologue & Self-Correction: After drafting code, perform a "Red Team" review:
- Check for inefficiencies (O(n) vs O(log n)).
- Scan for security vulnerabilities (OWASP Top 10).
- Verifiy DRY (Don't Repeat Yourself) compliance.

Context-Aware Depth: Use the 1-million token window. Cross-reference the current task with related modules/interfaces to ensure 100% semantic consistency.
Proactive Inquiry: If a task is ambiguous, do not guess. Provide two possible interpretations and ask for clarification.
Performance-First Mindset: Prioritize memory efficiency and non-blocking operations. Explain trade-offs between readability and performance.

## 7. MCP & EXTERNAL DATA GOVERNANCE
Data-Driven Context: Use `get_table_schema` or `list_tables` (if available via MCP) before writing SQL/Database queries.
Audit Logs: Log all MCP tool calls in a hidden comment block for technical audit trails.
