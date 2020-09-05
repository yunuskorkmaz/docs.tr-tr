---
ms.openlocfilehash: 1487e32ffca7b4bbebb5edac7efc8961ac05723b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496400"
---
### <a name="accessing-a-wpf-datagrids-selected-items-from-a-handler-of-the-datagrids-unloadingrow-event-can-cause-a-nullreferenceexception"></a><span data-ttu-id="8cf1d-101">Bir WPF DataGrid 'in seçili öğelerine DataGrid 'in UnloadingRow olayının bir bir NullReferenceException öğesine erişmesi bir NullReferenceException öğesine neden olabilir</span><span class="sxs-lookup"><span data-stu-id="8cf1d-101">Accessing a WPF DataGrid's selected items from a handler of the DataGrid's UnloadingRow event can cause a NullReferenceException</span></span>

#### <a name="details"></a><span data-ttu-id="8cf1d-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="8cf1d-102">Details</span></span>

<span data-ttu-id="8cf1d-103">.NET Framework 4,5 ' deki bir hata nedeniyle, <xref:System.Windows.Controls.DataGrid> bir satırı kaldırmayı içeren olaylar için olay işleyicileri, <xref:System.NullReferenceException?displayProperty=fullName> ya da özelliklerine eriştiklerinde oluşturulmasına neden olabilir <xref:System.Windows.Controls.DataGrid> <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=fullName> <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="8cf1d-103">Due to a bug in the .NET Framework 4.5, event handlers for <xref:System.Windows.Controls.DataGrid> events involving the removal of a row can cause a <xref:System.NullReferenceException?displayProperty=fullName> to be thrown if they access the <xref:System.Windows.Controls.DataGrid>'s <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=fullName> or <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> properties.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8cf1d-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="8cf1d-104">Suggestion</span></span>

<span data-ttu-id="8cf1d-105">Bu sorun .NET Framework 4,6 ' de düzeltilmiştir ve bu .NET Framework sürümüne yükselterek çözülebilir.</span><span class="sxs-lookup"><span data-stu-id="8cf1d-105">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="8cf1d-106">Name</span><span class="sxs-lookup"><span data-stu-id="8cf1d-106">Name</span></span>    | <span data-ttu-id="8cf1d-107">Değer</span><span class="sxs-lookup"><span data-stu-id="8cf1d-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8cf1d-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="8cf1d-108">Scope</span></span>   |<span data-ttu-id="8cf1d-109">İkincil</span><span class="sxs-lookup"><span data-stu-id="8cf1d-109">Minor</span></span>|
|<span data-ttu-id="8cf1d-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="8cf1d-110">Version</span></span>|<span data-ttu-id="8cf1d-111">4,5</span><span class="sxs-lookup"><span data-stu-id="8cf1d-111">4.5</span></span>|
|<span data-ttu-id="8cf1d-112">Tür</span><span class="sxs-lookup"><span data-stu-id="8cf1d-112">Type</span></span>|<span data-ttu-id="8cf1d-113">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="8cf1d-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="8cf1d-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="8cf1d-114">Affected APIs</span></span>

- <xref:System.Windows.Controls.DataGrid.UnloadingRow?displayProperty=nameWithType>
- <xref:System.Windows.Controls.DataGrid.UnloadingRowDetails?displayProperty=nameWithType>

<!--

#### Affected APIs

- `E:System.Windows.Controls.DataGrid.UnloadingRow`
- `E:System.Windows.Controls.DataGrid.UnloadingRowDetails`

-->
