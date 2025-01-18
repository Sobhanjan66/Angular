```markdown
# Angular Development Guide

## Node.js Installation
- [Node.js Download Link](https://nodejs.org/en)

### Verify Node.js Installation
- Run: `npm --version`

## Angular CLI Installation
- Install Angular CLI: `npm install -g @angular/cli`
- Verify Installation: `ng v`
- [Angular Official Website](https://angular.dev)

## Project Commands
- Create a new project: `ng new project_name`
- Run the project: `ng serve`
- Run the project and open the browser: `ng serve --o`
- Run the project on a specific port: `ng serve --port <port_number>`

## Component Management
- To create a component inside the `app` folder:
  ```bash
  ng generate component <Component-Name>
  ```
- `appComponent` is the **parent component**. Other components are rendered within it by adding their class names to the `imports` array in the `app.component.ts` file.

## Global Styles and Bootstrap Integration
- The `styles.css` file acts as the **global CSS file** for all components.
- Import the Bootstrap CDN in the `<head>` tag of `index.html`.

## Component File Structure
- When creating a component, 4 files are generated:
  - `.html`
  - `.css`
  - `.spec.ts`
  - `.ts`
- Configuration:
  - Use `templateUrl` and `styleUrls` in the component decorator to link `.html` and `.css` files.
  - Alternatively, inline HTML and CSS can be used:
    ```typescript
    @Component({
      template: `<h1>Hello</h1>`,
      styles: [`h1 { color: blue; }`]
    })
    ```

## Rendering Components
- Example: Render `employee.component` and `admin.component` in `app.component.html`:
  ```html
  <app-employee></app-employee>
  <app-admin></app-admin>
  ```
- To render one component within another:
  - Import the class name of the target component in the `ts` file of the rendering component.
  - Include the component's selector in the HTML.

---

## Data Binding in Angular

### 1. One-Way Data Binding
- Binding data between the `.ts` file and the `.html` file (Interpolation, Property Binding) or vice versa (Event Binding).
- Example: **Event Binding**
  ```typescript
  showAlert(msg: string) {
      alert(msg);
  }
  ```
  ```html
  <button class="btn btn-success" (click)="showAlert('Welcome to Angular 18')">Show Welcome</button>
  ```

### 2. Two-Way Data Binding
- Updates are reflected simultaneously between a variable and the input element using `ngModel`.
- Example:
  ```typescript
  courseName = "Angular 18";

  changeCourse() {
      this.courseName = "React 18";
  }
  ```
  ```html
  <input type="text" [(ngModel)]="courseName" /> {{courseName}}
  <button class="btn btn-primary" (click)="changeCourse()">Change Course</button>
  ```
- **Note**: To use `ngModel`, import `FormsModule`.

### 3. Signal (From Angular 17 onwards)
- Signals are initialized and updated as follows:
  ```typescript
  firstName = signal("Sobhanjan");

  changeName() {
      this.firstName.set("Yash");
  }
  ```
  ```html
  <h2>{{firstName()}}</h2>
  <button class="btn btn-info" (click)="changeName()">Change Name</button>
  ```
```