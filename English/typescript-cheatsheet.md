# TypeScript Cheatsheet
A typed languaje can help reduce a lot of bugs.

It is important to follow TypeScript languaje style:
[Google TypeScript Style Guide](https://google.github.io/styleguide/tsguide.html)
## Valiables
Setting the type to a variable:
``` ts
 const username: string = 'guest';
```
Setting two types to a varible:
``` ts
 const username: string | number = 123;
```
Typed function's parameter and return value:
``` ts
function getNumberEmployees (company: string) :number {
    //...
}
```
Class declaration:
``` ts
class Employee {
    public name: string;
    private age: number;

    constructor(public name: string){
        //It asigns to the property automatically.
    }

    seAge (age: number){
        this.age = age;
    }
}
```

Object instance:
``` ts
const albert = new Employee("albert");
```

Using an object's method:
``` ts
albert.setAge(22);
```