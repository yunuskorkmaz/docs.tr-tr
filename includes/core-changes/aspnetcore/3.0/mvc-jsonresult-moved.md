---
ms.openlocfilehash: 4f2ace670884d154b219d2146a242d2cee098831
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344299"
---
### <a name="mvc-jsonresult-moved-to-microsoftaspnetcoremvccore"></a><span data-ttu-id="9ed4d-101">MVC: JsonResult, Microsoft. AspNetCore. Mvc. Core 'a taşındı</span><span class="sxs-lookup"><span data-stu-id="9ed4d-101">MVC: JsonResult moved to Microsoft.AspNetCore.Mvc.Core</span></span>

<span data-ttu-id="9ed4d-102">`JsonResult` `Microsoft.AspNetCore.Mvc.Core` derlemesine taşındı.</span><span class="sxs-lookup"><span data-stu-id="9ed4d-102">`JsonResult` has moved to the `Microsoft.AspNetCore.Mvc.Core` assembly.</span></span> <span data-ttu-id="9ed4d-103">Bu tür, [Microsoft. AspNetCore. Mvc. Formatters. JSON](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Formatters.Json)içinde tanımlanması için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9ed4d-103">This type used to be defined in [Microsoft.AspNetCore.Mvc.Formatters.Json](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Formatters.Json).</span></span> <span data-ttu-id="9ed4d-104">Kullanıcıların çoğunluğu için bu sorunu gidermek üzere `Microsoft.AspNetCore.Mvc.Formatters.Json` derleme düzeyi [[TypeForwardedTo]](xref:System.Runtime.CompilerServices.TypeForwardedToAttribute) özniteliği eklendi.</span><span class="sxs-lookup"><span data-stu-id="9ed4d-104">An assembly-level [[TypeForwardedTo]](xref:System.Runtime.CompilerServices.TypeForwardedToAttribute) attribute was added to `Microsoft.AspNetCore.Mvc.Formatters.Json` to address this issue for the majority of users.</span></span> <span data-ttu-id="9ed4d-105">Üçüncü taraf kitaplıklar kullanan uygulamalar sorunlarla karşılaşabilir.</span><span class="sxs-lookup"><span data-stu-id="9ed4d-105">Apps that use third-party libraries may encounter issues.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9ed4d-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="9ed4d-106">Version introduced</span></span>

<span data-ttu-id="9ed4d-107">3,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="9ed4d-107">3.0 Preview 6</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="9ed4d-108">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="9ed4d-108">Old behavior</span></span>

<span data-ttu-id="9ed4d-109">2,2 tabanlı kitaplık kullanan bir uygulama başarıyla oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9ed4d-109">An app using a 2.2-based library builds successfully.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="9ed4d-110">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="9ed4d-110">New behavior</span></span>

<span data-ttu-id="9ed4d-111">2,2 tabanlı kitaplık kullanan bir uygulama derleme hatası verir.</span><span class="sxs-lookup"><span data-stu-id="9ed4d-111">An app using a 2.2-based library fails compilation.</span></span> <span data-ttu-id="9ed4d-112">Aşağıdaki metnin bir varyasyonunu içeren bir hata verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="9ed4d-112">An error containing a variation of the following text is provided:</span></span>

```
The type 'JsonResult' exists in both 'Microsoft.AspNetCore.Mvc.Core, Version=3.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60' and 'Microsoft.AspNetCore.Mvc.Formatters.Json, Version=2.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60'
```

<span data-ttu-id="9ed4d-113">Bu tür bir sorunun örneği için bkz. [ASPNET/AspNetCore # 7220](https://github.com/aspnet/AspNetCore/issues/7220).</span><span class="sxs-lookup"><span data-stu-id="9ed4d-113">For an example of such an issue, see [aspnet/AspNetCore#7220](https://github.com/aspnet/AspNetCore/issues/7220).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="9ed4d-114">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="9ed4d-114">Reason for change</span></span>

<span data-ttu-id="9ed4d-115">ASP.NET Core, [ASPNET/Duyurular # 325](https://github.com/aspnet/Announcements/issues/325)bölümünde açıklandığı gibi bileşim düzeyinde değişir.</span><span class="sxs-lookup"><span data-stu-id="9ed4d-115">Platform-level changes to the composition of ASP.NET Core as described at [aspnet/Announcements#325](https://github.com/aspnet/Announcements/issues/325).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9ed4d-116">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="9ed4d-116">Recommended action</span></span>

<span data-ttu-id="9ed4d-117">`Microsoft.AspNetCore.Mvc.Formatters.Json` 2,2 sürümüne göre derlenen kitaplıkların, tüm tüketiciler için sorunu gidermek üzere yeniden derlenmesi gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="9ed4d-117">Libraries compiled against the 2.2 version of `Microsoft.AspNetCore.Mvc.Formatters.Json` may need to recompile to address the problem for all consumers.</span></span> <span data-ttu-id="9ed4d-118">Etkileniyorsa kitaplık yazarına başvurun.</span><span class="sxs-lookup"><span data-stu-id="9ed4d-118">If affected, contact the library author.</span></span> <span data-ttu-id="9ed4d-119">ASP.NET Core 3,0 ' i hedeflemek için kitaplığın yeniden derlenmesi isteği.</span><span class="sxs-lookup"><span data-stu-id="9ed4d-119">Request recompilation of the library to target ASP.NET Core 3.0.</span></span>

#### <a name="category"></a><span data-ttu-id="9ed4d-120">Kategori</span><span class="sxs-lookup"><span data-stu-id="9ed4d-120">Category</span></span>

<span data-ttu-id="9ed4d-121">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9ed4d-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9ed4d-122">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="9ed4d-122">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Mvc.JsonResult?displayProperty=nameWithType>

<!-- 

### Affected APIs

`T:Microsoft.AspNetCore.Mvc.JsonResult`

-->
