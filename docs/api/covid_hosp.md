---
title: COVID-19 Reported Patient Impact and Hospital Capacity by State Timeseries
parent: Epidata API (Other Diseases)
---

# COVID-19 Hospitalization by State

This data source is a mirror of the "COVID-19 Reported Patient Impact and
Hospital Capacity by State Timeseries" and "COVID-19 Reported Patient Impact and
Hospital Capacity by State" datasets provided by the US Department of
Health & Human Services via healthdata.gov. The latter provides more frequent updates,
so it is combined with the former to create a single dataset which is as recent as possible.

For more information, see the
[official description and data dictionary at healthdata.gov](https://healthdata.gov/Hospital/COVID-19-Reported-Patient-Impact-and-Hospital-Capa/g62h-syeh)
for "COVID-19 Reported Patient Impact and Hospital Capacity by State Timeseries,"
as well as the [official description](https://healthdata.gov/dataset/COVID-19-Reported-Patient-Impact-and-Hospital-Capa/6xf2-c3ie)
for "COVID-19 Reported Patient Impact and Hospital Capacity by State."

General topics not specific to any particular data source are discussed in the
[API overview](README.md). Such topics include:
[contributing](README.md#contributing) and [citing](README.md#citing).

## Metadata

This data source provides various measures of COVID-19 burden on patients and healthcare in the US.
- Data source: US Department of Health & Human Services (HHS) [COVID-19 Reported Patient Impact and
Hospital Capacity by State Timeseries](https://healthdata.gov/Hospital/COVID-19-Reported-Patient-Impact-and-Hospital-Capa/g62h-syeh) (published weekly)
  and [COVID-19 Reported Patient Impact and Hospital Capacity by State](https://healthdata.gov/dataset/COVID-19-Reported-Patient-Impact-and-Hospital-Capa/6xf2-c3ie) (published on an irregular schedule, every 1-6 days)
- Temporal Resolution: Daily, starting 2020-01-01
- Spatial Resolution: US States plus DC, PR, and VI
- Open Access: [Public Domain US Government](https://www.usa.gov/government-works)
- Versioned by Delphi according to "issue" date, which is the date that the
dataset was published by HHS.

# The API

The base URL is: https://delphi.cmu.edu/epidata/covid_hosp_state_timeseries/

See [this documentation](README.md) for details on specifying locations and dates.

## Parameters

### Required

| Parameter | Description | Type |
| --- | --- | --- |
| `states` | two-letter state abbreviations | `list` of states |
| `dates` | dates | `list` of dates or date ranges |

### Optional

| Parameter | Description | Type |
| --- | --- | --- |
| `issues` | issues | `list` of "issue" dates or date ranges |

If `issues` is not specified, then the most recent issue is used by default.

## Response

| Field | Description | Type |
| --- | --- | --- |
| `result` | result code: 1 = success, 2 = too many results, -2 = no results | integer |
| `epidata` | list of results | array of objects |
| `epidata[].state` | state pertaining to this row | string |
| `epidata[].date` | date pertaining to this row | integer |
| `epidata[].issue` | the date on which the dataset containing this row was published | integer |
| `epidata[].*` | see the [data dictionary](https://healthdata.gov/covid-19-reported-patient-impact-and-hospital-capacity-state-data-dictionary) |  |
| `message` | `success` or error message | string |

# Example URLs

### MA on 2020-05-10 (per most recent issue)
https://delphi.cmu.edu/epidata/covid_hosp_state_timeseries/?states=MA&dates=20200510

```json
{
    "result": 1,
    "epidata": [
        {
            "state": "MA",
            "issue": 20201116,
            "date": 20200510,
            "hospital_onset_covid": 53,
            "hospital_onset_covid_coverage": 84,
            "inpatient_beds": 15691,
            "inpatient_beds_coverage": 73,
            "inpatient_beds_used": 12427,
            "inpatient_beds_used_coverage": 83,
            "inpatient_beds_used_covid": 3625,
            "inpatient_beds_used_covid_coverage": 84,
            "previous_day_admission_adult_covid_confirmed": null,
            "previous_day_admission_adult_covid_confirmed_coverage": 0,
            "previous_day_admission_adult_covid_suspected": null,
            "previous_day_admission_adult_covid_suspected_coverage": 0,
            "previous_day_admission_pediatric_covid_confirmed": null,
            "previous_day_admission_pediatric_covid_confirmed_coverage": 0,
            "previous_day_admission_pediatric_covid_suspected": null,
            "previous_day_admission_pediatric_covid_suspected_coverage": 0,
            "staffed_adult_icu_bed_occupancy": null,
            "staffed_adult_icu_bed_occupancy_coverage": 0,
            "staffed_icu_adult_patients_confirmed_suspected_covid": null,
            "staffed_icu_adult_patients_confirmed_suspected_covid_coverage": 0,
            "staffed_icu_adult_patients_confirmed_covid": null,
            "staffed_icu_adult_patients_confirmed_covid_coverage": 0,
            "total_adult_patients_hosp_confirmed_suspected_covid": null,
            "total_adult_patients_hosp_confirmed_suspected_covid_coverage": 0,
            "total_adult_patients_hosp_confirmed_covid": null,
            "total_adult_patients_hosp_confirmed_covid_coverage": 0,
            "total_pediatric_patients_hosp_confirmed_suspected_covid": null,
            "total_pediatric_patients_hosp_confirmed_suspected_covid_coverage": 0,
            "total_pediatric_patients_hosp_confirmed_covid": null,
            "total_pediatric_patients_hosp_confirmed_covid_coverage": 0,
            "total_staffed_adult_icu_beds": null,
            "total_staffed_adult_icu_beds_coverage": 0,
            "inpatient_beds_utilization_coverage": 72,
            "inpatient_beds_utilization_numerator": 10876,
            "inpatient_beds_utilization_denominator": 15585,
            "percent_of_inpatients_with_covid_coverage": 83,
            "percent_of_inpatients_with_covid_numerator": 3607,
            "percent_of_inpatients_with_covid_denominator": 12427,
            "inpatient_bed_covid_utilization_coverage": 73,
            "inpatient_bed_covid_utilization_numerator": 3304,
            "inpatient_bed_covid_utilization_denominator": 15691,
            "adult_icu_bed_covid_utilization_coverage": null,
            "adult_icu_bed_covid_utilization_numerator": null,
            "adult_icu_bed_covid_utilization_denominator": null,
            "adult_icu_bed_utilization_coverage": null,
            "adult_icu_bed_utilization_numerator": null,
            "adult_icu_bed_utilization_denominator": null,
            "inpatient_beds_utilization": 0.6978504972730191,
            "percent_of_inpatients_with_covid": 0.2902550897239881,
            "inpatient_bed_covid_utilization": 0.21056656682174496,
            "adult_icu_bed_covid_utilization": null,
            "adult_icu_bed_utilization": null
        }
    ],
    "message": "success"
}
```


# Code Samples

Libraries are available for [JavaScript](https://github.com/cmu-delphi/delphi-epidata/blob/main/src/client/delphi_epidata.js), [Python](https://pypi.org/project/delphi-epidata/), and [R](https://github.com/cmu-delphi/delphi-epidata/blob/dev/src/client/delphi_epidata.R).
The following sample shows how to import the library and fetch MA on 2020-05-10
(per most recent issue).

### Python

Optionally install the package using pip(env):
````bash
pip install delphi-epidata
````

Otherwise, place `delphi_epidata.py` from this repo next to your python script.

````python
# Import
from delphi_epidata import Epidata
# Fetch data
res = Epidata.covid_hosp('MA', 20200510)
print(res['result'], res['message'], len(res['epidata']))
````

# Repair Log

If we ever need to repair the data record due to a bug in our code (not at the
source), we will update the list below.

## January 22, 2021

The following issues were repaired:

* 20210113
* 20210118

These issues had been imported using the wrong column order due to an imprecise
database migration. If you pulled these issues before January 22, you will want
to discard that data.
