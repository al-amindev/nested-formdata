# nested-formdata nested object to formdata conversion

```
const formData = (items, data = new FormData(), name = '') => {
    items = Array.isArray(items)  || items instanceof FileList ? {...items} : items;
    for (let key in items) {
        let nestedName = name ? name + '[' + key + ']' : key;
        if (items[key] && typeof items[key] === 'object' && !(items[key] instanceof File)) {
            formData(items[key], data,  nestedName)
        } else if (typeof items[key] != 'undefined') {
            data.append(nestedName, items[key]);
        }
    }
    return data;
}
export default formData;
```

just impot this formData

```
import formData from "formData";

let nestedObject={
  //here your nested object
}

formData(nestedObject)
```
