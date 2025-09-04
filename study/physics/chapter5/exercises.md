# 习题练习

## **习题1（干涉）**：

在杨氏双缝干涉实验中，所用单色光的波长 $\lambda = 550 \text{ nm}$，双缝间距 $d = 0.22 \text{ mm}$，屏到双缝的距离 $D = 1.0 \text{ m}$。求：

(1) 中央明条纹两侧的第一条明条纹到中心的距离；

:::details 解析

第一条明条纹对应 $k=1$。其到中心的距离为：
$$ x_1 = \frac{D}{d} \cdot 1 \cdot \lambda = \frac{1.0 \text{ m}}{0.22 \times 10^{-3} \text{ m}} \times (550 \times 10^{-9} \text{ m}) = 2.5 \times 10^{-3} \text{ m} = 2.5 \text{ mm} $$

:::

(2) 屏上干涉条纹的间距。

:::details 解析

屏上干涉条纹的间距等于第一条明条纹到中心的距离，即：
$$ \Delta x = x_1 = 2.5 \text{ mm} $$

:::

## **例题2（衍射）**：

一束波长为 $600 \text{ nm}$ 的平行单色光，垂直投射到一宽度为 $a = 0.3 \text{ mm}$ 的单缝上，缝后置一焦距为 $f = 50 \text{ cm}$ 的凸透镜。求：

在透镜焦平面上中央明条纹的宽度。

::: details 解析

中央明条纹的边界是第一级暗纹 ($k=1$)。根据单缝衍射的暗纹条件 $a\sin\theta = k\lambda$，第一级暗纹的衍射角 $\theta_1$ 满足：
$$ a\sin\theta_1 = \lambda $$
$$ \sin\theta_1 = \frac{\lambda}{a} = \frac{600 \times 10^{-9} \text{ m}}{0.3 \times 10^{-3} \text{ m}} = 2.0 \times 10^{-3} $$
由于 $\theta_1$ 很小，可以认为 $\sin\theta_1 \approx \tan\theta_1$。
中央明条纹的半宽度为 $x_1 = f \tan\theta_1 \approx f \sin\theta_1$。
因此，中央明条纹的总宽度为 $W = 2x_1 \approx 2f\sin\theta_1$。
$$ W = 2 \times (0.5 \text{ m}) \times (2.0 \times 10^{-3}) = 2.0 \times 10^{-3} \text{ m} = 2.0 \text{ mm} $$

:::

## **例题3（偏振）**：

两块偏振片的透振方向成 $45^\circ$ 角。强度为 $I_0$ 的自然光垂直入射到第一块偏振片上，求：

通过两块偏振片后的光强。

::: details 解析

自然光通过第一块偏振片（起偏器）后，光强变为 $I_1 = \frac{1}{2}I_0$，且变为线偏振光。
这束线偏振光通过第二块偏振片（检偏器）时，根据马吕斯定律，其透射光强为 $I_2$。此时，入射光强为 $I_1$，夹角 $\theta = 45^\circ$。
$$ I_2 = I_1 \cos^2(45^\circ) = \left(\frac{1}{2}I_0\right) \left(\frac{\sqrt{2}}{2}\right)^2 = \left(\frac{1}{2}I_0\right) \left(\frac{1}{2}\right) = \frac{1}{4}I_0 $$
因此，通过两块偏振片后的光强为 $\frac{1}{4}I_0$。

:::