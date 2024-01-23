# JOIN QUERY
![Alt text](<Screenshot 2024-01-23 144341.png>)

1) 
SELECT `degrees`.`name` AS `nome_corso`, `students`.`name` AS `nome_studente`
FROM `degrees` 
INNER JOIN `students`
ON `degrees`.`id` =  `students`.`degree_id`
WHERE `degrees`.`name` = 'Corso di Laurea in Economia'
ORDER BY `students`.`name`;

2) 
SELECT `degrees`.`name`,  `departments`.`name`
FROM `departments` 
INNER JOIN `degrees` 
ON `departments`.`id` = `degrees`.`department_id` 
WHERE `degrees`.`name` LIKE 'Corso Di Laurea Magistrale%' AND `departments`.`name` = 'Dipartimento di Neuroscienze';

3) 
SELECT `courses`.`name`, `teachers`.`name`, `teachers`.`id`
FROM `course_teacher` 
INNER JOIN `courses`
INNER JOIN `teachers`
ON `course_teacher`.`teacher_id` = `teachers`.`id` AND `course_teacher`.`course_id` = `courses`.`id`
WHERE `teachers`.`name` LIKE 'Fulvio%';

4) 
SELECT `students`.`name`, `students`.`surname`, `degrees`.`name` AS `nome_corso`, `departments`.`name`
FROM `students` 
INNER JOIN `degrees`
INNER JOIN `departments`
ON `students`.`degree_id` = `degrees`.`id` AND `degrees`.`department_id` = `departments`.`id`
ORDER BY `students`.`name` , `students`.`surname`

5) 
SELECT `degrees`.`name` AS `nome_corso`, `teachers`.`name` AS `nome_insegnante`, `courses`.`name` AS `tipo_di_corso`
FROM `courses` INNER JOIN `degrees` INNER JOIN `course_teacher` 
INNER JOIN `teachers` 
ON `degrees`.`id` = `courses`.`degree_id` AND `courses`.`id` = `course_teacher`.`course_id`  AND `teachers`.`id` = `course_teacher`.`teacher_id`
ORDER BY `teachers`.`name`

6) 
SELECT `teachers`.`name`, `departments`.`name`
FROM `teachers` 
INNER JOIN `course_teacher`
INNER JOIN `courses`
INNER JOIN `degrees`
INNER JOIN `departments`
ON `teachers`.`id` = `course_teacher`.`teacher_id` AND `course_teacher`.`course_id` = `courses`.`id` AND `courses`.`degree_id` = `degrees`.`id` AND `degrees`.`department_id` = `departments`.`id`
WHERE `departments`.`name` = 'Dipartimento di Matematica'

7)  filtro per numero di tentativi per ogni esame
SELECT `students`.`name`,COUNT(`exams`.`course_id`) AS `numero_tentativi`, `exams`.`course_id`
FROM `exam_student` 
INNER JOIN `exams` 
INNER JOIN `students` ON `exam_student`.`exam_id` = `exams`.`id` AND `exam_student`.`student_id` = `students`.`id` 
GROUP BY `students`.`name`, `exams`.`course_id` ;

7) filtro per numero di tentativi per ogni esame con voto massimo
SELECT `students`.`name`,COUNT(`exams`.`course_id`) AS `numero_tentativi`, `exams`.`course_id`, MAX(`exam_student`.`vote`)
FROM `exam_student` 
INNER JOIN `exams` 
INNER JOIN `students` ON `exam_student`.`exam_id` = `exams`.`id` AND `exam_student`.`student_id` = `students`.`id` 
GROUP BY `students`.`name`, `exams`.`course_id` ;

7) filtro studenti ed esami con voto minimo 18
SELECT `students`.`name`,COUNT(`exams`.`course_id`) AS `numero_tentativi`, `exams`.`course_id`, `exam_student`.`vote`
FROM `exam_student` 
INNER JOIN `exams` 
INNER JOIN `students` ON `exam_student`.`exam_id` = `exams`.`id` AND `exam_student`.`student_id` = `students`.`id` 
WHERE `exam_student`.`vote` = '18'
GROUP BY `students`.`name`, `exams`.`course_id` ;
