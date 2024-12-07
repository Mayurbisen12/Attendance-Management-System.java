# Attendance-Management-System.java
CREATE TABLE students (
  id INT PRIMARY KEY,
  name VARCHAR(255),
  email VARCHAR(255),
  course VARCHAR(255)
);

CREATE TABLE faculty (
  id INT PRIMARY KEY,
  name VARCHAR(255),
  email VARCHAR(255),
  department VARCHAR(255)
);

CREATE TABLE courses (
  id INT PRIMARY KEY,
  name VARCHAR(255),
  faculty_id INT,
  FOREIGN KEY (faculty_id) REFERENCES faculty(id)
);

CREATE TABLE attendance (
  id INT PRIMARY KEY,
  student_id INT,
  course_id INT,
  date DATE,
  status VARCHAR(255),
  FOREIGN KEY (student_id) REFERENCES students(id),
  FOREIGN KEY (course_id) REFERENCES courses(id)
);

<dependencies>
  <dependency>
    <groupId>mysql</groupId>
    <artifactId>mysql-connector-java</artifactId>
    <version>8.0.21</version>
  </dependency>
  <dependency>
    <groupId>javax.servlet</groupId>
    <artifactId>javax.servlet-api</artifactId>
    <version>4.0.1</version>
  </dependency>
  <dependency>
    <groupId>javax.servlet.jsp</groupId>
    <artifactId>javax.servlet.jsp-api</artifactId>
    <version>2.3.3</version>
  </dependency>
  <dependency>
    <groupId>org.apache.tomcat</groupId>
    <artifactId>tomcat-servlet-api</artifactId>
    <version>9.0.41</version>
  </dependency>
</dependencies>
Student.java (Model)

public class Student {
  private int id;
  private String name;
  private String email;
  private String course;
  // getters and setters
}


StudentServlet.java (Controller)

@WebServlet("/student")
public class StudentServlet extends HttpServlet {
  @Override
  protected void doGet(HttpServletRequest req, HttpServletResponse resp) {
    // retrieve student attendance data from database
    // forward to student.jsp
  }
}


student.jsp (View)

jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" %>
<!DOCTYPE html>
<html>
<head>
  <title>Student Attendance</title>
</head>
<body>
  <h1>Student Attendance</h1>
  <table>
    <tr>
      <th>Date</th>
      <th>Status</th>
    </tr>
    <c:forEach items="${attendance}" var="attendance">
      <tr>
        <td>${attendance.date}</td>
        <td>${attendance.status}</td>
      </tr>
    </c:forEach>
  </table>
</body>
</html>


