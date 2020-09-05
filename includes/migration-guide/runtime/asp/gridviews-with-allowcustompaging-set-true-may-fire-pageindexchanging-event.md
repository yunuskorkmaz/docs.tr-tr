---
ms.openlocfilehash: 4d210eeedd2f228017634d29f11554deb6ed8079
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496845"
---
### <a name="gridviews-with-allowcustompaging-set-to-true-may-fire-the-pageindexchanging-event-when-leaving-the-final-page-of-the-view"></a><span data-ttu-id="ba3ea-101">Allowcustompeskime ile true olarak ayarlanan GridViews, görünümün son sayfasından çıkılırken PageIndexChanging olayını tetiklebiliyor</span><span class="sxs-lookup"><span data-stu-id="ba3ea-101">GridViews with AllowCustomPaging set to true may fire the PageIndexChanging event when leaving the final page of the view</span></span>

#### <a name="details"></a><span data-ttu-id="ba3ea-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="ba3ea-102">Details</span></span>

<span data-ttu-id="ba3ea-103">.NET Framework 4,5 ' deki bir hata <xref:System.Web.UI.WebControls.GridView.PageIndexChanging?displayProperty=fullName> bazen <xref:System.Web.UI.WebControls.GridView?displayProperty=fullName> etkinleştirilmiş olan s için tetiklenmesine neden olur <xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="ba3ea-103">A bug in the .NET Framework 4.5 causes <xref:System.Web.UI.WebControls.GridView.PageIndexChanging?displayProperty=fullName> to sometimes not fire for <xref:System.Web.UI.WebControls.GridView?displayProperty=fullName>s that have enabled <xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=fullName>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ba3ea-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="ba3ea-104">Suggestion</span></span>

<span data-ttu-id="ba3ea-105">Bu sorun .NET Framework 4,6 ' de düzeltilmiştir ve bu .NET Framework sürümüne yükselterek çözülebilir.</span><span class="sxs-lookup"><span data-stu-id="ba3ea-105">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span> <span data-ttu-id="ba3ea-106">Geçici bir çözüm olarak, uygulama, bu koşullara ulaşmaları için açık bir BindGrid gerçekleştirebilir <code>Page_Load</code> ( <xref:System.Web.UI.WebControls.GridView?displayProperty=fullName> son sayfada ve son <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName> olarak ' den farklıdır <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName> ).</span><span class="sxs-lookup"><span data-stu-id="ba3ea-106">As a work-around, the app can do an explicit BindGrid on any <code>Page_Load</code> that would hit these conditions (the <xref:System.Web.UI.WebControls.GridView?displayProperty=fullName> is on the last page and Last<xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName> is different from <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName>).</span></span> <span data-ttu-id="ba3ea-107">Alternatif olarak, bu senaryo sorunu göstermediğinden, uygulama, sayfalama (özel disk belleği yerine) için de değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="ba3ea-107">Alternatively, the app can be modified to allow paging (instead of custom paging), as that scenario does not demonstrate the problem.</span></span>

| <span data-ttu-id="ba3ea-108">Name</span><span class="sxs-lookup"><span data-stu-id="ba3ea-108">Name</span></span>    | <span data-ttu-id="ba3ea-109">Değer</span><span class="sxs-lookup"><span data-stu-id="ba3ea-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ba3ea-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="ba3ea-110">Scope</span></span>   |<span data-ttu-id="ba3ea-111">İkincil</span><span class="sxs-lookup"><span data-stu-id="ba3ea-111">Minor</span></span>|
|<span data-ttu-id="ba3ea-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="ba3ea-112">Version</span></span>|<span data-ttu-id="ba3ea-113">4,5</span><span class="sxs-lookup"><span data-stu-id="ba3ea-113">4.5</span></span>|
|<span data-ttu-id="ba3ea-114">Tür</span><span class="sxs-lookup"><span data-stu-id="ba3ea-114">Type</span></span>|<span data-ttu-id="ba3ea-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="ba3ea-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="ba3ea-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="ba3ea-116">Affected APIs</span></span>

- <xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Web.UI.WebControls.GridView.AllowCustomPaging`

-->
