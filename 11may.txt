class Solution {
  public:
    vector<long long> jugglerSequence(long long n) {
        // code here
         vector<long long> ans;
        
        while(n!=1) {
            ans.push_back(n);
            if(n%2==0)
                n=sqrt(n);
            else
                n=n*sqrt(n);
        }
        ans.push_back(1);
        return ans;
        
    }
};
