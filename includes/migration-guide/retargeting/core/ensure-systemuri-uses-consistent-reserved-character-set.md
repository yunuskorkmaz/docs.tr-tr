---
ms.openlocfilehash: 21921156295d89aad04f3197fef9fa322f3c8c87
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614666"
---
### <a name="ensure-systemuri-uses-a-consistent-reserved-character-set"></a><span data-ttu-id="69e93-101">System. Uri ' nin tutarlı bir ayrılmış karakter kümesi kullandığından emin olun</span><span class="sxs-lookup"><span data-stu-id="69e93-101">Ensure System.Uri uses a consistent reserved character set</span></span>

#### <a name="details"></a><span data-ttu-id="69e93-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="69e93-102">Details</span></span>

<span data-ttu-id="69e93-103"><xref:System.Uri?displayProperty=fullName>' De, bazen kodu çözülmüş bazı yüzde kodlamalı karakterler artık sürekli olarak ayrıldı.</span><span class="sxs-lookup"><span data-stu-id="69e93-103">In <xref:System.Uri?displayProperty=fullName>, certain percent-encoded characters that were sometimes decoded are now consistently left encoded.</span></span> <span data-ttu-id="69e93-104">Bu, URI 'nin yoluna, sorguya, parçaya veya UserInfo bileşenlerine erişen Özellikler ve Yöntemler genelinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="69e93-104">This occurs across the properties and methods that access the path, query, fragment, or userinfo components of the URI.</span></span> <span data-ttu-id="69e93-105">Davranış yalnızca aşağıdakilerin her ikisi de doğru olduğunda değişir:</span><span class="sxs-lookup"><span data-stu-id="69e93-105">The behavior will change only when both of the following are true:</span></span>

- <span data-ttu-id="69e93-106">URI, aşağıdaki ayrılmış karakterlerden herhangi birinin kodlanmış biçimini içerir: `:` , `'` ,, `(` `)` `!` veya `*` .</span><span class="sxs-lookup"><span data-stu-id="69e93-106">The URI contains the encoded form of any of the following reserved characters: `:`, `'`, `(`, `)`, `!` or `*`.</span></span>
- <span data-ttu-id="69e93-107">URI, Unicode veya kodlanmış ayrılmamış bir karakter içeriyor.</span><span class="sxs-lookup"><span data-stu-id="69e93-107">The URI contains a Unicode or encoded non-reserved character.</span></span> <span data-ttu-id="69e93-108">Yukarıdakilerin her ikisi de doğruysa, kodlanan ayrılmış karakterler bırakılır.</span><span class="sxs-lookup"><span data-stu-id="69e93-108">If both of the above are true, the encoded reserved characters are left encoded.</span></span> <span data-ttu-id="69e93-109">.NET Framework önceki sürümlerinde, bunların kodu çözülür.</span><span class="sxs-lookup"><span data-stu-id="69e93-109">In previous versions of the .NET Framework, they are decoded.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="69e93-110">Öneri</span><span class="sxs-lookup"><span data-stu-id="69e93-110">Suggestion</span></span>

<span data-ttu-id="69e93-111">4.7.2 ile başlayan .NET Framework sürümlerini hedefleyen uygulamalar için yeni kod çözme davranışı varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="69e93-111">For applications that target versions of .NET Framework starting with 4.7.2, the new decoding behavior is enabled by default.</span></span> <span data-ttu-id="69e93-112">Bu değişiklik istenmeyen ise, [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) `<runtime>` uygulama yapılandırma dosyasının bölümüne aşağıdaki AppContextSwitchOverrides anahtarını ekleyerek devre dışı bırakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="69e93-112">If this change is undesirable, you can disable it by adding the following [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switch to the `<runtime>` section of the application configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets=true" />
</runtime>
```

<span data-ttu-id="69e93-113">.NET Framework önceki sürümlerini hedefleyen ancak .NET Framework 4.7.2 ile başlayan sürümler altında çalışan uygulamalar için yeni kod çözme davranışı varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="69e93-113">For applications that target earlier versions of the .NET Framework but are running under versions starting with .NET Framework 4.7.2, the new decoding behavior is disabled by default.</span></span> <span data-ttu-id="69e93-114">Aşağıdaki [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) anahtarını `<runtime>` uygulama yapılandırma dosyasının bölümüne ekleyerek etkinleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="69e93-114">You can enable it by adding the following [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switch to the `<runtime>` section of the application configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets=false" />
</runtime>
```

| <span data-ttu-id="69e93-115">Name</span><span class="sxs-lookup"><span data-stu-id="69e93-115">Name</span></span>    | <span data-ttu-id="69e93-116">Değer</span><span class="sxs-lookup"><span data-stu-id="69e93-116">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="69e93-117">Kapsam</span><span class="sxs-lookup"><span data-stu-id="69e93-117">Scope</span></span>   | <span data-ttu-id="69e93-118">İkincil</span><span class="sxs-lookup"><span data-stu-id="69e93-118">Minor</span></span>       |
| <span data-ttu-id="69e93-119">Sürüm</span><span class="sxs-lookup"><span data-stu-id="69e93-119">Version</span></span> | <span data-ttu-id="69e93-120">4.7.2</span><span class="sxs-lookup"><span data-stu-id="69e93-120">4.7.2</span></span>       |
| <span data-ttu-id="69e93-121">Tür</span><span class="sxs-lookup"><span data-stu-id="69e93-121">Type</span></span>    | <span data-ttu-id="69e93-122">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="69e93-122">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="69e93-123">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="69e93-123">Affected APIs</span></span>

- <xref:System.Uri?displayProperty=nameWithType>
