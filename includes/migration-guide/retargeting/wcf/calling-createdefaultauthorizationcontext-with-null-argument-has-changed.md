---
ms.openlocfilehash: c5a061dffa1deb66e1769d6ec70dfa2155ac6a31
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615769"
---
### <a name="calling-createdefaultauthorizationcontext-with-a-null-argument-has-changed"></a><span data-ttu-id="36fa9-101">CreateDefaultAuthorizationContext 'in null bir bağımsız değişkenle çağrılması değiştirildi</span><span class="sxs-lookup"><span data-stu-id="36fa9-101">Calling CreateDefaultAuthorizationContext with a null argument has changed</span></span>

#### <a name="details"></a><span data-ttu-id="36fa9-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="36fa9-102">Details</span></span>

<span data-ttu-id="36fa9-103"><xref:System.IdentityModel.Policy.AuthorizationContext?displayProperty=fullName>Null authorizationPolicies bağımsız değişkeni ile öğesine yapılan bir çağrı tarafından döndürülen uygulanması, <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=fullName> .NET Framework 4,6 ' deki uygulamasını değiştirdi.</span><span class="sxs-lookup"><span data-stu-id="36fa9-103">The implementation of the <xref:System.IdentityModel.Policy.AuthorizationContext?displayProperty=fullName> returned by a call to the <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=fullName> with a null authorizationPolicies argument has changed its implementation in the .NET Framework 4.6.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="36fa9-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="36fa9-104">Suggestion</span></span>

<span data-ttu-id="36fa9-105">Nadir durumlarda, özel kimlik doğrulaması kullanan WCF uygulamaları davranış farklarını görebilirler.</span><span class="sxs-lookup"><span data-stu-id="36fa9-105">In rare cases, WCF apps that use custom authentication may see behavioral differences.</span></span> <span data-ttu-id="36fa9-106">Bu gibi durumlarda, önceki davranış iki şekilde geri yüklenebilir:</span><span class="sxs-lookup"><span data-stu-id="36fa9-106">In such cases, the previous behavior can be restored in either of two ways:</span></span>

- <span data-ttu-id="36fa9-107">Uygulamanızı 4,6 ' den daha önceki bir .NET Framework sürümünü hedeflemek için yeniden derleyin.</span><span class="sxs-lookup"><span data-stu-id="36fa9-107">Recompile your app to target an earlier version of the .NET Framework than 4.6.</span></span> <span data-ttu-id="36fa9-108">IIS tarafından barındırılan hizmetler için, `<httpRuntime targetFramework="x.x">` .NET Framework önceki bir sürümünü hedeflemek için öğesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="36fa9-108">For IIS-hosted services, use the `<httpRuntime targetFramework="x.x">` element to target an earlier version of the .NET Framework.</span></span>
- <span data-ttu-id="36fa9-109">app.config dosyanızın bölümüne aşağıdaki satırı ekleyin `<appSettings>` :</span><span class="sxs-lookup"><span data-stu-id="36fa9-109">Add the following line to the `<appSettings>` section of your app.config file:</span></span>

    ```xml
    <add key="appContext.SetSwitch:Switch.System.IdentityModel.EnableCachedEmptyDefaultAuthorizationContext" value="true" />
    ```

| <span data-ttu-id="36fa9-110">Name</span><span class="sxs-lookup"><span data-stu-id="36fa9-110">Name</span></span>    | <span data-ttu-id="36fa9-111">Değer</span><span class="sxs-lookup"><span data-stu-id="36fa9-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="36fa9-112">Kapsam</span><span class="sxs-lookup"><span data-stu-id="36fa9-112">Scope</span></span>   | <span data-ttu-id="36fa9-113">İkincil</span><span class="sxs-lookup"><span data-stu-id="36fa9-113">Minor</span></span>       |
| <span data-ttu-id="36fa9-114">Sürüm</span><span class="sxs-lookup"><span data-stu-id="36fa9-114">Version</span></span> | <span data-ttu-id="36fa9-115">4.6</span><span class="sxs-lookup"><span data-stu-id="36fa9-115">4.6</span></span>         |
| <span data-ttu-id="36fa9-116">Tür</span><span class="sxs-lookup"><span data-stu-id="36fa9-116">Type</span></span>    | <span data-ttu-id="36fa9-117">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="36fa9-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="36fa9-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="36fa9-118">Affected APIs</span></span>

- <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=nameWithType>
