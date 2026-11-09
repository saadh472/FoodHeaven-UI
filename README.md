# FoodHeaven Employee Portal UI

[![Quality checks](https://github.com/saadh472/FoodHeaven-UI/actions/workflows/quality.yml/badge.svg)](https://github.com/saadh472/FoodHeaven-UI/actions/workflows/quality.yml)

A lightweight employee management interface built with HTML, CSS, and JavaScript. The dashboard links attendance, payroll, performance, shift scheduling, employee details, and profile screens.

## Run locally

Install Python 3, open a terminal in this repository, and run the following command.

```sh
python -m http.server 8000 --bind 127.0.0.1
```

Open [the dashboard](http://127.0.0.1:8000/). The interface also works as static files. An internet connection is optional for Google Fonts.

## Try the demo

- Open **Employee Details** to search the sample directory. Add a fictional employee, edit its details, or remove its row.
- Open **Payroll**, choose **Modify**, and apply a salary adjustment between the displayed limits.
- Open **Shift Scheduling**, choose **Edit**, and change a sample employee's working hours.
- Use the profile panel to view the sample manager profile and the password form previews.

Changes in these screens are held in browser memory for the current page and reset on reload. Attendance, performance, payroll, and shift records use sample data. The portal and password pages preview navigation and validation with fictional values.

## Optional companion API

The employee directory tries `GET http://127.0.0.1:5000/employees` when it loads. Run the companion API with a configured SQL Server table to display those records. If the API is unavailable, the page shows a status message and uses synthetic demo employees. See the [FoodHeaven API setup](https://github.com/saadh472/FoodHeaven-API).

The directory expects these fields from each API row.

```text
EmployeeID, EmployeeName, ContactNo, EmailID, Address, HireDate, DateOfBirth
```

The companion API is read-only. Directory edits remain a browser-session preview even when the initial records come from SQL Server.

## Repository layout

| Path | Purpose |
| --- | --- |
| `index.html` | Entry point that opens the dashboard |
| `interface.html` | Main dashboard and profile panel |
| `Sidebar/` | Attendance, payroll, performance, shifts, and directory screens |
| `Canvas/` | Profile and password form previews |
| `Portal_login/` | Demo portal and password recovery previews |
| `tests/test_static_site.py` | Portable link and asset checks |

## Verify

```sh
python -m unittest discover -s tests -v
node --check Sidebar/employees.js
```

The static checks verify local references with exact filename case and reject machine-specific filesystem paths. Use fictional records when exploring this educational prototype.
