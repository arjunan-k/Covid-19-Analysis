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

# ----- Top 10 infected Country ----- #

SELECT location, population, MAX(total_cases), 
MAX((total_cases/population)) * 100 AS infected_population
FROM covid_deaths
WHERE ((total_cases/population) * 100) IS NOT NULL
GROUP BY location, population
ORDER BY infected_population DESC
LIMIT 10
```
# Showing top 10 Countries with highest death count per population
```sql
SELECT location, continent, population, MAX(total_deaths) AS total_death_count
FROM covid_deaths
WHERE total_deaths IS NOT NULL AND continent IS NOT NULL
GROUP BY location, population, continent
ORDER BY total_death_count DESC
LIMIT 10

# ----- Death count in continents ----- #

SELECT location, MAX(total_deaths) AS total_death_count
FROM covid_deaths
WHERE continent IS NULL
GROUP BY location
ORDER BY total_death_count DESC
```
# Showing the total death percentage per date
```sql
SELECT SUM(new_cases) as total_cases, SUM(new_deaths) as total_death,
(SUM(new_deaths)/SUM(new_cases)) * 100 AS deathpercentage
FROM covid_deaths
WHERE CONTINENT IS NOT NULL
GROUP BY date
HAVING (SUM(new_deaths)/SUM(new_cases)) IS NOT NULL
ORDER BY total_cases DESC
```
# Total Population v/s Vaccinations
```sql
SELECT cd.continent, cd.location, cd.date, cd.population, cv.new_vaccinations 
FROM covid_deaths AS cd
INNER JOIN covid_vaccinations AS cv
ON cd.location = cv.location
WHERE new_vaccinations IS NOT NULL
ORDER BY new_vaccinations DESC
```
# 
```sql

```

```sql

```

```sql

```