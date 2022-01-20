# array_object_RsSchool
===


Your task is to write a function that takes two or more objects and returns a new object which combines all the input objects.

All input object properties will have only numeric values. Objects are combined together so that the values of matching keys are added together.

An example:
===
аша задача состоит в том, чтобы написать функцию, которая принимает два или более объекта и возвращает новый объект, объединяющий все входные объекты.

Все свойства входного объекта будут иметь только числовые значения. Объекты объединяются вместе таким образом, чтобы значения соответствующих ключей складывались вместе.

Пример:
```
const objA = { a: 10, b: 20, c: 30 }
const objB = { a: 3, c: 6, d: 3 }
combine(objA, objB) // Returns { a: 13, b: 20, c: 36, d: 3 }
```
Функция объединения должна быть хорошим гражданином, поэтому не должна изменять входные объекты.
===

```
function combine() {
  let allM=[];
  let all={};
  for(key in arguments){
    for(i of Object.entries(arguments[key])){
        allM.push(i);
      }
  }
  
  let keyAr='';
  for(i of allM){
    if(keyAr.indexOf(i[0]) >0){
      all[i[0]]=all[i[0]]+i[1];
    }else{
      all[i[0]]=i[1];
      
    }
    keyAr += ` ${i[0]}`;
    
  }
  return all;
```
