# Produlist-Productivity-List-
Produlist (Productivity + List) is a minimalist command-line task manager built for focus and simplicity. Whether you're managing personal goals or work-related tasks, Produlist helps you stay organized without distractions. No complex setup. Just launch, list, and get things done.

def load_tasks(filename="tasks.txt"):
    try:
        with open(filename, "r") as f:
            return [line.strip() for line in f.readlines()]
    except FileNotFoundError:
        return []

def save_tasks(tasks, filename="tasks.txt"):
    with open(filename, "w") as f:
        for task in tasks:
            f.write(task + "\n")

def main():
    tasks = load_tasks()
    while True:
        print("\nTo-Do List:")
        for i, task in enumerate(tasks, 1):
            print(f"{i}. {task}")
        print("\nOptions: [a]dd, [d]elete, [q]uit")
        choice = input("Choose an option: ").lower()

        if choice == 'a':
            task = input("Enter new task: ")
            tasks.append(task)
        elif choice == 'd':
            try:
                num = int(input("Enter task number to delete: "))
                tasks.pop(num - 1)
            except (ValueError, IndexError):
                print("Invalid number.")
        elif choice == 'q':
            break
        else:
            print("Invalid choice.")
    
    save_tasks(tasks)

if __name__ == "__main__":
    main()
