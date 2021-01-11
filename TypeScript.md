# Basic Type

```typescript
let isDone: boolean = false;
```

## Array

```typescript
let list: number[] = [1, 2, 3];
let list: Array<number> = [1, 2, 3];
```

## Tuple

```typescript
let x: [string, number];
```

Order must be correct.

## Enum

```typescript
enum Color {
  Red,
  Green,
  Blue,
}
let c: Color = Color.Green;
console.log(c)//1
console.log(Color[2])//Blue
```

Default value is 0, next is the previous one plus one.

## Unknown

```typescript
const maybe: unknown;
const aNumber: number= maybe;//Error cant assign unknow to number
if (maybe===true){
    const bool:bolean = maybe;//Ok,TS know maybe is bool
    const aString: string = maybe;//Error cant assign bool to string
}
```

Describe type that we don't know yet(user input, API call). Must be narrowed down with `typeof`, comparison or type guard.

## Other

Any: No type checking

Void: not having type

Null, undefined: //TODO

Never: Type of value never occur ( always throw error function)

Object: //TODO

## Type assertion

```typescript
let strLength: number = (someValue as string).length;
let strLength: number = (<string>someValue).length;
```

# Interface

## Object

Duck typing/ structural subtyping

No order, don't care if more properties

```typescript
interface Shape{
    name: string;
    color?: string;//Optional property
    readonly id: number;
    [propName: string]: any;// string index signature
}
```

Object literal get excess property check. Can be bypassed with type assertion.

## Function

```typescript
interface SearchFunc{
    (source:string,subString:string): boolean;
}
```

## Indexable type

```typescript
interface StringArray {
    [index:number]:string;
}
```

## Class type

```typescript
interface ClockInterface {
  currentTime: Date;
  setTime(d: Date): void;
}

class Clock implements ClockInterface {
  currentTime: Date = new Date();
  setTime(d: Date) {
    this.currentTime = d;
  }
  constructor(h: number, m: number) {}
}
//Extend is combine
interface AlarmClockInterface extends ClockInterface{
    alarmTime:Date;
    alarm():void;
}
//Hybrid: both function and object
interface Counter{
    (tickSound:string):void;
    current:number;
}
```

Interface only describe public properties and methods.

# Function

```typescript
function isEqual(x:number,y:number):boolean{
  return x==y
}
const isEqual2: (x:number,y:number)=>boolean = function (a,b){
  return a==b
}
const isEqual3= (x:number,y:number):boolean=>{
  return x==y
}
function buildName(firstName: string, ...restOfName: string[]) {
  return firstName + " " + restOfName.join(" ");
}
//Overloading
function add(x:number,y:number):number;
function add(x:string,y:string):string;
function add(x:any,y:any):any{
  if (typeof x==="number"){
    return x+y
  }
  if (typeof x=== "string"){
    return x+y;
  }
}
```

Can have optional and default. Can infer return type. Can type this argument.

# Literal 

Enforce exact value which string, number or Boolean must have

```typescript
type Dice = 1|2|3|4|5|6;
function rollDice():Dice{
//return only number literal from 1 to 6
}
function getAnswer():"yes"|"no"{
	return isAccepted()?"yes":"no"
}
```

# Union and Intersection

```typescript
function multiply(x:number|string,y:number):string|number{
 if (typeof x==="number"){
     return x*y;
 }
 else{
     let s="";
     for (let i=0;i<y;i++){
         s+=x;
     }
     return s;
 }
}
```

Can only access common member of union. Use single field with literal type to discriminate union, must provide exhaustive type narrow. Intersection (& operator) to combine multi type.

# Class

```typescript

```

