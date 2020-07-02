---
ms.openlocfilehash: bae6d7c0f8843211c721c68ce6f16000b35b4401
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620700"
---
### <a name="new-enum-values-in-wpfs-pagerangeselection"></a><span data-ttu-id="9c415-101">WPF 'in PageRangeSelection öğesindeki yeni Enum değerleri</span><span class="sxs-lookup"><span data-stu-id="9c415-101">New enum values in WPF's PageRangeSelection</span></span>

#### <a name="details"></a><span data-ttu-id="9c415-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="9c415-102">Details</span></span>

<span data-ttu-id="9c415-103">Sabit listesine iki yeni üye ( <xref:System.Windows.Controls.PageRangeSelection.CurrentPage?displayProperty=fullName> ve <xref:System.Windows.Controls.PageRangeSelection.SelectedPages?displayProperty=fullName> ) eklenmiştir <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="9c415-103">Two new members (<xref:System.Windows.Controls.PageRangeSelection.CurrentPage?displayProperty=fullName> and <xref:System.Windows.Controls.PageRangeSelection.SelectedPages?displayProperty=fullName>) have been added to the <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> enum.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="9c415-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="9c415-104">Suggestion</span></span>

<span data-ttu-id="9c415-105">Çoğu durumda, bu değişiklikler Kullanıcı kodunu etkilemez.</span><span class="sxs-lookup"><span data-stu-id="9c415-105">In most cases, these changes won't impact user code.</span></span> <span data-ttu-id="9c415-106">Aynı olsa da, içindeki belirli bir öğe sayısına veya bu <xref:System.Enum.GetNames(System.Type)> türdeki çağrılara bağlı olan kod <xref:System.Enum.GetValues(System.Type)> <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> değiştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="9c415-106">Code that depends on a particular number of elements existing in <xref:System.Enum.GetNames(System.Type)> or <xref:System.Enum.GetValues(System.Type)> calls on the <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> type should be modified, though.</span></span>

| <span data-ttu-id="9c415-107">Name</span><span class="sxs-lookup"><span data-stu-id="9c415-107">Name</span></span>    | <span data-ttu-id="9c415-108">Değer</span><span class="sxs-lookup"><span data-stu-id="9c415-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="9c415-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="9c415-109">Scope</span></span>   |<span data-ttu-id="9c415-110">Edge</span><span class="sxs-lookup"><span data-stu-id="9c415-110">Edge</span></span>|
|<span data-ttu-id="9c415-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="9c415-111">Version</span></span>|<span data-ttu-id="9c415-112">4,5</span><span class="sxs-lookup"><span data-stu-id="9c415-112">4.5</span></span>|
|<span data-ttu-id="9c415-113">Tür</span><span class="sxs-lookup"><span data-stu-id="9c415-113">Type</span></span>|<span data-ttu-id="9c415-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="9c415-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9c415-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="9c415-115">Affected APIs</span></span>

-<xref:System.Windows.Controls.PageRangeSelection?displayProperty=nameWithType></li></ul>|
