1st May Leetcode problem of day

Input: word = "abcdefd", ch = "d"
Output: "dcbaefd"
Explanation: The first occurrence of "d" is at index 3. 
Reverse the part of word from 0 to 3 (inclusive), the resulting string is "dcbaefd".
**********Solution*****************
class Solution {
public:
    string reversePrefix(string word, char ch) {
      int n = word.size();
        int m = -1;
        for (int i = 0; i < n; i++) {
            if (word[i] == ch) {
                m = i;
                break;
            }
        }
        if (m == -1) {
            return word;
        }
        for (int i = 0, j = m; i < j; i++, j--) {
            swap(word[i], word[j]);
        }
        return word;
    }
};
