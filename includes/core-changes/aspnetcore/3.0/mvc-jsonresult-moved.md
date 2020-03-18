---
ms.openlocfilehash: f6fd75c5b49156f44d31c650ea452eb549f13b0e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901685"
---
### <a name="mvc-jsonresult-moved-to-microsoftaspnetcoremvccore"></a><span data-ttu-id="e43b5-101">MVC: JsonResult Microsoft.AspNetCore.Mvc.Core taşındı</span><span class="sxs-lookup"><span data-stu-id="e43b5-101">MVC: JsonResult moved to Microsoft.AspNetCore.Mvc.Core</span></span>

<span data-ttu-id="e43b5-102">`JsonResult`meclise `Microsoft.AspNetCore.Mvc.Core` taşındı.</span><span class="sxs-lookup"><span data-stu-id="e43b5-102">`JsonResult` has moved to the `Microsoft.AspNetCore.Mvc.Core` assembly.</span></span> <span data-ttu-id="e43b5-103">Bu tür [Microsoft.AspNetCore.Mvc.Formatters.Json](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Formatters.Json)tanımlanır için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e43b5-103">This type used to be defined in [Microsoft.AspNetCore.Mvc.Formatters.Json](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Formatters.Json).</span></span> <span data-ttu-id="e43b5-104">Bu sorunu kullanıcıların çoğunluğu için `Microsoft.AspNetCore.Mvc.Formatters.Json` gidermek için derleme düzeyinde [[TypeForwardedTo]](xref:System.Runtime.CompilerServices.TypeForwardedToAttribute) özniteliği eklendi.</span><span class="sxs-lookup"><span data-stu-id="e43b5-104">An assembly-level [[TypeForwardedTo]](xref:System.Runtime.CompilerServices.TypeForwardedToAttribute) attribute was added to `Microsoft.AspNetCore.Mvc.Formatters.Json` to address this issue for the majority of users.</span></span> <span data-ttu-id="e43b5-105">Üçüncü taraf kitaplıkları kullanan uygulamalar sorunlarla karşılaşabilir.</span><span class="sxs-lookup"><span data-stu-id="e43b5-105">Apps that use third-party libraries may encounter issues.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e43b5-106">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="e43b5-106">Version introduced</span></span>

<span data-ttu-id="e43b5-107">3.0 Önizleme 6</span><span class="sxs-lookup"><span data-stu-id="e43b5-107">3.0 Preview 6</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="e43b5-108">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="e43b5-108">Old behavior</span></span>

<span data-ttu-id="e43b5-109">2,2 tabanlı kitaplık kullanan bir uygulama başarıyla oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e43b5-109">An app using a 2.2-based library builds successfully.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="e43b5-110">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="e43b5-110">New behavior</span></span>

<span data-ttu-id="e43b5-111">2.2 tabanlı kitaplık kullanan bir uygulama derlemede başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="e43b5-111">An app using a 2.2-based library fails compilation.</span></span> <span data-ttu-id="e43b5-112">Aşağıdaki metnin bir varyasyonunu içeren bir hata sağlanır:</span><span class="sxs-lookup"><span data-stu-id="e43b5-112">An error containing a variation of the following text is provided:</span></span>

```
The type 'JsonResult' exists in both 'Microsoft.AspNetCore.Mvc.Core, Version=3.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60' and 'Microsoft.AspNetCore.Mvc.Formatters.Json, Version=2.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60'
```

<span data-ttu-id="e43b5-113">Böyle bir sorun örneği için [dotnet/aspnetcore#7220'ye](https://github.com/dotnet/aspnetcore/issues/7220)bakın.</span><span class="sxs-lookup"><span data-stu-id="e43b5-113">For an example of such an issue, see [dotnet/aspnetcore#7220](https://github.com/dotnet/aspnetcore/issues/7220).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="e43b5-114">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="e43b5-114">Reason for change</span></span>

<span data-ttu-id="e43b5-115">[aspnet/Announcements#325](https://github.com/aspnet/Announcements/issues/325)adresinde açıklandığı gibi ASP.NET Core bileşiminde platform düzeyinde değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="e43b5-115">Platform-level changes to the composition of ASP.NET Core as described at [aspnet/Announcements#325](https://github.com/aspnet/Announcements/issues/325).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e43b5-116">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="e43b5-116">Recommended action</span></span>

<span data-ttu-id="e43b5-117">2.2 sürümüne `Microsoft.AspNetCore.Mvc.Formatters.Json` karşı derlenen kitaplıkların tüm tüketiciler için sorunu çözmek için yeniden derlenmeleri gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="e43b5-117">Libraries compiled against the 2.2 version of `Microsoft.AspNetCore.Mvc.Formatters.Json` may need to recompile to address the problem for all consumers.</span></span> <span data-ttu-id="e43b5-118">Etkilenirse, kitaplık yazarına başvurun.</span><span class="sxs-lookup"><span data-stu-id="e43b5-118">If affected, contact the library author.</span></span> <span data-ttu-id="e43b5-119">Core 3.0 ASP.NET hedeflemek için kitaplığın yeniden derlemisini isteyin.</span><span class="sxs-lookup"><span data-stu-id="e43b5-119">Request recompilation of the library to target ASP.NET Core 3.0.</span></span>

#### <a name="category"></a><span data-ttu-id="e43b5-120">Kategori</span><span class="sxs-lookup"><span data-stu-id="e43b5-120">Category</span></span>

<span data-ttu-id="e43b5-121">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="e43b5-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e43b5-122">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="e43b5-122">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Mvc.JsonResult?displayProperty=nameWithType>

<!-- 

### Affected APIs

`T:Microsoft.AspNetCore.Mvc.JsonResult`

-->
