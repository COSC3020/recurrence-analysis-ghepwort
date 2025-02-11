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

Add your answer to this markdown file. [This
page](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)
might help with the notation for mathematical expressions.



## Answers

$$ T(n) =
    \begin{cases}
        1 & n \leq 1\\
        3T\left(\frac{n}{3}\right) + n^5 & n > 1
    \end{cases}
$$

$T(n) = 3T(\frac{n}3) + n^5$

$T(n) = 3(3T(\frac{n}{3^2}) + \frac{n^5}{3})+ n^5$

$T(n) = 9T(\frac{n}{9}) + 2n^5$

$T(n) = 27T(\frac{n}{27}) + 3n^5$

$T(n) = ...$

$T(n) = 3^iT(\frac{n}{3^i}) + i \cdot n^5$

For $i = log_3n$:

$T(n) = 3^{log_3n}T(\frac{n}{3^{log_3n}}) + log_3n \cdot n^5$

$T(n) = n \cdot T(1) + n^5 \cdot log_3n$

$T(n) = n + 3n^5 \cdot log_3n \in O(n^5)$

This gives us a final time complexity of $O(n^5)$

## Sources
Aidan Newberry and I talked determening if $O(n^5)$ is equivalent to $O(n^2)$. We decided that since they differ by a function of n, they must not be.

I certify that I have listed all sources used to complete this exercise, including the use of any Large Language Models. All of the work is my own, except where stated otherwise. I am aware that plagiarism carries severe penalties and that if plagiarism is suspected, charges may be filed against me without prior notice.