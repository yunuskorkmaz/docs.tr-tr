---
ms.openlocfilehash: 0a3dc43ebdc58d54675f2264a8ee56d9f4358cd8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61759509"
---
### <a name="wcf-message-security-now-is-able-to-use-tls11-and-tls12"></a><span data-ttu-id="e143e-101">WCF ileti güvenliğini TLS1.1 ve TLS1.2 kullanabilir</span><span class="sxs-lookup"><span data-stu-id="e143e-101">WCF message security now is able to use TLS1.1 and TLS1.2</span></span>

|   |   |
|---|---|
|<span data-ttu-id="e143e-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="e143e-102">Details</span></span>|<span data-ttu-id="e143e-103">İçinde .NET Framework 4.7 başlayarak, müşterilerin TLS1.1 ya da TLS1.2 SSL3.0 ve TLS1.0 yanı sıra WCF ileti güvenliğini uygulama yapılandırma ayarları ile yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e143e-103">Starting in the .NET Framework 4.7, customers can configure either TLS1.1 or TLS1.2 in WCF message security in addition to SSL3.0 and TLS1.0 through application configuration settings.</span></span>|
|<span data-ttu-id="e143e-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="e143e-104">Suggestion</span></span>|<span data-ttu-id="e143e-105">.NET Framework 4.7 WCF ileti güvenliğini TLS1.1 ve TLS1.2 için destek, varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="e143e-105">In the .NET Framework 4.7, support for TLS1.1 and TLS1.2 in WCF message security is disabled by default.</span></span> <span data-ttu-id="e143e-106">Aşağıdaki satırı ekleyerek etkinleştirebilirsiniz <code>&lt;runtime&gt;</code> app.config veya web.config dosyasının:</span><span class="sxs-lookup"><span data-stu-id="e143e-106">You can enable it by adding the following line to the <code>&lt;runtime&gt;</code> section of the app.config or web.config file:</span></span><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="e143e-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="e143e-107">Scope</span></span>|<span data-ttu-id="e143e-108">Kenar</span><span class="sxs-lookup"><span data-stu-id="e143e-108">Edge</span></span>|
|<span data-ttu-id="e143e-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="e143e-109">Version</span></span>|<span data-ttu-id="e143e-110">4.7</span><span class="sxs-lookup"><span data-stu-id="e143e-110">4.7</span></span>|
|<span data-ttu-id="e143e-111">Tür</span><span class="sxs-lookup"><span data-stu-id="e143e-111">Type</span></span>|<span data-ttu-id="e143e-112">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="e143e-112">Retargeting</span></span>|
