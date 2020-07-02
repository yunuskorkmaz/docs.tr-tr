---
ms.openlocfilehash: 23e278d38d6904d8afe927e6b54c388d443e41f5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616098"
---
### <a name="signedxmlgetpublickey-returns-rsacng-on-net462-or-lightup-without-retargeting-change"></a><span data-ttu-id="aea50-101">SignedXml. GetPublicKey yeniden hedefleme değişikliği olmadan net462 (veya açıklamadan) üzerinde RSACng döndürüyor</span><span class="sxs-lookup"><span data-stu-id="aea50-101">SignedXml.GetPublicKey returns RSACng on net462 (or lightup) without retargeting change</span></span>

#### <a name="details"></a><span data-ttu-id="aea50-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="aea50-102">Details</span></span>

<span data-ttu-id="aea50-103">.NET Framework 4.6.2 ile başlayarak, yöntem tarafından döndürülen nesnenin somut türü <xref:System.Security.Cryptography.Xml.SignedXml.GetPublicKey%2A?displayProperty=nameWithType> (bir olağandışı bir şekilde), bir CryptoServiceProvider uygulamasından CNG uygulamasına değişti.</span><span class="sxs-lookup"><span data-stu-id="aea50-103">Starting with the .NET Framework 4.6.2, the concrete type of the object returned by the <xref:System.Security.Cryptography.Xml.SignedXml.GetPublicKey%2A?displayProperty=nameWithType> method changed (without a quirk) from a CryptoServiceProvider implementation to a Cng implementation.</span></span> <span data-ttu-id="aea50-104">Bunun nedeni, uygulamanın ' i `certificate.PublicKey.Key` ileten iç öğesini kullanmaya değiştiği `certificate.GetAnyPublicKey` anlamına gelir <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="aea50-104">This is because the implementation changed from using `certificate.PublicKey.Key` to using the internal `certificate.GetAnyPublicKey` which forwards to <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey%2A?displayProperty=nameWithType>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="aea50-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="aea50-105">Suggestion</span></span>

<span data-ttu-id="aea50-106">.NET Framework 4.7.1 üzerinde çalışan uygulamalardan başlayarak, uygulama yapılandırma dosyanızın [çalışma zamanı](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) bölümüne aşağıdaki yapılandırma anahtarını ekleyerek .NET Framework 4.6.1 ve önceki sürümlerde varsayılan olarak kullanılan CryptoServiceProvider kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="aea50-106">Starting with apps running on the .NET Framework 4.7.1, you can use the CryptoServiceProvider implementation used by default in the .NET Framework 4.6.1 and earlier versions by adding the following configuration switch to the [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app config file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.Xml.SignedXmlUseLegacyCertificatePrivateKey=true" />
```

| <span data-ttu-id="aea50-107">Name</span><span class="sxs-lookup"><span data-stu-id="aea50-107">Name</span></span>    | <span data-ttu-id="aea50-108">Değer</span><span class="sxs-lookup"><span data-stu-id="aea50-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="aea50-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="aea50-109">Scope</span></span>   | <span data-ttu-id="aea50-110">Edge</span><span class="sxs-lookup"><span data-stu-id="aea50-110">Edge</span></span>        |
| <span data-ttu-id="aea50-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="aea50-111">Version</span></span> | <span data-ttu-id="aea50-112">4.6.2</span><span class="sxs-lookup"><span data-stu-id="aea50-112">4.6.2</span></span>       |
| <span data-ttu-id="aea50-113">Tür</span><span class="sxs-lookup"><span data-stu-id="aea50-113">Type</span></span>    | <span data-ttu-id="aea50-114">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="aea50-114">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="aea50-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="aea50-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignatureReturningKey(System.Security.Cryptography.AsymmetricAlgorithm@)?displayProperty=nameWithType>
