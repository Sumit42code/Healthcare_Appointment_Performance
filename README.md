# Healthcare_Appointment_Performance


## Project overview

This Excel portfolio project analyses synthetic healthcare appointment data from four community clinics across New Zealand. Six monthly source tables covering January to June 2026 were combined and cleaned with Power Query, enriched with clinic and service reference data, and presented through an interactive Excel dashboard.

The project focuses on appointment attendance, no-shows, booking lead times, service waiting targets, patient waiting times, satisfaction and recorded fees.

> **Data notice:** All records in this project are synthetic and were created for learning and portfolio purposes. The workbook contains no real patient information.

## Business objectives

The analysis was designed to answer the following questions:

- How many appointments were attended, cancelled, rescheduled or recorded as no-shows?
- Which clinics have the highest no-show rates?
- Which services are meeting their waiting-time targets?
- How long do attended patients wait between check-in and being seen?
- What proportion of attended patients are seen within 30 minutes?
- How are recorded appointment fees distributed across clinics?

## Tools and techniques

- Microsoft Excel
- Power Query
- Excel Tables and structured references
- Data-type and data-quality validation
- Query append and lookup merges
- Conditional logic and analytical flags
- PivotTables and PivotCharts
- Slicers and a date timeline
- KPI calculations and dashboard design

## Dataset and scope

| Item | Value |
|---|---:|
| Reporting period | January–June 2026 |
| Monthly source files | 6 |
| Original appointment records | 978 |
| Records without an Appointment ID excluded | 6 |
| Exact duplicate records removed | 18 |
| Final cleaned appointment records | 954 |
| Records with a usable appointment date | 948 |
| Clinics | 4 |
| Services | 5 |

## Dashboard preview
<img width="900" height="500" alt="image" src="https://github.com/user-attachments/assets/a943faca-afca-4b60-a92a-5c6547d1b7cb" />


The Excel dashboard contains eight headline KPI cards and five interactive charts:

- Monthly appointments by status
- No-show rate by clinic
- Wait-target achievement by service
- Average patient wait by clinic
- Share of recorded fees by clinic


## Data preparation

The monthly appointment tables were appended into one Power Query pipeline. The cleaning process was recorded through reversible Applied Steps so that the workbook can be refreshed when its source data changes.

| Data-quality issue | Treatment |
|---|---|
| Blank Appointment IDs | Six records were excluded because a reliable appointment identifier could not be created. |
| Exact duplicate records | Eighteen repeated rows were removed after comparing all appointment fields. |
| Missing Patient IDs | Six records were retained and identified with a missing-value flag. No patient IDs were invented. |
| Missing Service Codes | Twelve records were retained and flagged as missing service codes. |
| Inconsistent categorical values | Appointment status, booking channel and follow-up values were standardised. |
| Invalid numeric values | Text and out-of-range values in duration, satisfaction and fee fields were converted or set to null under documented rules. |
| Invalid or unavailable dates | Unconvertible dates were set to null rather than estimated. |
| Invalid time sequences | Appointments were retained, but invalid times were excluded from patient-wait calculations. |
| Clinic and service codes | Valid codes were standardised and merged with reference tables. |

## Analytical fields

The enriched appointment table includes calculated fields used by the dashboard, including:

- `Booking_Lead_Days`
- `Met_Wait_Target_Flag`
- `Patient_Wait_Minutes`
- `Seen_Within_30_Min_Flag`
- `Attendance_Eligible_Flag`
- `No_Show_Flag`
- `Fee_Recorded_Flag`
- `Fee_Variance_NZD`
- `Appointment_Month_Start`

These fields separate valid analytical populations from missing or logically invalid values. For example, the no-show rate uses only attendance-eligible appointments, while patient-wait measures use valid attended records.

## KPI summary

| KPI | Result |
|---|---:|
| Total appointments | 954 |
| Attended appointments | 666 |
| No-show appointments | 123 |
| No-show rate | 15.6% |
| Average booking lead time | 27.8 days |
| Appointments meeting the service wait target | 30.9% |
| Average patient waiting time | 19.7 minutes |
| Attended patients seen within 30 minutes | 79.8% |
| Average satisfaction score | 3.83 out of 5 |
| Total recorded appointment fees | NZ$96,335 |
| Appointments with a recorded fee | 98.7% |

## Data story

The analysis shows that the main patient-access challenge occurs before the appointment rather than after patients arrive at the clinic.

Across 954 cleaned appointments, 666 were attended and 123 were recorded as no-shows, producing an overall no-show rate of 15.6%. Wellington Harbour Community Clinic had the highest date-filtered no-show rate at 17.3%, compared with 13.5% at Auckland Central Community Clinic. This variation suggests that reminder and rescheduling interventions should be targeted by clinic rather than applied uniformly.

Waiting-target performance presented a larger operational concern. The average booking lead time was 27.8 days, and only 30.9% of assessable appointments met their service-specific waiting target. Cardiology Review achieved the strongest result at 50.8%, while General Practice achieved only 14.0%. This indicates that appointment capacity or scheduling pressure differs substantially between services.

Once patients arrived, clinic flow performed more strongly. The average patient wait was 19.7 minutes, and 79.8% of valid attended appointments were seen within 30 minutes. This contrast suggests that the larger access bottleneck is securing a timely appointment, rather than waiting inside the clinic.

Wellington also contributed the largest share of recorded fees among dated appointments at approximately 27.2%. Its combination of high activity and the highest no-show rate indicates an opportunity to recover potentially unused capacity through targeted reminders, easier cancellation and rescheduling options, and closer monitoring of high-risk appointment groups.

Based on these findings, the operational priorities are to reduce no-shows at higher-rate clinics, investigate capacity constraints in General Practice and Diabetes Care, and maintain the comparatively strong check-in-to-consultation performance.


## Key findings

1. **No-shows varied by clinic.** The overall no-show rate was 15.6%. Among records with an appointment date, Wellington Harbour Community Clinic had the highest rate at 17.3%, while Auckland Central Community Clinic had the lowest at 13.5%.

2. **Service waiting-target achievement was low overall.** Only 30.9% of assessable appointments met the applicable service target. Cardiology Review performed best at 50.8%, while General Practice was lowest at 14.0%.

3. **Most valid attended appointments were seen within 30 minutes.** The average patient wait was 19.7 minutes and 79.8% were seen within 30 minutes. In the dated-record clinic comparison, Auckland had the longest average wait at approximately 20.5 minutes and Palmerston North had the shortest at 18.6 minutes.

4. **Wellington contributed the largest share of dated recorded fees.** Wellington Harbour Community Clinic represented approximately 27.2% of fees in the date-filtered clinic comparison, followed by Palmerston North at 25.6%.

## Recommendations

- Review reminder and rescheduling processes at clinics with higher no-show rates, particularly Wellington Harbour Community Clinic.
- Investigate capacity, scheduling and referral processes for services with low waiting-target achievement, especially General Practice and Diabetes Care.
- Monitor patient-flow performance at clinics with above-average waiting times and review check-in-to-consultation workflows.
- Continue monitoring missing identifiers and dates during each refresh so that data-quality problems do not silently enter KPI calculations.


Clinic, booking-channel and appointment-month controls allow users to explore the results. The headline KPI cards show the complete January–June results, while date-filtered charts use the 948 records with a valid appointment date.

## Workbook structure

| Worksheet | Purpose |
|---|---|
| `Dashboard` | Interactive KPI and chart presentation |
| `KPI_Summary` | Supporting KPI calculations |
| `Pivot_Analysis` | PivotTables behind the dashboard charts |
| `Appointments_Analysis` | Final 954-row enriched analytical table |
| `QUALITY_LOG` | Data-quality checks, evidence and decisions |
| `KPI_DEFINITIONS` | KPI definitions and calculation rules |
| `DATA_DICTIONARY` | Field definitions and expected data types |
| Monthly raw sheets | Original January–June source records |
| Lookup sheets | Clinic, service, clinician and patient reference data |


## Limitations

- The dataset is synthetic and should not be interpreted as evidence about real healthcare providers or patients.
- Six retained appointments have no usable appointment date. Date-filtered visuals therefore analyse 948 records, while the headline totals use all 954 cleaned records.
- Missing service and patient identifiers were retained and flagged rather than estimated.
- The analysis supports operational reporting and does not make clinical decisions.



## Skills demonstrated

This project demonstrates data cleaning, transformation, quality assurance, lookup enrichment, KPI design, analytical population definition, PivotTable analysis, interactive dashboard development and data storytelling in Excel.

## Author

**Sumit Uniyal**  
Graduate data analyst portfolio project  
[GitHub profile](https://github.com/Sumit42code)
