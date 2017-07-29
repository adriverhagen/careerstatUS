# careerstatUS
SQLlite3 project based on labor statistics US data 2014-24
data found here:
I use only data from table 1.7

Start to make database using SQLite3
make new .db file by opening terminal and >sqlite3 DATABASENAME
then create table + import data or import from data(where first row is column title)
then check schema of table
then start queering.

Code look like this

adrianas-Air:~ Adriver$ sqlite3 occupationUS
SQLite version 3.8.5 2014-08-15 22:37:57
Enter ".help" for usage hints.
sqlite> .mode csv
sqlite> .import /Users/Adriver/Desktop/occupationdatas.csv occupation ;
Usage: .import FILE TABLE
sqlite> .schema occupation
CREATE TABLE occupation(
  "title" TEXT,
  "code" TEXT,
  "type" TEXT,
  "e_2014" TEXT,
  "e_2024" TEXT,
  "change_number" TEXT,
  "change_percent" TEXT,
  "self_e_percent_2014" TEXT,
  "openings" TEXT,
  "wage" TEXT,
  "education" TEXT,
  "experience" TEXT,
  "trainingneed" TEXT)
  
now I can queery from it! So let's get going.

How many occupations are there?
sqlite> Select Count(*) from occupation;
1091

But we know this is not ture because in the data set we also have totals. The occupation column is actually a category tree, which is not representated in our data.

Also problem appears when I select MAX(wage) from occupation, because it is TEXT value we get NA....
I wonder wether it was possible to ALTER TABLE, but with SQLite it is not possible. This is a limitation of SQlite3, so I am only left to create new table. Table was created upon import of csv, so I wonder where do I make the value of the column as a number in CSV.








