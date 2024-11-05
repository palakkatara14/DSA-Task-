import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt();
        while (t-- > 0) {
            int n = sc.nextInt();
            int c = sc.nextInt();
            int[] stalls = new int[n];
            for (int i = 0; i < n; i++) {
                stalls[i] = sc.nextInt();
            }
            Arrays.sort(stalls);
            System.out.println(maxdistance(c, stalls));
        }
    }

    public static int maxdistance(int c, int[] stalls) {
        int start = 1;
        int end = stalls[stalls.length - 1];
        int ans = 0;

        while (start <= end) {
            int mid = start + (end - start) / 2;
            if (isitpossible(mid, stalls, c)) {
                ans = mid;
                start = mid + 1;
            } else {
                end = mid - 1;
            }
        }
        return ans;
    }

    public static boolean isitpossible(int mid, int[] stalls, int c) {
        int cp = 1;
        int lastplaced = stalls[0];
        for (int i = 1; i < stalls.length; i++) {
            if ((stalls[i] - lastplaced) >= mid) {
                cp++;
                lastplaced = stalls[i];
            }
        }
        return cp >= c;
    }
}
