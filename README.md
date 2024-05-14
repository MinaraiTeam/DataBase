# DataBase

## Diagram

![MINARAI TEAM](https://github.com/MinaraiTeam/DataBase/assets/145032349/aa388bb4-5542-4032-ae9f-6c3791d88028)


## Tables
```sql
create database minarai_db;
use minarai_db;

CREATE TABLE users (
    user_id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(255),
    password VARCHAR(255),
    profile_image VARCHAR(255),
    role ENUM('standard', 'creator', 'banned')
);

CREATE TABLE categories (
    category_id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(255)
);

CREATE TABLE articles (
    article_id INT PRIMARY KEY AUTO_INCREMENT,
    title VARCHAR(255),
    preview_image VARCHAR(255),
    content LONGTEXT,
    language ENUM('ES', 'JP'),
    annex TEXT,
    country ENUM('ES', 'JP'),
    date VARCHAR(100),
    views INT,
    user_id INT,
    category_id INT,
    FOREIGN KEY (user_id) REFERENCES users(user_id),
    FOREIGN KEY (category_id) REFERENCES categories(category_id)
);

CREATE TABLE comments (
    comment_id INT PRIMARY KEY AUTO_INCREMENT,
    description TEXT,
    date VARCHAR(100),
    article_id INT,
    user_id INT,
    FOREIGN KEY (article_id) REFERENCES articles(article_id),
    FOREIGN KEY (user_id) REFERENCES users(user_id)
);
```
