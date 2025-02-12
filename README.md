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

$T(\frac{n}{3}) = 3T(\frac{n}{9})+(\frac{n}{3})^5$

$T(n) = 3(3T(\frac{n}{9})+(\frac{n}{3})^5)+n^5$

$T(n) = 9T(\frac{n}{9})+n^5+\frac{n^5}{81}$

$T(\frac{n}{9}) = 3T(\frac{n}{27}) +  (\frac{n}{9})^5$

$T(n) = 9(3T(\frac{n}{27})+(\frac{n}{9})^5) + n^5+\frac{n^5}{81}$

$T(n) = 27T(\frac{n}{27}) + n^5 + \frac{n^5}{3^4} + \frac{n^5}{9^4}$

$T(n) = ...$

$T(n) = 3^iT(\frac{n}{3^i}) + n^5 + \frac{n^5}{3^4} + \frac{n^5}{3^8} + \frac{n^5}{3^{12}} ...$

$T(n) = 3^iT(\frac{n}{3^i}) + \sum_{k = 0}^{i - 1}{\frac{n^5}{3^{4i}}}$

The series $\sum_{k = 0}^{i - 1}{\frac{n^5}{3^{4i}}}$ is a geometric sum so we can solve $\sum_{k = 0}^{i - 1}{\frac{n^5}{3^{4i}}} = \frac{n^5}{1-\frac{1}{3^4}} = \frac{n^5}{\frac{80}{81}} = \frac{81n^5}{80}$

Substituting the value of the series we get:

$T(n) = 3^iT(\frac{n}{3^i}) + \frac{81n^5}{80}$

For $i = log_3n$:

$T(n) = 3^{log_3n}T(\frac{n}{3^{log_3n}}) + \frac{81n^5}{80}$

$T(n) = n \cdot T(1) + \frac{81n^5}{80}$

$T(n) = n + \frac{81n^5}{80} \in O(n^5)$

This gives us a final time complexity of $O(n^5)$


## Sources
Aidan Newberry and I talked determening if $O(n^5)$ is equivalent to $O(n^2)$. We decided that since they differ by a function of n, they must not be.

I used [Chilimath.com](https://www.chilimath.com/lessons/advanced-algebra/infinite-geometric-series-formula/) to help remind myself on how to do an infinite geometric sum.

I certify that I have listed all sources used to complete this exercise, including the use of any Large Language Models. All of the work is my own, except where stated otherwise. I am aware that plagiarism carries severe penalties and that if plagiarism is suspected, charges may be filed against me without prior notice.

