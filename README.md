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
3️⃣ ListOperations 🛠️  
Namespace: P03_ListOperations  
📌 Description:  
Reads a list of integers and processes a series of commands:  
- `Add X` – adds `X` to the end of the list  
- `Insert X Y` – inserts `X` at index `Y`, validates index  
- `Remove X` – removes element at index `X`, validates index  
- `Shift left X` / `Shift right X` – rotates the list `X` times  
Ends with `"End"` and prints the final list state.

📝 Code:

```csharp
namespace P03_ListOperations
{
    internal class Program
    {
        static void Main(string[] args)
        {
            List<int> numbers = Console.ReadLine()
                .Split(' ', StringSplitOptions.RemoveEmptyEntries)
                .Select(int.Parse)
                .ToList();

            string currentCmd = Console.ReadLine();
            while (currentCmd != "End")
            {
                string[] cmdArgs = currentCmd
                    .Split(' ', StringSplitOptions.RemoveEmptyEntries);

                string cmdType = cmdArgs[0];
                if (cmdType == "Add")
                {
                    int numberToAdd = int.Parse(cmdArgs[1]);
                    numbers.Add(numberToAdd);
                }
                else if (cmdType == "Insert")
                {
                    int numberToInsert = int.Parse(cmdArgs[1]);
                    int index = int.Parse(cmdArgs[2]);

                    bool isSuccess = InsertNumber(numbers, numberToInsert, index);
                    if (!isSuccess)
                    {
                        Console.WriteLine("Invalid index");
                    }
                }
                else if (cmdType == "Remove")
                {
                    int removeIndex = int.Parse(cmdArgs[1]);

                    bool isSuccess = RemoveNumber(numbers, removeIndex);
                    if (!isSuccess)
                    {
                        Console.WriteLine("Invalid index");
                    }
                }
                else if (cmdType == "Shift")
                {
                    string shiftDirection = cmdArgs[1];
                    int shiftsCount = int.Parse(cmdArgs[2]);

                    ShiftNumbers(numbers, shiftDirection, shiftsCount);
                }

                currentCmd = Console.ReadLine();
            }

            Console.WriteLine(string.Join(' ', numbers));
        }

        static void ShiftNumbers(List<int> numbers, string direction, int count)
        {
            if (numbers.Count > 1)
            {
                count = count % numbers.Count;

                for (int i = 0; i < count; i++)
                {
                    if (direction == "left")
                    {
                        int firstElement = numbers[0];
                        numbers.RemoveAt(0);
                        numbers.Add(firstElement);
                    }
                    else if (direction == "right")
                    {
                        int lastElement = numbers[^1];
                        numbers.RemoveAt(numbers.Count - 1);
                        numbers.Insert(0, lastElement);
                    }
                }
            }
        }

        static bool RemoveNumber(List<int> numbers, int index)
        {
            if (IsIndexValid(numbers, index))
            {
                numbers.RemoveAt(index);
                return true;
            }
            return false;
        }

        static bool InsertNumber(List<int> numbers, int number, int index)
        {
            if (IsIndexValid(numbers, index))
            {
                numbers.Insert(index, number);
                return true;
            }
            return false;
        }

        static bool IsIndexValid(List<int> numbers, int index)
        {
            return index >= 0 && index < numbers.Count;
        }
    }
}

```
4️⃣ ListEditor ✏️
Namespace: P04_ListEditor
📌 Description:
Reads a list of integers and processes commands dynamically:

Add X – adds X to the end of the list

Remove X – removes the first occurrence of X

RemoveAt X – removes the element at index X

Insert X Y – inserts X at index Y
Ends with "end" and prints the final list state.

📝 Code:

```csharp

List<int> numbers = Console.ReadLine().Split().Select(int.Parse).ToList();

string command = Console.ReadLine();

while (command != "end")
{
    string[] commandParts = command.Split(" ");
    string commandName = commandParts[0];

    switch (commandName)
    {
        case "Add":
            int numberToAdd = int.Parse(commandParts[1]);
            numbers.Add(numberToAdd);
            break;
        case "Remove":
            int numberToRemove = int.Parse(commandParts[1]);
            numbers.Remove(numberToRemove);
            break;
        case "RemoveAt":
            int positionForRemove = int.Parse(commandParts[1]);
            numbers.RemoveAt(positionForRemove);
            break;
        case "Insert":
            int numberToInsert = int.Parse(commandParts[1]);
            int positionToInsert = int.Parse(commandParts[2]);
            numbers.Insert(positionToInsert, numberToInsert);
            break;
    }

    command = Console.ReadLine();
}

Console.WriteLine(string.Join(" ", numbers));

```
5️⃣ BombNumbers 💣
Namespace: P05_BombNumbers
📌 Description:
Reads a list of integers and a bomb specification (bombNumber and bombPower). For each occurrence of bombNumber, removes it along with bombPower numbers to its left and right (with boundary checks). Finally, prints the sum of the remaining numbers.

📝 Code:

```csharp

namespace P05_BombNumbers
{
    internal class Program
    {
        static void Main(string[] args)
        {
            List<int> numbers = Console.ReadLine()
                .Split(' ', StringSplitOptions.RemoveEmptyEntries)
                .Select(int.Parse)
                .ToList();
            int[] bombArgs = Console.ReadLine()
                .Split(' ', StringSplitOptions.RemoveEmptyEntries)
                .Select(int.Parse)
                .ToArray();

            int bombNumber = bombArgs[0];
            int bombPower = bombArgs[1];
            if (bombPower < 0)
            {
                bombPower *= -1;
            }

            while (numbers.Contains(bombNumber))
            {
                int indexOfBomb = numbers.IndexOf(bombNumber);
                int leftIndex = indexOfBomb - bombPower;
                if (leftIndex < 0)
                {
                    leftIndex = 0;
                }

                int rightIndex = indexOfBomb + bombPower;
                if (rightIndex >= numbers.Count)
                {
                    rightIndex = numbers.Count - 1;
                }

                int elementsToRemove = rightIndex - leftIndex + 1;
                for (int i = 0; i < elementsToRemove; i++)
                {
                    numbers.RemoveAt(leftIndex);
                }
            }

            long numbersSum = SumNumbers(numbers);
            Console.WriteLine(numbersSum);
        }

        static long SumNumbers(List<int> numbers)
        {
            long sum = 0L;
            foreach (int number in numbers)
            {
                sum += number;
            }

            return sum;
        }
    }
}

```
📅 Commit Progress Update:

📅 Current Progress: 450 commits
📊 Progress Bar:
███████████████████████████████████████████████░90.0% (450/500)

📌 Milestones:
✅ 100 commits
✅ 200 commits
✅ 300 commits
✅ 400 commits
🔲 500 commits (🎉)

🎯 Commit Progress Tracker
🚀 Goal: 500 commits in 2025
