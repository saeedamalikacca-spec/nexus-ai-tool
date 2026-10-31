# NEXUS AI — Personal AI Toolkit

NEXUS AI is a responsive, browser-based educational demo of **tool calling** and **structured JSON output**. It has a dark purple dashboard, three working JavaScript tools, an execution log, and a copyable JSON response panel.

## Features

- **Tool routing:** reads a request and selects a suitable tool.
- **`calculator(expression)`:** safely parses basic arithmetic (`+`, `-`, `*`, `/`, `%`, parentheses) without using `eval()`.
- **`task_planner(goal, days)`:** returns a day-by-day starter plan.
- **`text_summarizer(text)`:** returns a short summary, key points, and word count.
- **Structured output:** each request produces a predictable JSON object with `status`, `tool`, `arguments`, and `result` (or `error`).
- **Execution trace:** records request receipt, tool selection, arguments, and completion.
- **Responsive interface:** works on desktop and mobile browsers.

## Run it

1. Download or clone this repository.
2. Open `index.html` in a modern browser. No package installation or API key is required.
3. Click a sample prompt or enter a request such as:
   - `Calculate (128 * 7) + 45`
   - `Make a task plan for finishing my science project in 3 days`
   - `Summarize: Tool calling lets an AI choose a function, provide arguments, and use the result to answer a request.`
4. Inspect **Tool execution log** and **Structured output**. Use **Copy JSON** to copy the response.

## Example structured response

```json
{
  "status": "success",
  "tool": "calculator",
  "arguments": {
    "expression": "(128 * 7) + 45"
  },
  "result": {
    "expression": "(128 * 7) + 45",
    "result": 941
  },
  "timestamp": "generated at runtime"
}
```

## How the tool-calling flow works

1. The user submits a natural-language request.
2. `routeRequest()` selects a tool and prepares its arguments.
3. The selected function in the tool registry executes.
4. The result is packaged into a JSON object and displayed.
5. The execution log makes the sequence visible for demonstration and testing.

## Important limitation

This is a **local tool-calling simulation**, not an LLM-powered assistant. The routing is rule-based and the tools run in the browser; no external AI API is called. It demonstrates the core function-selection, function-execution, and structured-output concepts without requiring a secret API key. If the course rubric specifically requires a live AI provider API, an API-backed version would be needed.

## Files

- `index.html` — application structure
- `style.css` — responsive visual design
- `script.js` — routing, tools, JSON output, and execution log
