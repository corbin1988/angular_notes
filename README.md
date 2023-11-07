# Angular Context Switching Notes

## Starting A Project And Running It

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

