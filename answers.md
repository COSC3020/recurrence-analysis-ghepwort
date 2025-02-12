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