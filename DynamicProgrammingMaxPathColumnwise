import java.util.*;

public class Main {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int R = sc.nextInt();
        int C = sc.nextInt();
        int grid[][] = new int[R][C];
        long dp[][] = new long[R][C];

        // Input and initialize first column
        for (int row = 0; row < R; row++) {
            for (int col = 0; col < C; col++) {
                grid[row][col] = sc.nextInt();
                if (col == 0) {
                    dp[row][col] = grid[row][col];
                }
            }
        }

        // Column-wise DP calculation
        for (int col = 1; col < C; col++) {
            long fsmax[] = getFSMax(dp, col - 1, R);
            for (int row = 0; row < R; row++) {
                dp[row][col] = grid[row][col] + (dp[row][col - 1] == fsmax[0] ? fsmax[1] : fsmax[0]);
            }
        }

        // Print the largest in the last column
        System.out.println(getFSMaxColumn(dp, C - 1, R)[0]);
    }

    // Finds largest and second largest in a column
    private static long[] getFSMax(long[][] dp, int col, int R) {
        long firstMax = Long.MIN_VALUE, secondMax = Long.MIN_VALUE;
        for (int row = 0; row < R; row++) {
            if (dp[row][col] > firstMax) {
                secondMax = firstMax;
                firstMax = dp[row][col];
            } else if (dp[row][col] > secondMax) {
                secondMax = dp[row][col];
            }
        }
        return new long[]{firstMax, secondMax};
    }

    // Helper to get max in final column
    private static long[] getFSMaxColumn(long[][] dp, int col, int R) {
        return getFSMax(dp, col, R);
    }
}
