# H3:ZUC
## H3_1 Compute the DDT and LAT tables of ZUC S0 and S1
### 设计思路
#### 差分密码分析
差分密码分析是迄今已知的攻击迭代密码最有效的方法之一，其基本思想实：通过分析明文对的差值对密文对的差值的影响来恢复某些密钥比特。
ZUC算法的S-Box 是8 × 8 的 输入，所以x 和 y的差分取值在[0, 255]区间。DDT的计算用python3实现，如下所示：
```python
SBOX to DDT
    for p1 in range(256)
      for p2 in range(256)
        XOR_IN = p1 ^ p2
        XOR_OUT = sbox[p1] ^ sbox[p2]
```
#### 线性密码分析
线性密码分析是对迭代密码的一种已知明文攻击，它利用的是密码算法中的”不平衡（有效）的线性逼近“。
ZUC算法的S-Box 是8 × 8 的 输入，所以x 和 y的差分取值在[0, 255]区间。LAT的计算用python3实现，如下所示：
```python
SBOX to LAT
    for a in range(256)
      for b in range(256)
        for i in range(256)
          LAT[a][b] += a.i ^ b.sbox_val[i]
```
### 实验结果
S0 DDT IN Result/Re_ZUC_DDT_S0.xls
S1 DDT IN Result/Re_ZUC_DDT_S1.xls
S0 LAT IN Result/Re_ZUC_LAT_S0.xls
S1 LAT IN Result/Re_ZUC_LAT_S1.xls
<br>
## H3_2 Answer shy a final key mixing is required by a cipher?
如果最后不进行一轮mixing,由于S盒已知，Permutation是不安全的，攻击者不需要密钥也能够还原一轮，降低了密码破解的复杂度。


