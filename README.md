# TimePulse &bull; Office Short & Extra Hours Calculator

A single-page application (HTML, CSS, JavaScript) built to calculate attendance short hours, overtime/extra hours, lunch duration penalties, personal leave deductions, and net balance from punch logs.

---

## 🕒 Shift Rules & Calculation Workflow

Based on your attendance requirements and reverse-engineered against the official HR reports (`IMG-20260930-WA0002.jpg`, `IMG-20260930-WA0003.jpg`, `IMG-20260930-WA0004.jpg`):

1. **Standard Full-Day Shift**:
   - **Office Start Time**: `08:10 AM`
   - **Office End Time**: `04:50 PM (16:50)`
   - **Lunch Window**: `12:10 PM &ndash; 12:40 PM` (30 minutes allowance)
   - **12:40 Hard Limit**: Returning after 12:40 PM or spending > 30 minutes on lunch incurs a penalty.
   - **Morning Arrival**:
     - Arriving after `08:10`: **Short time** (`Arrival - 08:10`).
     - Arriving before `08:10`: **Extra time** (`08:10 - Arrival`).
   - **Evening Departure**:
     - Leaving after `16:50`: **Extra time** (`Departure - 16:50`).
     - Leaving before `16:50`: **Short time** (`16:50 - Departure`).

2. **Punch Types**:
   - **OFFICIAL Punches**: **Exempt** (do not deduct time or count as short hours).
   - **PERSONAL Punches**: **Counted as Short Time** (duration outside the building between punch-out and punch-in).
   - **LUNCH Punches**:
     - 30-minute allowance between `12:10` and `12:40`.
     - Time spent beyond 30 minutes or returning past `12:40` is deducted as Short Time.

3. **Half-Day Shifts**:
   - **Morning Session (`08:10 &ndash; 12:10`)**:
     - Arriving after `08:10` is short; arriving before `08:10` is extra.
     - Leaving past `12:10` is extra.
   - **Afternoon Session (`12:10 &ndash; 16:50`)**:
     - Arrival before `12:10` or during lunch window (`12:10 &ndash; 12:40`) is not considered extra.
     - Arrival after `12:40` is considered late (short time).
     - Leaving after `16:50` is extra time.

4. **Net Difference**:
   $$\text{Net Balance} = \text{Total Extra Minutes} - \text{Total Short Minutes}$$
   Displayed in both:
   - **Formatted Time**: e.g., `+0h 33m`, `-1h 42m`
   - **HR Decimal Format**: e.g., `+0.55`, `1.70-` (negative values denoted with a trailing `-` matching the HR system)

---

## 🚀 Features

- **Instant Zero-Config Preview**: Pre-loaded with all 374 punch records from [timesheet.xls](file:///g:/MyProjects/short-hours/timesheet.xls).
- **Drag & Drop Upload**: Upload any `.xls`, `.xlsx`, `.csv`, `.tsv`, or `.html` file.
- **KPI Metrics Dashboard**:
  - Net Balance with glowing surplus/deficit status.
  - Total Extra Hours & count of overtime days.
  - Total Short Hours & count of deficit days.
  - Total Active Days (Full vs Half Day breakdown).
  - Morning Punctuality Rate (% on-time arrivals).
- **Month Tabs**: Filter by April, May, June, July, August, September with individual month net totals.
- **Interactive Daily Table**:
  - Full breakdown of Arrival, Departure, Morning Late/Early, Evening Extra/Early, Lunch Penalty, and Personal Out.
  - Dropdown to manually override or toggle Session Type (Full Day, Morning Half Day, Afternoon Half Day) with real-time recalculation.
- **Inspect Day Modal**:
  - Visual 24-hour punch timeline with colorful badges for each turnstile/door reader.
  - Step-by-step mathematical deduction formula explained in plain English.
- **HR Report Comparator**:
  - Side-by-side table comparing calculated results with the reference images (`IMG-20260930-WA0002.jpg`, etc.).
  - Accuracy badge showing 100% matches.
- **Customizable Shift Parameters**:
  - Adjust Start, End, Lunch Window, Allowance, and Calculation Modes anytime.
- **Export & Theme**:
  - Export to CSV.
  - Dark Mode and Light Mode with glassmorphic aesthetic.

---

## 💻 How to Run

Simply open [index.html](file:///g:/MyProjects/short-hours/index.html) in any browser (Chrome, Edge, Firefox, Brave) or run:

```bash
python -m http.server 8080
```
Then navigate to: `http://localhost:8080/`
