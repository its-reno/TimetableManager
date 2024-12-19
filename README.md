## University Timetable Visualizer and Manager

This project is a **Java-based timetable visualizer and management application** developed as a university thesis. It processes an initial timetable of the University of Miskolc, Faculty of Mechanical Engineering and Informatics, which is provided in a `.doc` file format, extracts and transforms the data, and presents it in a user-friendly **Graphical User Interface (GUI)**. The program allows users to filter, manage, and display courses based on various criteria. It demonstrates advanced Java programming skills, including GUI development, database integration, and file processing.

## Features

### Core Functionality

- **Import Timetable Data**: Reads a `.doc` file containing the initial timetable using Apache POI libraries to extract course details.
- **Transform Data**: Converts raw timetable data into structured course objects with attributes such as subject name, semester, time, instructor, room, etc.
- **Display Timetable**: Presents the timetable in a GUI with filtering options (e.g., by day, semester, or instructor).
- **Manage Courses**:
    
    - Add new courses manually through the GUI.
    - Edit existing course details directly in the database.
    - Delete courses after confirmation.
    
- **User Management**:
    
    - Separate interfaces for administrators, teachers, and students.
    - User registration and login system with password management.
    - Email support for password recovery.
    

### User Roles

- **Administrator**:
    
    - Full access to manage courses and users.
    - View and edit all timetable entries.
    
- **Teacher**:
    
    - View their assigned courses and access relevant timetable details.
    
- **Student**:
    
    - View filtered timetables based on their enrolled courses.
    

### Technical Features

- **Database Integration**:
    
    - Uses Hibernate ORM for managing course and user data in a relational database.
    - Includes SQL scripts (`timetable.sql`) for initializing the database schema.
    
- **Dynamic GUI Generation**:
    
    - Built using IntelliJ IDEA's GUI Designer for streamlined development.
    - Separate GUIs for different user roles (AdminGUI, TeacherGUI, StudentGUI).
    
- **Duplicate Handling**: Automatically removes duplicate entries (e.g., same course listed multiple times for different groups) during timetable generation.

## Code Structure

The project is organized into three main packages:

### `coursemanagement`

Handles all functionalities related to courses and timetables:

- `CourseController`: Processes `.doc` files to extract and transform timetable data into course objects.
- `CourseDatabaseManager`: Manages CRUD operations for courses using Hibernate ORM.
- `TimeTable`: GUI for displaying the generated timetable with filtering options (e.g., by day of the week).
- GUIs:
    
    - `AddCourseGUI`: Add new courses manually.
    - `CourseTable` & `CourseTableStudent`: Display tables of courses for admins and students.
    

### `usermanagement`

Manages user accounts and authentication:

- `LoginGUI`, `RegistrationGUI`, `ChangePasswordGUI`, etc.: GUIs for user login, registration, and password management.
- `UserController`: Handles user-related logic such as authentication and account updates.
- `SendEmail`: Sends emails for password recovery or notifications.

### `maingui`

Provides role-specific dashboards:

- `AdminGUI`: Admin dashboard with full access to course and user management features.
- `TeacherGUI`: Teacher-specific dashboard to view assigned courses.
- `StudentGUI`: Student-specific dashboard to view filtered timetables.

### Resources

Includes configuration files and sample data:

- `geik_orarend.doc`: Sample `.doc` file containing the initial timetable structure.
- `hibernate.cfg.xml` & `UsersDB.hbm.xml`: Hibernate configuration files for database setup.
- `timetable.sql`: SQL script for initializing the database schema.

## How It Works

1. **Input Processing**:
    
    - The program reads the `.doc` file using Apache POI's WordExtractor to extract raw text data from the timetable document.
    - The extracted data is cleaned and transformed into structured course objects using fixed-width parsing techniques.
    
2. **Data Storage**:
    
    - The processed course objects are stored in a relational database using Hibernate ORM.
    
3. **Timetable Visualization**:
    
    - The GUI displays the timetable dynamically based on user-selected filters (e.g., day of the week).
    - Duplicate or redundant entries are automatically removed during visualization.
    
4. **User Interaction**:
    
    - Users log in through role-specific GUIs (Admin, Teacher, Student).
    - Depending on their role, users can view or manage courses using intuitive interfaces.
    

## Purpose

This project showcases advanced Java development skills suitable for enterprise-level applications:

- File processing with Apache POI libraries for `.doc` files.
- Database integration using Hibernate ORM with SQL schema design.
- Multi-role GUI development with dynamic content rendering based on user input.
- Object-oriented programming principles applied across modular packages.

## Limitations

- The `.doc` file format is outdated; support for modern formats like `.docx` could improve usability.
- No web-based interface; functionality is limited to desktop environments.
- Limited error handling for malformed input files or invalid database states.

## How to Run

1. Clone or download this repository.
2. Set up the database using the provided SQL script (`timetable.sql`).
3. Configure Hibernate by updating connection details in `hibernate.cfg.xml`.
4. Compile and run the application using your preferred IDE or command line:    
    ```
   javac Main.java
    java Main
    ```
    
- Use the provided sample `.doc` file (`geik_orarend.doc`) to test the application.
