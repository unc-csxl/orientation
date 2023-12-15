# CSXL Orientation 👋

**Welcome**, CSXL Developers and students of *COMP 423: Foundations of Software Engineering* 🤠! This repository serves as a collection of resources, documentation, and supplemental materials to help you become acclimated to working with the technology, languages, and tools that power the CSXL Web Application. The CSXL Application is a *full-stack web application* with both a frontend and backend.

## Frontend

This section contains resources relating to the frontend of the CSXL Web Application.

### TypeScript

[**TypeScript for the COMP 301 Developer**]() (COMING SOON)

This reading introduces the TypeScript programming language for those who just concluded a Java programming course (such as COMP 210 or COMP 301). Learn more about how TypeScript compares to Java in purpose, syntax, and language features.

### Angular

[**Crash Course on Angular Widgets**](https://github.com/unc-csxl/orientation/blob/main/angular/widgets.md)

This reading introduces Angular Widgets - an extremely useful convention used in the CSXL application that allows the abstraction and reuse of Angular UI components. Widgets allow for cleaner HTML and CSS in your Components, better organization, and the easy reuse of components that appear frequently throughout the site.

[**Angular Resolvers**](https://github.com/unc-csxl/orientation/blob/main/angular/resolvers.md)

This reading introduces Angular Resolvers, a feature of Angular that enables the pre-loading of data into Angular Components! This is extremely useful to make code more concise and prevents implementing numerous unnecessary subscriptions to observables.

## Backend

This section contains resources relating to the backend of the CSXL Web Application.

### FastAPI and Error Handling

[**Error Handling Using the Middleware**](https://github.com/unc-csxl/orientation/blob/main/backend/middleware.md)

Middleware exception handling is a nifty feature in the backend that allows you to simplify the Python code of your backend services and APIs. Rather than having to throw Exceptions in the service, then catching them and re-throwing them as HTTPExceptions in your APIs, you can throw custom exceptions in your service only - then, the middleware handles the rest! The documentation above discusses how to set this up for the services and APIs in your project.

### SQLAlchemy

[**The SQLAlchemy Tutorial**](https://github.com/unc-csxl/orientation/blob/main/sqlalchemy/0_introduction.md)

SQLAlchemy is the primary SQL toolkit that we will use to interact with the PostgreSQL database that stores the data for our application. This reading contains numerous chapters that introduce you to SQLAlchemy, helps you become familiar with what it does and how it functions, and how to use SQLAlchemy to model and modify data in the PostgreSQL database.

## The Stack

### Stack Diagram

The entire CSXL tech stack, as well as the flow of data from the frontend to the backend and back across HTTP, can be summarized in the diagram below. The diagram is also linked [here](https://go.unc.edu/comp423-23f-stack) for easy access.

![The Tech Stack](https://github.com/unc-csxl/csxl.unc.edu/blob/main/docs/images/sqlalchemy/tech-stack-with-alchemy.png)
