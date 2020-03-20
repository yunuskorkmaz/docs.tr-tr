---
ms.openlocfilehash: e04134ec731c5e7bede3388621078c6518805ec2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803525"
---
### <a name="add-selectiontextbrush-public-property-to-textboxpasswordbox-non-adorner-selection"></a>TextBox/PasswordBox olmayan adorner seçimine SelectionTextBrush kamu mülkiyeti ekle

|   |   |
|---|---|
|Ayrıntılar|WPF uygulamalarında, kapiçin ve için <xref:System.Windows.Controls.TextBox> [adorner tabanlı metin seçimi](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-TextBox-PasswordBox-text-selection-does-not-follow-system-colors.md) <xref:System.Windows.Controls.PasswordBox>kullanarak, geliştiriciler artık seçili metnin işlenmesini değiştirmek için yeni eklenen SelectionTextBrush özelliğini ayarlayabilir.  Varsayılan olarak, bu <xref:System.Windows.SystemColors.HighlightTextBrushKey>renk .  Adorner tabanlı olmayan metin seçimi etkinleştirilemezse, bu özellik hiçbir şey yapmaz.|
|Öneri|Adorner tabanlı olmayan metin seçimi etkinleştirildikten <xref:System.Windows.Controls.PasswordBox.SelectionTextBrush?displayProperty=nameWithType> sonra, seçili metnin görünümünü değiştirmek için bu özelliği ve <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush> özelliği kullanabilirsiniz. Bu XAML kullanılarak elde edilebilir:<pre><code class="lang-xaml">&lt;TextBox SelectionBrush=&quot;Red&quot; SelectionTextBrush=&quot;White&quot;  SelectionOpacity=&quot;0.5&quot;&#13;&#10;Foreground=&quot;Blue&quot; CaretBrush=&quot;Blue&quot;&gt;&#13;&#10;This is some text.&#13;&#10;&lt;/TextBox&gt;&#13;&#10;</code></pre>|
|Kapsam|Ana|
|Sürüm|4.8|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrushProperty?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush?displayProperty=nameWithType></li><li>[System.Windows.Controls.TextBox](xref:System.Windows.Controls.TextBox)</li><li>[System.Windows.Controls.PasswordBox](xref:System.Windows.Controls.PasswordBox)</li></ul>|
