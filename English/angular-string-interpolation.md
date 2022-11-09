# Angular String Interpolation, Data Binding and Event Binding
## String Interpolation
String interpolation is an Angular Caracteristic, that allow us to use TS code inside the Html page.

Example:
Printing hello world 5 times inside an h2 tag:
``` html
<h2>{{ 'Hello World'.repeat(5) }}</h2>
```

Printing 3 + 3;
``` html
<h2>3 + 3 = {{ 3 + 3 }}</h2>
```
Using variables from the component:

app.component.html
``` html
<h2>Hello, I am {{ name }} and I am {{ age }} years old.</h2>
```
app.component.ts 
``` ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.sass']
})
export class AppComponent {
  public name: string = 'Alfred';
  public age: number = 25;
}

```

Setting an image source:
``` html
<img src={{img}} alt="image"/>
```

## Property Binding
Binding the state of a button:

app.component.ts
``` ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.sass']
})
export class AppComponent {
  public btnDisabled: bool = true;  
}
```
app.component.html
``` html
<button [disabled]="btnDisabled">Submit</button>
```
Binding the properties of an object.

app.component.ts
``` ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.sass']
})
export class AppComponent {
  person = {
    name: 'Nicolas',
    age: 23
    avatar: 'http://www.w3schools.com/howto/img_avatar.png'
  } 
}
```
app.component.html
``` html
<input type="text" [value]="person.name"/>
<progress max="100" [value]="person.age"></progress>
<img width="100" [src]="person.avatar"/>
```

## Property Binding
Example:
Toogle a button:
app.component.ts
``` ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.sass']
})
export class AppComponent {
  public btnDisabled: bool = true;  
  public toggleButton() {
    this.btnDisabled = !this.btnDisabled;
  }
}
```
app.component.html
``` html
<button [disabled]="btnDisabled">Submit</button>
<button (click)="toggleButton">Toogle button</button>
```