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
