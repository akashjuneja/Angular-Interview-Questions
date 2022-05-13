# Reactive Forms and Template Driven Forms

In Reactive forms , lot of thing is done by angular behind the scenes just like the validation ,but in template driven forms we have to build a lot more logic

Reactive forms is little more consuming rather than template driven forms


### Reactive Forms
* In Reactive forms , we have to import ReactiveForms from @angular/forms in app.module.ts

* In the component.ts, we are importing FormsControl and make object of name =new FormControl('') ,for all the fields that we have 

* In component.html, we use it like that
```
<input type="text" [FormControl]="name">
```
This name is similar to what we have defined in component.ts file, this name field have a lot of properties like name.value , name.error,name.setvalue like that

* There are so many fields in forms , so reactive forms provide two methods to group them 
1. Form Group-Defines a form with a fixed set of controls that you can manage together.
2. Form Array-Defines a dynamic form, where you can add and remove controls at run time

For using Form Group 
in app.component.ts file
```
import { Component } from '@angular/core';
import { FormGroup, FormControl } from '@angular/forms';

@Component({
  selector: 'app-profile-editor',
  templateUrl: './profile-editor.component.html',
  styleUrls: ['./profile-editor.component.css']
})
export class ProfileEditorComponent {
  profileForm = new FormGroup({
    firstName: new FormControl(''),
    lastName: new FormControl(''),
  });
}

```

in app.component.html
```
<form [formGroup]="profileForm"> ** imp

  <label for="first-name">First Name: </label>
  <input id="first-name" type="text" formControlName="firstName"> //here we use formControlName

  <label for="last-name">Last Name: </label>
  <input id="last-name" type="text" formControlName="lastName">

</form>
```



### Validators in Reactive Forms
In src/app/profile-editor/profile-editor.component.ts (required validator)
```
import { Validators } from '@angular/forms';
profileForm = this.fb.group({
  firstName: ['', Validators.required],
  lastName: [''],
  address: this.fb.group({
    street: [''],
    city: [''],
    state: [''],
    zip: ['']
  }),
});
```

### Template Driven Forms

In Template Driven Forms , we import FormsModule on app.module.ts

in component.ts 