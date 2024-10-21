# Kickstarter Projects Analysis
The purpose of this project is to understand what influences the success of a Kickstarter campaign. 

## Data Sources
The source of the data is <a href="https://www.kaggle.com/datasets/kemical/kickstarter-projects">Kaggle</a>. 

## 🛠 Skills 
SQL 

## Actions

Examine the table information. 

```
PRAGMA table_info(ksprojects);

``` 


Select the relevant columns. 

```
SELECT main_category, 
       goal,
       backers,
       pledged 
 FROM ksprojects 
LIMIT 10;

```

Filter to find the projects that weren't successful. 

```
SELECT main_category, goal, backers, pledged
  FROM ksprojects
  WHERE state IN ('failed','canceled','suspended') 
 LIMIT 10;

```


Filter to find large projects (in terms of number of backers and amount pledged) that weren't successful. 

```
SELECT main_category, backers, pledged, goal
 FROM ksprojects
WHERE state IN ('failed', 'canceled', 'suspended')
    AND backers >= 100 AND pledged >= 20000
LIMIT 10;
```

```
SELECT main_category, 
       backers, 
       pledged, 
       goal, 
       pledged / goal AS pct_pledged 
  FROM ksprojects
 WHERE state IN ('failed')
   AND backers >= 100 AND pledged >= 20000
ORDER BY main_category, pct_pledged DESC
 LIMIT 10;

```

```
SELECT main_category, 
       backers, 
       pledged, 
       goal, 
       pledged / goal AS pct_pledged 
  FROM ksprojects
 WHERE state IN ('failed')
   AND backers >= 100 AND pledged >= 20000
ORDER BY main_category, pct_pledged DESC
 LIMIT 10;
```


```
SELECT main_category, 
       backers, 
       pledged, 
       goal, 
       pledged/goal AS pct_pledged,
       CASE
       WHEN pledged/goal  >= 1 THEN "Fully funded"
       WHEN pledged/goal BETWEEN .75 AND 1 THEN "Nearly funded"
       ELSE "Not nearly funded"
       END AS funding_status 
  FROM ksprojects
 WHERE state IN ('failed')
       AND backers >= 100 AND pledged >= 20000
 ORDER BY main_category, pct_pledged DESC
 LIMIT 10;
```

```
SELECT main_category, 
       backers, 
       pledged, 
       goal, 
       pledged/goal AS pct_pledged,
       CASE
       WHEN pledged/goal  >= 1 THEN "Fully funded"
       WHEN pledged/goal BETWEEN .75 AND 1 THEN "Nearly funded"
       ELSE "Not nearly funded"
       END AS funding_status 
  FROM ksprojects
 WHERE state IN ('failed')
       AND backers >= 100 AND pledged >= 20000
 ORDER BY main_category, pct_pledged DESC
 LIMIT 10;
``` 

