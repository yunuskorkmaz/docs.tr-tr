---
ms.openlocfilehash: aade03c29ff16053a97683499cf719a98ae33f3f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616311"
---
### <a name="add-selectiontextbrush-public-property-to-textboxpasswordbox-non-adorner-selection"></a><span data-ttu-id="a16cb-101">TextBox/PasswordBox öğesine SelectionTextBrush ortak özelliği ekleme donatıcı olmayan seçim</span><span class="sxs-lookup"><span data-stu-id="a16cb-101">Add SelectionTextBrush public property to TextBox/PasswordBox non-adorner selection</span></span>

#### <a name="details"></a><span data-ttu-id="a16cb-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="a16cb-102">Details</span></span>

<span data-ttu-id="a16cb-103">Ve için [donatıcı tabanlı olmayan metin seçimi](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-TextBox-PasswordBox-text-selection-does-not-follow-system-colors.md) kullanan WPF uygulamalarında <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.PasswordBox> , geliştiriciler artık seçili metnin işlemesini değiştirmek Için yeni eklenen selectiontextbrush özelliğini ayarlayabilir.</span><span class="sxs-lookup"><span data-stu-id="a16cb-103">In WPF applications using [non-adorner based text selection](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-TextBox-PasswordBox-text-selection-does-not-follow-system-colors.md) for <xref:System.Windows.Controls.TextBox> and <xref:System.Windows.Controls.PasswordBox>, developers may now set the newly added SelectionTextBrush property in order to alter the rendering of the selected text.</span></span>  <span data-ttu-id="a16cb-104">Varsayılan olarak, bu renk ile değişir <xref:System.Windows.SystemColors.HighlightTextBrushKey> .</span><span class="sxs-lookup"><span data-stu-id="a16cb-104">By default, this color changes with <xref:System.Windows.SystemColors.HighlightTextBrushKey>.</span></span>  <span data-ttu-id="a16cb-105">Donatıcı olmayan tabanlı metin seçimi etkinleştirilmemişse, bu özellik hiçbir şey yapmaz.</span><span class="sxs-lookup"><span data-stu-id="a16cb-105">If non-adorner based text selection is not enabled, this property does nothing.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a16cb-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="a16cb-106">Suggestion</span></span>

<span data-ttu-id="a16cb-107">Donatıcı olmayan bir metin seçimi etkinleştirildikten sonra, <xref:System.Windows.Controls.PasswordBox.SelectionTextBrush?displayProperty=nameWithType> <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush> Seçilen metnin görünüşünü değiştirmek için ve özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a16cb-107">Once non-adorner based text selection is enabled, you can use the <xref:System.Windows.Controls.PasswordBox.SelectionTextBrush?displayProperty=nameWithType> and <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush> property to change the appearance of the selected text.</span></span> <span data-ttu-id="a16cb-108">Bu, XAML kullanılarak sağlanabilir:</span><span class="sxs-lookup"><span data-stu-id="a16cb-108">This can be achieved using XAML:</span></span>

<pre><code class="lang-xaml">&lt;TextBox SelectionBrush=&quot;Red&quot; SelectionTextBrush=&quot;White&quot;  SelectionOpacity=&quot;0.5&quot;&#13;&#10;Foreground=&quot;Blue&quot; CaretBrush=&quot;Blue&quot;&gt;&#13;&#10;This is some text.&#13;&#10;&lt;/TextBox&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="a16cb-109">Name</span><span class="sxs-lookup"><span data-stu-id="a16cb-109">Name</span></span>    | <span data-ttu-id="a16cb-110">Değer</span><span class="sxs-lookup"><span data-stu-id="a16cb-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a16cb-111">Kapsam</span><span class="sxs-lookup"><span data-stu-id="a16cb-111">Scope</span></span>   | <span data-ttu-id="a16cb-112">Ana</span><span class="sxs-lookup"><span data-stu-id="a16cb-112">Major</span></span>       |
| <span data-ttu-id="a16cb-113">Sürüm</span><span class="sxs-lookup"><span data-stu-id="a16cb-113">Version</span></span> | <span data-ttu-id="a16cb-114">4,8</span><span class="sxs-lookup"><span data-stu-id="a16cb-114">4.8</span></span>         |
| <span data-ttu-id="a16cb-115">Tür</span><span class="sxs-lookup"><span data-stu-id="a16cb-115">Type</span></span>    | <span data-ttu-id="a16cb-116">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="a16cb-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="a16cb-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="a16cb-117">Affected APIs</span></span>

- <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrushProperty?displayProperty=nameWithType>
- <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush?displayProperty=nameWithType>
- [<span data-ttu-id="a16cb-118">System. Windows. Controls. TextBox</span><span class="sxs-lookup"><span data-stu-id="a16cb-118">System.Windows.Controls.TextBox</span></span>](xref:System.Windows.Controls.TextBox)
- [<span data-ttu-id="a16cb-119">System. Windows. Controls. PasswordBox</span><span class="sxs-lookup"><span data-stu-id="a16cb-119">System.Windows.Controls.PasswordBox</span></span>](xref:System.Windows.Controls.PasswordBox)
