Node Js Install - https://nodejs.org/en

Check If Node Installed by checking: - npm --version

Install Angular Cli: — npm install -g @angular/cli

Check if Installed: ng v

https://angular.dev - Angular Home Website

Create Project: ng new project_name

run project: ng serve

run project including opening browser: ng serve --o

run project specifying port number: ng serve --port <port_number>

To create component in app folder which is inside src folder, open integrated terminal of app folder, & give command: ng generate component <Component-Name>

appComponent is the parent Component of all the components, all the individual components are rendered within app component by setting up the class names into Imports array of Component Decorator of app.Component.ts file.

styles.css file is the Global CSS file for all the components.

when we create a component, 4 files are generated: .html, .css, .spec.ts, .ts. 
We configure the html & css files within the .ts file in the Component decorator's templateUrl & styleUrl section. we can bind them like this or can directly write the html & css code in the .ts file by replacing the templateUrl & styleUrl with template & styles & can write the html & css code within them respectively. in case of template, it is written within single quote & in case of styles, it is written within an array.

suppose we have created 2 components named employee.component.ts & admin.component.ts, we can render these two components within app.component.ts like this: <app-employee></app-employee> & <app-admin></app-admin>.



