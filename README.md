# chi二乗検定と、fisherの正確検定
chi二乗検定と、fisherの正確検定について知見と使い方とか

## fisherの正確検定
考え方としてはノンパラメトリックなんだけど、一個一個のマトリックスの事象が”平等に起こり得る”という帰無仮説を立てると、次のように簡単に組み合わせ表現にすることができる  
<p align="center">
  <img width="150px" src="https://user-images.githubusercontent.com/4949982/36095701-a5f35a36-1036-11e8-8748-7c3b62a265c1.png">
</p>
例.４の目を仮定

<p align="center">
  <img width="350px" src="https://user-images.githubusercontent.com/4949982/36095653-6df7e584-1036-11e8-9530-a157984f0d01.png">
</p>
ある組み合わせが起こりうる頻度

これをpythonでコーディングするとこのようになる  
```python
import math

# web良かった、web悪かった, SI良かった, SI悪かった
a,b,c,d = [5,1,1,6]

ps = []
for a in range(0, 6 + 1):
  b = 6 - a
  c = 6 - a
  d = 7 - b
  ps.append( (a,b,c,d) )

  s = math.factorial( a+b ) * \
  math.factorial( a+c ) * \
  math.factorial( b+d ) * \
  math.factorial( c+d ) / ( math.factorial(a) * \
    math.factorial(b) * \
    math.factorial(c) * \
    math.factorial(d) * math.factorial(a+b+c+d) )
  print(a, s)
print(ps)
```
これを行うと山状の形を自由度に応じて得ることができて、山の面積の95%以外にあればそれは自然に起きたことではないという解釈が成り立ちそうである  
<p align="center">
  <img width="450px" src="https://user-images.githubusercontent.com/4949982/36096096-2d6a7110-1038-11e8-92e5-9591c030aaa5.png">
</p>

これをもってして有効か無効かという視点では、なにかしらバイアスがあって平等に起こり得るという状態が否決されたと見させそうです  
