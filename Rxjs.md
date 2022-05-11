# RxJs
### What Problem RxJs is trying to solve?

* To handle async calls with multiple events 
   * what does it mean , for eg events that are happening again and again in the future but not at the one time , for eg : when you subscribe to the the channel in the youtube , whenever the guy uploads the video , you get a notification , you dont have to again and again refresh the page

### What are Observables?
Observables are events happening in the future and you want to observe that events for a period of time



(<svg width="612" height="63" style="display: block; font-size: 14px; font-family: Arial, sans-serif; dominant-baseline: central; text-anchor: middle; cursor: default; user-select: none;"><g transform="translate(0, 11)"><g transform="translate(21, 0)"><line x1="0" y1="26" x2="581" y2="26" stroke-width="2" stroke="rgba(0, 0, 0, 0.2)" style="shape-rendering: crispedges;"></line><line x1="0" y1="26" x2="465.8458" y2="26" stroke-width="2" stroke="#000000" style="shape-rendering: crispedges;"></line><path transform="translate(581, 21)" d="M0 0 L10 5 L0 10 z" fill="rgba(0, 0, 0, 0.2)" style="transition: fill 0.2s ease-in-out 0s;"></path><line x1="465.8458" y1="3.5" x2="465.8458" y2="48.5" stroke-width="2" stroke="#000000" style="opacity: 1; transition: opacity 0.5s ease-in-out 0s;"></line><g><g style="transform: translate(117.13px, 26px) scale(1); transition: transform 0.5s ease-in-out 0s;"><circle cx="0" cy="0" r="15" stroke-width="2" stroke="#000000" fill="#ffffff"></circle><text x="0" y="0" style="fill: rgb(0, 0, 0); dominant-baseline: central;">0</text></g><g style="transform: translate(232.749px, 26px) scale(1); transition: transform 0.5s ease-in-out 0s;"><circle cx="0" cy="0" r="15" stroke-width="2" stroke="#000000" fill="#ffffff"></circle><text x="0" y="0" style="fill: rgb(0, 0, 0); dominant-baseline: central;">1</text></g><g style="transform: translate(349.413px, 26px) scale(1); transition: transform 0.5s ease-in-out 0s;"><circle cx="0" cy="0" r="15" stroke-width="2" stroke="#000000" fill="#ffffff"></circle><text x="0" y="0" style="fill: rgb(0, 0, 0); dominant-baseline: central;">2</text></g><g style="transform: translate(465.613px, 26px) scale(1); transition: transform 0.5s ease-in-out 0s;"><circle cx="0" cy="0" r="15" stroke-width="2" stroke="#000000" fill="#ffffff"></circle><text x="0" y="0" style="fill: rgb(0, 0, 0); dominant-baseline: central;">3</text></g></g></g></g><g style="text-anchor: start; dominant-baseline: text-before-edge;"></g></svg>)

### Different ways to create Observables in Rxjs
1. Observables
2. fromEvent

   ```
   import {Observable, fromEvent} from rxjs

   fromEvent(document,'click').subscribe(()=>console.log("click")
   )

   ```
   here we are from an event we are subscribing to the the event with the help of subscribe


   ### Understand the flow of RxJs
    * Operators in RxJs

    Scan Operator
    ```
    import {scan} from rxjs/operators

    fromEvent(document,'click')
    .pipe(scan(count=>count+1,0))
    .subscribe((count)=>console.log(count))
    ```

    ### Observables in RxJs

    ```
    const observable = new Observable (susbcriber => {
       susbcriber. next (1)
       susbcriber. next (2) ;
      susbcriber. next (3) ;


         setTimeout( () => {
        susbcriber. next (4) 
       susbcriber. complete (); //its like a return statement
           }, 2000 )
    ```
### Observers in RxJs
Observers are thing which listens/Observes to the event , for Eg subscribe
subscribe has 3 properties
1. next
2. complete
3. error

```
observable.subscribe({
    next(){}
    error(){}
    complete(){}
})
```
#### From can convert anything to observable
```
import {from} from 'rxjs'

const observable=from([1,2,3])

```
### Pipes and Observables
1. of
2. merge
3. map