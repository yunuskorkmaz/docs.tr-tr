---
ms.openlocfilehash: b88f7d4a17f885b687d99ab9410a56039e176080
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614642"
---
### <a name="calls-to-claimsidentity-constructors"></a><span data-ttu-id="a999c-101">ClaimsIdentity oluşturucuları çağrıları</span><span class="sxs-lookup"><span data-stu-id="a999c-101">Calls to ClaimsIdentity constructors</span></span>

#### <a name="details"></a><span data-ttu-id="a999c-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="a999c-102">Details</span></span>

<span data-ttu-id="a999c-103">.NET Framework 4.6.2 ' den başlayarak, <xref:System.Security.Claims.ClaimsIdentity> bir parametreye sahip oluşturucuların özelliği ayarlama biçiminde bir değişiklik vardır <xref:System.Security.Principal.IIdentity?displayProperty=fullName> <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="a999c-103">Starting with the .NET Framework 4.6.2, there is a change in how <xref:System.Security.Claims.ClaimsIdentity> constructors with an <xref:System.Security.Principal.IIdentity?displayProperty=fullName> parameter set the <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> property.</span></span> <span data-ttu-id="a999c-104"><xref:System.Security.Principal.IIdentity?displayProperty=fullName>Bağımsız değişken bir nesne ise <xref:System.Security.Claims.ClaimsIdentity> ve <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> Bu <xref:System.Security.Claims.ClaimsIdentity> nesnenin özelliği değilse `null` , <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> özelliği yöntemi kullanılarak iliştirilir <xref:System.Security.Claims.ClaimsIdentity.Clone> .</span><span class="sxs-lookup"><span data-stu-id="a999c-104">If the <xref:System.Security.Principal.IIdentity?displayProperty=fullName> argument is a <xref:System.Security.Claims.ClaimsIdentity> object, and the <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> property of that <xref:System.Security.Claims.ClaimsIdentity> object is not `null`, the <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> property is attached by using the <xref:System.Security.Claims.ClaimsIdentity.Clone> method.</span></span> <span data-ttu-id="a999c-105">Framework 4.6.1 ve önceki sürümlerde, <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> özelliği var olan bir başvuru olarak eklenir. Bu değişiklik nedeniyle .NET Framework 4.6.2 ile başlayarak, <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> Yeni <xref:System.Security.Claims.ClaimsIdentity> nesnenin özelliği <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> oluşturucunun bağımsız değişkeninin özelliğine eşit değildir <xref:System.Security.Principal.IIdentity?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="a999c-105">In the Framework 4.6.1 and earlier versions, the <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> property is attached as an existing reference.Because of this change, starting with the .NET Framework 4.6.2, the <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> property of the new <xref:System.Security.Claims.ClaimsIdentity> object is not equal to the <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> property of the constructor's <xref:System.Security.Principal.IIdentity?displayProperty=fullName> argument.</span></span> <span data-ttu-id="a999c-106">.NET Framework 4.6.1 ve önceki sürümlerde, eşittir.</span><span class="sxs-lookup"><span data-stu-id="a999c-106">In the .NET Framework 4.6.1 and earlier versions, it is equal.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a999c-107">Öneri</span><span class="sxs-lookup"><span data-stu-id="a999c-107">Suggestion</span></span>

<span data-ttu-id="a999c-108">Bu davranış istenerek, `Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity` uygulama yapılandırma dosyanızdaki anahtarı olarak ayarlayarak önceki davranışı geri yükleyebilirsiniz `true` .</span><span class="sxs-lookup"><span data-stu-id="a999c-108">If this behavior is undesirable, you can restore the previous behavior by setting the `Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity` switch in your application configuration file to `true`.</span></span> <span data-ttu-id="a999c-109">Bunun için aşağıdakileri `<runtime>` web.config dosyanızın bölümüne eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="a999c-109">This requires that you add the following to the `<runtime>` section of your web.config file:</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity=true" />
  </runtime>
</configuration>
```

| <span data-ttu-id="a999c-110">Name</span><span class="sxs-lookup"><span data-stu-id="a999c-110">Name</span></span>    | <span data-ttu-id="a999c-111">Değer</span><span class="sxs-lookup"><span data-stu-id="a999c-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a999c-112">Kapsam</span><span class="sxs-lookup"><span data-stu-id="a999c-112">Scope</span></span>   | <span data-ttu-id="a999c-113">Edge</span><span class="sxs-lookup"><span data-stu-id="a999c-113">Edge</span></span>        |
| <span data-ttu-id="a999c-114">Sürüm</span><span class="sxs-lookup"><span data-stu-id="a999c-114">Version</span></span> | <span data-ttu-id="a999c-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="a999c-115">4.6.2</span></span>       |
| <span data-ttu-id="a999c-116">Tür</span><span class="sxs-lookup"><span data-stu-id="a999c-116">Type</span></span>    | <span data-ttu-id="a999c-117">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="a999c-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="a999c-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="a999c-118">Affected APIs</span></span>

- <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity)>
- <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity,System.Collections.Generic.IEnumerable{System.Security.Claims.Claim})>
- <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity,System.Collections.Generic.IEnumerable{System.Security.Claims.Claim},System.String,System.String,System.String)>
