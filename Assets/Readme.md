-- Create users table
CREATE TABLE users (
    UserID INT AUTO_INCREMENT PRIMARY KEY,
    Username VARCHAR(255),
    Email VARCHAR(255),
    UserType VARCHAR(255)
);

-- Create mentors table
CREATE TABLE mentors (
    MentorID INT AUTO_INCREMENT PRIMARY KEY,
    MentorName VARCHAR(255),
    Email VARCHAR(255)
);

-- Create courses table
CREATE TABLE courses (
    CourseID INT AUTO_INCREMENT PRIMARY KEY,
    CourseName VARCHAR(255),
    Description TEXT,
    MentorID INT,
    FOREIGN KEY (MentorID) REFERENCES mentors(MentorID)
);

-- Create admissions table
CREATE TABLE admissions (
    AdmissionID INT AUTO_INCREMENT PRIMARY KEY,
    UserID INT,
    CourseID INT,
    AdmissionDate DATE,
    FOREIGN KEY (UserID) REFERENCES users(UserID),
    FOREIGN KEY (CourseID) REFERENCES courses(CourseID)
);

-- Create codekata table
CREATE TABLE codekata (
    CodeKataID INT AUTO_INCREMENT PRIMARY KEY,
    CodeKataName VARCHAR(255),
    Description TEXT,
    CourseID INT,
    FOREIGN KEY (CourseID) REFERENCES courses(CourseID)
);

-- Create mentor table (assuming it's different from mentors)
CREATE TABLE mentor (
    MentorID INT AUTO_INCREMENT PRIMARY KEY,
    MentorName VARCHAR(255),
    Email VARCHAR(255)
);

-- Create student table (assuming it's different from users)
CREATE TABLE student (
    StudentID INT AUTO_INCREMENT PRIMARY KEY,
    StudentName VARCHAR(255),
    Email VARCHAR(255),
    UserType VARCHAR(255)
);

-- Create attendance table
CREATE TABLE attendance (
    AttendanceID INT AUTO_INCREMENT PRIMARY KEY,
    StudentID INT,
    CourseID INT,
    Date DATE,
    Status VARCHAR(255),
    FOREIGN KEY (StudentID) REFERENCES student(StudentID),
    FOREIGN KEY (CourseID) REFERENCES courses(CourseID)
);

-- Create task table
CREATE TABLE task (
    TaskID INT AUTO_INCREMENT PRIMARY KEY,
    TaskName VARCHAR(255),
    Description TEXT,
    UserID INT,
    Deadline DATE,
    FOREIGN KEY (UserID) REFERENCES users(UserID)
);

-- Create leaderboard table
CREATE TABLE leaderboard (
    LeaderboardID INT AUTO_INCREMENT PRIMARY KEY,
    UserID INT,
    CourseID INT,
    Score INT,
    FOREIGN KEY (UserID) REFERENCES users(UserID),
    FOREIGN KEY (CourseID) REFERENCES courses(CourseID)
);