1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

```sql

SELECT `students`.*,
		`degrees`.`name`,
        `degrees`.`level`
FROM `degrees`
INNER JOIN `students`
ON `degrees`. `id` = `students`.`degree_id`
WHERE
`degrees`.`name` = "Corso di Laurea in Economia";

```

2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di
   Neuroscienze

```sql

SELECT `departments`.*,
	   `degrees`.`name`,
       `degrees`.`level`,
       `degrees`.`address`
FROM `departments`
INNER JOIN `degrees`
ON `departments`.`id` = `degrees`.`department_id`
WHERE `degrees`.`level` = "magistrale" AND
	  `departments`.`name` = "Dipartimento di Neuroscienze"

```

3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

```sql

SELECT `teachers`.`id` AS `teacher_id`,
	   `teachers`.`name`,
       `teachers`.`surname`,
       `courses`.`id` AS `course_id`,
	   `courses`.`name`,
	   `courses`.`period`,
       `courses`.`year`,
       `courses`.`cfu`
FROM `teachers`
INNER JOIN `course_teacher`
ON `teachers`.`id` = `course_teacher`.`teacher_id`
INNER JOIN `courses`
ON `courses`.`id` = `course_teacher`.`course_id`
WHERE `teachers`.`id` = 44

```

4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui
   sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e
   nome

```sql

SELECT `students`.`id` AS `student_id`,
	   `students`.`name` AS `student_name`,
       `students`.`surname` AS `student_surname`,
       `students`.`date_of_birth`,
       `degrees`.`id` AS `degree_id`,
       `degrees`.`name` AS `degree_name`,
       `degrees`.`level`,
       `degrees`.`website` AS `degree_website`,
       `departments`.`id` AS `department_id`,
       `departments`.`name` AS `department_name`,
       `departments`.`address`,
       `departments`.`email`,
       `departments`.`website` AS `department_website`

FROM `students`
INNER JOIN `degrees`
ON `students`.`degree_id` = `degrees`.`id`
INNER JOIN `departments`
ON `degrees`.`department_id` = `departments`.`id`
ORDER BY `students`.`surname` ASC, `students`.`name` ASC

```

5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

```sql

SELECT `degrees`.`id` AS `degree_id`,
	   `degrees`.`name` AS `degree_name`,
       `degrees`.`level`,
       `degrees`.`email` AS `degree_email`,
       `courses`.`id` AS `course_id`,
       `courses`.`name` AS `course_name`,
       `courses`.`period`,
       `courses`.`year`,
       `courses`.`cfu`,
       `teachers`.`id` AS `teacher_id`,
       `teachers`.`name` AS `teacher_name`,
       `teachers`.`surname` AS `teacher_surname`,
       `teachers`.`email` AS `teacher_email`

FROM `degrees`
INNER JOIN `courses`
ON `degrees`.`id` = `courses`.`degree_id`
INNER JOIN `course_teacher`
ON `courses`.`id` = `course_teacher`.`course_id`
INNER JOIN `teachers`
ON `teachers`.`id` = `course_teacher`.`teacher_id`
ORDER BY `degrees`.`name`, `courses`.`name`, `teachers`.`surname`;

```

6. Selezionare tutti i docenti che insegnano nel Dipartimento di
   Matematica (54)

```sql

SELECT DISTINCT
	   `teachers`.`id` AS `teacher_id`,
	   `teachers`.`name` AS `teacher_name`,
       `teachers`.`surname` AS `teacher_surname`,
       `teachers`.`email`,
	   `departments`.`id` AS `department_id`,
       `departments`.`name` AS `department_name`,
       `departments`.`website`
FROM `teachers`
INNER JOIN `course_teacher`
ON `teachers`.`id` = `course_teacher`.`teacher_id`
INNER JOIN `courses`
ON `courses`.`id` = `course_teacher`.`course_id`
INNER JOIN `degrees`
ON `courses`.`degree_id` = `degrees`.`id`
INNER JOIN `departments`
ON `degrees`.`department_id` = `departments`.`id`
WHERE `departments`.`name` = "Dipartimento di Matematica"
ORDER BY `teachers`.`name` ASC

```

7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti
   per ogni esame, stampando anche il voto massimo. Successivamente,
   filtrare i tentativi con voto minimo 18.

```sql

```
