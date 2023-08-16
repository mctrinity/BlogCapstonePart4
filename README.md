The program is able to do the following:
-create posts (admin only)
-other users can comment on all posts
-create/register new users
-viewing of posts is available to all registered users
-authentication/CSRF are applied
-CKEditor version 4
-gravatars are generated per user and can be seen via comments

To copy data from one database to another, you'll need to follow these general steps:
Dump Data from Source Database: Dump the data from the source database into a file. This can usually be done using database-specific tools or utilities. For example, for SQLite, you can use the sqlite3 command-line tool. For other databases like MySQL or PostgreSQL, you can use tools like mysqldump or pg_dump.
Transfer Data to New Database: Transfer the dumped data file to the new computer or database server where you want to import the data.
Import Data into New Database: Import the dumped data into the new database. Again, use database-specific tools or utilities to accomplish this. For example, for SQLite, you can use the sqlite3 tool. For other databases, you'll use tools like mysql or psql.

Here's a more detailed guide for common databases:

SQLite:

On the source computer, open a terminal and navigate to the directory containing your original database file (posts.db).
Use the sqlite3 command to create a dump of the database:

On bash:
sqlite3 posts.db .dump > dump.sql
Copy the dump.sql file to the new computer.

On the new computer, open a terminal and navigate to the directory where you copied the dump.sql file.
Create a new database (if not already done) and then import the data from the dump file you created.

MySQL:

On the source computer, open a terminal and use mysqldump to create a dump of the database:

On bash
mysqldump -u username -p database_name > dump.sql
Copy the dump.sql file to the new computer.

On the new computer, open a terminal and use the mysql command to import the dump file.

PostgreSQL:

On the source computer, open a terminal and use pg_dump to create a dump of the database:

bash
pg_dump -U username -d database_name > dump.sql

Copy the dump.sql file to the new computer.

On the new computer, open a terminal and use the psql command to import the data:

bash
psql -U username -d new_database_name < dump.sql

Please note that the above commands are general guidelines and may need adjustments based on your specific setup and configuration. Also, ensure that you have the necessary permissions and credentials to perform these operations.

Once you've imported the data into the new database, make sure your Flask application is properly configured to use the new database URI, and you should be able to access the copied data.

Prequisite:
Run your main.py to create the instance folder with post.db
Run the following scripts
flask init
flask db migrate
flask db upgrade
