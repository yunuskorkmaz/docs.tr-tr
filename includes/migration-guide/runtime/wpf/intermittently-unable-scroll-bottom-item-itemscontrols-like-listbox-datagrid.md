---
ms.openlocfilehash: bca76daca6e9c424377a80aa56e1a5ff191be5ca
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497157"
---
### <a name="intermittently-unable-to-scroll-to-bottom-item-in-itemscontrols-like-listbox-and-datagrid-when-using-custom-datatemplates"></a><span data-ttu-id="c28a8-101">Özel veri şablonları kullanılırken, ara sıra ıtemcontrols (ListBox ve DataGrid gibi) alt öğeye kaydırılamıyor</span><span class="sxs-lookup"><span data-stu-id="c28a8-101">Intermittently unable to scroll to bottom item in ItemsControls (like ListBox and DataGrid) when using custom DataTemplates</span></span>

#### <a name="details"></a><span data-ttu-id="c28a8-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="c28a8-102">Details</span></span>

<span data-ttu-id="c28a8-103">Bazı örneklerde, 4,5 .NET Framework bir hata, ıtemcontrols (gibi,, <xref:System.Windows.Controls.ListBox?displayProperty=fullName> <xref:System.Windows.Controls.ComboBox?displayProperty=fullName> <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> vb.), özel veri şablonları kullanırken kendi alt öğelerini kaydırmamasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="c28a8-103">In some instances, a bug in the .NET Framework 4.5 is causing ItemsControls (like <xref:System.Windows.Controls.ListBox?displayProperty=fullName>, <xref:System.Windows.Controls.ComboBox?displayProperty=fullName>, <xref:System.Windows.Controls.DataGrid?displayProperty=fullName>, etc.) to not scroll to their bottom item when using custom DataTemplates.</span></span> <span data-ttu-id="c28a8-104">Kaydırmanın ikinci kez denendiğinde (geri alındıktan sonra), daha sonra çalışır.</span><span class="sxs-lookup"><span data-stu-id="c28a8-104">If the scrolling is attempted a second time (after scrolling back up), it will work then.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c28a8-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="c28a8-105">Suggestion</span></span>

<span data-ttu-id="c28a8-106">Bu sorun .NET Framework 4.5.2 düzeltilmiştir ve bu sürüme (veya sonraki bir sürüme) yükselterek .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c28a8-106">This issue has been fixed in the .NET Framework 4.5.2 and may be addressed by upgrading to that version (or a later version) of the .NET Framework.</span></span> <span data-ttu-id="c28a8-107">Alternatif olarak, kullanıcılar kaydırma çubuklarını bu koleksiyonlardaki son öğelere sürüklemeye devam edebilir, ancak bunu iki kez denemek gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="c28a8-107">Alternatively, users can still drag scroll bars to the final items in these collections, but may need to try twice to do so successfully.</span></span>

| <span data-ttu-id="c28a8-108">Name</span><span class="sxs-lookup"><span data-stu-id="c28a8-108">Name</span></span>    | <span data-ttu-id="c28a8-109">Değer</span><span class="sxs-lookup"><span data-stu-id="c28a8-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c28a8-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="c28a8-110">Scope</span></span>   |<span data-ttu-id="c28a8-111">İkincil</span><span class="sxs-lookup"><span data-stu-id="c28a8-111">Minor</span></span>|
|<span data-ttu-id="c28a8-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="c28a8-112">Version</span></span>|<span data-ttu-id="c28a8-113">4,5</span><span class="sxs-lookup"><span data-stu-id="c28a8-113">4.5</span></span>|
|<span data-ttu-id="c28a8-114">Tür</span><span class="sxs-lookup"><span data-stu-id="c28a8-114">Type</span></span>|<span data-ttu-id="c28a8-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="c28a8-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="c28a8-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="c28a8-116">Affected APIs</span></span>

<span data-ttu-id="c28a8-117">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="c28a8-117">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
