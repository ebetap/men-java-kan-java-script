Untuk mengimplementasikan konsep Object-Oriented Programming (OOP) dengan adab maksimal di JavaScript ES2024, kita harus memperhatikan prinsip-prinsip seperti enkapsulasi, pewarisan, polimorfisme, dan abstraksi. Selain itu, kita harus menggunakan fitur-fitur terbaru yang diperkenalkan di ES2024 untuk memastikan kode yang kita tulis modern, efisien, dan mudah dibaca.

Berikut adalah contoh implementasi OOP di JavaScript ES2024:

### 1. Enkapsulasi
Enkapsulasi dilakukan dengan menggunakan properti privat dan getter/setter untuk mengontrol akses ke data.

```javascript
class Person {
    #name;
    #age;

    constructor(name, age) {
        this.#name = name;
        this.#age = age;
    }

    get name() {
        return this.#name;
    }

    set name(name) {
        if (name) {
            this.#name = name;
        } else {
            throw new Error("Name cannot be empty");
        }
    }

    get age() {
        return this.#age;
    }

    set age(age) {
        if (age > 0) {
            this.#age = age;
        } else {
            throw new Error("Age must be a positive number");
        }
    }

    introduce() {
        console.log(`Hi, my name is ${this.#name} and I am ${this.#age} years old.`);
    }
}

const person = new Person("John Doe", 30);
person.introduce(); // Output: Hi, my name is John Doe and I am 30 years old.
person.name = "Jane Doe";
person.introduce(); // Output: Hi, my name is Jane Doe and I am 30 years old.
```

### 2. Pewarisan
Pewarisan digunakan untuk menciptakan hierarki kelas dan berbagi fungsionalitas antara kelas-kelas.

```javascript
class Employee extends Person {
    #position;

    constructor(name, age, position) {
        super(name, age);
        this.#position = position;
    }

    get position() {
        return this.#position;
    }

    set position(position) {
        if (position) {
            this.#position = position;
        } else {
            throw new Error("Position cannot be empty");
        }
    }

    introduce() {
        console.log(`Hi, my name is ${this.name}, I am ${this.age} years old, and I work as a ${this.#position}.`);
    }
}

const employee = new Employee("Alice Smith", 28, "Software Engineer");
employee.introduce(); // Output: Hi, my name is Alice Smith, I am 28 years old, and I work as a Software Engineer.
```

### 3. Polimorfisme
Polimorfisme dicapai melalui metode overriding, di mana metode di kelas turunan dapat memiliki perilaku yang berbeda dari metode di kelas induk.

```javascript
class Manager extends Employee {
    #teamSize;

    constructor(name, age, position, teamSize) {
        super(name, age, position);
        this.#teamSize = teamSize;
    }

    get teamSize() {
        return this.#teamSize;
    }

    set teamSize(teamSize) {
        if (teamSize >= 0) {
            this.#teamSize = teamSize;
        } else {
            throw new Error("Team size must be a non-negative number");
        }
    }

    introduce() {
        console.log(`Hi, my name is ${this.name}, I am ${this.age} years old, and I manage a team of ${this.#teamSize} people.`);
    }
}

const manager = new Manager("Bob Johnson", 40, "Engineering Manager", 10);
manager.introduce(); // Output: Hi, my name is Bob Johnson, I am 40 years old, and I manage a team of 10 people.
```

### 4. Abstraksi
Abstraksi dilakukan dengan menggunakan kelas abstrak dan metode abstrak yang harus diimplementasikan oleh kelas turunan.

```javascript
class Vehicle {
    constructor(make, model) {
        if (new.target === Vehicle) {
            throw new Error("Cannot instantiate an abstract class");
        }
        this.make = make;
        this.model = model;
    }

    start() {
        throw new Error("Abstract method 'start' must be implemented");
    }

    stop() {
        throw new Error("Abstract method 'stop' must be implemented");
    }

    info() {
        return `${this.make} ${this.model}`;
    }
}

class Car extends Vehicle {
    start() {
        console.log(`The car ${this.info()} is starting.`);
    }

    stop() {
        console.log(`The car ${this.info()} is stopping.`);
    }
}

const car = new Car("Toyota", "Corolla");
car.start(); // Output: The car Toyota Corolla is starting.
car.stop(); // Output: The car Toyota Corolla is stopping.
```

Dalam contoh di atas, kita telah mengimplementasikan empat pilar utama OOP dengan fitur-fitur modern yang disediakan oleh JavaScript ES2024, seperti properti privat, getter/setter, dan penggunaan kelas abstrak. Pendekatan ini memastikan bahwa kode kita tetap terstruktur, dapat diperluas, dan mudah dipelihara.
