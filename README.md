# javascript-array-methods-all
Bu belge Javascript 'in tüm temel array metotlarını, bu metotların tanımlarını ve kullanım örneklerini içermektedir. 
Bu markdown dosyası github.com/burakkrt tarafından hazırlanmıştır.


# Array Methods

### concant()

İki veya daha fazla diziyi birleştirmek için kullanılır. Yeni bir dizi geriye döndürür.

```jsx
const array1 = ['a', 'b', 'c'];
const array2 = ['d', 'e', 'f'];
const array3 = array1.concat(array2);

console.log(array3);
// Expected output: Array ["a", "b", "c", "d", "e", "f"]

const result = array1.concat(array2,array3) //Üç diziyi birleştirme
```

### copyWithin()

Bir dizinin bir bölümünü başka bir diziye kopyalar, bunu yaparken kopyaladığı dizinin eleman sayısını değiştirmek yerine üzerine yazar.

```jsx
const array1 = ['a', 'b', 'c', 'd', 'e'];

// array1 'deki 3. indexden başlayıp 4. indexe kadar olan elemanları 0. index 'e yaz
console.log(array1.copyWithin(0, 3, 4));
// Expected output: Array ["d", "b", "c", "d", "e"]
// Burada çıktı olarak dizini 0. elemanı olan a elemanın üzerine 3 ile 4 index arasındaki
// d elemanını yazdırdı. Dizinin uzunluğu değişmedi.

console.log(array1.copyWithin(1, 3));
// Expected output: Array ["d", "d", "e", "d", "e"]
// 3. indexten itibaren (d,e) olan tüm elemanları 1. index 'den itibaren üzerine yazıp
// kopyaladı.
```

### every()

Dizideki tüm elemanların belirtilen koşulu sağlayıp sağlamadığına göre boolean değer döndürür.

```jsx
const array1 = [1, 30, 39, 29, 10, 13];
console.log(array1.every((eleman) => eleman !== 0)); //true

// yada dışarıdan fonksiyon gönderebiliriz.
const isBelowThreshold = (currentValue) => currentValue < 10;
console.log(array1.every(isBelowThreshold)); //false
```

### filter()

Verilen dizideki koşulları sağlayan elemanların kopyasını bir dizi olarak geri döndürür.

```jsx
const words = ['spray', 'limit', 'elite', 'exuberant', 'destruction', 'present'];

const result = words.filter(word => word.length > 6);

console.log(result);
// Expected output: Array ["exuberant", "destruction", "present"]
```

```jsx
const fruits = ["apple", "banana", "grapes", "mango", "orange"];

/**
 * Filter array items based on search criteria (query)
 */
function filterItems(arr, query) {
  return arr.filter((el) => el.toLowerCase().includes(query.toLowerCase()));
}

console.log(filterItems(fruits, "ap")); // ['apple', 'grapes']
console.log(filterItems(fruits, "an")); // ['banana', 'mango', 'orange']
```

```jsx
const array = [-3, -2, -1, 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13];

function isPrime(num) {
  for (let i = 2; num > i; i++) { //her sayı 1 e bölüneceği için 2 den başla.
    if (num % i === 0) { //eğer tam bölünüyor ise
      return false;  //bu elemanı false olarak döndür yani alma
    }
  }
  return num > 1;  //onun haricinde 1 den büyük tüm sayıları geri döndür.
}

// kendisi ve 1 haricinde hiçbir sayıya bölünmeneyenler. (asay sayılar)
console.log(array.filter(isPrime)); // [2, 3, 5, 7, 11, 13]
```

### forEach()

Bu yöntem, bir dizi (array) üzerindeki her bir eleman için belirtilen bir fonksiyonu çağırmak için kullanılır. 

```jsx
const array1 = ['a', 'b', 'c'];

array1.forEach(element => console.log(element));

//index değeride alınabilir
array1.forEach((element,index) => console.log(index + " : " + element));
```

**map** döngü sonucunda yeni bir dizi oluşturulur ve bu dizi, döngüde yapılan işlemlerin sonuçları ile doldurulur ama **forEach** geriye bir değer döndürmez.

```jsx
const dizi = [1, 2, 3, 4];

const yeniDizi = dizi.map(function(eleman) {
  return eleman * 2;
});
```

### indexOf()

Dizideki elemanın index numarasını döndürür, yoksa -1 döner.

```jsx
const beasts = ['ant', 'bison', 'camel', 'duck', 'bison'];

console.log(beasts.indexOf('bison'));
// Expected output: 1

// 2. indexten itibaren arama yapıyor. (yani 1. indexteki bison 'u görmez)
console.log(beasts.indexOf('bison', 2));
// Expected output: 4

console.log(beasts.indexOf('giraffe'));
// Expected output: -1
```

### lastIndexOf()

Dizide aranan elemanın en sonuncu index ‘ini döndürür. Birden fazla aynı eleman olduğu dizilerde kullanışlıdır.

```jsx
const animals = ['Dodo', 'Tiger', 'Penguin', 'Dodo'];

console.log(animals.lastIndexOf('Dodo'));
// Expected output: 3

console.log(animals.lastIndexOf('Tiger'));
// Expected output: 1
```

### map()

Amacı, dizi içindeki her bir elemana sırayla erişerek belirli bir işlem sonucunda yeni bir dizi oluşturmaktır.

```jsx
const array1 = [1, 4, 9, 16];

// Pass a function to map
const map1 = array1.map(x => x * 2);

console.log(map1);
// Expected output: Array [2, 8, 18, 32]
```

### reduce()

Bir dizi (array) üzerinde döngü yaparak tüm elemanları birleştirerek veya toplayarak sonuç elde etmek için kullanılan bir dizi yöntemidir.

```jsx
const array1 = [1, 2, 3, 4];

const initialValue = 0; //başlangıç değeri

const sum= array1.reduce(
  (oncekiDeger, suankiEleman) => oncekiDeger+ oncekiDeger, initialValue
);

//return 0+1+2+3+4 = 10
```

Başlangıç değerini istediğimiz değer atayabiliriz. Eğer önceki değer yok ise dizideki ilk elemanın değerini kabul eder. (burada ilk eleman 1)

```jsx
const array1 = [1, 2, 3, 4];

const sum = array1.reduce((prev, current) => { return prev + current }, 2);

console.log(sum) // 0 dan başla 2 + 1 + 2 + 3 + 4 = 12
```

### reduceRight()

reduce ile aynı sadece dizinin sonundan başına doğru ters hareket eder.

```jsx
const array1 = [0,1,2,3,4];

let sum = array1.reduceRight((prev,current) =>  prev + " - " + current);

console.log(sum); "4-3-2-1-0"
```

> Birkaç farklı örnek
> 

```jsx
const array1 = [[0, 1], [2, 3], [4, 5]];

const result = array1.reduceRight((accumulator, currentValue) => accumulator.concat(currentValue));

console.log(result);
// Expected output: Array [4, 5, 2, 3, 0, 1]
```

```jsx
const array1 = [[0, 1], [2, 3], [4, 5]];

const result = array1.map(arr => 
     arr.reduce((prev,current) => prev + current)
).reduce((prev, current) => prev + current)

console.log(result);
// Expected output: 15
```

### reverse()

Bir dizideki elemanları index sırasına göre tersten geri döndürür.

```jsx
const array1 = ['one', 'two', 'three'];

const reversed = array1.reverse();
console.log(reversed) //result ["three", "two", "one"]

console.log(array1) // ÖNEMLİ : reverse yi başka bir diziye aktarsak bile 
// ana dizide değişmiş olur. result ["three", "two", "one"]
```

### toReverse()

Uygulanan diziyi değiştirmeden tersine döndürür.

```jsx
const array1 = ['one', 'two', 'three'];

const reversed = array1.reverse();
console.log(reversed) //result ["three", "two", "one"]

console.log(array1) // ana dizi değişmez ['one', 'two', 'three']
```

### slice()

Bir dizinin belirtilen index aralığının kopyasını geri döndürür. Orijinal diziyi değiştirmez. İkinci parametre olarak belirtilen son index ‘i saymaz, yani slice[0,2] methunda indexi 0 ve 1 olan değerleri geri döndürür.

```jsx
const animals = ['ant', 'bison', 'camel', 'duck', 'elephant'];

console.log(animals.slice(2));
// Expected output: Array ["camel", "duck", "elephant"]

console.log(animals.slice(2, 4));
// Expected output: Array ["camel", "duck"]

console.log(animals.slice(1, 5));
// Expected output: Array ["bison", "camel", "duck", "elephant"]

console.log(animals.slice(-2));
// Expected output: Array ["duck", "elephant"]

console.log(animals.slice(2, -1));
// Expected output: Array ["camel", "duck"]
```

### some()

Dizideki belirtilen koşulun en az bir kere sağlanması durumunda true, hiç sağlanmaz ise false değerini döndürmek için kullanılır.

```jsx
[0,1,2,3,4].some(element => element > 2) //return true
[0,1,2,3,4].some(element => element % 2 === 0) //return true
[0,1,2,3,4].some(element => element > 5) //return false

//dışarıdan callBack fonksiyon atama
function cbFunc(element){
return element > 2
}

[0,1,2,3,4].some(cbFunc) //return true

//dışarıdan atanan callBack function 3 değer alabilir. element zorunlu diğerleri opsionel.
function cbThree(element, index, arr){
		console.log(index + " : " +  element);
return element.length > 7;
}

["elma","muz","portakal","kivi"].some(cbThree);

// her bir elemanın tarar ve verilen koşulu sağladığı anda döngü durur ve true sonucu döndürür)
// koşul sağlanana kadar tüm elemanları gezer ve sağlanmaz ise en sonunda false döndürür.
//return
// 0 : "elma"
// 1 : "muz"
// 2 : "portakal"
// true  

function cbThree(element, index, arr){
		console.log(index + " : " +  element);
return element.length > 15;
}

["elma","muz","portakal","kivi"].some(cbThree);
// 0 : "elma"
// 1 : "muz"
// 2 : "portakal"
// 3 : "kivi"
// false
```

### sort()

Dizideki elemanları küçükten büyüğe doğru sıralar. Sıralamayı UTF-16 kod birimi değerlerine göre yaptığı için genellikle beklediğimiz sonuçları sergilemez. Orijinal diziyi değiştirir.

```jsx
const months = ["Ocak","Mart","Şubat","Nisan","Ali"];
months.sort();
console.log(months); // return ["Ali","Mart","Nisan","Ocak","Şubat"] (alfabeye göre sıralar)
```

**ÖNEMLİ :** Sayılarda karşılaştırma işlevi (compare function) geçirerek doğru sıralama yapabilirsiniz:

```jsx
//unicode göre sıralama
const array1 = [1, 30, 4, 21, 100000];
array1.sort();
console.log(array1);
// Expected output: Array [1, 100000, 21, 30, 4]

//doğru sıralama
let numbers = [40, 100, 1, 5, 25, 10];
numbers.sort(function(a, b) {
  return a - b;  //a - b diyerek eğer a değeri b den büyükse çıkartılabilir mantığı ile sıralar.
});

console.log(numbers);
// Çıktı: [1, 5, 10, 25, 40, 100]
```

### toSort()

Orijinal diziyi değiştirmeden geriye yeni bir dizi döndürerek sıralar.

```jsx
let numbers = [40, 100, 1, 5, 25, 10];
let newArray = numbers.toSort(function(a, b) {
  return a - b;  //a - b diyerek eğer a değeri b den büyükse çıkartılabilir mantığı ile sıralar.
});

console.log(newArray );
// Çıktı: [1, 5, 10, 25, 40, 100]
```

### splice()

Dizilerdeki elemanları eklemek, çıkarmak veya değiştirmek için kullanılan bir dizi işlevidir. Bu yöntem, dizi üzerinde değişiklik yapar ve değiştirilen elemanları yeni bir dizi olarak döndürür.

```jsx
array.splice(start, deleteCount, item1, item2, ...);
```

Parametreler:

- **`start`**: Dizide değişiklik yapılacak başlangıç indeksi. Ekleme veya çıkarma işlemi bu indeksten başlayarak yapılır.
- **`deleteCount`**: Başlangıç indeksinden itibaren kaç elemanın silineceği. 0 ise eleman silinmez, yalnızca ekleme yapılır.
- **`item1, item2, ...`**: Eklenecek yeni elemanlar. Bu parametreler isteğe bağlıdır.

Eleman ekleme:

```jsx
let fruits = ["elma", "armut", "portakal"];
fruits.splice(2, 0, "muz", "çilek");

console.log(fruits);
// Çıktı: ["elma", "armut", "muz", "çilek", "portakal"]
```

Eleman silme:

```jsx
let numbers = [10, 20, 30, 40, 50];
numbers.splice(2, 2);

console.log(numbers);
// Çıktı: [10, 20, 50]
```

Eleman değiştirme:

```jsx
let colors = ["kırmızı", "mavi", "yeşil", "sarı"];
colors.splice(1, 1, "turuncu");

console.log(colors);
	// Çıktı: ["kırmızı", "turuncu", "yeşil", "sarı"]
```

### entries()

Bir dizi veya bir nesne içindeki her bir öğenin key-value çiftlerinden oluşan bir dizi döndüren bir dizi veya nesne yöntemidir. Geriye yeni bir dizi döndürür.

```jsx
const fruits = ['apple', 'banana', 'orange'];

const entries = fruits.entries(); //geriye yeni dizi döndürür.

for (const entry of entries) {
  console.log(entry);
}
// [0, 'apple']
// [1, 'banana']
// [2, 'orange']
```

```jsx
const fruits = ['apple', 'banana', 'orange'];

for(let [key, value] of fruits.entries){
	console.log(key + " : " + value)
}
// "0 : apple"
// "1 : banana"
// "2 : orange"
```

```jsx
const person = {
  name: 'John',
  age: 30,
  city: 'New York'
};

for(let [key,value] of Object.entries(person)){
  console.log(key + " : " + value)
}

// "name : John"
// "age : 30"
// "city : New York"
```

```jsx
for (const element of [, "a"].entries()) {
  console.log(element);
}
// [0, undefined]
// [1, 'a']
```

### fill()

Bir dizideki elemanları verilen değerle değiştirip geriye döndürür.  Dizinin uzunluğundan fazla ekleme yapmaz. `fill(value, start, end)`

```jsx
const array1 = [1, 2, 3, 4];

console.log(array1.fill(0, 2, 4)); 
//  Array [1, 2, 0, 0] (0 değerini 2 den başlayıp 4 indexde kadar var olan elemanla değiş.)

console.log(array1.fill(5, 1)); 
// Array [1, 5, 5, 5] (5 değerini 1. indexten itibaren var olan elemanlar değiştir.)

console.log(array1.fill(6)); 
//Array [6, 6, 6, 6] Tüm elemanları 6 deperi ile değiştir.
```

### find()

Dizide verilen koşulun sağlandığı ilk elemanı geriye döndürür. Eğer hiçbir eleman koşulu sağlamaz ise `undefied` değeri döner.

```jsx
onst array1 = [5, 12, 8, 130, 44];

const found = array1.find(element => element > 10);

console.log(found); // Expected output: 12
```

```jsx
const array1 = [{id: 1, name: "kadir"},{id: 2, name: "süleyman"},{id: 3, name: "coşkun"}];

const found = array1.find(({id}) => id > 1);

console.log(found); // Expected output: return object {id: 2, name: "süleyman"}
```

### findIndex()

Dizideki verilen koşulu sağlayan ilk elemanın index numarasını geriye döndürür. Koşulu sağlayan eleman yok ise `-1` değerini döndürür.

```jsx
const array1 = [5, 12, 8, 130, 44];

const isLargeNumber = (element) => element > 13;

console.log(array1.findIndex(isLargeNumber)); // Expected output: 3
```

### findLast()

Diziye tersten başlayarak verilen koşulu sağlayan ilk elemanı geriye döndürür. Eleman yok ise `undefied` değeri geriye döndürür.

```jsx
const array1 = [5, 12, 50, 130, 44];

const found = array1.find((element) => element > 45);

console.log(found);  // Expected output: 130
```

### findLastIndex()

Diziye tersten başlayarak verilen koşulu sağlayan ilk elemanın index numarasını geriye döndürür. Eleman yok ise `-1` değeri geriye döner.

```jsx
const array1 = [5, 12, 50, 130, 44];

const isLargeNumber = (element) => element > 45;

console.log(array1.findLastIndex(isLargeNumber));  // Expected output: 3
```

### includes()

Dizideki belirli bir değerin olup olmadığını kontrol eder ve geriye true veya false döndürür.

```jsx
const pets = ['cat', 'dog', 'bat',12];

console.log(pets.includes(12)) //true
console.log(pets.includes("a")) //true
console.log([0,1, ,2].includes(undefined)) //true
```

### join()

Bir dizideki elemanları birleştirerek yeni bir string ifade döndürür.

```jsx
const elements = ['Fire', 'Air', 'Water'];

console.log(elements.join()); // "Fire,Air,Water"
console.log(elements.join('')); // "FireAirWater"
console.log(elements.join('-')); // "Fire-Air-Water"
console.log([1, undefined, 3].join()); // '1,,3'
```

### keys()

Dizideki her bir eleman için index numarası döndürür. Object ile kullanmak daha faydalı.

```jsx
const array1 = ['a', 'b', ,'c',];
const ite = Object.keys(array1); 
console.log(ite) // ["0","1","3"]

// yada spread operatör ile elemanları yayarak string değer döndürebiliriz.
const ite2 = Object.keys(array1);
console.log(...ite2) // "0","1","2"
```

### toLocaleString()

Tarihlerin dile duyarlı string değerini geriye döndürür.

```jsx
let date = new Date();

console.log(date) //return "2023-07-31T06:39:18.979Z"
console.log(date.toLocaleString('tr-TR')) //return "31.07.2023 09:39:18"
```
