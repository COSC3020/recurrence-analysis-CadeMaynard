[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-718a45dd9cf7e7f842a935f5ebbe5719a5e09af4491e668f4dbf3b35d5cca122.svg)](https://classroom.github.com/online_ide?assignment_repo_id=12089768&assignment_repo_type=AssignmentRepo)
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

## My solution:

$T(n)=1$ If $n \leq 1$, $3T(n/3)+n^5$ If $n>1$
<br>
<br>
$3T(\frac{n}{3})+n^5$
<br>
<br>
$9T(\frac{n}{9})+n^5+\frac{n^5}{3^4}$
<br>
<br>
$27T(\frac{n}{27})+n^5+\frac{n^5}{3^4}+\frac{n^5}{9^4}$
<br>
<br>
### Relation
$i$: Iterations
<br>
$3^iT(\frac{n}{3^i})+{n^5\sum_{n=1}}^i(\frac{1}{3})^{4n}$
<br>
$i = log_3n$
<br>
<br>
$nT(1)+{n^5\sum_{n=1}}^{log_3n}(\frac{1}{3})^{4n}$ the sum with $log_3n$ is a constant and in the context of asymptotic compexity, can be ignored. Higher order terms can also be ignored.
<br>
<br>
$T(1)+{n^5}$
<br>
$T(1)+{n^5}\in\Theta(n^5log_3n)$
