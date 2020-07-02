---
ms.openlocfilehash: aade03c29ff16053a97683499cf719a98ae33f3f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616311"
---
### <a name="add-selectiontextbrush-public-property-to-textboxpasswordbox-non-adorner-selection"></a>TextBox/PasswordBox öğesine SelectionTextBrush ortak özelliği ekleme donatıcı olmayan seçim

#### <a name="details"></a>Ayrıntılar

Ve için [donatıcı tabanlı olmayan metin seçimi](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-TextBox-PasswordBox-text-selection-does-not-follow-system-colors.md) kullanan WPF uygulamalarında <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.PasswordBox> , geliştiriciler artık seçili metnin işlemesini değiştirmek Için yeni eklenen selectiontextbrush özelliğini ayarlayabilir.  Varsayılan olarak, bu renk ile değişir <xref:System.Windows.SystemColors.HighlightTextBrushKey> .  Donatıcı olmayan tabanlı metin seçimi etkinleştirilmemişse, bu özellik hiçbir şey yapmaz.

#### <a name="suggestion"></a>Öneri

Donatıcı olmayan bir metin seçimi etkinleştirildikten sonra, <xref:System.Windows.Controls.PasswordBox.SelectionTextBrush?displayProperty=nameWithType> <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush> Seçilen metnin görünüşünü değiştirmek için ve özelliğini kullanabilirsiniz. Bu, XAML kullanılarak sağlanabilir:

<pre><code class="lang-xaml">&lt;TextBox SelectionBrush=&quot;Red&quot; SelectionTextBrush=&quot;White&quot;  SelectionOpacity=&quot;0.5&quot;&#13;&#10;Foreground=&quot;Blue&quot; CaretBrush=&quot;Blue&quot;&gt;&#13;&#10;This is some text.&#13;&#10;&lt;/TextBox&gt;&#13;&#10;</code></pre>

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Ana       |
| Sürüm | 4,8         |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrushProperty?displayProperty=nameWithType>
- <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush?displayProperty=nameWithType>
- [System. Windows. Controls. TextBox](xref:System.Windows.Controls.TextBox)
- [System. Windows. Controls. PasswordBox](xref:System.Windows.Controls.PasswordBox)
