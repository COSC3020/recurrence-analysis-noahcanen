# Recurrence Analysis -- Mystery Function

Analyze the running time of the following recursive procedure as a function of
$n$ and find a tight big $O$ bound on the runtime for the function. You may
assume that each operation takes unit time. You do not need to provide a formal
proof, but you should show your work: at a minimum, show the recurrence relation
you derive for the runtime of the code, and then how you solved the recurrence
relation.

```javascript
function mystery(n) {
    if(n <= 1)
        return;
    else {
        mystery(n / 3);
        var count = 0;
        mystery(n / 3);
        for(var i = 0; i < n*n; i++) {
            for(var j = 0; j < n; j++) {
                for(var k = 0; k < n*n; k++) {
                    count = count + 1;
                }
            }
        }
        mystery(n / 3);
    }
}
```

Recurrence relation:

T(n)=1 if n ≤ 1 or 3T(n/3) + $n^5$  if n > 1

Solve by substitution:


$T(n)= 3T(n/3) + n^5$

3(3T(n/9) + (n/3)^5) + n^5$
      
9T(n/9) + 3(n/3)^5 + n^5

9(3T(n/27) + (n/9)^5) + 3(n/3)^5 + n^5

27T(n/27) + 9(n/9)^5 + 3(n/3)^5 + n^5

27( 3T(n/81) + n^5) + 9(n/9)^5 + 3(n/3)^5 + n^5

81T(n/81) + 27(n/81)^5 + 9(n/9)^5 + 3(n/3)^5 + n^5

 ...
 
3^iT(n/3^i) + 3^(i-1)(n/3^(i-1))^5 + 3^(i-2)(n/3^(i-2))^5 + ...+ 3^(i-(i-1))(n/3^(i-(i-1)))^5 + $n^5$

$3^iT(n/3^i) + n^5 \sum_{k=o}^{lg n-1}(1/3^4)^k $

for i = lg n

$nT(1) + n^5 ∈ O(n^5)$

      
Add your answer to this markdown file. [This page](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)
might help with the notation for mathematical expressions.

For this assignment, I was able to do it entirely on my own with help from the TA.

"I certify that I have listed all sources used to complete this exercise, including the use of any Large Language Models. All of the work is my own, except where stated otherwise. I am aware that plagiarism carries severe penalties and that if plagiarism is suspected, charges may be filed against me without prior notice."

