# Component LifeCycle

### 8 Lifecycle Hooks



1. ngOnChanges()--mostly used
2. ngOnInit()--mostly used
3. ngDoCheck()
4. ngAfterContentInit()
5. ngAfterContentChecked()
6. ngAfterViewInit()---mostly used
7. ngAfterViewChecked()
8. ngOnDestroy()--mostly used

## ngOnChanges()
1. used in pretty much any component that has input 
2. called whenever input value changes
3. is called first time before ngOnInit

## ngOnInit()
1. used to initialize data in a component
2. called after input values are set
3. added to every component by default by angular CLI
4. called only once

## ngDoCheck()
1. called during all change detection runs
2. A run throuh the view by Angular to update/detect chnages

## ngAfterContentInit()
1. called only after first ngDoCheck()
2. called after the first run through of initializing content

## ngAfterContentCheckd()
1. called after every ngDoCheck()
2. waits till after ngAfterContentInit() on first run through

## ngAfterViewInit()
1. Called after angular initializes componnet and child component content
2. called anly once after view is initialized

## ngAfterViewCheckd()
1. called after all the conent is initialized and checked
2. first call after ngAfterViewInit()

## ngOnDestroy()

1. used to clean up necessary code when a component is removed from DOM
2. used to unsubscribe from services
3. called only once just before component is removed from DOM

