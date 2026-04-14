class Issue {
    public static void main(String[] args) {
        Issue issue1 = new Issue(1, "Alice", "Login Problem", "Unable to login to the portal.");
        Issue issue2 = new Issue(2, "Bob", "Assignment Submission", "Cannot submit assignment on time.");

        issue1.displayIssue();
        issue2.displayIssue();
    }
    int issueId;
    String studentName;
    String title;
    String description;
    String status;

    Issue(int issueId, String studentName, String title, String description) {
        this.issueId = issueId;
        this.studentName = studentName;
        this.title = title;
        this.description = description;
        this.status = "Pending";
    }

    void displayIssue() {
        System.out.println("Issue ID: " + issueId);
        System.out.println("Student: " + studentName);
        System.out.println("Title: " + title);
        System.out.println("Description: " + description);
        System.out.println("Status: " + status);
        System.out.println("---------------------------");
    }
}