## [Find Common Characters](https://leetcode.com/problems/find-common-characters/)
> Submission code: [Check here](https://leetcode.com/problems/find-common-characters/submissions/927047923/)

##### Concept

```
we can take a hashmap of type <char, int> and set the freq of each alphabet to max value of constraint. 
after that we will loop through each character of each word and set the freq to minimum occurrence for each word.
then we will loop throught the hashmap till the freq is zero and push the character into the solution array.

```

##### Algorithm

```
1. Create a hashmap alphaFreq<char, int> and set freq of each letter of alphabet to the maximum value of int or constraint.
2. Loop through each character of each word. create a hashmap freq and store the freq of each character of each word and the set the alphaFreq to the minimum freq of each character of each word.
3. Loop through the alphaFreq and push the character in the solution array until freq becomes 0.

```

<details><summary>Code</summary>

<p>

	
```C++
class Solution {
public:
    vector<string> commonChars(vector<string>& words) {
        unordered_map<char, int> alphaFreq;
        vector<string> solution;
        for(char i='a'; i<='z'; i++) {
            alphaFreq[i] = 1000;
        }
        for(auto w: words) {
            unordered_map<char, int> freq;
            for(auto ch: w) {
                freq[ch]++;
            }
            for(char c='a'; c<='z'; c++) {
                alphaFreq[c] = min(freq[c], alphaFreq[c]);
            }
        }
        for(auto alpha: alphaFreq) {
            while(alpha.second > 0) {
                string a = string(1, alpha.first);
                solution.push_back(a);
                alpha.second--;
            }
        }
        return solution;
    }
};
	
```
</p>
</details>
	
