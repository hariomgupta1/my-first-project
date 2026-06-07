import json

FILE_NAME = "students.json"

def load_students():
    try:
        with open(FILE_NAME, "r") as file:
            return json.load(file)
    except:
        return []

def save_students(students):
    with open(FILE_NAME, "w") as file:
        json.dump(students, file, indent=4)

def add_student():
    students = load_students()

    roll = input("Enter Roll No: ")
    name = input("Enter Name: ")
    course = input("Enter Course: ")

    students.append({
        "roll": roll,
        "name": name,
        "course": course
    })

    save_students(students)
    print("Student Added Successfully!")

def view_students():
    students = load_students()

    if not students:
        print("No Students Found!")
        return

    print("\nStudent List")
    print("-" * 30)

    for student in students:
        print(f"Roll No: {student['roll']}")
        print(f"Name: {student['name']}")
        print(f"Course: {student['course']}")
        print("-" * 30)

def delete_student():
    students = load_students()

    roll = input("Enter Roll No to Delete: ")

    students = [s for s in students if s["roll"] != roll]

    save_students(students)
    print("Student Deleted Successfully!")

while True:
    print("\n===== Student Management System =====")
    print("1. Add Student")
    print("2. View Students")
    print("3. Delete Student")
    print("4. Exit")

    choice = input("Enter Choice: ")

    if choice == "1":
        add_student()
    elif choice == "2":
        view_students()
    elif choice == "3":
        delete_student()
    elif choice == "4":
        print("Thank You!")
        break
    else:
        print("Invalid Choice!")# my-first-project
 my first project
