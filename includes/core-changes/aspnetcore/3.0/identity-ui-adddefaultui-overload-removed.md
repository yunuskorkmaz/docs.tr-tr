---
ms.openlocfilehash: 806722ea9aec1c828786525e3155b7f624159ac1
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522678"
---
### <a name="identity-adddefaultui-method-overload-removed"></a><span data-ttu-id="49a26-101">Kimlik: Adddefaultuı yöntemi aşırı yüklemesi kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="49a26-101">Identity: AddDefaultUI method overload removed</span></span>

<span data-ttu-id="49a26-102">ASP.NET Core 3,0 ' den başlayarak <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=nameWithType> yöntemi aşırı yüklemesi artık yok.</span><span class="sxs-lookup"><span data-stu-id="49a26-102">Starting with ASP.NET Core 3.0, the <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=nameWithType> method overload no longer exists.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="49a26-103">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="49a26-103">Version introduced</span></span>

<span data-ttu-id="49a26-104">3.0</span><span class="sxs-lookup"><span data-stu-id="49a26-104">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="49a26-105">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="49a26-105">Reason for change</span></span>

<span data-ttu-id="49a26-106">Bu değişiklik, statik Web varlıkları özelliğini benimsemenin bir sonucudur.</span><span class="sxs-lookup"><span data-stu-id="49a26-106">This change was a result of adoption of the static web assets feature.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="49a26-107">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="49a26-107">Recommended action</span></span>

<span data-ttu-id="49a26-108">Aşırı yükleme yerine <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType> çağırın.</span><span class="sxs-lookup"><span data-stu-id="49a26-108">Call <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType> instead of the overload.</span></span> <span data-ttu-id="49a26-109">Önyükleme 3 kullanıyorsanız, aşağıdaki satırı proje dosyanızdaki bir `<PropertyGroup>` öğesine de ekleyin:</span><span class="sxs-lookup"><span data-stu-id="49a26-109">If you're using Bootstrap 3, also add the following line to a `<PropertyGroup>` element in your project file:</span></span>

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a><span data-ttu-id="49a26-110">Kategori</span><span class="sxs-lookup"><span data-stu-id="49a26-110">Category</span></span>

<span data-ttu-id="49a26-111">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="49a26-111">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="49a26-112">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="49a26-112">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->
