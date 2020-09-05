---
ms.openlocfilehash: 25ce391f917bd270d4d9a75f608e4a8ec763d15c
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496215"
---
### <a name="itemsclear-does-not-remove-duplicates-from-selecteditems"></a><span data-ttu-id="55644-101">Items. Clear, Selectedilıtems 'dan yinelenenleri kaldırmaz</span><span class="sxs-lookup"><span data-stu-id="55644-101">Items.Clear does not remove duplicates from SelectedItems</span></span>

#### <a name="details"></a><span data-ttu-id="55644-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="55644-102">Details</span></span>

<span data-ttu-id="55644-103">Bir seçicinin (birden çok seçim etkinleştirilmiş olarak) koleksiyonunda yinelenen öğeler olduğunu varsayalım <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> . aynı öğe birden çok kez görünüyor.</span><span class="sxs-lookup"><span data-stu-id="55644-103">Suppose a Selector (with multiple selection enabled) has duplicates in its <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> collection - the same item appears more than once.</span></span>  <span data-ttu-id="55644-104">Bu öğeleri veri kaynağından kaldırmak (örneğin, Items. Clear öğesini çağırarak), öğesinden kaldıramazsa <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> ; yalnızca ilk örnek kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="55644-104">Removing those items from the data source (e.g. by calling Items.Clear) fails to remove them from <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName>; only the first instance is removed.</span></span> <span data-ttu-id="55644-105">Ayrıca, <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> (ör. Selectedilıtems. Clear ()) öğesinin daha sonra <xref:System.ArgumentException?displayProperty=fullName> <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> veri kaynağında olmayan öğeler içerdiğinden, ' nin sonraki kullanımı gibi sorunlar oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="55644-105">Furthermore, subsequent use of <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> (e.g. SelectedItems.Clear()) can encounter problems such as <xref:System.ArgumentException?displayProperty=fullName>, because <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> contains items that are no longer in the data source.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="55644-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="55644-106">Suggestion</span></span>

<span data-ttu-id="55644-107">4.6.2 .NET Framework için mümkünse yükseltin.</span><span class="sxs-lookup"><span data-stu-id="55644-107">Upgrade if possible to .NET Framework 4.6.2.</span></span>

| <span data-ttu-id="55644-108">Name</span><span class="sxs-lookup"><span data-stu-id="55644-108">Name</span></span>    | <span data-ttu-id="55644-109">Değer</span><span class="sxs-lookup"><span data-stu-id="55644-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="55644-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="55644-110">Scope</span></span>   |<span data-ttu-id="55644-111">İkincil</span><span class="sxs-lookup"><span data-stu-id="55644-111">Minor</span></span>|
|<span data-ttu-id="55644-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="55644-112">Version</span></span>|<span data-ttu-id="55644-113">4,5</span><span class="sxs-lookup"><span data-stu-id="55644-113">4.5</span></span>|
|<span data-ttu-id="55644-114">Tür</span><span class="sxs-lookup"><span data-stu-id="55644-114">Type</span></span>|<span data-ttu-id="55644-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="55644-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="55644-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="55644-116">Affected APIs</span></span>

- <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Windows.Controls.Primitives.MultiSelector.SelectedItems`

-->
