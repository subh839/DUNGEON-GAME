# DUNGEON-GAME

 int dp[201][201];
    int helper(vector<vector<int>> &dungeon ,int i,int j){
        if(i>=dungeon.size() || j>= dungeon[0].size())
            return INT_MAX;
        if(dp[i][j]!=-1) return dp[i][j];
        
        int health=min(helper(dungeon,i+1,j),helper(dungeon,i,j+1));
        if(health==INT_MAX)
            health=1;
        int res=0;
        if(health-dungeon[i][j]>0){
            res=health-dungeon[i][j];
        }
        else res=1;
        return dp[i][j]=res;

    }
    int calculateMinimumHP(vector<vector<int>>& dungeon) {
        memset(dp,-1,sizeof(dp));
        return helper(dungeon,0,0);
    }
};
