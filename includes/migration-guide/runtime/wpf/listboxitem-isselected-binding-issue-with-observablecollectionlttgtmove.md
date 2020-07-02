---
ms.openlocfilehash: f4ff938b2d0e9ead481fdf239aed8a6b918a99b0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620699"
---
### <a name="listboxitem-isselected-binding-issue-with-observablecollectionlttgtmove"></a><span data-ttu-id="2ed9f-101">ListBoxItem IsSelected bağlama sorunu ObservableCollection &lt; T &gt; . Geçiş</span><span class="sxs-lookup"><span data-stu-id="2ed9f-101">ListBoxItem IsSelected binding issue with ObservableCollection&lt;T&gt;.Move</span></span>

#### <a name="details"></a><span data-ttu-id="2ed9f-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="2ed9f-102">Details</span></span>

<span data-ttu-id="2ed9f-103"><xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)> Öğesi ile bağlantılı bir koleksiyon üzerinde veya seçili bir koleksiyon üzerinde çağırma <xref:System.Windows.Controls.ListBox?displayProperty=fullName> , gelecekteki seçim veya öğelerin seçimini kaldırma ile Erratic davranışına neden olabilir <xref:System.Windows.Controls.ListBox?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="2ed9f-103">Calling <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> or <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)> on a collection bound to a <xref:System.Windows.Controls.ListBox?displayProperty=fullName> with items selected can lead to erratic behavior with future selection or unselection of <xref:System.Windows.Controls.ListBox?displayProperty=fullName> items.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2ed9f-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="2ed9f-104">Suggestion</span></span>

<span data-ttu-id="2ed9f-105"><xref:System.Collections.ObjectModel.Collection%601.Remove(%600)?displayProperty=fullName>Ve <xref:System.Collections.ObjectModel.Collection%601.Insert(System.Int32,%600)?displayProperty=fullName> yerine çağırmak, <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> Bu sorunu geçici olarak çözmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2ed9f-105">Calling <xref:System.Collections.ObjectModel.Collection%601.Remove(%600)?displayProperty=fullName> and <xref:System.Collections.ObjectModel.Collection%601.Insert(System.Int32,%600)?displayProperty=fullName> instead of <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> will work around this issue.</span></span> <span data-ttu-id="2ed9f-106">Alternatif olarak, bu sorun .NET Framework 4,6 ' de düzeltilmiştir ve bu .NET Framework sürümüne yükseltilerek çözülebilir.</span><span class="sxs-lookup"><span data-stu-id="2ed9f-106">Alternatively, this issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="2ed9f-107">Name</span><span class="sxs-lookup"><span data-stu-id="2ed9f-107">Name</span></span>    | <span data-ttu-id="2ed9f-108">Değer</span><span class="sxs-lookup"><span data-stu-id="2ed9f-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2ed9f-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="2ed9f-109">Scope</span></span>   |<span data-ttu-id="2ed9f-110">İkincil</span><span class="sxs-lookup"><span data-stu-id="2ed9f-110">Minor</span></span>|
|<span data-ttu-id="2ed9f-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="2ed9f-111">Version</span></span>|<span data-ttu-id="2ed9f-112">4,5</span><span class="sxs-lookup"><span data-stu-id="2ed9f-112">4.5</span></span>|
|<span data-ttu-id="2ed9f-113">Tür</span><span class="sxs-lookup"><span data-stu-id="2ed9f-113">Type</span></span>|<span data-ttu-id="2ed9f-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="2ed9f-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2ed9f-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="2ed9f-115">Affected APIs</span></span>

-<xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)?displayProperty=nameWithType></li><li><xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|
