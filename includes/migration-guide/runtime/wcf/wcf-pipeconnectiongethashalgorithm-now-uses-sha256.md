---
ms.openlocfilehash: 318609c15d2e0b9a7ee59b38463735b33ef87974
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59805267"
---
### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a><span data-ttu-id="e6187-101">WCF PipeConnection.GetHashAlgorithm SHA256 artık kullanır.</span><span class="sxs-lookup"><span data-stu-id="e6187-101">WCF PipeConnection.GetHashAlgorithm now uses SHA256</span></span>

|   |   |
|---|---|
|<span data-ttu-id="e6187-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="e6187-102">Details</span></span>|<span data-ttu-id="e6187-103">.NET Framework 4.7.1 ile başlayarak, Windows Communication Foundation SHA256 karma rastgele adları için adlandırılmış kanallar oluşturmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="e6187-103">Starting with the .NET Framework 4.7.1, Windows Communication Foundation uses a SHA256 hash to generate random names for named pipes.</span></span> <span data-ttu-id="e6187-104">.NET Framework 4.7 ve önceki sürümlerinde SHA1 karması kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e6187-104">In the .NET Framework 4.7 and earlier versions, it used a SHA1 hash.</span></span>|
|<span data-ttu-id="e6187-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="e6187-105">Suggestion</span></span>|<span data-ttu-id="e6187-106">.NET Framework 4.7.1 Bu değişiklik ile uyumluluk sorunu içine çalıştırın ya da daha sonra bunu aşağıdaki satırı ekleyerek çevirme <code>&lt;runtime&gt;</code> app.config dosyanıza bölümünü:</span><span class="sxs-lookup"><span data-stu-id="e6187-106">If you run into compatibility issue with this change on the .NET Framework 4.7.1 or later, you can opt-out it by adding the following line to the <code>&lt;runtime&gt;</code> section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="e6187-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="e6187-107">Scope</span></span>|<span data-ttu-id="e6187-108">İkincil</span><span class="sxs-lookup"><span data-stu-id="e6187-108">Minor</span></span>|
|<span data-ttu-id="e6187-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="e6187-109">Version</span></span>|<span data-ttu-id="e6187-110">4.7.1</span><span class="sxs-lookup"><span data-stu-id="e6187-110">4.7.1</span></span>|
|<span data-ttu-id="e6187-111">Tür</span><span class="sxs-lookup"><span data-stu-id="e6187-111">Type</span></span>|<span data-ttu-id="e6187-112">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="e6187-112">Runtime</span></span>|
