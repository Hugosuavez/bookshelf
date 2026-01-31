# bookshelf


Bookshelf is a full stack application created as part of an MSc Computer Science course, I am unable to share code directly due to university policy. I have included here a description of the application and the tools and techniques used to create it, along with a PDF containing screenshots displaying the core functionality in action.

The application consists of a React client, a Java RESTful API and a MySQL database containing information about books. It allows users to view the data in an ordered table, browse books using pagination and query the database by title, author, genre and date. Users can view, view book details by ID, add, edit and delete books (all CRUD operations) in three different data formats: JSON, XML and Plain Text. For brevity, I have included screenshots for GET requests with payloads for all three data types demonstrating this multi data format functionality, but otherwise I am displaying requests in the default JSON format.

## Java RESTful API

In line with the assessment requirements, this Java API written in vanilla Java without build tools or frameworks such as Gradle, Spring or Hibernate. The aim here was to teach us the underlying functionality of Java programs before introducing tools which simplify the process. JAR files were manually added to lib folder to provide extra functionality, such as data formatting and connection pooling. As spring is not used, dependency injection and data validation are handled manually. This API is an exercise in some of the basics principles in object oriented programming and I employed some design patterns, such as singleton and factory. 

The basic structure of the application follows the single responsibility principle, delegating specific tasks to separate classes. 

- Controller - handles requests/responses. 
- Service layer - handles delegation of tasks such as object creation, data formatting and validation.
- Factory - handles object creation
- Data Formatter - maps the format of incoming request to Java objects
- Response Formatter - formats the response data to the requested type.
- Data access object - prepares statements for SQL injection prevention and makes database requests.
- Database manager - retrieves database credentials and establishes connection pool.
- Global Exception Handling Filter - handles unchecked runtime errors in three categories: Bad Request, Resource Not Found or Server Errors

### Dependencies

### Server & Connection Pool

- Tomcat 9
- HikariCP

### Data formatting

- Gson - JSON 
- JAXB - XML
- Custom method - Plain Text

## React Client

Simple react front end using React's component based architecture to separate concerns. Global context used to manage state and handle currently selected data format. Api calls and data formatting methods separated into their own files and grouped in a utils folder. Bootstrap used to provide simple default CSS and accelerate design speed. The Don't Repeat Yourself principle (DRY) applied, for example in reusing a book form for both add and update requests.

### Dependencies

- Vite - Build and development.

- React Router - Navigation.
- Axios - API requests.
- Bootstrap/Bootstrap Icons - UI.
- Fast xml parser - parsing XML.
- React Toastify - User feedback.
- React Paginate - Pagination feature.


