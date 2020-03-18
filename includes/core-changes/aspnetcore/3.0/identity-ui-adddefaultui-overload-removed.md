---
ms.openlocfilehash: 806722ea9aec1c828786525e3155b7f624159ac1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522678"
---
### <a name="identity-adddefaultui-method-overload-removed"></a><span data-ttu-id="86280-101">Kimlik: AddDefaultUI yöntemi aşırı kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="86280-101">Identity: AddDefaultUI method overload removed</span></span>

<span data-ttu-id="86280-102">Core 3.0 ASP.NET ile <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=nameWithType> başlayarak, yöntem aşırı artık yok.</span><span class="sxs-lookup"><span data-stu-id="86280-102">Starting with ASP.NET Core 3.0, the <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=nameWithType> method overload no longer exists.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="86280-103">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="86280-103">Version introduced</span></span>

<span data-ttu-id="86280-104">3,0</span><span class="sxs-lookup"><span data-stu-id="86280-104">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="86280-105">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="86280-105">Reason for change</span></span>

<span data-ttu-id="86280-106">Bu değişiklik, statik web varlıkları özelliğinin benimsenmesinin bir sonucuydu.</span><span class="sxs-lookup"><span data-stu-id="86280-106">This change was a result of adoption of the static web assets feature.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="86280-107">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="86280-107">Recommended action</span></span>

<span data-ttu-id="86280-108">Aşırı <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType> yükleme yerine arayın.</span><span class="sxs-lookup"><span data-stu-id="86280-108">Call <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType> instead of the overload.</span></span> <span data-ttu-id="86280-109">Bootstrap 3 kullanıyorsanız, proje dosyanızdaki bir `<PropertyGroup>` öğeye aşağıdaki satırı da ekleyin:</span><span class="sxs-lookup"><span data-stu-id="86280-109">If you're using Bootstrap 3, also add the following line to a `<PropertyGroup>` element in your project file:</span></span>

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a><span data-ttu-id="86280-110">Kategori</span><span class="sxs-lookup"><span data-stu-id="86280-110">Category</span></span>

<span data-ttu-id="86280-111">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="86280-111">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="86280-112">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="86280-112">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->
