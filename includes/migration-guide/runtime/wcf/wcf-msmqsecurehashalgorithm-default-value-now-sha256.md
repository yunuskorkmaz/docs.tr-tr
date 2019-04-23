---
ms.openlocfilehash: ce8e162e11802de1b06bfbc63d5c55de67ef23df
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59805330"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a><span data-ttu-id="84f99-101">WCF MsmqSecureHashAlgorithm varsayılan değer SHA256 şimdi:</span><span class="sxs-lookup"><span data-stu-id="84f99-101">WCF MsmqSecureHashAlgorithm default value is now SHA256</span></span>

|   |   |
|---|---|
|<span data-ttu-id="84f99-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="84f99-102">Details</span></span>|<span data-ttu-id="84f99-103">.NET Framework 4.7.1 ile başlayarak, imza algoritması wcf'de Msmq iletileri için varsayılan SHA256 iletisidir.</span><span class="sxs-lookup"><span data-stu-id="84f99-103">Starting with the .NET Framework 4.7.1, the default message signing algorithm in WCF for Msmq messages is SHA256.</span></span> <span data-ttu-id="84f99-104">.NET Framework 4.7 ve önceki sürümleri, imza algoritması varsayılan ileti SHA1 ' dir.</span><span class="sxs-lookup"><span data-stu-id="84f99-104">In the .NET Framework 4.7 and earlier versions, the default message signing algorithm is SHA1.</span></span>|
|<span data-ttu-id="84f99-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="84f99-105">Suggestion</span></span>|<span data-ttu-id="84f99-106">.NET Framework 4.7.1 uyumluluk sorunları bu değişikliği halinde çalıştırın ya da daha sonra değişikliğin aşağıdaki satırı ekleyerek çevirme <code>&lt;runtime&gt;</code>app.config dosyanıza bölümünü:</span><span class="sxs-lookup"><span data-stu-id="84f99-106">If you run into compatibility issues with this change on the .NET Framework 4.7.1 or later, you can opt-out the change by adding the following line to the <code>&lt;runtime&gt;</code>section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="84f99-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="84f99-107">Scope</span></span>|<span data-ttu-id="84f99-108">İkincil</span><span class="sxs-lookup"><span data-stu-id="84f99-108">Minor</span></span>|
|<span data-ttu-id="84f99-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="84f99-109">Version</span></span>|<span data-ttu-id="84f99-110">4.7.1</span><span class="sxs-lookup"><span data-stu-id="84f99-110">4.7.1</span></span>|
|<span data-ttu-id="84f99-111">Tür</span><span class="sxs-lookup"><span data-stu-id="84f99-111">Type</span></span>|<span data-ttu-id="84f99-112">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="84f99-112">Runtime</span></span>|
