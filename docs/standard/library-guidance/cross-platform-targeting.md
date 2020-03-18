---
title: .NET kitaplıkları için çapraz platform hedeflemesi
description: Platform arası .NET kitaplıkları oluşturmak için en iyi uygulama önerileri.
ms.date: 08/12/2019
ms.openlocfilehash: 61adff3759984554bb83531b4f9d8a49e29c929c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "76731452"
---
# <a name="cross-platform-targeting"></a><span data-ttu-id="b4f9a-103">Platformlar arası hedefleme</span><span class="sxs-lookup"><span data-stu-id="b4f9a-103">Cross-platform targeting</span></span>

<span data-ttu-id="b4f9a-104">Modern .NET birden çok işletim sistemi ve cihazı destekler.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-104">Modern .NET supports multiple operating systems and devices.</span></span> <span data-ttu-id="b4f9a-105">.NET açık kaynak kitaplıklarının, ister Azure'da barındırılan bir ASP.NET web sitesi ister Unity'de bir .NET oyunu oluşturmaları olsun, mümkün olduğunca çok geliştiriciyi desteklemesi önemlidir.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-105">It's important for .NET open-source libraries to support as many developers as possible, whether they're building an ASP.NET website hosted in Azure, or a .NET game in Unity.</span></span>

## <a name="net-standard"></a><span data-ttu-id="b4f9a-106">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="b4f9a-106">.NET Standard</span></span>

<span data-ttu-id="b4f9a-107">.NET Standard, bir .NET kitaplığına çapraz platform desteği eklemenin en iyi yoludur.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-107">.NET Standard is the best way to add cross-platform support to a .NET library.</span></span> <span data-ttu-id="b4f9a-108">[.NET Standardı,](../net-standard.md) tüm .NET uygulamalarında bulunan .NET API'lerinin bir belirtimidir.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-108">[.NET Standard](../net-standard.md) is a specification of .NET APIs that are available on all .NET implementations.</span></span> <span data-ttu-id="b4f9a-109">Hedefleme .NET Standard, .NET Standard'ın belirli bir sürümünde bulunan API'leri kullanmak üzere kısıtlanmış kitaplıklar oluşturmanıza olanak tanır, bu da .NET Standard'ın bu sürümünü uygulayan tüm platformlar tarafından kullanılabilir olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-109">Targeting .NET Standard lets you produce libraries that are constrained to use APIs that are in a given version of .NET Standard, which means it's usable by all platforms that implement that version of the .NET Standard.</span></span>

<span data-ttu-id="b4f9a-110">![.NET Standard](./media/cross-platform-targeting/platforms-netstandard.png ".NET Standard")</span><span class="sxs-lookup"><span data-stu-id="b4f9a-110">![.NET Standard](./media/cross-platform-targeting/platforms-netstandard.png ".NET Standard")</span></span>

<span data-ttu-id="b4f9a-111">.NET Standard'ı hedeflemek ve projenizi başarıyla derlemek, kitaplığın tüm platformlarda başarılı bir şekilde çalışacağına garanti etmez:</span><span class="sxs-lookup"><span data-stu-id="b4f9a-111">Targeting .NET Standard, and successfully compiling your project, doesn't guarantee the library will run successfully on all platforms:</span></span>

1. <span data-ttu-id="b4f9a-112">Platforma özel API'ler diğer platformlarda başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-112">Platform-specific APIs will fail on other platforms.</span></span> <span data-ttu-id="b4f9a-113">Örneğin, <xref:Microsoft.Win32.Registry?displayProperty=nameWithType> Windows'ta başarılı <xref:System.PlatformNotSupportedException> olacak ve başka bir işletim sistemi üzerinde kullanıldığında atmak.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-113">For example, <xref:Microsoft.Win32.Registry?displayProperty=nameWithType> will succeed on Windows and throw <xref:System.PlatformNotSupportedException> when used on any other OS.</span></span>
2. <span data-ttu-id="b4f9a-114">API'ler farklı davranabilir.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-114">APIs can behave differently.</span></span> <span data-ttu-id="b4f9a-115">Örneğin, bir uygulama iOS veya UWP'de zamanından önce derleme kullandığında yansıma API'leri farklı performans özelliklerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-115">For example, reflection APIs have different performance characteristics when an application uses ahead-of-time compilation on iOS or UWP.</span></span>

> [!TIP]
> <span data-ttu-id="b4f9a-116">.NET ekibi, olası sorunları keşfetmenize yardımcı olacak [bir Roslyn çözümleyicisi sunar.](../analyzers/api-analyzer.md)</span><span class="sxs-lookup"><span data-stu-id="b4f9a-116">The .NET team [offers a Roslyn analyzer](../analyzers/api-analyzer.md) to help you discover possible issues.</span></span>

<span data-ttu-id="b4f9a-117">✔️ DO bir `netstandard2.0` hedef dahil ile başlar.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-117">✔️ DO start with including a `netstandard2.0` target.</span></span>

> <span data-ttu-id="b4f9a-118">Genel amaçlı kitaplıkların çoğu .NET Standart 2.0 dışında API'ler gerekmez.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-118">Most general-purpose libraries should not need APIs outside of .NET Standard 2.0.</span></span> <span data-ttu-id="b4f9a-119">.NET Standart 2.0 tüm modern platformlar tarafından desteklenir ve tek bir hedefle birden fazla platformu desteklemek için önerilen yoldur.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-119">.NET Standard 2.0 is supported by all modern platforms and is the recommended way to support multiple platforms with one target.</span></span>

<span data-ttu-id="b4f9a-120">❌Bir `netstandard1.x` hedef dahil kaçının.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-120">❌ AVOID including a `netstandard1.x` target.</span></span>

> <span data-ttu-id="b4f9a-121">.NET Standart 1.x, büyük bir paket bağımlılık grafiği oluşturan ve geliştiricilerin oluştururken çok sayıda paket indirmesi ile sonuçlanan nuget paketlerinin tanecikli kümesi olarak dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-121">.NET Standard 1.x is distributed as a granular set of NuGet packages, which creates a large package dependency graph and results in developers downloading a lot of packages when building.</span></span> <span data-ttu-id="b4f9a-122">.NET Framework 4.6.1, UWP ve Xamarin gibi modern .NET platformları, tüm destek .NET Standart 2.0.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-122">Modern .NET platforms, including .NET Framework 4.6.1, UWP and Xamarin, all support .NET Standard 2.0.</span></span> <span data-ttu-id="b4f9a-123">Sadece daha eski bir platformu hedeflemeniz gerekiyorsa .NET Standart 1.x'i hedeflemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-123">You should only target .NET Standard 1.x if you specifically need to target an older platform.</span></span>

<span data-ttu-id="b4f9a-124">✔️ bir `netstandard2.0` `netstandard1.x` hedef gerekiyorsa bir hedef içerir.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-124">✔️ DO include a `netstandard2.0` target if you require a `netstandard1.x` target.</span></span>

> <span data-ttu-id="b4f9a-125">.NET Standard 2.0'ı destekleyen `netstandard2.0` tüm platformlar hedefi kullanır ve daha küçük bir paket grafiğine `netstandard1.x` sahip olmanın avantajını kullanırken, eski platformlar çalışmaya devam edecek ve hedefi kullanmaya geri dönecektir.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-125">All platforms supporting .NET Standard 2.0 will use the `netstandard2.0` target and benefit from having a smaller package graph while older platforms will still work and fall back to using the `netstandard1.x` target.</span></span>

<span data-ttu-id="b4f9a-126">❌Kitaplık platforma özgü bir uygulama modeline dayanıyorsa bir .NET Standart hedefi eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-126">❌ DO NOT include a .NET Standard target if the library relies on a platform-specific app model.</span></span>

> <span data-ttu-id="b4f9a-127">Örneğin, UWP denetim araç kiti kitaplığı yalnızca UWP'de kullanılabilen bir uygulama modeline bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-127">For example, a UWP control toolkit library depends on an app model that is only available on UWP.</span></span> <span data-ttu-id="b4f9a-128">Uygulama modeline özgü API'ler .NET Standard'da kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-128">App model specific APIs will not be available in .NET Standard.</span></span>

## <a name="multi-targeting"></a><span data-ttu-id="b4f9a-129">Çok hedefleme</span><span class="sxs-lookup"><span data-stu-id="b4f9a-129">Multi-targeting</span></span>

<span data-ttu-id="b4f9a-130">Bazen kitaplıklarınızdan çerçeveye özgü API'lere erişmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-130">Sometimes you need to access framework-specific APIs from your libraries.</span></span> <span data-ttu-id="b4f9a-131">Çerçeveye özgü API'leri aramanın en iyi yolu, projenizi tek bir hedef için değil, birçok [.NET hedef çerçevesi](../frameworks.md) için oluşturan çok hedeflemeli kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-131">The best way to call framework-specific APIs is using multi-targeting, which builds your project for many [.NET target frameworks](../frameworks.md) rather than for just one.</span></span>

<span data-ttu-id="b4f9a-132">Tüketicilerinizi bireysel çerçeveler için oluşturmak zorunda kalmaktan korumak için ,NET Standart çıktısına ve bir veya daha fazla çerçeveye özgü çıktıya sahip olmak için çaba göstermelisiniz.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-132">To shield your consumers from having to build for individual frameworks, you should strive to have a .NET Standard output plus one or more framework-specific outputs.</span></span> <span data-ttu-id="b4f9a-133">Çoklu hedefleme ile tüm montajlar tek bir NuGet paketinin içinde paketlenir.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-133">With multi-targeting, all assemblies are packaged inside a single NuGet package.</span></span> <span data-ttu-id="b4f9a-134">Tüketiciler daha sonra aynı pakete başvuruyapabilir ve NuGet uygun uygulamayı seçecektir.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-134">Consumers can then reference the same package and NuGet will pick the appropriate implementation.</span></span> <span data-ttu-id="b4f9a-135">.NET Standart kitaplığınız, NuGet paketinizin çerçeveye özgü bir uygulama sunduğu durumlar dışında her yerde kullanılan geri dönüş kitaplığı olarak hizmet vermektedir.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-135">Your .NET Standard library serves as the fallback library that is used everywhere, except for the cases where your NuGet package offers a framework-specific implementation.</span></span> <span data-ttu-id="b4f9a-136">Çoklu hedefleme, kodunuzda koşullu derlemeyi kullanmanıza ve çerçeveye özgü API'leri aramanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-136">Multi-targeting allows you to use conditional compilation in your code and call framework-specific APIs.</span></span>

<span data-ttu-id="b4f9a-137">![Birden fazla derlemeli NuGet paketi](./media/cross-platform-targeting/nuget-package-multiple-assemblies.png "Birden fazla derlemeli NuGet paketi")</span><span class="sxs-lookup"><span data-stu-id="b4f9a-137">![NuGet package with multiple assemblies](./media/cross-platform-targeting/nuget-package-multiple-assemblies.png "NuGet package with multiple assemblies")</span></span>

<span data-ttu-id="b4f9a-138">✔️ .NET Standardına ek olarak .NET uygulamalarını hedeflemeyi göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-138">✔️ CONSIDER targeting .NET implementations in addition to .NET Standard.</span></span>

> <span data-ttu-id="b4f9a-139">.NET uygulamalarını hedeflemek, .NET Standardı'nın dışında olan platforma özgü API'leri aramanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-139">Targeting .NET implementations allows you to call platform-specific APIs that are outside of .NET Standard.</span></span>
>
> <span data-ttu-id="b4f9a-140">Bunu yaparken .NET Standard desteğini düşürmeyin.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-140">Do not drop support for .NET Standard when you do this.</span></span> <span data-ttu-id="b4f9a-141">Bunun yerine, uygulamadan atın ve yetenek API'leri sunun.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-141">Instead, throw from the implementation and offer capability APIs.</span></span> <span data-ttu-id="b4f9a-142">Bu şekilde, kitaplığınız her yerde kullanılabilir ve özelliklerin çalışma zamanı ışıklarını destekler.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-142">This way, your library can be used anywhere and supports runtime light-up of features.</span></span>

```csharp
public static class GpsLocation
{
    // This project uses multi-targeting to expose device-specific APIs to .NET Standard.
    public static async Task<(double latitude, double longitude)> GetCoordinatesAsync()
    {
#if NET461
        return CallDotNetFramworkApi();
#elif WINDOWS_UWP
        return CallUwpApi();
#else
        throw new PlatformNotSupportedException();
#endif
    }

    // Allows callers to check without having to catch PlatformNotSupportedException
    // or replicating the OS check.
    public static bool IsSupported
    {
        get
        {
#if NET461 || WINDOWS_UWP
            return true;
#else
            return false;
#endif
        }
    }
}
```

<span data-ttu-id="b4f9a-143">❌Kaynak kodunuz tüm hedefler için aynıysa, çoklu hedeflemenin yanı sıra .NET Standard'ı hedeflemekten kaçının.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-143">❌ AVOID multi-targeting as well as targeting .NET Standard, if your source code is the same for all targets.</span></span>

> <span data-ttu-id="b4f9a-144">.NET Standart derlemesi NuGet tarafından otomatik olarak kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-144">The .NET Standard assembly will automatically be used by NuGet.</span></span> <span data-ttu-id="b4f9a-145">Bireysel .NET uygulamalarını `*.nupkg` hedeflemek, boyutu hiçbir fayda sağlamadan artırır.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-145">Targeting individual .NET implementations increases the `*.nupkg` size for no benefit.</span></span>

<span data-ttu-id="b4f9a-146">✔️ Bir `netstandard2.0` hedef `net461` sunarken bir hedef eklemeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-146">✔️ CONSIDER adding a target for `net461` when you're offering a `netstandard2.0` target.</span></span>

> <span data-ttu-id="b4f9a-147">.NET Framework'den .NET Standard 2.0'ın kullanılmasında .NET Framework 4.7.2'de ele alınan bazı sorunlar vardır.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-147">Using .NET Standard 2.0 from .NET Framework has some issues that were addressed in .NET Framework 4.7.2.</span></span> <span data-ttu-id="b4f9a-148">.NET Framework 4.6.1 - 4.7.1'de hala olan geliştiricilerin deneyimini ,NET Framework 4.6.1 için oluşturulmuş bir ikili teklif ederek geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-148">You can improve the experience for developers that are still on .NET Framework 4.6.1 - 4.7.1 by offering them a binary that is built for .NET Framework 4.6.1.</span></span>

<span data-ttu-id="b4f9a-149">✔️ DO kitaplığınızı bir NuGet paketi kullanarak dağıtın.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-149">✔️ DO distribute your library using a NuGet package.</span></span>

> <span data-ttu-id="b4f9a-150">NuGet geliştirici için en iyi hedefi seçecek ve onları uygun uygulamayı seçmek zorunda kalkan.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-150">NuGet will select the best target for the developer and shield them having to pick the appropriate implementation.</span></span>

<span data-ttu-id="b4f9a-151">✔️ ÇOKLU hedefleme yaparken `TargetFrameworks` proje dosyasının özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-151">✔️ DO use a project file's `TargetFrameworks` property when multi-targeting.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <!-- This project will output netstandard2.0 and net461 assemblies -->
    <TargetFrameworks>netstandard2.0;net461</TargetFrameworks>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="b4f9a-152">✔️, proje dosyanızı büyük ölçüde basitleştiren UWP ve Xamarin için çoklu hedefleme yaparken [MSBuild.Sdk.Extras'ı](https://github.com/onovotny/MSBuildSdkExtras) kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-152">✔️ CONSIDER using [MSBuild.Sdk.Extras](https://github.com/onovotny/MSBuildSdkExtras) when multi-targeting for UWP and Xamarin as it greatly simplifies your project file.</span></span>

## <a name="older-targets"></a><span data-ttu-id="b4f9a-153">Eski hedefler</span><span class="sxs-lookup"><span data-stu-id="b4f9a-153">Older targets</span></span>

<span data-ttu-id="b4f9a-154">.NET, .NET Framework'ün uzun süredir desteksiz olan hedefleme sürümlerini ve artık yaygın olarak kullanılmayan platformları destekler.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-154">.NET supports targeting versions of the .NET Framework that are long out of support as well as platforms that are no longer commonly used.</span></span> <span data-ttu-id="b4f9a-155">Kitaplığınızın mümkün olduğunca çok hedef üzerinde çalışmasını sağlamanın bir değeri olsa da, eksik API'ler üzerinde çalışmak zorunda kalmak önemli ek yükü ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-155">While there's value in making your library work on as many targets as possible, having to work around missing APIs can add significant overhead.</span></span> <span data-ttu-id="b4f9a-156">Erişim leri ve sınırlamaları göz önünde bulundurularak, bazı çerçevelerin artık hedef almaya değer olmadığına inanıyoruz.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-156">We believe certain frameworks are no longer worth targeting, considering their reach and limitations.</span></span>

<span data-ttu-id="b4f9a-157">❌Taşınabilir Sınıf Kitaplığı (PCL) hedefini EKLEMEYİn.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-157">❌ DO NOT include a Portable Class Library (PCL) target.</span></span> <span data-ttu-id="b4f9a-158">Örneğin, `portable-net45+win8+wpa81+wp8`.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-158">For example, `portable-net45+win8+wpa81+wp8`.</span></span>

> <span data-ttu-id="b4f9a-159">.NET Standard, çapraz platform .NET kitaplıklarını desteklemenin ve PCL'lerin yerini alan modern bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-159">.NET Standard is the modern way to support cross-platform .NET libraries and replaces PCLs.</span></span>

<span data-ttu-id="b4f9a-160">❌Artık desteklenmeyen .NET platformları için hedefler EKLEMEYIN.</span><span class="sxs-lookup"><span data-stu-id="b4f9a-160">❌ DO NOT include targets for .NET platforms that are no longer supported.</span></span> <span data-ttu-id="b4f9a-161">Örneğin, `SL4`. `WP`</span><span class="sxs-lookup"><span data-stu-id="b4f9a-161">For example, `SL4`, `WP`.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b4f9a-162">[Önceki](get-started.md)
>[Sonraki](strong-naming.md)</span><span class="sxs-lookup"><span data-stu-id="b4f9a-162">[Previous](get-started.md)
[Next](strong-naming.md)</span></span>
