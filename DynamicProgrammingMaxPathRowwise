import java.util.*;

public class Main {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int R = sc.nextInt();
        int C = sc.nextInt();
        int grid[][] = new int[R][C];
        long dp[][] = new long[R][C];

        // Input and initialize first row
        for (int row = 0; row < R; row++) {
            for (int col = 0; col < C; col++) {
                grid[row][col] = sc.nextInt();
                if (row == 0) {
                    dp[row][col] = grid[row][col];
                }
            }
        }

        // Now we need to do the calculation from the second row
        for (int row = 1; row < R; row++) {
            long fsmax[] = getFSMax(dp, row - 1, C);
            for (int col = 0; col < C; col++) {
                dp[row][col] = grid[row][col] + (dp[row - 1][col] == fsmax[0] ? fsmax[1] : fsmax[0]);
            }
        }

        // Print the largest in the last row
        System.out.println(getFSMax(dp, R - 1, C)[0]);
    }

    private static long[] getFSMax(long[][] dp, int row, int C) {
        long firstMax = Long.MIN_VALUE, secondMax = Long.MIN_VALUE;
        for (int col = 0; col < C; col++) {
            if (dp[row][col] > firstMax) {
                secondMax = firstMax;
                firstMax = dp[row][col];
            } else if (dp[row][col] > secondMax) {
                secondMax = dp[row][col];
            }
        }
        return new long[]{firstMax, secondMax};
    }
}
