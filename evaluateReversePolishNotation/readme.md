# 2 Sum. March 22nd, 2018

### Evaluate the value of an arithmetic expression in Reverse Polish Notation.

Valid operators are +, -, *, /. Each operand may be an integer or another expression.

###### Example:

```
["2", "1", "+", "3", "*"] -> ((2 + 1) * 3) -> 9
["4", "13", "5", "/", "+"] -> (4 + (13 / 5)) -> 6
```

###### Thoughts:
* push the element to array when a operand is met; 
pop out the last two elements when operator is met, 
and do the math, then push the result back to the array *

```
function evalRPN(tokens) {
  let offerArr = []
  let a;
  let b;
  let len = tokens.length;
  for(let i = 0; i < len; i ++) {
    switch(tokens[i]) {
      case '+':
        offerArr.push(offerArr.pop() + offerArr.pop());
        break;
      case '*':
        offerArr.push(offerArr.pop() * offerArr.pop());
        break;
      case '-':
        a = offerArr.pop();
        b = offerArr.pop();
        offerArr.push(b - a);
        break;
      case '/':
        a = offerArr.pop();
        b = offerArr.pop();
        offerArr.push(Math.floor(b / a));
        break;
      default:
        offArr.push(Number(token[i]))
        break;
    }
  }

  return offerArr.pop();
}

```

###### Complexity:
The time complexity for this solution will be O(n)
