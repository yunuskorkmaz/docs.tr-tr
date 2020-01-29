---
title: .NET kitaplıkları için platformlar arası hedefleme
description: Platformlar arası .NET kitaplıkları oluşturmaya yönelik en iyi yöntem önerileri.
ms.date: 08/12/2019
ms.openlocfilehash: 61adff3759984554bb83531b4f9d8a49e29c929c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731452"
---
# <a name="cross-platform-targeting"></a><span data-ttu-id="de1a5-103">Platformlar arası hedefleme</span><span class="sxs-lookup"><span data-stu-id="de1a5-103">Cross-platform targeting</span></span>

<span data-ttu-id="de1a5-104">Modern .NET birden çok işletim sistemini ve cihazı destekler.</span><span class="sxs-lookup"><span data-stu-id="de1a5-104">Modern .NET supports multiple operating systems and devices.</span></span> <span data-ttu-id="de1a5-105">.NET açık kaynaklı kitaplıkların, Azure 'da barındırılan bir ASP.NET Web sitesi mi yoksa Unity 'de bir .NET oyunu mi sundukları gibi çok sayıda geliştirici desteklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="de1a5-105">It's important for .NET open-source libraries to support as many developers as possible, whether they're building an ASP.NET website hosted in Azure, or a .NET game in Unity.</span></span>

## <a name="net-standard"></a><span data-ttu-id="de1a5-106">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="de1a5-106">.NET Standard</span></span>

<span data-ttu-id="de1a5-107">.NET Standard, bir .NET kitaplığına platformlar arası destek eklemenin en iyi yoludur.</span><span class="sxs-lookup"><span data-stu-id="de1a5-107">.NET Standard is the best way to add cross-platform support to a .NET library.</span></span> <span data-ttu-id="de1a5-108">[.NET Standard](../net-standard.md) , tüm .NET uygulamalarında bulunan .NET API 'lerinin bir belirtimidir.</span><span class="sxs-lookup"><span data-stu-id="de1a5-108">[.NET Standard](../net-standard.md) is a specification of .NET APIs that are available on all .NET implementations.</span></span> <span data-ttu-id="de1a5-109">.NET Standard hedefleme, belirli bir .NET Standard sürümünde olan API 'Leri kullanmak için kısıtlanmış kitaplıklar oluşturmanızı sağlar. Bu, .NET Standard bu sürümü uygulayan tüm platformlar tarafından kullanılabilir olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="de1a5-109">Targeting .NET Standard lets you produce libraries that are constrained to use APIs that are in a given version of .NET Standard, which means it's usable by all platforms that implement that version of the .NET Standard.</span></span>

<span data-ttu-id="de1a5-110">![.NET Standard](./media/cross-platform-targeting/platforms-netstandard.png ".NET Standard")</span><span class="sxs-lookup"><span data-stu-id="de1a5-110">![.NET Standard](./media/cross-platform-targeting/platforms-netstandard.png ".NET Standard")</span></span>

<span data-ttu-id="de1a5-111">.NET Standard ve projenizi başarıyla derleyerek, kitaplığın tüm platformlarda başarıyla çalışacağını garanti etmez:</span><span class="sxs-lookup"><span data-stu-id="de1a5-111">Targeting .NET Standard, and successfully compiling your project, doesn't guarantee the library will run successfully on all platforms:</span></span>

1. <span data-ttu-id="de1a5-112">Platforma özgü API 'Ler diğer platformlarda başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="de1a5-112">Platform-specific APIs will fail on other platforms.</span></span> <span data-ttu-id="de1a5-113">Örneğin, <xref:Microsoft.Win32.Registry?displayProperty=nameWithType> Windows üzerinde başarılı olur ve başka herhangi bir IŞLETIM sisteminde kullanıldığında <xref:System.PlatformNotSupportedException> oluşturur.</span><span class="sxs-lookup"><span data-stu-id="de1a5-113">For example, <xref:Microsoft.Win32.Registry?displayProperty=nameWithType> will succeed on Windows and throw <xref:System.PlatformNotSupportedException> when used on any other OS.</span></span>
2. <span data-ttu-id="de1a5-114">API 'Ler farklı davranabilirler.</span><span class="sxs-lookup"><span data-stu-id="de1a5-114">APIs can behave differently.</span></span> <span data-ttu-id="de1a5-115">Örneğin, bir uygulama iOS veya UWP üzerinde güncel derleme kullandığında, yansıma API 'Leri farklı performans özelliklerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="de1a5-115">For example, reflection APIs have different performance characteristics when an application uses ahead-of-time compilation on iOS or UWP.</span></span>

> [!TIP]
> <span data-ttu-id="de1a5-116">.NET ekibi, olası sorunları bulmanıza yardımcı olmak için [bir Roslyn Çözümleyicisi sunmaktadır](../analyzers/api-analyzer.md) .</span><span class="sxs-lookup"><span data-stu-id="de1a5-116">The .NET team [offers a Roslyn analyzer](../analyzers/api-analyzer.md) to help you discover possible issues.</span></span>

<span data-ttu-id="de1a5-117">`netstandard2.0` hedef dahil ✔️.</span><span class="sxs-lookup"><span data-stu-id="de1a5-117">✔️ DO start with including a `netstandard2.0` target.</span></span>

> <span data-ttu-id="de1a5-118">Genel amaçlı kitaplıkların çoğu .NET Standard 2,0 dışında API 'Lere ihtiyaç mamalıdır.</span><span class="sxs-lookup"><span data-stu-id="de1a5-118">Most general-purpose libraries should not need APIs outside of .NET Standard 2.0.</span></span> <span data-ttu-id="de1a5-119">.NET Standard 2,0 tüm modern platformlar tarafından desteklenir ve tek bir hedefle birden çok platformu desteklemek için önerilen yoldur.</span><span class="sxs-lookup"><span data-stu-id="de1a5-119">.NET Standard 2.0 is supported by all modern platforms and is the recommended way to support multiple platforms with one target.</span></span>

<span data-ttu-id="de1a5-120">❌ `netstandard1.x` hedefini kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="de1a5-120">❌ AVOID including a `netstandard1.x` target.</span></span>

> <span data-ttu-id="de1a5-121">.NET Standard 1. x, büyük bir paket bağımlılığı grafiği oluşturan ve geliştiricilerin derlerken çok sayıda paket indirmelerine neden olan ayrıntılı bir NuGet paketleri kümesi olarak dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="de1a5-121">.NET Standard 1.x is distributed as a granular set of NuGet packages, which creates a large package dependency graph and results in developers downloading a lot of packages when building.</span></span> <span data-ttu-id="de1a5-122">.NET Framework 4.6.1, UWP ve Xamarin gibi modern .NET platformları, tüm destek .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="de1a5-122">Modern .NET platforms, including .NET Framework 4.6.1, UWP and Xamarin, all support .NET Standard 2.0.</span></span> <span data-ttu-id="de1a5-123">Yalnızca daha eski bir platformu hedeflemek istiyorsanız .NET Standard 1. x hedefini hedefleyin.</span><span class="sxs-lookup"><span data-stu-id="de1a5-123">You should only target .NET Standard 1.x if you specifically need to target an older platform.</span></span>

<span data-ttu-id="de1a5-124">bir `netstandard1.x` hedefi gerekiyorsa ✔️ `netstandard2.0` hedefi vardır.</span><span class="sxs-lookup"><span data-stu-id="de1a5-124">✔️ DO include a `netstandard2.0` target if you require a `netstandard1.x` target.</span></span>

> <span data-ttu-id="de1a5-125">.NET Standard 2,0 destekleyen tüm platformlar `netstandard2.0` hedefini kullanır ve daha eski platformlar çalışmaya devam eder ve `netstandard1.x` hedefini kullanmaya geri dönecektir.</span><span class="sxs-lookup"><span data-stu-id="de1a5-125">All platforms supporting .NET Standard 2.0 will use the `netstandard2.0` target and benefit from having a smaller package graph while older platforms will still work and fall back to using the `netstandard1.x` target.</span></span>

<span data-ttu-id="de1a5-126">❌, kitaplık platforma özgü bir uygulama modelini kullanıyorsa .NET Standard hedefini içermez.</span><span class="sxs-lookup"><span data-stu-id="de1a5-126">❌ DO NOT include a .NET Standard target if the library relies on a platform-specific app model.</span></span>

> <span data-ttu-id="de1a5-127">Örneğin, UWP Denetim araç seti kitaplığı, yalnızca UWP üzerinde kullanılabilen bir uygulama modeline bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="de1a5-127">For example, a UWP control toolkit library depends on an app model that is only available on UWP.</span></span> <span data-ttu-id="de1a5-128">Uygulama modeline özgü API 'Ler .NET Standard kullanılabilir olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="de1a5-128">App model specific APIs will not be available in .NET Standard.</span></span>

## <a name="multi-targeting"></a><span data-ttu-id="de1a5-129">Çoklu hedefleme</span><span class="sxs-lookup"><span data-stu-id="de1a5-129">Multi-targeting</span></span>

<span data-ttu-id="de1a5-130">Bazen kitaplıklarınızdan çerçeveye özel API 'Lere erişmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="de1a5-130">Sometimes you need to access framework-specific APIs from your libraries.</span></span> <span data-ttu-id="de1a5-131">Çerçeveye özgü API 'Leri çağırmak için en iyi yol, projenizi yalnızca bir yerine birçok [.net hedef](../frameworks.md) çerçevesi için oluşturan Çoklu hedefleme kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="de1a5-131">The best way to call framework-specific APIs is using multi-targeting, which builds your project for many [.NET target frameworks](../frameworks.md) rather than for just one.</span></span>

<span data-ttu-id="de1a5-132">Tüketicilerinizin tek tek çerçeveler için derleme yapmasına gerek kalmadan, bir .NET Standard çıkışına ve bir veya daha fazla çerçeveye özgü çıktıya sahip olmaya çalışmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="de1a5-132">To shield your consumers from having to build for individual frameworks, you should strive to have a .NET Standard output plus one or more framework-specific outputs.</span></span> <span data-ttu-id="de1a5-133">Çoklu hedefleme ile, tüm derlemeler tek bir NuGet paketi içinde paketlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="de1a5-133">With multi-targeting, all assemblies are packaged inside a single NuGet package.</span></span> <span data-ttu-id="de1a5-134">Daha sonra tüketiciler aynı pakete başvurabilir ve NuGet uygun uygulamayı seçer.</span><span class="sxs-lookup"><span data-stu-id="de1a5-134">Consumers can then reference the same package and NuGet will pick the appropriate implementation.</span></span> <span data-ttu-id="de1a5-135">.NET Standard kitaplığınız, NuGet paketinizin çerçeveye özgü bir uygulama sunduğu durumlar dışında her yerde kullanılan geri dönüş Kitaplığı işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="de1a5-135">Your .NET Standard library serves as the fallback library that is used everywhere, except for the cases where your NuGet package offers a framework-specific implementation.</span></span> <span data-ttu-id="de1a5-136">Çoklu hedefleme, kodunuzda koşullu derleme kullanmanıza ve çerçeveye özgü API 'Leri çağırayapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="de1a5-136">Multi-targeting allows you to use conditional compilation in your code and call framework-specific APIs.</span></span>

<span data-ttu-id="de1a5-137">![Birden çok bütünleştirilmiş kod içeren NuGet paketi](./media/cross-platform-targeting/nuget-package-multiple-assemblies.png "Birden çok bütünleştirilmiş kod içeren NuGet paketi")</span><span class="sxs-lookup"><span data-stu-id="de1a5-137">![NuGet package with multiple assemblies](./media/cross-platform-targeting/nuget-package-multiple-assemblies.png "NuGet package with multiple assemblies")</span></span>

<span data-ttu-id="de1a5-138">✔️ .NET Standard ek olarak .NET uygulamalarını hedeflemeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="de1a5-138">✔️ CONSIDER targeting .NET implementations in addition to .NET Standard.</span></span>

> <span data-ttu-id="de1a5-139">.NET uygulamalarını hedefleme, .NET Standard dışında olan platforma özel API 'Leri aramanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="de1a5-139">Targeting .NET implementations allows you to call platform-specific APIs that are outside of .NET Standard.</span></span>
>
> <span data-ttu-id="de1a5-140">Bunu yaparken .NET Standard desteğini kaldırmayın.</span><span class="sxs-lookup"><span data-stu-id="de1a5-140">Do not drop support for .NET Standard when you do this.</span></span> <span data-ttu-id="de1a5-141">Bunun yerine, uygulama ve teklif yeteneği API 'Lerini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="de1a5-141">Instead, throw from the implementation and offer capability APIs.</span></span> <span data-ttu-id="de1a5-142">Bu şekilde, kitaplığınız her yerde kullanılabilir ve özelliklerin çalışma zamanı ışığını destekler.</span><span class="sxs-lookup"><span data-stu-id="de1a5-142">This way, your library can be used anywhere and supports runtime light-up of features.</span></span>

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

<span data-ttu-id="de1a5-143">kaynak kodunuz tüm hedefler için aynıysa, .NET Standard ❌ çoklu hedeflemeyi kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="de1a5-143">❌ AVOID multi-targeting as well as targeting .NET Standard, if your source code is the same for all targets.</span></span>

> <span data-ttu-id="de1a5-144">.NET Standard derlemesi NuGet tarafından otomatik olarak kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="de1a5-144">The .NET Standard assembly will automatically be used by NuGet.</span></span> <span data-ttu-id="de1a5-145">Bağımsız .NET uygulamalarının hedeflenmesi, `*.nupkg` boyutunu avantajsız olarak artırır.</span><span class="sxs-lookup"><span data-stu-id="de1a5-145">Targeting individual .NET implementations increases the `*.nupkg` size for no benefit.</span></span>

<span data-ttu-id="de1a5-146">✔️ bir `netstandard2.0` hedefi sunarken `net461` için bir hedef eklemeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="de1a5-146">✔️ CONSIDER adding a target for `net461` when you're offering a `netstandard2.0` target.</span></span>

> <span data-ttu-id="de1a5-147">.NET Framework .NET Standard 2,0 ' in kullanılması .NET Framework 4.7.2 giderilen bazı sorunları içerir.</span><span class="sxs-lookup"><span data-stu-id="de1a5-147">Using .NET Standard 2.0 from .NET Framework has some issues that were addressed in .NET Framework 4.7.2.</span></span> <span data-ttu-id="de1a5-148">Hala .NET Framework 4.6.1-4.7.1 ' de bulunan geliştiriciler için .NET Framework 4.6.1 için oluşturulmuş bir ikili sunarak deneyimi geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="de1a5-148">You can improve the experience for developers that are still on .NET Framework 4.6.1 - 4.7.1 by offering them a binary that is built for .NET Framework 4.6.1.</span></span>

<span data-ttu-id="de1a5-149">✔️, bir NuGet paketi kullanarak kitaplığınızı dağıtır.</span><span class="sxs-lookup"><span data-stu-id="de1a5-149">✔️ DO distribute your library using a NuGet package.</span></span>

> <span data-ttu-id="de1a5-150">NuGet, geliştirici için en iyi hedefi seçer ve uygun uygulamayı seçmek zorunda kalmalarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="de1a5-150">NuGet will select the best target for the developer and shield them having to pick the appropriate implementation.</span></span>

<span data-ttu-id="de1a5-151">✔️, Çoklu hedefleme bir proje dosyasının `TargetFrameworks` özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="de1a5-151">✔️ DO use a project file's `TargetFrameworks` property when multi-targeting.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <!-- This project will output netstandard2.0 and net461 assemblies -->
    <TargetFrameworks>netstandard2.0;net461</TargetFrameworks>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="de1a5-152">✔️, UWP ve Xamarin için Çoklu hedefleme proje dosyanızı büyük ölçüde basitleştirirken [MSBuild. SDK. Extras](https://github.com/onovotny/MSBuildSdkExtras) kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="de1a5-152">✔️ CONSIDER using [MSBuild.Sdk.Extras](https://github.com/onovotny/MSBuildSdkExtras) when multi-targeting for UWP and Xamarin as it greatly simplifies your project file.</span></span>

## <a name="older-targets"></a><span data-ttu-id="de1a5-153">Daha eski hedefler</span><span class="sxs-lookup"><span data-stu-id="de1a5-153">Older targets</span></span>

<span data-ttu-id="de1a5-154">.NET, artık yaygın olarak kullanılmayan platformların yanı sıra, .NET Framework, destek ve uzun süreli olan sürümlerinin hedeflenmesini destekler.</span><span class="sxs-lookup"><span data-stu-id="de1a5-154">.NET supports targeting versions of the .NET Framework that are long out of support as well as platforms that are no longer commonly used.</span></span> <span data-ttu-id="de1a5-155">Kitaplığınızın mümkün olduğunca çok sayıda hedef üzerinde çalışmasını sağlamak için bir değer olsa da, eksik API 'Leri geçici olarak çözmek için önemli ölçüde ek yük eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="de1a5-155">While there's value in making your library work on as many targets as possible, having to work around missing APIs can add significant overhead.</span></span> <span data-ttu-id="de1a5-156">Belirli çerçevelerin daha fazla hedeflenmesini ve bunların erişim ve sınırlamalarını göz önünde bulundurduğumuz düşünülmektedir.</span><span class="sxs-lookup"><span data-stu-id="de1a5-156">We believe certain frameworks are no longer worth targeting, considering their reach and limitations.</span></span>

<span data-ttu-id="de1a5-157">❌, taşınabilir sınıf kitaplığı (PCL) hedefi içermez.</span><span class="sxs-lookup"><span data-stu-id="de1a5-157">❌ DO NOT include a Portable Class Library (PCL) target.</span></span> <span data-ttu-id="de1a5-158">Örneğin: `portable-net45+win8+wpa81+wp8`.</span><span class="sxs-lookup"><span data-stu-id="de1a5-158">For example, `portable-net45+win8+wpa81+wp8`.</span></span>

> <span data-ttu-id="de1a5-159">.NET Standard, platformlar arası .NET kitaplıklarını desteklemeye yönelik modern bir yoldur ve PCLs 'yi değiştirir.</span><span class="sxs-lookup"><span data-stu-id="de1a5-159">.NET Standard is the modern way to support cross-platform .NET libraries and replaces PCLs.</span></span>

<span data-ttu-id="de1a5-160">❌ artık desteklenmeyen .NET platformları için hedefler dahil DEĞILDIR.</span><span class="sxs-lookup"><span data-stu-id="de1a5-160">❌ DO NOT include targets for .NET platforms that are no longer supported.</span></span> <span data-ttu-id="de1a5-161">Örneğin, `SL4``WP`.</span><span class="sxs-lookup"><span data-stu-id="de1a5-161">For example, `SL4`, `WP`.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="de1a5-162">[Önceki](get-started.md)
>[İleri](strong-naming.md)</span><span class="sxs-lookup"><span data-stu-id="de1a5-162">[Previous](get-started.md)
[Next](strong-naming.md)</span></span>
