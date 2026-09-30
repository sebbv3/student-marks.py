# Advanced Python Programming Assignment
# Student Marks Analyzer

subjects = [
    "Python",
    "Cloud Computing",
    "Networking",
    "Database",
    "DevOps"
]

# Counters for the class summary
a_students = 0
b_students = 0
c_students = 0
d_students = 0
failed_students = 0


# Ask how many students
num_students = int(input("How many students? "))


# Process each student
for student in range(num_students):

    print(f"\nStudent {student + 1}")

    name = input("Enter student name: ")

    marks = []

    # Ask for the mark for each subject
    for subject in subjects:

        while True:

            mark = float(input(f"Enter {subject} mark: "))

            # Validate the mark
            if 0 <= mark <= 100:
                marks.append(mark)
                break
            else:
                print("Invalid mark. Please enter a mark between 0 and 100.")


    # Calculate results
    total = sum(marks)
    average = total / len(marks)
    highest = max(marks)
    lowest = min(marks)


    # Determine final grade
    if average >= 90:
        grade = "A+"

    elif average >= 80:
        grade = "A"

    elif average >= 70:
        grade = "B"

    elif average >= 60:
        grade = "C"

    elif average >= 50:
        grade = "D"

    else:
        grade = "F"


    print(f"\n---- {name}'s Report ----\n")

    failed_subjects = 0


    # Analyze each individual subject
    for i in range(len(subjects)):

        subject = subjects[i]
        mark = marks[i]

        if mark >= 90:
            performance = "Excellent"

        elif mark >= 75:
            performance = "Very Good"

        elif mark >= 60:
            performance = "Good"

        elif mark >= 50:
            performance = "Passed"

        else:
            performance = "Failed"
            failed_subjects += 1

        print(f"{subject}: {mark:g} - {performance}")


    # Display calculations
    print(f"\nTotal: {total:g}")
    print(f"Average: {average:.2f}%")
    print(f"Highest Mark: {highest:g}")
    print(f"Lowest Mark: {lowest:g}")

    print(f"\nGrade: {grade}")
    print(f"Failed Subjects: {failed_subjects}")


    # Determine overall result
    if failed_subjects >= 2:
        result = "FAILED - Too many failed subjects"

    elif grade == "F":
        result = "FAILED"

    else:
        result = "PASSED"

    print(f"Result: {result}")


    # Update class summary
    if result.startswith("FAILED"):
        failed_students += 1

    elif grade == "A+" or grade == "A":
        a_students += 1

    elif grade == "B":
        b_students += 1

    elif grade == "C":
        c_students += 1

    elif grade == "D":
        d_students += 1


# Final class summary
print("\n========== CLASS SUMMARY ==========")

print(f"\nTotal Students: {num_students}")
print(f"A+/A Students: {a_students}")
print(f"B Students: {b_students}")
print(f"C Students: {c_students}")
print(f"D Students: {d_students}")
print(f"Failed Students: {failed_students}")
