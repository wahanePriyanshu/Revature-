// Task 1- Call Stack & Event Loop

//Code flow example:

console.log("Start");

setTimeout(() => {
  console.log("Async Task");
}, 0);

console.log("End");


//Execution Order:
//Start → End → Async Task

// Explanation:

// console.log("Start") goes to Call Stack → executes immediately

// setTimeout is sent to Web APIs

// console.log("End") executes next

// After Call Stack is empty, Event Loop moves callback from Callback Queue to Call Stack

// "Async Task" executes last

//********************************************************** */

//Task 2-  Callback Queue (0ms timeout)

// Why ads load later even with 0ms?

// setTimeout(0) does not mean instant execution

// It waits until:

// Call Stack is empty

// Main content finishes loading

// Event Loop then pushes callback from Callback Queue

// Ensures non-blocking UI

// ***************************************************************************

//Task 3 - JSON.parse()

// Convert string to object & access name

const response = '{"id":101,"name":"Laptop","price":50000}';

const obj = JSON.parse(response);

console.log(obj.name); // Laptop

// *****************************************************************************************

// Task 4- JSON.stringify()

// Convert object to JSON string

const user = { username: "admin", role: "manager" };

const jsonStr = JSON.stringify(user);

localStorage.setItem("user", jsonStr);


// *************************************************************************************************

// Task 5 - Array forEach() – Welcome Message

const users = ["Priyanshu", "Rahul", "Amit"];

users.forEach(user => {
  console.log(`Welcome, ${user}`);
});

// *****************************************************************************************************

//Task 6 - Array map() – 10% Discount

const prices = [1000, 2000, 3000];

const discounted = prices.map(price => price * 0.9);

console.log(discounted);


  // return a new  array

  //*******************************************************************
  
//   Task 7-Array filter() – Available Products
const products = [
  { name: "Laptop", inStock: true },
  { name: "Mouse", inStock: false }
];

const available = products.filter(p => p.inStock === true);

console.log(available);

// ***************************************************************************************************


// Task 8- Array reduce() – Cart Total
const cart = [500, 1500, 2000];

const total = cart.reduce((sum, price) => sum + price, 0);

console.log(total);


  // Used for sum, total, aggregation

//  **********************************************************************************************


// Task 9-Function Declaration vs Arrow Function

Function Declaration
function calculateGST(price) {
  return price * 0.18;
}

Arrow Function
const calculateGST = price => price * 0.18;

// Key Difference:

Arrow functions do NOT have their own this

Function declarations do


// Task 10-Closures – Secure Counter

function counter() {
  let count = 0;

  return function () {
    count++;
    return count;
  };
}

const myCounter = counter();

console.log(myCounter()); // 1
console.log(myCounter()); // 2


//  => count cannot be accessed directly from outside

//  **********************************************************************************************************

// Task 11-. Callback Function – Login Validation

function validateUser(username, callback) {
  if (username === "admin") {
    callback("Login Successful");
  } else {
    callback("Invalid User");
  }
}

validateUser("admin", message => {
  console.log(message);
});

// Task 12-Callback Hell – Explanation

validateUser(user, () => {
  processPayment(() => {
    generateInvoice(() => {
      sendEmail();
    });
  });
});

//  Problems:

Hard to read

Difficult debugging

Poor error handling

 Solved using Promises / async-await

//  *****************************************************************************************


// Task 13-Promises → async/await

Before:
fetch(url)
  .then(res => res.json())
  .then(data => console.log(data));

After:
async function getData() {
  const res = await fetch(url);
  const data = await res.json();
  console.log(data);
}

getData();


 Cleaner & readable

//  ********************************************************************************************************

// Task 14-DOM Manipulation – Add <li> Dynamically

Methods used:

document.createElement()

appendChild()

querySelector()

const ul = document.querySelector("ul");
const li = document.createElement("li");

li.textContent = "New Item";
ul.appendChild(li);

// ******************************************************************************************************

// Task 15-Event Listeners – Form Validation
form.addEventListener("submit", function (e) {
  e.preventDefault();

  if (input.value === "") {
    error.textContent = "Field is required";
  }
});
