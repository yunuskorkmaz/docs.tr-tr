---
ms.openlocfilehash: 6679e38aefa7d61ce430dc5375ff3b35c641ea27
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394186"
---
### <a name="identity-signinasync-throws-exception-for-unauthenticated-identity"></a><span data-ttu-id="ee196-101">Kimlik: SignInAsync kimliği doğrulanmamış kimlik için özel durum atar</span><span class="sxs-lookup"><span data-stu-id="ee196-101">Identity: SignInAsync throws exception for unauthenticated identity</span></span>

<span data-ttu-id="ee196-102">Varsayılan olarak, `SignInAsync` ilkeler / kimlikler `IsAuthenticated` için `false`bir özel durum atar.</span><span class="sxs-lookup"><span data-stu-id="ee196-102">By default, `SignInAsync` throws an exception for principals / identities in which `IsAuthenticated` is `false`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ee196-103">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="ee196-103">Version introduced</span></span>

<span data-ttu-id="ee196-104">3,0</span><span class="sxs-lookup"><span data-stu-id="ee196-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="ee196-105">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="ee196-105">Old behavior</span></span>

<span data-ttu-id="ee196-106">`SignInAsync`olduğu kimlikler `IsAuthenticated` de dahil olmak üzere herhangi bir `false`ilke / kimlik kabul eder.</span><span class="sxs-lookup"><span data-stu-id="ee196-106">`SignInAsync` accepts any principals / identities, including identities in which `IsAuthenticated` is `false`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="ee196-107">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="ee196-107">New behavior</span></span>

<span data-ttu-id="ee196-108">Varsayılan olarak, `SignInAsync` ilkeler / kimlikler `IsAuthenticated` için `false`bir özel durum atar.</span><span class="sxs-lookup"><span data-stu-id="ee196-108">By default, `SignInAsync` throws an exception for principals / identities in which `IsAuthenticated` is `false`.</span></span> <span data-ttu-id="ee196-109">Bu davranışı bastırmak için yeni bir bayrak var, ancak varsayılan davranış değişti.</span><span class="sxs-lookup"><span data-stu-id="ee196-109">There's a new flag to suppress this behavior, but the default behavior has changed.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="ee196-110">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="ee196-110">Reason for change</span></span>

<span data-ttu-id="ee196-111">Eski davranış sorunluydu, çünkü varsayılan olarak bu `[Authorize]`  /  `RequireAuthenticatedUser()`ilkeler .</span><span class="sxs-lookup"><span data-stu-id="ee196-111">The old behavior was problematic because, by default, these principals were rejected by `[Authorize]` / `RequireAuthenticatedUser()`.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ee196-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="ee196-112">Recommended action</span></span>

<span data-ttu-id="ee196-113">Core 3.0 Preview 6ASP.NET varsayılan `RequireAuthenticatedSignIn` olarak `AuthenticationOptions` üzerinde `true` bir bayrak vardır.</span><span class="sxs-lookup"><span data-stu-id="ee196-113">In ASP.NET Core 3.0 Preview 6, there's a `RequireAuthenticatedSignIn` flag on `AuthenticationOptions` that is `true` by default.</span></span> <span data-ttu-id="ee196-114">Eski davranışı `false` geri yüklemek için bu bayrağı ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ee196-114">Set this flag to `false` to restore the old behavior.</span></span>

#### <a name="category"></a><span data-ttu-id="ee196-115">Kategori</span><span class="sxs-lookup"><span data-stu-id="ee196-115">Category</span></span>

<span data-ttu-id="ee196-116">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="ee196-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ee196-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="ee196-117">Affected APIs</span></span>

<span data-ttu-id="ee196-118">None</span><span class="sxs-lookup"><span data-stu-id="ee196-118">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
