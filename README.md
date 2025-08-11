# Blog Traffic Analysis Reports

This repository contains exports from Google Analytics (GA4) used to analyze traction and traffic for the blog “No Offense But.” It includes CSV datasets and PDF summary reports that cover audience, acquisition, behavior (pages), devices, and events.

## What’s inside

- `data-export.csv` — Users by Platform (GA4 export)
  - Date range: 2023-10-15 → 2023-11-11
  - Columns:
    - `Platform`: e.g., ["Web"]
    - `Users`: number of users for the given platform

- `data-export (1).csv` — Users by Nth day (GA4 export)
  - Date range: 2023-10-08 → 2023-11-12
  - Columns:
    - `Nth day`: day index within the range or cohort day
    - `Users`: number of users on that index

- `General.pdf` — Overall traffic overview (users, sessions, engagement)
- `Pages.pdf` — Page-level performance (top pages, views, engagement)
- `Traffic Aquisition.pdf` — Acquisition overview by channels/mediums/sources
- `Type of Devices.pdf` — Device category breakdown (desktop, mobile, tablet)
- `Demography.pdf` — Audience demographics (age, gender, interests, geo)
- `Events.pdf` — Event-level interactions (clicks, scrolls, conversions)

Note: Filenames reflect the original exports (including spelling), e.g., `Traffic Aquisition.pdf`.

## Goals

- Understand blog traction over time
- Identify top acquisition channels and sources
- Analyze page performance and content engagement
- Break down traffic by device type and demographics
- Track key user actions/events and potential conversions

## Quick start (Python)

If you want to explore the CSVs programmatically, you can use Python with pandas.

```bash
pip install pandas matplotlib seaborn
```

```python
import pandas as pd

# Users by Platform
platform_df = pd.read_csv("data-export.csv", comment="#")
print(platform_df.head())

# Users by Nth day
nthday_df = pd.read_csv("data-export (1).csv", comment="#")
print(nthday_df.head())

# Example: bar chart of users by platform
ax = platform_df.groupby("Platform", dropna=False)["Users"].sum().sort_values(ascending=False).plot(kind="bar")
ax.set_title("Users by Platform")
ax.figure.tight_layout()
ax.figure.show()
```

Tip for Excel/Sheets: When opening the CSVs, ignore lines starting with `#` (they are GA4 headers), or import with the option to treat `#` as comment lines.

## Suggested analyses

- Acquisition
  - Users and sessions by Default Channel Group, Source/Medium
  - New users, returning users, and engagement rate by channel

- Traction over time
  - Daily/weekly users and engaged sessions
  - Use `Nth day` to inspect progression or cohort-like patterns

- Content performance
  - Top pages by views, users, average engagement time
  - Entrance pages and exit rates (if available)

- Audience & devices
  - Device category share (desktop vs mobile vs tablet)
  - Geo and demographics distributions

- Events and conversions
  - Key events volume (clicks, scrolls, sign-ups)
  - Conversion rate by page and by acquisition channel

## KPIs to track

- Users, New users, Engaged sessions, Engagement rate
- Views per user, Average engagement time
- Conversions and conversion rate
- Channel/source contribution to users and conversions
- Device mix and device-specific performance

## Updating the data

1. Export fresh GA4 reports (CSV and/or PDF) for the same dimensions/metrics.
2. Place new files in the repository. Keep original export names or update references here.
3. If you automate, consider naming with an ISO date suffix, e.g., `data-export_2023-11-12.csv`.

## Notes

- These exports may contain sensitive traffic information. Share with caution.
- The PDFs provide convenient overviews; CSVs are better for detailed analysis.
- If you add more CSVs (e.g., acquisition by channel, pages with metrics), extend this README with their column dictionaries.

