# Q2. Sibling Communication

## To send data from compA to Comp B --- 
 To send the data from _comp a_ to _comp b_ , we need a service for that
	
In service class, make variable of **subject** class imported from rxjs
```
Sendmessage=new Subject()

commMessage(msg){
Return this.Sendmessage.next()
}
```

Now in _compA_
Import the service in comA ,private in constructor
**And then call the function throught it , whatever message you want to pass ie commMessage function above**


Now in _compB_
Import the service through constructor 
Now call the service , throgh it **call data variable associated through it and subscribe to it ie sendmessage above**
