## Plan: Always log Q/A to Application Insights

Add one consistent log event emitted for `/ask`, `/chat`, and after `/chat/stream` completes (in `finally`). The log should include the full question and full answer (text). Ignore multimodal content (when `content` is not `str`). If `APPLICATIONINSIGHTS_CONNECTION_STRING` is set, logs will flow to Application Insights via the existing `configure_azure_monitor(...)`.

### Steps
1. Add helpers in `app/backend/telemetry_qa.py`: `extract_last_user_text(messages)`, `extract_answer_text(result)`, `log_qa_event(...)`.
2. Use a stable event name `event="qa_log"` with fields: `route`, `session_state`, `user_oid`, `question`, `answer`, `is_stream`, `skipped_reason`.
3. Call `log_qa_event(...)` after `approach.run(...)` in `ask()` and `chat()` in `app/backend/app.py`.
4. In `chat_stream()` in `app/backend/app.py`, wrap the NDJSON generator: accumulate `delta.content` (only `str`) and emit `qa_log` in `finally`.
5. Add `caplog` tests in `tests/test_app.py`: `/ask`, `/chat`, `/chat/stream`, plus a multimodal case → `skipped_reason`.

### Further considerations
1. If `APPLICATIONINSIGHTS_CONNECTION_STRING` is not set, logs will only appear in application logs (not in App Insights).
