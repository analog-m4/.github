<div align="center">
  <img width="350" alt="Screenshot 2023-12-10 at 00 24 43" src="https://github.com/analog-m4/.github/assets/126308696/4da02fb5-952b-4c79-9621-2f06638a8d18">
  
## [Deployed Link](https://analog-fe.vercel.app/)

</div>

## Table of Contents

[Abstract](#abstract) |
[Application Details](#application-details) |
[Preview](#preview) |
[Technologies](#technologies) |
[Database Schema](#database-schema) |
[Endpoints](#endpoints) |
[Contributors](#contributors) 

## Abstract

Analog is the ultimate to-do list application.  With this application, users can easily manage tasks, organize projects, and write notes.  With newly implemented features such as a whiteboard to plan in real-time and file uploads to utilize external resources, it will now be easier than ever to gather your thoughts and create the perfect strategy for your personal ventures!

This project served as our group's capstone, fulfilling the graduation requirements of Turing School of Software and Design. For further information on Capstone requirements, please visit: [Capstone Project](https://mod4.turing.edu/projects/capstone/)

## Application Details

This project utilizes service-oriented architecture, enabling the frontend to consume both the application's main database API and the AWS S3-specific API.  This design choice was created for easier scaliability, easier maintanence needs, and to properly utilize the different skillsets and tech stacks that each group member excels at.

See the respective repositories for thier installation instructions:

[Frontend Code Repository](https://github.com/analog-m4/analog_fe)

[Backend Code Repository](https://github.com/analog-m4/analog_be)

[AWS S3 Repository](https://github.com/analog-m4/s3_direct_upload_microservice)

## Preview
<img width="650" alt="Screenshot 2023-12-10 at 00 34 59" src="https://github.com/analog-m4/.github/assets/126308696/e9177493-fb3f-4e03-8c34-ae4b38f3ca11">

<details>
  
<summary>
More Images
</summary> 
<img width="650" alt="Screenshot 2023-12-10 at 00 38 21" src="https://github.com/analog-m4/.github/assets/126308696/57c32404-28b8-4a25-b164-028600376730">

Analog 1.0

<img width="650" alt="Screenshot 2023-12-10 at 00 46 08" src="https://github.com/analog-m4/.github/assets/126308696/3918a39d-b024-4f67-ba3e-8746d579add5">

Analog 1.0 Whiteboard

<img width="650" alt="Screenshot 2023-12-10 at 00 46 08" src="https://github.com/analog-m4/.github/assets/126308696/a677af76-c706-4c89-97fa-882e667aef50">

Analog 2.0

<img width="650" alt="Screenshot 2023-12-10 at 00 46 08" src="https://github.com/analog-m4/.github/assets/126308696/c091ead2-4e35-4fbd-9e65-2aad6d1c9529">

Analog 2.0 Dark Mode

</details>

## Videos
![Jan 12 2024: Eval Video](https://www.youtube.com/watch?v=85pB4Ev7b5o)

## Technologies
- React
- Redux
- Tailwind CSS
- Bootstrap
- Ruby 3.2.2
- Rails 7.08
- Gems:
  - capybara | factory_bot_rails | faker | jsonapi-serializer |  rack-cors | rspec-rails | shoulda-matchers | simplecov
- Websockets
- CI with GitHub Actions
- Postman
- Heroku (with CD)
- AWS

![React](https://img.shields.io/badge/react-%2320232a.svg?style=for-the-badge&logo=react&logoColor=%2361DAFB)
![Redux](https://img.shields.io/badge/Redux-764ABC.svg?style=for-the-badge&logo=Redux&logoColor=white)
![TailwindCSS](https://img.shields.io/badge/tailwindcss-%2338B2AC.svg?style=for-the-badge&logo=tailwind-css&logoColor=white)
![React Router](https://img.shields.io/badge/React_Router-CA4245?style=for-the-badge&logo=react-router&logoColor=white)
![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E)
![HTML5](https://img.shields.io/badge/html5-%23E34F26.svg?style=for-the-badge&logo=html5&logoColor=white) 
![CSS3](https://img.shields.io/badge/css3-%231572B6.svg?style=for-the-badge&logo=css3&logoColor=white)
![Cypress](https://img.shields.io/badge/Cypress-17202C.svg?style=for-the-badge&logo=Cypress&logoColor=white)
![Ruby](https://img.shields.io/badge/ruby-%23CC342D.svg?style=for-the-badge&logo=ruby&logoColor=white)
![Rails](https://img.shields.io/badge/rails-%23CC0000.svg?style=for-the-badge&logo=ruby-on-rails&logoColor=white)
![Postgres](https://img.shields.io/badge/postgres-%23316192.svg?style=for-the-badge&logo=postgresql&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-%23FF9900.svg?style=for-the-badge&logo=amazon-aws&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/github%20actions-%232671E5.svg?style=for-the-badge&logo=githubactions&logoColor=white)
![Heroku](https://img.shields.io/badge/heroku-%23430098.svg?style=for-the-badge&logo=heroku&logoColor=white)
![Vercel](https://img.shields.io/badge/Vercel-000000.svg?style=for-the-badge&logo=Vercel&logoColor=white)
![Postman](https://img.shields.io/badge/Postman-FF6C37.svg?style=for-the-badge&logo=Postman&logoColor=white)

### Database Schema

```
 create_table "projects", force: :cascade do |t|
    t.string "title"
    t.string "description"
    t.string "color"
    t.integer "status", default: 0
    t.date "deadline"
    t.bigint "user_id", null: false
    t.datetime "created_at", null: false
    t.datetime "updated_at", null: false
    t.index ["user_id"], name: "index_projects_on_user_id"
  end

  create_table "tasks", force: :cascade do |t|
    t.string "title"
    t.string "description"
    t.integer "priority"
    t.integer "status", default: 0
    t.bigint "project_id", null: false
    t.datetime "created_at", null: false
    t.datetime "updated_at", null: false
    t.index ["project_id"], name: "index_tasks_on_project_id"
  end

  create_table "users", force: :cascade do |t|
    t.string "username"
    t.string "email"
    t.datetime "created_at", null: false
    t.datetime "updated_at", null: false
  end

  add_foreign_key "projects", "users"
  add_foreign_key "tasks", "projects"
```

## Endpoints

<details close>

### Display a User's Dashboard

```
GET /api/v1/users/:id/dashboard
```
<details close>
Example Value:

```
{
    "data": {
        "id": "1",
        "type": "dashboard",
        "attributes": {
            "username": "Test User 1",
            "email": "user1@test.com",
            "projects": [
                {
                    "id": 1,
                    "title": "Project 1",
                    "description": "This is the first project",
                    "color": "123xyz",
                    "status": "assigned",
                    "deadline": "2023-12-12",
                    "tasks": [
                        {
                            "id": 1,
                            "title": "Task 1",
                            "description": "This is the first task",
                            "priority": "low",
                            "status": "backlog",
                            "project_id": 1
                        },
                        {
                            "id": 2,
                            "title": "Task 2",
                            "description": "This is the second task",
                            "priority": "medium",
                            "status": "doing",
                            "project_id": 1
                        }
                    ]
                },
                {
                    "id": 2,
                    "title": "Project 2",
                    "description": "This is the second project",
                    "color": "456abc",
                    "status": "assigned",
                    "deadline": "2023-11-24",
                    "tasks": [
                        {
                            "id": 3,
                            "title": "Task 3",
                            "description": "This is the third task",
                            "priority": "high",
                            "status": "backlog",
                            "project_id": 2
                        },
                        {
                            "id": 4,
                            "title": "Task 4",
                            "description": "This is the fourth task",
                            "priority": "critical",
                            "status": "done",
                            "project_id": 2
                        }
                    ]
                }
            ]
        }
    }
}
```

</details>

---

### Create a New Project

```
POST /api/v1/users/:id/projects
```
<details close>
Example Value:

```
{
    "data": {
        "id": "7",
        "type": "project",
        "attributes": {
            "user_id": 1,
            "title": "project 1",
            "description": "A New Project",
            "color": "123xyz",
            "status": "assigned",
            "deadline": "2023-12-11"
        },
        "relationships": {
            "tasks": {
                "data": []
            }
        }
    }
}
```

</details>

---

### Create a New Task

```
POST /api/v1/users/:id/projects/:project_id/tasks
```
<details close>
Example Value:

```
{
    "data": {
        "id": "13",
        "type": "task",
        "attributes": {
            "project_id": 6,
            "title": "Task 1",
            "description": "A New Task",
            "priority": "medium",
            "status": "backlog"
        }
    }
}
```

</details>

---
### Update a Task

```
PATCH /api/v1/users/:id/projects/:project_id/tasks/:task_id
```
<details close>
Example Value:

```
{
    "data": {
        "id": "13",
        "type": "task",
        "attributes": {
            "project_id": 6,
            "title": "Task 1",
            "description": "A New Task",
            "priority": "medium",
            "status": "doing"
        }
    }
}
```

</details>

---

</details>

## Contributors

- [William Chen](https://www.linkedin.com/in/williamfchen/) - GitHub: [@williamfchen](https://github.com/williamfchen)
- [Robert deLaguna](https://www.linkedin.com/in/robert-delaguna/) - GitHub: [@rjdelaguna](https://github.com/rjdelaguna)
- [Johann Dee](https://www.linkedin.com/in/johanndee/) - GitHub: [@joh-ann](https://github.com/joh-ann)
- [Logan Matheny](https://www.linkedin.com/in/loganpmatheny/) - GitHub: [@loganpaulmatheny](https://github.com/loganpaulmatheny)
- [Nicholas McEnroe](https://www.linkedin.com/in/nicholasmcenroe/) - GitHub: [@NSMcEnroe](https://github.com/NSMcEnroe)
- [Will Weston](https://www.linkedin.com/in/weston-william/) - GitHub: [@WillWeston94](https://github.com/WillWeston94)
