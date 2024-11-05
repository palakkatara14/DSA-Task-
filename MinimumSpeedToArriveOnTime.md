class Solution {
    public int minSpeedOnTime(int[] dist, double hour) {
        int start = 1;
        int end = 10000000;
        int ans = -1;
        
        while (start <= end) {
            int mid = start + (end - start) / 2;
            if (canReach(dist, hour, mid)) {
                ans = mid;
                end = mid - 1;
            } else {
                start = mid + 1;
            }
        }
        return ans;
    }

    public boolean canReach(int[] dist, double hour, double speed) {
        double time = 0;
        for (int i = 0; i < dist.length - 1; i++) {
            time += Math.ceil((double) dist[i] / speed);
        }
        time += ((double) dist[dist.length - 1] / speed);
        return time <= hour;
    }
}