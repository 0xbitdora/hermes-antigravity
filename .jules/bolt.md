## 2024-10-15 - Unnecessary Spin Loop in stream reading
**Learning:** `subprocess.Popen.stdout.readline()` on a blocking pipe automatically blocks until a full line is received or EOF is reached. A spin loop checking `proc.poll()` with `time.sleep()` when `readline()` returns empty actually artificially delays EOF detection, because an empty string already exclusively indicates EOF on a blocking stream.
**Action:** Remove `time.sleep` and `proc.poll()` checks after `readline()`; just break when `readline()` returns an empty string.
