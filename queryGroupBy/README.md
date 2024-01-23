# GROUP BY 

![Alt text](<img/Screenshot 2024-01-23 144300.png>)

1) 
SELECT COUNT(`id`) AS `numero_studenti`, YEAR(`enrolment_date`) AS `anno_iscrizione`
FROM `students`
GROUP BY  `anno_iscrizione`;

2) 
SELECT COUNT(`id`) AS `numero_insegnanti`, `office_address`
FROM `teachers`
GROUP BY `office_address`;

3)
SELECT AVG(`vote`) AS `media_voto`, `exam_id`
FROM `exam_student` 
GROUP BY `exam_id`;

4)
SELECT  `department_id`, COUNT(`id`) AS `numero corsi`
FROM `degrees`
GROUP BY  `department_id`
