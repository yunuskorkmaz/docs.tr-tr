---
ms.openlocfilehash: a2d4b7592727ca20ee79867094d6972eb9c4baed
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67857253"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a><span data-ttu-id="164bf-101">WCF MsmqSecureHashAlgorithm varsayılan değer SHA256 şimdi:</span><span class="sxs-lookup"><span data-stu-id="164bf-101">WCF MsmqSecureHashAlgorithm default value is now SHA256</span></span>

|   |   |
|---|---|
|<span data-ttu-id="164bf-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="164bf-102">Details</span></span>|<span data-ttu-id="164bf-103">.NET Framework 4.7.1 ile başlayarak, imza algoritması wcf'de Msmq iletileri için varsayılan SHA256 iletisidir.</span><span class="sxs-lookup"><span data-stu-id="164bf-103">Starting with the .NET Framework 4.7.1, the default message signing algorithm in WCF for Msmq messages is SHA256.</span></span> <span data-ttu-id="164bf-104">.NET Framework 4.7 ve önceki sürümleri, imza algoritması varsayılan ileti SHA1 ' dir.</span><span class="sxs-lookup"><span data-stu-id="164bf-104">In the .NET Framework 4.7 and earlier versions, the default message signing algorithm is SHA1.</span></span>|
|<span data-ttu-id="164bf-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="164bf-105">Suggestion</span></span>|<span data-ttu-id="164bf-106">.NET Framework 4.7.1 uyumluluk sorunları bu değişikliği halinde çalıştırın ya da daha sonra değişikliğin aşağıdaki satırı ekleyerek çevirme <code>&lt;runtime&gt;</code>app.config dosyanıza bölümünü:</span><span class="sxs-lookup"><span data-stu-id="164bf-106">If you run into compatibility issues with this change on the .NET Framework 4.7.1 or later, you can opt-out the change by adding the following line to the <code>&lt;runtime&gt;</code>section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="164bf-107">`Scope`</span><span class="sxs-lookup"><span data-stu-id="164bf-107">Scope</span></span>|<span data-ttu-id="164bf-108">Küçük</span><span class="sxs-lookup"><span data-stu-id="164bf-108">Minor</span></span>|
|<span data-ttu-id="164bf-109">Version</span><span class="sxs-lookup"><span data-stu-id="164bf-109">Version</span></span>|<span data-ttu-id="164bf-110">4.7.1</span><span class="sxs-lookup"><span data-stu-id="164bf-110">4.7.1</span></span>|
|<span data-ttu-id="164bf-111">Type</span><span class="sxs-lookup"><span data-stu-id="164bf-111">Type</span></span>|<span data-ttu-id="164bf-112">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="164bf-112">Runtime</span></span>|

