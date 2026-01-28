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

**Union:**
We can use union when we use a variable for different types
Example:
<pre>
	let userId: string | number;
	userId = "UserId_123";
	userId = 42;

	function safeSquare(val : string | number) : number
	{
		if(typeof val == "string"){
			val = parseInt(val, 10);
		}
		return val * val;
	}
</pre>

**Optional Parameters:**

We can use optional parameters in a function parameter using "?" after the variable name
Example:
<pre>
	function greet(name: string, title?:string) : string
	{
		if(title){
			return 'Hello, ${title} ${name}!';
		}
		return 'Hello ${name}!';
	}
</pre>

**Optional with default Parameters:**

We can use optional with default parameters in a function parameter by specifying the default value to a parameter. No need to place a "?" after the variable name
Example:
<pre>
	function greet(name: string, title :string= "Mr.") : string
	{
			return 'Hello, ${title} ${name}!';
	}
</pre>

