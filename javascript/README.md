# JavaScript Exercises

## Exercise 1
A text in CSV format has the name of the fields in the first row and the data in the remaining rows, separated by commas. 
Implement a parser that receives a string in CSV format and returns a collection of objects. 
Use destructuring, rest y spread operator where you feel convenient.
```
const data = `id,name,surname,gender,email,picture
15519533,Raul,Flores,male,raul.flores@example.com,https://randomuser.me/api/portraits/men/42.jpg
82739790,Alvaro,Alvarez,male,alvaro.alvarez@example.com,https://randomuser.me/api/portraits/men/48.jpg
37206344,Adrian,Pastor,male,adrian.pastor@example.com,https://randomuser.me/api/portraits/men/86.jpg
58054375,Fatima,Guerrero,female,fatima.guerrero@example.com,https://randomuser.me/api/portraits/women/74.jpg
35133706,Raul,Ruiz,male,raul.ruiz@example.com,https://randomuser.me/api/portraits/men/78.jpg
79300902,Nerea,Santos,female,nerea.santos@example.com,https://randomuser.me/api/portraits/women/61.jpg
89802965,Andres,Sanchez,male,andres.sanchez@example.com,https://randomuser.me/api/portraits/men/34.jpg
62431141,Lorenzo,Gomez,male,lorenzo.gomez@example.com,https://randomuser.me/api/portraits/men/81.jpg
05298880,Marco,Campos,male,marco.campos@example.com,https://randomuser.me/api/portraits/men/67.jpg
61539018,Marco,Calvo,male,marco.calvo@example.com,https://randomuser.me/api/portraits/men/86.jpg`;

const fromCSV = (csv) => {

};

const result = fromCSV(data);
console.log(result);

```

```
Result output:

[
  {
    id: "15519533",
    name: "Raul",
    surname: "Flores",
    gender: "male",
    email: "raul.flores@example.com",
    picture: "https://randomuser.me/api/portraits/men/42.jpg"
  },
  {
    id: "82739790",
    name: "Alvaro",
    surname: "Alvarez",
    gender: "male",
    email: "alvaro.alvarez@example.com",
    picture: "https://randomuser.me/api/portraits/men/48.jpg"
  },
  {
    ...
  }
]

```
My first attempt was returning an array of objects with the data provided except the headers.

```
const data = `id,name,surname,gender,email,picture
15519533,Raul,Flores,male,raul.flores@example.com,https://randomuser.me/api/portraits/men/42.jpg
82739790,Alvaro,Alvarez,male,alvaro.alvarez@example.com,https://randomuser.me/api/portraits/men/48.jpg
37206344,Adrian,Pastor,male,adrian.pastor@example.com,https://randomuser.me/api/portraits/men/86.jpg
58054375,Fatima,Guerrero,female,fatima.guerrero@example.com,https://randomuser.me/api/portraits/women/74.jpg
35133706,Raul,Ruiz,male,raul.ruiz@example.com,https://randomuser.me/api/portraits/men/78.jpg
79300902,Nerea,Santos,female,nerea.santos@example.com,https://randomuser.me/api/portraits/women/61.jpg
89802965,Andres,Sanchez,male,andres.sanchez@example.com,https://randomuser.me/api/portraits/men/34.jpg
62431141,Lorenzo,Gomez,male,lorenzo.gomez@example.com,https://randomuser.me/api/portraits/men/81.jpg
05298880,Marco,Campos,male,marco.campos@example.com,https://randomuser.me/api/portraits/men/67.jpg
61539018,Marco,Calvo,male,marco.calvo@example.com,https://randomuser.me/api/portraits/men/86.jpg`;

const fromCSV = (csv) => {
    var fieldDelimiter = ",";
    var rowDelimiter =  "\n";
    rows = csv.split(rowDelimiter);
        
    return rows[0].map((row) => {
    	return row.split(fieldDelimiter);         
    });
};

const result = fromCSV(data);
console.log(result);
```

This is the output with my first attempt:

```
[
  [
    '15519533',
    'Raul',
    'Flores',
    'male',
    'raul.flores@example.com',
    'https://randomuser.me/api/portraits/men/42.jpg'
  ],
  [
    '82739790',
    'Alvaro',
    'Alvarez',
    'male',
    'alvaro.alvarez@example.com',
    'https://randomuser.me/api/portraits/men/48.jpg'
  },
  {
    '37206344',
    'Adrian',
    'Pastor',
    'male',
    'adrian.pastor@example.com',
    'https://randomuser.me/api/portraits/men/86.jpg'
  ],
  {
    '58054375',
    'Fatima',
    'Guerrero',
    'female',
    'fatima.guerrero@example.com',
    'https://randomuser.me/api/portraits/women/74.jpg'
  },
  {
    '35133706',
    'Raul',
    'Ruiz',
    'male',
    'raul.ruiz@example.com',
    'https://randomuser.me/api/portraits/men/78.jpg'
  ],
  {
    '79300902',
    'Nerea',
    'Santos',
    'female',
    'nerea.santos@example.com',
    'https://randomuser.me/api/portraits/women/61.jpg'
  ],
  {
    '89802965',
    'Andres',
    'Sanchez',
    'male',
    'andres.sanchez@example.com',
    'https://randomuser.me/api/portraits/men/34.jpg'
  ],
  {
    '62431141',
    'Lorenzo',
    'Gomez',
    'male',
    'lorenzo.gomez@example.com',
    'https://randomuser.me/api/portraits/men/81.jpg'
  ],
  {
    '05298880',
    'Marco',
    'Campos',
    'male',
    'marco.campos@example.com',
    'https://randomuser.me/api/portraits/men/67.jpg'
  ]
]
```

Solution
```
const data = `id,name,surname,gender,email,picture
15519533,Raul,Flores,male,raul.flores@example.com,https://randomuser.me/api/portraits/men/42.jpg
82739790,Alvaro,Alvarez,male,alvaro.alvarez@example.com,https://randomuser.me/api/portraits/men/48.jpg
37206344,Adrian,Pastor,male,adrian.pastor@example.com,https://randomuser.me/api/portraits/men/86.jpg
58054375,Fatima,Guerrero,female,fatima.guerrero@example.com,https://randomuser.me/api/portraits/women/74.jpg
35133706,Raul,Ruiz,male,raul.ruiz@example.com,https://randomuser.me/api/portraits/men/78.jpg
79300902,Nerea,Santos,female,nerea.santos@example.com,https://randomuser.me/api/portraits/women/61.jpg
89802965,Andres,Sanchez,male,andres.sanchez@example.com,https://randomuser.me/api/portraits/men/34.jpg
62431141,Lorenzo,Gomez,male,lorenzo.gomez@example.com,https://randomuser.me/api/portraits/men/81.jpg
05298880,Marco,Campos,male,marco.campos@example.com,https://randomuser.me/api/portraits/men/67.jpg
61539018,Marco,Calvo,male,marco.calvo@example.com,https://randomuser.me/api/portraits/men/86.jpg`;

const fromCSV = (csv) => {
    var fieldDelimiter = ",";
    var rowDelimiter =  "\n";
    /* The split() method splits a string into an array of substrings */
    rows = csv.split(rowDelimiter);

    /* Store the CSV column headers into separate variable */
    const headers = rows[0].split(fieldDelimiter);
    // [ 'id', 'name', 'surname', 'gender', 'email', 'picture' ]
   
    /* Store the converted result into an array */
    var output = [];

    /* Iterate over the remaning data rows */
    for (var i = 1; i < rows.length - 1; i++) {
        /* Empty object to store result in key value pair */
        const user = {}

        /* Store the current user in a array element */
        let jsonProperties = rows[i].split(fieldDelimiter);
        // [
        //     '15519533',
        //     'Raul',
        //     'Flores',
        //     'male',
        //     'raul.flores@example.com',
        //     'https://randomuser.me/api/portraits/men/42.jpg'
        // ]

        for (let j in headers) {           
			// note here we can not use dot notation (user.headers[j] = values[j]) 
			// because Javascript cannot set properties of undefined;
            user[headers[j]] = jsonProperties[j]
        }
        
        /* Push the genearted JSON object to resultant array */
        output.push(user);
     }
    return output;
};

const result = fromCSV(data);

console.log(result);
```
This is the output with my second attempt:
```
[
  {
    id: '15519533',
    name: 'Raul',
    surname: 'Flores',
    gender: 'male',
    email: 'raul.flores@example.com',
    picture: 'https://randomuser.me/api/portraits/men/42.jpg'
  },
  {
    id: '82739790',
    name: 'Alvaro',
    surname: 'Alvarez',
    gender: 'male',
    email: 'alvaro.alvarez@example.com',
    picture: 'https://randomuser.me/api/portraits/men/48.jpg'
  },
  {
    id: '37206344',
    name: 'Adrian',
    surname: 'Pastor',
    gender: 'male',
    email: 'adrian.pastor@example.com',
    picture: 'https://randomuser.me/api/portraits/men/86.jpg'
  },
  {
    id: '58054375',
    name: 'Fatima',
    surname: 'Guerrero',
    gender: 'female',
    email: 'fatima.guerrero@example.com',
    picture: 'https://randomuser.me/api/portraits/women/74.jpg'
  },
  {
    id: '35133706',
    name: 'Raul',
    surname: 'Ruiz',
    gender: 'male',
    email: 'raul.ruiz@example.com',
    picture: 'https://randomuser.me/api/portraits/men/78.jpg'
  },
  {
    id: '79300902',
    name: 'Nerea',
    surname: 'Santos',
    gender: 'female',
    email: 'nerea.santos@example.com',
    picture: 'https://randomuser.me/api/portraits/women/61.jpg'
  },
  {
    id: '89802965',
    name: 'Andres',
    surname: 'Sanchez',
    gender: 'male',
    email: 'andres.sanchez@example.com',
    picture: 'https://randomuser.me/api/portraits/men/34.jpg'
  },
  {
    id: '62431141',
    name: 'Lorenzo',
    surname: 'Gomez',
    gender: 'male',
    email: 'lorenzo.gomez@example.com',
    picture: 'https://randomuser.me/api/portraits/men/81.jpg'
  },
  {
    id: '05298880',
    name: 'Marco',
    surname: 'Campos',
    gender: 'male',
    email: 'marco.campos@example.com',
    picture: 'https://randomuser.me/api/portraits/men/67.jpg'
  }
]
```
Plus: Add a second parameter to the function for the number of attributes to add. If that parameter is not provided, each object will have all the fields.

```
const fromCSV = (csv, nAttrs) => {};

console.log(fromCSV(data)); // Cada usuario tendrá todos los atributos como la implementación original
console.log(fromCSV(data, 2)); // cada usuario tendrá sólo `id` y `name`
console.log(fromCSV(data, 3)); // cada usuario tendrá sólo `id`, `name` y `surname`
console.log(fromCSV(data, 4)); // cada usuario tendrá sólo `id`, `name`, `surname` y `gender`
```

Solution. Just use slice (start, end) on the header fields. 
The javascript slice() method returns a portion of an array into a new array object selected from start to end where start and end represent the index of items in that array. 
The original array will not be modified.

```
const data = `id,name,surname,gender,email,picture
15519533,Raul,Flores,male,raul.flores@example.com,https://randomuser.me/api/portraits/men/42.jpg
82739790,Alvaro,Alvarez,male,alvaro.alvarez@example.com,https://randomuser.me/api/portraits/men/48.jpg
37206344,Adrian,Pastor,male,adrian.pastor@example.com,https://randomuser.me/api/portraits/men/86.jpg
58054375,Fatima,Guerrero,female,fatima.guerrero@example.com,https://randomuser.me/api/portraits/women/74.jpg
35133706,Raul,Ruiz,male,raul.ruiz@example.com,https://randomuser.me/api/portraits/men/78.jpg
79300902,Nerea,Santos,female,nerea.santos@example.com,https://randomuser.me/api/portraits/women/61.jpg
89802965,Andres,Sanchez,male,andres.sanchez@example.com,https://randomuser.me/api/portraits/men/34.jpg
62431141,Lorenzo,Gomez,male,lorenzo.gomez@example.com,https://randomuser.me/api/portraits/men/81.jpg
05298880,Marco,Campos,male,marco.campos@example.com,https://randomuser.me/api/portraits/men/67.jpg
61539018,Marco,Calvo,male,marco.calvo@example.com,https://randomuser.me/api/portraits/men/86.jpg`;

const fromCSV = (csv, nAttrs) => {
    var fieldDelimiter = ",";
    var rowDelimiter =  "\n";
    /* The split() method splits a string into an array of substrings */
    rows = csv.split(rowDelimiter);

    /* Store the CSV column headers into seperate variable */
    const headers = rows[0].split(fieldDelimiter).slice(0, nAttrs);   
   
    /* Store the converted result into an array */
    var output = [];

    /* Iterate over the remaning data rows */
    for (var i = 1; i < rows.length - 1; i++) {
        /* Empty object to store result in key value pair */
        const user = {}

        /* Store the current user in a array element */
        let jsonProperties = rows[i].split(fieldDelimiter);        

        for (let j in headers) {
            // note here we can not use dot notation (user.headers[j] = values[j]) 
			// because Javascript cannot set properties of undefined;
            user[headers[j]] = jsonProperties[j]
        }
        
        /* Push the generated JSON object to resultant array */
        output.push(user);
     }
    return output;
};

const result = fromCSV(data, 2);

console.log(result);
```

```
[
  { id: '15519533', name: 'Raul' },
  { id: '82739790', name: 'Alvaro' },
  { id: '37206344', name: 'Adrian' },
  { id: '58054375', name: 'Fatima' },
  { id: '35133706', name: 'Raul' },
  { id: '79300902', name: 'Nerea' },
  { id: '89802965', name: 'Andres' },
  { id: '62431141', name: 'Lorenzo' },
  { id: '05298880', name: 'Marco' }
]
```
## Exercise 2
Implement a function replaceAt that accepts as first argument an array, as second an index and as third argument a value and replace the element in the array in the index provided. The input array must not be mutted, that means, you need to create a new array without modifying the original one. Use spread operator, and slice to get it.

```
const elements = ["lorem", "ipsum", "dolor", "sit", "amet"];
const index = 2;
const newValue = "furor";

const replaceAt = (arr, index, newElement) => {

};

const result = replaceAt(elements, index, newValue);
console.log(result === elements); // false
console.log(result); // ['lorem', 'ipsum', 'furor', 'sit', 'amet'];
```

Solution
```

```
## Exercise 3
Crea una función que reciba una colección de objetos y un año. Dicha función deberá de mostrar los nombres de las tres personas con el ranking más alto del año.

```
const data = [
  { ranking: 6.3, year: 1998, name: "Monroe", gender: "Genderfluid", id: 1450, surname: "Jerde" },
  { ranking: 5.4, year: 1999, name: "Maxie", gender: "Bigender", id: 1652, surname: "Keebler" },
  { ranking: 8.7, year: 2000, name: "Emilee", gender: "Genderqueer", id: 4779, surname: "Ritchie" },
  { ranking: 6.5, year: 2001, name: "Rudy", gender: "Bigender", id: 7105, surname: "Gusikowski" },
  { ranking: 7.1, year: 1998, name: "Randy", gender: "Genderqueer", id: 5950, surname: "Lebsack" },
  { ranking: 4.9, year: 2000, name: "Esteban", gender: "Genderqueer", id: 7987, surname: "Fritsch" },
  { ranking: 5.3, year: 2001, name: "Leonard", gender: "Male", id: 6268, surname: "Frami" },
  { ranking: 8.8, year: 2002, name: "Lang", gender: "Polygender", id: 1033, surname: "Dietrich" },
  { ranking: 9.1, year: 2000, name: "Lettie", gender: "Agender", id: 6403, surname: "Gutmann" },
  { ranking: 6.0, year: 1998, name: "Shonda", gender: "Agender", id: 1324, surname: "Borer" },
  { ranking: 7.3, year: 2003, name: "Francene", gender: "Agender", id: 6836, surname: "Blanda" },
  { ranking: 6.8, year: 2003, name: "Everett", gender: "Polygender", id: 4937, surname: "O'Keefe" },
  { ranking: 5.3, year: 1998, name: "Bernardo", gender: "Agender", id: 8148, surname: "Baumbach" },
  { ranking: 9.3, year: 2003, name: "Brianna", gender: "Female", id: 7716, surname: "Schamberger" },
  { ranking: 9.7, year: 1998, name: "Douglass", gender: "Male", id: 4152, surname: "Hilpert" },
  { ranking: 4.8, year: 1998, name: "Angel", gender: "Female", id: 355, surname: "O'Hara" },
  { ranking: 5.7, year: 2000, name: "Hugh", gender: "Male", id: 9600, surname: "Hilll" },
  { ranking: 8.5, year: 1999, name: "Graciela", gender: "Agender", id: 871, surname: "Kerluke" },
  { ranking: 2.4, year: 2000, name: "Chassidy", gender: "Agender", id: 4313, surname: "Hegmann" },
  { ranking: 3.4, year: 1999, name: "Abdul", gender: "Agender", id: 367, surname: "Weimann" },
  { ranking: 7.1, year: 2002, name: "Coleen", gender: "Non-binary", id: 1428, surname: "Feil" },
  { ranking: 8.7, year: 2001, name: "Eleanora", gender: "Genderfluid", id: 984, surname: "Barton" },
  { ranking: 9.7, year: 2002, name: "Sean", gender: "Agender", id: 5689, surname: "Runolfsson" },
  { ranking: 4.5, year: 1999, name: "Ike", gender: "Female", id: 8445, surname: "Haag" },
  { ranking: 7.7, year: 2001, name: "Rachele", gender: "Genderqueer", id: 6978, surname: "Grady" },
  { ranking: 9.1, year: 2001, name: "Sam", gender: "Bigender", id: 1321, surname: "Fritsch" },
  { ranking: 9.0, year: 2000, name: "Eddy", gender: "Polygender", id: 8273, surname: "Kemmer" },
  { ranking: 4.6, year: 1999, name: "Jamar", gender: "Female", id: 6052, surname: "Grant" },
  { ranking: 9.3, year: 2001, name: "Dino", gender: "Genderfluid", id: 5671, surname: "Erdman" },
  { ranking: 7.6, year: 1999, name: "Ervin", gender: "Non-binary", id: 9945, surname: "Powlowski" }
];

const winnerByYear = (arr, year) => {

};

console.log(winnerByYear(data, 1998)) // [ 'Douglass', 'Randy', 'Monroe' ]
console.log(winnerByYear(data, 1999)) // [ 'Graciela', 'Ervin', 'Maxie' ]
console.log(winnerByYear(data, 2000)) // [ 'Lettie', 'Eddy', 'Emilee' ]
console.log(winnerByYear(data, 2001)) // [ 'Dino', 'Sam', 'Eleanora' ]
console.log(winnerByYear(data, 2002)) // [ 'Sean', 'Lang', 'Coleen' ]
console.log(winnerByYear(data, 2003)) // [ 'Brianna', 'Francene', 'Everett' ]
console.log(winnerByYear(data, 2004)) // []
```

## Exercise 4
Crear funcion para normalizar una colección de objetos a un objeto, de tal manera que devuelva un objeto que tenga como claves las ids de los objetos y como valores los objetos en sí pero sin la id.

```
const collection = [
  {
    id: "f0b6930c-331a-43e1-80db-e6c46ed552aa",
    nationality: "Barbadians",
    language: "English",
    capital: "Belgrade",
    national_sport: "taekwondo",
    flag: "🇮🇩",
  },
  {
    id: "3e690823-fc74-4376-999a-501e5f9ae4be",
    nationality: "Congolese",
    language: "German",
    capital: "Kinshasa",
    national_sport: "wrestling",
    flag: "🇺🇾",
  },
  {
    id: "9edd87d6-2f4f-4701-8ec4-272a361dbfe9",
    nationality: "Libyans",
    language: "Tagalog",
    capital: "Jakarta",
    national_sport: "buzkashi",
    flag: "🇬🇼",
  },
  {
    id: "9873a1ed-6dc5-4034-8214-1f428c8951bd",
    nationality: "Guineans",
    language: "Hakka",
    capital: "Ankara",
    national_sport: "gymnastics",
    flag: "🇹🇷",
  },
  {
    id: "4679c4a4-4e2e-4470-a900-2445dc1f4a1e",
    nationality: "Ugandans",
    language: "German",
    capital: "Beijing",
    national_sport: "dandi biyo",
    flag: "🇮🇳",
  },
  {
    id: "4274ad62-5089-4b8e-a002-b2c1c3c74926",
    nationality: "Finns",
    language: "Swedish",
    capital: "Djibouti",
    national_sport: "bull fighting",
    flag: "🇭🇲",
  },
  {
    id: "2bb25c20-7962-47b7-82d9-d62a9493308f",
    nationality: "Poles",
    language: "Swedish",
    capital: "Beirut",
    national_sport: "cricket",
    flag: "🇰🇭",
  },
  {
    id: "9b3e09da-7484-49f3-aed0-13ccc7e77fff",
    nationality: "Guineans",
    language: "Portuguese",
    capital: "Guatemala City",
    national_sport: "cricket",
    flag: "🇩🇪",
  },
  {
    id: "903fb062-647c-46f8-857f-c1eba0cbbc9b",
    nationality: "Ivoirians",
    language: "Nepali",
    capital: "Juba",
    national_sport: "cricket",
    flag: "🇫🇮",
  },
  {
    id: "21bcd231-1d8f-49f5-826a-1dc986c52f0d",
    nationality: "Hungarians",
    language: "Russian",
    capital: "Tarawa Atoll",
    national_sport: "gymnastics",
    flag: "🇲🇴",
  },
];

const normalize = (arr) => {

};

const result = normalize(collection);
console.log(result);

```
```
// Resultado:
{
  "f0b6930c-331a-43e1-80db-e6c46ed552aa": {
    nationality: "Barbadians",
    language: "English",
    capital: "Belgrade",
    national_sport: "taekwondo",
    flag: "🇮🇩"
  },
  "3e690823-fc74-4376-999a-501e5f9ae4be": {
    nationality: "Congolese",
    language: "German",
    capital: "Kinshasa",
    national_sport: "wrestling",
    flag: "🇺🇾"
  },
  ...
}
```

Optional: Si tu solución previa utiliza bucles, crea una versión sin bucles, basándote en los métodos funcionales de Array.prototype.

## Exercise 5
Implementa una función para eliminar valores falsys de una estructura de datos. Si el argumento es un objeto, deberá eliminar sus propiedades falsys. Si el argumento es un array, deberá eliminar los elementos falsys. Si el argumento es un objeto o un array no deberán ser mutados. Siempre deberá de crear una estructura nueva. Si no es ni un objeto ni un array deberá de devolver dicho argumento.

```
const elements = [0, 1, false, 2, "", 3];

const compact = (arg) => {

};

console.log(compact(123)); // 123
console.log(compact(null)); // null
console.log(compact([0, 1, false, 2, "", 3])); // [1, 2, 3]
console.log(compact({})); // {}
console.log(compact({ price: 0, name: "cloud", altitude: NaN, taste: undefined, isAlive: false })); // {name: "cloud"}
```