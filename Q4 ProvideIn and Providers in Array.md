Q4. ProvideIn and providers array

**If providededin  is set to root** , then it is a **tree shakable service** which means if it is getting used in application then angular will create only 1 object of the service (singleton service) and if it is not used in application , angular will not include it in final bundle	

**If you pass service in components through providers , then service object is creted as many times it will be passed and providedIn is set to root**

So there are two objects , one is global an one is in component , **the object which is in components will be avilable to components and its child**


There's also way to inject the service in app.module.ts , **it will also behave like when providedIn is set to root**

_The major difference is that , when providedin is set to root ,it’s a tree shakable service while when it is passed in app.module.ts it is not tree shakable service_


Also a way to inject a service

useClass
```
Providers:[(LogService,useClass:LogService)]
```

