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







#####Учитывая два целых массива, где второй массив представляет собой перемешанный дубликат первого массива с одним отсутствующим элементом, найдите отсутствующий элемент.
Пожалуйста, обратите внимание, что в массивах могут быть дубликаты, поэтому проверка того, существует ли числовое значение в одном, а не в другом, не является правильным решением.
--

```
find_missing([1, 2, 2, 3], [1, 2, 3]) => 2
find_missing([6, 1, 3, 6, 8, 2], [3, 6, 6, 1, 2]) => 8
```


===

```
function findMissing(arr1, arr2) {
            let notNum = 0;
            for (let i = 0; i < arr1.length; i++) {
                let number = arr2.indexOf(arr1[i])
                if (number >= 0) {
                    delete arr2[number];
                } else { notNum = arr1[i] }
            }
            return notNum;
        }
        console.log(findMissing([1, 2, 3], [1, 3]));
        console.log(findMissing([6, 1, 3, 6, 8, 2], [3, 6, 6, 1, 2]));
        console.log(findMissing([7], []),);
        console.log(findMissing([4, 3, 3, 61, 8, 8], [8, 61, 8, 3, 4]));
        console.log(findMissing([0, 0, 0, 0, 0], [0, 0, 0, 0]));

```




Take an integer n (n >= 0) and a digit d (0 <= d <= 9) as an integer.

Square all numbers k (0 <= k <= n) between 0 and n.

Count the numbers of digits d used in the writing of all the k**2.

Call nb_dig (or nbDig or ...) the function taking n and d as parameters and returning this count.

Examples:
n = 10, d = 1 
the k*k are 0, 1, 4, 9, 16, 25, 36, 49, 64, 81, 100
We are using the digit 1 in: 1, 16, 81, 100. The total count is then 4.

nb_dig(25, 1) returns 11 since
the k*k that contain the digit 1 are:
1, 16, 81, 100, 121, 144, 169, 196, 361, 441.
So there are 11 digits 1 for the squares of numbers between 0 and 25.
Note that 121 has twice the digit 1.
===


```
       function nbDig(n, d) {
            let sum = 0;
            let i = 0;
            while (i <= n) {
                let k = ((i * i) + '').split('');
                for (let i = 0; i < k.length; i++) {
                    d === +(k[i]) ? sum++ : null;
                }
                i++;

            }
            return sum;
        }
        console.log(nbDig(10, 1))
        console.log(nbDig(5750, 0))
        console.log(nbDig(11011, 2))
        console.log(nbDig(12224, 8))
        console.log(nbDig(11549, 1))
```









Напишите функцию, которая возвращает только десятичную часть заданного числа.

Вам нужно обрабатывать только действительные номера, неInfinityNaN, или аналогичные. Всегда возвращайте положительную десятичную часть.

Примеры
getDecimal(2.4)  === 0.4
getDecimal(-0.2) === 0.2
===



```
function getDecimal(n){
  return Math.abs(n%1)
}
```




Task
Given an array/list [] of n integers , find maximum triplet sum in the array Without duplications .
===
Notes :
Array/list size is at least 3 .
===
Array/list numbers could be a mixture of positives , negatives and zeros .
===
Repetition of numbers in the array/list could occur , So (duplications are not included when summing).
===


```
function maxTriSum(numbers) {
            numbers.sort((a, b) => b - a);
            let numberND = [];
            for (let i = 0, y = 1; i < numbers.length; i++, y++) {
                if (numbers[i] !== numbers[y] && numbers[y] !== null) {
                    numberND.push(numbers[i])
                } else {
                    i++;
                    y++;
                    numberND.push(numbers[i])
                }
            }
            let i = 0;
            let sum = 0;
            while (i !== 3) {
                sum += numberND[i];
                i++;
            }
            return sum;

        }

```

```
    assert.strictEqual(maxTriSum([3,2,6,8,2,3]),17);
    assert.strictEqual(maxTriSum([2,9,13,10,5,2,9,5]),32);
    assert.strictEqual(maxTriSum([2,1,8,0,6,4,8,6,2,4]),18);
    assert.strictEqual(maxTriSum([-3,-27,-4,-2,-27,-2]),-9);
    assert.strictEqual(maxTriSum([-14,-12,-7,-42,-809,-14,-12]),-33);
    assert.strictEqual(maxTriSum([-13,-50,57,13,67,-13,57,108,67]),232);
    assert.strictEqual(maxTriSum([-7,12,-7,29,-5,0,-7,0,0,29]),41);
    assert.strictEqual(maxTriSum([-2,0,2]),0);
    assert.strictEqual(maxTriSum([-2,-4,0,-9,2]),0);
    assert.strictEqual(maxTriSum([-5,-1,-9,0,2]),1);
```
