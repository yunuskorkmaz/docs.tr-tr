---
ms.openlocfilehash: 196b6a13d32c7767b858d6d68ca775eb49324805
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496751"
---
### <a name="listboxitem-isselected-binding-issue-with-observablecollectionlttgtmove"></a><span data-ttu-id="800ff-101">ListBoxItem IsSelected bağlama sorunu ObservableCollection &lt; T &gt; . Geçiş</span><span class="sxs-lookup"><span data-stu-id="800ff-101">ListBoxItem IsSelected binding issue with ObservableCollection&lt;T&gt;.Move</span></span>

#### <a name="details"></a><span data-ttu-id="800ff-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="800ff-102">Details</span></span>

<span data-ttu-id="800ff-103"><xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)> Öğesi ile bağlantılı bir koleksiyon üzerinde veya seçili bir koleksiyon üzerinde çağırma <xref:System.Windows.Controls.ListBox?displayProperty=fullName> , gelecekteki seçim veya öğelerin seçimini kaldırma ile Erratic davranışına neden olabilir <xref:System.Windows.Controls.ListBox?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="800ff-103">Calling <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> or <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)> on a collection bound to a <xref:System.Windows.Controls.ListBox?displayProperty=fullName> with items selected can lead to erratic behavior with future selection or unselection of <xref:System.Windows.Controls.ListBox?displayProperty=fullName> items.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="800ff-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="800ff-104">Suggestion</span></span>

<span data-ttu-id="800ff-105"><xref:System.Collections.ObjectModel.Collection%601.Remove(%600)?displayProperty=fullName>Ve <xref:System.Collections.ObjectModel.Collection%601.Insert(System.Int32,%600)?displayProperty=fullName> yerine çağırmak, <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> Bu sorunu geçici olarak çözmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="800ff-105">Calling <xref:System.Collections.ObjectModel.Collection%601.Remove(%600)?displayProperty=fullName> and <xref:System.Collections.ObjectModel.Collection%601.Insert(System.Int32,%600)?displayProperty=fullName> instead of <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> will work around this issue.</span></span> <span data-ttu-id="800ff-106">Alternatif olarak, bu sorun .NET Framework 4,6 ' de düzeltilmiştir ve bu .NET Framework sürümüne yükseltilerek çözülebilir.</span><span class="sxs-lookup"><span data-stu-id="800ff-106">Alternatively, this issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="800ff-107">Name</span><span class="sxs-lookup"><span data-stu-id="800ff-107">Name</span></span>    | <span data-ttu-id="800ff-108">Değer</span><span class="sxs-lookup"><span data-stu-id="800ff-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="800ff-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="800ff-109">Scope</span></span>   |<span data-ttu-id="800ff-110">İkincil</span><span class="sxs-lookup"><span data-stu-id="800ff-110">Minor</span></span>|
|<span data-ttu-id="800ff-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="800ff-111">Version</span></span>|<span data-ttu-id="800ff-112">4,5</span><span class="sxs-lookup"><span data-stu-id="800ff-112">4.5</span></span>|
|<span data-ttu-id="800ff-113">Tür</span><span class="sxs-lookup"><span data-stu-id="800ff-113">Type</span></span>|<span data-ttu-id="800ff-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="800ff-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="800ff-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="800ff-115">Affected APIs</span></span>

- <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)?displayProperty=nameWithType>

<!--

#### Affected APIs

- ``M:System.Collections.ObjectModel.ObservableCollection`1.Move(System.Int32,System.Int32)``
- ``M:System.Collections.ObjectModel.ObservableCollection`1.MoveItem(System.Int32,System.Int32)``

-->
