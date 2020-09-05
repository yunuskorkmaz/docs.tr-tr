---
ms.openlocfilehash: 4e685722271a8079e727ea9c2e0e501f68b30fc9
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497889"
---
### <a name="targetframeworkname-for-default-app-domain-no-longer-defaults-to-null-if-not-set"></a><span data-ttu-id="15deb-101">Varsayılan uygulama etki alanı için TargetFrameworkName, ayarlanmamışsa artık varsayılan olarak null değerini alır</span><span class="sxs-lookup"><span data-stu-id="15deb-101">TargetFrameworkName for default app domain no longer defaults to null if not set</span></span>

#### <a name="details"></a><span data-ttu-id="15deb-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="15deb-102">Details</span></span>

<span data-ttu-id="15deb-103"><xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName>Açık olarak ayarlanmadığı takdirde, varsayılan uygulama etki alanında daha önce null idi.</span><span class="sxs-lookup"><span data-stu-id="15deb-103">The <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> was previously null in the default app domain, unless it was explicitly set.</span></span> <span data-ttu-id="15deb-104">4,6 ' den başlayarak, <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> Varsayılan uygulama etki alanı için özelliği TargetFrameworkAttribute öğesinden türetilen varsayılan değere sahip olacaktır (varsa).</span><span class="sxs-lookup"><span data-stu-id="15deb-104">Beginning in 4.6, the <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> property for the default app domain will have a default value derived from the TargetFrameworkAttribute (if one is present).</span></span> <span data-ttu-id="15deb-105">Varsayılan olmayan uygulama etki alanları, <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> açıkça geçersiz kılınmadıkça varsayılan uygulama etki alanından (varsayılan olarak 4,6 ' de null değeri yoktur) devralma yapmaya devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="15deb-105">Non-default app domains will continue to inherit their <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> from the default app domain (which will not default to null in 4.6) unless it is explicitly overridden.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="15deb-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="15deb-106">Suggestion</span></span>

<span data-ttu-id="15deb-107">Kodun, <xref:System.AppDomainSetup.TargetFrameworkName> varsayılan değer olarak null değerine bağlı olmaması için güncelleştirilmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="15deb-107">Code should be updated to not depend on <xref:System.AppDomainSetup.TargetFrameworkName> defaulting to null.</span></span> <span data-ttu-id="15deb-108">Bu özelliğin NULL olarak değerlendirilmeye devam etmesi gerekiyorsa, açıkça bu değere ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="15deb-108">If it is required that this property continue to evaluate to null, it can be explicitly set to that value.</span></span>

| <span data-ttu-id="15deb-109">Name</span><span class="sxs-lookup"><span data-stu-id="15deb-109">Name</span></span>    | <span data-ttu-id="15deb-110">Değer</span><span class="sxs-lookup"><span data-stu-id="15deb-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="15deb-111">Kapsam</span><span class="sxs-lookup"><span data-stu-id="15deb-111">Scope</span></span>   |<span data-ttu-id="15deb-112">Edge</span><span class="sxs-lookup"><span data-stu-id="15deb-112">Edge</span></span>|
|<span data-ttu-id="15deb-113">Sürüm</span><span class="sxs-lookup"><span data-stu-id="15deb-113">Version</span></span>|<span data-ttu-id="15deb-114">4.6</span><span class="sxs-lookup"><span data-stu-id="15deb-114">4.6</span></span>|
|<span data-ttu-id="15deb-115">Tür</span><span class="sxs-lookup"><span data-stu-id="15deb-115">Type</span></span>|<span data-ttu-id="15deb-116">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="15deb-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="15deb-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="15deb-117">Affected APIs</span></span>

- <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.AppDomainSetup.TargetFrameworkName`

-->
