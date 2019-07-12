---
ms.openlocfilehash: 01bbc49cb0febc5a29dafc7c311b848387a4094a
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803525"
---
### <a name="add-selectiontextbrush-public-property-to-textboxpasswordbox-non-adorner-selection"></a>Metin/PasswordBox donatıcı olmayan seçime SelectionTextBrush ortak özelliği Ekle

|   |   |
|---|---|
|Ayrıntılar|Kullanarak WPF uygulamalarında [donatıcı olmayan metin seçimi temel](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-TextBox-PasswordBox-text-selection-does-not-follow-system-colors.md) için <xref:System.Windows.Controls.TextBox> ve <xref:System.Windows.Controls.PasswordBox>, geliştiricilerin artık yeni eklenen SelectionTextBrush özelliğini ayarlayın seçili metni işlenmesini değiştirmek için.  Varsayılan olarak, bu renk ile değiştirir. <xref:System.Windows.SystemColors.HighlightTextBrushKey>.  Donatıcı olmayan temel metin seçimi etkin değil, bu özellik, işlem gerçekleştirmez.|
|Öneri|Donatıcı olmayan temel sonra metin seçimi etkin, kullanabileceğiniz <xref:System.Windows.Controls.PasswordBox.SelectionTextBrush?displayProperty=nameWithType> ve <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush> seçili metin görünümünü değiştirmek için özellik. Bu, XAML kullanarak gerçekleştirilebilir:<pre><code class="lang-xaml">&lt;TextBox SelectionBrush=&quot;Red&quot; SelectionTextBrush=&quot;White&quot;  SelectionOpacity=&quot;0.5&quot;&#13;&#10;Foreground=&quot;Blue&quot; CaretBrush=&quot;Blue&quot;&gt;&#13;&#10;This is some text.&#13;&#10;&lt;/TextBox&gt;&#13;&#10;</code></pre>|
|Kapsam|Ana|
|Sürüm|4.8|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrushProperty?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush?displayProperty=nameWithType></li><li>[System.Windows.Controls.TextBox](xref:System.Windows.Controls.TextBox)</li><li>[System.Windows.Controls.PasswordBox](xref:System.Windows.Controls.PasswordBox)</li></ul>|

