---
ms.openlocfilehash: 474f039cf00cb48761bfe7b7c4a0a9c6300cd820
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81637203"
---
### <a name="identity-adddefaultui-method-overload-removed"></a><span data-ttu-id="36a13-101">Kimlik: AddDefaultUI yöntemi aşırı kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="36a13-101">Identity: AddDefaultUI method overload removed</span></span>

<span data-ttu-id="36a13-102">Core 3.0 ASP.NET ile başlayarak, [IdentityBuilderUIExtensions.AddDefaultUI (IdentityBuilder, UIFramework)](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.identity.identitybuilderuiextensions.adddefaultui?view=aspnetcore-2.2#Microsoft_AspNetCore_Identity_IdentityBuilderUIExtensions_AddDefaultUI_Microsoft_AspNetCore_Identity_IdentityBuilder_Microsoft_AspNetCore_Identity_UI_UIFramework_) yöntemi aşırı artık yok.</span><span class="sxs-lookup"><span data-stu-id="36a13-102">Starting with ASP.NET Core 3.0, the [IdentityBuilderUIExtensions.AddDefaultUI(IdentityBuilder,UIFramework)](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.identity.identitybuilderuiextensions.adddefaultui?view=aspnetcore-2.2#Microsoft_AspNetCore_Identity_IdentityBuilderUIExtensions_AddDefaultUI_Microsoft_AspNetCore_Identity_IdentityBuilder_Microsoft_AspNetCore_Identity_UI_UIFramework_) method overload no longer exists.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="36a13-103">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="36a13-103">Version introduced</span></span>

<span data-ttu-id="36a13-104">3,0</span><span class="sxs-lookup"><span data-stu-id="36a13-104">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="36a13-105">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="36a13-105">Reason for change</span></span>

<span data-ttu-id="36a13-106">Bu değişiklik, statik web varlıkları özelliğinin benimsenmesinin bir sonucuydu.</span><span class="sxs-lookup"><span data-stu-id="36a13-106">This change was a result of adoption of the static web assets feature.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="36a13-107">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="36a13-107">Recommended action</span></span>

<span data-ttu-id="36a13-108">İki <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType> bağımsız değişken gerektiren aşırı yükleme yerine arayın.</span><span class="sxs-lookup"><span data-stu-id="36a13-108">Call <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType> instead of the overload that takes two arguments.</span></span> <span data-ttu-id="36a13-109">Bootstrap 3 kullanıyorsanız, proje dosyanızdaki bir `<PropertyGroup>` öğeye aşağıdaki satırı da ekleyin:</span><span class="sxs-lookup"><span data-stu-id="36a13-109">If you're using Bootstrap 3, also add the following line to a `<PropertyGroup>` element in your project file:</span></span>

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a><span data-ttu-id="36a13-110">Kategori</span><span class="sxs-lookup"><span data-stu-id="36a13-110">Category</span></span>

<span data-ttu-id="36a13-111">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="36a13-111">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="36a13-112">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="36a13-112">Affected APIs</span></span>

[<span data-ttu-id="36a13-113">IdentityBuilderUIExtensions.AddDefaultUI(IdentityBuilder,UIFramework)</span><span class="sxs-lookup"><span data-stu-id="36a13-113">IdentityBuilderUIExtensions.AddDefaultUI(IdentityBuilder,UIFramework)</span></span>](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.identity.identitybuilderuiextensions.adddefaultui?view=aspnetcore-2.2#Microsoft_AspNetCore_Identity_IdentityBuilderUIExtensions_AddDefaultUI_Microsoft_AspNetCore_Identity_IdentityBuilder_Microsoft_AspNetCore_Identity_UI_UIFramework_)

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->
