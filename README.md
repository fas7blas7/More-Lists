1️⃣ ListManipulator 🧮  
Namespace: _01.ListManipulator  
📌 Description:  
Reads a list of integers and processes commands:  
- `Delete X`: removes all occurrences of `X`  
- `Insert X Y`: inserts `X` at index `Y`  
Ends with the command `"end"` and prints the final list.

📝 Code:

```csharp
List<int> numbers = Console.ReadLine().Split().Select(int.Parse).ToList();

string input = Console.ReadLine();

while (input != "end")
{
    string[] comandParts = input.Split();
    string commandName = comandParts[0];

    if (commandName == "Delete")
    {
        int elementForDelete = int.Parse(comandParts[1]);
        numbers.RemoveAll(e => e == elementForDelete);
    }
    else if (commandName == "Insert")
    {
        int elementToInsert = int.Parse(comandParts[1]);
        int positionToInsert = int.Parse(comandParts[2]);

        numbers.Insert(positionToInsert, elementToInsert);
    }

    input = Console.ReadLine();
}

Console.WriteLine(string.Join(" ", numbers));

```
📅 Commit Progress Update:

📅 Current Progress: 442 commits  
📊 Progress Bar:  
██████████████████████████████████████████▍88.4% (442/500)

📌 Milestones:  
✅ 100 commits  
✅ 200 commits  
✅ 300 commits  
✅ 400 commits  
🔲 500 commits (🎉)

🎯 Commit Progress Tracker  
🚀 Goal: 500 commits in 2025
