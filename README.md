Here’s the detailed markdown version for your repository's `Readme.md` file:

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
```