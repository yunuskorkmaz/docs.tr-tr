---
ms.openlocfilehash: 961ca545560a53fc2c1d52722b68ae460de66877
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496315"
---
### <a name="datagridcellspanelbringindexintoview-throws-argumentoutofrangeexception"></a><span data-ttu-id="3a330-101">DataGridCellsPanel. BringIndexIntoView, ArgumentOutOfRangeException oluşturur</span><span class="sxs-lookup"><span data-stu-id="3a330-101">DataGridCellsPanel.BringIndexIntoView throws ArgumentOutOfRangeException</span></span>

#### <a name="details"></a><span data-ttu-id="3a330-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="3a330-102">Details</span></span>

<span data-ttu-id="3a330-103"><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> sütun sanallaştırma etkinleştirildiğinde zaman uyumsuz olarak çalışır, ancak sütun genişlikleri henüz belirlenmemiştir.</span><span class="sxs-lookup"><span data-stu-id="3a330-103"><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> will work asynchronously when column virtualization is enabled but the column widths have not yet been determined.</span></span>  <span data-ttu-id="3a330-104">Zaman uyumsuz çalışma yapılmadan önce sütunlar kaldırılırsa, bir <xref:System.ArgumentOutOfRangeException?displayProperty=fullName> gerçekleşebilir.</span><span class="sxs-lookup"><span data-stu-id="3a330-104">If columns are removed before the asynchronous work happens, an <xref:System.ArgumentOutOfRangeException?displayProperty=fullName> can occur.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3a330-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="3a330-105">Suggestion</span></span>

<span data-ttu-id="3a330-106">Aşağıdakilerden biri:</span><span class="sxs-lookup"><span data-stu-id="3a330-106">Any one of the following:</span></span><ol><li><span data-ttu-id="3a330-107">.NET Framework 4,7 ' ye yükseltin.</span><span class="sxs-lookup"><span data-stu-id="3a330-107">Upgrade to .NET Framework 4.7.</span></span></li><li><span data-ttu-id="3a330-108">.NET Framework 4.6.2 için en son bakım düzeltme ekini yükler.</span><span class="sxs-lookup"><span data-stu-id="3a330-108">Install the latest servicing patch for .NET Framework 4.6.2.</span></span></li><li><span data-ttu-id="3a330-109">Zaman uyumsuz yanıt tamamlanana kadar sütunları kaldırmaktan kaçının <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> .</span><span class="sxs-lookup"><span data-stu-id="3a330-109">Avoid removing columns until the asynchronous response to <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> has completed.</span></span></li></ol>

| <span data-ttu-id="3a330-110">Name</span><span class="sxs-lookup"><span data-stu-id="3a330-110">Name</span></span>    | <span data-ttu-id="3a330-111">Değer</span><span class="sxs-lookup"><span data-stu-id="3a330-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3a330-112">Kapsam</span><span class="sxs-lookup"><span data-stu-id="3a330-112">Scope</span></span>   |<span data-ttu-id="3a330-113">Edge</span><span class="sxs-lookup"><span data-stu-id="3a330-113">Edge</span></span>|
|<span data-ttu-id="3a330-114">Sürüm</span><span class="sxs-lookup"><span data-stu-id="3a330-114">Version</span></span>|<span data-ttu-id="3a330-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="3a330-115">4.6.2</span></span>|
|<span data-ttu-id="3a330-116">Tür</span><span class="sxs-lookup"><span data-stu-id="3a330-116">Type</span></span>|<span data-ttu-id="3a330-117">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="3a330-117">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="3a330-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="3a330-118">Affected APIs</span></span>

- <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)?displayProperty=nameWithType>
- <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object,System.Windows.Controls.DataGridColumn)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)`
- `M:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object,System.Windows.Controls.DataGridColumn)`

-->
