Contare quanti iscritti ci sono stati ogni anno{
SELECT COUNT(id), YEAR(enrolment_date) 
FROM `students` 
GROUP BY YEAR(enrolment_date)
}

Contare gli insegnanti che hanno l'ufficio nello stesso edificio{
SELECT COUNT(id), office_address 
FROM `teachers` 
GROUP BY office_address
}

Calcolare la media dei voti di ogni appello d'esame{
    SELECT AVG(vote)  as `vote_average`
    FROM `exam_student`
}

Contare quanti corsi di laurea ci sono per ogni dipartimento{
SELECT COUNT(name), department_id 
FROM `degrees`
GROUP BY department_id
}

Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia{
SELECT students.name, students.surname 
FROM students 
JOIN degrees ON degrees.id = students.degree_id 
WHERE degrees.name = 'Corso di Laurea in Economia'
}

Selezionare tutti i Corsi di Laurea del Dipartimento di Neuroscienze{
    SELECT degrees.name
FROM degrees
JOIN departments ON departments.id = degrees.department_id
WHERE departments.name = 'Dipartimento di Neuroscienze'
}

Selezionare tutti i corsi in cui insegna Fulvio Amato{
    SELECT courses.name 
    FROM course_teacher 
    JOIN courses ON course_teacher.course_id = courses.id JOIN teachers ON course_teacher.teacher_id = teachers.id 
    WHERE teachers.id = '44'
}

Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome{
    SELECT students.name, students.surname, degrees.name, departments.name 
    FROM students 
    JOIN degrees ON degree_id = students.degree_id 
    JOIN departments ON departments.id = degrees.department_id
    ORDER BY students.name, students.surname
}

Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti{
    SELECT degrees.name, courses.name, teachers.name,teachers.surname 
    FROM degrees JOIN courses ON degrees.id = courses.degree_id 
    JOIN course_teacher ON course_teacher.course_id = courses.id JOIN teachers ON course_teacher.teacher_id = teachers.id
}

Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica{
    SELECT teachers.name,teachers.surname
    FROM teachers
    JOIN course_teacher ON course_teacher.teacher_id = teachers.id
    JOIN courses ON course_teacher.course_id = courses.id
    JOIN degrees ON courses.degree_id = degrees.id
    JOIN departments ON departments.id = degrees.department_id
    WHERE departments.name = 'Dipartimento di Matematica'
}

 Selezionare per ogni studente quanti tentativi d’esame ha sostenuto per superare ciascuno dei suoi esami{
     SELECT students.name,students.surname,exam_student.exam_id, COUNT(exam_student.exam_id)
    FROM exam_student
    JOIN students ON exam_student.student_id = students.id
    JOIN exams ON exam_student.exam_id = exams.id
    GROUP BY student_id, exams.id  
 }
