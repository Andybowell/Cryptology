import java.lang.Math;
import java.util.Scanner;

public class Encryption {

    @SuppressWarnings({
        "unused",
        "resource"
    })
    public static void main(String[] args) {
        // TODO Auto-generated method stub
        //initiating variables

        int DeltaOne = 0x11111111;
        int DeltaTwo = 0x22222222;
        long Delta[] = {
            0x11111111,
            0x22222222
        };
        long K[] = new long[4];
        long L[] = new long[3];
        long R[] = new long[3];


        Scanner input = new Scanner(System.in); // If you want to take 5 numbers for user and store it in an int array
        for (int i = 0; i < 4; i++) {
            System.out.print("\nPlease input K[i] in Hex String (without “0x”) " + (i) + ": ");
            String hexStr = input.nextLine().toUpperCase(); // Taking user input

            // Convert HexaDecimal String to long
            K[i] = Long.parseLong(hexStr, 16);
        }

        // For printing those numbers
        for (int i = 0; i < 4; i++) {
            System.out.println("\n" + "K" + (i) + ": 0x" + Long.toHexString(K[i]).toUpperCase());
        }

        //input L[2] from the Scanner
        System.out.print("\nPlease input L[0] in Hex String (without “0x”): ");
        String hexStr = input.nextLine().toUpperCase(); // Taking user input
        L[0] = Long.parseLong(hexStr, 16);
        System.out.println("\n" + "L[0]" + ": 0x" + Long.toHexString(L[0]).toUpperCase());

        //input R[2] from the Scanner
        System.out.print("\nPlease input R[0] in Hex String (without “0x”): ");
        String hexStr1 = input.nextLine().toUpperCase(); // Taking user input
        R[0] = Long.parseLong(hexStr1, 16);
        System.out.println("\n" + "R[0]" + ": 0x" + Long.toHexString(R[0]).toUpperCase());
        System.out.println("\n L[1]= 0x" + L[1] + "\n L[2]= 0x" + L[2] + "\n R[1]= 0x" + R[1] + "\n R[2]= 0x" + R[2]);

        System.out.println("\n Encryption: \n");

        //initiating L[1], L[2], R[1], R[2]
        L[1] = L[2] = R[1] = R[2] = 0x00000000;

        for (int i = 1, j = 0; i < 3; i++, j += 2) {

            long P = (((R[i - 1] << 4) + K[j]) % (long) Math.pow(2, 32));
            long Q = ((R[i - 1] + Delta[i - 1]) % (long) Math.pow(2, 32));
            long O = (((R[i - 1] >>> 5) + K[j + 1]) % (long) Math.pow(2, 32));

            L[i] = R[i - 1];
            R[i] = (((P ^ O ^ Q) + L[i-1]) % (long) Math.pow(2, 32));


            System.out.println("\nCiphertext pass " + (i) + "\nL" + (i) + "= 0x" + Long.toHexString(L[i]).toUpperCase() +
                "\nR" + (i) + "= 0x" + Long.toHexString(R[i]).toUpperCase());
        }
    }

}
