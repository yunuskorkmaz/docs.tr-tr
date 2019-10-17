---
ms.openlocfilehash: 65bac44c84589fb55d2b04c39088c2825c451a6b
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394266"
---
### <a name="authorization-addauthorization-overload-moved-to-different-assembly"></a><span data-ttu-id="e9c27-101">Yetkilendirme: Addaduthorleştirme aşırı yüklemesi farklı bir derlemeye taşındı</span><span class="sxs-lookup"><span data-stu-id="e9c27-101">Authorization: AddAuthorization overload moved to different assembly</span></span>

<span data-ttu-id="e9c27-102">@No__t-1 ' de yer almak için kullanılan çekirdek `AddAuthorization` yöntemleri `AddAuthorizationCore` olarak yeniden adlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="e9c27-102">The core `AddAuthorization` methods that used to reside in `Microsoft.AspNetCore.Authorization` were renamed to `AddAuthorizationCore`.</span></span> <span data-ttu-id="e9c27-103">Eski `AddAuthorization` yöntemleri hala mevcuttur, ancak bunun yerine `Microsoft.AspNetCore.Authorization.Policy` paketidir.</span><span class="sxs-lookup"><span data-stu-id="e9c27-103">The old `AddAuthorization` methods still exist, but are in the `Microsoft.AspNetCore.Authorization.Policy` package instead.</span></span> <span data-ttu-id="e9c27-104">Her iki yöntemi kullanan uygulamalar hiçbir etki görmemelidir.</span><span class="sxs-lookup"><span data-stu-id="e9c27-104">Apps using both methods should see no impact.</span></span> <span data-ttu-id="e9c27-105">İlke paketini kullanmayan uygulamalar `AddAuthorizationCore` ' a geçiş yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e9c27-105">Apps that weren't using the policy package must switch to using `AddAuthorizationCore`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e9c27-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="e9c27-106">Version introduced</span></span>

<span data-ttu-id="e9c27-107">3.0</span><span class="sxs-lookup"><span data-stu-id="e9c27-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="e9c27-108">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="e9c27-108">Old behavior</span></span>

<span data-ttu-id="e9c27-109">`AddAuthorization` yöntemleri `Microsoft.AspNetCore.Authorization` ' de vardı.</span><span class="sxs-lookup"><span data-stu-id="e9c27-109">`AddAuthorization` methods existed in `Microsoft.AspNetCore.Authorization`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="e9c27-110">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="e9c27-110">New behavior</span></span>

<span data-ttu-id="e9c27-111">`AddAuthorization` yöntemleri `Microsoft.AspNetCore.Authorization.Policy` ' de bulunur.</span><span class="sxs-lookup"><span data-stu-id="e9c27-111">`AddAuthorization` methods exist in `Microsoft.AspNetCore.Authorization.Policy`.</span></span> <span data-ttu-id="e9c27-112">`AddAuthorizationCore`, eski yöntemlerin yeni adıdır.</span><span class="sxs-lookup"><span data-stu-id="e9c27-112">`AddAuthorizationCore` is the new name for the old methods.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="e9c27-113">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="e9c27-113">Reason for change</span></span>

<span data-ttu-id="e9c27-114">`AddAuthorization`, yetkilendirme için gereken tüm ortak hizmetleri eklemek için daha iyi bir yöntem adıdır.</span><span class="sxs-lookup"><span data-stu-id="e9c27-114">`AddAuthorization` is a better method name for adding all common services needed for authorization.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e9c27-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="e9c27-115">Recommended action</span></span>

<span data-ttu-id="e9c27-116">@No__t-0 ' a bir başvuru ekleyin ya da bunun yerine `AddAuthorizationCore` kullanın.</span><span class="sxs-lookup"><span data-stu-id="e9c27-116">Either add a reference to `Microsoft.AspNetCore.Authorization.Policy` or use `AddAuthorizationCore` instead.</span></span>

#### <a name="category"></a><span data-ttu-id="e9c27-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="e9c27-117">Category</span></span>

<span data-ttu-id="e9c27-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e9c27-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e9c27-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="e9c27-119">Affected APIs</span></span>

<xref:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})`

-->
