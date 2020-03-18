---
ms.openlocfilehash: ac5a3c4f3aefbb59418ad92b2d795f36916f877f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394074"
---
### <a name="spas-spaservices-and-nodeservices-marked-obsolete"></a><span data-ttu-id="3a466-101">STA'lar: SpaServices ve NodeServices eski işaretlenmiş</span><span class="sxs-lookup"><span data-stu-id="3a466-101">SPAs: SpaServices and NodeServices marked obsolete</span></span>

<span data-ttu-id="3a466-102">Aşağıdaki NuGet paketlerinin içeriği Core 2.1'ASP.NET beri gereksizdir.</span><span class="sxs-lookup"><span data-stu-id="3a466-102">The contents of the following NuGet packages have all been unnecessary since ASP.NET Core 2.1.</span></span> <span data-ttu-id="3a466-103">Sonuç olarak, aşağıdaki paketler eski olarak işaretlenmektedir:</span><span class="sxs-lookup"><span data-stu-id="3a466-103">Consequently, the following packages are being marked as obsolete:</span></span>

- [<span data-ttu-id="3a466-104">Microsoft.AspNetCore.SpaServices</span><span class="sxs-lookup"><span data-stu-id="3a466-104">Microsoft.AspNetCore.SpaServices</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices/)
- [<span data-ttu-id="3a466-105">Microsoft.AspNetCore.NodeServices</span><span class="sxs-lookup"><span data-stu-id="3a466-105">Microsoft.AspNetCore.NodeServices</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.NodeServices/)

<span data-ttu-id="3a466-106">Aynı nedenle, aşağıdaki npm modülleri amortismana npm olarak işaretlenmektedir:</span><span class="sxs-lookup"><span data-stu-id="3a466-106">For the same reason, the following npm modules are being marked as deprecated:</span></span>

- [<span data-ttu-id="3a466-107">aspnet-açısal</span><span class="sxs-lookup"><span data-stu-id="3a466-107">aspnet-angular</span></span>](https://www.npmjs.com/package/aspnet-angular)
- [<span data-ttu-id="3a466-108">aspnet önoluşturma</span><span class="sxs-lookup"><span data-stu-id="3a466-108">aspnet-prerendering</span></span>](https://www.npmjs.com/package/aspnet-prerendering)
- [<span data-ttu-id="3a466-109">aspnet-webpack</span><span class="sxs-lookup"><span data-stu-id="3a466-109">aspnet-webpack</span></span>](https://www.npmjs.com/package/aspnet-webpack)
- [<span data-ttu-id="3a466-110">aspnet-webpack-tepki</span><span class="sxs-lookup"><span data-stu-id="3a466-110">aspnet-webpack-react</span></span>](https://www.npmjs.com/package/aspnet-webpack-react)
- [<span data-ttu-id="3a466-111">etki alanı görevi</span><span class="sxs-lookup"><span data-stu-id="3a466-111">domain-task</span></span>](https://www.npmjs.com/package/domain-task)

<span data-ttu-id="3a466-112">Önceki paketler ve npm modülleri daha sonra .NET 5'te kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="3a466-112">The preceding packages and npm modules will later be removed in .NET 5.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3a466-113">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="3a466-113">Version introduced</span></span>

<span data-ttu-id="3a466-114">3,0</span><span class="sxs-lookup"><span data-stu-id="3a466-114">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="3a466-115">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="3a466-115">Old behavior</span></span>

<span data-ttu-id="3a466-116">Amortismana tabi paketler ve npm modülleri ASP.NET Core'u çeşitli Tek Sayfalı Uygulama (SPA) çerçeveleriyle entegre etmeyi amaçlıyordu.</span><span class="sxs-lookup"><span data-stu-id="3a466-116">The deprecated packages and npm modules were intended to integrate ASP.NET Core with various Single-Page App (SPA) frameworks.</span></span> <span data-ttu-id="3a466-117">Bu tür çerçeveler Açısal içerir, React, ve Redux ile React.</span><span class="sxs-lookup"><span data-stu-id="3a466-117">Such frameworks include Angular, React, and React with Redux.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="3a466-118">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="3a466-118">New behavior</span></span>

<span data-ttu-id="3a466-119">[Microsoft.AspNetCore.SpaServices.Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices.Extensions/) NuGet paketinde yeni bir tümleştirme mekanizması bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3a466-119">A new integration mechanism exists in the [Microsoft.AspNetCore.SpaServices.Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices.Extensions/) NuGet package.</span></span> <span data-ttu-id="3a466-120">Paket, Core 2.1'ASP.NET bu yana Açısal ve Tepki proje şablonlarının temelini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3a466-120">The package remains the basis of the Angular and React project templates since ASP.NET Core 2.1.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="3a466-121">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="3a466-121">Reason for change</span></span>

<span data-ttu-id="3a466-122">ASP.NET Core, Açısal, React ve React with Redux gibi çeşitli Tek Sayfalı Uygulama (SPA) çerçeveleriyle tümleştirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="3a466-122">ASP.NET Core supports integration with various Single-Page App (SPA) frameworks, including Angular, React, and React with Redux.</span></span> <span data-ttu-id="3a466-123">Başlangıçta, bu çerçevelerle tümleştirme, sunucu tarafı ön oluşturma ve Webpack ile tümleştirme gibi senaryoları işleyen ASP.NET Core'a özgü bileşenlerle gerçekleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3a466-123">Initially, integration with these frameworks was accomplished with ASP.NET Core-specific components that handled scenarios like server-side prerendering and integration with Webpack.</span></span> <span data-ttu-id="3a466-124">Zaman geçtikçe, endüstri standartları değişti.</span><span class="sxs-lookup"><span data-stu-id="3a466-124">As time went on, industry standards changed.</span></span> <span data-ttu-id="3a466-125">SPA çerçevelerinin her biri kendi standart komut satırı arayüzlerini yayımladı.</span><span class="sxs-lookup"><span data-stu-id="3a466-125">Each of the SPA frameworks released their own standard command-line interfaces.</span></span> <span data-ttu-id="3a466-126">Örneğin, Açısal CLI ve create-react-app.</span><span class="sxs-lookup"><span data-stu-id="3a466-126">For example, Angular CLI and create-react-app.</span></span>

<span data-ttu-id="3a466-127">ASP.NET Core 2.1 Mayıs 2018'de piyasaya sürüldüğünde, ekip standartlardaki değişikliğe yanıt verdi.</span><span class="sxs-lookup"><span data-stu-id="3a466-127">When ASP.NET Core 2.1 was released in May 2018, the team responded to the change in standards.</span></span> <span data-ttu-id="3a466-128">SPA çerçevelerinin kendi araç zincirleriyle entegre olmak için daha yeni ve daha basit bir yol sağlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="3a466-128">A newer and simpler way to integrate with the SPA frameworks' own toolchains was provided.</span></span> <span data-ttu-id="3a466-129">Yeni tümleştirme mekanizması pakette `Microsoft.AspNetCore.SpaServices.Extensions` bulunur ve Core 2.1'den ASP.NET bu yana Açısal ve Tepki proje şablonlarının temelini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3a466-129">The new integration mechanism exists in the package `Microsoft.AspNetCore.SpaServices.Extensions` and remains the basis of the Angular and React project templates since ASP.NET Core 2.1.</span></span>

<span data-ttu-id="3a466-130">Eski ASP.NET Core'a özgü bileşenlerin alakasız olduğunu ve önerilmediğini açıklığa kavuşturmak için:</span><span class="sxs-lookup"><span data-stu-id="3a466-130">To clarify that the older ASP.NET Core-specific components are irrelevant and not recommended:</span></span>

- <span data-ttu-id="3a466-131">Pre-2.1 tümleştirme mekanizması eski olarak işaretlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="3a466-131">The pre-2.1 integration mechanism is marked as obsolete.</span></span>
- <span data-ttu-id="3a466-132">Destekleyen npm paketleri amortismana lı olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="3a466-132">The supporting npm packages are marked as deprecated.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3a466-133">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="3a466-133">Recommended action</span></span>

<span data-ttu-id="3a466-134">Bu paketleri kullanıyorsanız, işlevselliği kullanmak için uygulamalarınızı güncelleyin:</span><span class="sxs-lookup"><span data-stu-id="3a466-134">If you're using these packages, update your apps to use the functionality:</span></span>

- <span data-ttu-id="3a466-135">Pakette. `Microsoft.AspNetCore.SpaServices.Extensions`</span><span class="sxs-lookup"><span data-stu-id="3a466-135">In the `Microsoft.AspNetCore.SpaServices.Extensions` package.</span></span>
- <span data-ttu-id="3a466-136">Kullandığınız SPA çerçeveleri tarafından sağlanan</span><span class="sxs-lookup"><span data-stu-id="3a466-136">Provided by the SPA frameworks you're using</span></span>

<span data-ttu-id="3a466-137">Sunucu tarafı önoluşturma ve sıcak modül yeniden yüklemesi gibi özellikleri etkinleştirmek için ilgili SPA çerçevesi için belgelere bakın.</span><span class="sxs-lookup"><span data-stu-id="3a466-137">To enable features like server-side prerendering and hot module reload, see the documentation for the corresponding SPA framework.</span></span> <span data-ttu-id="3a466-138">İşlevsellik eski `Microsoft.AspNetCore.SpaServices.Extensions` *değildir* ve desteklenmeye devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="3a466-138">The functionality in `Microsoft.AspNetCore.SpaServices.Extensions` is *not* obsolete and will continue to be supported.</span></span>

#### <a name="category"></a><span data-ttu-id="3a466-139">Kategori</span><span class="sxs-lookup"><span data-stu-id="3a466-139">Category</span></span>

<span data-ttu-id="3a466-140">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="3a466-140">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3a466-141">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="3a466-141">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Builder.SpaRouteExtensions?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.WebpackDevMiddleware?displayProperty=nameWithType>

- <xref:Microsoft.AspNetCore.NodeServices.EmbeddedResourceReader?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.INodeServices?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.NodeServicesFactory?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.NodeServicesOptions?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.StringAsTempFile?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.INodeInstance?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationException?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationInfo?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.NodeServicesOptionsExtensions?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.OutOfProcessNodeInstance?displayProperty=nameWithType>

- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerenderer?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerendererBuilder?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.JavaScriptModuleExport?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.Prerenderer?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.PrerenderTagHelper?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.RenderToStringResult?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Webpack.WebpackDevMiddlewareOptions?displayProperty=nameWithType>

- <xref:Microsoft.Extensions.DependencyInjection.NodeServicesServiceCollectionExtensions?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.DependencyInjection.PrerenderingServiceCollectionExtensions?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.AspNetCore.Builder.SpaRouteExtensions`
- `T:Microsoft.AspNetCore.Builder.WebpackDevMiddleware`

- `T:Microsoft.AspNetCore.NodeServices.EmbeddedResourceReader`
- `T:Microsoft.AspNetCore.NodeServices.INodeServices`
- `T:Microsoft.AspNetCore.NodeServices.NodeServicesFactory`
- `T:Microsoft.AspNetCore.NodeServices.NodeServicesOptions`
- `T:Microsoft.AspNetCore.NodeServices.StringAsTempFile`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.INodeInstance`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationException`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationInfo`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.NodeServicesOptionsExtensions`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.OutOfProcessNodeInstance`

- `T:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerenderer`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerendererBuilder`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.JavaScriptModuleExport`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.Prerenderer`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.PrerenderTagHelper`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.RenderToStringResult`
- `T:Microsoft.AspNetCore.SpaServices.Webpack.WebpackDevMiddlewareOptions`

- `T:Microsoft.Extensions.DependencyInjection.NodeServicesServiceCollectionExtensions`
- `T:Microsoft.Extensions.DependencyInjection.PrerenderingServiceCollectionExtensions`

-->
