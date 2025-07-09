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

