# Settings Panel
To stop everyone finding there own way of handeling settings this is one settings standard.
Much like Black you may not like it but at least its always the same.

## How to use
see hideinput for example

All you need to do is add a field onto `window.spaceSettings`
```js
window.spaceSettings.yourAddon={
    title:"your addon - feature here",
    fieldType:"boolean"|"string"|"custom",
    description:"",
    value:boolean|"string",
    onSave:(newValue:string|boolean)=>void
}

```
### Not required but you can set an on mount callback
```js
window.spaceSettingsOnMount.push(()=>{})
```

### For something very custom you can handle everything your self like this
```js
window.spaceSettings.yourAddon={
    title:"my_custom_setting", // one string this will become your class name for the div you have full controll over
    fieldType:"custom",
}
window.spaceSettingsOnMount.push(()=>{
    // get your div 
    const form = document.getElementsByClassName("my_custom_setting")[0]
    if(form){
        // go to town you controll everything now
        // best for complex inputs like arrays or objects of data
        // this is your addon you can style it how ever you like we dont even ask that it matches the rest of the site
        // the only thing we ask is for you to keep settings in this popover instead of bleeding around the page
    }

})
```

## Storage
Its good to remember this is a UI for changing settings not a storage for settings.
That's why you set an onChange callback function for you to handle your own storage.
You can store your settings in a few ways in memory(will reset on page reload),localStorge(will reset for new viewer),as space posts **need to get users write password** then store in and parse html comments( this is very robust but does add a lot of bloat to your code and is not always needed)

