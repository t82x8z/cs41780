java c
COMP 636:  Web App Assessment - S2 2024
Milestone submission due:  5pm Friday 4 October 2024 via Learn
Final submission due:  5pm Tuesday 29 October 2024 via Learn
Worth:  50% of COMP636 grade
Submit via Akoraka | Learn, with files set up and available on GitHub and PythonAnywhere.
Introduction
Te Waihora farm management simulator (FMS) is a system that models stock management on a farm. The aim is for the farmer to simulate the number of stock (cows in this case) that the farm can maintain, with the amount of pasture (grass) that it has available for the stock to eat.
Stock are kept in paddocks – a fenced area of pasture.  The paddocks can grow pasture at a certain rate per day, so the aim is to keep moving stock between paddocks so that the pasture level does not get too low.  Pasture above 1800 kg DM/ha is considered good, while levels below 1500 kg DM/ha are considered poor (below this, the ability of the grass to regrow can be affected).  Stock are managed and moved between paddocks in groups called ‘mobs’ .  Each mob is moved as a whole group and each paddock can only have one mob (otherwise the mobs would get mixed up).
The FMS simulates the ‘current date’, which can be moved ahead one day at a time, to calculate pasture growth and pasture consumption by the stock.  (To be clear: ‘current date’ is not the actual date shown by the computer’sclock.)
Terms and abbreviations:
DM              Dry matter (in kg) – the weight of the pasture with the water component removed.
DM/ha        Dry matter per hectare (kg DM/ha) = DM (in kg) divided by paddock area (in hectares).
ha                 Hectares – a measure of paddock area (size).
Pasture       Grass that is eaten by stock.
Stock           Animals – cows in this case.
Note:  The requirements presented here are not exhaustive, you are expected to apply critical thought to them, and best practices taught in the course, as a key part of the software development process. Ask clarifying questions in the in-person or online support sessions.
Download the web application files from the Assessment block on Learn.  These will get you started, including for the Milestone.  You will add more routes and templates as you develop your app.
Important
This is an individual assessment. You may not collaborate or confer with others. You may help others by verbally explaining concepts and making suggestions in general terms, but without directly showing or sharing your own code. You must develop the logical structure and the detail of your code on your own. No use of generative AI is permitted for any part of this assessment.
Code or content that is copied, shares a similar logic to others or is produced by generative AI will receive zero marks for all parties involved.
The university guidelines and policy on academic integrity can be found here.
Milestone Submission (5 marks, due 4 October)
This milestone is to ensure that your app is correctly configured, and any set-up issues are resolved early.  The milestone does not require any changes to the code and templates provided.By this date you only need to sync and share the provided fileson GitHub, provide us teacher access to your PythonAnywhere, and host the provided code on PythonAnywhere so that the web app and  provided routes run correctly.
Milestone Requirements
1)   Create a private GitHub repository called fms.
a.    Your web application (app.py, etc.) must be in the main folder of your repository (not in a subfolder)
2)    Host your web app on PythonAnywhere.
a.    Use files pulled from your GitHub repository.
b.   Your fms web app folder must be in your PythonAnywhere home directory (which should happen automatically when cloning the files from GitHub).
c.    Your MySQL database must be called fms and contain the required tables and data. 3)   The provided web application pages must load correctly in PythonAnywhere:
a.    Home page:  / route; home.html template page.
b.    Mobs page:  /mobs route; mobs.html template page.
c.    These pages require no modification of app.py or their HTML files to work. For this submission you must have:
•    Your GitHub repository setup correctly.
•    The provided files loaded in GitHub and in PythonAnywhere.
•    Your database set up on PythonAnywhere.
•    Your app hosted successfully on PythonAnywhere.
•    The / and /mobs routes working (as provided in the files).
•    Granted access to your PythonAnywhere account (set lincolnmacas teacher).
•    Granted access to your GitHub repository (invite lincolnmac or computing@lincoln.ac.nzas collaborator).
Submit the following via the link on the Learn COMP636 page:
•    Your PythonAnywhere URL (e.g., yourname1234567.PythonAnywhere.com/ )
•    Your GitHub username and repository name (e.g., yourname1234567/fms)
IMPORTANT: Do not pull further changes to your PythonAnywhere files until after you have
received your Milestone marks.  You may continue to work in the local copy on your computer in the meantime and you should also commit and pushto your GitHub repository.
In this submission we will check your GitHub, PythonAnywhere setup, including MySQL database.
Set-up Requirement
Marks Available
GitHub Repository set up and shared
1 mark
PythonAnywhere web app hosting correctly configured, including home URL and database setup, and teacher access granted
3 marks
/ and /mobs routes and pages (as provided) running on PythonAnywhere
1 mark
TOTAL
5 marks
Technical details
Current date
A session variable has been created – a dictionary called session (which is like a global variable that is stored by the browser in a cookie for the page).  It can be accessed anywhere in app.py or your template pages without needing to be passed as a value.  The current date is stored as session[‘curr_date’].  This is already initialised by the / route and is displayed on the base.html page. For testing purposes, two routes – /clear-date and /reset-date – have been provided to delete the session variable or to reset it to the project start date.  Note:  Do not create or use any other session variable values for this assessment.
Pasture
To calculate pasture growth and consumption, two global variables are provided in app.py:
-      pasture_growth_rate:  growth rate of pasture in kg of dry matter per hectare per day.
-      stock_consumption_rate:  amount of pasture in kg of dry matter eaten per animal per day. For each paddock, recalculate the pasture growth when the current date changes:
-      Pasture growth (in kg DM) per day  =  area (in ha)  x  pasture_growth_rate
-      Pasture consumption (in kg DM) per day  =  number of stock  x  stock_consumption_rate
-     Total DM  =  starting total DM  +  growth  –  consumption
-      Recalculate:  DM/ha  =  total DM  /  area
For this assessment, you don’t need to worry about mobs being in one paddock for part of the day    and another for the rest of the day.  You can assume that all mobs have been in the paddock for the whole day at the moment of calculating pasture levels.
Web application requirements
1)   On every page, include a page header which includes:  the name of the app, a navigation bar with links to the pages, plus the value of ‘current date’ (session[‘curr_date’]).
2)   Add a picture and some (brief) introductory text to the home page.
3)    Modify the page on the /mobs route to show the paddock name that each mob is in and sort alphabetically by mob name.  Improve table appearance.
4)   Create a route to list the stock (animals), grouped by mob, so that:
a.    Each mob list has its own header, including the mob name, paddock, number of stock in the mob and the average weight of the mob.  Mobs are to appear in
alphabetical mob name order.
b.    Underneath each mob header, display the details for each animal in that mob,
including its ID and age in years (as at the FMS ‘current date’).  Animals are to appear in ID order within each mob.
5)   Create a route to list the paddocks:
a.    Showing the details for each paddock.    
b.    Sorted alphabetically by paddock name. 
c.    For each paddock include:
i.   the name of the mob in that paddock (if any).
ii.   the number of stock (animals) in that paddock (if any).
d.    Highlight the paddock row background colour in yellow if DM/ha falls below 1800 kg DM/ha and in red if it falls below 1500 kg DM/ha
6)   Create a route to so that a mob can be moved代 写COMP 636: Web App Assessment – S2 2024Java
代做程序编程语言 to any other available paddock.
a.    A paddock cannot contain more than one mob at a time.
b.    Each mob can be in only one paddock at a time.
7)    Update the system so that paddocks can be edited and added by the user:
a.    New paddock IDs are assigned automatically by the database and not editable.
b.   Total DM iscalculated automatically from the area and dm/ha values that the user enters as:  total DM  =  area  x  dm/ha.  This value can’t be typed indirectly.
8)    For each paddock, calculate pasture totals based on growth and consumption (see Technical Details above):
a.    The user is able to click to move current date to the next day – from the paddocks page (so that the changes in pasture values can be observed).
b.   The pasture values for each paddock are updated when the current date changes.
General requirements
1)   The application should follow the best practices mentioned in class, even where not specifically requested.
2)    Data that is entered should be validated and errors from inappropriate data handled without crashing the web application.
3)    Information should be presented in a manner appropriate for a professional web application, such as appropriate headings, labels, and date and number formatting.
a.    Note that abbreviations ‘DM’, ‘ha’ and ‘DM/ha’ maybe used in headers and labels.
4)   General presentation and user interface should be tidy and professional making use of
Bootstrap CSS for formatting, but it does not need to be ‘fancy’ .  Clean and functional is    sufficient.  It is OK, for example, for the user to need to press a submit button to submit a form. (rather than it submitting automatically).
Report
Your report must be created using GitHub Markdown format and saved in the README.md file of
your GitHub repository.  It does not need to be a formal report – a tidy document using the following headings will be sufficient.  Write a brief project report that includes:
•   Design decisions:
Discuss the design decisions you made when designing and developing your app:  why you
created one set of pages, routes and functions to connect and interact in this way, and not in some other way.  Discuss the structural and logical options you considered.
For example, when the edit button is clicked on a page, does that open a different template for editing or does it use the same template with IF statements to enable the editing?   Did you use GET or POST to request and send data?  How, and why?  (These are just examples; you do not    have to include them in your own discussion.)  You will have considered many design
possibilities; write in plain language about your own personal decisions.     Make notes about your decisions as you work, so you do not forget them!
•   Image sources: If you use any external images in your web app,  ensure you reference the image source in your report.
•   Database questions:  Refer to the supplied fms-local.sql file to answer the following questions. Do not implement these changes in your app, just write your answers in your report:
1.    What SQL statement creates the mobs table and defines its fields/columns?  (Copy and paste the relevant lines of SQL.)
2.    Which lines of SQL script. sets up the relationship between the mobs and paddocks tables?
3.   The current FMS only works for one farm.  Write SQL script. to create a new table called farms, which includes a unique farm ID, the farm name, an optional short   description and the owner’s name.  The ID can be added automatically by the
database.  (Relationships to other tables not required.)
4.    Write an SQL statement to add details for an example farm to your new farms table,   which would be suitable to include in your web application for the users to add farms in afuture version.  (Type in actual values, don’t use %smarkers.)
5.    What changes would you need to make to other tables to incorporate the new farms table?  (Describe the changes.  SQL script. not required.)
Data Model

Model Notes:
Child table.field *
(refers to)
Parent table.field
mobs.paddock_id

paddocks.id
stock.mob_id

mobs.id
* the ‘Foreign Key’
Project Constraints
You must:
•   Use only the COMP636 technologies (Python  Flask, Bootstrap CSS, MySQL).  Do not use SQLAlchemy or ReactJS (or other similar technologies or libraries) in your solution.
o Do not use any scripts, including JavaScript. and do not write your own CSS (use Bootstrap).
o Exceptions:  You may use:
The Bootstrap  at the bottom of base.html.Very simple inline JavaScript, e.g., to auto-submit a form.  (Not required or expected).<br>Style. attributes for columnwidths in tables<br>•   Use the provided SQL files to create a database within your local MySQL and in PythonAnywhere.  Each script. also populates the database with initial data.<br>o You can re-run the appropriate SQL script. at anytime to reset your data back to the original version and remove any changes you made to it (if it starts to get messy during testing).<br>o You may modify data in your database for testing purposes and may add new data, but you must not modify the schema.<br>o Markers will not change the structure of the data, but will modify or add alternative data to your database as part of the marking process.  You can rely on table names and columns<br>staying the same, but the data in the rows in the tables may change.<br>•   Use the provided files to develop a Flask web app that:<br>o Must be in a top-level folder called ‘fms’ (locally and on PythonAnywhere).<br>o Meets the functional requirements.<br>o Is appropriately commented.<br>o Connects to your database.<br>o Uses %s to insert values into SQL statements.<br>o Provides appropriate routes for the different functions.<br>o Provides templates and incorporates HTML forms to take input data.<br>o Uses Bootstrap CSS to provide styling and formatting.<br>•   Include your report in your GitHub README.md file as outlined earlier.<br>o This report must be created using GitHub Markdown and saved in the README.md file of your GitHub repository.<br>•   Create a private GitHub repository called fms that contains:<br>o All Python, HTML, images and any other required files for the web app.<br>o Your repository must have a .gitignore file and therefore not have a copy of your virtual environment.<br>o A requirements.txt file showing the required pip packages.<br>o Your project report as the README.md document.<br>o Add lincolnmac (computing@lincoln.ac.nz) as a collaborator to your GitHub repository.<br>o Your repository must show a minimum of two commits per week after the milestone submission (but do not pull to PythonAnywhere until after your Milestone has been<br>marked).<br>•   Host your system (including database) using PythonAnywhere.<br>o Add lincolnmacas your “teacher” via Account > Education.<br>o The webapp must be in a directory called ‘fms’ in the home directory.<br>Project Hints<br>Create your GitHub repository first and create all your required code and files in your local folder, then pushto GitHub.com and clone/ pull changes through to PythonAnywhere.<br>PythonAnywhere is case sensitive in ways that your local web application is not.  So test your app frequently, as you develop it.  We will mark the PythonAnywhere version of your app.<br>Spend sometime sketching and planning the structure of your application before you start<br>developing.  Think about which features could share the same (or nearly the same) templates. Remember that you can nest templates (templates within templates).<br>Make notes of your design decisions, compromises, workarounds, etc. as you develop your web app. Otherwise afterwards you may struggle to remember all of the issues you worked through, when it    comes time to discuss those design decisions in your report.  Do not include masses of insignificant    decisions in your report though.<br>The requirements in this project brief are not exhaustive, you are expected to apply critical thought and think about the user experience of the web application.<br><br><br>Final Submission (95 marks, due 29 Oct)<br>Submit your URLs again via the final submission link on the Learn COMP636 page:<br>•    Your PythonAnywhere URL (e.g., yourname1234567.PythonAnywhere.com/ )<br>•    Your GitHub username and repository name (e.g., yourname1234567/fms)<br>This confirms where your work is and tells us that your final submission is ready for marking.<br><br><br><br><br><br> &nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp<br>加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
