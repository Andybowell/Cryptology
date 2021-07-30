import java.lang.Math;
import java.util.Scanner;
class Main {
    public static void main(String[] args) {

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


        //initiating L[1], L[2], R[1], R[2]

        L[1] = L[2] = R[1] = R[2] = 0x00000000;

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


        // Decryption
        //input L[2] from the Scanner
        System.out.print("\nPlease input L[2] in Hex String (without “0x”): ");
        hexStr = input.nextLine().toUpperCase(); // Taking user input
        L[2] = Long.parseLong(hexStr, 16);
        System.out.println("\n" + "L[2]" + ": 0x" + Long.toHexString(L[2]).toUpperCase());

        //input R[2] from the Scanner
        System.out.print("\nPlease input R[2] in Hex String (without “0x”): ");
        hexStr1 = input.nextLine().toUpperCase(); // Taking user input
        R[2] = Long.parseLong(hexStr1, 16);
        System.out.println("\n" + "R[2]" + ": 0x" + Long.toHexString(R[0]).toUpperCase());
        //System.out.println("\n L[1]= 0x" + L[1] + "\n L[2]= 0x"  + L[2] + "\n R[1]= 0x"  + R[1] + "\n R[2]= 0x" +  R[2]);

        System.out.println("\n Decryption: \n");
        L[1] = L[0] = R[1] = R[0] = 0x00000000;

        // R0 = R2 曰 [[(L2 << 4) ⽥ K2]  [L2 ⽥ δ2]  [(L2 >> 5) ⽥ K3]]
        // L0 = L2 曰 [[(R0 << 4) ⽥ K0]  [R0 ⽥ δ1]  [(R0 >> 5) ⽥ K1]]

        // L1 = R2 -  F(L2, K2, K3, δ2)
        // R1 = L2

        // L0 = R1 -  F(L1, K0, K1, δ1)
        // R0 = L1   

        for (int i = 1, j = 2 ; i >= 0; i--, j-= 2) {

            long P = (((L[i+1]<< 4) + K[j]) % (long) Math.pow(2, 32));
            long Q = ((L[i+1] + Delta[i]) % (long) Math.pow(2, 32));
            long O = (((L[i+1] >> 5) + K[j + 1]) % (long) Math.pow(2, 32));

            L[i] = ((R[i+1] - (P^Q^O)) % (long) Math.pow(2, 32));
            R[i] = L[i+1];

            System.out.println("\nCiphertext pass " + (i) + "\nL" + (i) + "= 0x" + L[i] + "\nR" + (i) + "= 0x" + R[i]);
        }
    }
}
