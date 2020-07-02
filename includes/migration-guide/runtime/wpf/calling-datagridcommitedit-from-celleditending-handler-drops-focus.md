---
ms.openlocfilehash: c3c3ed44cf53625c246dfe0408bb861750ecf336
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622123"
---
### <a name="calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a><span data-ttu-id="bbaf9-101">Bir CellEditEnding işleyicisinden DataGrid. Commitedıt çağrısı odağı bırakır</span><span class="sxs-lookup"><span data-stu-id="bbaf9-101">Calling DataGrid.CommitEdit from a CellEditEnding handler drops focus</span></span>

#### <a name="details"></a><span data-ttu-id="bbaf9-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="bbaf9-102">Details</span></span>

<span data-ttu-id="bbaf9-103"><xref:System.Windows.Controls.DataGrid.CommitEdit> <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=fullName> Olay işleyicilerinden birinin çağrılması, odağın kaybetmesine neden olur <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="bbaf9-103">Calling <xref:System.Windows.Controls.DataGrid.CommitEdit> from one of the <xref:System.Windows.Controls.DataGrid?displayProperty=fullName>'s <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=fullName> event handlers causes the <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> to lose focus.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="bbaf9-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="bbaf9-104">Suggestion</span></span>

<span data-ttu-id="bbaf9-105">Bu hata 4.5.2 .NET Framework düzeltildi, bu nedenle .NET Framework yükseltilerek kaçınılabilir.</span><span class="sxs-lookup"><span data-stu-id="bbaf9-105">This bug has been fixed in the .NET Framework 4.5.2, so it can be avoided by upgrading the .NET Framework.</span></span> <span data-ttu-id="bbaf9-106">Alternatif olarak, çağrıldıktan sonra açıkça yeniden seçilerek bu kaçınılabilir <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="bbaf9-106">Alternatively, it can be avoided by explicitly re-selecting the <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> after calling <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=fullName>.</span></span>

| <span data-ttu-id="bbaf9-107">Name</span><span class="sxs-lookup"><span data-stu-id="bbaf9-107">Name</span></span>    | <span data-ttu-id="bbaf9-108">Değer</span><span class="sxs-lookup"><span data-stu-id="bbaf9-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="bbaf9-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="bbaf9-109">Scope</span></span>   |<span data-ttu-id="bbaf9-110">Edge</span><span class="sxs-lookup"><span data-stu-id="bbaf9-110">Edge</span></span>|
|<span data-ttu-id="bbaf9-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="bbaf9-111">Version</span></span>|<span data-ttu-id="bbaf9-112">4,5</span><span class="sxs-lookup"><span data-stu-id="bbaf9-112">4.5</span></span>|
|<span data-ttu-id="bbaf9-113">Tür</span><span class="sxs-lookup"><span data-stu-id="bbaf9-113">Type</span></span>|<span data-ttu-id="bbaf9-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="bbaf9-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="bbaf9-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="bbaf9-115">Affected APIs</span></span>

-<xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)?displayProperty=nameWithType></li></ul>|
