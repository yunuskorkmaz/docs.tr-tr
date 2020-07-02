---
ms.openlocfilehash: e2ae329d027d605e6331afe422e550990fab1042
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614814"
---
### <a name="default-signedxml-and-signedxms-algorithms-changed-to-sha256"></a><span data-ttu-id="0b701-101">Varsayılan SignedXML ve SignedXMS algoritmaları SHA256 olarak değiştirildi</span><span class="sxs-lookup"><span data-stu-id="0b701-101">Default SignedXML and SignedXMS algorithms changed to SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="0b701-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="0b701-102">Details</span></span>

<span data-ttu-id="0b701-103">.NET Framework 4,7 ve önceki sürümlerde, SignedXML ve SignedCMS varsayılan olarak bazı işlemler için SHA1 ' ya yöneliktir. .NET Framework 4.7.1 başlayarak, bu işlemler için SHA256 varsayılan olarak etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="0b701-103">In the .NET Framework 4.7 and earlier, SignedXML and SignedCMS default to SHA1 for some operations.Starting with the .NET Framework 4.7.1, SHA256 is enabled by default for these operations.</span></span> <span data-ttu-id="0b701-104">Bu değişiklik gereklidir çünkü SHA1 artık güvenli olarak kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="0b701-104">This change is necessary because SHA1 is no longer considered to be secure.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="0b701-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="0b701-105">Suggestion</span></span>

<span data-ttu-id="0b701-106">Varsayılan olarak SHA1 (güvensiz) veya SHA256 kullanılıp kullanılmayacağını denetlemek için iki yeni bağlam anahtarı değeri vardır:</span><span class="sxs-lookup"><span data-stu-id="0b701-106">There are two new context switch values to control whether SHA1 (insecure) or SHA256 is used by default:</span></span>

- <span data-ttu-id="0b701-107">Switch.System.Security.Cryptography.Xml. Useınsecurehashalgoritmalarını</span><span class="sxs-lookup"><span data-stu-id="0b701-107">Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms</span></span>
- <span data-ttu-id="0b701-108">Switch.SysTem. Security. Cryptography. Pkcs. Useınsecurehashalgoritmalarını .NET Framework 4.7.1 ve sonraki sürümlerini hedefleyen uygulamalar Için, SHA256 kullanımı istenmeyen bir değer değilse, uygulama yapılandırma dosyanızın [çalışma zamanı](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) bölümüne aşağıdaki yapılandırma anahtarını ekleyerek varsayılan değeri SHA1 olarak geri yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0b701-108">Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms For applications that target the .NET Framework 4.7.1 and later versions, if the use of SHA256 is undesirable, you can restore the default to SHA1 by adding the following configuration switch to the [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app config file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=true;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=true" />
```

<span data-ttu-id="0b701-109">.NET Framework 4,7 ve önceki sürümlerini hedefleyen uygulamalar için, uygulama yapılandırma dosyanızın [çalışma zamanı](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) bölümüne aşağıdaki yapılandırma anahtarını ekleyerek bu değişikliği tercih edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0b701-109">For applications that target the .NET Framework 4.7 and earlier versions, you can opt into this change by adding the following configuration switch to the [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app config file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=false;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=false" />
```

| <span data-ttu-id="0b701-110">Name</span><span class="sxs-lookup"><span data-stu-id="0b701-110">Name</span></span>    | <span data-ttu-id="0b701-111">Değer</span><span class="sxs-lookup"><span data-stu-id="0b701-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="0b701-112">Kapsam</span><span class="sxs-lookup"><span data-stu-id="0b701-112">Scope</span></span>   | <span data-ttu-id="0b701-113">İkincil</span><span class="sxs-lookup"><span data-stu-id="0b701-113">Minor</span></span>       |
| <span data-ttu-id="0b701-114">Sürüm</span><span class="sxs-lookup"><span data-stu-id="0b701-114">Version</span></span> | <span data-ttu-id="0b701-115">4.7.1</span><span class="sxs-lookup"><span data-stu-id="0b701-115">4.7.1</span></span>       |
| <span data-ttu-id="0b701-116">Tür</span><span class="sxs-lookup"><span data-stu-id="0b701-116">Type</span></span>    | <span data-ttu-id="0b701-117">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="0b701-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="0b701-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="0b701-118">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Pkcs.CmsSigner?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Xml.Reference?displayProperty=nameWithType>
