## 文档梳理

- **元祖 Tuple**: 表示一个已知元素数量和类型的数组，各元素的类型不必相同。
``` javascript
let x: [string, number];
x = ['hello', 10]; // OK
x = [10, 'hello']; // Error
```

- **类型断言**: 你在TypeScript里使用JSX时，只有 as语法断言是被允许的。

- **对象解构**: 当你展开一个对象实例时，会丢失其方法
``` javascript
class C {
  p = 12;
  m() {
  }
}
let c = new C();
let clone = { ...c };
clone.p; // ok
clone.m(); // error!
```

- **private、protected的区别**
如果其中一个类型里包含一个 private成员，那么只有当另外一个类型中也存在这样一个 private成员， 并且它们都是来自同一处声明时，我们才认为这两个类型是兼容的。
protected修饰符与 private修饰符的行为很相似，但有一点不同， protected成员在派生类的实例方法中仍然可以访问.

``` javascript
class Person {
    protected name: string;
    constructor(name: string) { this.name = name; }
}

class Employee extends Person {
    private department: string;

    constructor(name: string, department: string) {
        super(name)
        this.department = department;
    }

    public getElevatorPitch() {
        return `Hello, my name is ${this.name} and I work in ${this.department}.`;
    }
}

let howard = new Employee("Howard", "Sales");
console.log(howard.getElevatorPitch());
console.log(howard.name); // 错误
```

- **抽象类**
抽象类做为其它派生类的基类使用。 它们一般不会直接被实例化。 不同于接口，抽象类可以包含成员的实现细节。 abstract关键字是用于定义抽象类和在抽象类内部定义抽象方法。

- **泛型**

无法创建泛型枚举和泛型命名空间

类有两部分：静态部分和实例部分。 泛型类指的是实例部分的类型，所以类的静态属性不能使用这个泛型类型