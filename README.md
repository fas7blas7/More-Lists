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
2️⃣ HouseParty 🥳
Namespace: P02_HouseParty
📌 Description:
Manages a guest list based on commands like {name} is going and {name} is not going.
Prints error messages if invalid operations are attempted and finally outputs the guest list.

📝 Code:

```csharp
Copy
Edit
List<string> guestList = new List<string>();

int n = int.Parse(Console.ReadLine());

for (int i = 0; i < n; i++)
{
    string[] currentCmd = Console.ReadLine()
        .Split(' ', StringSplitOptions.RemoveEmptyEntries);
    string name = currentCmd[0];

    if (currentCmd.Length == 3)
    {
        if (guestList.Contains(name))
        {
            Console.WriteLine($"{name} is already in the list!");
            continue;
        }

        guestList.Add(name);
    }
    else if (currentCmd.Length == 4)
    {
        if (!guestList.Contains(name))
        {
            Console.WriteLine($"{name} is not in the list!");
            continue;
        }

        guestList.Remove(name);
    }
}

foreach (string name in guestList)
{
    Console.WriteLine(name);
}

```
📅 Commit Progress Update:

📅 Current Progress: 444 commits
📊 Progress Bar:
███████████████████████████████████████████▌88.8% (444/500)

📌 Milestones:
✅ 100 commits
✅ 200 commits
✅ 300 commits
✅ 400 commits
🔲 500 commits (🎉)

🎯 Commit Progress Tracker
🚀 Goal: 500 commits in 2025
