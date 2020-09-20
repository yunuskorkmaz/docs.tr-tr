---
ms.openlocfilehash: 7c0227980aa5d90f3788783088bcd7cd9509ed66
ms.sourcegitcommit: 261e0c98a111357692b3b63c596edf0cacf72991
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2020
ms.locfileid: "90770963"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a><span data-ttu-id="7205c-101">WCF MsmqSecureHashAlgorithm varsayılan değeri artık SHA256</span><span class="sxs-lookup"><span data-stu-id="7205c-101">WCF MsmqSecureHashAlgorithm default value is now SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="7205c-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="7205c-102">Details</span></span>

<span data-ttu-id="7205c-103">.NET Framework 4.7.1 başlayarak, MSMQ iletileri için WCF 'de varsayılan ileti imzalama algoritması SHA256 ' dir.</span><span class="sxs-lookup"><span data-stu-id="7205c-103">Starting with the .NET Framework 4.7.1, the default message signing algorithm in WCF for Msmq messages is SHA256.</span></span> <span data-ttu-id="7205c-104">.NET Framework 4,7 ve önceki sürümlerde, varsayılan ileti imzalama algoritması SHA1 ' dır.</span><span class="sxs-lookup"><span data-stu-id="7205c-104">In the .NET Framework 4.7 and earlier versions, the default message signing algorithm is SHA1.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7205c-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="7205c-105">Suggestion</span></span>

<span data-ttu-id="7205c-106">Bu değişiklik ile .NET Framework 4.7.1 veya sonraki bir sürümde uyumluluk sorunları yaşıyorsanız, app.config dosyanızın bölümüne aşağıdaki satırı ekleyerek değişikliği devre dışı bırakabilirsiniz `<runtime>` :</span><span class="sxs-lookup"><span data-stu-id="7205c-106">If you run into compatibility issues with this change on the .NET Framework 4.7.1 or later, you can opt-out the change by adding the following line to the `<runtime>` section of your app.config file:</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; />
  </runtime>
</configuration>
```

| <span data-ttu-id="7205c-107">Name</span><span class="sxs-lookup"><span data-stu-id="7205c-107">Name</span></span>    | <span data-ttu-id="7205c-108">Değer</span><span class="sxs-lookup"><span data-stu-id="7205c-108">Value</span></span>   |
|:--------|:--------|
| <span data-ttu-id="7205c-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="7205c-109">Scope</span></span>   | <span data-ttu-id="7205c-110">İkincil</span><span class="sxs-lookup"><span data-stu-id="7205c-110">Minor</span></span>   |
| <span data-ttu-id="7205c-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="7205c-111">Version</span></span> | <span data-ttu-id="7205c-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="7205c-112">4.7.1</span></span>   |
| <span data-ttu-id="7205c-113">Tür</span><span class="sxs-lookup"><span data-stu-id="7205c-113">Type</span></span>    | <span data-ttu-id="7205c-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="7205c-114">Runtime</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="7205c-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="7205c-115">Affected APIs</span></span>

<span data-ttu-id="7205c-116">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="7205c-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
