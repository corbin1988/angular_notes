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

## Event Binding

Event binding lets you listen for and respond to user actions such as keystrokes, mouse movements, clicks, and touches.

### Click Event: Display Book Details

Let's say you want to display book details when a user clicks on a book title. You can use the (click) event binding to achieve this. In your "books" component template (`books.component.html`), you can do something like this:

```html
<div>
  <h2>Book List</h2>
  <ul>
    <li *ngFor="let book of books">
      <a [href]="'/book-details/' + book.title" (click)="showBookDetails(book)">{{ book.title }} by {{ book.author }}</a>
    </li>
  </ul>
</div>
```

In the above example, we're binding the (click) event to a showBookDetails(book) method in your component. When a user clicks on a book title, the showBookDetails method can display book details or navigate to a book details page.

### Mouseover Event: Tooltip Display

Suppose you want to display a tooltip when a user hovers the mouse over a book title. You can use the (mouseover) event binding for this purpose. Here's an example:

```HTML
<div>
  <h2>Book List</h2>
  <ul>
    <li *ngFor="let book of books">
      <a [href]="'/book-details/' + book.title" (mouseover)="displayTooltip(book.title)">{{ book.title }} by {{ book.author }}</a>
    </li>
  </ul>
</div>
```

In this example, we're binding the (mouseover) event to a displayTooltip(book.title) method. When a user hovers over a book title, the displayTooltip method can show a tooltip with the book's title.

### Keypress Event: Search Books

If you want to allow users to search for books by typing in a search box, you can use the (keypress) event binding to capture keypress events. Here's an example:

```HTML
<div>
  <h2>Search for Books</h2>
  <input type="text" (keypress)="searchBooks($event)" placeholder="Type to search...">
</div>
```

In this example, we're binding the (keypress) event to a searchBooks($event) method. The searchBooks method can handle user input and filter the list of books based on the search query.

## Two Way Binding

Two-way binding gives components in your application a way to share data. Use two-
way binding to listen for events and update values simultaneously between parent and
child components.

Suppose you want to allow users to edit a book's title in a child component, and when the user changes the title, it should also update the parent component. You can use two-way binding with [(ngModel)] for this purpose. Here's how it works:

### Setting up Two-way Binding in Child Component:

In your child component's template (book-edit.component.html for this example), you can have an input field that binds to the book's title using [(ngModel)]:

```html
<input type="text" [(ngModel)]="book.title">
```

In your child component's TypeScript file (`book-edit.component.ts`), you define an `@Input` property to receive the book object from the parent component and `@Output` to emit the updated book when the user edits the title:

```rsjs
import { Component, Input, Output, EventEmitter } from '@angular/core';

@Component({
  selector: 'app-book-edit',
  templateUrl: './book-edit.component.html',
})
export class BookEditComponent {
  @Input() book: any;
  @Output() bookChange = new EventEmitter<any>();
}
```

### Using the Child Component in the Parent Component:

In your parent component's template (`books.component.html`), you can use the child component and pass the book object to it:

```rxjs
<div>
  <h2>Edit Book Title</h2>
  <app-book-edit [(book)]="selectedBook"></app-book-edit>
</div>
```

n this example, selectedBook is a property in your parent component that holds the book object you want to edit.

### Handling Changes in the Parent Component:

When the user edits the title in the child component, it automatically updates the `selectedBook` property in the parent component because of the two-way binding. You can listen to changes in the parent component using the `(bookChange)` event emitted by the child component:

```rxjs
import { Component } from '@angular/core';

@Component({
  selector: 'app-books',
  templateUrl: './books.component.html',
})
export class BooksComponent {
  selectedBook: any = { title: 'Book 1', author: 'Author 1' };

  onBookChange(book: any) {
    console.log('Book changed:', book);
  }
}
```
In the parent component's template, you can bind the `(bookChange)` event to the `onBookChange` method:

```rxjs
<app-book-edit [(book)]="selectedBook" (bookChange)="onBookChange($event)"></app-book-edit>
```

With this setup, when the user edits the book title in the child component, the updated title will be automatically reflected in the parent component's `selectedBook` property. The `(bookChange)` event allows you to handle the changes in the parent component.

Two-way binding simplifies the synchronization of data between parent and child components, making it a convenient feature for building interactive forms and real-time data sharing. It enhances the user experience by keeping data in sync without the need for extensive manual code.

## Directives

Directives are classes that add additional behavior to elements in your Angular applications. Directives are an essential part of Angular that allow you to manipulate the DOM, control rendering, and add behavior to your templates. Here are a few examples of common directives in the context of the "books" component:

### ngFor Directive: Displaying a List of Books

The `*ngFor` directive is used to iterate through an array and render a list of elements. In your "books" component template (`books.component.html`), you can use it to display a list of books from an array:

```html
<div>
  <h2>Book List</h2>
  <ul>
    <li *ngFor="let book of books">{{ book.title }} by {{ book.author }}</li>
  </ul>
</div>
```

In this example, the `*ngFor` directive iterates through the books array and displays each book's title and author.

### `ngIf` Directive: Conditionally Displaying Elements

The `*ngIf` directive allows you to conditionally render elements based on a condition. For instance, you can use it to display a message only if there are no books to show:

```html
<div>
  <h2>Book List</h2>
  <ul *ngIf="books.length > 0">
    <li *ngFor="let book of books">{{ book.title }} by {{ book.author }}</li>
  </ul>
  <p *ngIf="books.length === 0">No books to display.</p>
</div>
```

In this example, the `*ngIf` directive checks if the books array is empty and renders either the list of books or a message accordingly.

### ngModel Directive: Two-Way Data Binding

The ngModel directive is used for two-way data binding, especially with form elements. In the context of editing a book's title, you can use ngModel to bind an input field to a book's title property:

```html
<div>
  <h2>Edit Book Title</h2>
  <input type="text [(ngModel)]="selectedBook.title">
</div>
```

In this example, changes made in the input field will update the `selectedBook.title` property in real-time due to two-way binding.

### ngClass Directive: Applying CSS Classes Conditionally

The ngClass directive allows you to conditionally apply CSS classes to elements. For example, you can highlight books based on their availability:

```html
<div>
  <h2>Book List</h2>
  <ul>
    <li *ngFor="let book of books" [ngClass]="{'available': book.available, 'unavailable': !book.available}">
      {{ book.title }} by {{ book.author }}
    </li>
  </ul>
</div>
```

In this example, the `ngClass` directive applies the "available" or "unavailable" CSS class based on the `book.available` property.

### ngStyle Directive: Applying Inline Styles Conditionally

The ngStyle directive is used to apply inline styles conditionally. You can style books differently based on their genre, for example:

```html
<div>
  <h2>Book List</h2>
  <ul>
    <li *ngFor="let book of books" [ngStyle]="{ 'color': book.genre === 'Fiction' ? 'blue' : 'green' }">
      {{ book.title }} by {{ book.author }}
    </li>
  </ul>
</div>
```

In this example, the `ngStyle` directive sets the text color to blue for fiction books and green for other genres.

## Pipes

Pipes are simple functions to use in template expressions to accept an input value and return a transformed value. 

Pipes are useful because you can use them throughout your application, while only declaring each pipe once.

For example, you would use a pipe to show a date as April 15, 1988 rather than the raw string format.

```
<div>
  <h2>Book List</h2>
  <ul>
    <li *ngFor="let book of books">
      {{ book.title }} by {{ book.author }} (Released: {{ book.releaseDate | date:'longDate' }})
    </li>
  </ul>
</div>
```

We're using the date pipe to format the `book.releaseDate` property.

The date:'longDate' part of the pipe specifies the desired date format. Angular's date pipe provides various date format options, and 'longDate' is one of them, which displays the date in a long, human-readable format.

### Parent To Child Data

In Angular, you can pass data from a parent component to a child component by using input properties. Let's take the example of the "books" component (parent) passing data to a "book" component (child) by passing a book object. Here's how you can do it:

### Parent Component ("books.component.ts"):

In your parent component, you can define a book object and pass it to the child component using an input property.

```TS
import { Component } from '@angular/core';

@Component({
  selector: 'app-books',
  templateUrl: './books.component.html',
})
export class BooksComponent {
  bookData: any = { title: 'Book 1', author: 'Author 1' };
}
```

### Parent Component Template ("books.component.html"):

In the parent component's template, you can use the child component and bind the bookData to an input property in the child component. Let's assume the child component selector is app-book.

```html
<div>
  <h2>Books</h2>
  <app-book [book]="bookData"></app-book>
</div>
```

### Child Component ("book.component.ts"):

In your child component, you need to define an input property to receive the book data passed from the parent component.

``` TS
import { Component, Input } from '@angular/core';
@Component({
  selector: 'app-book',
  templateUrl: './book.component.html',
})
export class BookComponent {
  @Input() book: any;
}
```

### Child Component Template ("book.component.html"):

In the child component's template, you can access and display the book data received from the parent component.

```
<div>
  <h3>Book Details</h3>
  <p>Title: {{ book.title }}</p>
  <p>Author: {{ book.author }}</p>
</div>
```

## Passing Data From Child To Parent

In Angular, passing data from a child component to a parent component can be accomplished through a child-to-parent event with a custom listener. This process is often used when you want a child component to notify its parent component about specific actions or events, and the parent component needs to respond to those events.

Here's an explanation of how this communication works:

### Child Component Sending Data to Parent Component with a Custom Listener:

**Child Component (Emitter):** In the child component, you first define an event or action that needs to be communicated to the parent component. You can create a custom event using Angular's `EventEmitter`.

```TS
import { Component, Output, EventEmitter } from '@angular/core';

@Component({
  selector: 'app-child',
  templateUrl: './child.component.html',
})
export class ChildComponent {
  @Output() customEvent = new EventEmitter<any>();

  sendDataToParent() {
    const data = 'Some data from the child component';
    this.customEvent.emit(data);
  }
}
```

In this example, the `ChildComponent` defines an `@Output` property named `customEvent` of type `EventEmitter`. The `sendDataToParent` method emits the event and sends data to the parent component.

### Child Component Triggering the Event: 

When a specific action occurs in the child component (e.g., a button click), you call the method that emits the custom event. This triggers the event and sends the data to the parent component.

```
<button (click)="sendDataToParent()">Send Data to Parent</button>
```

When the user clicks the button, the `sendDataToParent` method is called, and the custom event is emitted.

###Parent Component (Listener): 

In the parent component, you need to listen for the custom event emitted by the child component. You can do this by binding to the event in the parent component's template and calling a method to handle the data.

```TS
import { Component } from '@angular/core';

@Component({
  selector: 'app-parent',
  templateUrl: './parent.component.html',
})
export class ParentComponent {
  receivedData: string;

  handleCustomEvent(data: string) {
    this.receivedData = data;
  }
}
```


In the parent component, you define a property (receivedData) to store the data received from the child component and a method (handleCustomEvent) to handle the data.

### Binding to the Child Component's Event: 

In the parent component's template, you bind to the child component's custom event and call the handleCustomEvent method to process the received data.

```
<app-child (customEvent)="handleCustomEvent($event)"></app-child>
<p>Data received from child component: {{ receivedData }}</p>
```

In this example, when the child component emits the customEvent, it triggers the handleCustomEvent method in the parent component. The data sent from the child component is captured and displayed in the parent component's template.
