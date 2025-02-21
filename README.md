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

$T(n)=1 if n ≤ 1 or 3T(n/3) + n^5  if n > 2$

Solve by substitution:


$T(n)= 3T(n/3) + n^5$

      $3(3T(n/9) + n^5) + n^5$
      
      $9T(n/9) + 2n^5$
      
      $27T(n/27) + 3n^5$
      ...
      $3^iT(n/3^i) + i*n^5$
$for i = lg n$
      $nT(1) + n^5*lg n = n+ n^5*lgn ∈ Θ(n^5)$

      
Add your answer to this markdown file. [This
page](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)
might help with the notation for mathematical expressions.
