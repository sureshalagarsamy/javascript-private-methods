# Drawback of creating private methods in JavaScript

One of the drawbacks of creating true private methods in JavaScript is that they are very ```memory-inefficient```, as a new copy of the method would be created for each instance.

```javascript
var Employee = function (name, company, salary) {
    this.name = name || "";       //Public attribute default value is null
    this.company = company || ""; //Public attribute default value is null
    this.salary = salary || 5000; //Public attribute default value is null

    // Private method
    var increaseSalary = function () {
        this.salary = this.salary + 1000;
    };

    // Public method
    this.displayIncreasedSalary = function() {
        increaseSalary();
        console.log(this.salary);
    };
};

// Create Employee class object
var emp1 = new Employee("ABC","Company-1",1000);
console.log(emp1);

// Create Employee class object
var emp2 = new Employee("XYZ","Company-2",2000);
console.log(emp2);

// Create Employee class object
var emp3 = new Employee("SURESH","Company-3",3000);
console.log(emp3);
```

Here each instance variable ```emp1```, ```emp2```, ```emp3``` has its own copy of the ```increaseSalary``` private method.

So, as a recommendation, don’t use private methods unless it’s necessary.
