---
ms.openlocfilehash: 710d1517397f423fa40cc0c4a26c3499aac6179e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620682"
---
### <a name="calling-itemsrefresh-on-a-wpf-listbox-listview-or-datagrid-with-items-selected-can-cause-duplicate-items-to-appear-in-the-element"></a><span data-ttu-id="29bbc-101">Öğeleri çağırma. bir WPF ListBox, ListView veya DataGrid üzerinde seçili öğeler içeren DataGrid 'de yenileme yinelenen öğelerin öğede görünmesine neden olabilir</span><span class="sxs-lookup"><span data-stu-id="29bbc-101">Calling Items.Refresh on a WPF ListBox, ListView, or DataGrid with items selected can cause duplicate items to appear in the element</span></span>

#### <a name="details"></a><span data-ttu-id="29bbc-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="29bbc-102">Details</span></span>

<span data-ttu-id="29bbc-103">.NET Framework 4,5 ' de, ListBox. Items ' ı çağırma. bir öğesinde öğeler seçildiğinde koddan Yenile <xref:System.Windows.Controls.ListBox?displayProperty=fullName> Seçili öğelerin listede yinelenmesine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="29bbc-103">In the .NET Framework 4.5, calling ListBox.Items.Refresh from code while items are selected in a <xref:System.Windows.Controls.ListBox?displayProperty=fullName> can cause the selected items to be duplicated in the list.</span></span> <span data-ttu-id="29bbc-104">Ve ile benzer bir sorun <xref:System.Windows.Controls.ListView?displayProperty=fullName> oluşur <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="29bbc-104">A similar issue occurs with <xref:System.Windows.Controls.ListView?displayProperty=fullName> and <xref:System.Windows.Controls.DataGrid?displayProperty=fullName>.</span></span> <span data-ttu-id="29bbc-105">Bu .NET Framework 4,6 ' de düzeltilir.</span><span class="sxs-lookup"><span data-stu-id="29bbc-105">This is fixed in the .NET Framework 4.6.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="29bbc-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="29bbc-106">Suggestion</span></span>

<span data-ttu-id="29bbc-107">Bu sorun, çağrılmadan önce öğeleri seçerek <xref:System.Windows.Data.CollectionView.Refresh?displayProperty=fullName> ve ardından çağrı tamamlandıktan sonra yeniden seçmeye çalışan geçici bir çözüm olabilir.</span><span class="sxs-lookup"><span data-stu-id="29bbc-107">This issue may be worked around by programmatically unselecting items before <xref:System.Windows.Data.CollectionView.Refresh?displayProperty=fullName> is called and then re-selecting them after the call is completed.</span></span> <span data-ttu-id="29bbc-108">Alternatif olarak, bu sorun .NET Framework 4,6 ' de düzeltilmiştir ve bu .NET Framework sürümüne yükseltilerek çözülebilir.</span><span class="sxs-lookup"><span data-stu-id="29bbc-108">Alternatively, this issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="29bbc-109">Name</span><span class="sxs-lookup"><span data-stu-id="29bbc-109">Name</span></span>    | <span data-ttu-id="29bbc-110">Değer</span><span class="sxs-lookup"><span data-stu-id="29bbc-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="29bbc-111">Kapsam</span><span class="sxs-lookup"><span data-stu-id="29bbc-111">Scope</span></span>   |<span data-ttu-id="29bbc-112">İkincil</span><span class="sxs-lookup"><span data-stu-id="29bbc-112">Minor</span></span>|
|<span data-ttu-id="29bbc-113">Sürüm</span><span class="sxs-lookup"><span data-stu-id="29bbc-113">Version</span></span>|<span data-ttu-id="29bbc-114">4,5</span><span class="sxs-lookup"><span data-stu-id="29bbc-114">4.5</span></span>|
|<span data-ttu-id="29bbc-115">Tür</span><span class="sxs-lookup"><span data-stu-id="29bbc-115">Type</span></span>|<span data-ttu-id="29bbc-116">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="29bbc-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="29bbc-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="29bbc-117">Affected APIs</span></span>

-<xref:System.Windows.Data.CollectionView.Refresh?displayProperty=nameWithType></li></ul>|
