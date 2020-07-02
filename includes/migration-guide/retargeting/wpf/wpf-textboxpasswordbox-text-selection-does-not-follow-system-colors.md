---
ms.openlocfilehash: 7c2e80669d9ef27f87cde9442d8eeab0ee31a524
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614982"
---
### <a name="wpf-textboxpasswordbox-text-selection-does-not-follow-system-colors"></a><span data-ttu-id="baa93-101">WPF metin kutusu/PasswordBox metin seçimi sistem renklerini Izlemez</span><span class="sxs-lookup"><span data-stu-id="baa93-101">WPF TextBox/PasswordBox Text Selection Does Not Follow System Colors</span></span>

#### <a name="details"></a><span data-ttu-id="baa93-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="baa93-102">Details</span></span>

<span data-ttu-id="baa93-103">.NET Framework 4.7.1 ve önceki sürümlerinde, WPF `System.Windows.Controls.TextBox` ve `System.Windows.Controls.PasswordBox` yalnızca donatıcı katmanında bir metin seçimi işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="baa93-103">In .NET Framework 4.7.1 and earlier versions, WPF `System.Windows.Controls.TextBox` and `System.Windows.Controls.PasswordBox` could only render a text selection in the Adorner layer.</span></span> <span data-ttu-id="baa93-104">Bazı sistem temaları 'nda bu metin, bu şekilde okunabilir ve okunması zor hale gelir.</span><span class="sxs-lookup"><span data-stu-id="baa93-104">In some system themes this would occlude text, making it hard to read.</span></span>  <span data-ttu-id="baa93-105">.NET Framework 4.7.2 ve sonraki sürümlerde, geliştiricilerin bu sorunu konuma almayı azaltır olan donatıcı olmayan bir seçim işleme düzenini etkinleştirme seçeneği vardır.</span><span class="sxs-lookup"><span data-stu-id="baa93-105">In .NET Framework 4.7.2 and later, developers have an option of enabling a non-Adorner-based selection rendering scheme that alleviates this issue.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="baa93-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="baa93-106">Suggestion</span></span>

<span data-ttu-id="baa93-107">Bu değişikliği kullanmak isteyen bir geliştirici aşağıdaki AppContext bayrağını uygun şekilde ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="baa93-107">A developer who wants to utilize this change must set the following AppContext flag appropriately.</span></span>  <span data-ttu-id="baa93-108">Bu özelliği kullanmak için, yüklü .NET Framework sürümü 4.7.2 veya daha büyük olmalıdır. Donatıcı olmayan tabanlı seçimi etkinleştirmek için aşağıdaki AppContext bayrağını kullanın.</span><span class="sxs-lookup"><span data-stu-id="baa93-108">To utilize this feature, the installed .NET Framework version must be 4.7.2 or greater.To enabled the non-adorner-based selection, use the following AppContext flag.</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Text.UseAdornerForTextboxSelectionRendering=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="baa93-109">Name</span><span class="sxs-lookup"><span data-stu-id="baa93-109">Name</span></span>    | <span data-ttu-id="baa93-110">Değer</span><span class="sxs-lookup"><span data-stu-id="baa93-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="baa93-111">Kapsam</span><span class="sxs-lookup"><span data-stu-id="baa93-111">Scope</span></span>   | <span data-ttu-id="baa93-112">Edge</span><span class="sxs-lookup"><span data-stu-id="baa93-112">Edge</span></span>        |
| <span data-ttu-id="baa93-113">Sürüm</span><span class="sxs-lookup"><span data-stu-id="baa93-113">Version</span></span> | <span data-ttu-id="baa93-114">4.7.2</span><span class="sxs-lookup"><span data-stu-id="baa93-114">4.7.2</span></span>       |
| <span data-ttu-id="baa93-115">Tür</span><span class="sxs-lookup"><span data-stu-id="baa93-115">Type</span></span>    | <span data-ttu-id="baa93-116">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="baa93-116">Retargeting</span></span> |
