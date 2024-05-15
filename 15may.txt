class Solution {
  public:
    vector<vector<string>> accountsMerge(vector<vector<string>> &accounts) {
        // code here
        unordered_map<string, string> emailToName;
        unordered_map<string, unordered_set<string>> graph;
        for (auto& account : accounts) {
            string name = account[0];
            for (int i = 1; i < account.size(); ++i) {
                emailToName[account[i]] = name;
                graph[account[i]].insert(account[1]);
                graph[account[1]].insert(account[i]);
            }
        }
        
        vector<vector<string>> mergedAccounts;
        unordered_set<string> visited;
        for (auto it = graph.begin(); it != graph.end(); ++it) {
            const string& email = it->first;
            const unordered_set<string>& neighbors = it->second;
            if (!visited.count(email)) {
                vector<string> component;
                dfs(email, graph, visited, component);
                sort(component.begin(), component.end());
                component.insert(component.begin(), emailToName[email]);
                mergedAccounts.push_back(component);
            }
        }
        
        return mergedAccounts;
    }

private:
    void dfs(const string& email, unordered_map<string, unordered_set<string>>& graph, unordered_set<string>& visited, vector<string>& component) {
        visited.insert(email);
        component.push_back(email);
        for (const auto& neighbor : graph[email]) {
            if (!visited.count(neighbor)) {
                dfs(neighbor, graph, visited, component);
            }
        }
    }
};
