## 均勻分布 (Uniform distribution)

意義：在範圍 (a,b) 內的出現機會均等。

R 函數：[unif(a:min, b:max)](http://sites.stat.psu.edu/~dhunter/R/html/stats/html/Uniform.html)

課本公式：$f(x) = \frac{1}{b-a}$

R 的公式：f(x) = 1/(max-min)

變數意義：a:min 範圍下限, b:max 上限

### R 程式範例

```R
> op=par(mfrow=c(2,2))
> curve(dunif(x, 0, 1), -2, 10)
> curve(dunif(x, 1, 5), -2, 10)
> curve(dunif(x, -1, 9), -2, 10)
> curve(dunif(x, 10, 110), 0, 200)
>
```

![](dunifCurve4.jpg)
