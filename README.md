# Book_Search_Engine

## MERN: Book Search Engine

## Description

Your assignment this week is emblematic of the fact that most modern websites are driven by two things: data and user demands. This shouldn't come as a surprise, as the ability to personalize user data is the cornerstone of real-world web development today. And as user demands evolve, applications need to be more performant.

This week, you’ll take starter code with a fully functioning Google Books API search engine built with a RESTful API, and refactor it to be a GraphQL API built with Apollo Server. The app was built using the MERN stack with a React front end, MongoDB database, and Node.js/Express.js server and API. It's already set up to allow users to save book searches to the back end.

To complete the assignment, you’ll need to do the following:

1. Set up an Apollo Server to use GraphQL queries and mutations to fetch and modify data, replacing the existing RESTful API.

2. Modify the existing authentication middleware so that it works in the context of a GraphQL API.

3. Create an Apollo Provider so that requests can communicate with an Apollo Server.

4. Deploy your application to Render with a MongoDB database using MongoDB Atlas. Use the [Deploy with Render and MongoDB Atlas](https://coding-boot-camp.github.io/full-stack/mongodb/deploy-with-render-and-mongodb-atlas) walkthrough for instructions.

In order for this application to use a GraphQL API, you’ll need to refactor the API to use GraphQL on the back end and add some functionality to the front end. The following sections contain details about the files you’ll need to modify on the back end and the front end.

**Important**: Make sure to study the application before building upon it. Better yet, start by making a copy of it. It's already a working application&mdash;you're converting it from RESTful API practices to a GraphQL API.

## Back-End Specifications

You’ll need to complete the following tasks in each of these back-end files:

* `auth.js`: Update the auth middleware function to work with the GraphQL API.

* `server.js`: Implement the Apollo Server and apply it to the Express server as middleware.

* `Schemas` directory:

  * `index.js`: Export your typeDefs and resolvers.

  * `resolvers.js`: Define the query and mutation functionality to work with the Mongoose models.

  **Hint**: Use the functionality in the `user-controller.js` as a guide.

  * `typeDefs.js`: Define the necessary `Query` and `Mutation` types:

    * `Query` type:

      * `me`: Which returns a `User` type.
  
    * `Mutation` type:

      * `login`: Accepts an email and password as parameters; returns an `Auth` type.

      * `addUser`: Accepts a username, email, and password as parameters; returns an `Auth` type.

      * `saveBook`: Accepts a book author's array, description, title, bookId, image, and link as parameters; returns a `User` type. (Look into creating what's known as an `input` type to handle all of these parameters!)

      * `removeBook`: Accepts a book's `bookId` as a parameter; returns a `User` type.

    * `User` type:

      * `_id`

      * `username`

      * `email`

      * `bookCount`

      * `savedBooks` (This will be an array of the `Book` type.)

    * `Book` type:

      * `bookId` (Not the `_id`, but the book's `id` value returned from Google's Book API.)

      * `authors` (An array of strings, as there may be more than one author.)

      * `description`

      * `title`

      * `image`

      * `link`

    * `Auth` type:

      * `token`

      * `user` (References the `User` type.)

## Front-End Specifications

You'll need to create the following front-end files:

* `queries.js`: This will hold the query `GET_ME`, which will execute the `me` query set up using Apollo Server.

* `mutations.js`:

  * `LOGIN_USER` will execute the `loginUser` mutation set up using Apollo Server.

  * `ADD_USER` will execute the `addUser` mutation.

  * `SAVE_BOOK` will execute the `saveBook` mutation.

  * `REMOVE_BOOK` will execute the `removeBook` mutation.

Additionally, you’ll need to complete the following tasks in each of these front-end files:

* `App.jsx`: Create an Apollo Provider to make every request work with the Apollo Server.
 
* `SearchBooks.jsx`:

  * Use the Apollo `useMutation()` Hook to execute the `SAVE_BOOK` mutation in the `handleSaveBook()` function instead of the `saveBook()` function imported from the `API` file.

  * Make sure you keep the logic for saving the book's ID to state in the `try...catch` block!

* `SavedBooks.jsx`:

  * Remove the `useEffect()` Hook that sets the state for `UserData`.

  * Instead, use the `useQuery()` Hook to execute the `GET_ME` query on load and save it to a variable named `userData`.

  * Use the `useMutation()` Hook to execute the `REMOVE_BOOK` mutation in the `handleDeleteBook()` function instead of the `deleteBook()` function that's imported from `API` file. (Make sure you keep the `removeBookId()` function in place!)

* `SignupForm.jsx`: Replace the `addUser()` functionality imported from the `API` file with the `ADD_USER` mutation functionality.

* `LoginForm.jsx`: Replace the `loginUser()` functionality imported from the `API` file with the `LOGIN_USER` mutation functionality.



## Technical Acceptance Criteria

* Satisfies all of the preceding acceptance criteria plus the following:

  * Has an Apollo Server that uses GraphQL queries and mutations to fetch and modify data, replacing the existing RESTful API.

  * Use an Apollo Server and apply it to the Express.js server as middleware.

  * Include schema settings for resolvers and typeDefs as outlined in the Challenge instructions.

  * Modify the existing authentication middleware to work in the context of a GraphQL API.

  * Use an Apollo Provider so that the application can communicate with the Apollo Server.

  * Application must be deployed to Render.

## Deployment

* Application deployed at live URL.

* Application loads with no errors.

* Application GitHub URL submitted.

* GitHub repository contains application code.

## Application Quality

* User experience is intuitive and easy to navigate.

* User interface style is clean and polished.

* Application resembles the mock-up functionality provided in the Challenge instructions.

## Repository Quality

* Repository has a unique name.

* Repository follows best practices for file structure and naming conventions.

* Repository follows best practices for class/id naming conventions, indentation, quality comments, etc.

* Repository contains multiple descriptive commit messages.

* Repository contains high-quality README file with description, screenshot, and link to the deployed application.

## Screenshot

![Screenshot 2024-05-23 204327](https://github.com/hemuprabu/Book_Search_Engine/assets/108079829/0603365b-cc47-45c9-94b2-eb6363c6f01b)
![Screenshot 2024-05-23 204341](https://github.com/hemuprabu/Book_Search_Engine/assets/108079829/d0c61de6-62fd-4cb1-885b-621fb059123b)
![Screenshot 2024-05-23 204354](https://github.com/hemuprabu/Book_Search_Engine/assets/108079829/63d33c84-2364-4f65-b299-fc3f84c3b70d)
![Screenshot 2024-05-23 204417](https://github.com/hemuprabu/Book_Search_Engine/assets/108079829/51aed13e-15a0-428f-b61d-ef7997fc1d66)



## Installation

Include instructions on how to install any dependencies required for your project. You can mention running npm install to install necessary packages.

To run the Book_Search_Engine application, follow these steps to install the required dependencies:

1. Clone the repository to your local machine:
   ```bash
   git clone https://github.com/hemuprabu/Book_Search_Engine

2. cd Book_Search_Engine

3. Run npm install to install dependencies.

## License

The Book Search Engine project is distributed under the [MIT License](https://opensource.org/licenses/MIT). This license allows you to use, modify, and distribute the project for both personal and commercial purposes, with attribution to the original author.

For more details on the MIT License terms, please refer to the [LICENSE](./LICENSE) file included in the project repository.

## Author

This Book Search Engine project was created by:

- **Your Name**: Hemalatha Prakasam
- **GitHub**: [GitHub Profile](https://github.com/hemuprabu)

Feel free to connect with me for any inquiries or feedback related to Book Search Engine application. I hope you enjoy using the application.

## Contact

If you have any feedback, questions, or suggestions regarding the Book Search Engine application, feel free to reach out to me:

- **Email**: Hemalathaprakasam219@gmail.com

I welcome any feedback or inquiries and am happy to assist with any queries related to the Book Search Engine project. Your input is valuable in improving the application and making it more user-friendly.


