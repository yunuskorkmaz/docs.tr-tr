---
ms.openlocfilehash: c78122a2fe69c78625d6cb7fa9ddf41c49c2e737
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497928"
---
### <a name="calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a><span data-ttu-id="6d834-101">Bir CellEditEnding işleyicisinden DataGrid. Commitedıt çağrısı odağı bırakır</span><span class="sxs-lookup"><span data-stu-id="6d834-101">Calling DataGrid.CommitEdit from a CellEditEnding handler drops focus</span></span>

#### <a name="details"></a><span data-ttu-id="6d834-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="6d834-102">Details</span></span>

<span data-ttu-id="6d834-103"><xref:System.Windows.Controls.DataGrid.CommitEdit> <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=fullName> Olay işleyicilerinden birinin çağrılması, odağın kaybetmesine neden olur <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="6d834-103">Calling <xref:System.Windows.Controls.DataGrid.CommitEdit> from one of the <xref:System.Windows.Controls.DataGrid?displayProperty=fullName>'s <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=fullName> event handlers causes the <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> to lose focus.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6d834-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="6d834-104">Suggestion</span></span>

<span data-ttu-id="6d834-105">Bu hata 4.5.2 .NET Framework düzeltildi, bu nedenle .NET Framework yükseltilerek kaçınılabilir.</span><span class="sxs-lookup"><span data-stu-id="6d834-105">This bug has been fixed in the .NET Framework 4.5.2, so it can be avoided by upgrading the .NET Framework.</span></span> <span data-ttu-id="6d834-106">Alternatif olarak, çağrıldıktan sonra açıkça yeniden seçilerek bu kaçınılabilir <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="6d834-106">Alternatively, it can be avoided by explicitly re-selecting the <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> after calling <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=fullName>.</span></span>

| <span data-ttu-id="6d834-107">Name</span><span class="sxs-lookup"><span data-stu-id="6d834-107">Name</span></span>    | <span data-ttu-id="6d834-108">Değer</span><span class="sxs-lookup"><span data-stu-id="6d834-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6d834-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="6d834-109">Scope</span></span>   |<span data-ttu-id="6d834-110">Edge</span><span class="sxs-lookup"><span data-stu-id="6d834-110">Edge</span></span>|
|<span data-ttu-id="6d834-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="6d834-111">Version</span></span>|<span data-ttu-id="6d834-112">4,5</span><span class="sxs-lookup"><span data-stu-id="6d834-112">4.5</span></span>|
|<span data-ttu-id="6d834-113">Tür</span><span class="sxs-lookup"><span data-stu-id="6d834-113">Type</span></span>|<span data-ttu-id="6d834-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="6d834-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="6d834-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="6d834-115">Affected APIs</span></span>

- <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=nameWithType>
- <xref:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Windows.Controls.DataGrid.CommitEdit`
- `M:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)`

-->
