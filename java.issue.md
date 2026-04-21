\\Issue.java file
class Issue {

    int issueId;
    String studentName;
    String title;
    String description;
    String priority;
    String status;

    Issue(int issueId, String studentName, String title, String description, String priority) {
        this.issueId = issueId;
        this.studentName = studentName;
        this.title = title;
        this.description = description;
        this.priority = priority;
        this.status = "Pending";
    }

    void displayIssue() {
        System.out.println("Issue ID: " + issueId);
        System.out.println("Student: " + studentName);
        System.out.println("Title: " + title);
        System.out.println("Description: " + description);
        System.out.println("Priority: " + priority);
        System.out.println("Status: " + status);
        System.out.println("---------------------------");
    }
}
//IssueManager.java file
import java.util.*;

class IssueManager {

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
                System.out.println("Status updated!");
                return;
            }
        }
        System.out.println("Issue not found!");
    }

    void updatePriority(int id, String newPriority) {
        for (Issue i : issues) {
            if (i.issueId == id) {
                i.priority = newPriority;
                System.out.println("Priority updated!");
                return;
            }
        }
        System.out.println("Issue not found!");
    }

    void searchIssueById(int id) {
        boolean found = false;

        for (Issue i : issues) {
            if (i.issueId == id) {
                i.displayIssue();
                found = true;
                break;
            }
        }

        if (!found) {
            System.out.println("Issue not found!");
        }
    }
}
//Main file
import java.util.*;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);
        IssueManager manager = new IssueManager();

        int issueCounter = 1;

        while(true) {

            System.out.println("1 Submit Issue");
            System.out.println("2 View Issues");
            System.out.println("3 Update Status");
            System.out.println("4 Search Issue by ID");
            System.out.println("5 Exit");

            int choice = sc.nextInt();
            sc.nextLine();

            if(choice == 1) {

                System.out.println("Enter Student Name:");
                String name = sc.nextLine();

                System.out.println("Enter Issue Title:");
                String title = sc.nextLine();

                System.out.println("Enter Description:");
                String desc = sc.nextLine();

                System.out.println("Enter Priority (Low/Medium/High):");
                String priority = sc.nextLine();

                Issue issue = new Issue(issueCounter++, name, title, desc, priority);
                manager.addIssue(issue);

            }

            else if(choice == 2) {

                manager.viewAllIssues();

            }

            else if(choice == 3) {

                System.out.println("Enter Issue ID:");
                int id = sc.nextInt();
                sc.nextLine();

                System.out.println("Enter New Status:");
                String status = sc.nextLine();

                manager.updateStatus(id, status);

            }

            else if(choice == 4) {

                System.out.println("Enter Issue ID:");
                int id = sc.nextInt();
                sc.nextLine();

                manager.searchIssueById(id);

            }

            else if(choice == 5) {

                System.out.println("Exiting...");
                break;

            }
        }
    }
}
