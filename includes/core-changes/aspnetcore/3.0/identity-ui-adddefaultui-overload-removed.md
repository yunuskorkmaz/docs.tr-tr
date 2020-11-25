---
ms.openlocfilehash: e77312605ee367c159171e305d8f69429f9ac58b
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032787"
---
### <a name="identity-adddefaultui-method-overload-removed"></a><span data-ttu-id="b9723-101">Kimlik: Adddefaultuı yöntemi aşırı yüklemesi kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="b9723-101">Identity: AddDefaultUI method overload removed</span></span>

<span data-ttu-id="b9723-102">ASP.NET Core 3,0 ' den başlayarak [ıdentitybuilderuıextensions. Adddefaultuı (ıdentitybuilder, Uıiframework)](/dotnet/api/microsoft.aspnetcore.identity.identitybuilderuiextensions.adddefaultui?view=aspnetcore-2.2#Microsoft_AspNetCore_Identity_IdentityBuilderUIExtensions_AddDefaultUI_Microsoft_AspNetCore_Identity_IdentityBuilder_Microsoft_AspNetCore_Identity_UI_UIFramework_) yöntem aşırı yüklemesi artık yok.</span><span class="sxs-lookup"><span data-stu-id="b9723-102">Starting with ASP.NET Core 3.0, the [IdentityBuilderUIExtensions.AddDefaultUI(IdentityBuilder,UIFramework)](/dotnet/api/microsoft.aspnetcore.identity.identitybuilderuiextensions.adddefaultui?view=aspnetcore-2.2#Microsoft_AspNetCore_Identity_IdentityBuilderUIExtensions_AddDefaultUI_Microsoft_AspNetCore_Identity_IdentityBuilder_Microsoft_AspNetCore_Identity_UI_UIFramework_) method overload no longer exists.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b9723-103">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="b9723-103">Version introduced</span></span>

<span data-ttu-id="b9723-104">3,0</span><span class="sxs-lookup"><span data-stu-id="b9723-104">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b9723-105">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="b9723-105">Reason for change</span></span>

<span data-ttu-id="b9723-106">Bu değişiklik, statik Web varlıkları özelliğini benimsemenin bir sonucudur.</span><span class="sxs-lookup"><span data-stu-id="b9723-106">This change was a result of adoption of the static web assets feature.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b9723-107">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="b9723-107">Recommended action</span></span>

<span data-ttu-id="b9723-108"><xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType>İki bağımsız değişken alan aşırı yükleme yerine çağırın.</span><span class="sxs-lookup"><span data-stu-id="b9723-108">Call <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType> instead of the overload that takes two arguments.</span></span> <span data-ttu-id="b9723-109">Bootstrap 3 kullanıyorsanız, aşağıdaki satırı `<PropertyGroup>` proje dosyanızdaki bir öğeye de ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b9723-109">If you're using Bootstrap 3, also add the following line to a `<PropertyGroup>` element in your project file:</span></span>

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a><span data-ttu-id="b9723-110">Kategori</span><span class="sxs-lookup"><span data-stu-id="b9723-110">Category</span></span>

<span data-ttu-id="b9723-111">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b9723-111">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b9723-112">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="b9723-112">Affected APIs</span></span>

[<span data-ttu-id="b9723-113">Identitybuilderuıextensions. Adddefaultuı (ıdentitybuilder, Uıiframework)</span><span class="sxs-lookup"><span data-stu-id="b9723-113">IdentityBuilderUIExtensions.AddDefaultUI(IdentityBuilder,UIFramework)</span></span>](/dotnet/api/microsoft.aspnetcore.identity.identitybuilderuiextensions.adddefaultui?view=aspnetcore-2.2#Microsoft_AspNetCore_Identity_IdentityBuilderUIExtensions_AddDefaultUI_Microsoft_AspNetCore_Identity_IdentityBuilder_Microsoft_AspNetCore_Identity_UI_UIFramework_)

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->
