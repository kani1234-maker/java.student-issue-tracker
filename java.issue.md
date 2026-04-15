class Issue {
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
public class IssueManager { 
     public static void main(String[] args) {
        IssueManager manager = new IssueManager();

        Issue issue1 = new Issue(1, "Alice", "Login Problem", "Unable to login to the portal.");
        Issue issue2 = new Issue(2, "Bob", "Assignment Submission", "Cannot submit assignment on time.");

        manager.addIssue(issue1);
        manager.addIssue(issue2);

        System.out.println("All Issues:");
        manager.viewAllIssues();

        System.out.println("Updating status of Issue ID 1...");
        manager.updateStatus(1, "Resolved");

        System.out.println("All Issues after update:");
        manager.viewAllIssues();
    }
    ArrayList<Issue> issues = new ArrayList<>();

    void addIssue(Issue issue) {
        issues.add(issue);
    }

    void viewAllIssues() {
        for (Issue i : issues) {
            i.displayIssue();
        }
    }

    void updateStatus(int id, String newStatus) {
        for (Issue i : issues) {
            if (i.issueId == id) {
                i.status = newStatus;
            }
        }
    }
    public static void main(String[] args) {
        IssueManager manager = new IssueManager();

        Issue issue1 = new Issue(1, "Alice", "Login Problem", "Unable to login to the portal.");
        Issue issue2 = new Issue(2, "Bob", "Assignment Submission", "Cannot submit assignment on time.");

        manager.addIssue(issue1);
        manager.addIssue(issue2);

        manager.viewAllIssues();
        manager.updateStatus(1, "Resolved");
        manager.viewAllIssues();
    }
}
