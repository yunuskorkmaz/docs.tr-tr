---
ms.openlocfilehash: 318609c15d2e0b9a7ee59b38463735b33ef87974
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857240"
---
### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a><span data-ttu-id="86fd4-101">WCF PipeConnection.GetHashAlgorithm şimdi SHA256 kullanır</span><span class="sxs-lookup"><span data-stu-id="86fd4-101">WCF PipeConnection.GetHashAlgorithm now uses SHA256</span></span>

|   |   |
|---|---|
|<span data-ttu-id="86fd4-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="86fd4-102">Details</span></span>|<span data-ttu-id="86fd4-103">.NET Framework 4.7.1 ile başlayarak, Windows Communication Foundation adlandırılmış borular için rasgele adlar oluşturmak için sha256 karma kullanır.</span><span class="sxs-lookup"><span data-stu-id="86fd4-103">Starting with the .NET Framework 4.7.1, Windows Communication Foundation uses a SHA256 hash to generate random names for named pipes.</span></span> <span data-ttu-id="86fd4-104">.NET Framework 4.7 ve önceki sürümlerinde SHA1 karma kullanılmıştır.</span><span class="sxs-lookup"><span data-stu-id="86fd4-104">In the .NET Framework 4.7 and earlier versions, it used a SHA1 hash.</span></span>|
|<span data-ttu-id="86fd4-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="86fd4-105">Suggestion</span></span>|<span data-ttu-id="86fd4-106">.NET Framework 4.7.1 veya sonraki düzey bu değişiklikle uyumluluk sorunuyla karşınıza çıkarsa, app.config dosyanızın <code>&lt;runtime&gt;</code> bölümüne aşağıdaki satırı ekleyerek bu değişikliği devre dışı kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="86fd4-106">If you run into compatibility issue with this change on the .NET Framework 4.7.1 or later, you can opt-out it by adding the following line to the <code>&lt;runtime&gt;</code> section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="86fd4-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="86fd4-107">Scope</span></span>|<span data-ttu-id="86fd4-108">İkincil</span><span class="sxs-lookup"><span data-stu-id="86fd4-108">Minor</span></span>|
|<span data-ttu-id="86fd4-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="86fd4-109">Version</span></span>|<span data-ttu-id="86fd4-110">4.7.1</span><span class="sxs-lookup"><span data-stu-id="86fd4-110">4.7.1</span></span>|
|<span data-ttu-id="86fd4-111">Tür</span><span class="sxs-lookup"><span data-stu-id="86fd4-111">Type</span></span>|<span data-ttu-id="86fd4-112">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="86fd4-112">Runtime</span></span>|
