## 1. 

### select * from wordform limit 10;

    wordformid | plaintext | phonetictext | stemtext | occurences 
    ------------+-----------+--------------+----------+------------
        596293 | the       | 0            | the      |      28932
        596294 | and       | ANT          | and      |      27296
        596295 | i         | I            | i        |      21120
        596296 | to        | T            | to       |      20136
        596297 | of        | OF           | of       |      17169
        596298 | a         | A            | a        |      14943
        596299 | you       | Y            | you      |      13989
        596300 | my        | M            | my       |      12950
        596301 | in        | IN           | in       |      11512
        596302 | that      | 0T           | that     |      11487
            (10 rows)

## 2.

### select * wordform ilike 'a%'

        wordformid |     plaintext     | phonetictext |     stemtext      | occurences 
    ------------+-------------------+--------------+-------------------+------------
        596294 | and               | ANT          | and               |      27296
        596298 | a                 | A            | a                 |      14943
        596316 | as                | AS           | a                 |       6048
        596324 | all               | AL           | all               |       4009
        596330 | are               | AR           | ar                |       3575
        596341 | at                | AT           | at                |       2628
        596354 | am                | AM           | am                |       2218
        596367 | an                | AN           | an                |       1835
        596410 | art               | ART          | art               |        964
        596415 | away              | AW           | awai              |        898
        596426 | any               | AN           | ani               |        816
        596428 | again             | AKN          | again             |        804
        596433 | ay                | A            | ai                |        771
        596471 | against           | AKNST        | against           |        608
        596528 | aside             | AST          | asid              |        444
        596532 | after             | AFTR         | after             |        431
        596540 | about             | ABT          | about             |        411
        596549 | answer            | ANSWR        | answer            |        389
        596555 | another           | AN0R         | anoth             |        382
        596636 | arms              | ARMS         | arm               |        281
        (....)
        (15.. row)


## 3.

### select title,genretype from work where genretype = 'p';

             title         | genretype 
    ------------------------+-----------
    Lover's Complaint      | p
    Passionate Pilgrim     | p
    Phoenix and the Turtle | p
    Rape of Lucrece        | p
    Venus and Adonis       | p


## 4. 

### select avg(totalparagraphs) as avg from work where genretype = 't';

                  avg          
    -----------------------
    1070.8181818181818182
    (1 row)

## 5. 

### select title from work where totalwords > (select avg(totalwords ) from work);

               title           
    ---------------------------
    All's Well That Ends Well
    Antony and Cleopatra
    As You Like It
    Coriolanus
    Cymbeline
    Hamlet
    Henry IV, Part I
    Henry IV, Part II
    Henry V
    Henry VI, Part I
    Henry VI, Part II
    Henry VI, Part III
    Henry VIII
    King John
    King Lear
    Love's Labour's Lost
    Measure for Measure
    Merchant of Venice
    Merry Wives of Windsor
    Much Ado about Nothing
    Othello
    Richard II
    Richard III
    Romeo and Juliet
    Taming of the Shrew
    Titus Andronicus
    Troilus and Cressida
    The Winter's Tale
    (28 rows)

## 6. 

### SELECT character.charname, speechcount, work.title FROM character LEFT JOIN character_work ON character.charid = character_work.charid LEFT JOIN work ON character_work.workid = work.workid  

                     charname                | speechcount |           title           
    ------------------------------------------+-------------+---------------------------
    First Apparition                         |           1 | Macbeth
    First Citizen                            |           3 | Romeo and Juliet
    First Conspirator                        |           3 | Coriolanus
    First Gentleman                          |           1 | Othello
    First Goth                               |           4 | Titus Andronicus
    First Murderer                           |          21 | Macbeth
    First Musician                           |           5 | Othello
    First Musician                           |          10 | Romeo and Juliet
    First Officer                            |           3 | Othello
    First Player                             |           8 | Hamlet
    First Senator                            |          33 | Coriolanus
    First Senator                            |           8 | Othello
    First Servant                            |           4 | Romeo and Juliet
    First Serving-Man                        |           5 | Henry VI, Part I
    First Soldier                            |           8 | Coriolanus
    First Watchman                           |           6 | Much Ado about Nothing
    First Watchman                           |           6 | Romeo and Juliet
    First Witch                              |          23 | Macbeth



## 7.

### select round(avg(speechcount)) as round, work.title from character join character_work on character.charid = character_work.charid join work on character_work.workid=work.workid where work.title = 'Romeo and Juliet' group by work.title;

    | round | title |

 git remote add origin git@github.com:ARGEN03/postgresql_task.git git remote add origin git@github.com:ARGEN03/postgresql_task.git


## 8. 

### select section, sum(wordcount) as sum from paragraph group by section;

    section|  sum   
    ---------+--------
        0 |   2963
        1 | 219622
        3 | 174015
        5 | 148638
        4 | 168204
        2 | 170774
    (6 rows)

## 9. 

### select  charname, speechcount from character where speechcount between 15 and 30;

       charname    | speechcount   
    ----------------+-------------   
    First Murderer |          21   
    First Witch    |          23   
    Second Witch   |          15   
    Aegeon         |          17   
    Aemilia        |          16   
    Agrippa        |          28   
    Alexas         |          15   
    ...  
    (153 rows)

## 10. 

### SELECT title, year FROM work WHERE year between 1601 and 1699;

## 11. 

### select longtitle from work where longtitle like '%the%' ;

                   longtitle                
    ----------------------------------------
    The Tragedy of Othello, Moor of Venice
    The Phoenix and the Turtle
    The Taming of the Shrew
    The Tragedy of Timon of Athens
    (4 rows)


## 12.

### select distinct section from paragraph;

    section   
    ---------         
    0         
    1         
    3         
    5         
    4         
    2  
    (6 rows) 

## 13. 

### select chapterid, description, work.title from chapter join work on chapter.workid = work.workid;

        chapterid |      description      |   title     
    -----------+-----------------------+--------------   
        18934 | Prologue.             | Henry V       
        18704 | DUKE ORSINO's palace. | Twelfth Night       
        18705 | The sea-coast.        | Twelfth Night       
        18706 | OLIVIA'S house.       | Twelfth Night       
        18707 | DUKE ORSINO's palace. | Twelfth Night       
        18708 | OLIVIA'S house.       | Twelfth Night       
        18709 | The sea-coast.        | Twelfth Night   
        ...  
        (945 rows) 

## 14.

### select paragraphnum, character.charname, character.speechcount from paragraph join character on character.charid = paragraph.charid; 

    paragraphnum |      charname      | speechcount   
    --------------+------------------- +-------------              
            3 | (stage directions) |         126              
            4 | Orsino             |          59             
            19 | Curio              |           4             
            20 | Orsino             |          59             
            21 | Curio              |           4             
            22 | Orsino             |          59             
            30 | Valentine          |           3   
    ...  
    (35465 rows)

## 15.

### select paragraph.paragraphnum, work.title, work.year from paragraph join work on paragraph.workid = work.workid;

        paragraphnum |           title           | year   
    --------------+---------------------------+-----              
            3 | Twelfth Night             | 1599              
            4 | Twelfth Night             | 1599             
            19 | Twelfth Night             | 1599             
            20 | Twelfth Night             | 1599             
            21 | Twelfth Night             | 1599             
            22 | Twelfth Night             | 1599             
            30 | Twelfth Night             | 1599   
    ...  
    (35465 rows) 






