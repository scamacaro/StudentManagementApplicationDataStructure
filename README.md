# StudentManagementApplicationDataStructure
"""
Sanyerlis Camacaro - CSC235 - Sancamac@uat.edu Assignment:
Lists, indexing, dictionaries, and other common data structures.

This code demonstrates how to:
Create a new Python application, or add to your library application,
or add to your tutorial application two or more data structures from the list.
List
Dictionary
Set
Tuple
Over comment your code.

In this application, we use the following data structures:

1. List (`students`): It stores the student records. Each student record is represented as a tuple containing the name,
age, and grade.
2. Tuple (`student`): It stores the individual student record. Each tuple contains the name, age, and grade of a
student. Tuples are used to ensure that the student information remains immutable.
3.This program stores student data in a dictionary called 'students'. The dictionary uses student IDs as keys and
another dictionary as value which stores student details like name, age, and grade.
4.We also use a set called 'student_ids' to
store unique student IDs, ensuring no duplicate IDs exist in the records.

The program provides a menu-based interface where the user can add new students, search for a specific student,
display all students, remove a student, and quit the application. Each functionality utilizes the appropriate data
structures to store and manipulate the student records.
"""
# Student Management Application

# Initialize an empty dictionary to store student records
students = {}

# Initialize an empty set to store unique student IDs
student_ids = set()


# Function to add a new student record
def add_student():
    studentid = int(input("Enter unique student ID: "))
    if studentid in student_ids:
        print("This ID already exists. Please enter a unique ID.")
        return
    name = input("Enter student name: ")
    age = int(input("Enter student age: "))
    grade = input("Enter student grade: ")
    student = {'name': name, 'age': age, 'grade': grade}  # Using a dictionary to store student information
    students[studentid] = student
    student_ids.add(studentid)
    print("Student added successfully!")


# Function to search for a student record
def search_student():
    studentid = int(input("Enter student ID to search: "))
    if studentid not in student_ids:
        print("Student not found!")
        return
    student = students[studentid]
    print("Student found!")
    print("ID:", studentid)
    print("Name:", student['name'])
    print("Age:", student['age'])
    print("Grade:", student['grade'])


# Function to display all student records
def display_students():
    print("Student Records:")
    for studentid, student in students.items():
        print("ID:", studentid)
        print("Name:", student['name'])
        print("Age:", student['age'])
        print("Grade:", student['grade'])
        print("--------")


# Function to remove a student record
def remove_student():
    studentid = int(input("Enter student ID to remove: "))
    if studentid not in student_ids:
        print("Student not found!")
        return
    students.pop(studentid)
    student_ids.remove(studentid)
    print("Student removed successfully!")


# Main program loop
while True:
    print("Welcome to Student Management Application!")
    print("\nThis program allows you to manage student records in an efficient way.")
    print("\nYou can perform the following actions:\n")
    print("1. Add a Student: You can add a new student by providing a unique ID, name, age, and grade.")
    print("2. Search for a Student: You can search for an existing student using their unique ID.")
    print("3. Display All Students: You can display all the students' details stored in the program.")
    print("4. Remove a Student: You can remove a student's record from the program using their unique ID.")
    print("5. Quit: Exit the application.\n")
    print("Please note, it is important to use unique IDs for each student to ensure accurate data handling.")

    print("Select an option to proceed:")
    print("1. Add Student")
    print("2. Search Student")
    print("3. Display All Students")
    print("4. Remove Student")
    print("5. Quit")
    choice = int(input("\nEnter your choice (1-5): "))

    if choice == 1:
        add_student()
    elif choice == 2:
        search_student()
    elif choice == 3:
        display_students()
    elif choice == 4:
        remove_student()
    elif choice == 5:
        print("Thank you for using the application. Goodbye!")
        break
    else:
        print("Invalid choice. Please try again.")
