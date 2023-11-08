# Angular Context Switching Notes

## Table of Contents

# Table of Contents

# Table of Contents

* [Using Angular CLI](#using-angular-cli)
   * [Creating A Project](#creating-a-project)
   * [Starting A Project](#starting-a-project)
   * [Generate A Component](#generate-a-component)

* [Project Structure Explained](#project-structure-explained)
* [How the App Module Works](#how-the-app-module-works)
   * [Imports](#imports)
   * [NgModule Decorator](#ngmodule-decorator)
   * [declarations](#declarations)
   * [imports](#imports)
   * [providers](#providers)
   * [bootstrap](#bootstrap)
   * [Exporting the Module](#exporting-the-module)

* [How To Make A Component](#how-to-make-a-component)
   * [Step 1: Import the Component](#step-1-import-the-component)
   * [Step 2: Use the Component in the Template](#step-2-use-the-component-in-the-template)
   * [Step 3: Update the Module Declarations](#step-3-update-the-module-declarations)
   * [Step 4: Render the Component](#step-4-render-the-component)

* [Template Interpolation](#template-interpolation)
* [Property Binding](#property-binding)
* [Event Binding](#event-binding)
   * [Click Event: Display Book Details](#click-event-display-book-details)
   * [Mouseover Event: Tooltip Display](#mouseover-event-tooltip-display)
   * [Keypress Event: Search Books](#keypress-event-search-books)

* [Two Way Binding](#two-way-binding)
   * [Setting up Two-way Binding in Child Component](#setting-up-two-way-binding-in-child-component)
   * [Using the Child Component in the Parent Component](#using-the-child-component-in-the-parent-component)
   * [Handling Changes in the Parent Component](#handling-changes-in-the-parent-component)

* [Directives](#directives)
   * [ngFor Directive: Displaying a List of Books](#ngfor-directive-displaying-a-list-of-books)
   * [`ngIf` Directive: Conditionally Displaying Elements](#ngif-directive-conditionally-displaying-elements)
   * [ngModel Directive: Two-Way Data Binding](#ngmodel-directive-two-way-data-binding)
   * [ngClass Directive: Applying CSS Classes Conditionally](#ngclass-directive-applying-css-classes-conditionally)
   * [ngStyle Directive: Applying Inline Styles Conditionally](#ngstyle-directive-applying-inline-styles-conditionally)

* [Pipes](#pipes)
* [Parent To Child Data](#parent-to-child-data)
   * [Parent Component ("books.component.ts")](#parent-component-bookscomponentts)
   * [Parent Component Template ("books.component.html")](#parent-component-template-bookscomponenthtml)
   * [Child Component ("book.component.ts")](#child-component-bookcomponentts)
   * [Child Component Template ("book.component.html")](#child-component-template-bookcomponenthtml)

* [Passing Data From Child To Parent](#passing-data-from-child-to-parent)
   * [Child Component Sending Data to Parent Component with a Custom Listener](#child-component-sending-data-to-parent-component-with-a-custom-listener)
   * [Child Component Triggering the Event](#child-component-triggering-the-event)
   * [Parent Component (Listener)](#parent-component-listener)
   * [Binding to the Child Component's Event](#binding-to-the-child-components-event)

* [Lifecycle Hooks](#lifecycle-hooks)
   * [ngOnChanges](#ngonchanges)
   * [ngOnInit](#ngoninit)
   * [ngDoCheck](#ngodocheck)
   * [ngAfterContentInit](#ngaftercontentinit)
   * [ngAfterContentChecked](#ngaftercontentchecked)
   * [ngAfterViewInit](#ngafterviewinit)
   * [ngAfterViewChecked](#ngafterviewchecked)
   * [ngOnDestroy](#ngondestroy)

* [Services](#services)
   * [Create the Service Class](#create-the-service-class)
   * [Define the Service Class (book.service.ts)](#define-the-service-class-bookservicets)
   * [Using the Book Service in a Component](#using-the-book-service-in-a-component)
   * [Inject the Service (`books.component.ts`)](#inject-the-service-bookscomponentts)

* [Dependency Injection](#dependency-injection)
   * [How Dependency Injection Works in Angular](#how-dependency-injection-works-in-angular)
      * [Service Registration](#service-registration)
      * [Requesting Dependencies](#requesting-dependencies)
      * [Dependency Resolution](#dependency-resolution)
   * [Example: Using Dependency Injection in Angular](#example-using-dependency-injection-in-angular)

* [Custom Modules](#custom-modules)
   * [Generate a Custom Module](#generate-a-custom-module)
   * [Use the Custom Module in Your Application](#use-the-custom-module-in-your-application)

* [State Management With Services](#state-management-with-services)
   * [Step 1: Create a Shopping Cart Service](#step-1-create-a-shopping-cart-service)
   * [Step 2: Use the Shopping Cart Service in Your Components](#step-2-use-the-shopping-cart-service-in-your-components)
   * [Step 3: Display Cart Items in the Template](#step-3-display-cart-items-in-the-template)

* [State Management Options in Angular](#state-management-options-in-angular)

* [Routing](#routing)
   * [Step 1. Generate Routes](#step-1-generate-routes)
   * [Step 2: Create Link](#step-2-create-link)
   * [Step 3: Display Single Page Component](#step-3-display-single-page-component)
   * [Step 4: Create Single Page Template](#step-4-create-single-page-template)
   * [Step 5: Update App Module](#step-5-update-app-module)

* [Route Guards](#route-guards)
   * [Step 1: Create an Auth Guard](#step-1-create-an-auth-guard)
   * [Step 2: Implement the Route Guard](#step-2-implement-the-route-guard)
   * [Step 3: Update the Route Configuration](#step-3-update-the-route-configuration)


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

### Lifecycle Hooks

A component instance has a lifecycle that starts when Angula instantiates the component class and renders the componenview along with its child views.

The lifecycle continues with change detection, as Angular che to see when data-bound properties change, and updates bot the view and the component instance as needed.

The lifecycle ends when Angular destroys the component instance and removes its rendered template from the DOM.

### ngOnChanges 

This hook is called when data-bound input properties change. It receives a SimpleChanges object that holds information about the changes.

```TS
ngOnChanges(changes: SimpleChanges) {
  if (changes.someInput) {
    console.log('Input property "someInput" changed.');
  }
}
```

### ngOnInit

This hook is called once, after the component is initialized. It's commonly used for tasks like initializing data.

```TS
ngOnInit() {
  console.log('Component initialized.');
}
```

### ngDoCheck 

This hook is called during every change detection cycle, allowing you to perform custom change detection logic.

```TS
ngDoCheck() {
  console.log('Change detection cycle triggered.');
}
```

### ngAfterContentInit 

This hook is called after the component's content is initialized. It's often used with content projection in Angular.

```TS
ngAfterContentInit() {
  console.log('Content initialization completed.');
}
```

### ngAfterContentChecked 

This hook is called after every check of the component's content. It can be used to perform additional logic after content projection changes.

```TS
ngAfterContentChecked() {
  console.log('Content checked.');
}
```
### ngAfterViewInit 

This hook is called after the component's view and child views are initialized.

```TS
ngAfterViewInit() {
  console.log('View and child views initialized.');
}
```
### ngAfterViewChecked

This hook is called after every check of the component's view and child views. It's used to perform additional logic after view changes.

```TS
ngAfterViewChecked() {
  console.log('View and child views checked.');
}
```
### ngOnDestroy

This hook is called just before the component is destroyed. It's useful for cleaning up resources, like unsubscribing from observables.

```TS
ngOnDestroy() {
  console.log('Component destroyed.');
}
```

The component's lifecycle starts with the instantiation of the component class, rendering of the component view, and child views. Change detection continuously checks for data-bound property changes, and updates both the view and the component instance as needed. The lifecycle ends when Angular destroys the component instance and removes its rendered template from the DOM. By implementing these hooks, you can customize the behavior of your components at different stages of their lifecycle.

## Services

In Angular, services are used to encapsulate and manage data and business logic, like API requests, that can be shared across components. Let's create an example of a BookService in the context of your "books" application.


### Create the Service Class:

You can generate a service using Angular CLI, which will create a service class for you. Alternatively, you can manually create a service file. Here, we'll manually create a BookService:

```
ng generate service book
```

This will create a `book.service.ts` file, which you can find in the `src/app` directory.

### Define the Service Class (book.service.ts):

In the `book.service.ts` file, define the `BookService` class and its methods. For example, you can create a method to get a list of books.

```TS
import { Injectable } from '@angular/core';

@Injectable({
  providedIn: 'root', // Registers the service as a singleton at the root level
})
export class BookService {
  //This would come from the API
  private books: any[] = [
    { title: 'Book 1', author: 'Author 1' },
    { title: 'Book 2', author: 'Author 2' },
    // Add more books as needed
  ];
  //This would be an API GET request
  getBooks() {
    return this.books;
  }
  
  //This would be an API POST request
  addBook(book: any) {
    this.books.push(book);
  }
}
```


Here, the `BookService` class provides a `getBooks` method to retrieve a list of books and an `addBook` method to add a new book to the list. The `@Injectable` decorator is used to indicate that this class can be injected into other components.

### Using the Book Service in a Component:

Now, let's see how you can use the `BookService` in a component, for example, in your "books" component.

### Inject the Service (`books.component.ts`):

In your component file (books.component.ts), inject the BookService by including it in the constructor.

```TS
import { Component } from '@angular/core';
import { BookService } from './book.service';

@Component({
  selector: 'app-books',
  templateUrl: './books.component.html',
})
export class BooksComponent {
  books: any[] = [];

  constructor(private bookService: BookService) {
    this.books = this.bookService.getBooks();
  }
}
```

In this example, the `BooksComponent` injects the BookService and calls the `getBooks` method to retrieve the list of books.

Using the Service in the Component Template (`books.component.html`):

In your component's template (`books.component.html`), you can display the list of books obtained from the service.

```html
<div>
  <h2>Books</h2>
  <ul>
    <li *ngFor="let book of books">{{ book.title }} by {{ book.author }}</li>
  </ul>
</div>
```

With this setup, the `BookService` provides a centralized way to manage and access data (in this case, a list of books) across components. The service can be reused in multiple components, promoting data consistency and maintainability in your Angular application.

## Dependency Injection

DI is wired into the Angular framework and used everywhere to provide new
components with the services or other
things they need.

Components consume services; that is, you can inject a service into a component, giving the component access to that service class.

### How Dependency Injection Works in Angular:

#### Service Registration 

In Angular, you define services by creating classes and decorating them with @Injectable metadata. These services are registered in the application's dependency injection framework.

#### Requesting Dependencies 

Components, services, or other classes can request dependencies (services) by specifying them in their constructor. Angular will provide the required dependencies when an instance of the class is created.

#### Dependency Resolution

When an instance of a component or service is created, Angular's dependency injection system resolves the required dependencies and injects them into the constructor parameters.

####Example: Using Dependency Injection in Angular:

Let's say you have a service called BookService that provides a list of books. You want to use this service in a component called BooksComponent to display the list of books.

1. Create the `BookService` Service:

```TS
// book.service.ts
import { Injectable } from '@angular/core';

@Injectable({
  providedIn: 'root',
})
export class BookService {
  private books: any[] = [
    { title: 'Book 1', author: 'Author 1' },
    { title: 'Book 2', author: 'Author 2' },
    // Add more books as needed
  ];

  getBooks() {
    return this.books;
  }
}
```

2. Use the Service in the `BooksComponent` Component:

```TS
// books.component.ts
import { Component } from '@angular/core';
import { BookService } from './book.service'; // Import the BookService

@Component({
  selector: 'app-books',
  templateUrl: './books.component.html',
})
export class BooksComponent {
  books: any[] = [];

  constructor(private bookService: BookService) {
    // Use the BookService to get the list of books
    this.books = this.bookService.getBooks();
  }
}
```

In this example:

- The `BookService` is registered with Angular's dependency injection framework using the `@Injectabl`e decorator. It's a singleton service and is provided at the root level (providedIn: 'root').

- In the BooksComponent, we inject the BookService as a dependency in the constructor. Angular's dependency injection framework automatically provides an instance of the BookService to the component.

- The component uses the injected `BookService` to call the getBooks method and populate the books property, which is then used in the component's template.

This demonstrates how dependency injection helps you manage and share dependencies (in this case, the BookService) throughout your Angular application. It promotes reusability and makes it easy to change or update dependencies without modifying a large number of components.

## Custom Modules

### Generate a Custom Module:

You can generate a new module using the Angular CLI, which will create the necessary files for your module:

```
ng generate module books
```

This command generates a new directory named "books" with the required module files.

Define the Module Class (`books.module.ts`):

Open the `books.module.ts` file generated by the Angular CLI and define your custom module. The module class should be decorated with the `@NgModule` decorator, where you configure the module with declarations, imports, providers, and exports:

```TS
// books.module.ts
import { NgModule } from '@angular/core';
import { CommonModule } from '@angular/common';
import { BooksComponent } from './books.component'; // Import the component
import { BookService } from './book.service'; // Import the service

@NgModule({
  declarations: [BooksComponent], // Components to be used in this module
  imports: [CommonModule], // Modules to import (e.g., CommonModule for common directives and pipes)
  providers: [BookService], // Services to be available within this module
  exports: [BooksComponent], // Components to export (optional)
})
export class BooksModule {}
```

- **declarations:** Includes the components that are part of this module. In this case, we have `BooksComponent`.
- **imports:** Lists the modules to import. CommonModule is imported for common Angular directives and pipes.
- **providers:** Specifies the services available within this module, such as the `BookService`.
- **exports:** Optionally, you can specify components to export for use in other modules.

### Use the Custom Module in Your Application:

To use the custom module in your application, you need to import it in the main application module or any other module where you want to use the "books" feature. For example, in your main `app.module.ts`:

```
// app.module.ts
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { BooksModule } from './books/books.module'; // Import the custom module
import { AppComponent } from './app.component';

@NgModule({
  declarations: [AppComponent],
  imports: [BrowserModule, BooksModule], // Import the custom module
  bootstrap: [AppComponent],
})
export class AppModule {}
```

By importing the BooksModule into your main module, you make the "books" feature available within your application.

Explanation:

- The custom module (`BooksModule`) encapsulates the "books" feature, including the `BooksComponent` and `BookService`.
- The `@NgModule` decorator is used to configure the module and specify which components, services, and other resources are associated with it.
- Importing `CommonModule` is common to include directives and pipes shared among different modules.
- By specifying `providers`, you make services available for injection within the module.
- You can optionally export components from the module, making them available for use in other modules that import `BooksModule`.
- In your application's main module (e.g., `AppModule`), you import the custom module (`BooksModule`) to include the "books" feature in your application.

## State Management With Services

State management in an Angular application is the process of handling and controlling the data and user interface (UI) state of your application. This includes managing the data, properties, and behaviors of your application in a consistent and organized way. 

In this example we're going to be handling state between multiple components. In our case a cart and books. 

### Step 1: Create a Shopping Cart Service:

```TS
// cart.service.ts
import { Injectable } from '@angular/core';

@Injectable({
  providedIn: 'root',
})
export class CartService {
  private cart: any[] = [];

  addToCart(book: any) {
    this.cart.push(book);
  }

  removeFromCart(bookId: number) {
    this.cart = this.cart.filter((book) => book.id !== bookId);
  }

  getCart() {
    return this.cart;
  }
}
```

In this service:

- We use the `@Injectable` decorator to make the service available at the root level.
- We maintain a private `cart` array to store the selected books.
- The `addToCart` method adds a book to the cart.
The `removeFromCart` method removes a book from the cart based on its ID.
- The `getCart` method returns the current contents of the cart.

### Step 2: Use the Shopping Cart Service in Your Components:

Now, you can use the `CartService` in your components to manage the shopping cart state.

```TS
// book.component.ts
import { Component, Input } from '@angular/core';
import { CartService } from './cart.service';

@Component({
  selector: 'app-book',
  templateUrl: './book.component.html',
})
export class BookComponent {
  @Input() book: any;

  constructor(private cartService: CartService) {}

  onAddToCart() {
    this.cartService.addToCart(this.book);
  }
}

// cart.component.ts
import { Component } from '@angular/core';
import { CartService } from './cart.service';

@Component({
  selector: 'app-cart',
  templateUrl: './cart.component.html',
})
export class CartComponent {
  cart: any[] = [];

  constructor(private cartService: CartService) {
    this.cart = this.cartService.getCart();
  }

  onRemoveFromCart(bookId: number) {
    this.cartService.removeFromCart(bookId);
  }
}
```

In the `BookComponent`:

- We inject the `CartService` and use the `onAddToCart` method to add a book to the cart.
- In the CartComponent:
- We inject the `CartService` and use the `getCart` method to retrieve the cart contents.
- The `onRemoveFromCart` method is used to remove a book from the cart.

### Step 3: Display Cart Items in the Template:

```html
<!-- cart.component.html -->
<div>
  <h2>Shopping Cart</h2>
  <ul>
    <li *ngFor="let item of cart">
      {{ item.title }} <button (click)="onRemoveFromCart(item.id)">Remove</button>
    </li>
  </ul>
</div>
```

Explanation:

- The `CartService` is used to manage the shopping cart state with methods for adding, removing, and retrieving items from the cart.
- In the `BookComponent`, we use the service to add books to the cart.
- In the `CartComponent`, we use the service to retrieve the cart contents and remove items from the cart.
- The state is shared across components using the `CartService`, and changes made in one component are reflected in the other components that use the same service.

## State Management Options in Angular

In Angular, you have several options for managing state, depending on the complexity of your application:
   
1. **Local Component State:** For simple scenarios, you can manage state within individual components. This can be done using component properties and event binding.
2. **Services:** Services can be used to centralize state and business logic. You can inject services into components and share data and functionality across the application.
3. **RxJS Observables:** RxJS is a powerful library for handling asynchronous data streams. It's commonly used for managing state, especially when dealing with real-time data and complex interactions.
4. **NgRx:** NgRx is a popular library that implements the Redux pattern for state management in Angular. It's especially useful for larger applications where state management can become complex.

## Routing

### Step 1. Generate Routes

In the `app-routing.module.ts` file, configure the routes for your application. Create a route to display a single book:

```TS
// app-routing.module.ts
import { NgModule } from '@angular/core';
import { RouterModule, Routes } from '@angular/router';
import { BooksComponent } from './books/books.component'; // Create this component
import { BookDetailComponent } from './book-detail/book-detail.component'; // Create this component

const routes: Routes = [
  { path: '', redirectTo: '/books', pathMatch: 'full' },
  { path: 'books', component: BooksComponent },
  { path: 'book/:id', component: BookDetailComponent },
];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule],
})
export class AppRoutingModule {}
```

### Step 2: Create Link

In the `books.component.html` file, display the list of books and provide a link to view the details of each book:

```TS
<!-- books.component.html -->
<h2>Books</h2>
<ul>
  <li *ngFor="let book of books">
    {{ book.title }} by {{ book.author }}
    <a [routerLink]="['/book', book.id]">View Details</a>
  </li>
</ul>
```

### Step 3: Display Single Page Component

In the `book-detail.component.ts` file, retrieve and display the details of a single book using the BookService:

```TS
// book-detail.component.ts
import { Component, OnInit } from '@angular/core';
import { ActivatedRoute } from '@angular/router';
import { BookService } from '../book.service';

@Component({
  selector: 'app-book-detail',
  templateUrl: './book-detail.component.html',
  styleUrls: ['./book-detail.component.css'],
})
export class BookDetailComponent implements OnInit {
  book: any;

  constructor(private bookService: BookService, private route: ActivatedRoute) {}

  ngOnInit(): void {
    const id = +this.route.snapshot.paramMap.get('id');
    this.book = this.bookService.getBook(id);
  }
}
```

### Step 4: Create Single Page Template:

In the `book-detail.component.html` file, display the details of the selected book:

```html
<!-- book-detail.component.html -->
<h2>Book Details</h2>
<div *ngIf="book">
  <h3>{{ book.title }}</h3>
  <p>Author: {{ book.author }}</p>
  <p>Description: {{ book.description }}</p>
</div>
```

### Step 5: Update App Module

Make sure to add the AppRoutingModule to your AppModule in the `app.module.ts` file:

```TS
// app.module.ts
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';
import { AppRoutingModule } from './app-routing.module'; // Import the routing module

import { AppComponent } from './app.component';
import { BooksComponent } from './books/books.component';
import { BookDetailComponent } from './book-detail/book-detail.component';

@NgModule({
  declarations: [AppComponent, BooksComponent, BookDetailComponent],
  imports: [BrowserModule, AppRoutingModule], // Add the AppRoutingModule to imports
  providers: [],
  bootstrap: [AppComponent],
})
export class AppModule {}
```

## Route Guards

Route guards are used to protect routes in an Angular application, ensuring that only authorized users can access certain routes. In your case, you can create a route guard to protect the route for viewing book details. 

### Step 1: Create an Auth Guard

Generate a route guard using the Angular CLI:

```
ng generate guard auth
```
This command will generate an `auth.guard.ts` file, which you can use to implement your route guard.

### Step 2: Implement the Route Guard

In the `auth.guard.ts` file, implement your route guard logic. For this example, let's create a simple `canActivate` guard that allows access to the book detail route only if the user is logged in. You can modify the logic according to your authentication requirements.

```TS
// auth.guard.ts
import { Injectable } from '@angular/core';
import { CanActivate, ActivatedRouteSnapshot, RouterStateSnapshot, UrlTree, Router } from '@angular/router';

@Injectable({
  providedIn: 'root',
})
export class AuthGuard implements CanActivate {
  constructor(private router: Router) {}

  canActivate(
    route: ActivatedRouteSnapshot,
    state: RouterStateSnapshot
  ): boolean | UrlTree {
    // Implement your authentication logic here.
    // For this example, let's assume the user is logged in.
    const isLoggedIn = true;

    if (isLoggedIn) {
      return true; // Allow access to the route
    } else {
      // Redirect to the login page or any other route
      return this.router.parseUrl('/login');
    }
  }
}
```

### Step 3: Update the Route Configuration

In your route configuration (`app-routing.module.ts`), apply the route guard to the book detail route:

```
// app-routing.module.ts
import { NgModule } from '@angular/core';
import { RouterModule, Routes } from '@angular/router';
import { BooksComponent } from './books/books.component';
import { BookDetailComponent } from './book-detail/book-detail.component';
import { AuthGuard } from './auth.guard'; // Import the AuthGuard

const routes: Routes = [
  { path: '', redirectTo: '/books', pathMatch: 'full' },
  { path: 'books', component: BooksComponent },
  {
    path: 'book/:id',
    component: BookDetailComponent,
    canActivate: [AuthGuard], // Apply the route guard
  },
];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule],
})
export class AppRoutingModule {}
```

