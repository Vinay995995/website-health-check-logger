# website-health-check-logger
✅ 1. Set the target URL
URL="https://github.com"
→ The website whose health is being monitored.

✅ 2. Define the log directory
LOG_DIR="$HOME/website_health_logs"
mkdir -p "$LOG_DIR"
→ Ensures the log directory exists. $HOME means the current user’s home directory.
→ Example: /home/ubuntu/website_health_logs

✅ 3. Get today's date
TODAY=$(date +"%Y-%m-%d")
LOG_FILE="$LOG_DIR/health_log_$TODAY.log"
→ This creates a unique log file for each day.
Example: health_log_2025-04-03.log

✅ 4. Send HTTP request
response=$(curl -o /dev/null -s -A "Mozilla/5.0" -w "%{http_code} %{time_total}" "$URL")
-o /dev/null: Discards actual webpage content.
-s: Silent mode (no progress bar).
-A: Sets a browser-style User-Agent (helps avoid blocks).
-w: Formats curl's output to show only the status code and response time.
