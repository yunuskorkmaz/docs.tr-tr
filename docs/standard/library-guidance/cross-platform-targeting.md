---
title: Platformlar arası hedefleme
description: Platformlar arası .NET kitaplıkları oluşturmak için en iyi yöntem önerileri.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 72fa891d5b1054af485a98d89b4efb11d6b0018b
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50202822"
---
# <a name="cross-platform-targeting"></a><span data-ttu-id="7e5f8-103">Platformlar arası hedefleme</span><span class="sxs-lookup"><span data-stu-id="7e5f8-103">Cross-platform targeting</span></span>

<span data-ttu-id="7e5f8-104">Birden çok işletim sistemleri ve cihazların modern .NET destekler.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-104">Modern .NET supports multiple operating systems and devices.</span></span> <span data-ttu-id="7e5f8-105">Azure veya bir .NET oyununuzu Unity barındırılan ASP.NET Web sitesi oluşturuyor mümkün olduğu kadar çok geliştiricileri desteklemek .NET açık kaynak kitaplıkları için önemlidir.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-105">It's important for .NET open-source libraries to support as many developers as possible, whether they're building an ASP.NET website hosted in Azure, or a .NET game in Unity.</span></span>

## <a name="net-standard"></a><span data-ttu-id="7e5f8-106">.NET standard</span><span class="sxs-lookup"><span data-stu-id="7e5f8-106">.NET Standard</span></span>

<span data-ttu-id="7e5f8-107">.NET standard platformlar arası destek .NET Kitaplığı'na eklemek için en iyi yoludur.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-107">.NET Standard is the best way to add cross-platform support to a .NET library.</span></span> <span data-ttu-id="7e5f8-108">[.NET standard](../net-standard.md) bir belirtimi .NET API'leri, tüm .NET uygulamalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-108">[.NET Standard](../net-standard.md) is a specification of .NET APIs that are available on all .NET implementations.</span></span> <span data-ttu-id="7e5f8-109">.NET Standard hedefleyen Standard'ın .NET, .NET Standard sürümünü kullanan tüm platformlar tarafından kullanılabilir olması anlamına gelir, belirli bir sürümü olan API'leri kullanmak için kısıtlanır kitaplıkları oluşturmak olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-109">Targeting .NET Standard lets you produce libraries that are constrained to use APIs that are in a given version of .NET Standard, which means it's usable by all platforms that implement that version of the .NET Standard.</span></span>

<span data-ttu-id="7e5f8-110">![.NET standard](./media/cross-platform-targeting/platforms-netstandard.png ".NET Standard")</span><span class="sxs-lookup"><span data-stu-id="7e5f8-110">![.NET Standard](./media/cross-platform-targeting/platforms-netstandard.png ".NET Standard")</span></span>

<span data-ttu-id="7e5f8-111">.NET Standard desteği ve başarıyla projenizde, derlemek, kitaplık başarıyla tüm platformlarda çalışacak garanti etmez:</span><span class="sxs-lookup"><span data-stu-id="7e5f8-111">Targeting .NET Standard, and successfully compiling your project, doesn't guarantee the library will run successfully on all platforms:</span></span>

1. <span data-ttu-id="7e5f8-112">Platforma özgü API, diğer platformlarda başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-112">Platform-specific APIs will fail on other platforms.</span></span> <span data-ttu-id="7e5f8-113">Örneğin, <xref:Microsoft.Win32.Registry?displayProperty=nameWithType> Windows üzerinde başarısız ve throw <xref:System.PlatformNotSupportedException> diğer tüm işletim sistemlerinde kullanıldığında.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-113">For example, <xref:Microsoft.Win32.Registry?displayProperty=nameWithType> will succeed on Windows and throw <xref:System.PlatformNotSupportedException> when used on any other OS.</span></span>
2. <span data-ttu-id="7e5f8-114">API'ler farklı şekilde davranabilir.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-114">APIs can behave differently.</span></span> <span data-ttu-id="7e5f8-115">Örneğin, bir uygulama, iOS veya UWP, zamanında tamamlanan derleme kullandığında yansıma API'leri farklı performans özelliklerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-115">For example, reflection APIs have different performance characteristics when an application uses ahead-of-time compilation on iOS or UWP.</span></span>

> [!TIP]
> <span data-ttu-id="7e5f8-116">.NET ekibi [Roslyn çözümleyicinizi sunar](../analyzers/api-analyzer.md) olası sorunları keşfetmenize yardımcı olmak için.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-116">The .NET team [offers a Roslyn analyzer](../analyzers/api-analyzer.md) to help you discover possible issues.</span></span>

<span data-ttu-id="7e5f8-117">**✔️ YAPMAK** dahil olmak üzere ile Başlat bir `netstandard2.0` hedef.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-117">**✔️ DO** start with including a `netstandard2.0` target.</span></span>

> <span data-ttu-id="7e5f8-118">En genel amaçlı kitaplıkları API'ler .NET Standard 2.0 dışında gerçekleştirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-118">Most general-purpose libraries should not need APIs outside of .NET Standard 2.0.</span></span> <span data-ttu-id="7e5f8-119">.NET standard 2.0 tüm modern platformlar tarafından desteklenir ve bir hedef ile birden çok platform desteklemek için önerilen yoldur.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-119">.NET Standard 2.0 is supported by all modern platforms and is the recommended way to support multiple platforms with one target.</span></span>

<span data-ttu-id="7e5f8-120">**❌ KAÇININ** dahil olmak üzere bir `netstandard1.x` hedef.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-120">**❌ AVOID** including a `netstandard1.x` target.</span></span>

> <span data-ttu-id="7e5f8-121">.NET standard 1.x NuGet paketlerini büyük paket bağımlılık grafiği oluşturur ve geliştiricilerin çok sayıda paketleri oluştururken indirme sonuçları ayrıntılı kümesi olarak dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-121">.NET Standard 1.x is distributed as a granular set of NuGet packages, which creates a large package dependency graph and results in developers downloading a lot of packages when building.</span></span> <span data-ttu-id="7e5f8-122">.NET Framework 4.6.1, UWP ve Xamarin, gibi Modern .NET platformları, tüm .NET Standard 2.0 desteği.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-122">Modern .NET platforms, including .NET Framework 4.6.1, UWP and Xamarin, all support .NET Standard 2.0.</span></span> <span data-ttu-id="7e5f8-123">Yalnızca .NET Standard hedeflemesi gereken özellikle daha eski bir platformunu hedeflemeniz gerekirse 1.x.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-123">You should only target .NET Standard 1.x if you specifically need to target an older platform.</span></span>

<span data-ttu-id="7e5f8-124">**✔️ YAPMAK** dahil bir `netstandard2.0` gerektiriyorsa hedef bir `netstandard1.x` hedef.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-124">**✔️ DO** include a `netstandard2.0` target if you require a `netstandard1.x` target.</span></span>

> <span data-ttu-id="7e5f8-125">.NET Standard 2.0 destekleyen tüm platformlar kullanacağı `netstandard2.0` hedef ve avantaj daha eski platformlar hala çalışır ve kullanmaya geri döner ancak daha küçük bir paket grafik kalmamasını `netstandard1.x` hedef.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-125">All platforms supporting .NET Standard 2.0 will use the `netstandard2.0` target and benefit from having a smaller package graph while older platforms will still work and fall back to using the `netstandard1.x` target.</span></span>

<span data-ttu-id="7e5f8-126">**❌ SAĞLAMADIĞI** kitaplığı bir platforma özgü uygulama modelini kullanır. .NET standart bir hedef ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-126">**❌ DO NOT** include a .NET Standard target if the library relies on a platform-specific app model.</span></span>

> <span data-ttu-id="7e5f8-127">Örneğin, bir UWP Denetim Araç Seti kitaplığı yalnızca UWP üzerinde kullanılabilir bir uygulama modeli bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-127">For example, a UWP control toolkit library depends on an app model that is only available on UWP.</span></span> <span data-ttu-id="7e5f8-128">Uygulama modeli özel API'ler .NET Standard sürümünde kullanılabilir olmayacak.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-128">App model specific APIs will not be available in .NET Standard.</span></span>

## <a name="multi-targeting"></a><span data-ttu-id="7e5f8-129">Çoklu sürüm desteği</span><span class="sxs-lookup"><span data-stu-id="7e5f8-129">Multi-targeting</span></span>

<span data-ttu-id="7e5f8-130">Bazen, kitaplıklarından çerçeveye özgü API erişmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-130">Sometimes you need to access framework-specific APIs from your libraries.</span></span> <span data-ttu-id="7e5f8-131">Çoklu fazla projeniz derlenir, sürüm, çerçeveye özgü API'leri çağırmak için en iyi yolu kullanarak [.NET hedef Framework](../frameworks.md) yerine yalnızca bir tane.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-131">The best way to call framework-specific APIs is using multi-targeting, which builds your project for many [.NET target frameworks](../frameworks.md) rather than for just one.</span></span>

<span data-ttu-id="7e5f8-132">Tüketicileriniz, tek tek çerçeveleri için yapı zorunda korumak için .NET standart çıktı artı bir veya daha fazla çerçeveye özgü çıkışları çaba göstermelisiniz.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-132">To shield your consumers from having to build for individual frameworks, you should strive to have a .NET Standard output plus one or more framework-specific outputs.</span></span> <span data-ttu-id="7e5f8-133">Çoklu sürüm desteği ile tüm derlemeler içinde tek bir NuGet paketi olarak paketlenir.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-133">With multi-targeting, all assemblies are packaged inside a single NuGet package.</span></span> <span data-ttu-id="7e5f8-134">Tüketiciler aynı paket ardından başvurabilir ve NuGet uygun uygulama seçer.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-134">Consumers can then reference the same package and NuGet will pick the appropriate implementation.</span></span> <span data-ttu-id="7e5f8-135">Geri dönüş kitaplığı NuGet paketinizi çerçeveye özgü uygulama yeri sunar durumları hariç her yerde kullanılan, .NET Standard kitaplığı işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-135">Your .NET Standard library serves as the fallback library that is used everywhere, except for the cases where your NuGet package offers a framework-specific implementation.</span></span> <span data-ttu-id="7e5f8-136">Multi-targeting'e koşullu derleme kodunuzda kullanın ve çerçeveye özgü API'leri çağırmak sağlar.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-136">Multi-targeting allows you to use conditional compilation in your code and call framework-specific APIs.</span></span>

<span data-ttu-id="7e5f8-137">![NuGet paketi ile birden çok derleme](./media/cross-platform-targeting/nuget-package-multiple-assemblies.png "birden çok derleme ile NuGet paketi")</span><span class="sxs-lookup"><span data-stu-id="7e5f8-137">![NuGet package with multiple assemblies](./media/cross-platform-targeting/nuget-package-multiple-assemblies.png "NuGet package with multiple assemblies")</span></span>

<span data-ttu-id="7e5f8-138">**✔️ DÜŞÜNÜN** .NET uygulamalarının yanı sıra .NET Standard desteği.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-138">**✔️ CONSIDER** targeting .NET implementations in addition to .NET Standard.</span></span>

> <span data-ttu-id="7e5f8-139">.NET uygulamaları hedefleyen .NET Standard dışında olan platforma özel API'leri çağırmak sağlar.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-139">Targeting .NET implementations allows you to call platform-specific APIs that are outside of .NET Standard.</span></span>
>
> <span data-ttu-id="7e5f8-140">Bunu yaptığınızda, .NET Standard desteği bırak değil.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-140">Do not drop support for .NET Standard when you do this.</span></span> <span data-ttu-id="7e5f8-141">Bunun yerine, uygulamadan throw ve API'leri becerisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-141">Instead, throw from the implementation and offer capability APIs.</span></span> <span data-ttu-id="7e5f8-142">Bu şekilde kitaplığınızı her yerde kullanılabilir ve çalışma zamanı açık yukarı özelliklerini destekler.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-142">This way, your library can be used anywhere and supports runtime light-up of features.</span></span>

<span data-ttu-id="7e5f8-143">**❌ KAÇININ** çoklu hedefleme-.NET Standard ile tüm hedefler için aynı kaynak kodunuzu ise kullanarak.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-143">**❌ AVOID** using multi-targeting with .NET Standard if your source code is the same for all targets.</span></span>

> <span data-ttu-id="7e5f8-144">.NET Standard derleme NuGet tarafından otomatik olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-144">The .NET Standard assembly will automatically be used by NuGet.</span></span> <span data-ttu-id="7e5f8-145">Tek tek .NET uygulamalarını hedefleme artırır `*.nupkg` hiçbir avantajı olmadan boyutu.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-145">Targeting individual .NET implementations increases the `*.nupkg` size for no benefit.</span></span>

<span data-ttu-id="7e5f8-146">**✔️ DÜŞÜNÜN** ekleme için hedef `net461` teklifi ne zaman bir `netstandard2.0` hedef.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-146">**✔️ CONSIDER** adding a target for `net461` when you're offering a `netstandard2.0` target.</span></span> 

> <span data-ttu-id="7e5f8-147">.NET Standard 2.0, .NET Framework kullanarak .NET Framework 4.7.2 ele alınan bazı sorunlar vardır.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-147">Using .NET Standard 2.0 from .NET Framework has some issues that were addressed in .NET Framework 4.7.2.</span></span> <span data-ttu-id="7e5f8-148">.NET Framework 4.6.1 - .NET Framework 4.6.1 için yerleşik bir ikili sunarak bunları 4.7.1 hala açıktır geliştiriciler için kullanım deneyimi sunmasını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-148">You can improve the experience for developers that are still on .NET Framework 4.6.1 - 4.7.1 by offering them a binary that is built for .NET Framework 4.6.1.</span></span>

<span data-ttu-id="7e5f8-149">**✔️ YAPMAK** bir NuGet paketi kullanarak kitaplığınızda dağıtın.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-149">**✔️ DO** distribute your library using a NuGet package.</span></span>

> <span data-ttu-id="7e5f8-150">NuGet, geliştirici için en iyi hedef seçin ve bunları uygun uygulama almak zorunda korunamadı.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-150">NuGet will select the best target for the developer and shield them having to pick the appropriate implementation.</span></span>

<span data-ttu-id="7e5f8-151">**✔️ YAPMAK** kullanan bir proje dosyasının `TargetFrameworks` özelliği çoklu sürüm desteği olduğunda.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-151">**✔️ DO** use a project file's `TargetFrameworks` property when multi-targeting.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <!-- This project will output netstandard2.0 and net461 assemblies -->
    <TargetFrameworks>netstandard2.0;net461</TargetFrameworks>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="7e5f8-152">**✔️ DÜŞÜNÜN** kullanarak [MSBuild.Sdk.Extras](https://github.com/onovotny/MSBuildSdkExtras) çoklu sürüm desteği olduğunda UWP ve Xamarin gibi proje dosyanız büyük ölçüde basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-152">**✔️ CONSIDER** using [MSBuild.Sdk.Extras](https://github.com/onovotny/MSBuildSdkExtras) when multi-targeting for UWP and Xamarin as it greatly simplifies your project file.</span></span>

## <a name="older-targets"></a><span data-ttu-id="7e5f8-153">Eski hedefleri</span><span class="sxs-lookup"><span data-stu-id="7e5f8-153">Older targets</span></span>

<span data-ttu-id="7e5f8-154">.NET, Internet Explorer'ın artık yaygın olarak kullanılan platformları yanı sıra destek dışında uzun hedefleme .NET Framework sürümlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-154">.NET supports targeting versions of the .NET Framework that are long out of support as well as platforms that are no longer commonly used.</span></span> <span data-ttu-id="7e5f8-155">Varken değer olabildiğince fazla sayıda hedefe API'leri eksik etrafında çalışmak zorunda ekleyebilirsiniz kitaplığı iş üzerinde ek yükünü önemli yaparak içinde.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-155">While there's value in making your library work on as many targets as possible, having to work around missing APIs can add significant overhead.</span></span> <span data-ttu-id="7e5f8-156">Çerçeve hedefleme değer bunların erişim ve sınırlamaları dikkate alarak kalmadığında belirli inanıyoruz.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-156">We believe certain frameworks are no longer worth targeting, considering their reach and limitations.</span></span>

<span data-ttu-id="7e5f8-157">**❌ SAĞLAMADIĞI** taşınabilir sınıf kitaplığı (PCL) hedef içerir.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-157">**❌ DO NOT** include a Portable Class Library (PCL) target.</span></span> <span data-ttu-id="7e5f8-158">Örneğin: `portable-net45+win8+wpa81+wp8`</span><span class="sxs-lookup"><span data-stu-id="7e5f8-158">For example, `portable-net45+win8+wpa81+wp8`.</span></span>

> <span data-ttu-id="7e5f8-159">.NET standard platformlar arası .NET kitaplıkları destekleyen modern yoludur ve PCLs değiştirir.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-159">.NET Standard is the modern way to support cross-platform .NET libraries and replaces PCLs.</span></span>

<span data-ttu-id="7e5f8-160">**❌ SAĞLAMADIĞI** artık desteklenmeyen bir .NET platformları için hedefler içerir.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-160">**❌ DO NOT** include targets for .NET platforms that are no longer supported.</span></span> <span data-ttu-id="7e5f8-161">Örneğin, `SL4`, `WP`.</span><span class="sxs-lookup"><span data-stu-id="7e5f8-161">For example, `SL4`, `WP`.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="7e5f8-162">[Önceki](./get-started.md)
[İleri](./strong-naming.md)</span><span class="sxs-lookup"><span data-stu-id="7e5f8-162">[Previous](./get-started.md)
[Next](./strong-naming.md)</span></span>
