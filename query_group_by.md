1. Contare quanti iscritti ci sono stati ogni anno

```sql

SELECT COUNT(*) AS "studenti_iscritti", YEAR(`enrolment_date`) AS "anno"
FROM `students`
GROUP BY YEAR(`enrolment_date`)
ORDER BY YEAR(`enrolment_date`);

```

2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio

```sql

SELECT COUNT(*) AS "numero_insegnanti", `office_address`
FROM `teachers`
GROUP BY `office_address`
ORDER BY "numero_insegnanti";

```

3. Calcolare la media dei voti di ogni appello d'esame

```sql

```

4. Contare quanti corsi di laurea ci sono per ogni dipartimento

```sql

```
