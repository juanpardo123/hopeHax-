Check out our Deployed Site Here: https://hopehax.onrender.com/

Dependencies used:
Node.js
Nodemon 
Axios 
Body-parser 
Bcrypt
Dbeaver 
Express
MailChimp

An interactive web app design that has intuitive features. 
Home user login or create an account - users can enter in details such as height, weight, and choose a theme. 
Foods and recipes are able to be saved to the user's account.

Dashboard - a graph of calories consumed and calories remaining 
Another graph to break down proteins vs carbs vs fats consumption for the user.

Search bar at the top will lead to nutrition information for specific food items and that information is able to be saved for foods and recipes. 
Search bar on the recipes page will lead to specific recipes and caloric information for them. 

Information is sent to the sql database and saved for individual users and users can track nutrition progress. 

Blog - added to post recipes and send comments to share with others. 

Newsletter - once a user signs up a newsletter will be sent to their email.


Database is currently connected to an online hosted DB. If a local database is implemented SQL tables must be initialized.

SQL initialization code:

CREATE TABLE UserLogins (
  ID INT PRIMARY KEY AUTO_INCREMENT,
  Username VARCHAR(50) NOT NULL,
Password VARCHAR(60) NOT NULL,
  LoginTime TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);


CREATE TABLE postMessages (
  messageID INT PRIMARY KEY AUTO_INCREMENT,
  postID VARCHAR(50) NOT NULL,
  messagerUsername VARCHAR(50) NOT NULL,
  message VARCHAR(2500) NOT NULL,
  commentTime TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE UserFoods (
  User_ID INT,
  Food_Name VARCHAR(50) NOT NULL,
  Food_Calories DECIMAL(10, 2) NOT NULL,
  Food_Protein DECIMAL(10, 2) NOT NULL,
  Food_Fats DECIMAL(10, 2) NOT NULL,
  Food_Carbs DECIMAL(10, 2) NOT NULL,
  Food_Image VARCHAR(100) NOT NULL,
  AddedTime TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  FOREIGN KEY (User_ID) REFERENCES UserLogins(ID)
);

CREATE TABLE UserInfo (
  User_ID INT ,
  User_name varchar (50),
  User_height varchar (50),
  User_weight varchar (50),
  User_target_calories INT,
  User_preferences varchar (50),
  AddedTime TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  FOREIGN KEY (User_ID) REFERENCES UserLogins(ID)
);



CREATE TABLE UserRecipes (
  User_ID INT,
  Recipe_Name VARCHAR(2000) NOT NULL,
  Recipe_Image VARCHAR(2000) NOT NULL,
  Recipe_Calories VARCHAR(50) NOT NULL,
  Recipe_TotalWeight VARCHAR(50) NOT NULL,
  Recipe_TotalTime VARCHAR(50) NOT NULL,
  Recipe_Yield VARCHAR(50) NOT NULL,
  Recipe_MealType VARCHAR(100) NOT NULL,
  Recipe_URL VARCHAR(2000)NOT NULL,
  Recipe_Ingredients VARCHAR(2000) NOT NULL,
  AddedTime TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  RecipeID INT PRIMARY KEY auto_increment,
  FOREIGN KEY (User_ID) REFERENCES UserLogins(ID)
);

CREATE TABLE UserPosts (
  User_ID INT,
  Recipe_Name VARCHAR(2000) NOT NULL,
  Recipe_Image VARCHAR(2000) NOT NULL,
  Recipe_Calories VARCHAR(50) NOT NULL,
  Recipe_TotalWeight VARCHAR(50) NOT NULL,
  Recipe_TotalTime VARCHAR(50) NOT NULL,
  Recipe_Yield VARCHAR(50) NOT NULL,
  Recipe_MealType VARCHAR(100) NOT NULL,
  Recipe_URL VARCHAR(2000)NOT NULL,
  Recipe_Ingredients VARCHAR(2000) NOT NULL,
  Post_Message VARCHAR(2000) NOT null,
  AddedTime TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  PostID INT PRIMARY KEY auto_increment,
  FOREIGN KEY (User_ID) REFERENCES UserLogins(ID)
);




ALTER TABLE UserPosts ADD COLUMN UserName VARCHAR(50) NOT null

ALTER TABLE UserRecipes MODIFY Recipe_Image VARCHAR(2000) NOT null

ALTER TABLE UserRecipes ADD COLUMN RecipeID INT PRIMARY KEY auto_increment

ALTER TABLE UserFoods ADD COLUMN food_quantity int 
ALTER TABLE UserFoods ADD COLUMN food_quantity int 
ALTER TABLE UserFoods ADD COLUMN food_entry_ID int primary key auto_increment





 
