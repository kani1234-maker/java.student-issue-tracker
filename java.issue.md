\\Issue.java file
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
//IssueManager.java file
import java.util.*;

class IssueManager {

    ArrayList<Issue> issues = new ArrayList<>();

    void addIssue(Issue issue) {
        issues.add(issue);
    }

    void viewAllIssues() {
        for(Issue i : issues) {
            i.displayIssue();
        }
    }

    void updateStatus(int id, String newStatus) {

        for(Issue i : issues) {

            if(i.issueId == id) {
                i.status = newStatus;
            }

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
            System.out.println("4 Exit");

            int choice = sc.nextInt();
            sc.nextLine();

            if(choice == 1) {

                System.out.println("Enter Student Name:");
                String name = sc.nextLine();

                System.out.println("Enter Issue Title:");
                String title = sc.nextLine();

                System.out.println("Enter Description:");
                String desc = sc.nextLine();

                Issue issue = new Issue(issueCounter++, name, title, desc);
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

                break;

            }

        }

    }
}
