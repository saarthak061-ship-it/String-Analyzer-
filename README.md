# String-Analyzer-
import java.util.Scanner;

class StringAnalyzer {
    private String text;

    public StringAnalyzer(String text) {
        this.text = text;
    }

    public int countVowels() {
        int count = 0;
        for (char c : text.toCharArray()) {
            if ("aeiouAEIOU".indexOf(c) != -1) count++;
        }
        return count;
    }

    public int countConsonants() {
        int count = 0;
        for (char c : text.toCharArray()) {
            if (Character.isLetter(c) && "aeiouAEIOU".indexOf(c) == -1) count++;
        }
        return count;
    }

    public int countDigits() {
        int count = 0;
        for (char c : text.toCharArray()) {
            if (Character.isDigit(c)) count++;
        }
        return count;
    }

    public int countSpaces() {
        int count = 0;
        for (char c : text.toCharArray()) {
            if (Character.isWhitespace(c)) count++;
        }
        return count;
    }

    public boolean isPalindrome() {
        String clean = text.replaceAll("[^a-zA-Z0-9]", "").toLowerCase();
        String reversed = new StringBuilder(clean).reverse().toString();
        return clean.equals(reversed);
    }
}

public class StringAnalyzerApp {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter a string: ");
        String input = sc.nextLine();

        StringAnalyzer analyzer = new StringAnalyzer(input);
        System.out.println("\n--- String Analysis ---");
        System.out.println("a) Vowels     : " + analyzer.countVowels());
        System.out.println("b) Consonants : " + analyzer.countConsonants());
        System.out.println("c) Digits     : " + analyzer.countDigits());
        System.out.println("d) Spaces     : " + analyzer.countSpaces());
        System.out.println("e) Palindrome : " + (analyzer.isPalindrome() ? "Yes" : "No"));

        sc.close();
    }
}
