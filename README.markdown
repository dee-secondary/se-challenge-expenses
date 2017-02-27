# Wave Software Development Challenge

## Set up instructions:
brew install postgresql
brew services start postgresql
brew services list 
psql

Set up for variables needed to run the flask backend API:
 export DATABASE_URL="postgresql://localhost/wave_db"
 export APP_SETTINGS="config.DevConfig"

Install requirements:
 pip install -r requirements.txt

Database migrations are handled through Alembic (Flask Migrate)

Initialize Alembic
 python manage.py db init

First migration
 python manage.py db migrate

Apply changes to db
 python manage.py db upgrade

Change datestyle in postgresql
 SET datestyle = "ISO, MDY";

Install npm and make sure you have the lates npm:
 sudo npm install npm -g

Install npm packages from package.json for frontend
 npm install

start flask app on localhost port 5000:
 python app.py

start on frontend:
 npm start

Drop table data and reset sequence (Ideally this could be make into a command in the future):
TRUNCATE TABLE table_name(s) RESTART IDENTITY;


## Assumptions:
- Expense name is not unique, because different employees could use the same name. Only employees, category and tax names are unique.

## Improvements with more time:
- Create a Summary model and the query to gather summary data should be written in sqlalchemy and not straight sql. I ran out of time to make this improvement.
- Write unit tests! 
- More user friendly fronend including allowing users to upload subsequent files after uploading their first.
- Validation for file types
- Better error handling for both the frontend and backend API 
- Keeping track of the currently uploaded file and providing a summary based on expenses that file, and not all expenses in the database. Could be done by introducing an source_id column to the expense model that keeps track of which expenses were created at the same time from the same source csv.

## General Comments:
- I was happy in building this app from scratch, which I haven't had a chance to do in a while. I also took this as an opportunity to learn a frontend framework (React). Have been away from frontend code in a couple of years, so it was a good chance to brush on my rust frontend skills. I was impressed at how easy it was to find packages/modules that made building a frontend pretty easy with Node/React.
- I wish I did have more time to spend on this to polish it up. It was tough finding more time between work & research papers for school to dedicate to this project. However, I'm glad I had a chance to work on some interesting project that wasn't related to work or school!
