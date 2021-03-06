# 36. Valid Sudoku
### Question:

Determine if a 9x9 Sudoku board is valid. Only the filled cells need to be validated according to the following rules:

Each row must contain the digits 1-9 without repetition.
Each column must contain the digits 1-9 without repetition.
Each of the 9 3x3 sub-boxes of the grid must contain the digits 1-9 without repetition.

![数独](https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1524037017049&di=0e1f5339ba4788e38826c6dc21c3c75b&imgtype=0&src=http%3A%2F%2Fp8.qhimg.com%2Ft0154f4db11f42802bf.jpg)

### Example:
```
Input:
[
  ["5","3",".",".","7",".",".",".","."],
  ["6",".",".","1","9","5",".",".","."],
  [".","9","8",".",".",".",".","6","."],
  ["8",".",".",".","6",".",".",".","3"],
  ["4",".",".","8",".","3",".",".","1"],
  ["7",".",".",".","2",".",".",".","6"],
  [".","6",".",".",".",".","2","8","."],
  [".",".",".","4","1","9",".",".","5"],
  [".",".",".",".","8",".",".","7","9"]
]
Output: true
```

### Analysis:

### Solution:
```+python
def isValidSudoku(self, board):
    seen = []
    for i, row in enumerate(board):
        for j, c in enumerate(row):
            if c != '.':
                seen += [(c,j),(i,c),(i/3,j/3,c)] #第一列判断行有没有重复，第二列判断列有没有重复，第三列判断一个小矩阵内有没有重复
                #如果都没有重复，去除重复后应该相等
    return len(seen) == len(set(seen))
```

### 本题关键：
* ***巧用set***
`python的set和其他语言类似, 是一个无序不重复元素集, 基本功能包括关系测试和消除重复元素. 集合对象还支持union(联合), intersection(交), difference(差)和sysmmetric difference(对称差集)等数学运算.`
```
>>> x = set('spam')  
>>> y = set(['h','a','m'])  
>>> x, y  
(set(['a', 'p', 's', 'm']), set(['a', 'h', 'm']))  
```
