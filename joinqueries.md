QUERY 1:
- SELECT `degrees`.`name` AS `degree_name`, `students`.`name`, `surname`, `registration_number` FROM `students` INNER JOIN `degrees` ON `degrees`.`id` = `students`.`degree_id` WHERE `degrees`.`name` = 'Corso di Laurea in Economia';

QUERY 2:
- SELECT `departments`.`name`, `degrees`.* FROM `degrees` INNER JOIN `departments` ON `departments`.`id` = `degrees`.`department_id` WHERE `degrees`.`level` = 'magistrale' AND `departments`.`name` = 'Dipartimento di Neuroscienze';

QUERY 3:
- SELECT CONCAT( `teachers`.`name`,' ', `surname`) AS `teacher_full_name`, `courses`.`name` AS `course_name` FROM `teachers` INNER JOIN `course_teacher` ON `course_teacher`.`teacher_id` = `teachers`.`id` INNER JOIN `courses` ON `course_teacher`.`course_id` = `courses`.`id` WHERE `teacher_id` = 44;

QUERY 4:
- SELECT CONCAT(`surname`, ' ', `students`.`name`) AS `full_name`, `degrees`.*, `departments`.* FROM `students` INNER JOIN `degrees` ON `degrees`.`id` = `students`.`degree_id` INNER JOIN `departments` ON `degrees`.`department_id` = `departments`.`id` ORDER BY `full_name` ASC;

QUERY 5:
- SELECT * FROM `degrees` INNER JOIN `courses` ON `degrees`.`id` = `courses`.`degree_id` INNER JOIN `course_teacher` ON `courses`.`id` = `course_teacher`.`course_id` INNER JOIN `teachers` ON `teachers`.`id` = `course_teacher`.`teacher_id`;

QUERY 6:
- SELECT DISTINCT `departments`.`name` AS `department_name`, `teachers`.* FROM `teachers` INNER JOIN `course_teacher` ON `course_teacher`.`teacher_id` = `teachers`.`id` INNER JOIN `courses` ON `course_teacher`.`course_id` = `courses`.`id` INNER JOIN `degrees` ON `courses`.`degree_id` = `degrees`.`id` INNER JOIN `departments` ON `degrees`.`department_id` = `departments`.`id` WHERE `departments`.`name` = 'Dipartimento di Matematica';

QUERY 7 (BONUS)
- SELECT CONCAT(`students`.`name`, ' ',`students`.`surname`) AS `student`, `courses`.`name`, COUNT(`exams`.`id`) AS `attempts`, MAX(`exam_student`.`vote`) AS `max_score`
FROM `students`
INNER JOIN `exam_student`
ON `students`.`id` = `exam_student`.`student_id`
INNER JOIN `exams`
ON `exam_student`.`exam_id` = `exams`.`id`
INNER JOIN `courses`
ON `courses`.`id` = `exams`.`course_id`
WHERE `exam_student`.`vote` >= 18
GROUP BY `students`.`id`, `courses`.`id`