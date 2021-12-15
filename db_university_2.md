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
