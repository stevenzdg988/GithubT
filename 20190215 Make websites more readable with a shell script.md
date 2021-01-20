[#]: collector: (lujun9972)
[#]: translator: (stevenzdg988)
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Make websites more readable with a shell script)
[#]: via: (https://opensource.com/article/19/2/make-websites-more-readable-shell-script)
[#]: author: (Jim Hall https://opensource.com/users/jim-hall)

Make websites more readable with a shell script
利用 Shell 脚本让网站更具可读性
======
Calculate the contrast ratio between your website's text and background to make sure your site is easy to read.

测算对比网站文本和背景之间的对比度，以确保站点易于阅读。

![](https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/talk_chat_team_mobile_desktop.png?itok=d7sRtKfQ)

If you want people to find your website useful, they need to be able to read it. The colors you choose for your text can affect the readability of your site. Unfortunately, a popular trend in web design is to use low-contrast colors when printing text, such as gray text on a white background. Maybe that looks really cool to the web designer, but it is really hard for many of us to read.

如果希望人们发现你的网站实用，那么他们需要能够阅读它。为文本选择的颜色可能会影响网站的可读性。不幸的是，网页设计中的一种流行趋势是在打印输出文本时使用低对比度的颜色，就像在白色背景上的灰色文本。对于 Web 设计师来说，这也许看起来很酷，但对于许多阅读它的人来说确实很困难。

The W3C provides Web Content Accessibility Guidelines, which includes guidance to help web designers pick text and background colors that can be easily distinguished from each other. This is called the "contrast ratio." The W3C definition of the contrast ratio requires several calculations: given two colors, you first compute the relative luminance of each, then calculate the contrast ratio. The ratio will fall in the range 1 to 21 (typically written 1:1 to 21:1). The higher the contrast ratio, the more the text will stand out against the background. For example, black text on a white background is highly visible and has a contrast ratio of 21:1. And white text on a white background is unreadable at a contrast ratio of 1:1.

W3C 提供了 Web 内容可访问性指南，其中包括帮助 Web 设计人员选择易于区分文本和背景色的指南。称为“对比度”。 W3C 定义的对比度需要进行一些计算：给定两种颜色，首先计算每种颜色的相对亮度，然后计算对比度。对比度在 1 到 21 的范围内（通常写为1：1到21：1）。对比度越高，文本在背景下的突出程度就越高。例如，白色背景上的黑色文本非常醒目，对比度为 21：1。对比度为 1：1 的白色背景上的白色文本不可读。

The [W3C says body text][1] should have a contrast ratio of at least 4.5:1 with headings at least 3:1. But that seems to be the bare minimum. The W3C also recommends at least 7:1 for body text and at least 4.5:1 for headings.

[W3C 说文本显示][1] 的对比度至少应为 4.5：1，标题至少应为 3：1。但这似乎是最低要求。 W3C 还建议正文至少 7：1，标题至少 4.5：1。

Calculating the contrast ratio can be a chore, so it's best to automate it. I've done that with this handy Bash script. In general, the script does these things:

计算对比度可能比较麻烦，因此最好将其自动化。我已经用这个方便的 Bash 脚本做到了这一点。通常，脚本执行以下操作：

  1. Gets the text color and background color
  2. Computes the relative luminance of each
  3. Calculates the contrast ratio

  1. 获取文本颜色和背景颜色
  2. 计算相对亮度
  3. 计算对比度


### Get the colors
获取颜色

You may know that every color on your monitor can be represented by red, green, and blue (R, G, and B). To calculate the relative luminance of a color, my script will need to know the red, green, and blue components of the color. Ideally, my script would read this information as separate R, G, and B values. Web designers might know the specific RGB code for their favorite colors, but most humans don't know RGB values for the different colors. Instead, most people reference colors by names like "red" or "gold" or "maroon."

你可能知道显示器上的每种颜色都可以用红色，绿色和蓝色（R，G 和 B）表示。要计算颜色的相对亮度，脚本需要知道颜色的红，绿和蓝的各个分量。理想情况下，脚本会将这些信息读取为单独的 R，G 和 B 值。 Web 设计人员可能知道他们喜欢的颜色的特定 RGB 代码，但是大多数人不知道不同颜色的 RGB 值。作为一种替代的方法是，大多数人通过 “红色” 或 “金色” 或 “栗色” 之类的名称来引用颜色。

Fortunately, the GNOME [Zenity][2] tool has a color-picker app that lets you use different methods to select a color, then returns the RGB values in a predictable format of "rgb( **R** , **G** , **B** )". Using Zenity makes it easy to get a color value:

幸运的是，GNOME [Zenity][2] 工具有一个颜色选择器应用程序，可让您使用不同的方法选择颜色，然后用可预测的格式“rgb（**R**，**G**，**B**）” 返回 RGB 值。使用 Zenity 可以轻松获得颜色值：

```
color=$( zenity --title 'Set text color' --color-selection --color='black' )
```

In case the user (accidentally) clicks the Cancel button, the script assumes a color:

如果用户（意外地）单击 “Cancel（取消）” 按钮，脚本将采用一种颜色：

```
if [ $? -ne 0 ] ; then
        echo '** color canceled .. assume black'
        color='rgb(0,0,0)'
fi
```

My script does something similar to set the background color value as **$background**.

我的脚本执行了类似的操作，将背景颜色值设置为 **$background**。
### Compute the relative luminance
计算相对亮度
Once you have the foreground color in **$color** and the background color in **$background** , the next step is to compute the relative luminance for each. On its website, the [W3C provides an algorithm][3] to compute the relative luminance of a color.

一旦您在 **$color** 中设置了前景色，并在 **$background** 中设置了背景色，下一步就是计算每种颜色的相对亮度。 [W3C 提供算法][3] 用以计算颜色的相对亮度。
> For the sRGB colorspace, the relative luminance of a color is defined as
>(对于 sRGB 色彩空间，一种颜色的相对亮度定义为)
>
>  **L = 0.2126 core.md Dict.md lctt2014.md lctt2016.md lctt2018.md LICENSE published README.md scripts sources translated R + 0.7152 core.md Dict.md lctt2014.md lctt2016.md lctt2018.md LICENSE published README.md scripts sources translated G + 0.0722 core.md Dict.md lctt2014.md lctt2016.md lctt2018.md LICENSE published README.md scripts sources translated B** where R, G and B are defined as:(R，G 和 B 定义为:)
>
> if RsRGB <= 0.03928 then R = RsRGB/12.92
>  else R = ((RsRGB+0.055)/1.055) ^ 2.4
>
> if GsRGB <= 0.03928 then G = GsRGB/12.92
>  else G = ((GsRGB+0.055)/1.055) ^ 2.4
>
> if BsRGB <= 0.03928 then B = BsRGB/12.92
>  else B = ((BsRGB+0.055)/1.055) ^ 2.4
>
> and RsRGB, GsRGB, and BsRGB are defined as:
>
>RsRGB, GsRGB, 和 BsRGB 定义为：
>
> RsRGB = R8bit/255
>
> GsRGB = G8bit/255
>
> BsRGB = B8bit/255

Since Zenity returns color values in the format "rgb( **R** , **G** , **B** )," the script can easily pull apart the R, B, and G values to compute the relative luminance. AWK makes this a simple task, using the comma as the field separator ( **-F,** ) and using AWK's **substr()** string function to pick just the text we want from the "rgb( **R** , **G** , **B** )" color value:

由于 Zenity 以 “rgb（**R**，**G**，**B**）”的格式返回颜色值，因此脚本可以轻松拉取分隔开的 R，B 和 G 的值以计算相对亮度。 AWK 使用逗号作为字段分隔符（**-F,**），并使用 **substr()** 字符串函数从 “rgb(**R**，**G**，**B**)中提取所要的颜色值：

```
R=$( echo $color | awk -F, '{print substr($1,5)}' )
G=$( echo $color | awk -F, '{print $2}' )
B=$( echo $color | awk -F, '{n=length($3); print substr($3,1,n-1)}' )
```

**(For more on extracting and displaying data with AWK,[Get our AWK cheat sheet][4].)**

**(有关使用 AWK 提取和显示数据的更多信息，[获取 AWK 备忘表][4].)**

Calculating the final relative luminance is best done using the BC calculator. BC supports the simple if-then-else needed in the calculation, which makes this part simple. But since BC cannot directly calculate exponentiation using a non-integer exponent, we need to do some extra math using the natural logarithm instead:

最好使用 BC 计算器来计算最终的相对亮度。 BC 支持计算中所需的简单 `if-then-else`，这使得这一过程变得简单。 但是由于 BC 无法使用非整数指数直接计算乘幂，因此需要使用自然对数替代它做一些额外的数学运算：

```
echo "scale=4
rsrgb=$R/255
gsrgb=$G/255
bsrgb=$B/255
if ( rsrgb <= 0.03928 ) r = rsrgb/12.92 else r = e( 2.4 core.md Dict.md lctt2014.md lctt2016.md lctt2018.md LICENSE published README.md scripts sources translated l((rsrgb+0.055)/1.055) )
if ( gsrgb <= 0.03928 ) g = gsrgb/12.92 else g = e( 2.4 core.md Dict.md lctt2014.md lctt2016.md lctt2018.md LICENSE published README.md scripts sources translated l((gsrgb+0.055)/1.055) )
if ( bsrgb <= 0.03928 ) b = bsrgb/12.92 else b = e( 2.4 core.md Dict.md lctt2014.md lctt2016.md lctt2018.md LICENSE published README.md scripts sources translated l((bsrgb+0.055)/1.055) )
0.2126 core.md Dict.md lctt2014.md lctt2016.md lctt2018.md LICENSE published README.md scripts sources translated r + 0.7152 core.md Dict.md lctt2014.md lctt2016.md lctt2018.md LICENSE published README.md scripts sources translated g + 0.0722 core.md Dict.md lctt2014.md lctt2016.md lctt2018.md LICENSE published README.md scripts sources translated b" | bc -l
```

This passes several instructions to BC, including the if-then-else statements that are part of the relative luminance formula. BC then prints the final value.

这会将一些指令传递给 BC，包括作为相对亮度公式一部分的 `if-then-else` 语句。接下来 BC 打印出最终值。
### Calculate the contrast ratio
计算对比度

With the relative luminance of the text color and the background color, now the script can calculate the contrast ratio. The [W3C determines the contrast ratio][5] with this formula:

利用文本颜色和背景颜色的相对亮度，脚本就可以计算对比度了。 [W3C 确定对比度][5] 使用以下公式：

> (L1 + 0.05) / (L2 + 0.05), where
>  L1 is the relative luminance of the lighter of the colors, and
>  L2 is the relative luminance of the darker of the colors

> 这里的L1是颜色较浅的相对亮度,
> L2是颜色较深的相对亮度

Given two relative luminance values **$r1** and **$r2** , it's easy to calculate the contrast ratio using the BC calculator:

给定两个相对亮度值 **$r1** 和 **$r2**，使用 BC 计算器很容易计算对比度：

```
echo "scale=2
if ( $r1 > $r2 ) { l1=$r1; l2=$r2 } else { l1=$r2; l2=$r1 }
(l1 + 0.05) / (l2 + 0.05)" | bc
```

This uses an if-then-else statement to determine which value ( **$r1** or **$r2** ) is the lighter or darker color. BC performs the resulting calculation and prints the result, which the script can store in a variable.

使用 `if-then-else` 语句确定哪个值（**$r1** 或 **$r2**）是较浅还是较深的颜色。 BC 执行结果计算并打印结果，脚本可以将其存储在变量中。

### The final script
最终脚本

With the above, we can pull everything together into a final script. I use Zenity to display the final result in a text box:

通过以上内容，我们可以将所有内容整合到一个最终脚本。 我使用 Zenity 在文本框中显示最终结果：

```
#!/bin/sh
# script to calculate contrast ratio of colors

# read color and background color:
# zenity returns values like 'rgb(255,140,0)' and 'rgb(255,255,255)'

color=$( zenity --title 'Set text color' --color-selection --color='black' )
if [ $? -ne 0 ] ; then
        echo '** color canceled .. assume black'
        color='rgb(0,0,0)'
fi

background=$( zenity --title 'Set background color' --color-selection --color='white' )
if [ $? -ne 0 ] ; then
        echo '** background canceled .. assume white'
        background='rgb(255,255,255)'
fi

# compute relative luminance:

function luminance()
{
        R=$( echo $1 | awk -F, '{print substr($1,5)}' )
        G=$( echo $1 | awk -F, '{print $2}' )
        B=$( echo $1 | awk -F, '{n=length($3); print substr($3,1,n-1)}' )

        echo "scale=4
rsrgb=$R/255
gsrgb=$G/255
bsrgb=$B/255
if ( rsrgb <= 0.03928 ) r = rsrgb/12.92 else r = e( 2.4 core.md Dict.md lctt2014.md lctt2016.md lctt2018.md LICENSE published README.md scripts sources translated l((rsrgb+0.055)/1.055) )
if ( gsrgb <= 0.03928 ) g = gsrgb/12.92 else g = e( 2.4 core.md Dict.md lctt2014.md lctt2016.md lctt2018.md LICENSE published README.md scripts sources translated l((gsrgb+0.055)/1.055) )
if ( bsrgb <= 0.03928 ) b = bsrgb/12.92 else b = e( 2.4 core.md Dict.md lctt2014.md lctt2016.md lctt2018.md LICENSE published README.md scripts sources translated l((bsrgb+0.055)/1.055) )
0.2126 core.md Dict.md lctt2014.md lctt2016.md lctt2018.md LICENSE published README.md scripts sources translated r + 0.7152 core.md Dict.md lctt2014.md lctt2016.md lctt2018.md LICENSE published README.md scripts sources translated g + 0.0722 core.md Dict.md lctt2014.md lctt2016.md lctt2018.md LICENSE published README.md scripts sources translated b" | bc -l
}

lum1=$( luminance $color )
lum2=$( luminance $background )

# compute contrast

function contrast()
{
        echo "scale=2
if ( $1 > $2 ) { l1=$1; l2=$2 } else { l1=$2; l2=$1 }
(l1 + 0.05) / (l2 + 0.05)" | bc
}

rel=$( contrast $lum1 $lum2 )

# print results

( cat<<EOF
Color is $color on $background

Contrast ratio is $rel
Contrast ratios can range from 1 to 21 (commonly written 1:1 to 21:1).

EOF

if [ ${rel%.*} -ge 4 ] ; then
        echo "Ok for body text"
else
        echo "Not good for body text"
fi
if [ ${rel%.*} -ge 3 ] ; then
        echo "Ok for title text"
else
        echo "Not good for title text"
fi

cat<<EOF

The W3C says this:
W3C这样说：
1.4.3 Contrast (Minimum): The visual presentation of text and images of text has a contrast ratio of at least 4.5:1, except for the following: (Level AA)
1.4.3 对比度（最小值）：文本和文本图像的视觉呈现方式的对比度至少为4.5：1，但以下情况除外：（AA级）
    Large Text: Large-scale text and images of large-scale text have a contrast ratio of at least 3:1;
大文本：大文本和大文本图像的对比度至少为 3：1；
    Incidental: Text or images of text that are part of an inactive user interface component, that are pure decoration, that are not visible to anyone, or that are part of a picture that contains significant other visual content, have no contrast requirement.
附带说明：作为非活动用户界面组件一部分，纯装饰的，任何人都不可见或图片的一部分包含特定的其他可视内容的文本或文本图像没有对比度要求。
    Logotypes: Text that is part of a logo or brand name has no minimum contrast requirement.
小示意图：徽标或商标名称中的文本没有最低对比度要求。
and:

1.4.6 Contrast (Enhanced): The visual presentation of text and images of text has a contrast ratio of at least 7:1, except for the following: (Level AAA)
1.4.6 对比度（增强）：文本和文本图像的视觉表示具有至少 7：1 的对比度，但以下情况除外：（AAA级）
    Large Text: Large-scale text and images of large-scale text have a contrast ratio of at least 4.5:1;
大文本：大文本和大文本图像的对比度至少为 4.5：1；
    Incidental: Text or images of text that are part of an inactive user interface component, that are pure decoration, that are not visible to anyone, or that are part of a picture that contains significant other visual content, have no contrast requirement.
附带说明：作为非活动用户界面组件一部分，纯装饰的，任何人都不可见或图片的一部分包含特定的其他可视内容的文本或文本图像没有对比度要求。
    Logotypes: Text that is part of a logo or brand name has no minimum contrast requirement.
小示意图：徽标或商标名称中的文本没有最低对比度要求。
EOF
) | zenity --text-info --title='Relative Luminance' --width=800 --height=600
```

At the end, I like to include reference information about the W3C recommendations as a reminder for myself.

最后，我希望提供有关 W3C 建议的参考信息，以提醒自己。

The Zenity color picker does all the hard work of interpreting colors, which the user can select by clicking in the color wheel or by entering a value. Zenity accepts standard hex color values used on websites, like #000000 or #000 or rgb(0,0,0) (all of those are black). Here's an example calculation for black text on a white background:

Zenity 颜色选择器完成了所有解释颜色的艰苦工作，用户可以通过单击色轮或输入值来选择颜色。 Zenity 接受网站上使用的标准十六进制颜色值，例如 `＃000000` 或 `＃000`或 `rgb（0,0,0）`（所有这些均为黑色）。这是白色背景上的黑色文本的示例计算：

![](https://opensource.com/sites/default/files/uploads/zenity_screenshot1-a.png)

![](https://opensource.com/sites/default/files/uploads/zenity_screenshot1-b.png)

![](https://opensource.com/sites/default/files/uploads/relativeluminescence1-result.png)

Zenity also understands standard color names like cadetblue or orange or gold. Enter the color name in Zenity then hit Tab, and Zenity will convert the color name into a hex color value, as in this example calculation for black text on a gold background:

Zenity 还识别标准的颜色名称，如深蓝色，橙色或金色。在Zenity 中输入颜色名称，然后点击 Tab 键，Zenity 会将颜色名称转换为十六进制颜色值，如以下示例中对金色背景上的黑色文本的计算：

![](https://opensource.com/sites/default/files/uploads/zenity_screenshot2-a-name.png)

![](https://opensource.com/sites/default/files/uploads/zenity_screenshot2-a-value.png)

![](https://opensource.com/sites/default/files/uploads/zenity_screenshot2-b-name.png)

![](https://opensource.com/sites/default/files/uploads/zenity_screenshot2-b-value.png)

![](https://opensource.com/sites/default/files/uploads/relativeluminescence2-result.png)

--------------------------------------------------------------------------------

via: https://opensource.com/article/19/2/make-websites-more-readable-shell-script

作者：[Jim Hall][a]
选题：[lujun9972][b]
译者：[stevenzdg988](https://github.com/stevenzdg988)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/jim-hall
[b]: https://github.com/lujun9972
[1]: https://www.w3.org/TR/2008/REC-WCAG20-20081211/#visual-audio-contrast
[2]: https://wiki.gnome.org/Projects/Zenity
[3]: https://www.w3.org/TR/2008/REC-WCAG20-20081211/#relativeluminancedef
[4]: https://opensource.com/article/18/7/cheat-sheet-awk
[5]: https://www.w3.org/TR/2008/REC-WCAG20-20081211/#contrast-ratiodef
