---
ms.openlocfilehash: d23d7821e19b9d7f2db13a6bfdf868a8414cf721
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497134"
---
### <a name="item-scrolling-a-flat-list-with-items-of-different-pixel-height"></a><span data-ttu-id="c03f0-101">Öğe-farklı piksel yüksekliğinde öğeleri olan düz bir liste kaydırma</span><span class="sxs-lookup"><span data-stu-id="c03f0-101">Item-scrolling a flat list with items of different pixel-height</span></span>

#### <a name="details"></a><span data-ttu-id="c03f0-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="c03f0-102">Details</span></span>

<span data-ttu-id="c03f0-103">Bir <xref:System.Windows.Controls.ItemsControl?displayProperty=fullName> koleksiyon, sanallaştırma ( <code>IsVirtualizing=true</code> ) ve öğe kaydırma () kullanarak bir koleksiyon <code>ScrollUnit=Item</code> görüntülediğinde ve denetimin piksel cinsinden yüksekliği, komşularından farklı olan bir öğeyi görüntülemek için kaydırıldığında, <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=fullName> koleksiyondaki tüm öğeler üzerinde dolaşır.</span><span class="sxs-lookup"><span data-stu-id="c03f0-103">When an <xref:System.Windows.Controls.ItemsControl?displayProperty=fullName> displays a collection using virtualization (<code>IsVirtualizing=true</code>) and item- scrolling (<code>ScrollUnit=Item</code>), and when the control scrolls to display an item whose height in pixels differs from its neighbors, the <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=fullName> iterates over all items in the collection.</span></span> <span data-ttu-id="c03f0-104">Kullanıcı arabirimi bu yineleme sırasında yanıt vermiyor; koleksiyon büyükse, bu, askıda bir şekilde algılanır.</span><span class="sxs-lookup"><span data-stu-id="c03f0-104">The UI is unresponsive during this iteration; if the collection is large, this can be perceived as a hang.</span></span> <span data-ttu-id="c03f0-105">Yineleme, önceki .NET Framework sürümlerde bile diğer koşullarda oluşur.</span><span class="sxs-lookup"><span data-stu-id="c03f0-105">The iteration occurs in other circumstances, even in previous .NET Framework releases.</span></span> <span data-ttu-id="c03f0-106">Örneğin, piksel <code>ScrollUnit=Pixel</code> kaydırdıktan sonra (), farklı piksel yüksekliğine sahip bir öğeyle karşılaşıldığında ve öğe kaydırılırken hiyerarşik veriler (örneğin <xref:System.Windows.Controls.TreeView?displayProperty=fullName> , bir veya bir <xref:System.Windows.Controls.ItemsControl?displayProperty=fullName> gruplama etkin gibi), komşularından farklı sayıda alt öğe içeren bir öğeyle karşılaşınca meydana gelir. Öğe kaydırma ve farklı piksel yüksekliğinin olması durumunda yineleme, hiyerarşik verilerin düzeninde hataları onarmak için .NET Framework 4.6.1 ' de tanıtılmıştır.</span><span class="sxs-lookup"><span data-stu-id="c03f0-106">For example, it occurs when pixel-scrolling (<code>ScrollUnit=Pixel</code>) upon encountering an item with different pixel height, and when item-scrolling hierarchical data (such as a <xref:System.Windows.Controls.TreeView?displayProperty=fullName> or an <xref:System.Windows.Controls.ItemsControl?displayProperty=fullName> with grouping enabled) upon encountering an item with a different number of descendant items than its neighbors.For the case of item-scrolling and different pixel height, the iteration was introduced in .NET Framework 4.6.1 to fix bugs in the layout of hierarchical data.</span></span>  <span data-ttu-id="c03f0-107">Veriler düz (hiyerarşi yok) ise ve bu durumda .NET Framework 4.6.2 bunu yapmaz.</span><span class="sxs-lookup"><span data-stu-id="c03f0-107">It is not needed if the data is flat (no hierarchy), and .NET Framework 4.6.2 does not do it in that case.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c03f0-108">Öneri</span><span class="sxs-lookup"><span data-stu-id="c03f0-108">Suggestion</span></span>

<span data-ttu-id="c03f0-109">Yineleme, daha önceki sürümlerde değil, .NET Framework 4.6.1 içinde oluşursa, yani <xref:System.Windows.Controls.ItemsControl?displayProperty=fullName> öğesi farklı piksel yüksekliğinin bulunduğu düz bir liste içeriyorsa, iki düzeltme vardır:</span><span class="sxs-lookup"><span data-stu-id="c03f0-109">If the iteration occurs in .NET Framework 4.6.1 but not in earlier releases - that is, if the <xref:System.Windows.Controls.ItemsControl?displayProperty=fullName> is item- scrolling a flat list with items of different pixel height - there are two remedies:</span></span><ol><li><span data-ttu-id="c03f0-110">.NET Framework 4.6.2 'yi yükler.</span><span class="sxs-lookup"><span data-stu-id="c03f0-110">Install .NET Framework 4.6.2.</span></span></li><li><span data-ttu-id="c03f0-111">.NET Framework 4.6.1 için HR 1605 düzeltmesini yükler.</span><span class="sxs-lookup"><span data-stu-id="c03f0-111">Install hotfix HR 1605 for .NET Framework 4.6.1.</span></span></li></ol>

| <span data-ttu-id="c03f0-112">Name</span><span class="sxs-lookup"><span data-stu-id="c03f0-112">Name</span></span>    | <span data-ttu-id="c03f0-113">Değer</span><span class="sxs-lookup"><span data-stu-id="c03f0-113">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c03f0-114">Kapsam</span><span class="sxs-lookup"><span data-stu-id="c03f0-114">Scope</span></span>   |<span data-ttu-id="c03f0-115">İkincil</span><span class="sxs-lookup"><span data-stu-id="c03f0-115">Minor</span></span>|
|<span data-ttu-id="c03f0-116">Sürüm</span><span class="sxs-lookup"><span data-stu-id="c03f0-116">Version</span></span>|<span data-ttu-id="c03f0-117">4.6.1</span><span class="sxs-lookup"><span data-stu-id="c03f0-117">4.6.1</span></span>|
|<span data-ttu-id="c03f0-118">Tür</span><span class="sxs-lookup"><span data-stu-id="c03f0-118">Type</span></span>|<span data-ttu-id="c03f0-119">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="c03f0-119">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="c03f0-120">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="c03f0-120">Affected APIs</span></span>

- <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Windows.Controls.VirtualizingStackPanel`

-->
