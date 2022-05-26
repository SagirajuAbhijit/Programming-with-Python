#abhijitvarma
 import sqlite3
con = sqlite3.connect('Marks.db')
query = ''' CREATE TABLE if not exists students(RollNo INT PRIMARY KEY, Name TEXT,Maths TEXT,Python TEXT)'''
con.execute(query)
con.commit()
query = ''' INSERT Into students Values(?,?,?,?)'''
multiple_rows = [(1,'Vinay','A+','O'),(2,'Likith','F','B'),(3,'Sandy','A+','F'),(4,'Vinod','A+','A+'),(5,'Summit','B','B+')]
cursor = con.cursor()
cursor.executemany(query,multiple_rows)
con.commit()
query = ''' UPDATE students SET Maths = ? WHERE RollNo = 3 '''
cursor.execute(query,('O'))
con.commit()
query = ''' SELECT * FROM Students '''
cursor.execute(query)
all_rows = cursor.fetchall()
for row in all_rows:
    print(row)
