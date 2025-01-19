```markdown
# Angular Development Guide

## Node.js Installation
- Download and install Node.js: [Node.js Official Website](https://nodejs.org/en)
- Verify installation:  
  ```bash
  npm --version
  ```

## Installing Angular CLI
- Install Angular CLI globally:  
  ```bash
  npm install -g @angular/cli
  ```
- Verify Angular CLI installation:  
  ```bash
  ng v
  ```
- Official Angular website: [Angular](https://angular.dev)

## Creating and Running an Angular Project
1. Create a new Angular project:  
   ```bash
   ng new project_name
   ```
2. Run the project:  
   ```bash
   ng serve
   ```
3. Run and open the browser automatically:  
   ```bash
   ng serve --o
   ```
4. Run on a specific port:  
   ```bash
   ng serve --port <port_number>
   ```

## Creating Components
- To create a component in the `app` folder (inside `src`), open the terminal in the `app` directory and use:  
  ```bash
  ng generate component <Component-Name>
  ```

## Application Component Structure
- `appComponent` is the parent component of all components. Individual components are rendered within the `appComponent` by importing their class names into the `Imports` array of the `@Component` decorator in `app.component.ts`.
- The `styles.css` file is the global CSS file for all components.
- To include Bootstrap, import its CDN into the `<head>` section of `index.html`.

## Component Files
When you create a component, four files are generated:
1. `.html` - Template file.
2. `.css` - Stylesheet file.
3. `.spec.ts` - Unit test file.
4. `.ts` - TypeScript logic file.

### Configuring HTML and CSS in `.ts` File
- Use the `templateUrl` and `styleUrls` properties of the `@Component` decorator to link `.html` and `.css` files.
- Alternatively, you can inline HTML and CSS:
  ```typescript
  @Component({
    selector: 'app-example',
    template: '<h1>Inline HTML</h1>',
    styles: ['h1 { color: red; }']
  })
  ```

## Rendering Components
- Example: If you have two components, `employee.component` and `admin.component`:
  - Import their classes into `app.component.ts`.
  - Render them in `app.component.html`:
    ```html
    <app-employee></app-employee>
    <app-admin></app-admin>
    ```
- Components can also be rendered in other components by importing their class names and referencing them in the target component's `.html` file.

---

## Data Binding in Angular

### 1. One-Way Data Binding
- **Definition**: Binding data from `.ts` to `.html` or vice versa.
- **Types**:
  1. **Interpolation**:  
     Bind variables from `.ts` to `.html` using `{{}}`.  
     Example:  
     ```html
     <h1>{{variableName}}</h1>
     ```
  2. **Property Binding**:  
     Bind properties using `[]`.  
     Example:  
     ```html
     <input [value]="variableName">
     ```
  3. **Event Binding**:  
     Bind events using `()`.  
     Example:  
     ```html
     <button (click)="functionName()">Click Me</button>
     ```

- Example of event binding with a function:  
  ```typescript
  showAlert(msg: string) {
    alert(msg);
  }
  ```
  ```html
  <button (click)="showAlert('Welcome to Angular!')">Show Alert</button>
  ```

### 2. Two-Way Data Binding
- **Definition**: Sync data between the `.ts` file and the HTML input fields.
- **Implementation**:
  - Import `FormsModule`.
  - Use `[(ngModel)]` for two-way binding.  
  Example:  
  ```html
  <input type="text" [(ngModel)]="variableName">
  <p>{{variableName}}</p>
  ```
- **Use Case**: Updating input and bound variable values simultaneously.

### 3. Signal (Angular 17+)
- **Definition**: Reactive state management using signals.
- **Example**:
  ```typescript
  firstName = signal('Sobhanjan');

  changeName() {
    this.firstName.set('Yash');
  }
  ```
  ```html
  <h2>{{firstName()}}</h2>
  <button (click)="changeName()">Change Name</button>
  ```

---

### Notes
- `ngModel` works only on input elements.
- It can be used in dropdowns, radio buttons, and other form controls.


# Angular Directives Guide

Angular directives are powerful tools to manipulate the DOM, extend HTML behavior, and dynamically control component rendering. This guide provides a detailed overview of **structural directives** like `*ngIf` and `*ngFor`, complete with examples and explanations.

---

## Table of Contents
1. [Introduction to Directives](#introduction-to-directives)
2. [Structural Directives](#structural-directives)
   - [ngIf](#ngif)
   - [ngFor](#ngfor)
3. [Examples and Use Cases](#examples-and-use-cases)
4. [Summary](#summary)

---

## Introduction to Directives

In Angular, **directives** are classes that let you extend the functionality of HTML. Directives can be categorized as:
- **Structural Directives**: Modify the structure of the DOM (e.g., adding or removing elements).
- **Attribute Directives**: Modify the behavior or appearance of an element.

This guide focuses on **Structural Directives** and their usage.

---

## Structural Directives

### 1. **ngIf**
The `*ngIf` directive is used to conditionally include or exclude elements from the DOM.

#### Basic Syntax:
```html
<div *ngIf="condition">
  Content to display if the condition is true.
</div>
```

---

#### Example 1: Show/Hide a Div with Buttons
**Objective**: Use `*ngIf` to toggle the visibility of a div with "Show" and "Hide" buttons.

**HTML:**
```html
<div *ngIf="isDiv1Visible" class="bg-danger p-3 text-center">
  <h4>Div-1</h4>
</div>

<button class="btn btn-danger" (click)="hideDiv1()">Hide</button>
<button class="btn btn-primary mx-2" (click)="showDiv1()">Show</button>
```

**TypeScript:**
```typescript
isDiv1Visible: boolean = false;

showDiv1() {
  this.isDiv1Visible = true;
}

hideDiv1() {
  this.isDiv1Visible = false;
}
```

---

#### Example 2: Toggle Visibility with a Single Button
**Objective**: Use `*ngIf` with a single "Toggle" button to control the visibility of a div.

**HTML:**
```html
<div *ngIf="isDiv2Visible" class="bg-success p-3 text-center">
  <h4>Div-2</h4>
</div>

<button class="btn btn-success" (click)="toggleDiv2()">Toggle</button>
```

**TypeScript:**
```typescript
isDiv2Visible: boolean = false;

toggleDiv2() {
  this.isDiv2Visible = !this.isDiv2Visible;
}
```

---

#### Example 3: Conditional Visibility with Inputs
**Objective**: Show a div only if the values in two text inputs match.

**HTML:**
```html
<div *ngIf="num1 === num2" class="bg-secondary p-3 text-center">
  <h4>Div-3</h4>
</div>

<input type="text" [(ngModel)]="num1" placeholder="Enter Num-1" class="form-control mb-2">
<input type="text" [(ngModel)]="num2" placeholder="Enter Num-2" class="form-control">
```

**TypeScript:**
```typescript
num1: string = "";
num2: string = "";
```

---

#### Example 4: Checkbox Controlled Visibility
**Objective**: Use a checkbox to toggle the visibility of a div.

**HTML:**
```html
<div *ngIf="isActive">
  <h4>Div-4</h4>
</div>

<input type="checkbox" [(ngModel)]="isActive" /> Toggle Div-4
```

**TypeScript:**
```typescript
isActive: boolean = false;
```

---

#### Example 5: Dropdown Controlled Visibility
**Objective**: Display a div only when a specific option ("West Bengal") is selected in a dropdown menu.

**HTML:**
```html
<div *ngIf="selectedState === 'West Bengal'">
  <h4>Div-5</h4>
</div>

<select [(ngModel)]="selectedState" class="form-select">
  <option value="">Select State</option>
  <option value="Bihar">Bihar</option>
  <option value="West Bengal">West Bengal</option>
  <option value="Odisha">Odisha</option>
</select>
```

**TypeScript:**
```typescript
selectedState: string = "";
```

---

### 2. **ngFor**
The `*ngFor` directive is used to iterate over a collection and render a template for each item.

#### Basic Syntax:
```html
<div *ngFor="let item of items">
  {{ item }}
</div>
```

---

#### Example 1: Rendering an Array of Cities
**Objective**: Display a list of cities and populate a dropdown menu with the same data.

**HTML:**
```html
<ul>
  <li *ngFor="let city of cityArray">{{ city }}</li>
</ul>

<select class="form-select">
  <option *ngFor="let city of cityArray">{{ city }}</option>
</select>
```

**TypeScript:**
```typescript
cityArray: string[] = ["Kolkata", "Delhi", "Mumbai", "Chennai"];
```

---

#### Example 2: Rendering an Object Array
**Objective**: Use `*ngFor` to display a table of student details and populate a dropdown menu.

**HTML:**
```html
<select class="form-select">
  <option *ngFor="let student of studentList" [value]="student.studId">
    {{ student.name }}
  </option>
</select>

<table class="table table-bordered mt-3">
  <thead>
    <tr>
      <th>#</th>
      <th>Name</th>
      <th>City</th>
      <th>Status</th>
    </tr>
  </thead>
  <tbody>
    <tr *ngFor="let student of studentList; let i = index">
      <td>{{ i + 1 }}</td>
      <td>{{ student.name }}</td>
      <td>{{ student.city }}</td>
      <td>
        <span *ngIf="student.isActive" class="badge bg-success">Active</span>
        <span *ngIf="!student.isActive" class="badge bg-danger">Inactive</span>
      </td>
    </tr>
  </tbody>
</table>
```

**TypeScript:**
```typescript
studentList: any[] = [
  { studId: 1, name: "John", city: "Kolkata", isActive: true },
  { studId: 2, name: "Alice", city: "Delhi", isActive: false },
  { studId: 3, name: "Bob", city: "Mumbai", isActive: true },
  { studId: 4, name: "Eve", city: "Chennai", isActive: false },
];
```

---

## Summary

- **ngIf**: Use to conditionally include or remove elements based on expressions.
- **ngFor**: Use to iterate over arrays or collections and render templates for each item.
- **CommonModule** and **FormsModule** must be imported to use directives like `*ngIf`, `*ngFor`, and `ngModel`.

By mastering Angular directives, you can build dynamic and efficient applications with clean and reusable code.
```

    
