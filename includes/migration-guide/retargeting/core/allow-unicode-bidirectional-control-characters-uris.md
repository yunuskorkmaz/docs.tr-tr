---
ms.openlocfilehash: 53d74db1a77e62cc64250658281fd3e4706fe494
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614631"
---
### <a name="allow-unicode-bidirectional-control-characters-in-uris"></a><span data-ttu-id="051d2-101">URI 'Lerinde Unicode çift yönlü denetim karakterlerine izin ver</span><span class="sxs-lookup"><span data-stu-id="051d2-101">Allow Unicode Bidirectional Control Characters in URIs</span></span>

#### <a name="details"></a><span data-ttu-id="051d2-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="051d2-102">Details</span></span>

<span data-ttu-id="051d2-103">Unicode, metnin yönünü belirtmek için kullanılan birkaç özel denetim karakterini belirtir.</span><span class="sxs-lookup"><span data-stu-id="051d2-103">Unicode specifies several special control characters used to specify the orientation of text.</span></span> <span data-ttu-id="051d2-104">.NET Framework önceki sürümlerinde bu karakterler, yüzde olarak kodlanmış biçiminde olsa bile tüm URI 'lerden yanlış şekilde kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="051d2-104">In previous versions of the .NET Framework, these characters were incorrectly stripped from all URIs even if they were present in their percent-encoded form.</span></span> <span data-ttu-id="051d2-105">[RFC 3987](https://tools.ietf.org/html/rfc3987)' i daha iyi izlemek Için artık URI 'lerinde Bu karakterlere izin veririz.</span><span class="sxs-lookup"><span data-stu-id="051d2-105">In order to better follow [RFC 3987](https://tools.ietf.org/html/rfc3987), we now allow these characters in URIs.</span></span> <span data-ttu-id="051d2-106">URI 'de kodlanmamış olarak bulunursa, yüzde olarak kodlanır.</span><span class="sxs-lookup"><span data-stu-id="051d2-106">When found unencoded in a URI, they are percent-encoded.</span></span> <span data-ttu-id="051d2-107">Yüzde kodlamalı olduğunda, her zaman olduğu gibi kalır.</span><span class="sxs-lookup"><span data-stu-id="051d2-107">When found percent-encoded they are left as-is.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="051d2-108">Öneri</span><span class="sxs-lookup"><span data-stu-id="051d2-108">Suggestion</span></span>

<span data-ttu-id="051d2-109">4.7.2 ile başlayan .NET Framework sürümlerini hedefleyen uygulamalar için, Unicode çift yönlü karakterler için destek varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="051d2-109">For applications that target versions of .NET Framework starting with 4.7.2, support for Unicode bidirectional characters is enabled by default.</span></span> <span data-ttu-id="051d2-110">Bu değişiklik istenmeyen ise, [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) `<runtime>` uygulama yapılandırma dosyasının bölümüne aşağıdaki AppContextSwitchOverrides anahtarını ekleyerek devre dışı bırakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="051d2-110">If this change is undesirable, you can disable it by adding the following [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switch to the `<runtime>` section of the application configuration file:</span></span>

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Uri.DontKeepUnicodeBidiFormattingCharacters=true" />
</runtime>
```

<span data-ttu-id="051d2-111">.NET Framework önceki sürümlerini hedefleyen ancak .NET Framework 4.7.2 ile başlayan sürümler altında çalışan uygulamalar için, Unicode çift yönlü karakterler için destek varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="051d2-111">For applications that target earlier versions of the .NET Framework but are running under versions starting with .NET Framework 4.7.2, support for Unicode bidirectional characters is disabled by default.</span></span> <span data-ttu-id="051d2-112">Aşağıdaki [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) anahtarını `<runtime>` uygulama yapılandırma dosyasının bölümüne ekleyerek etkinleştirebilirsiniz::</span><span class="sxs-lookup"><span data-stu-id="051d2-112">You can enable it by adding the following [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switch to the `<runtime>` section of the application configuration file::</span></span>

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Uri.DontKeepUnicodeBidiFormattingCharacters=false" />
</runtime>
```

| <span data-ttu-id="051d2-113">Name</span><span class="sxs-lookup"><span data-stu-id="051d2-113">Name</span></span>    | <span data-ttu-id="051d2-114">Değer</span><span class="sxs-lookup"><span data-stu-id="051d2-114">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="051d2-115">Kapsam</span><span class="sxs-lookup"><span data-stu-id="051d2-115">Scope</span></span>   | <span data-ttu-id="051d2-116">İkincil</span><span class="sxs-lookup"><span data-stu-id="051d2-116">Minor</span></span>       |
| <span data-ttu-id="051d2-117">Sürüm</span><span class="sxs-lookup"><span data-stu-id="051d2-117">Version</span></span> | <span data-ttu-id="051d2-118">4.7.2</span><span class="sxs-lookup"><span data-stu-id="051d2-118">4.7.2</span></span>       |
| <span data-ttu-id="051d2-119">Tür</span><span class="sxs-lookup"><span data-stu-id="051d2-119">Type</span></span>    | <span data-ttu-id="051d2-120">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="051d2-120">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="051d2-121">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="051d2-121">Affected APIs</span></span>

- <xref:System.Uri?displayProperty=nameWithType>
