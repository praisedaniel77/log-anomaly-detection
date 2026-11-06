# Log Anomaly Detection

Detects anomalies in application logs using an Isolation Forest model (scikit-learn). It learns what normal log activity looks like and flags unusual patterns such as error spikes, so you don't have to scan logs by hand.

## What's inside

| File | Purpose |
|---|---|
| `simple_log_analysis.py` | Basic analysis: parses the logs and counts errors in 30-second windows |
| `aiops_log_analysis.py` | Uses an Isolation Forest model to flag anomalous log activity |
| `system_logs.txt` | Sample log file used by both scripts |

## Prerequisites

- Python 3.10 or newer
- Git Bash or any terminal

## Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/praisedaniel77/log-anomaly-detection.git
   cd log-anomaly-detection
   ```

2. Create and activate a virtual environment:
   ```bash
   python3 -m venv venv
   source venv/Scripts/activate   # Windows (Git Bash)
   # source venv/bin/activate     # Linux / macOS
   ```

3. Install dependencies:
   ```bash
   pip install pandas scikit-learn numpy
   ```

## Usage

Run the basic analysis:
```bash
python3 simple_log_analysis.py
```

Run the Isolation Forest anomaly detection:
```bash
python3 aiops_log_analysis.py
```

The anomalies found are printed to the terminal.

## How it works

1. Logs are read from `system_logs.txt` and parsed into timestamp, level, and message.
2. Log entries are grouped into time windows and turned into numeric features (for example, error counts per window).
3. An Isolation Forest model learns the normal pattern and isolates the points that behave differently.
4. Windows or entries scored as outliers are reported as anomalies.

## Notes

- Updated for newer pandas: time frequencies use lowercase units (`"30s"` instead of `"30S"`).
- Isolation Forest is unsupervised, so it needs no labeled data, but results depend on the sample logs and settings used.

## Credits

Based on the AI-assisted DevOps series by [Abhishek Veeramalla](https://github.com/iam-veeramalla/ai-assisted-devops) and Krish Naik. Adapted and tested by me on Windows with Git Bash.

## What I learned

- How Isolation Forest detects outliers without labeled data
- How AIOps can speed up log analysis
- Reading Python tracebacks to find the real cause of an error
