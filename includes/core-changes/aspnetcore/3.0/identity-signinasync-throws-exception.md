---
ms.openlocfilehash: 6679e38aefa7d61ce430dc5375ff3b35c641ea27
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032780"
---
### <a name="identity-signinasync-throws-exception-for-unauthenticated-identity"></a><span data-ttu-id="9583e-101">Kimlik: Signınasync kimliği doğrulanmamış kimlik için özel durum oluşturur</span><span class="sxs-lookup"><span data-stu-id="9583e-101">Identity: SignInAsync throws exception for unauthenticated identity</span></span>

<span data-ttu-id="9583e-102">Varsayılan olarak, `SignInAsync` olan sorumlular/kimlikler için bir özel durum `IsAuthenticated` oluşturur `false` .</span><span class="sxs-lookup"><span data-stu-id="9583e-102">By default, `SignInAsync` throws an exception for principals / identities in which `IsAuthenticated` is `false`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9583e-103">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="9583e-103">Version introduced</span></span>

<span data-ttu-id="9583e-104">3,0</span><span class="sxs-lookup"><span data-stu-id="9583e-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="9583e-105">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="9583e-105">Old behavior</span></span>

<span data-ttu-id="9583e-106">`SignInAsync` içindeki kimlikler dahil tüm sorumluları/kimlikleri kabul eder `IsAuthenticated` `false` .</span><span class="sxs-lookup"><span data-stu-id="9583e-106">`SignInAsync` accepts any principals / identities, including identities in which `IsAuthenticated` is `false`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="9583e-107">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="9583e-107">New behavior</span></span>

<span data-ttu-id="9583e-108">Varsayılan olarak, `SignInAsync` olan sorumlular/kimlikler için bir özel durum `IsAuthenticated` oluşturur `false` .</span><span class="sxs-lookup"><span data-stu-id="9583e-108">By default, `SignInAsync` throws an exception for principals / identities in which `IsAuthenticated` is `false`.</span></span> <span data-ttu-id="9583e-109">Bu davranışı bastırmak için yeni bir bayrak bulunur, ancak varsayılan davranış değişmiştir.</span><span class="sxs-lookup"><span data-stu-id="9583e-109">There's a new flag to suppress this behavior, but the default behavior has changed.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="9583e-110">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="9583e-110">Reason for change</span></span>

<span data-ttu-id="9583e-111">Varsayılan olarak, bu sorumlular tarafından reddedildiği için eski davranış soruna neden oldu `[Authorize]`  /  `RequireAuthenticatedUser()` .</span><span class="sxs-lookup"><span data-stu-id="9583e-111">The old behavior was problematic because, by default, these principals were rejected by `[Authorize]` / `RequireAuthenticatedUser()`.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9583e-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="9583e-112">Recommended action</span></span>

<span data-ttu-id="9583e-113">ASP.NET Core 3,0 Preview 6 ' da, varsayılan olarak ' de bir `RequireAuthenticatedSignIn` bayrak vardır `AuthenticationOptions` `true` .</span><span class="sxs-lookup"><span data-stu-id="9583e-113">In ASP.NET Core 3.0 Preview 6, there's a `RequireAuthenticatedSignIn` flag on `AuthenticationOptions` that is `true` by default.</span></span> <span data-ttu-id="9583e-114">`false`Eski davranışı geri yüklemek için bu bayrağı ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9583e-114">Set this flag to `false` to restore the old behavior.</span></span>

#### <a name="category"></a><span data-ttu-id="9583e-115">Kategori</span><span class="sxs-lookup"><span data-stu-id="9583e-115">Category</span></span>

<span data-ttu-id="9583e-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9583e-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9583e-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="9583e-117">Affected APIs</span></span>

<span data-ttu-id="9583e-118">Yok</span><span class="sxs-lookup"><span data-stu-id="9583e-118">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
