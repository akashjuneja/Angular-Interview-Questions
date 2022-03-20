

# Q1. Can you explain, various ways of component communication in Angular

##	1. From  Parent to child with Input Decorator

``` 
--------In parentComponent.ts------------

import { Component } from '@angular/core';
@Component({
  selector: 'app-parent',
  template: ` 
     <app-child [childMessage]="parentMessage"></app-child> 
`,
  styleUrls: ['./parent.component.css']
})
export class ParentComponent{
    
  parentMessage = "message from parent";
constructor() { }
}

---------In childComponent.ts-------------
import { Component, Input } from '@angular/core';
@Component({
  selector: 'app-child',
  template: ` Say {{ message }  `,
  styleUrls: ['./child.component.css']
})
export class ChildComponent {
    
  @Input() childMessage: string;
constructor() { }
}

```
## 2. From Child to Parent with @Output decorator and Eventemitter property
	
The Child Component exposes an EventEmitter Property. This Property is adorned with the @Output decorator. When Child Component needs to communicate with the parent it raises the event. The Parent Component listens to that event and reacts to it.
	
To raise an event, an @Output() must have the type of EventEmitter, which is a class in @angular/core that you use to emit custom events.
	
```
	@Output() newItemEvent = new EventEmitter<number>();
	
	<child-component  (newItemEvent)="countChangedHandler($event)"></child-component>`
	
	countChangedHandler(count: number) {
	    this.Counter = count;
	    console.log(count);
	  }
      
```
	
	
## 3.From Child to Parent with @ViewChild and AfterViewInit
	 	
ViewChild allows a child component to be injected into a parent component.
It will give the parent access to its attributes and functions.
A Child won’t be available to give access until the view has been initialized.
```
-------In ParentComponent.ts-------------
import { Component, ViewChild, AfterViewInit  ,ChangeDetectorRef} from '@angular/core';
import { ChildComponent } from "../child/child.component";
	@Component({
  selector: 'app-parent',
  template: `
    Message: {{ message }}
    <app-child></app-child>
  `,
  styleUrls: ['./parent.component.css']
})
	export class ParentComponent implements AfterViewInit {
  
  @ViewChild(ChildComponent) child;
  
  constructor(private change:ChangeDetectorRef) { }
  
  Message:string="";
  
  ngAfterViewInit() {
	This.change.detectChanges;
	this.message = this.child.akash  --->this should be in child component
  }
}
	
	From <https://www.thirdrocktechkno.com/blog/how-angular-components-communicate/> 
```