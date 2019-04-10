---
ms.openlocfilehash: ce8e162e11802de1b06bfbc63d5c55de67ef23df
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236221"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a><span data-ttu-id="30fb4-101">WCF MsmqSecureHashAlgorithm varsayılan değer SHA256 şimdi:</span><span class="sxs-lookup"><span data-stu-id="30fb4-101">WCF MsmqSecureHashAlgorithm default value is now SHA256</span></span>

|   |   |
|---|---|
|<span data-ttu-id="30fb4-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="30fb4-102">Details</span></span>|<span data-ttu-id="30fb4-103">.NET Framework 4.7.1 ile başlayarak, imza algoritması wcf'de Msmq iletileri için varsayılan SHA256 iletisidir.</span><span class="sxs-lookup"><span data-stu-id="30fb4-103">Starting with the .NET Framework 4.7.1, the default message signing algorithm in WCF for Msmq messages is SHA256.</span></span> <span data-ttu-id="30fb4-104">.NET Framework 4.7 ve önceki sürümleri, imza algoritması varsayılan ileti SHA1 ' dir.</span><span class="sxs-lookup"><span data-stu-id="30fb4-104">In the .NET Framework 4.7 and earlier versions, the default message signing algorithm is SHA1.</span></span>|
|<span data-ttu-id="30fb4-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="30fb4-105">Suggestion</span></span>|<span data-ttu-id="30fb4-106">.NET Framework 4.7.1 uyumluluk sorunları bu değişikliği halinde çalıştırın ya da daha sonra değişikliğin aşağıdaki satırı ekleyerek çevirme <code>&lt;runtime&gt;</code>app.config dosyanıza bölümünü:</span><span class="sxs-lookup"><span data-stu-id="30fb4-106">If you run into compatibility issues with this change on the .NET Framework 4.7.1 or later, you can opt-out the change by adding the following line to the <code>&lt;runtime&gt;</code>section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="30fb4-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="30fb4-107">Scope</span></span>|<span data-ttu-id="30fb4-108">İkincil</span><span class="sxs-lookup"><span data-stu-id="30fb4-108">Minor</span></span>|
|<span data-ttu-id="30fb4-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="30fb4-109">Version</span></span>|<span data-ttu-id="30fb4-110">4.7.1</span><span class="sxs-lookup"><span data-stu-id="30fb4-110">4.7.1</span></span>|
|<span data-ttu-id="30fb4-111">Tür</span><span class="sxs-lookup"><span data-stu-id="30fb4-111">Type</span></span>|<span data-ttu-id="30fb4-112">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="30fb4-112">Runtime</span></span>|
