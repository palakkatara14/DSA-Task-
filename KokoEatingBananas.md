class Solution {
    static boolean isitPossible(int[] arr, int hr, int mid) {
        int time = 0;
        for (int pile : arr) {
            if (pile % mid == 0) {
                time += (pile / mid);
            } else {
                time += (pile / mid) + 1;
            }
            if (time > hr) return false;
        }
        return true;
    }

    public int minEatingSpeed(int[] piles, int h) {
        Arrays.sort(piles);
        int strt = 1;
        int ans = 1;
        int end = piles[piles.length - 1];
        while (strt <= end) {
            int mid = strt + (end - strt) / 2;
            if (isitPossible(piles, h, mid)) {
                ans = mid;
                end = mid - 1;
            } else {
                strt = mid + 1;
            }
        }
        return ans;
    }
}
