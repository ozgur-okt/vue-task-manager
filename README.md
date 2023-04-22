# Vue Task Manager

This is a simple task management web application built with Vue.js. It allows users to add, delete, and edit tasks, and has an "about" page that can be accessed via Vue Router. The backend is implemented using the json-server module on npm, which provides a simple RESTful API to store and retrieve tasks.

This app is inspired by Brad Traversy's creating vue app video on youtube. 

![Screenshot 2023-04-22 at 20 58 51](https://user-images.githubusercontent.com/73358116/233800350-5f35180a-1a58-4691-94a3-59b2968efad8.png)

## Getting started
To run this project on your local machine, you'll need to have Node.js and npm installed. Once you have these dependencies, follow these steps:

Clone the repository and navigate to the project directory:
```
git clone https://github.com/ozgur-okt/vue-task-manager.git
cd vue-task-manager
```

Install the project dependencies:

```
npm install
```

## Run the JSON-Server backend (http://localhost:5000)

```
npm run backend
```

## In a separate terminal, start the Vue development server: (http://localhost:8080)

```
npm run serve
```
Open your browser and navigate to http://localhost:8080/ to access the application.

## Compiles and minifies for production

```
npm run build
```


# Usage

## Adding tasks

To add a new task, simply click the "Add task" button at the top of the page. This will open a modal dialog where you can enter the task details. Once you've entered the task title and description, click "Save" to add the task to the list. If you click on "set reminder", the task gets a green vertical line on left side.

![Screenshot 2023-04-22 at 20 59 07](https://user-images.githubusercontent.com/73358116/233800425-19573701-7900-4255-9c0b-701a9d8752d9.png)

## Editing tasks

To edit an existing task, click the edit icon next to the task title. This will open the same modal dialog as when adding a task, but with the current task details pre-populated. Make any changes you like, then click "Save" to update the task.

![Screenshot 2023-04-22 at 20 59 27](https://user-images.githubusercontent.com/73358116/233800432-f7c24ef0-9481-4adc-87d9-8edb229efeac.png)

## Deleting tasks

To delete a task, click the delete icon next to the task title. This will immediately remove the task from the list.

## About page

To access the about page, click the "About" link in the top navigation bar. This will take you to a page with some basic information about the application.

# Acknowledgements

This project was built using the following technologies:

Vue.js (https://vuejs.org/)

Vue Router (https://router.vuejs.org/)

json-server (https://github.com/typicode/json-server)

# License
This project is licensed under the MIT License. See the LICENSE file for details.


