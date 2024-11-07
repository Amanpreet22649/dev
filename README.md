#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#define MAX_STUDENTS 100
// Define the Student structure
struct Student {
 char name[50];
 float grade;
};
// Function prototypes
void addStudent(struct Student students[], int *count);
void displayStudents(const struct Student students[], int count);
int main() {
 struct Student students[MAX_STUDENTS];
 int studentCount = 0;
 int choice;
 while (1) {
 printf("\n--- Student Grade Tracker ---\n");
 printf("1. Add Student\n");
 printf("2. Display Students\n");
 printf("3. Exit\n");
 printf("Enter your choice: ");
 scanf("%d", &choice);
 switch (choice) {
 case 1:
 addStudent(students, &studentCount);
 break;
 case 2:
 displayStudents(students, studentCount);
 break;
 case 3:
 printf("Exiting program.\n");
 exit(0);
 default:
 printf("Invalid choice. Please try again.\n");
 }
 }
 return 0;
}
// Function to add a student record
void addStudent(struct Student students[], int *count) {
 if (*count >= MAX_STUDENTS) {
 printf("Maximum student limit reached.\n");
 return;
 }

 struct Student newStudent;
 printf("Enter student's name: ");
 scanf(" %[^\n]", newStudent.name); // Using " %[^\n]" to allow spaces in the name
 printf("Enter grade: ");
 scanf("%f", &newStudent.grade);
 students[*count] = newStudent;
 (*count)++;

 printf("Student added successfully.\n");
}
// Function to display all students' information
void displayStudents(const struct Student students[], int count) {
 if (count == 0) {
 printf("No students to display.\n");
 return;
 }
 printf("\n--- Student Records ---\n");
 for (int i = 0; i < count; i++) {
 printf("Student %d:\n", i + 1);
 printf(" Name: %s\n", students[i].name);
 printf(" Grade: %.2f\n\n", students[i].grade);
 }
}

