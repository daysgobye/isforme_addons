# Settings Panel
To stop everyone finding there own way of handeling settings this is one settings standard.
Much like Black you may not like it but at least its always the same.

## How to use
see hideinput for example

All you need to do is add a field onto `window.spaceSettings`
```js
window.spaceSettings.yourAddon={
    title:"your addon - feature here",
    fieldType:"boolean"|"string",
    description:"",
    value:boolean|"string",
    onSave:(newValue:string|boolean)=>void
}
```

## Storage
Its good to remember this is a UI for changing settings not a storage for settings.
That's why you set an onChange callback function for you to handle your own storage.
You can store your settings in a few ways in memory(will reset on page reload),localStorge(will reset for new viewer),as space posts **need to get users write password** then store in and parse html comments( this is very robust but does add a lot of bloat to your code and is not always needed)

