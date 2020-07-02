---
ms.openlocfilehash: ae557ce57557d027dba35b7da213c08aee85f2c7
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622073"
---
### <a name="aspnet-fix-handling-of-inputattributes-and-labelattributes-for-webforms-checkbox-control"></a><span data-ttu-id="9ef8f-101">WebForms onay kutusu denetimi için InputAttributes ve LabelAttributes 'ın ASP.NET düzeltmesini işleme</span><span class="sxs-lookup"><span data-stu-id="9ef8f-101">ASP.NET Fix handling of InputAttributes and LabelAttributes for WebForms CheckBox control</span></span>

#### <a name="details"></a><span data-ttu-id="9ef8f-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="9ef8f-102">Details</span></span>

<span data-ttu-id="9ef8f-103">.NET Framework 4.7.2 ve önceki sürümleri hedefleyen <xref:System.Web.UI.WebControls.CheckBox.InputAttributes?displayProperty=nameWithType> ve <xref:System.Web.UI.WebControls.CheckBox.LabelAttributes?displayProperty=nameWithType> Program aracılığıyla bir WebForms denetimine eklenen uygulamalar için <xref:System.Web.UI.WebControls.CheckBox> geri gönderme işleminden sonra kaybolacaktır.</span><span class="sxs-lookup"><span data-stu-id="9ef8f-103">For applications that target .NET Framework 4.7.2 and earlier versions, <xref:System.Web.UI.WebControls.CheckBox.InputAttributes?displayProperty=nameWithType> and <xref:System.Web.UI.WebControls.CheckBox.LabelAttributes?displayProperty=nameWithType> that are programmatically added to a WebForms <xref:System.Web.UI.WebControls.CheckBox> control are lost after postback.</span></span> <span data-ttu-id="9ef8f-104">.NET Framework 4,8 veya sonraki sürümlerini hedefleyen uygulamalar için, geri gönderme sonrasında korunur.</span><span class="sxs-lookup"><span data-stu-id="9ef8f-104">For applications that target .NET Framework 4.8 or later versions, they are preserved after postback.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="9ef8f-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="9ef8f-105">Suggestion</span></span>

<span data-ttu-id="9ef8f-106">Geri göndermede özniteliklerin geri yüklenmesine yönelik doğru davranış için, öğesini <code>targetFrameworkVersion</code> 4,8 veya üzeri olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9ef8f-106">For the correct behavior for restoring attributes on postback, set the <code>targetFrameworkVersion</code> to 4.8 or higher.</span></span> <span data-ttu-id="9ef8f-107">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="9ef8f-107">For example:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;system.web&gt;&#13;&#10;&lt;httpRuntime targetFramework=&quot;4.8&quot;/&gt;&#13;&#10;&lt;/system.web&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre><span data-ttu-id="9ef8f-108">Bu ayarı daha düşük veya hiç değil, eski hatalı davranışı korur.</span><span class="sxs-lookup"><span data-stu-id="9ef8f-108">Setting it lower, or not at all, preserves the old incorrect behavior.</span></span>

| <span data-ttu-id="9ef8f-109">Name</span><span class="sxs-lookup"><span data-stu-id="9ef8f-109">Name</span></span>    | <span data-ttu-id="9ef8f-110">Değer</span><span class="sxs-lookup"><span data-stu-id="9ef8f-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="9ef8f-111">Kapsam</span><span class="sxs-lookup"><span data-stu-id="9ef8f-111">Scope</span></span>   |<span data-ttu-id="9ef8f-112">Bilinmiyor</span><span class="sxs-lookup"><span data-stu-id="9ef8f-112">Unknown</span></span>|
|<span data-ttu-id="9ef8f-113">Sürüm</span><span class="sxs-lookup"><span data-stu-id="9ef8f-113">Version</span></span>|<span data-ttu-id="9ef8f-114">4,8</span><span class="sxs-lookup"><span data-stu-id="9ef8f-114">4.8</span></span>|
|<span data-ttu-id="9ef8f-115">Tür</span><span class="sxs-lookup"><span data-stu-id="9ef8f-115">Type</span></span>|<span data-ttu-id="9ef8f-116">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="9ef8f-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9ef8f-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="9ef8f-117">Affected APIs</span></span>

-<xref:System.Web.UI.WebControls.CheckBox?displayProperty=nameWithType></li></ul>|
