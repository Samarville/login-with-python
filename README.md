# login-with-python
login with python using css, html5, mysql
--python--
import cgi, cgitb
import mysql.connector

formData = cgi.FieldStorage()
username = formData.getvalue('username')
password = formData.getvalue('password')
print("Content-Type: text/html;charset=utf-8")
print() # <----------- addtional newline for header/body separation.


cnx = mysql.connector.connect(user='root', password='',
                              host='localhost',
                              database='*******')

#Query
mycursor = cnx.cursor()
mycursor.execute("SELECT * FROM new_table WHERE name = '%s' AND password = '%s'" % (username, password))
myresult = mycursor.fetchall()

#this is for me to check if user found with this username or password.
for x in myresult:
  myvariable = x

try:
    if myvariable is None: # The variable
        print('It is None')
except NameError:
    print ("Sorry you have entered wrong login details.")
else:
    print("Welcome to the page")
    

