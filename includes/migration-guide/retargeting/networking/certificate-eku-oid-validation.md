---
ms.openlocfilehash: c996dafcf65b1fd428be908be346de603ead6e0b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615757"
---
### <a name="certificate-eku-oid-validation"></a><span data-ttu-id="6f818-101">Sertifika EKU OID doğrulaması</span><span class="sxs-lookup"><span data-stu-id="6f818-101">Certificate EKU OID validation</span></span>

#### <a name="details"></a><span data-ttu-id="6f818-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="6f818-102">Details</span></span>

<span data-ttu-id="6f818-103">.NET Framework 4,6 ' den başlayarak, <xref:System.Net.Security.SslStream> veya <xref:System.Net.ServicePointManager> sınıfları gelişmiş anahtar kullanımı (EKU) nesne tanımlayıcısı (OID) doğrulaması gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="6f818-103">Starting with .NET Framework 4.6, the <xref:System.Net.Security.SslStream> or <xref:System.Net.ServicePointManager> classes perform enhanced key use (EKU) object identifier (OID) validation.</span></span> <span data-ttu-id="6f818-104">Gelişmiş anahtar kullanımı (EKU) uzantısı, anahtarı kullanan uygulamaları belirten bir nesne tanımlayıcıları (OID) koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="6f818-104">An enhanced key usage (EKU) extension is a collection of object identifiers (OIDs) that indicate the applications that use the key.</span></span> <span data-ttu-id="6f818-105">EKU OID doğrulaması, uzak sertifikanın amaçlanan amaç için doğru OID 'ler olduğundan emin olmak için uzak sertifika geri çağırmaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="6f818-105">EKU OID validation uses remote certificate callbacks to ensure that the remote certificate has the correct OIDs for the intended purpose.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6f818-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="6f818-106">Suggestion</span></span>

<span data-ttu-id="6f818-107">Bu değişiklik istenmeyen ise, [\<AppContextSwitchOverrides>](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) uygulama yapılandırma dosyanızdaki öğesine aşağıdaki anahtarı ekleyerek SERTIFIKA EKU OID doğrulamasını devre dışı bırakabilirsiniz [\`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) :</span><span class="sxs-lookup"><span data-stu-id="6f818-107">If this change is undesirable, you can disable certificate EKU OID validation by adding the following switch to the [\<AppContextSwitchOverrides>](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) in the [\`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) of your app configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Net.DontCheckCertificateEKUs=true" />
</runtime>
```

> [!IMPORTANT]
> <span data-ttu-id="6f818-108">Bu ayar yalnızca geriye dönük uyumluluk için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="6f818-108">This setting is provided for backward compatibility only.</span></span> <span data-ttu-id="6f818-109">Aksi takdirde kullanılması önerilmez.</span><span class="sxs-lookup"><span data-stu-id="6f818-109">Its use is otherwise not recommended.</span></span>

| <span data-ttu-id="6f818-110">Name</span><span class="sxs-lookup"><span data-stu-id="6f818-110">Name</span></span>    | <span data-ttu-id="6f818-111">Değer</span><span class="sxs-lookup"><span data-stu-id="6f818-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6f818-112">Kapsam</span><span class="sxs-lookup"><span data-stu-id="6f818-112">Scope</span></span>   | <span data-ttu-id="6f818-113">İkincil</span><span class="sxs-lookup"><span data-stu-id="6f818-113">Minor</span></span>       |
| <span data-ttu-id="6f818-114">Sürüm</span><span class="sxs-lookup"><span data-stu-id="6f818-114">Version</span></span> | <span data-ttu-id="6f818-115">4.6</span><span class="sxs-lookup"><span data-stu-id="6f818-115">4.6</span></span>         |
| <span data-ttu-id="6f818-116">Tür</span><span class="sxs-lookup"><span data-stu-id="6f818-116">Type</span></span>    | <span data-ttu-id="6f818-117">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="6f818-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="6f818-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="6f818-118">Affected APIs</span></span>

- <xref:System.Net.Security.SslStream?displayProperty=nameWithType>
- <xref:System.Net.ServicePointManager?displayProperty=nameWithType>
- <xref:System.Net.Http.HttpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.FtpWebRequest?displayProperty=nameWithType>
