---
ms.openlocfilehash: b91cdc7a0d2e4258662155a840500ce21ab35760
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74101589"
---
### <a name="authorization-addauthorization-overload-moved-to-different-assembly"></a><span data-ttu-id="70c53-101">Yetkilendirme: Addaduthorleştirme aşırı yüklemesi farklı bir derlemeye taşındı</span><span class="sxs-lookup"><span data-stu-id="70c53-101">Authorization: AddAuthorization overload moved to different assembly</span></span>

<span data-ttu-id="70c53-102">`Microsoft.AspNetCore.Authorization` içinde yer almak için kullanılan temel `AddAuthorization` yöntemleri `AddAuthorizationCore`olarak yeniden adlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="70c53-102">The core `AddAuthorization` methods that used to reside in `Microsoft.AspNetCore.Authorization` were renamed to `AddAuthorizationCore`.</span></span> <span data-ttu-id="70c53-103">Eski `AddAuthorization` yöntemleri hala mevcuttur, ancak bunun yerine `Microsoft.AspNetCore.Authorization.Policy` bütünleştirilmiş kodunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="70c53-103">The old `AddAuthorization` methods still exist, but are in the `Microsoft.AspNetCore.Authorization.Policy` assembly instead.</span></span> <span data-ttu-id="70c53-104">Her iki yöntemi kullanan uygulamalar hiçbir etki görmemelidir.</span><span class="sxs-lookup"><span data-stu-id="70c53-104">Apps using both methods should see no impact.</span></span> <span data-ttu-id="70c53-105">`Microsoft.AspNetCore.Authorization.Policy` artık paylaşılan çerçevede açıklandığı gibi, paylaşılan çerçevede ( [Microsoft. AspNetCore. app 'ten kaldırılan derlemeler](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp)) kullanıma sunulmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="70c53-105">Note that `Microsoft.AspNetCore.Authorization.Policy` now ships in the shared framework rather than a standalone package as discussed in [Shared framework: Assemblies removed from Microsoft.AspNetCore.App](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="70c53-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="70c53-106">Version introduced</span></span>

<span data-ttu-id="70c53-107">3.0</span><span class="sxs-lookup"><span data-stu-id="70c53-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="70c53-108">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="70c53-108">Old behavior</span></span>
<span data-ttu-id="70c53-109">`AddAuthorization` yöntemleri `Microsoft.AspNetCore.Authorization` ' de vardı.</span><span class="sxs-lookup"><span data-stu-id="70c53-109">`AddAuthorization` methods existed in `Microsoft.AspNetCore.Authorization`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="70c53-110">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="70c53-110">New behavior</span></span>

<span data-ttu-id="70c53-111">`AddAuthorization` yöntemleri `Microsoft.AspNetCore.Authorization.Policy` ' de bulunur.</span><span class="sxs-lookup"><span data-stu-id="70c53-111">`AddAuthorization` methods exist in `Microsoft.AspNetCore.Authorization.Policy`.</span></span> <span data-ttu-id="70c53-112">`AddAuthorizationCore`, eski yöntemlerin yeni adıdır.</span><span class="sxs-lookup"><span data-stu-id="70c53-112">`AddAuthorizationCore` is the new name for the old methods.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="70c53-113">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="70c53-113">Reason for change</span></span>

<span data-ttu-id="70c53-114">`AddAuthorization`, yetkilendirme için gereken tüm ortak hizmetleri eklemek için daha iyi bir yöntem adıdır.</span><span class="sxs-lookup"><span data-stu-id="70c53-114">`AddAuthorization` is a better method name for adding all common services needed for authorization.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="70c53-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="70c53-115">Recommended action</span></span>

<span data-ttu-id="70c53-116">`Microsoft.AspNetCore.Authorization.Policy` bir başvuru ekleyin ya da bunun yerine `AddAuthorizationCore` kullanın.</span><span class="sxs-lookup"><span data-stu-id="70c53-116">Either add a reference to `Microsoft.AspNetCore.Authorization.Policy` or use `AddAuthorizationCore` instead.</span></span>

#### <a name="category"></a><span data-ttu-id="70c53-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="70c53-117">Category</span></span>

<span data-ttu-id="70c53-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="70c53-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="70c53-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="70c53-119">Affected APIs</span></span>

<xref:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})`

-->
