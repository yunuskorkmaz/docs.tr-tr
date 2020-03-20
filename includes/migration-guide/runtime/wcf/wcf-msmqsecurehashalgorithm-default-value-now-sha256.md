---
ms.openlocfilehash: ce8e162e11802de1b06bfbc63d5c55de67ef23df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857253"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a><span data-ttu-id="25db2-101">WCF MsmqSecureHashAlgorithm varsayılan değeri şimdi SHA256 olduğunu</span><span class="sxs-lookup"><span data-stu-id="25db2-101">WCF MsmqSecureHashAlgorithm default value is now SHA256</span></span>

|   |   |
|---|---|
|<span data-ttu-id="25db2-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="25db2-102">Details</span></span>|<span data-ttu-id="25db2-103">.NET Framework 4.7.1 ile başlayarak, Msmq iletileri için WCF'deki varsayılan ileti imzalama algoritması SHA256'dır.</span><span class="sxs-lookup"><span data-stu-id="25db2-103">Starting with the .NET Framework 4.7.1, the default message signing algorithm in WCF for Msmq messages is SHA256.</span></span> <span data-ttu-id="25db2-104">.NET Framework 4.7 ve önceki sürümlerinde varsayılan ileti imzalama algoritması SHA1'dir.</span><span class="sxs-lookup"><span data-stu-id="25db2-104">In the .NET Framework 4.7 and earlier versions, the default message signing algorithm is SHA1.</span></span>|
|<span data-ttu-id="25db2-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="25db2-105">Suggestion</span></span>|<span data-ttu-id="25db2-106">.NET Framework 4.7.1 veya sonraki düzey bu değişiklikle uyumluluk sorunlarıyla karşınıza çıkarsa, app.config <code>&lt;runtime&gt;</code>dosyanızın bölümüne aşağıdaki satırı ekleyerek değişikliği devre dışı kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="25db2-106">If you run into compatibility issues with this change on the .NET Framework 4.7.1 or later, you can opt-out the change by adding the following line to the <code>&lt;runtime&gt;</code>section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="25db2-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="25db2-107">Scope</span></span>|<span data-ttu-id="25db2-108">İkincil</span><span class="sxs-lookup"><span data-stu-id="25db2-108">Minor</span></span>|
|<span data-ttu-id="25db2-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="25db2-109">Version</span></span>|<span data-ttu-id="25db2-110">4.7.1</span><span class="sxs-lookup"><span data-stu-id="25db2-110">4.7.1</span></span>|
|<span data-ttu-id="25db2-111">Tür</span><span class="sxs-lookup"><span data-stu-id="25db2-111">Type</span></span>|<span data-ttu-id="25db2-112">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="25db2-112">Runtime</span></span>|
