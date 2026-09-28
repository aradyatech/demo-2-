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
class Solution {
public:
    string reverseParentheses(string s) {
        stack<string> st;
        string curr = "";

        for (char ch : s) {
            if (ch == '(') {
                st.push(curr);
                curr = "";
            }
            else if (ch == ')') {
                reverse(curr.begin(), curr.end());
                curr = st.top() + curr;
                st.pop();
            }
            else {
                curr += ch;
            }
        }

        return curr;
    }
};

class Solution {
public:
    int maxDepth(string s) {
        int depth = 0;
        int ans = 0;

        for (char ch : s) {
            if (ch == '(') {
                depth++;
                ans = max(ans, depth);
            }
            else if (ch == ')') {
                depth--;
            }
        }

        return ans;
    }
};
