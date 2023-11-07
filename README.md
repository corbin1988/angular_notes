# Angular Context Switching Notes

## Using Angular CLI

Angular has its own cli tool you need to install.

### Creating A Project

```
ng new project-name
```

### Starting A Project

Navigate to the project name

```
cd project-name
```

Then

```
ng serve
```

### Generate A Component

Components are automatically registered in `app.module.ts`

```
ng generate component books
```

## Project Structure Explained



```js
project-name/
│
├── e2e/
│   ├── src/                 # End-to-End testing configuration and test files
│   └── ...
│
├── node_modules/             # Node.js modules (dependencies)
│
├── src/                      # Application source code
│   ├── app/                 # Application-specific code
│   │   ├── components/      # Angular components
│   │   │   ├── books/       # Example component
│   │   │   │   ├── books.component.html
│   │   │   │   ├── books.component.ts
│   │   │   │   ├── books.component.scss
│   │   │   │   └── ...
│   │   │   ├── book/        # Another example component
│   │   │   │   ├── book.component.html
│   │   │   │   ├── book.component.ts
│   │   │   │   ├── book.component.scss
│   │   │   │   └── ...
│   │   │   └── ...          # Other components
│   │   ├── services/        # Angular services
│   │   ├── models/          # Data models/interfaces
│   │   ├── app-routing.module.ts  # Angular Router configuration
│   │   ├── app.module.ts    # Main application module
│   │   └── ...
│   ├── assets/              # Static assets like images, fonts, etc.
│   ├── environments/         # Environment-specific configuration
│   ├── index.html           # Main HTML file
│   ├── main.ts               # Entry point for the application
│   ├── styles.scss           # Global styles
│   └── ...
│
├── .angular.json             # Angular CLI configuration
├── package.json              # Project dependencies and scripts
├── tsconfig.json             # TypeScript configuration
├── tslint.json               # TSLint configuration (optional, as it's deprecated)
├── README.md                # Project documentation
└── ...
```

Here's a brief explanation of key directories and files in an Angular project:

- **e2e**: End-to-End testing directory. Contains test configuration and spec files for testing your application.
- **node_modules**: Node.js modules required for your project (dependencies). These are installed via npm.
- **src**: The main source code directory where your application code resides.
- **app**: This is where you'll put most of your application-specific code.
  - **components**: Angular components, which define the UI and functionality.
  - **services**: Angular services for managing data, state, and business logic.
  - **models**: Data models or interfaces.
  - **app-routing.module.ts**: Configuration for the Angular Router, defining the app's navigation routes.
  - **app.module.ts**: The main application module where you declare and bootstrap your app.
- **assets**: Contains static assets like images, fonts, and other non-code files.
- **environments**: Configuration files for different environments (e.g., production, development).
- **index.html**: The main HTML file that serves as the entry point for your application.
- **main.ts**: The application's main TypeScript file, where the app is initialized.
- **styles.scss**: Global styles for your application.
- **.angular.json**: Configuration file used by Angular CLI for project settings and build configurations.
- **package.json**: Lists project dependencies and scripts for running various tasks.
- **tsconfig.json**: TypeScript configuration for your project.
- **tslint.json**: TSLint configuration (optional, as TSLint is deprecated; consider using ESLint with TypeScript).
- **README.md**: Project documentation and instructions for other developers.

## How the App Module Works:

The root module is often named AppModule and serves as the entry point of your Angular application.

```TS
// Import required Angular modules and libraries
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';

// Import the root component
import { AppComponent } from './app.component';

@NgModule({
  declarations: [
    // Declare components, directives, and pipes belonging to this module
    AppComponent,
    BooksComponent
  ],
  imports: [
    // Import other modules that this module depends on
    BrowserModule
  ],
  providers: [
    // Provide services at the module level
  ],
  bootstrap: [
    // Define the root component of the application
    AppComponent
  ]
})
export class AppModule { }
```

### Imports:

We start by importing the necessary modules and libraries. In this example, we import the `BrowserModule` from `@angular/platform-browser` and the `NgModule` decorator from `@angular/core`. You'll also import any other Angular modules, components, services, or libraries that your application needs.

### NgModule Decorator:

The `@NgModule` decorator is used to define and configure the Angular module. This decorator takes an object with several configuration options.

### declarations:

The `declarations` array is used to list the components, directives, and pipes that belong to this module. In our example, we declare the `AppComponent`. If you have other components, you would include them here.

### imports:

The `imports` array lists other modules that this module depends on. In this case, we import the `BrowserModule`, which is a fundamental module required for running Angular applications in a browser.

### providers:

The `providers` array is used to specify services that should be available at the module level. You can provide services here that you want to be accessible throughout the module. For example, you would add services that provide data or functionality used by components.

### bootstrap:

The `bootstrap` array defines the root component of the application. The root component is the initial component that gets loaded when the application starts. In this example, we set `AppComponent` as the root component.

### Exporting the Module:

Finally, we export the `AppModule` class so that it can be used in other parts of your application.

## How To Make A Component

### Step 1: Import the Component

In your Angular application, open the TypeScript file where you want to use the "books" component. Typically, you would use it in another component or within your application's root module. Import the "books" component at the top of the file. For example, if you have a component called `app.component.ts`, you can import it like this:

```
import { Component } from '@angular/core';
import { BooksComponent } from './path-to-books-component/books.component'; // Update the path as needed
```

### Step 2: Use the Component in the Template

In the same file (`app.component.ts` in this example), you can use the "books" component in your template by including its selector. If you've defined a selector for the "books" component in its metadata, you can use it like this:

```TS
@Component({
  selector: 'app-root',
  template: `
    <h1>Welcome to My Bookstore</h1>
    <app-books></app-books> <!-- Use the selector here -->
  `
})
export class AppComponent {
  // Component logic here
}
```

In this example, we're using the "app-books" selector within the template of the AppComponent. The "app-books" selector represents the "books" component, and it will render the "books" component's template and functionality in the AppComponent's template.

### Step 3: Update the Module Declarations

If you haven't already added the "books" component to the declarations array of your module (e.g., the root module), you need to do so. In your module file (e.g., `app.module.ts`), ensure that the "books" component is declared like this:

```TS
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';
import { BooksComponent } from './path-to-books-component/books.component'; // Update the path as needed

@NgModule({
  declarations: [
    BooksComponent, // Include the BooksComponent in the declarations array
    // ... other components, directives, and pipes
  ],
  imports: [BrowserModule],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```

### Step 4: Render the Component

Now, when you run your Angular application, the "books" component will be rendered as part of the AppComponent. You will see the content and functionality of the "books" component within the application.

## Template Interpolation

First, assume you have a "books" component with a list of books defined in its TypeScript file (`books.component.ts`). Here's an example of what the component could look like:

```TS
import { Component } from '@angular/core';

@Component({
  selector: 'app-books',
  templateUrl: './books.component.html',
})
export class BooksComponent {
  books: Books[] = [
    { title: 'Book 1', author: 'Author 1' },
    { title: 'Book 2', author: 'Author 2' },
    { title: 'Book 3', author: 'Author 3' },
    { title: 'Book 4', author: 'Author 4' },
    { title: 'Book 5', author: 'Author 5' },
  ];
}
```

Now, let's create the template for the "books" component in the HTML file (`books.component.html`) and use template interpolation to display the list of books:

```
<!-- books.component.html -->

<div>
  <h2>Book List</h2>
  <ul>
    <li *ngFor="let book of books">{{ book }}</li>
  </ul>
</div>
```
## Property Binding

Property binding in Angular allows you to set or update an HTML element's property (or attribute) based on a value from your component. In the context of the "books" component with book objects, I'll explain how property binding works.

Let's say you want to bind an HTML element's property, such as the `title` attribute of an anchor (`<a>`) element, to a book's title. Here's how you can achieve property binding:

First, in your "books" component template (`books.component.html`), let's assume you have an anchor element that you want to set the `title` attribute for a book link. You can use property binding to set the `title` attribute to the book's title. Here's an example:

```
<!-- books.component.html -->

<div>
  <h2>Book List</h2>
  <ul>
    <li *ngFor="let book of books">
      <a [href]="'/book-details/' + book.title">{{ book.title }} by {{ book.author }}</a>
    </li>
  </ul>
</div>
```
We use `[href]` for property binding to set the `href` attribute of the anchor element.

`'/'` is a string representing the base URL for your application. You may need to adjust this to match your application's routing configuration.

`'/book-details/' + book.title` is an expression that dynamically constructs the URL for the book details page. We append the book's title to the base URL to create a unique URL for each book.

