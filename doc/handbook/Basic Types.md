### 基本类型
```ts
boolean // 布尔值

number  // 数字 (所有数字都是浮点数,支持十进制、十六进制、二进制及八进制字面量)

string  // 字符串

number[] // 数组 (可以在元素类型后面接上`[]`，表示由此类型元素组成的一个数组)

Array<number> // 数组 (数组泛型，`Array<元素类型>`)

object  // 对象

undefined & null // undefined & null （默认情况下是所有类型的子类型，指定--strictNullChecks标记，null和undefined只能赋值给void和它们各自）

[string, number] // 元组 (表示一个已知元素数量和类型的数组，各元素的类型不必相同)

enum    // 枚举 ？

any     // 任意值 （any类型允许你在编译时可选择地包含或移除类型检查。）

void    // 空值 （声明`void`类型的变量只可以赋予`undefined`和`null`）

never   // never类型表示的是那些永不存在的值的类型。never是任何类型的子类型，也可以赋值给任何类型，但没有类型可以给never类型的变量赋值。
```
### 类型应用(大部分类型通用公式： 变量名: 类型)
```ts
let isNice: boolean = true;

let age: number = 6;

let name: string = "mhw";

let list1: number[] = [1, 2, 3];

let list2: Array<number> = [1, 2, 3];

let x: [string, number];

enum Color {Red = 1, Green, Blue}
let colorName: string = Color[2];

let notSure: any = 4;

function warnUser(): void {
    console.log("This is my warning message");
}
let unusable: void = undefined;

let u: undefined = undefined;
let n: null = null;

function error(message: string): never {
    throw new Error(message);
}
function infiniteLoop(): never {
    while (true) {
    }
}

declare function create(o: object | null): void;
create({ prop: 0 }); // OK
create(null); // OK

let all: string | null | undefined = '2'

let student:(x:string,y:number)=>string = function(name:string,age:number):string{
    return `我是${name},今年${age}岁`;
}
```
### 类型断言

有时候你会遇到这样的情况，你会比TypeScript更了解某个值的详细信息。
通常这会发生在你清楚地知道一个实体具有比它现有类型更确切的类型。

通过*类型断言*这种方式可以告诉编译器，“相信我，我知道自己在干什么”。
类型断言好比其它语言里的类型转换，但是不进行特殊的数据检查和解构。
它没有运行时的影响，只是在编译阶段起作用。
TypeScript会假设你，程序员，已经进行了必须的检查。

类型断言有两种形式。
其一是“尖括号”语法：

```ts
let someValue: any = "this is a string";

let strLength: number = (<string>someValue).length;
```

另一个为`as`语法：

```ts
let someValue: any = "this is a string";

let strLength: number = (someValue as string).length;
```

两种形式是等价的。在TypeScript里使用JSX时，只有`as`语法断言是被允许的。
