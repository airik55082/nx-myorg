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
- Misc
  - When dealing with prompts (such as after `npx create-nx-workspace myorg`), `Enter` selects the default option (even when no options are presented).
  - Remember to run `npm install`
  - If you get an error about `@myorg/data` or `@myorg/ui` not being a module:
    - Make sure you're `export`ing what's needed in `index.ts`.
      - For `Todo` from the `data` library:
        ```
        export interface Todo {
          title: string;
        }
        ```
    - If you continue to get the same error, try restarting your IDE.
  - The internal North Loop network likes to block access to `.dev` sites. If you connect to the VPN, however, you *can* access them. Since working on the VPN while in the office is a suboptimal state, I logged on briefly, opened all the steps, and then logged off.
  - Unrelated to this particular tutorial, but worth nothing: Mark discovered that including a digit in a component name makes Angular quite unhappy - though it isn't quite able to articulate what has displeased it.
- [Getting Started](https://nx.dev/getting-started/getting-started)
  - Install Angular CLI
    - `npm install -g @angular/cli`
  - Create an Nx workspace
    - `npx`
      - `npx create-nx-workspace myworkspace`
    - `npm`
      - `npm init nx-workspace myworkspace`
    - `yarn`
      - `yarn create nx-workspace myworkspace`
  - Add NX to an existing Angular CLI project
    - `ng add @nrwl/schematics`
  - Create Nx application
    - `ng g application myapp`
  - Serve application
    - `ng serve myapp`
  - Note `Angular Console` VSCode extension
- [Step 1: Create Application](https://nx.dev/tutorial/01-create-application)
  - Create a `myorg` workspace
    - `npx create-nx-workspace myorg`
  - Create an `app` Angular application
    - `ng g app todos`
  - Serve the `todos` application
    - `ng serve todos`
- [Step 2: Add E2E Test](https://nx.dev/tutorial/02-add-e2e-test)
  - Run `todos-e2e` E2E tests
    - `ng e2e todos-e2e --watch`
- [Step 3: Display Todos](https://nx.dev/tutorial/03-display-todos)
    - Run `todos-e2e` E2E tests, in headless mode
      - `ng e2e todos-e2e --headless`
- [Step 4: Connect to API](https://nx.dev/tutorial/04-connect-to-api)
- [Step 5: Add Node Application](https://nx.dev/tutorial/05-add-node-app)
  - Generate a new Node appplication associated with the `todos` app
    - `ng g node-app api --frontendProject=todos`
  - Serve `api` application
    - `ng serve api`
  - Build `api` application
    - `ng build api`
  - Test `api` application
    - `ng test api`
  - I had to delete the extra `/` from `"proxyConfig": "apps/todos//proxy.conf.json"` in `angular.json`.
  - Run todos: `ng serve todos` -> [http://localhost:4200/](http://localhost:4200/)
    - This didn't behave well when I had set the port to `4201` while running `e2e` tests on `4200`.
  - Run api: `ng serve api` -> [http://localhost:3333/api/todos](http://localhost:3333/api/todos)
- [Step 6: Configure Proxy](https://nx.dev/tutorial/06-proxy)
- [Step 7: Share Code](https://nx.dev/tutorial/07-share-code)
  - Create `data` library
    - `ng g lib data`
  - See the notes in **Misc** if you encounter errors related to `data` not being a module.
- [Step 8: Create Libraries](https://nx.dev/tutorial/08-create-libs)
  - Create `ui` library
    - `ng g lib ui`
  - Add a component to `ui` library
    - `ng g component todos --project=ui --export`
  - See the notes in **Misc** if you encounter errors related to `ui` not being a module.
- [Step 9: Dep Graph](https://nx.dev/tutorial/09-dep-graph)
  - View a dependency graph in a browser window
    - `npm run dep-graph`
- [Step 10: Test Affected Projects](https://nx.dev/tutorial/10-test-affected-projects)
  - Print (to console) which apps have changed (compared to `base`, here set to `master`)
    - `npm run affected:apps -- --base=master`
  - Print (to console) which libraries have changed (compared to `base`, here set to `master`)
    - `npm run affected:libs -- --base=master`
  - Test all affected projects
    - `npm run affected:test -- --base=master`
  - Retest all affected projects, only rerunning tests for a project that failed
    - `npm run affected:test -- --base=master --only-failed`
  - Test all projects in parallel
    - `npm run affected:test -- --base=master --parallel`
- Step 11: Build Affected Projects
- Step 12: Summary