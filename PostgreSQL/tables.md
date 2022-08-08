```sql
CREATE TABLE public.covid_deaths
(
    iso_code character varying(10),
    continent character varying(25),
    location character varying(25),
    date date,
    population bigint,
    total_cases bigint,
    new_cases bigint,
    new_cases_smoothed numeric(10, 3),
    total_deaths bigint,
    new_deaths bigint,
    new_deaths_smoothed numeric(10, 3),
    total_cases_per_million numeric(10, 3),
    new_cases_per_million numeric(10, 3),
    new_cases_smoothed_per_million numeric(10, 3),
    total_deaths_per_million numeric(10, 3),
    new_deaths_per_million numeric(10, 3),
    new_deaths_smoothed_per_million numeric(10, 3),
    reproduction_rate numeric(10, 3),
    icu_patients integer,
    icu_patients_per_million numeric(10, 3),
    hosp_patients integer,
    hosp_patients_per_million numeric(10, 3),
    weekly_icu_admissions numeric(10, 3),
    weekly_icu_admissions_per_million numeric(10, 3),
    weekly_hosp_admissions numeric(10, 3),
    weekly_hosp_admissions_per_million numeric(10, 3)
);

ALTER TABLE IF EXISTS public.covid_deaths
    OWNER to postgres;
```
