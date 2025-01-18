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
We can import the Bootstrap cdn into the head tag of index.html file which is the global html file.

when we create a component, 4 files are generated: .html, .css, .spec.ts, .ts. 
We configure the html & css files within the .ts file in the Component decorator's templateUrl & styleUrl section. we can bind them like this or can directly write the html & css code in the .ts file by replacing the templateUrl & styleUrl with template & styles & can write the html & css code within them respectively. In case of template, it is written within single quote & in case of styles, it is written within an array.

suppose we have created 2 components named employee.component & admin.component, we can import the class names of those two components into the import portion of app.Component.ts & then we can render these two components within app.component.html like this: <app-employee></app-employee> & <app-admin></app-admin>, as app.component is the parent component of all components which is rendered first while we host our project.

Basically, not only within app component, if we want to render any component within other component, so we have to import the class name of that first component into the .ts file of second component & simply have to define the first component into that 2nd component's .html file as like previously mentioned.

----Data Binding----


3 ways in angular:

1.One way data binding
2.Two way data binding
3.Signal (Angular 17 onwards)

1.One way data binding:

Oneway Data Binding is nothing but binding the access of any variable from the .ts file to .html file of any component (Interpolation or Property Binding) or vice versa (Event Binding), so that we can access any variables between ts & html files.

we can achieve it by declaring the variable (with or without initialization) into the export section of the ts file & using it in the html file through interpolation ( declaring the variable warpped with {{}} ) or Property Binding ( wrapping the property or attribute with [] ) or in case of Event Binding, we first write a function within export section of the ts file with a parameter & then call the function with click event within html file. example:

  writing a function named "showAlert" within export section:
       
        showAlert( msg: string){
            alert(msg)
        }

  Now using a click event in html file:

        <button class="btn btn-success" (click)="showAlert("Welcome to Angular 18")">Show Welcome</button>




2.Two way data binding:

Suppose we have a text box with some value & other same valued texts both of which refers to same binded variable declared in ts file. Now we want that if we change the text box value, the text values also should be changed & simultaneously if we change the text values, the text box value should be also changed. Here we use two way data binding.

Example:
  Suppose we have declared a variable in the ts file named courseName & initialized its value = "Angular 18";

  now we have designed a function named changeCourse:

       changeCourse(){
        this.courseName = "React 18"
       } 

  now we have created a button called "Change Course" & fired a click event & called the function in it.

       <button class="btn btn-primary" (click)="changeCourse()">Change Course</button>

 Now we have set up a preparation by which if we click on the button we can change our variable value, by which we can change the text values along with text box value. but what if we wanna change the text values concurrently changing the text box value?

 Here we use the two way binding. 
 In angular we can impliment two way data binding using ngModel. 

 To use ngModel, we have to import FormsModule. Now we can connect any text box with variable. If we change the input box value, the variable value will also be updated in the front-end without explicitely changing it by writing any function.

   Example:

       <input type="text" [(ngModel)]="courseName"/>.{{courseName}}

    Now if i change the text box value, the other binded text values will also change & also vice versa.

Note: ngModel only works on input elements.

We can also implement ngModel in Select tag of drop down input type or radio box  to set its by default value which would be initialized in the binded variable.



3.Signal:

It is initialized like this:

     firstName = signal("Sobhanjan");

Then we can bind it in frontend like this:

    <h2>{{firstName()}}</h2>

Now, we can change its value using function like this:

     changeName(){
        this.firstName.set("Yash")
       } 

    & call this function using click event on any button.





 


