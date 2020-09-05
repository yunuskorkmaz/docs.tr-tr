---
ms.openlocfilehash: d32725b0d3063d3320b73e02039ff567090da932
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497931"
---
### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a><span data-ttu-id="e1897-101">WCF PipeConnection. GetHashAlgorithm artık SHA256 kullanıyor</span><span class="sxs-lookup"><span data-stu-id="e1897-101">WCF PipeConnection.GetHashAlgorithm now uses SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="e1897-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="e1897-102">Details</span></span>

<span data-ttu-id="e1897-103">Windows Communication Foundation .NET Framework başlayarak, adlandırılmış kanallar için rastgele adlar oluşturmak üzere bir SHA256 karması kullanır.</span><span class="sxs-lookup"><span data-stu-id="e1897-103">Starting with the .NET Framework 4.7.1, Windows Communication Foundation uses a SHA256 hash to generate random names for named pipes.</span></span> <span data-ttu-id="e1897-104">.NET Framework 4,7 ve önceki sürümlerde, bir SHA1 karması kullandı.</span><span class="sxs-lookup"><span data-stu-id="e1897-104">In the .NET Framework 4.7 and earlier versions, it used a SHA1 hash.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e1897-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="e1897-105">Suggestion</span></span>

<span data-ttu-id="e1897-106">Bu değişiklik ile .NET Framework 4.7.1 veya sonraki bir sürümde uyumluluk sorunuyla karşılaşırsanız, app.config dosyanızın bölümüne aşağıdaki satırı ekleyerek geri alabilirsiniz <code>&lt;runtime&gt;</code> :</span><span class="sxs-lookup"><span data-stu-id="e1897-106">If you run into compatibility issue with this change on the .NET Framework 4.7.1 or later, you can opt-out it by adding the following line to the <code>&lt;runtime&gt;</code> section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="e1897-107">Name</span><span class="sxs-lookup"><span data-stu-id="e1897-107">Name</span></span>    | <span data-ttu-id="e1897-108">Değer</span><span class="sxs-lookup"><span data-stu-id="e1897-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e1897-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="e1897-109">Scope</span></span>   |<span data-ttu-id="e1897-110">İkincil</span><span class="sxs-lookup"><span data-stu-id="e1897-110">Minor</span></span>|
|<span data-ttu-id="e1897-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="e1897-111">Version</span></span>|<span data-ttu-id="e1897-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="e1897-112">4.7.1</span></span>|
|<span data-ttu-id="e1897-113">Tür</span><span class="sxs-lookup"><span data-stu-id="e1897-113">Type</span></span>|<span data-ttu-id="e1897-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="e1897-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="e1897-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="e1897-115">Affected APIs</span></span>

<span data-ttu-id="e1897-116">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="e1897-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
