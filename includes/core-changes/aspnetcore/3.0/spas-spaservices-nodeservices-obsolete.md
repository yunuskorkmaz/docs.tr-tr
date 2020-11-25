---
ms.openlocfilehash: ac5a3c4f3aefbb59418ad92b2d795f36916f877f
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032901"
---
### <a name="spas-spaservices-and-nodeservices-marked-obsolete"></a><span data-ttu-id="23a3b-101">Maça 'Lar: gereksiz olarak işaretlenen SpaServices ve NodeServices</span><span class="sxs-lookup"><span data-stu-id="23a3b-101">SPAs: SpaServices and NodeServices marked obsolete</span></span>

<span data-ttu-id="23a3b-102">ASP.NET Core 2,1 ' den bu yana aşağıdaki NuGet paketlerinin içeriği gereksizdir.</span><span class="sxs-lookup"><span data-stu-id="23a3b-102">The contents of the following NuGet packages have all been unnecessary since ASP.NET Core 2.1.</span></span> <span data-ttu-id="23a3b-103">Sonuç olarak, aşağıdaki paketler artık kullanılmıyor olarak işaretlenir:</span><span class="sxs-lookup"><span data-stu-id="23a3b-103">Consequently, the following packages are being marked as obsolete:</span></span>

- [<span data-ttu-id="23a3b-104">Microsoft. AspNetCore. SpaServices</span><span class="sxs-lookup"><span data-stu-id="23a3b-104">Microsoft.AspNetCore.SpaServices</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices/)
- [<span data-ttu-id="23a3b-105">Microsoft. AspNetCore. NodeServices</span><span class="sxs-lookup"><span data-stu-id="23a3b-105">Microsoft.AspNetCore.NodeServices</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.NodeServices/)

<span data-ttu-id="23a3b-106">Aynı nedenden dolayı, aşağıdaki NPM modülleri kullanım dışı olarak işaretlenmekte:</span><span class="sxs-lookup"><span data-stu-id="23a3b-106">For the same reason, the following npm modules are being marked as deprecated:</span></span>

- [<span data-ttu-id="23a3b-107">ASPNET-angular</span><span class="sxs-lookup"><span data-stu-id="23a3b-107">aspnet-angular</span></span>](https://www.npmjs.com/package/aspnet-angular)
- [<span data-ttu-id="23a3b-108">ASPNET-prerendering</span><span class="sxs-lookup"><span data-stu-id="23a3b-108">aspnet-prerendering</span></span>](https://www.npmjs.com/package/aspnet-prerendering)
- [<span data-ttu-id="23a3b-109">ASPNET-WebPack</span><span class="sxs-lookup"><span data-stu-id="23a3b-109">aspnet-webpack</span></span>](https://www.npmjs.com/package/aspnet-webpack)
- [<span data-ttu-id="23a3b-110">ASPNET-WebPack-tepki verme</span><span class="sxs-lookup"><span data-stu-id="23a3b-110">aspnet-webpack-react</span></span>](https://www.npmjs.com/package/aspnet-webpack-react)
- [<span data-ttu-id="23a3b-111">etki alanı-görev</span><span class="sxs-lookup"><span data-stu-id="23a3b-111">domain-task</span></span>](https://www.npmjs.com/package/domain-task)

<span data-ttu-id="23a3b-112">Önceki paketler ve NPM modülleri daha sonra .NET 5 ' te kaldırılacaktır.</span><span class="sxs-lookup"><span data-stu-id="23a3b-112">The preceding packages and npm modules will later be removed in .NET 5.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="23a3b-113">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="23a3b-113">Version introduced</span></span>

<span data-ttu-id="23a3b-114">3,0</span><span class="sxs-lookup"><span data-stu-id="23a3b-114">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="23a3b-115">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="23a3b-115">Old behavior</span></span>

<span data-ttu-id="23a3b-116">Kullanım dışı bırakılan paketler ve NPM modülleri, ASP.NET Core çeşitli Single-Page App (SPA) çerçeveleri ile tümleştirilecek şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="23a3b-116">The deprecated packages and npm modules were intended to integrate ASP.NET Core with various Single-Page App (SPA) frameworks.</span></span> <span data-ttu-id="23a3b-117">Bu tür çerçeveler, Redux ile angular, tepki verme ve tepki verme içerir.</span><span class="sxs-lookup"><span data-stu-id="23a3b-117">Such frameworks include Angular, React, and React with Redux.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="23a3b-118">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="23a3b-118">New behavior</span></span>

<span data-ttu-id="23a3b-119">[Microsoft. AspNetCore. SpaServices. Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices.Extensions/) NuGet paketinde yeni bir tümleştirme mekanizması bulunur.</span><span class="sxs-lookup"><span data-stu-id="23a3b-119">A new integration mechanism exists in the [Microsoft.AspNetCore.SpaServices.Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices.Extensions/) NuGet package.</span></span> <span data-ttu-id="23a3b-120">Paket, ASP.NET Core 2,1 ' den itibaren angular ve tepki verme projesi şablonlarına göre kalır.</span><span class="sxs-lookup"><span data-stu-id="23a3b-120">The package remains the basis of the Angular and React project templates since ASP.NET Core 2.1.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="23a3b-121">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="23a3b-121">Reason for change</span></span>

<span data-ttu-id="23a3b-122">ASP.NET Core, angular, tepki verme ve Redux ile tepki verme gibi çeşitli Single-Page uygulama (SPA) çerçeveleri ile tümleştirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="23a3b-122">ASP.NET Core supports integration with various Single-Page App (SPA) frameworks, including Angular, React, and React with Redux.</span></span> <span data-ttu-id="23a3b-123">Başlangıçta bu çerçevelerle tümleştirme, sunucu tarafı prerendering ve WebPack ile tümleştirme gibi senaryolar işlenen ASP.NET Core özel bileşenlerle oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="23a3b-123">Initially, integration with these frameworks was accomplished with ASP.NET Core-specific components that handled scenarios like server-side prerendering and integration with Webpack.</span></span> <span data-ttu-id="23a3b-124">Saat itibarıyla, sektör standartları değişmiştir.</span><span class="sxs-lookup"><span data-stu-id="23a3b-124">As time went on, industry standards changed.</span></span> <span data-ttu-id="23a3b-125">SPA çerçevelerinin her biri kendi standart komut satırı arabirimlerini serbest bıraktı.</span><span class="sxs-lookup"><span data-stu-id="23a3b-125">Each of the SPA frameworks released their own standard command-line interfaces.</span></span> <span data-ttu-id="23a3b-126">Örneğin, angular CLı ve oluşturma-tepki-uygulama.</span><span class="sxs-lookup"><span data-stu-id="23a3b-126">For example, Angular CLI and create-react-app.</span></span>

<span data-ttu-id="23a3b-127">ASP.NET Core 2,1 Mayıs 2018 ' de yayınlanmışsa, takım standartlara göre değişikliğe cevap verdi.</span><span class="sxs-lookup"><span data-stu-id="23a3b-127">When ASP.NET Core 2.1 was released in May 2018, the team responded to the change in standards.</span></span> <span data-ttu-id="23a3b-128">SPA çerçevelerinin kendi araç zincirleriyle tümleştirmenin daha yeni ve kolay bir yolu sağlandı.</span><span class="sxs-lookup"><span data-stu-id="23a3b-128">A newer and simpler way to integrate with the SPA frameworks' own toolchains was provided.</span></span> <span data-ttu-id="23a3b-129">Yeni tümleştirme mekanizması pakette bulunur `Microsoft.AspNetCore.SpaServices.Extensions` ve 2,1 ASP.NET Core sonrasında angular ve tepki verme projesi şablonlarına göre kalır.</span><span class="sxs-lookup"><span data-stu-id="23a3b-129">The new integration mechanism exists in the package `Microsoft.AspNetCore.SpaServices.Extensions` and remains the basis of the Angular and React project templates since ASP.NET Core 2.1.</span></span>

<span data-ttu-id="23a3b-130">Eski ASP.NET Core özgü bileşenlerin ilgisiz olduğunu ve önerilmediğini netleştirmek için:</span><span class="sxs-lookup"><span data-stu-id="23a3b-130">To clarify that the older ASP.NET Core-specific components are irrelevant and not recommended:</span></span>

- <span data-ttu-id="23a3b-131">2,1 öncesi tümleştirme mekanizması eski olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="23a3b-131">The pre-2.1 integration mechanism is marked as obsolete.</span></span>
- <span data-ttu-id="23a3b-132">Destekleyici NPM paketleri kullanım dışı olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="23a3b-132">The supporting npm packages are marked as deprecated.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="23a3b-133">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="23a3b-133">Recommended action</span></span>

<span data-ttu-id="23a3b-134">Bu paketleri kullanıyorsanız, işlevleri kullanmak için uygulamalarınızı güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="23a3b-134">If you're using these packages, update your apps to use the functionality:</span></span>

- <span data-ttu-id="23a3b-135">Paketini yeniden yapın `Microsoft.AspNetCore.SpaServices.Extensions` .</span><span class="sxs-lookup"><span data-stu-id="23a3b-135">In the `Microsoft.AspNetCore.SpaServices.Extensions` package.</span></span>
- <span data-ttu-id="23a3b-136">Kullanmakta olduğunuz SPA çerçeveleri tarafından sağlanıyor</span><span class="sxs-lookup"><span data-stu-id="23a3b-136">Provided by the SPA frameworks you're using</span></span>

<span data-ttu-id="23a3b-137">Sunucu tarafı prerendering ve sık erişimli modül yeniden yükleme gibi özellikleri etkinleştirmek için ilgili SPA çerçevesine yönelik belgelere bakın.</span><span class="sxs-lookup"><span data-stu-id="23a3b-137">To enable features like server-side prerendering and hot module reload, see the documentation for the corresponding SPA framework.</span></span> <span data-ttu-id="23a3b-138">İçindeki işlev `Microsoft.AspNetCore.SpaServices.Extensions` kullanılmıyor ve *not* desteklenmeye devam edecek.</span><span class="sxs-lookup"><span data-stu-id="23a3b-138">The functionality in `Microsoft.AspNetCore.SpaServices.Extensions` is *not* obsolete and will continue to be supported.</span></span>

#### <a name="category"></a><span data-ttu-id="23a3b-139">Kategori</span><span class="sxs-lookup"><span data-stu-id="23a3b-139">Category</span></span>

<span data-ttu-id="23a3b-140">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="23a3b-140">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="23a3b-141">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="23a3b-141">Affected APIs</span></span>

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
