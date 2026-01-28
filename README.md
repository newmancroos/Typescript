# Typescript

TypeScript Datatypes:
- number
- string
- null
- boolean
- any
- undefined
Example : 
<pre>
	const myName : string ="Newman Croos"
</pre>

**

## Function

In a function we shoulduse explicit types input parameters so that others would easily understand the function but we can user explicit return type or Inferred return types. explicit return type is a good practice.
If a function return nothing so we can use **void**  as return type
Explicit return type : 
<pre>
export function calculateTotal(
price : number 
quantity: number,
discount: number
): number{
	return (price * quantity) * (1- discount);
}
</pre>

inferred return type : 
<pre>
export function calculateTotal(
price : number,
quantity: number,
discount: number
) {
	return (price * quantity) * (1- discount);
}
</pre>

**Arrow Function :** 
<pre>
	let sub = (x:number, y:number):number =>{
		return x + y;
	}
</pre>

**Type**
<pre>
	type Character ={
			name : string;
			level : number;
	};
</pre>


