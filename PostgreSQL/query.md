# Covid Death Anlysis
```sql
SELECT * FROM covid_deaths            -- Complete dataset of covid_deaths
SELECT * FROM covid_vaccinations      -- Complete dataset of covid_vaccinations
```
# Dataset of covid_deaths we are using
```sql
SELECT location, date, total_cases, new_cases, total_deaths, population 
FROM covid_deaths
```
# Comparison of Total Cases v/s Total Deaths
Shows the percentage chance of dying if you get infected
```sql
SELECT location, date, total_cases, total_deaths, population, 
(total_deaths/total_cases) * 100 AS death_percentage
FROM covid_deaths
WHERE location ILIKE '%india%'
ORDER BY death_percentage DESC
```
# Comparison of Total Cases v/s Population
```sql
SELECT location, date, population, total_cases, 
(total_cases/population) * 100 AS infected_population
FROM covid_deaths
ORDER BY infected_population DESC

# Top 10 infected Country

SELECT location, population, MAX(total_cases), 
MAX((total_cases/population)) * 100 AS infected_population
FROM covid_deaths
WHERE ((total_cases/population) * 100) IS NOT NULL
GROUP BY location, population
ORDER BY infected_population DESC
LIMIT 10
```
```sql

```

```sql

```

```sql

```

```sql

```

```sql

```

```sql

```
