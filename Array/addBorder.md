# Add Border

Source: [CodeSignal Arcade][https://app.codesignal.com/]



## Problem

Given a rectangular matrix of characters, add a border of asterisks(`*`) to it.

#### 	Example

- For

  ```
  picture = ["abc",
             "ded"]
  ```

- the output should be

  ```
  addBorder(picture) = ["*****",
                        "*abc*",
                        "*ded*",
                        "*****"]
  ```


#### 	Input/Output

- **[input] array.string picture**

  A non-empty array of non-empty equal-length strings.

  *Guaranteed constraints:*
  `1 ≤ picture.length ≤ 100`,
  `1 ≤ picture[i].length ≤ 100`.

- **[output] array.string**

  The same matrix of characters, framed with a border of asterisks of width `1`.

  

## My Solution

##### python3

```python
def addBorder(picture):
    h = len(picture) + 1    # 3
    w = len(picture[0]) + 1
    rst = []
    temp = ""
    
    for i in range(h + 1):
        if i == 0 or i == h:
            for j in range(w + 1):
                temp += "*"
            rst.append(temp)
            temp = ""
        else:
            temp = "*%s*" %picture[i - 1]
            rst.append(temp)
            temp = ""
            
    return rst
```



## Other's Solutions

##### python3

```python
def addBorder(picture):
    l=len(picture[0])+2
    return ["*"*l]+[x.center(l,"*") for x in picture]+["*"*l]
```

```python
def addBorder(pic):
    return ['*'*(len(pic[0]) + 2)] + \
           ['*' + i + '*' for i in pic] + \
           ['*'*(len(pic[0]) + 2)]
```

```python
def addBorder(picture):
    r = ['*'*(len(picture[0])+2)]
    for i in picture:
        r.append('*' + i + '*')

    r.append(r[0])
    
    return r
```



##### C++

```c++
std::vector<std::string> addBorder(std::vector<std::string> picture) {
    for(auto &s: picture)
        s = "*"+s+"*";
    picture.insert(picture.begin(), string(picture[0].size(),'*'));
    picture.insert(picture.end(), string(picture[0].size(),'*'));
    return picture;
}
```

