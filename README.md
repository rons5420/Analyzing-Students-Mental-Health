# 🧠 Exploring the Impact of Stay Duration on Mental Health in International Students

This SQL-based analysis explores how the **length of stay** affects the **mental health diagnostic scores** of international students, using structured data and PostgreSQL.

---

## 📊 Objective

To determine whether the duration of stay influences:

- **Depression** scores (PHQ-9 test)
- **Social connectedness** (SCS test)
- **Acculturative stress** (ASISS test)

The project filters for international students and groups them by the number of years they’ve stayed in the host country.

---

## 🗃️ Dataset Overview

| Column Name     | Description                                                           |
|-----------------|-----------------------------------------------------------------------|
| `inter_dom`     | Type of student: `'Inter'` for international, `'Dom'` for domestic     |
| `stay`          | Length of stay in years                                               |
| `todep`         | Total score on the PHQ-9 Depression test                              |
| `tosc`          | Total score on the SCS Social Connectedness test                      |
| `toas`          | Total score on the ASISS Acculturative Stress test                    |

Only records with `inter_dom = 'Inter'` are included in the analysis.

---

## 🔍 Methodology

1. Queried the dataset using **PostgreSQL**.
2. Filtered for international students.
3. Grouped by `stay` (length of stay in years).
4. Calculated:
   - `count_int`: number of students per group
   - `average_phq`: average depression score
   - `average_scs`: average social connectedness
   - `average_as`: average acculturative stress
5. Rounded all averages to **two decimal places**.
6. Sorted the results by `stay` in **descending order**.
7. Saved the result to a DataFrame called `df`.

---

## 🧪 SQL Query Used

```sql
SELECT 
    stay,
    COUNT(*) AS count_int,
    ROUND(AVG(todep), 2) AS average_phq,
    ROUND(AVG(tosc), 2) AS average_scs,
    ROUND(AVG(toas), 2) AS average_as
FROM students
WHERE inter_dom = 'Inter'
GROUP BY stay
ORDER BY stay DESC;


