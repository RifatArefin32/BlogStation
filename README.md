# BlogStation

# Requirements
- Install python and pip
```bash
sudo apt update
sudo apt install python3 python3-pip
```
- Install `venv` Module
```bash
sudo apt install python3-venv
```

# Project setup
Create project root directory `BlogStation` and change directory to it
```bash
mkdir BlogStation
cd BlogStation
```
Set Up a Virtual Environment `env` and activate it
```bash
python3 -m venv env
source env/bin/activate
```
Install Django to the virtual environment and Save installed packages to a `requirements.txt` file
```bash
pip install django
pip freeze > requirements.txt
```
Start our Django Project `BlogStation` to the current directory
```bash
django-admin startproject BlogStation .
```
Setup `.gitignore` file
```bash
touch .gitignore
```
Initialize git repository and connect to the remote repository
```bash
git init
git add . && git commit -m "Initial commit"
git remote add origin https://github.com/RifatArefin32/BlogStation.git
git branch -M main
```
Run the project
```bash
python3 manage.py runserver
```

# Clone the project and setup to local PC
- Clone the project
- Create a virtual environment and activate it
- Install packages of `requirements.txt` on the virtual environment
```bash
pip install -r requirements.txt
```

# ERD Overview
- User: Represents a registered user of the app (Author of blog posts, commenters, etc.).
- BlogPost: Represents an individual blog post written by a user.
- Comment: Represents a comment on a blog post.
- Category: Categorizes blog posts (e.g., Technology, Health, Lifestyle).
- Tag: Tags that can be associated with blog posts (e.g., Python, Django, Web Development).
- Like: Represents a like or dislike on a blog post by a user.

## Relationships
- One-to-Many: A user can write many blog posts.
- One-to-Many: A blog post can have many comments.
- Many-to-Many: A blog post can belong to many categories, and a category can have many blog posts.
- Many-to-Many: A blog post can have many tags, and a tag can be associated with many blog posts.
- Many-to-Many: A user can like many blog posts, and a blog post can have many users who liked it.

## ERD Models

### User

| Field            | Type         | Constraints            |
|-------------------|--------------|------------------------|
| id               | Primary Key  | Auto-increment         |
| username         | String       | Unique                |
| email            | String       | Unique                |
| password_hash    | String       | Not null              |
| first_name       | String       | Not null              |
| last_name        | String       | Not null              |
| profile_picture  | String       | Optional              |
| created_at       | Timestamp    | Not null              |
| updated_at       | Timestamp    | Not null              |

---

### BlogPost

| Field            | Type         | Constraints            |
|-------------------|--------------|------------------------|
| id               | Primary Key  | Auto-increment         |
| user_id          | Foreign Key  | References `User.id`   |
| title            | String       | Not null              |
| content          | Text         | Not null              |
| status           | String       | E.g., draft, published |
| created_at       | Timestamp    | Not null              |
| updated_at       | Timestamp    | Not null              |
| published_at     | Timestamp    | Optional              |

---

### Comment

| Field            | Type         | Constraints            |
|-------------------|--------------|------------------------|
| id               | Primary Key  | Auto-increment         |
| user_id          | Foreign Key  | References `User.id`   |
| blog_post_id     | Foreign Key  | References `BlogPost.id` |
| content          | Text         | Not null              |
| created_at       | Timestamp    | Not null              |
| updated_at       | Timestamp    | Not null              |

---

### Category

| Field            | Type         | Constraints            |
|-------------------|--------------|------------------------|
| id               | Primary Key  | Auto-increment         |
| name             | String       | Unique, Not null       |
| description      | Text         | Optional              |

---

### BlogPostCategory (Join Table)

| Field            | Type         | Constraints            |
|-------------------|--------------|------------------------|
| blog_post_id     | Foreign Key  | References `BlogPost.id` |
| category_id      | Foreign Key  | References `Category.id` |

---

### Tag

| Field            | Type         | Constraints            |
|-------------------|--------------|------------------------|
| id               | Primary Key  | Auto-increment         |
| name             | String       | Unique, Not null       |

---

### BlogPostTag (Join Table)

| Field            | Type         | Constraints            |
|-------------------|--------------|------------------------|
| blog_post_id     | Foreign Key  | References `BlogPost.id` |
| tag_id           | Foreign Key  | References `Tag.id`    |

---

### Like

| Field            | Type         | Constraints            |
|-------------------|--------------|------------------------|
| id               | Primary Key  | Auto-increment         |
| user_id          | Foreign Key  | References `User.id`   |
| blog_post_id     | Foreign Key  | References `BlogPost.id` |
| created_at       | Timestamp    | Not null              |
| updated_at       | Timestamp    | Not null              |
