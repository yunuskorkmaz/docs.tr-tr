---
ms.openlocfilehash: 2819fb3857fa6d40a2b2e42eeaec2d9c6e50eef0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96299359"
---
### <a name="authorization-addauthorization-overload-moved-to-different-assembly"></a><span data-ttu-id="474d6-101">Yetkilendirme: Addaduthorleştirme aşırı yüklemesi farklı bir derlemeye taşındı</span><span class="sxs-lookup"><span data-stu-id="474d6-101">Authorization: AddAuthorization overload moved to different assembly</span></span>

<span data-ttu-id="474d6-102">`AddAuthorization`İçinde yer almak için kullanılan temel yöntemler `Microsoft.AspNetCore.Authorization` olarak yeniden adlandırıldı `AddAuthorizationCore` .</span><span class="sxs-lookup"><span data-stu-id="474d6-102">The core `AddAuthorization` methods that used to reside in `Microsoft.AspNetCore.Authorization` were renamed to `AddAuthorizationCore`.</span></span> <span data-ttu-id="474d6-103">Eski `AddAuthorization` Yöntemler hala mevcuttur, ancak `Microsoft.AspNetCore.Authorization.Policy` bunun yerine derlemede bulunur.</span><span class="sxs-lookup"><span data-stu-id="474d6-103">The old `AddAuthorization` methods still exist, but are in the `Microsoft.AspNetCore.Authorization.Policy` assembly instead.</span></span> <span data-ttu-id="474d6-104">Her iki yöntemi kullanan uygulamalar hiçbir etki görmemelidir.</span><span class="sxs-lookup"><span data-stu-id="474d6-104">Apps using both methods should see no impact.</span></span> <span data-ttu-id="474d6-105">Artık paylaşılan çerçevede `Microsoft.AspNetCore.Authorization.Policy` açıklandığı gibi, paylaşılan çerçevede kullanıma sunulan bir bağımsız paket yerine, [Microsoft. Aspnetcore. app öğesinden kaldırılan derlemeler](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp).</span><span class="sxs-lookup"><span data-stu-id="474d6-105">Note that `Microsoft.AspNetCore.Authorization.Policy` now ships in the shared framework rather than a standalone package as discussed in [Shared framework: Assemblies removed from Microsoft.AspNetCore.App](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="474d6-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="474d6-106">Version introduced</span></span>

<span data-ttu-id="474d6-107">3,0</span><span class="sxs-lookup"><span data-stu-id="474d6-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="474d6-108">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="474d6-108">Old behavior</span></span>

<span data-ttu-id="474d6-109">`AddAuthorization` Yöntemler içinde vardı `Microsoft.AspNetCore.Authorization` .</span><span class="sxs-lookup"><span data-stu-id="474d6-109">`AddAuthorization` methods existed in `Microsoft.AspNetCore.Authorization`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="474d6-110">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="474d6-110">New behavior</span></span>

<span data-ttu-id="474d6-111">`AddAuthorization` yöntemleri içinde bulunur `Microsoft.AspNetCore.Authorization.Policy` .</span><span class="sxs-lookup"><span data-stu-id="474d6-111">`AddAuthorization` methods exist in `Microsoft.AspNetCore.Authorization.Policy`.</span></span> <span data-ttu-id="474d6-112">`AddAuthorizationCore` , eski yöntemlerin yeni adıdır.</span><span class="sxs-lookup"><span data-stu-id="474d6-112">`AddAuthorizationCore` is the new name for the old methods.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="474d6-113">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="474d6-113">Reason for change</span></span>

<span data-ttu-id="474d6-114">`AddAuthorization` , yetkilendirme için gereken tüm ortak hizmetleri eklemek için daha iyi bir yöntem adıdır.</span><span class="sxs-lookup"><span data-stu-id="474d6-114">`AddAuthorization` is a better method name for adding all common services needed for authorization.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="474d6-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="474d6-115">Recommended action</span></span>

<span data-ttu-id="474d6-116">Bunun yerine bir başvuru ekleyin `Microsoft.AspNetCore.Authorization.Policy` ya da kullanın `AddAuthorizationCore` .</span><span class="sxs-lookup"><span data-stu-id="474d6-116">Either add a reference to `Microsoft.AspNetCore.Authorization.Policy` or use `AddAuthorizationCore` instead.</span></span>

#### <a name="category"></a><span data-ttu-id="474d6-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="474d6-117">Category</span></span>

<span data-ttu-id="474d6-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="474d6-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="474d6-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="474d6-119">Affected APIs</span></span>

<xref:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})`

-->
