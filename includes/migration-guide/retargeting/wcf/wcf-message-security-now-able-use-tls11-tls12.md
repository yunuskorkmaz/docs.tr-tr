---
ms.openlocfilehash: c646372104457e8bc5d418744847f3ee771c8d8b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614801"
---
### <a name="wcf-message-security-now-is-able-to-use-tls11-and-tls12"></a><span data-ttu-id="69107-101">WCF ileti güvenliği artık TLS 1.1 ve TLS 1.2 kullanabiliyor</span><span class="sxs-lookup"><span data-stu-id="69107-101">WCF message security now is able to use TLS1.1 and TLS1.2</span></span>

#### <a name="details"></a><span data-ttu-id="69107-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="69107-102">Details</span></span>

<span data-ttu-id="69107-103">.NET Framework 4,7 ' den başlayarak, müşteriler, uygulama yapılandırma ayarları aracılığıyla SSL 3.0 ve TLS 1.0 ' a ek olarak WCF ileti güvenliği 'nde TLS 1.1 veya TLS 1.2 'yi yapılandırabilir.</span><span class="sxs-lookup"><span data-stu-id="69107-103">Starting in the .NET Framework 4.7, customers can configure either TLS1.1 or TLS1.2 in WCF message security in addition to SSL3.0 and TLS1.0 through application configuration settings.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="69107-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="69107-104">Suggestion</span></span>

<span data-ttu-id="69107-105">.NET Framework 4,7 ' de, WCF ileti güvenliği 'nde TLS 1.1 ve TLS 1.2 desteği varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="69107-105">In the .NET Framework 4.7, support for TLS1.1 and TLS1.2 in WCF message security is disabled by default.</span></span> <span data-ttu-id="69107-106">`<runtime>`app.config veya web.config dosyasının bölümüne aşağıdaki satırı ekleyerek etkinleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="69107-106">You can enable it by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false" />
</runtime>
```

| <span data-ttu-id="69107-107">Name</span><span class="sxs-lookup"><span data-stu-id="69107-107">Name</span></span>    | <span data-ttu-id="69107-108">Değer</span><span class="sxs-lookup"><span data-stu-id="69107-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="69107-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="69107-109">Scope</span></span>   | <span data-ttu-id="69107-110">Edge</span><span class="sxs-lookup"><span data-stu-id="69107-110">Edge</span></span>        |
| <span data-ttu-id="69107-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="69107-111">Version</span></span> | <span data-ttu-id="69107-112">4,7</span><span class="sxs-lookup"><span data-stu-id="69107-112">4.7</span></span>         |
| <span data-ttu-id="69107-113">Tür</span><span class="sxs-lookup"><span data-stu-id="69107-113">Type</span></span>    | <span data-ttu-id="69107-114">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="69107-114">Retargeting</span></span> |
