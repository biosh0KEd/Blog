# Data Binding with ngModel
## Angular Forms
First we need to import Angular Forms module.

app.module.ts
``` ts
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';

//------------------------------------------
import { FormsModule } from '@angular/forms';
//------------------------------------------

import { AppRoutingModule } from './app-routing.module';
import { AppComponent } from './app.component';
import { BrowserAnimationsModule } from '@angular/platform-browser/animations';

@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    BrowserModule,
    AppRoutingModule,
    BrowserAnimationsModule,
    //----------
    FormsModule
    //----------
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }

```

## Using ngModel to bind the property and the event.
Binding the value of an input:
app.component.ts
``` ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.sass']
})
export class AppComponent {
  public valueInput: string;
}
```
app.component.html
``` html
<input type="text" [(ngModel)]="valueInput"/>
```
Make validations to the value of the input:
app.component.ts
``` ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.sass']
})
export class AppComponent {
  public age: int;
}
```
app.component.html
``` html
<input type="number" max="18" min="10" required #ageInput="ngModel" [(ngModel)]="age"/>
<p>Valid: {{ ageInput.valid }}</p>
```