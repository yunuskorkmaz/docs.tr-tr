---
ms.openlocfilehash: 75f176133697056bab9349ba1d18d7a0e1aa7da2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620528"
---
### <a name="itemsclear-does-not-remove-duplicates-from-selecteditems"></a><span data-ttu-id="feac0-101">Items. Clear, Selectedilıtems 'dan yinelenenleri kaldırmaz</span><span class="sxs-lookup"><span data-stu-id="feac0-101">Items.Clear does not remove duplicates from SelectedItems</span></span>

#### <a name="details"></a><span data-ttu-id="feac0-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="feac0-102">Details</span></span>

<span data-ttu-id="feac0-103">Bir seçicinin (birden çok seçim etkinleştirilmiş olarak) koleksiyonunda yinelenen öğeler olduğunu varsayalım <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> . aynı öğe birden çok kez görünüyor.</span><span class="sxs-lookup"><span data-stu-id="feac0-103">Suppose a Selector (with multiple selection enabled) has duplicates in its <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> collection - the same item appears more than once.</span></span>  <span data-ttu-id="feac0-104">Bu öğeleri veri kaynağından kaldırmak (örneğin, Items. Clear öğesini çağırarak), öğesinden kaldıramazsa <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> ; yalnızca ilk örnek kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="feac0-104">Removing those items from the data source (e.g. by calling Items.Clear) fails to remove them from <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName>; only the first instance is removed.</span></span> <span data-ttu-id="feac0-105">Ayrıca, <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> (ör. Selectedilıtems. Clear ()) öğesinin daha sonra <xref:System.ArgumentException?displayProperty=fullName> <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> veri kaynağında olmayan öğeler içerdiğinden, ' nin sonraki kullanımı gibi sorunlar oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="feac0-105">Furthermore, subsequent use of <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> (e.g. SelectedItems.Clear()) can encounter problems such as <xref:System.ArgumentException?displayProperty=fullName>, because <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> contains items that are no longer in the data source.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="feac0-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="feac0-106">Suggestion</span></span>

<span data-ttu-id="feac0-107">4.6.2 .NET Framework için mümkünse yükseltin.</span><span class="sxs-lookup"><span data-stu-id="feac0-107">Upgrade if possible to .NET Framework 4.6.2.</span></span>

| <span data-ttu-id="feac0-108">Name</span><span class="sxs-lookup"><span data-stu-id="feac0-108">Name</span></span>    | <span data-ttu-id="feac0-109">Değer</span><span class="sxs-lookup"><span data-stu-id="feac0-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="feac0-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="feac0-110">Scope</span></span>   |<span data-ttu-id="feac0-111">İkincil</span><span class="sxs-lookup"><span data-stu-id="feac0-111">Minor</span></span>|
|<span data-ttu-id="feac0-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="feac0-112">Version</span></span>|<span data-ttu-id="feac0-113">4,5</span><span class="sxs-lookup"><span data-stu-id="feac0-113">4.5</span></span>|
|<span data-ttu-id="feac0-114">Tür</span><span class="sxs-lookup"><span data-stu-id="feac0-114">Type</span></span>|<span data-ttu-id="feac0-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="feac0-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="feac0-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="feac0-116">Affected APIs</span></span>

-<xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=nameWithType></li></ul>|
