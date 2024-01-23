# join esercizi bonus

![Alt text](<Screenshot 2024-01-23 144214.png>)

1) 
SELECT `courses`.`name` AS `nome_corso`, `degrees`.`name` 
FROM `degrees` 
INNER JOIN `courses` ON `degrees`.`id` = `courses`.`degree_id` WHERE `degrees`.`name` = 'corso di laurea in informatica';

2) 
SELECT `courses`.`id` AS `id_corso`, `exams`.`date`, `exams`.`hour`, `exams`.`location`, `exams`.`address`
FROM `courses` 
INNER JOIN `exams` 
ON `courses`.`id` = `exams`.`course_id`
WHERE `courses`.`id` = 144;

3) 
SELECT `degrees`.`name`, `departments`.`name`
FROM `departments`
INNER JOIN `degrees`
ON `departments`.`id` = `degrees`.`department_id`
WHERE `degrees`.`name` = "Corso di Laurea in Diritto dell'Economia"

4) 
SELECT  `degrees`.`name`, `exams`.`date`, `exams`.`id`
FROM `exams`
INNER JOIN `exam_student`
INNER JOIN `students`
INNER JOIN `degrees`
ON  `exams`.`id` = `exam_student`.`exam_id` AND `exam_student`.`student_id` = `students`.`id` AND `students`.`degree_id` = `degrees`.`id`
WHERE `degrees`.`name` = 'Corso di Laurea Magistrale in Fisica'

5) 
SELECT `degrees`.`name`, `teachers`.`name` 
FROM `teachers` 
INNER JOIN `courses` 
INNER JOIN `course_teacher` 
INNER JOIN `degrees` 
ON `teachers`.`id` = `course_teacher`.`teacher_id` AND `course_teacher`.`course_id` = `courses`.`id` AND `courses`.`degree_id` = `degrees`.`id` 
WHERE `degrees`.`name` = 'Corso di Laurea in lettere';

6) 
SELECT `students`.`registration_number`
FROM `students` 
WHERE `students`.`name` = 'mirco' AND `students`.`surname` = 'messina'

7) 
SELECT AVG( `exam_student`.`vote`) AS `voto_medio_per_corso`, `exams`.`course_id`, `degrees`.`name`
FROM `exams`
INNER JOIN `exam_student`
INNER JOIN `students`
INNER JOIN `degrees`
ON  `exams`.`id` = `exam_student`.`exam_id` AND `exam_student`.`student_id` = `students`.`id` AND `students`.`degree_id` = `degrees`.`id`
GROUP BY `exams`.`course_id`, `degrees`.`name`
ORDER BY `voto_medio_per_corso` DESC