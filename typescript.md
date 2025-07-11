***const addInvoice = async (invoice: Omit<Invoice, "id">) => ***

(invoice: Omit<Invoice, "id">)
This is the function parameter:

The function takes one argument called invoice.

The type of invoice is Omit<Invoice, "id">.

What is Omit<Invoice, "id">?
This is a TypeScript utility type that constructs a new type by:

Taking the Invoice type.

Removing the "id" property from it.

🔸 So this function expects an object that has all properties of Invoice except id.

If your Invoice type is like:

ts
Copy
Edit
type Invoice = {
  id: string;
  customerName: string;
  amount: number;
  date: string;
};
Then Omit<Invoice, "id"> becomes:

ts
Copy
Edit
{
  customerName: string;
  amount: number;
  date: string;
}
***some supabase concepts***

const { data: newTask, error } = await supabase
  .from('tasks')
  .insert(taskData)
  .select()
  .single();

   =>
   
   .select()
After inserting, this tells Supabase:
👉 "Return the inserted row(s)."

By default, .insert() returns nothing unless you use .select().

.insert(taskData)
This inserts data into the table.

taskData should be an object (or array of objects) representing the row(s) you want to insert.


.single()
This tells Supabase:
👉 "We are expecting only one row as a result."

It will:

Return a single object instead of an array.

Throw an error if more than one row is returned.



const { data: newTask, error } = await supabase
  .from('tasks')
  .insert([taskData])
  .select();


  With [taskData] and .select():
You will get an array of inserted rows (even if it's just one).

newTask will look like this:

ts
Copy
Edit
[
  {
    id: 1,
    title: "Do something",
    completed: false,
    created_at: "2025-07-07T09:00:00Z",
  }
]


*** What is Partial<Company>? ****


Partial<T> is a TypeScript utility type that makes all properties of a type optional.

So if you have:

ts
Copy
Edit
type Company = {
  id: string;
  name: string;
  address: string;
  website: string;
};
Then:

ts
Copy
Edit
Partial<Company>
is equivalent to:

ts
Copy
Edit
{
  id?: string;
  name?: string;
  address?: string;
  website?: string;
}
🔸 Every field is now optional — you can provide just some of them.


***Zod is a TypeScript-first schema declaration and validation library. It helps you define the shape of data and then validate that data at runtime***

const addressSchema = z.object({
  address: z.string().optional(),
  city: z.string().optional(),
  state: z.string().optional(),
  postalCode: z.string().optional(),
  country: z.string().optional(),
});

This defines a schema for an address object where each field is a string and optional.
Type inference in TypeScript

type Address = z.infer<typeof addressSchema>;

# Why use Zod?
Built-in TypeScript type inference

Clear and declarative schema syntax

Runtime validation + compile-time types

Useful for form validation, API payload validation, etc.


#### what is runtime and compile time


1. Compile Time
Definition:
Compile time is when the code is being translated from a high-level language (like TypeScript) into a lower-level language (like JavaScript).

🔍 Happens when:
You run tsc (TypeScript compiler).

You're building your project.

Before the program actually starts running.

✅ At compile time:
Type checking happens (e.g., if a variable is a string or number).

Syntax errors are caught.

Code is transpiled (in TypeScript).

💡 Example (TypeScript):

let age: number = "25";  // ❌ Compile-time error: "25" is a string, not a number


2. Runtime
Definition:
Runtime is when the code is actually running in an environment (like a browser or Node.js).

🔍 Happens when:
The user opens your website.

You run node index.js.

After the code has been compiled (if needed).

✅ At runtime:
Logic errors happen (e.g., divide by zero).

Unexpected inputs can cause crashes.

You use tools like Zod, try/catch, or console.log to handle errors.

💡 Example (JavaScript):

const age = JSON.parse("not a number");  // ❌ Runtime error: Unexpected token




