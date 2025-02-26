# Project-C-
// main.cpp
#include <iostream>
#include <vector>
#include "Student.h"
#include "Teacher.h"
#include "Course.h"
#include "Database.h"

void displayMenu();
void handleUserChoice(int choice, Database& db);

int main() {
    Database db;
    int choice;
    
    do {
        displayMenu();
        std::cin >> choice;
        handleUserChoice(choice, db);
    } while (choice != 0);

    return 0;
}

void displayMenu() {
    std::cout << "\nSchool Information System\n";
    std::cout << "1. Add Student\n";
    std::cout << "2. Add Teacher\n";
    std::cout << "3. Add Course\n";
    std::cout << "4. View All Students\n";
    std::cout << "5. View All Teachers\n";
    std::cout << "6. View All Courses\n";
    std::cout << "0. Exit\n";
    std::cout << "Enter your choice: ";
}

void handleUserChoice(int choice, Database& db) {
    switch(choice) {
        case 1:
            db.addStudent();
            break;
        case 2:
            db.addTeacher();
            break;
        case 3:
            db.addCourse();
            break;
        case 4:
            db.viewAllStudents();
            break;
        case 5:
            db.viewAllTeachers();
            break;
        case 6:
            db.viewAllCourses();
            break;
        case 0:
            std::cout << "Exiting program. Goodbye!\n";
            break;
        default:
            std::cout << "Invalid choice. Please try again.\n";
    }
}

// Student.h
#pragma once
#include <string>

class Student {
private:
    int id;
    std::string name;
    int age;

public:
    Student(int id, const std::string& name, int age);
    void display() const;
    // Add getters and setters as needed
};

// Teacher.h
#pragma once
#include <string>

class Teacher {
private:
    int id;
    std::string name;
    std::string subject;

public:
    Teacher(int id, const std::string& name, const std::string& subject);
    void display() const;
    // Add getters and setters as needed
};

// Course.h
#pragma once
#include <string>

class Course {
private:
    int id;
    std::string name;
    int teacherId;

public:
    Course(int id, const std::string& name, int teacherId);
    void display() const;
    // Add getters and setters as needed
};

// Database.h
#pragma once
#include <vector>
#include "Student.h"
#include "Teacher.h"
#include "Course.h"

class Database {
private:
    std::vector<Student> students;
    std::vector<Teacher> teachers;
    std::vector<Course> courses;

public:
    void addStudent();
    void addTeacher();
    void addCourse();
    void viewAllStudents() const;
    void viewAllTeachers() const;
    void viewAllCourses() const;
    // Add more methods as needed
};
