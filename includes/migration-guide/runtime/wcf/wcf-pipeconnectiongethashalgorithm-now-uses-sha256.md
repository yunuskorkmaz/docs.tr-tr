---
ms.openlocfilehash: 9f5f238e3d4222af1da3a1713e1b3e65de6e6f49
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "91024982"
---
### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a><span data-ttu-id="fe469-101">WCF PipeConnection. GetHashAlgorithm artık SHA256 kullanıyor</span><span class="sxs-lookup"><span data-stu-id="fe469-101">WCF PipeConnection.GetHashAlgorithm now uses SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="fe469-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="fe469-102">Details</span></span>

<span data-ttu-id="fe469-103">Windows Communication Foundation .NET Framework başlayarak, adlandırılmış kanallar için rastgele adlar oluşturmak üzere bir SHA256 karması kullanır.</span><span class="sxs-lookup"><span data-stu-id="fe469-103">Starting with the .NET Framework 4.7.1, Windows Communication Foundation uses a SHA256 hash to generate random names for named pipes.</span></span> <span data-ttu-id="fe469-104">.NET Framework 4,7 ve önceki sürümlerde, bir SHA1 karması kullandı.</span><span class="sxs-lookup"><span data-stu-id="fe469-104">In the .NET Framework 4.7 and earlier versions, it used a SHA1 hash.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="fe469-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="fe469-105">Suggestion</span></span>

<span data-ttu-id="fe469-106">Bu değişiklik ile .NET Framework 4.7.1 veya sonraki bir sürümde uyumluluk sorunuyla karşılaşırsanız, app.config dosyanızın bölümüne aşağıdaki satırı ekleyerek geri alabilirsiniz `<runtime>` :</span><span class="sxs-lookup"><span data-stu-id="fe469-106">If you run into compatibility issue with this change on the .NET Framework 4.7.1 or later, you can opt-out it by adding the following line to the `<runtime>` section of your app.config file:</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true" />
  </runtime>
</configuration>
```

| <span data-ttu-id="fe469-107">Ad</span><span class="sxs-lookup"><span data-stu-id="fe469-107">Name</span></span>    | <span data-ttu-id="fe469-108">Değer</span><span class="sxs-lookup"><span data-stu-id="fe469-108">Value</span></span>   |
|:--------|:--------|
| <span data-ttu-id="fe469-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="fe469-109">Scope</span></span>   | <span data-ttu-id="fe469-110">İkincil</span><span class="sxs-lookup"><span data-stu-id="fe469-110">Minor</span></span>   |
| <span data-ttu-id="fe469-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="fe469-111">Version</span></span> | <span data-ttu-id="fe469-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="fe469-112">4.7.1</span></span>   |
| <span data-ttu-id="fe469-113">Tür</span><span class="sxs-lookup"><span data-stu-id="fe469-113">Type</span></span>    | <span data-ttu-id="fe469-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="fe469-114">Runtime</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="fe469-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="fe469-115">Affected APIs</span></span>

<span data-ttu-id="fe469-116">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="fe469-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
