import java.util.Arrays;
public class CoinChange {
    public static int coinChange(int coins[], int amount) {
        int dp[] = new int[amount + 1];
        Arrays.fill(dp, amount + 1);
        dp[0] = 0;
        for (int i = 0; i < coins.length; i++) {     // i → coin
            for (int j = coins[i]; j <= amount; j++) {   // j → amount
                dp[j] = Math.min(dp[j], dp[j - coins[i]] + 1);
            }
        }
        if (dp[amount] > amount)
            return -1;
        return dp[amount];
    }
    public static void main(String[] args) {
        int coins[] = {1, 2, 5,7};
        int amount = 9;
        int result = coinChange(coins, amount);
        if (result == -1)
            System.out.println("Not possible to make the amount");
        else
            System.out.println("Minimum coins required: " + result);
    }
}
