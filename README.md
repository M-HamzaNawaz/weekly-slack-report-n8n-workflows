# Weekly Slack Attendance Report Workflow

An automated n8n workflow that generates comprehensive weekly attendance reports, tracks employee hours across multiple shifts, and provides performance insights with visual indicators.

## 📋 Overview

This workflow extends the daily attendance system by aggregating data across a 5-day work week (Monday-Friday), calculating weekly totals, identifying attendance patterns, and generating formatted reports with color-coded status indicators and motivational messages.

## ✨ Features

### Core Functionality
- **Weekly Data Aggregation** - Collects and processes attendance data from Monday to Friday
- **Multi-Shift Support** - Handles both day shifts (1 PM - 10 PM) and night shifts (4 PM - 1 AM)
- **Fuzzy Message Matching** - Recognizes variations of check-in/out and break commands
- **Automated Report Generation** - Creates CSV reports with daily breakdowns
- **Slack Integration** - Posts reports directly to configured channels

### Smart Features
- **Missing Check-out Detection** - Automatically flags incomplete days with `(M)` indicator
- **Late Arrival Tracking** - Identifies late check-ins based on shift start times
- **Break Time Calculation** - Accurately tracks step-out/step-in durations
- **Overnight Shift Handling** - Correctly processes shifts that span past midnight
- **Fallback Check-out Logic** - Auto-assigns expected check-out time when missing

### Visual Indicators
| Indicator | Meaning |
|-----------|---------|
| 🔴 | Very Low hours (< 7h/day) |
| 🟡 | Below average (7-8h/day) |
| 🟢 | Good hours (8h/day) |
| (L) | Late Check-in |
| (M) | Missing Check-out |
| (A) | Absent |

### Performance Messaging
The workflow generates personalized motivational messages based on weekly performance:

| Weekly Hours | Message Theme |
|--------------|---------------|
| < 7 hours | ⚠️ Critical Low / Urgent Fix |
| 7-20 hours | 📉 Needs Improvement |
| 20-30 hours | 👍 Good Progress |
| 30-35 hours | 🚀 Almost There |
| 35-40 hours | 🏆 Excellent Work |
| 40+ hours | 👑 Elite Performance |

## 🚀 User Commands

Users type these commands in the monitored Slack channel:

| Command | Purpose |
|---------|---------|
| `check in` / `check-in` / `checked in` | Mark start of work shift |
| `check out` / `check-out` / `checked out` | Mark end of work shift |
| `step out` / `step-out` / `stepped out` | Start a break |
| `step in` / `step-in` / `stepped in` | End a break |

**Fuzzy Matching Examples:**
- `"checkin"`, `"Checked In"`, `"In"` → Recognized as Check-in
- `"stepout"`, `"Stepped Out"` → Recognized as Step-out

## 📊 Report Structure

### CSV Report Columns
