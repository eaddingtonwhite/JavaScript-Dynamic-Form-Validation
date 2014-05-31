JavaScript-Dynamic-Form-Validation
==================================

JavaScript Dynamic form validation in backbone.js (logic could be used anywhere though)

##Phone Number

###Event

```javascript

//important use on input so it will catch user input before it is displayed!!
events:{
   input input[name=phone]': 'checkPhoneInput'
}

````

###Logic

```javascript

 //Checking at end
    var val = evt.target.value.replace(/\D/g, '');
    if(val.length==11){
      val = val.substr(0, val.length-1);
    }
    val = val.replace(/^(\d{3})(\d{3})(\d{4})$/, "($1) $2-$3", val);

    evt.target.value = val;

    // Checking as user types
    var val = evt.target.value.replace(/\D/g, '');
    var newVal = '';
    if((val.length > 3) && (val.length <= 6)) {
     newVal += '(' + val.substr(0, 3) + ') ';
     val = val.substr(3);
    }
    if (val.length > 6) {
     newVal +=  '(' + val.substr(0, 3) + ') ';
     newVal += val.substr(3, 3) + '-';
     val = val.substr(6);
     if(val.length > 4){
      val = val.substr(0, val.length - 1);
     }
    }
    newVal += val;
    evt.target.value = newVal;
    
```
