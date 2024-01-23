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