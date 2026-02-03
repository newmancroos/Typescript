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

Type can also be used as eNum

Example:
<pre>
	export type Priority = "Low" | "Medium" | "High" | "Critical"
	export function setPriority(level : Priority)
	{
		switch(level){
			case "Low":
				return 0;
			case "Medium":
				return 1;
			case "High":
				return 2;
			case "Critical" :
				return 3:
			case default:
				return -1;
		}
	}
</pre>

We can use **type**  to create another type with some modification on all element of the type 

Example:
<pre>
	type Class = "wizard" | "warrior" | "rogu";
	type Hero = 'elf ${Class}';
//Output is Type Hero =  "elf wizard" | "elf warrior" | "elfrogu";    //Loopthrough all element add the prefix
</pre>
same way we can combine multiple types 
Example:
<pre>
		type Class = "wizard" | "warrior" | "rogu";
		type Race = "elf" | "huma" | "dwarf";
		type Hero = 'Hero: ${Race} ${Class};
		//Output : Hero: elf wizard | Hero: elf warrior | Hero: elf orgu | Hero: human wizard | Hero: human warrior| ...
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


## Array

by adding [] to the end of the datatype we can make a variable array
Example:
<pre>
	let myNames : string[];
	let objects : (string | number)[];
export function averageScore(ratings: (string | number)[]) {
	if(ratings.length == 0) return 0;
	return ratngs.reduce(rating,sum) => {
		return rating * sum
	},0)/ rating.length;
} 
//We can also using Array keyword
function assignLightsaberColor(name : string, colors: Array<string>) : void{

}
</pre>


**Rest Parameters:**

If we want to pass n number of paramter we can use it
Example:
<pre>
	function gatherParty (partyname:string, ...adventure:string[]) : string{
		let msg = '${parttyName} consist of : ${adventure.join(", ")'};
		console.log(msg);
	}
</pre>

## Object Literal Types:

In Type script object declare as type as follows
<pre>
	export type Mail = {
		firstName: string,
		lastName: string,
		middleName?: string   //Optional property
	}
</pre>


**Discriminated Union :**

	<pre>
		type MultipleChoiceLession = {
			kind: "multiple-choice",  //Discriminant property
			question: string,
			studentAnswer: sytring,
			correctAnswer: string
		}

		type CodingLession = {
			kind: "coding", //Discriminant property
			question: string,
			studentCode: sytring,
			solutionCode: string
		}

		type lesson = MultipleChoiceLession  | CodingLession;
		function iscorrect(lesson:Lesson){
			switch (lesson.kind){
				case "multiple-choice":
					return lesson.studentAnswer === lesson.correctAnswer;
				case "coding":
					return lesson.studentCode === lession.solutionCode;
			}
		}
	</pre>
	
## Sets:
It is equivalent to HashSet, It will always have unique values/element.
<pre>
	const set =new Set<string>()
	set.add("Newman");
	set.add("Nithin");
	set.add("Newman");
	// second Newman will be removed
</pre>

<pre>
		export function findNumUniqueLabels(formattedAddresses : string[]) : number
		{
			const set = new Set(formattedAddresses );
			return set.size;  //any duplicate values will be removed and unique values will be return
										// also Set has size not length
		}
</pre>


## Map:

Map is dictionary type, it accespt Key value paire

<pre>
		const map = new Map<string, number>();
		map.set("Newman", 1);
		map.set("Nithin", 2);
		var empId = map.get("Newman");  //get a element from Map using its key 
</pre>

## Dynamic Key:

Sometimes, you won't know all of an object's property names in advance. For example, say you'r building a customer management system where employees can add custome Key/Valye paires to the customer recodes, like 
 * favoriteColoe : "Blues"
 * favoriteFood : "Pizza"
you can't know what the user will add ahead of time, you still want to model the data in your program.

Syntax :
<pre>
	type UserMetrices = {
		[key : string] : number;
		//here We need to give a key as string and value as number
	}
</pre>

Example1:
<pre>
	//export type MailPreferences = {
	//			[key : string] : number
	//		};
	export type MailPreferences = Record&lt;string, number&gt;;
	
	//Both declaration are valid 
		const a: MailPreferences = {
			Normal : 0,
			Express: 1,
			SuperExpress : 2
		};
	
		console.log(a["Normal"]); // 0
</pre>

Example2:
<pre>
interface Dictionary&lt;T&gt; {
  [key: string]: T; // The key can be any string, and the value will be of type T
}
const userScores: Dictionary<number> = {
  alice: 100,
  bob: 120,
  carol: 90,
};

// Accessing and assigning dynamic keys using bracket notation
const userName: string = "dave";
userScores[userName] = 80; // Valid assignment
console.log(userScores["alice"]); // Output: 100
</pre>

