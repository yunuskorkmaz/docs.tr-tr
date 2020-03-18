---
ms.openlocfilehash: b91cdc7a0d2e4258662155a840500ce21ab35760
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74101589"
---
### <a name="authorization-addauthorization-overload-moved-to-different-assembly"></a><span data-ttu-id="d54b7-101">Yetkilendirme: AddAuthorization aşırı yükü farklı derlemeye taşındı</span><span class="sxs-lookup"><span data-stu-id="d54b7-101">Authorization: AddAuthorization overload moved to different assembly</span></span>

<span data-ttu-id="d54b7-102">Eskiden `AddAuthorization` içinde bulunan `Microsoft.AspNetCore.Authorization` temel yöntemlerin adı `AddAuthorizationCore`".</span><span class="sxs-lookup"><span data-stu-id="d54b7-102">The core `AddAuthorization` methods that used to reside in `Microsoft.AspNetCore.Authorization` were renamed to `AddAuthorizationCore`.</span></span> <span data-ttu-id="d54b7-103">Eski `AddAuthorization` yöntemler hala var, ancak `Microsoft.AspNetCore.Authorization.Policy` bunun yerine derleme bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d54b7-103">The old `AddAuthorization` methods still exist, but are in the `Microsoft.AspNetCore.Authorization.Policy` assembly instead.</span></span> <span data-ttu-id="d54b7-104">Her iki yöntemi kullanan uygulamalar hiçbir etki görmemelidir.</span><span class="sxs-lookup"><span data-stu-id="d54b7-104">Apps using both methods should see no impact.</span></span> <span data-ttu-id="d54b7-105">`Microsoft.AspNetCore.Authorization.Policy` Artık paylaşılan çerçevede tartışılan bağımsız bir paket yerine paylaşılan çerçevede gemilerin olduğunu [unutmayın: Derlemeler Microsoft.AspNetCore.App kaldırıldı.](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp)</span><span class="sxs-lookup"><span data-stu-id="d54b7-105">Note that `Microsoft.AspNetCore.Authorization.Policy` now ships in the shared framework rather than a standalone package as discussed in [Shared framework: Assemblies removed from Microsoft.AspNetCore.App](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d54b7-106">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="d54b7-106">Version introduced</span></span>

<span data-ttu-id="d54b7-107">3,0</span><span class="sxs-lookup"><span data-stu-id="d54b7-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="d54b7-108">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="d54b7-108">Old behavior</span></span>
<span data-ttu-id="d54b7-109">`AddAuthorization`metodları `Microsoft.AspNetCore.Authorization`var.</span><span class="sxs-lookup"><span data-stu-id="d54b7-109">`AddAuthorization` methods existed in `Microsoft.AspNetCore.Authorization`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="d54b7-110">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="d54b7-110">New behavior</span></span>

<span data-ttu-id="d54b7-111">`AddAuthorization`metodları `Microsoft.AspNetCore.Authorization.Policy`.</span><span class="sxs-lookup"><span data-stu-id="d54b7-111">`AddAuthorization` methods exist in `Microsoft.AspNetCore.Authorization.Policy`.</span></span> <span data-ttu-id="d54b7-112">`AddAuthorizationCore`eski yöntemleriçin yeni bir addır.</span><span class="sxs-lookup"><span data-stu-id="d54b7-112">`AddAuthorizationCore` is the new name for the old methods.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d54b7-113">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="d54b7-113">Reason for change</span></span>

<span data-ttu-id="d54b7-114">`AddAuthorization`yetkilendirme için gereken tüm ortak hizmetleri eklemek için daha iyi bir yöntem adıdır.</span><span class="sxs-lookup"><span data-stu-id="d54b7-114">`AddAuthorization` is a better method name for adding all common services needed for authorization.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d54b7-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="d54b7-115">Recommended action</span></span>

<span data-ttu-id="d54b7-116">Bir başvuru ekleyin `Microsoft.AspNetCore.Authorization.Policy` veya `AddAuthorizationCore` bunun yerine kullanın.</span><span class="sxs-lookup"><span data-stu-id="d54b7-116">Either add a reference to `Microsoft.AspNetCore.Authorization.Policy` or use `AddAuthorizationCore` instead.</span></span>

#### <a name="category"></a><span data-ttu-id="d54b7-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="d54b7-117">Category</span></span>

<span data-ttu-id="d54b7-118">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="d54b7-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d54b7-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="d54b7-119">Affected APIs</span></span>

<xref:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})`

-->
