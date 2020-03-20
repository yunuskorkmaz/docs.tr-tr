---
ms.openlocfilehash: 0a3dc43ebdc58d54675f2264a8ee56d9f4358cd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859211"
---
### <a name="wcf-message-security-now-is-able-to-use-tls11-and-tls12"></a><span data-ttu-id="bd0b9-101">WCF mesaj güvenliği artık TLS1.1 ve TLS1.2'yi kullanabiliyor</span><span class="sxs-lookup"><span data-stu-id="bd0b9-101">WCF message security now is able to use TLS1.1 and TLS1.2</span></span>

|   |   |
|---|---|
|<span data-ttu-id="bd0b9-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="bd0b9-102">Details</span></span>|<span data-ttu-id="bd0b9-103">.NET Framework 4.7'den başlayarak, müşteriler uygulama yapılandırma ayarları üzerinden SSL3.0 ve TLS1.0'a ek olarak WCF mesaj güvenliğinde TLS1.1 veya TLS1.2'yi yapılandırabilirler.</span><span class="sxs-lookup"><span data-stu-id="bd0b9-103">Starting in the .NET Framework 4.7, customers can configure either TLS1.1 or TLS1.2 in WCF message security in addition to SSL3.0 and TLS1.0 through application configuration settings.</span></span>|
|<span data-ttu-id="bd0b9-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="bd0b9-104">Suggestion</span></span>|<span data-ttu-id="bd0b9-105">.NET Framework 4.7'de, WCF ileti güvenliğinde TLS1.1 ve TLS1.2 desteği varsayılan olarak devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="bd0b9-105">In the .NET Framework 4.7, support for TLS1.1 and TLS1.2 in WCF message security is disabled by default.</span></span> <span data-ttu-id="bd0b9-106">App.config veya web.config <code>&lt;runtime&gt;</code> dosyasıbölümüne aşağıdaki satırı ekleyerek etkinleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bd0b9-106">You can enable it by adding the following line to the <code>&lt;runtime&gt;</code> section of the app.config or web.config file:</span></span><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="bd0b9-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="bd0b9-107">Scope</span></span>|<span data-ttu-id="bd0b9-108">Edge</span><span class="sxs-lookup"><span data-stu-id="bd0b9-108">Edge</span></span>|
|<span data-ttu-id="bd0b9-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="bd0b9-109">Version</span></span>|<span data-ttu-id="bd0b9-110">4.7</span><span class="sxs-lookup"><span data-stu-id="bd0b9-110">4.7</span></span>|
|<span data-ttu-id="bd0b9-111">Tür</span><span class="sxs-lookup"><span data-stu-id="bd0b9-111">Type</span></span>|<span data-ttu-id="bd0b9-112">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="bd0b9-112">Retargeting</span></span>|
