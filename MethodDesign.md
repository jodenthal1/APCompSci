public class MethodDesign {

    public static void main(String[] args) {
        // Create a new Student object
        Student student = new Student("Alice", 101);

        // Set test scores for the student's courses
        student.setTestScore(0, 85);
        student.setTestScore(1, 90);
        student.setTestScore(2, 95);

        // Display student details and average test score
        System.out.println(student);
        System.out.println("Average Score: " + student.getAverage());
    }
}

class Course {
    private String courseName;
    private int testScore;

    public Course(String courseName) {
        this.courseName = courseName;
        this.testScore = 0; // Initialize test score to 0
    }

    public String getCourseName() {
        return courseName;
    }

    public void setCourseName(String courseName) {
        this.courseName = courseName;
    }

    public int getTestScore() {
        return testScore;
    }

    public void setTestScore(int score) {
        this.testScore = score;
    }
}

class Student {
    private String name;
    private int id;
    private Course[] courses;

    // Constructor with name and id, initializing 3 courses
    public Student(String name, int id) {
        this.name = name;
        this.id = id;
        this.courses = new Course[3];
        this.courses[0] = new Course("Course 1");
        this.courses[1] = new Course("Course 2");
        this.courses[2] = new Course("Course 3");
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }

    public void setTestScore(int courseIndex, int score) {
        if (courseIndex >= 0 && courseIndex < courses.length) {
            courses[courseIndex].setTestScore(score);
        } else {
            System.out.println("Invalid course index");
        }
    }

    public int getTestScore(int courseIndex) {
        if (courseIndex >= 0 && courseIndex < courses.length) {
            return courses[courseIndex].getTestScore();
        } else {
            System.out.println("Invalid course index");
            return -1;
        }
    }

    public double getAverage() {
        int totalScore = 0;
        for (Course course : courses) {
            totalScore += course.getTestScore();
        }
        return totalScore / 3.0;
    }

    @Override
    public String toString() {
        StringBuilder details = new StringBuilder("Name: " + name + ", ID: " + id + "\nCourses:\n");
        for (Course course : courses) {
            details.append(course.getCourseName()).append(" - Test Score: ").append(course.getTestScore()).append("\n");
        }
        return details.toString();
    }
}
