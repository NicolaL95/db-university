Selezionare tutti gli studenti nati nel 1990
{
SELECT *
FROM students
WHERE dates BETWEEN '19900101' and '19901231'
}

Selezionare tutti i corsi che valgono più di 10 crediti
{
    SELECT * 
    FROM courses 
    WHERE cfu > 10
}