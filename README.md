# Myorg

This project was generated using [Nx](https://nx.dev).

<p align="center"><img src="https://raw.githubusercontent.com/nrwl/nx/master/nx-logo.png" width="450"></p>

🔎 **Nx is a set of Angular CLI power-ups for modern development.**

## Quick Start & Documentation

[30-minute video showing all Nx features](https://nx.dev/getting-started/what-is-nx)

[Interactive tutorial](https://nx.dev/tutorial/01-create-application)

## Generate your first application

Run `ng g app myapp` to generate an application. When using Nx, you can create multiple applications and libraries in the same CLI workspace.

## Development server

Run `ng serve myapp` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name --project=myapp` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build myapp` to build the project. The build artifacts will be stored in the `dist/` directory. Use the `--prod` flag for a production build.

## Running unit tests

Run `ng test` to execute the unit tests via [Jest](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via [Cypress](http://www.protractortest.org/).

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI README](https://github.com/angular/angular-cli/blob/master/README.md).


## Eric's Notes
- General
  - When dealing with prompts (such as after `npx create-nx-workspace myorg`), `Enter` selects the default option (even when no options are presented).
  - `npm install`
- Step 1: Create Application
  - Create a new workspace
    - `npx create-nx-workspace myorg`
  - Create an Angular application
    - `ng g app todos`
  - Serve the `todos` application
    - `ng serve todos`
- Step 2: Add E2E Test
  - Run E2E tests
    - `ng e2e todos-e2e --watch`
- Step 3: Display Todos
    - `ng e2e todos-e2e --headless`
- Step 4: Connect to API
  - 
- Step 5: Add Node Application
  - Generate a new Node appplication associated with the `todos` app
    - `ng g node-app api --frontendProject=todos`
  - Serve application
    - `ng serve api`
  - Build application
    - `ng build api`
  - Test application
    - `ng test api`
  - I had to delete the extra `/` from `"proxyConfig": "apps/todos//proxy.conf.json"` in `angular.json`.
  - Run todos: `ng serve todos` -> [http://localhost:4200/](http://localhost:4200/)
    - This didn't behave well when I had set the port to `4201` while running `e2e` tests on `4200`.
  - Run api: `ng serve api` -> [http://localhost:3333/api/todos]
- Step 6
- Step 7
  - Create a library
    - `ng g lib data`
  - If you get an error about `@myorg/data` not being a module, make sure to add an `export` in front of the `interface`:
    ```
    interface Todo {
      title: string;
    }
    ```
- 
