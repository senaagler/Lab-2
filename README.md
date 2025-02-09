# Lab-2
Number
import java.util.Scanner;


class InvalidAgeException extends Exception {
    public InvalidAgeException(String message) {
        super(message);
    }
}

public class Lab10 {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        try {
            
            System.out.print("Bir sayı girin: ");
            String sayiInput = scanner.nextLine();

            System.out.print("Bir yaş girin: ");
            String yasInput = scanner.nextLine();

            
            int sayi = parseSayi(sayiInput);

            
            int yas = parseYas(yasInput);

            
            System.out.println("Girilen sayı doğru formatta ve yaşı uygun.");
            System.out.println("Sayının karesi: " + (sayi * sayi));

            
        } catch (NumberFormatException e) {
            System.out.println("Hata: Sayı formatı hatalı. " + e.getMessage());
        } catch (InvalidAgeException e) {
            System.out.println("Hata: " + e.getMessage());
        } finally {
            scanner.close();
        }
    }

    
    private static int parseSayi(String input) throws NumberFormatException {
        try {
            return Integer.parseInt(input);
        } catch (NumberFormatException e) {
            throw new NumberFormatException("Girilen sayı bir tam sayı değil.");
        }
    }

  
    private static int parseYas(String input) throws InvalidAgeException {
        try {
            int yas = Integer.parseInt(input);
            if (yas < 18) {
                throw new InvalidAgeException("Yaş 18'den küçük olamaz.");
            }
            return yas;
        } catch (NumberFormatException e) {
            throw new NumberFormatException("Girilen yaş bir tam sayı değil.");
        }
    }
}
