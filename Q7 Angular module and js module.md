# What is the difference between Javascript Module & Angular Module ?
The difference between Js Module & Angular Module is Js module is just a file, but angular module is a class that logically groups the components and others.

ng module is a class that is decorated with ng_module decorator with some meta data. This ng_module specifies that the class is a module

```
@NgModule({
declaration:[],
exports:[],
imports:[],
providers:[],
})

class ModuleName{

}
```
The Angular module classes differ from JavaScript module class in three key respects:
1. An Angular module bounds declarable classes only. 
2. Declarables are the only classes that matter to the Angular.Instead of defining all member classes in one giant file (as in a JavaScript module), we list the module's classes in the @NgModule.declarations list
3. An Angular module can only export the declarable classes it owns or imports from other modules. It doesn't declare or export any other kind of class.