import java.util.*;

public class QuizApp {
    private static Map<String, List<Question>> quizCollection = new HashMap<>();

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        boolean isRunning = true;

        System.out.println("Welcome to the Quiz Application!");

        while (isRunning) {
            System.out.println("\nMain Menu:");
            System.out.println("1. Create a Quiz");
            System.out.println("2. Take a Quiz");
            System.out.println("3. Exit");
            System.out.print("Enter your choice: ");

            int userChoice = scanner.nextInt();
            scanner.nextLine(); 

            switch (userChoice) {
                case 1:
                    createQuiz(scanner);
                    break;
                case 2:
                    takeQuiz(scanner);
                    break;
                case 3:
                    isRunning = false;
                    System.out.println("Thank you for using the Quiz Application!");
                    break;
                default:
                    System.out.println("Invalid choice. Please try again.");
            }
        }

        scanner.close();
    }

    private static void createQuiz(Scanner scanner) {
        System.out.print("Enter quiz name: ");
        String quizName = scanner.nextLine();

        List<Question> questions = new ArrayList<>();
        boolean addMoreQuestions = true;

        while (addMoreQuestions) {
            System.out.print("Enter the question: ");
            String questionText = scanner.nextLine();

            List<String> options = new ArrayList<>();
            for (int i = 1; i <= 4; i++) {
                System.out.print("Option " + i + ": ");
                options.add(scanner.nextLine());
            }

            System.out.print("Enter the correct answer (1-4): ");
            int correctAnswerIndex = scanner.nextInt();
            scanner.nextLine(); 

            questions.add(new Question(questionText, options, correctAnswerIndex));

            System.out.print("Would you like to add another question? (yes/no): ");
            addMoreQuestions = scanner.nextLine().equalsIgnoreCase("yes");
        }

        quizCollection.put(quizName, questions);
        System.out.println("Quiz '" + quizName + "' created successfully!");
    }

    private static void takeQuiz(Scanner scanner) {
        if (quizCollection.isEmpty()) {
            System.out.println("No quizzes available. Please create one first.");
            return;
        }

        System.out.println("Available quizzes:");
        for (String quizName : quizCollection.keySet()) {
            System.out.println("- " + quizName);
        }

        System.out.print("Enter the name of the quiz you'd like to take: ");
        String quizName = scanner.nextLine();

        List<Question> questions = quizCollection.get(quizName);
        if (questions == null) {
            System.out.println("Quiz not found. Please check the name and try again.");
            return;
        }

        int score = 0;

        for (Question question : questions) {
            System.out.println("\n" + question.getText());
            List<String> options = question.getOptions();
            for (int i = 0; i < options.size(); i++) {
                System.out.println((i + 1) + ". " + options.get(i));
            }

            System.out.print("Your answer (1-4): ");
            int userAnswer = scanner.nextInt();
            scanner.nextLine(); 

            if (userAnswer == question.getCorrectAnswerIndex()) {
                score++;
                System.out.println("Correct!");
            } else {
                System.out.println("Incorrect. The correct answer was option " + question.getCorrectAnswerIndex() + ".");
            }
        }

        System.out.println("\nYour final score: " + score + " out of " + questions.size());
    }
}

class Question {
    private String text;
    private List<String> options;
    private int correctAnswerIndex;

    public Question(String text, List<String> options, int correctAnswerIndex) {
        this.text = text;
        this.options = options;
        this.correctAnswerIndex = correctAnswerIndex;
    }

    public String getText() {
        return text;
    }

    public List<String> getOptions() {
        return options;
    }

    public int getCorrectAnswerIndex() {
        return correctAnswerIndex;
    }
}
