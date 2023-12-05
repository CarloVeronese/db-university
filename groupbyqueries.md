QUERY 1:
- SELECT YEAR(`enrolment_date`) `enrolment_year`, COUNT(`students`.`id`) `students_enrolled` FROM `students` GROUP BY YEAR(`enrolment_date`);

QUERY 2:
- SELECT `office_address`, COUNT(*) AS `teachers_in_address` FROM `teachers` GROUP BY `teachers`.`office_address`;

QUERY 3:
- SELECT `exam_id`, AVG(`vote`) AS `avg_score` FROM `exam_student` GROUP BY `exam_id`;

QUERY 4:
- SELECT `departments`.`name` as `department`, COUNT(*) AS `number_of_degrees` FROM `degrees` INNER JOIN `departments` ON `departments`.`id` = `degrees`.`department_id` GROUP BY `department_id`;