# demo-2-
class Solution {
public:
    string evaluate(string s, vector<vector<string>>& knowledge) {
        
        // Store key-value pairs in a map
        unordered_map<string, string> mp;
        
        for (auto &p : knowledge) {
            mp[p[0]] = p[1];
        }
        
        string ans = "";
        
        for (int i = 0; i < s.size(); i++) {
            
            if (s[i] == '(') {
                // Find closing bracket
                int j = i + 1;
                string key = "";
                
                while (s[j] != ')') {
                    key += s[j];
                    j++;
                }
                
                // Replace key with its value
                if (mp.find(key) != mp.end()) {
                    ans += mp[key];
                } else {
                    ans += "?";
                }
                
                // Skip the complete bracket pair
                i = j;
            }
            else {
                ans += s[i];
            }
        }
        
        return ans;
    }
};
