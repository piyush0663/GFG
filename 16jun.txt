class Solution {
  public:
    vector<int> getPrimes(int n) {
        vector<bool> prime(n, true);
        for(int p = 2; p*p<n; p++){
            if(prime[p]){
                for(int i = p*p; i<n; i+=p)prime[i]=false;
            }
        }
        
        for(int i=2; i<=n/2; i++){
            if(prime[i] && prime[n-i])return vector<int>{i, n-i};
        }
        
        return vector<int> {-1, -1};
    }
};
