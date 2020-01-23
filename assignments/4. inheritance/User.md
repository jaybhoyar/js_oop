# Inheritance

## User

### -properties

-name
-score

### -methods

-increaseScore: returns score increased by 1
-decreaseScore: returns score decreased by 1

## PaidUser

### -properties

-name
-score
-balance

### -methods

-increaseScore: returns score increased by 1
-decreaseScore: returns score decreased by 1

Using Inheritance convert the above into following patterns.

1. Prototypal Pattern
2. Pseudoclassical Pattern
3. Classes

```js
1. Prototypal Pattern

let userMethods  = {
  increaseScore(){
    this.score += 1;
    return this.score;
  },
  decreaseScore(){
    this.score -= 1;
    return this.score;
  }
}
function createUser(name, score = 0) {
  let obj = {};
  obj.__proto__ = userMethods;
  obj.name = name;
  obj.score = score;
  return obj;
}
let paidUserMethods = {
  incrementBalance() {
    this.balance += 1
    return this.balance
  },
  decrementBalance() {
    this.balance -= 1
    return this.balance
  }
}
function createPaidUser(name, score = 0, balance = 0) {
  let obj = createUser(name, score);
  Object.setPrototypeOf(obj, paidUserMethods);
  Object.setPrototypeOf(paidUserMethods, userMethods);
  obj.balance = balance;
  return obj;
}
let sam = createPaidUser('Sam', 25);
console.group("User");
console.log("Name:", sam.name);
console.log("Score:",sam.score);
console.log("Increase:",sam.increaseScore());
console.log("Decrease:",sam.decreaseScore());
console.groupEnd();


// 3. Classes
  class createUser {
    constructor(name, score){
      this.name  = name;
      this.score  = score;
    }
    increaseScore(){
      this.score += 1;
      return score;
    }
    decreaseScore(){
      this.score -= 1;
      return score;
    }
  }
  class PaidUser extends User {
    constructor(name, score){
      super(name, score);
    }
    incrementBalance() {
      this.balance += 1;
      return this.balance;
    }
    decrementBalance() {
      this.balance -= 1;
      return this.balance;
   }
  }
  let mike = createPaidUser('Mike', 27, 100);
  console.group("Paid User");
  console.log("Name:", mike.name);
  console.log("Score:",mike.score);
  console.log("Balance:",mike.balance);
  console.log("Increase:",mike.increaseScore());
  console.log("Decrease:",mike.decreaseScore());
  console.log("Increase Balance:",mike.incrementBalance());
  console.log("Decrease Balance:",mike.decrementBalance());
  console.groupEnd();

```
