---
ms.openlocfilehash: 55a26f1ab27792cbedf3f31b797f37d3f768d51a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496605"
---
### <a name="aspnet-fix-handling-of-inputattributes-and-labelattributes-for-webforms-checkbox-control"></a><span data-ttu-id="2247c-101">WebForms onay kutusu denetimi için InputAttributes ve LabelAttributes 'ın ASP.NET düzeltmesini işleme</span><span class="sxs-lookup"><span data-stu-id="2247c-101">ASP.NET Fix handling of InputAttributes and LabelAttributes for WebForms CheckBox control</span></span>

#### <a name="details"></a><span data-ttu-id="2247c-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="2247c-102">Details</span></span>

<span data-ttu-id="2247c-103">.NET Framework 4.7.2 ve önceki sürümleri hedefleyen <xref:System.Web.UI.WebControls.CheckBox.InputAttributes?displayProperty=nameWithType> ve <xref:System.Web.UI.WebControls.CheckBox.LabelAttributes?displayProperty=nameWithType> Program aracılığıyla bir WebForms denetimine eklenen uygulamalar için <xref:System.Web.UI.WebControls.CheckBox> geri gönderme işleminden sonra kaybolacaktır.</span><span class="sxs-lookup"><span data-stu-id="2247c-103">For applications that target .NET Framework 4.7.2 and earlier versions, <xref:System.Web.UI.WebControls.CheckBox.InputAttributes?displayProperty=nameWithType> and <xref:System.Web.UI.WebControls.CheckBox.LabelAttributes?displayProperty=nameWithType> that are programmatically added to a WebForms <xref:System.Web.UI.WebControls.CheckBox> control are lost after postback.</span></span> <span data-ttu-id="2247c-104">.NET Framework 4,8 veya sonraki sürümlerini hedefleyen uygulamalar için, geri gönderme sonrasında korunur.</span><span class="sxs-lookup"><span data-stu-id="2247c-104">For applications that target .NET Framework 4.8 or later versions, they are preserved after postback.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2247c-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="2247c-105">Suggestion</span></span>

<span data-ttu-id="2247c-106">Geri göndermede özniteliklerin geri yüklenmesine yönelik doğru davranış için, öğesini <code>targetFrameworkVersion</code> 4,8 veya üzeri olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2247c-106">For the correct behavior for restoring attributes on postback, set the <code>targetFrameworkVersion</code> to 4.8 or higher.</span></span> <span data-ttu-id="2247c-107">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="2247c-107">For example:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;system.web&gt;&#13;&#10;&lt;httpRuntime targetFramework=&quot;4.8&quot;/&gt;&#13;&#10;&lt;/system.web&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre><span data-ttu-id="2247c-108">Bu ayarı daha düşük veya hiç değil, eski hatalı davranışı korur.</span><span class="sxs-lookup"><span data-stu-id="2247c-108">Setting it lower, or not at all, preserves the old incorrect behavior.</span></span>

| <span data-ttu-id="2247c-109">Name</span><span class="sxs-lookup"><span data-stu-id="2247c-109">Name</span></span>    | <span data-ttu-id="2247c-110">Değer</span><span class="sxs-lookup"><span data-stu-id="2247c-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2247c-111">Kapsam</span><span class="sxs-lookup"><span data-stu-id="2247c-111">Scope</span></span>   |<span data-ttu-id="2247c-112">Bilinmiyor</span><span class="sxs-lookup"><span data-stu-id="2247c-112">Unknown</span></span>|
|<span data-ttu-id="2247c-113">Sürüm</span><span class="sxs-lookup"><span data-stu-id="2247c-113">Version</span></span>|<span data-ttu-id="2247c-114">4,8</span><span class="sxs-lookup"><span data-stu-id="2247c-114">4.8</span></span>|
|<span data-ttu-id="2247c-115">Tür</span><span class="sxs-lookup"><span data-stu-id="2247c-115">Type</span></span>|<span data-ttu-id="2247c-116">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="2247c-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="2247c-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="2247c-117">Affected APIs</span></span>

- <xref:System.Web.UI.WebControls.CheckBox?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Web.UI.WebControls.CheckBox`

-->
