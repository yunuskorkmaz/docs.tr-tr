---
ms.openlocfilehash: 6679e38aefa7d61ce430dc5375ff3b35c641ea27
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394186"
---
### <a name="identity-signinasync-throws-exception-for-unauthenticated-identity"></a><span data-ttu-id="f7fc4-101">Kimlik: Signınasync kimliği doğrulanmamış kimlik için özel durum oluşturur</span><span class="sxs-lookup"><span data-stu-id="f7fc4-101">Identity: SignInAsync throws exception for unauthenticated identity</span></span>

<span data-ttu-id="f7fc4-102">Varsayılan olarak, `IsAuthenticated`  `false` olduğu sorumlular/kimlikler için bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f7fc4-102">By default, `SignInAsync` throws an exception for principals / identities in which `IsAuthenticated` is `false`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f7fc4-103">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="f7fc4-103">Version introduced</span></span>

<span data-ttu-id="f7fc4-104">3.0</span><span class="sxs-lookup"><span data-stu-id="f7fc4-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="f7fc4-105">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="f7fc4-105">Old behavior</span></span>

<span data-ttu-id="f7fc4-106">`SignInAsync`, `IsAuthenticated` ' in `false` olduğu kimlikler de dahil olmak üzere herhangi bir sorumlusu/kimliği kabul eder.</span><span class="sxs-lookup"><span data-stu-id="f7fc4-106">`SignInAsync` accepts any principals / identities, including identities in which `IsAuthenticated` is `false`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="f7fc4-107">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="f7fc4-107">New behavior</span></span>

<span data-ttu-id="f7fc4-108">Varsayılan olarak, `IsAuthenticated`  `false` olduğu sorumlular/kimlikler için bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f7fc4-108">By default, `SignInAsync` throws an exception for principals / identities in which `IsAuthenticated` is `false`.</span></span> <span data-ttu-id="f7fc4-109">Bu davranışı bastırmak için yeni bir bayrak bulunur, ancak varsayılan davranış değişmiştir.</span><span class="sxs-lookup"><span data-stu-id="f7fc4-109">There's a new flag to suppress this behavior, but the default behavior has changed.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="f7fc4-110">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="f7fc4-110">Reason for change</span></span>

<span data-ttu-id="f7fc4-111">Varsayılan olarak, bu sorumlular `[Authorize]` @ no__t-1 @ no__t-2 tarafından reddedildiği için eski davranış soruna neden oldu.</span><span class="sxs-lookup"><span data-stu-id="f7fc4-111">The old behavior was problematic because, by default, these principals were rejected by `[Authorize]` / `RequireAuthenticatedUser()`.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f7fc4-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="f7fc4-112">Recommended action</span></span>

<span data-ttu-id="f7fc4-113">ASP.NET Core 3,0 Preview 6 ' da, varsayılan olarak `true` olan `AuthenticationOptions` `RequireAuthenticatedSignIn` bayrağı vardır.</span><span class="sxs-lookup"><span data-stu-id="f7fc4-113">In ASP.NET Core 3.0 Preview 6, there's a `RequireAuthenticatedSignIn` flag on `AuthenticationOptions` that is `true` by default.</span></span> <span data-ttu-id="f7fc4-114">Eski davranışı geri yüklemek için bu bayrağı `false` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f7fc4-114">Set this flag to `false` to restore the old behavior.</span></span>

#### <a name="category"></a><span data-ttu-id="f7fc4-115">Kategori</span><span class="sxs-lookup"><span data-stu-id="f7fc4-115">Category</span></span>

<span data-ttu-id="f7fc4-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f7fc4-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f7fc4-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="f7fc4-117">Affected APIs</span></span>

<span data-ttu-id="f7fc4-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="f7fc4-118">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
