##### leetcode17_电话号码的字母组合
给定一个仅包含数字 2-9 的字符串，返回所有它能表示的字母组合。答案可以按任意顺序返回。
```javascript
/**
 * @param {string} digits
 * @return {string[]}
 */
var letterCombinations = function(digits) {
    const k = digits.length;
    const map = ["", "", "abc", "def", "ghi", "jkl", "mno", "pqrs", "tuv", "wxyz"];
    //每题必须点，判断边界
    if(!k) return [];
    if(k === 1) return map[digits].split("");

    //使用回溯
    var res = [], path = [];
    back_Tracking(digits, k, 0);
    return res;

    //建立N叉树，宽度为子集的长度map[tree[a]]，深度为digits的长度
    function back_Tracking(tree, deep, a) {
        if(path.length == deep) {
            res.push(path.join(""));
            return;
        }
        for(const v of map[tree[a]]) {
            path.push(v);
            back_Tracking(tree, deep, a+1);
            path.pop();
        }
    }
    
};


```