---
title: .NET Core için bağlantı noktası kod için bağımlılıkları analiz edin
description: .NET Framework projenizden .NET Core için bağlantı noktası için dış bağımlılıkları analiz etmeyi öğrenin.
author: cartermp
ms.date: 12/04/2018
ms.custom: seodec18
ms.openlocfilehash: dce8e6cd4986b15cf926154b378964db4beef398
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170333"
---
# <a name="analyze-your-dependencies-to-port-code-to-net-core"></a><span data-ttu-id="70ad7-103">Bağımlılıklarınızı .NET Core için bağlantı noktası kod çözümleme</span><span class="sxs-lookup"><span data-stu-id="70ad7-103">Analyze your dependencies to port code to .NET Core</span></span>

<span data-ttu-id="70ad7-104">Kodunuzu .NET Core veya .NET Standard için bağımlılıklarınızı anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="70ad7-104">To port your code to .NET Core or .NET Standard, you must understand your dependencies.</span></span> <span data-ttu-id="70ad7-105">Dış bağımlılıklar [NuGet paketlerini](#analyze-referenced-nuget-packages-on-your-project) veya [DLL'leri](#analyze-dependencies-that-arent-nuget-packages) projeye başvuran ancak derleme yok.</span><span class="sxs-lookup"><span data-stu-id="70ad7-105">External dependencies are the [NuGet packages](#analyze-referenced-nuget-packages-on-your-project) or [DLLs](#analyze-dependencies-that-arent-nuget-packages) you reference in your project, but that you don't build.</span></span> <span data-ttu-id="70ad7-106">Her bir bağımlılığın değerlendirin ve .NET Core ile uyumlu değil ve olanlar için yedek bir plan geliştirin.</span><span class="sxs-lookup"><span data-stu-id="70ad7-106">Evaluate each dependency and develop a contingency plan for the ones that aren't compatible with .NET Core.</span></span> <span data-ttu-id="70ad7-107">.NET Core ile uyumlu bir bağımlılık olup olmadığını açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="70ad7-107">Here's how to determine if a dependency is compatible with .NET Core.</span></span>

## <a name="analyze-referenced-nuget-packages-in-your-projects"></a><span data-ttu-id="70ad7-108">Projelerinizde başvurulan NuGet paketleri analiz</span><span class="sxs-lookup"><span data-stu-id="70ad7-108">Analyze referenced NuGet packages in your projects</span></span>

<span data-ttu-id="70ad7-109">NuGet paketlerini projenize başvuruda bulunursanız, .NET Core ile uyumlu olup olmadıklarını doğrulamak gerekir.</span><span class="sxs-lookup"><span data-stu-id="70ad7-109">If you reference NuGet packages in your project, you need to verify if they're compatible with .NET Core.</span></span>
<span data-ttu-id="70ad7-110">Gerçekleştirmenin iki yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="70ad7-110">There are two ways to accomplish that:</span></span>

* [<span data-ttu-id="70ad7-111">NuGet kullanarak paket Gezgini uygulama</span><span class="sxs-lookup"><span data-stu-id="70ad7-111">Using the NuGet Package Explorer app</span></span>](#analyze-nuget-packages-using-nuget-package-explorer)
* [<span data-ttu-id="70ad7-112">Nuget.org sitesini kullanma</span><span class="sxs-lookup"><span data-stu-id="70ad7-112">Using the nuget.org site</span></span>](#analyze-nuget-packages-using-nugetorg)

<span data-ttu-id="70ad7-113">.NET Core ve yalnızca hedef .NET Framework ile uyumlu değillerse paketlerini çözümledikten sonra olursa denetleyebilirsiniz [.NET Framework uyumluluk modu](#net-framework-compatibility-mode) taşıma sürecinizi yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="70ad7-113">After analyzing the packages, if they're not compatible with .NET Core and only target .NET Framework, you can check if the [.NET Framework compatibility mode](#net-framework-compatibility-mode) can help with your porting process.</span></span>

### <a name="analyze-nuget-packages-using-nuget-package-explorer"></a><span data-ttu-id="70ad7-114">NuGet paket Gezgini kullanarak NuGet paketleri çözümleyin</span><span class="sxs-lookup"><span data-stu-id="70ad7-114">Analyze NuGet packages using NuGet Package Explorer</span></span>

<span data-ttu-id="70ad7-115">Bir NuGet paketi kendisi bir platforma özgü derlemeleri içeren klasörleri kümesidir.</span><span class="sxs-lookup"><span data-stu-id="70ad7-115">A NuGet package is itself a set of folders that contain platform-specific assemblies.</span></span> <span data-ttu-id="70ad7-116">Bu nedenle paketin içindeki uyumlu bir derlemeyi içeren bir klasör olup olmadığını denetlemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="70ad7-116">So you need to check if there's a folder that contains a compatible assembly inside the package.</span></span>

<span data-ttu-id="70ad7-117">NuGet paketi klasörleri incelemek için en kolay yolu kullanmaktır [NuGet paket Gezgini](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) aracı.</span><span class="sxs-lookup"><span data-stu-id="70ad7-117">The easiest way to inspect NuGet Package folders is to use the [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) tool.</span></span> <span data-ttu-id="70ad7-118">Yükledikten sonra klasör adlarını görmek için aşağıdaki adımları kullanın:</span><span class="sxs-lookup"><span data-stu-id="70ad7-118">After installing it, use the following steps to see the folder names:</span></span>

1. <span data-ttu-id="70ad7-119">NuGet paket Gezgini açın.</span><span class="sxs-lookup"><span data-stu-id="70ad7-119">Open the NuGet Package Explorer.</span></span>
2. <span data-ttu-id="70ad7-120">Tıklayın **açık çevrimiçi akış paketinden**.</span><span class="sxs-lookup"><span data-stu-id="70ad7-120">Click **Open package from online feed**.</span></span>
3. <span data-ttu-id="70ad7-121">Paket adını arayın.</span><span class="sxs-lookup"><span data-stu-id="70ad7-121">Search for the name of the package.</span></span>
4. <span data-ttu-id="70ad7-122">Arama sonuçlarından paket adını seçin ve tıklayın **açın**.</span><span class="sxs-lookup"><span data-stu-id="70ad7-122">Select the package name from the search results and click **open**.</span></span>
5. <span data-ttu-id="70ad7-123">Genişletin *LIB* klasörünü sağ tarafı ve klasör adlarını bakın.</span><span class="sxs-lookup"><span data-stu-id="70ad7-123">Expand the *lib* folder on the right-hand side and look at folder names.</span></span>

<span data-ttu-id="70ad7-124">Aşağıdaki adlarından biriyle bir klasörü arayın:</span><span class="sxs-lookup"><span data-stu-id="70ad7-124">Look for a folder with any of the following names:</span></span>

```
netstandard1.0
netstandard1.1
netstandard1.2
netstandard1.3
netstandard1.4
netstandard1.5
netstandard1.6
netstandard2.0
netcoreapp1.0
netcoreapp1.1
netcoreapp2.0
netcoreapp2.1
netcoreapp2.2
portable-net45-win8
portable-win8-wpa8
portable-net451-win81
portable-net45-win8-wpa8-wpa81
```

<span data-ttu-id="70ad7-125">Bu değerler [hedef çerçeve bilinen adlar (Tfm'ler)](../../standard/frameworks.md) sürümleri için harita [.NET Standard](../../standard/net-standard.md), .NET Core ve .NET Core ile uyumlu olan geleneksel taşınabilir sınıf kitaplığı (PCL) profilleri.</span><span class="sxs-lookup"><span data-stu-id="70ad7-125">These values are the [Target Framework Monikers (TFMs)](../../standard/frameworks.md) that map to versions of the [.NET Standard](../../standard/net-standard.md), .NET Core, and traditional Portable Class Library (PCL) profiles that are compatible with .NET Core.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="70ad7-126">Bir paket destekleyen Tfm'ler baktığımda unutmayın `netcoreapp*`, uyumlu açıkken, yalnızca .NET Core projeleri için ve .NET Standard projeleri için değil.</span><span class="sxs-lookup"><span data-stu-id="70ad7-126">When looking at the TFMs that a package supports, note that `netcoreapp*`, while compatible, is for .NET Core projects only and not for .NET Standard projects.</span></span>
> <span data-ttu-id="70ad7-127">Yalnızca hedefleyen bir kitaplık `netcoreapp*` değil `netstandard*` yalnızca diğer .NET Core uygulamaları tarafından kullanılabilecek.</span><span class="sxs-lookup"><span data-stu-id="70ad7-127">A library that only targets `netcoreapp*` and not `netstandard*` can only be consumed by other .NET Core apps.</span></span>

### <a name="analyze-nuget-packages-using-nugetorg"></a><span data-ttu-id="70ad7-128">NuGet paketleri nuget.org kullanarak Analiz</span><span class="sxs-lookup"><span data-stu-id="70ad7-128">Analyze NuGet packages using nuget.org</span></span>

<span data-ttu-id="70ad7-129">Alternatif olarak, her paket destekler Tfm'ler gördüğünüz [nuget.org](https://www.nuget.org/) altında **bağımlılıkları** paket bölümü.</span><span class="sxs-lookup"><span data-stu-id="70ad7-129">Alternatively, you can see the TFMs that each package supports on [nuget.org](https://www.nuget.org/) under the **Dependencies** section of the package page.</span></span>

<span data-ttu-id="70ad7-130">Site kullanarak uyumluluğunu doğrulamak için daha kolay bir yöntem olmasına karşın **bağımlılıkları** bilgileri kullanılabilir değil tüm paketler için sitesinde.</span><span class="sxs-lookup"><span data-stu-id="70ad7-130">Although using the site is an easier method to verify the compatibility, **Dependencies** information is not available on the site for all packages.</span></span>

### <a name="net-framework-compatibility-mode"></a><span data-ttu-id="70ad7-131">.NET framework uyumluluk modu</span><span class="sxs-lookup"><span data-stu-id="70ad7-131">.NET Framework compatibility mode</span></span>

<span data-ttu-id="70ad7-132">Birçok NuGet paketi olarak NuGet paketlerini çözümledikten sonra bunların yalnızca .NET Framework'ü hedefleyen bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70ad7-132">After analyzing the NuGet packages, you might find that they only target the .NET Framework, as most NuGet packages do.</span></span>

<span data-ttu-id="70ad7-133">.NET Standard 2.0 ile başlayarak, .NET Framework uyumluluk modu sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="70ad7-133">Starting with .NET Standard 2.0, the .NET Framework compatibility mode was introduced.</span></span> <span data-ttu-id="70ad7-134">Bu uyumluluk modu, .NET Framework kitaplıkları başvurmak .NET Standard ve .NET Core projeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="70ad7-134">This compatibility mode allows .NET Standard and .NET Core projects to reference .NET Framework libraries.</span></span> <span data-ttu-id="70ad7-135">.NET Framework kitaplıklarına başvuruda bulunan işe yaramazsa tüm projeler için örneğin Windows Presentation Foundation (WPF) API'leri kitaplığı kullanan, ancak birçok taşıma senaryosu engeli kaldırın.</span><span class="sxs-lookup"><span data-stu-id="70ad7-135">Referencing .NET Framework libraries doesn't work for all projects, such as if the library uses Windows Presentation Foundation (WPF) APIs, but it does unblock many porting scenarios.</span></span>

<span data-ttu-id="70ad7-136">Projenizde, .NET Framework gibi hedefleyen NuGet paketlerini başvurduğunuzda [Huitian.PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections), bir paket geri dönüş uyarı alırsınız ([NU1701](/nuget/reference/errors-and-warnings#nu1701)) aşağıdaki örneğe benzer:</span><span class="sxs-lookup"><span data-stu-id="70ad7-136">When you reference NuGet packages that target the .NET Framework in your project, such as [Huitian.PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections), you get a package fallback warning ([NU1701](/nuget/reference/errors-and-warnings#nu1701)) similar to the following example:</span></span>

`NU1701: Package ‘Huitian.PowerCollections 1.0.0’ was restored using ‘.NETFramework,Version=v4.6.1’ instead of the project target framework ‘.NETStandard,Version=v2.0’. This package may not be fully compatible with your project.`

<span data-ttu-id="70ad7-137">Bu uyarı, paket eklediğinizde ve emin olmak için oluşturduğunuz her zaman bu paket projenizle test görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="70ad7-137">That warning is displayed when you add the package and every time you build to make sure you test that package with your project.</span></span> <span data-ttu-id="70ad7-138">Projenizi beklendiği gibi çalışıp çalışmadığını Visual Studio'da paket özelliklerini düzenleyerek veya sık kullandığınız kod proje dosyasında el ile düzenleme, uyarı gösterilmemesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70ad7-138">If your project is working as expected, you can suppress that warning by editing the package properties in Visual Studio or by manually editing the project file in your favorite code editor.</span></span>

<span data-ttu-id="70ad7-139">Proje dosyasını düzenleyerek uyarıyı bastırmak için bulma `PackageReference` giriş paketi için uyarıyı engellemek ve istediğiniz ekleme `NoWarn` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="70ad7-139">To suppress the warning by editing the project file, find the `PackageReference` entry for the package you want to suppress the warning for and add the `NoWarn` attribute.</span></span> <span data-ttu-id="70ad7-140">`NoWarn` Özniteliği tüm uyarı kimliklerinin virgülle ayrılmış listesini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="70ad7-140">The `NoWarn` attribute accepts a comma-separated list of all the warning IDs.</span></span> <span data-ttu-id="70ad7-141">Aşağıdaki örnek, gizlemek gösterilmektedir `NU1701` için uyarı `Huitian.PowerCollections` el ile proje dosyasını düzenleyerek paket:</span><span class="sxs-lookup"><span data-stu-id="70ad7-141">The following example shows how to suppress the `NU1701` warning for the `Huitian.PowerCollections` package by editing your project file manually:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Huitian.PowerCollections" Version="1.0.0" NoWarn="NU1701" />
</ItemGroup>
```

<span data-ttu-id="70ad7-142">Visual Studio'da Derleyici uyarılarını gizleme hakkında daha fazla bilgi için bkz: [NuGet paketleri için uyarıları gizleme](/visualstudio/ide/how-to-suppress-compiler-warnings#suppressing-warnings-for-nuget-packages).</span><span class="sxs-lookup"><span data-stu-id="70ad7-142">For more information on how to suppress compiler warnings in Visual Studio, see [Suppressing warnings for NuGet packages](/visualstudio/ide/how-to-suppress-compiler-warnings#suppressing-warnings-for-nuget-packages).</span></span>

### <a name="port-your-packages-to-packagereference"></a><span data-ttu-id="70ad7-143">Paketleriniz için bağlantı noktası `PackageReference`</span><span class="sxs-lookup"><span data-stu-id="70ad7-143">Port your packages to `PackageReference`</span></span>

<span data-ttu-id="70ad7-144">.NET core kullanan [PackageReference](/nuget/consume-packages/package-references-in-project-files) Paket bağımlılıklarını belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="70ad7-144">.NET Core uses [PackageReference](/nuget/consume-packages/package-references-in-project-files) to specify package dependencies.</span></span> <span data-ttu-id="70ad7-145">Kullanıyorsanız [packages.config](/nuget/reference/packages-config) paketlerinizi belirtmek için üzerinde dönüştürmek ihtiyacınız olacak `PackageReference`.</span><span class="sxs-lookup"><span data-stu-id="70ad7-145">If you are using [packages.config](/nuget/reference/packages-config) to specify your packages, you will need to convert over to `PackageReference`.</span></span>

<span data-ttu-id="70ad7-146">Daha fazla bilgi edinebilirsiniz [PackageReference packages.config'ten geçiş](/nuget/reference/migrate-packages-config-to-package-reference).</span><span class="sxs-lookup"><span data-stu-id="70ad7-146">You can learn more at [Migrate from packages.config to PackageReference](/nuget/reference/migrate-packages-config-to-package-reference).</span></span>

### <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a><span data-ttu-id="70ad7-147">.NET Core üzerinde NuGet paket bağımlılık çalıştırmaz ne yapılacağını</span><span class="sxs-lookup"><span data-stu-id="70ad7-147">What to do when your NuGet package dependency doesn't run on .NET Core</span></span>

<span data-ttu-id="70ad7-148">.NET Core üzerinde bağımlı bir NuGet paketi çalışmazsa yapabileceğiniz birkaç şey vardır:</span><span class="sxs-lookup"><span data-stu-id="70ad7-148">There are a few things you can do if a NuGet package you depend on doesn't run on .NET Core:</span></span>

1. <span data-ttu-id="70ad7-149">Proje açık kaynaklıdır ve GitHub gibi herhangi bir yerde barındırılan, geliştiricilerin doğrudan bağlantı kurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70ad7-149">If the project is open source and hosted somewhere like GitHub, you can engage the developers directly.</span></span>
2. <span data-ttu-id="70ad7-150">Doğrudan üzerinde Yazar başvurabilirsiniz [nuget.org](https://www.nuget.org/). Paketini arayın ve'ı tıklatın **kişi sahipleri** paketin sayfasının sol taraftaki.</span><span class="sxs-lookup"><span data-stu-id="70ad7-150">You can contact the author directly on [nuget.org](https://www.nuget.org/). Search for the package and click **Contact Owners** on the left-hand side of the package's page.</span></span>
3. <span data-ttu-id="70ad7-151">Kullanmakta olduğunuz paket aynı görevi gerçekleştirir .NET Core üzerinde çalışan başka bir paket için arama yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70ad7-151">You can search for another package that runs on .NET Core that accomplishes the same task as the package you were using.</span></span>
4. <span data-ttu-id="70ad7-152">Paket kendiniz yapmakta olduğu kod yazma girişiminde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="70ad7-152">You can attempt to write the code the package was doing yourself.</span></span>
5. <span data-ttu-id="70ad7-153">Uygulamanızın işlevselliğini en az değiştirerek paket bağımlılığını ortadan kaldırabileceğiniz paket uyumlu bir sürümünün kullanılabilir olana kadar.</span><span class="sxs-lookup"><span data-stu-id="70ad7-153">You could eliminate the dependency on the package by changing the functionality of your app, at least until a compatible version of the package becomes available.</span></span>

<span data-ttu-id="70ad7-154">Açık kaynaklı proje maintainers ve NuGet paket yayımlayanlar genellikle gönüllüler olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="70ad7-154">Remember that open-source project maintainers and NuGet package publishers are often volunteers.</span></span> <span data-ttu-id="70ad7-155">Çünkü bunlar belirli bir etki alanı hakkında dikkat edin, ücretsiz yapın ve genellikle farklı bir gündüz saatlerinde kullanılan iş sahip, katkıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="70ad7-155">They contribute because they care about a given domain, do it for free, and often have a different daytime job.</span></span> <span data-ttu-id="70ad7-156">Bu nedenle bunları sormak için .NET Core desteği ile iletişim kurarken, oluşturduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="70ad7-156">So be mindful of that when contacting them to ask for .NET Core support.</span></span>

<span data-ttu-id="70ad7-157">Yukarıdakilerden herhangi biri ile sorunu çözemezseniz, .NET Core için bağlantı noktası daha sonraki bir tarihte zorunda kalabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70ad7-157">If you can't resolve your issue with any of the above, you may have to port to .NET Core at a later date.</span></span>

<span data-ttu-id="70ad7-158">.NET ekibi hangi kitaplıkların .NET Core ile desteklemek en önemli olduğunu bilmek istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="70ad7-158">The .NET Team would like to know which libraries are the most important to support with .NET Core.</span></span> <span data-ttu-id="70ad7-159">Bir e-posta gönderebilir dotnet@microsoft.com kullanmak istediğiniz kitaplıkları hakkında.</span><span class="sxs-lookup"><span data-stu-id="70ad7-159">You can send an email to dotnet@microsoft.com about the libraries you'd like to use.</span></span>

## <a name="analyze-dependencies-that-arent-nuget-packages"></a><span data-ttu-id="70ad7-160">NuGet paketlerini olmayan bağımlılıkları analiz edin</span><span class="sxs-lookup"><span data-stu-id="70ad7-160">Analyze dependencies that aren't NuGet packages</span></span>

<span data-ttu-id="70ad7-161">Dosya sistemindeki bir DLL gibi bir NuGet paketi olmayan bağımlılığa sahip.</span><span class="sxs-lookup"><span data-stu-id="70ad7-161">You may have a dependency that isn't a NuGet package, such as a DLL in the file system.</span></span> <span data-ttu-id="70ad7-162">Bu bağımlılık taşınabilirliğinin belirlemek için tek yol [.NET Portability Analyzer](https://github.com/Microsoft/dotnet-apiport) aracı.</span><span class="sxs-lookup"><span data-stu-id="70ad7-162">The only way to determine the portability of that dependency is to run the [.NET Portability Analyzer](https://github.com/Microsoft/dotnet-apiport) tool.</span></span> <span data-ttu-id="70ad7-163">Araç, .NET Framework'ü hedefleyen derlemeler analiz edin ve .NET Core gibi diğer .NET platformları için taşınabilir olmayan API'leri tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="70ad7-163">The tool can analyze assemblies that target the .NET Framework and identify APIs that aren't portable to other .NET platforms such as .NET Core.</span></span> <span data-ttu-id="70ad7-164">Aracı veya konsol uygulaması olarak çalıştırabilirsiniz bir [Visual Studio Uzantısı](../../standard/analyzers/portability-analyzer.md).</span><span class="sxs-lookup"><span data-stu-id="70ad7-164">You can run the tool as a console application or as a [Visual Studio extension](../../standard/analyzers/portability-analyzer.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="70ad7-165">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="70ad7-165">Next steps</span></span>

<span data-ttu-id="70ad7-166">Bir kitaplığı taşıma, kullanıma [Kitaplıklarınızı taşıma](libraries.md).</span><span class="sxs-lookup"><span data-stu-id="70ad7-166">If you're porting a library, check out [Porting your Libraries](libraries.md).</span></span>
