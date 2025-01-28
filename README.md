# Leetcode---2300
Successful Pairs of Spells and Potions
//Code in java
import java.util.Arrays;

public class Solution {
    public int[] successfulPairs(int[] spells, int[] potions, long success) {
        Arrays.sort(potions);
        int[] result = new int[spells.length];
        for (int i = 0; i < spells.length; i++) {
            int left = 0, right = potions.length - 1;
            while (left <= right) {
                int mid = left + (right - left) / 2;
                if ((long) spells[i] * potions[mid] >= success) {
                    right = mid - 1;
                } else {
                    left = mid + 1;
                }
            }
            result[i] = potions.length - left;
        }
        return result;
    }

    public static void main(String[] args) {
        Solution solution = new Solution();
        int[] spells = {10, 20, 30};
        int[] potions = {1, 2, 3, 4, 5};
        long success = 50;
        int[] result = solution.successfulPairs(spells, potions, success);
        System.out.println("Successful pairs: " + Arrays.toString(result));
    }
}
