# Data-Visualization-Using-Streamlit-and-plotly
###Python Cloning in Pycharm
     ######From the main menu, choose Git | Clone.
     ######In the Version control drop-down, select Git.
     ######Specify the URL of the remote repository that you want to clone.
     ######In the Directory field, enter the path to the folder where your local repository will be created.
     ######Click Clone
 ###Readjsonfile 
            
          '''import json
              with open('filename.json', 'r') as f:
                data = json.load(f)
                  # assuming entry was a json array
                for entry in data:
                 # use format "entry['myfield']" to access named fields
                     print(entry)'''
  
###MYSQL-PYTHON Connector
The recommended way to install Connector/Python is via pip.
                     ''' pip install mysql-connector-python'''
                        ''' import mysql.connector 

                            # Connect to sql
                             Database = mysql.connector.connect(
                             host="local host",
                             user="your username",
                              password="your password")

                               #Get a cursor
                               Cursor = Database.cursor()
                               Cursor.execute("CREATE DATABASE databasename")
                               # Close connection
                               Database.close()'''
####creating tables in sql and inserting data from json file
                            '''DataBase = mysql.connector.connect(
                                 host="localhost",
                                 username="username",
                                 password="yourpassword",
                                 database="phone_pe_pulse"
                                   )
                                 Cursor = Database.cursor()
                                # Cursor to the database
                                  Cursor = DataBase.cursor()'''
 
     ### Creating  table
                 # creating table for transactions data of first quarter q1 for the year 2018
                 # similarly we create tables for transactions data of four quarters q1,q2,q3,q4 for the years 2019,2020,2021,2022
                         '''TableName ="CREATE TABLE transactions_jfmq18
                                           (
                                              Name VARCHAR(255),
                                              Type VARCHAR(255),
                                              Count int,
                                              Amount Float
                                            );"  
 
                                 Cursor.execute(TableName)
                                 print("transactions_jfm18 is Created in the Database")
                                 return
                                  # Calling CreateTable function
                                 CreateTable()'''
   
   ####creating table for users data of four quarters q1,q2,q3,q4 for the years 2018,2019,2020,2021,2022
   
       '''TableName ="CREATE TABLE users_jfmq18
                (
                    Name VARCHAR(255),
                    Count int,
                    Percentage Float
                  );"'''
   
   
   ####creating table for top 10 states of transactions data of four quarters q1,q2,q3,q4 for the years 2018,2019,2020,2021,2022
         '''TableName ="CREATE TABLE state_jfmq18
                (
                    Name VARCHAR(255),
                    Type VARCHAR(255),
                    Count int,
                    Amount Float
                  );"'''
   
    ###creating table for top 10 states of transactions data of four quarters q1,q2,q3,q4 for the years 2018,2019,2020,2021,2022
              '''TableName ="CREATE TABLE users_top_jfmq18
                (
                    Name VARCHAR(255),
                    registered_users int,
                  );"'''  
     ####inserting data from df to database
                    '''sql_insert = "INSERT INTO users_top_jfm18(Name,registered_users) VALUES (%s, %s)"
                       val = [x for x in df1.agg(tuple, 1)]
                       print(val)
                       Cursor.executemany(sql_insert, val)
                      DataBase.commit()
                      print(Cursor.rowcount, "details inserted")'''
                      
                  
   ##USING STREAMLIT
   with streamlit the structured data are visualized using dropdowns and charts
               '''st.title("Phone pe pulse ")
                  st.header("INDIA")
                  selection = st.sidebar.selectbox("details?", ("Transactions", 'Users'))
                  with st.sidebar:
                  year_select = st.selectbox(
                  "Choose a year"("2018", "2019", "2020", "2021", "2022"))
                   year_quarter = st.radio("year_quarter: ", ('Q1(Jan-Mar)', 'Q2(Apr-Jun)', "Q3(Jul-Sep)", "Q4(Oct-Dec)"))'''
    
   ##Fetching data from database
                 '''if selection == "Transactions":
                       if year_select == '2018':
                          if year_quarter == 'Q1(Jan-Mar)':
                             Cursor.execute("SELECT * FROM Transactions_JFM18")
                             result = Cursor.fetchall()
                             df = pd.DataFrame(result, columns=['name', 'type', 'count', 'amount'])'''
   ##visualization using plotly
                  '''import plotly.express as px'''
                 '''' def users_display(df1):
                           st.title("Users of Different Brands")
                               fig = px.scatter(df1, x="Percentage", y="Count", size="Count", color="Percentage", hover_name="Name",
                                     log_x=True,
                                     size_max=60,
                                      )
                       st.plotly_chart(fig, theme=None, use_container_width=True)'''
          ###### scatter plot is used to display different brand users of phone pe
          

   
