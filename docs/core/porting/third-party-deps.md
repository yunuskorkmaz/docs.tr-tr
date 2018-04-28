---
title: Bağlantı noktası oluşturma, üçüncü taraf bağımlılıkları için .NET Core - Çözümle
description: .NET Framework projenizden .NET Core için bağlantı noktası için üçüncü taraf bağımlılıkları çözümlemeyi öğrenin.
author: cartermp
ms.author: mairaw
ms.date: 02/15/2018
ms.topic: conceptual
ms.prod: dotnet-core
ms.workload:
- dotnetcore
ms.openlocfilehash: be8d5a60977c7863136a1661a60e3bf23c0eb93e
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="analyze-your-third-party-dependencies"></a><span data-ttu-id="ffc9f-103">Üçüncü taraf bağımlılıkları analiz</span><span class="sxs-lookup"><span data-stu-id="ffc9f-103">Analyze your third-party dependencies</span></span>

<span data-ttu-id="ffc9f-104">Kodunuzu .NET Core veya .NET standart bağlantı noktasına arıyorsanız, taşıma işleminin ilk adımında, üçüncü taraf bağımlılıkları anlamaktır.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-104">If you're looking to port your code to .NET Core or .NET Standard, the first step in the porting process is to understand your third-party dependencies.</span></span> <span data-ttu-id="ffc9f-105">Üçüncü taraf bağımlılıklarıdır ya da [NuGet paketlerini](#analyze-referenced-nuget-packages-on-your-project) veya [DLL'leri](#analyze-dependencies-that-arent-nuget-packages) projenizde başvuran.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-105">Third-party dependencies are either [NuGet packages](#analyze-referenced-nuget-packages-on-your-project) or [DLLs](#analyze-dependencies-that-arent-nuget-packages) you're referencing in your project.</span></span> <span data-ttu-id="ffc9f-106">Her bir bağımlılığın değerlendirin ve .NET Core ile uyumlu değil bağımlılıklar için yedek bir plan geliştirin.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-106">Evaluate each dependency and develop a contingency plan for the dependencies that aren't compatible with .NET Core.</span></span> <span data-ttu-id="ffc9f-107">Bu makalede bağımlılık .NET Core ile uyumlu olup olmadığını belirleme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-107">This article shows you how to determine if the dependency is compatible with .NET Core.</span></span>

## <a name="analyze-referenced-nuget-packages-in-your-project"></a><span data-ttu-id="ffc9f-108">Projenizdeki başvurulan NuGet paketleri analiz</span><span class="sxs-lookup"><span data-stu-id="ffc9f-108">Analyze referenced NuGet packages in your project</span></span>

<span data-ttu-id="ffc9f-109">Projenizdeki NuGet paketlerini başvuran, .NET Core ile uyumlu değilse doğrulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-109">If you're referencing NuGet packages in your project, you need to verify if they're compatible with .NET Core.</span></span>
<span data-ttu-id="ffc9f-110">Bunu yapmaya yönelik iki yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="ffc9f-110">There are two ways to accomplish that:</span></span>

* <span data-ttu-id="ffc9f-111">[NuGet paketi Gezgini uygulamasını kullanarak](#analyze-nuget-packages-using-nuget-package-explorer) (en güvenilir yöntemi).</span><span class="sxs-lookup"><span data-stu-id="ffc9f-111">[Using the NuGet Package Explorer app](#analyze-nuget-packages-using-nuget-package-explorer) (the most reliable method).</span></span>
* <span data-ttu-id="ffc9f-112">[Nuget.org site kullanarak](#analyze-nuget-packages-using-nugetorg).</span><span class="sxs-lookup"><span data-stu-id="ffc9f-112">[Using the nuget.org site](#analyze-nuget-packages-using-nugetorg).</span></span>

<span data-ttu-id="ffc9f-113">.NET Core ve yalnızca hedef .NET Framework ile uyumlu değillerse paketlerini çözümledikten sonra varsa göz atabilirsiniz [.NET Framework uyumluluk modu](#net-framework-compatibility-mode) taşıma işlemine yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-113">After analyzing the packages, if they're not compatible with .NET Core and only target .NET Framework, you can check if the [.NET Framework compatibility mode](#net-framework-compatibility-mode) can help with your porting process.</span></span>

### <a name="analyze-nuget-packages-using-nuget-package-explorer"></a><span data-ttu-id="ffc9f-114">NuGet paket Gezgini'ni kullanarak NuGet paketleri analiz</span><span class="sxs-lookup"><span data-stu-id="ffc9f-114">Analyze NuGet packages using NuGet Package Explorer</span></span>

<span data-ttu-id="ffc9f-115">Bir NuGet paketi kendisini platforma özgü derlemeleri içeren klasörleri kümesidir.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-115">A NuGet package is itself a set of folders that contain platform-specific assemblies.</span></span> <span data-ttu-id="ffc9f-116">Bu nedenle paketin içindeki uyumlu bir derleme içeren bir klasör olup olmadığını denetlemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-116">So you need to check if there's a folder that contains a compatible assembly inside the package.</span></span>

<span data-ttu-id="ffc9f-117">NuGet paketi klasörleri incelemek için en kolay yolu kullanmaktır [NuGet paketi Gezgini](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) aracı.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-117">The easiest way to inspect NuGet Package folders is to use the [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) tool.</span></span> <span data-ttu-id="ffc9f-118">Yükledikten sonra klasör adlarını görmek için aşağıdaki adımları kullanın:</span><span class="sxs-lookup"><span data-stu-id="ffc9f-118">After installing it, use the following steps to see the folder names:</span></span>

1. <span data-ttu-id="ffc9f-119">NuGet paketi Explorer'ı açın.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-119">Open the NuGet Package Explorer.</span></span>
2. <span data-ttu-id="ffc9f-120">Tıklatın **çevrimiçi akış açık paketinden**.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-120">Click **Open package from online feed**.</span></span>
3. <span data-ttu-id="ffc9f-121">Paketin adını arayın.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-121">Search for the name of the package.</span></span>
4. <span data-ttu-id="ffc9f-122">Arama sonuçlarından paket adını seçin ve tıklatın **açmak**.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-122">Select the package name from the search results and click **open**.</span></span>
5. <span data-ttu-id="ffc9f-123">Genişletme *lib* klasörünü sağ taraftaki ve klasör adlarını bakın.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-123">Expand the *lib* folder on the right-hand side and look at folder names.</span></span>

<span data-ttu-id="ffc9f-124">Aşağıdaki adlarının herhangi biri bir klasörle arayın:</span><span class="sxs-lookup"><span data-stu-id="ffc9f-124">Look for a folder with any of the following names:</span></span>

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
portable-net45-win8
portable-win8-wpa8
portable-net451-win81
portable-net45-win8-wpa8-wpa81
```

<span data-ttu-id="ffc9f-125">Bu değerler [hedef Framework adlar (TFMs)](../../standard/frameworks.md) sürümleri için eşleme [.NET standart](../../standard/net-standard.md), .NET Core ve .NET Core ile uyumlu olan geleneksel taşınabilir sınıf kitaplığı (PCL) profilleri.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-125">These values are the [Target Framework Monikers (TFMs)](../../standard/frameworks.md) that map to versions of the [.NET Standard](../../standard/net-standard.md), .NET Core, and traditional Portable Class Library (PCL) profiles that are compatible with .NET Core.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ffc9f-126">Bir paketi destekler TFMs bakarken unutmayın `netcoreapp*`, uyumlu çalışırken, yalnızca .NET çekirdeği projelerde ve .NET standart projeleri için değil.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-126">When looking at the TFMs that a package supports, note that `netcoreapp*`, while compatible, is for .NET Core projects only and not for .NET Standard projects.</span></span>
> <span data-ttu-id="ffc9f-127">Yalnızca hedefleyen bir kitaplık `netcoreapp*` ve `netstandard*` yalnızca diğer .NET Core uygulamaları tarafından kullanılabilecek.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-127">A library that only targets `netcoreapp*` and not `netstandard*` can only be consumed by other .NET Core apps.</span></span>

<span data-ttu-id="ffc9f-128">Uyumlu olabilir .NET Core yayın öncesi sürümlerini kullanılan bazı eski TFMs vardır:</span><span class="sxs-lookup"><span data-stu-id="ffc9f-128">There are also some legacy TFMs used in pre-release versions of .NET Core that may also be compatible:</span></span>

```
dnxcore50
dotnet5.0
dotnet5.1
dotnet5.2
dotnet5.3
dotnet5.4
dotnet5.5
```

<span data-ttu-id="ffc9f-129">Büyük olasılıkla bu TFMs kodunuzu ile çalışırken, uyumluluk garantisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-129">While these TFMs likely work with your code, there is no guarantee of compatibility.</span></span> <span data-ttu-id="ffc9f-130">Bu TFMs paketlerle yayın öncesi .NET Core paketlerle oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-130">Packages with these TFMs were built with pre-release .NET Core packages.</span></span> <span data-ttu-id="ffc9f-131">Zaman (veya varsa) not edin bu TFMs kullanarak paketleri .NET standart temelli olacak şekilde güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-131">Take note of when (or if) packages using these TFMs are updated to be .NET Standard-based.</span></span>

> [!NOTE]
> <span data-ttu-id="ffc9f-132">Geleneksel PCL veya yayın öncesi .NET Core hedef hedefleme paketini kullanmak için kullanmanız gerekir `PackageTargetFallback` MSBuild proje dosyası öğesinde.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-132">To use a package targeting a traditional PCL or pre-release .NET Core target, you must use the `PackageTargetFallback` MSBuild element in your project file.</span></span>
> <span data-ttu-id="ffc9f-133">Bu MSBuild öğe hakkında daha fazla bilgi için bkz: [ `PackageTargetFallback` ](../tools/csproj.md#packagetargetfallback).</span><span class="sxs-lookup"><span data-stu-id="ffc9f-133">For more information about this MSBuild element, see [`PackageTargetFallback`](../tools/csproj.md#packagetargetfallback).</span></span>

### <a name="analyze-nuget-packages-using-nugetorg"></a><span data-ttu-id="ffc9f-134">Nuget.org kullanarak NuGet paketleri analiz</span><span class="sxs-lookup"><span data-stu-id="ffc9f-134">Analyze NuGet packages using nuget.org</span></span>

<span data-ttu-id="ffc9f-135">Alternatif olarak, her paketi üzerinde destekler TFMs görebilirsiniz [nuget.org](https://www.nuget.org/) altında **bağımlılıkları** paket sayfasının bölümünde.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-135">Alternatively, you can see the TFMs that each package supports on [nuget.org](https://www.nuget.org/) under the **Dependencies** section of the package page.</span></span>

<span data-ttu-id="ffc9f-136">Site kullanarak uyumluluğunu doğrulamak için daha kolay bir yöntem olsa **bağımlılıkları** bilgi kullanılabilir değil tüm paketler için sitesinde.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-136">Although using the site is an easier method to verify the compatibility, **Dependencies** information is not available on the site for all packages.</span></span>

### <a name="net-framework-compatibility-mode"></a><span data-ttu-id="ffc9f-137">.NET framework uyumluluk modu</span><span class="sxs-lookup"><span data-stu-id="ffc9f-137">.NET Framework compatibility mode</span></span>

<span data-ttu-id="ffc9f-138">Çoğu NuGet paketleri gibi NuGet paketlerini çözümledikten sonra bunlar yalnızca .NET Framework hedefleyen bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-138">After analyzing the NuGet packages, you might find that they only target the .NET Framework, as most NuGet packages do.</span></span>

<span data-ttu-id="ffc9f-139">.NET standart 2.0 ile başlayarak, .NET Framework uyumluluk modu sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-139">Starting with .NET Standard 2.0, the .NET Framework compatibility mode was introduced.</span></span> <span data-ttu-id="ffc9f-140">Bu uyumluluk modu, .NET Framework kitaplıkları başvurmak .NET standart ve .NET Core projeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-140">This compatibility mode allows .NET Standard and .NET Core projects to reference .NET Framework libraries.</span></span> <span data-ttu-id="ffc9f-141">.NET Framework kitaplıklarına başvuruda bulunan işe yaramazsa tüm projelerde gelmesi gibi kitaplık Windows Presentation Foundation (WPF) API'lerini kullanır, ancak çok sayıda taşıma senaryoları engellemeyi.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-141">Referencing .NET Framework libraries doesn't work for all projects, such as if the library uses Windows Presentation Foundation (WPF) APIs, but it does unblock many porting scenarios.</span></span>

<span data-ttu-id="ffc9f-142">Projeniz .NET Framework gibi hedef NuGet paketlerini başvuru yaptığınızda [Huitian.PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections), bir paket geri dönüş uyarı alın ([NU1701](/nuget/reference/errors-and-warnings#nu1701)) aşağıdaki örneğe benzer:</span><span class="sxs-lookup"><span data-stu-id="ffc9f-142">When you reference NuGet packages that target the .NET Framework in your project, such as [Huitian.PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections), you get a package fallback warning ([NU1701](/nuget/reference/errors-and-warnings#nu1701)) similar to the following example:</span></span>

`NU1701: Package ‘Huitian.PowerCollections 1.0.0’ was restored using ‘.NETFramework,Version=v4.6.1’ instead of the project target framework ‘.NETStandard,Version=v2.0’. This package may not be fully compatible with your project.`

<span data-ttu-id="ffc9f-143">Paketi ekleyin ve emin olmak için oluşturduğunuz her zaman projenizi ile paket test bu uyarı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-143">That warning is displayed when you add the package and every time you build to make sure you test that package with your project.</span></span> <span data-ttu-id="ffc9f-144">Projenizi beklendiği gibi çalışıp çalışmadığını Visual Studio'da paket özelliklerini düzenleyerek veya el ile sık kullanılan kod düzenleyicisinde proje dosyasını düzenleyerek bu uyarı gizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-144">If your project is working as expected, you can suppress that warning by editing the package properties in Visual Studio or by manually editing the project file in your favorite code editor.</span></span>

<span data-ttu-id="ffc9f-145">Proje dosyasını düzenleyerek gizlemek için bulma `PackageReference` giriş paketi için istediğiniz için gizlemek ve eklemek `NoWarn` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-145">To suppress the warning by editing the project file, find the `PackageReference` entry for the package you want to suppress the warning for and add the `NoWarn` attribute.</span></span> <span data-ttu-id="ffc9f-146">`NoWarn` Özniteliği tüm uyarı kimliklerinin virgülle ayrılmış listesini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-146">The `NoWarn` attribute accepts a comma-separated list of all the warning IDs.</span></span> <span data-ttu-id="ffc9f-147">Aşağıdaki örnek, gizlemek gösterilmiştir `NU1701` için uyarı `Huitian.PowerCollections` proje dosyanızı el ile düzenleyerek paketi:</span><span class="sxs-lookup"><span data-stu-id="ffc9f-147">The following example shows how to suppress the `NU1701` warning for the `Huitian.PowerCollections` package by editing your project file manually:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Huitian.PowerCollections" Version="1.0.0" NoWarn="NU1701" />
</ItemGroup>
```

<span data-ttu-id="ffc9f-148">Visual Studio'da Derleyici uyarılarını gizleme hakkında daha fazla bilgi için bkz: [NuGet paketleri için uyarıları gizleme](/visualstudio/ide/how-to-suppress-compiler-warnings#suppressing-warnings-for-nuget-packages).</span><span class="sxs-lookup"><span data-stu-id="ffc9f-148">For more information on how to suppress compiler warnings in Visual Studio, see [Suppressing warnings for NuGet packages](/visualstudio/ide/how-to-suppress-compiler-warnings#suppressing-warnings-for-nuget-packages).</span></span>

### <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a><span data-ttu-id="ffc9f-149">NuGet paket bağımlılığı .NET Core üzerinde çalıştırdığınızda değil yapmanız gerekenler</span><span class="sxs-lookup"><span data-stu-id="ffc9f-149">What to do when your NuGet package dependency doesn't run on .NET Core</span></span>

<span data-ttu-id="ffc9f-150">.NET Core üzerinde bağımlı bir NuGet paketi çalışmazsa yapabileceğiniz birkaç şey vardır:</span><span class="sxs-lookup"><span data-stu-id="ffc9f-150">There are a few things you can do if a NuGet package you depend on doesn't run on .NET Core:</span></span>

1. <span data-ttu-id="ffc9f-151">Proje açık bir kaynaktır ve Github'da gibi herhangi bir yerde barındırılan, geliştiricilerin doğrudan devreye.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-151">If the project is open source and hosted somewhere like GitHub, you can engage the developers directly.</span></span>
2. <span data-ttu-id="ffc9f-152">Yazarın doğrudan üzerinde başvurabilirsiniz [nuget.org](https://www.nuget.org/). Arama için paketi ve tıklayın **kişi sahipleri** paketin sayfasının sol taraftaki.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-152">You can contact the author directly on [nuget.org](https://www.nuget.org/). Search for the package and click **Contact Owners** on the left-hand side of the package's page.</span></span>
3. <span data-ttu-id="ffc9f-153">Kullanmakta olduğunuz paket gibi aynı görevi gerçekleştirir .NET Core üzerinde çalışan başka bir paket için arama yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-153">You can search for another package that runs on .NET Core that accomplishes the same task as the package you were using.</span></span>
4. <span data-ttu-id="ffc9f-154">Paket kendiniz yapmakta olduğu için kod yazma girişiminde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-154">You can attempt to write the code the package was doing yourself.</span></span>
5. <span data-ttu-id="ffc9f-155">En az işlevselliği, uygulamanızın değiştirerek paket bağımlılığını ortadan paket uyumlu bir sürümü kullanılabilir duruma gelinceye kadar.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-155">You could eliminate the dependency on the package by changing the functionality of your app, at least until a compatible version of the package becomes available.</span></span>

<span data-ttu-id="ffc9f-156">Açık kaynaklı proje maintainers ve NuGet paketi yayıncıları genellikle gönüllüsü olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-156">Remember that open-source project maintainers and NuGet package publishers are often volunteers.</span></span> <span data-ttu-id="ffc9f-157">Çünkü bunlar belirli bir etki alanı hakkında dikkat edin, ücretsiz yapın ve genellikle farklı daytime iş sahip oldukları katkıda.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-157">They contribute because they care about a given domain, do it for free, and often have a different daytime job.</span></span> <span data-ttu-id="ffc9f-158">Böylece bunları .NET Core desteği sorulacak iletişim kurarken, oluşturduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-158">So be mindful of that when contacting them to ask for .NET Core support.</span></span>

<span data-ttu-id="ffc9f-159">Yukarıdakilerden herhangi biri ile sorunu çözemezseniz, .NET Core bağlantı noktasına daha sonraki bir tarihte zorunda kalabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-159">If you can't resolve your issue with any of the above, you may have to port to .NET Core at a later date.</span></span>

<span data-ttu-id="ffc9f-160">.NET ekibi hangi kitaplıkları ile .NET Core desteklemek en önemli olan bilmek ister misiniz?</span><span class="sxs-lookup"><span data-stu-id="ffc9f-160">The .NET Team would like to know which libraries are the most important to support with .NET Core.</span></span> <span data-ttu-id="ffc9f-161">E-posta gönderebilirsiniz dotnet@microsoft.com kullanmak istediğiniz kitaplıklar hakkında.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-161">You can send an email to dotnet@microsoft.com about the libraries you'd like to use.</span></span>

## <a name="analyze-dependencies-that-arent-nuget-packages"></a><span data-ttu-id="ffc9f-162">NuGet paketlerini olmayan bağımlılıklarını Çözümle</span><span class="sxs-lookup"><span data-stu-id="ffc9f-162">Analyze dependencies that aren't NuGet packages</span></span>

<span data-ttu-id="ffc9f-163">Dosya sistemi DLL'de gibi bir NuGet paketi olmayan bir bağımlılık olabilir.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-163">You may have a dependency that isn't a NuGet package, such as a DLL in the file system.</span></span> <span data-ttu-id="ffc9f-164">Bu bağımlılık taşınabilirlik belirlemek için tek yolu çalıştırmaktır [.NET taşınabilirlik Çözümleyicisi](https://github.com/Microsoft/dotnet-apiport) aracı.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-164">The only way to determine the portability of that dependency is to run the [.NET Portability Analyzer](https://github.com/Microsoft/dotnet-apiport) tool.</span></span> <span data-ttu-id="ffc9f-165">Aracı, .NET Framework hedefleyen derlemeleri çözümlemek ve .NET Core gibi diğer .NET platformları için taşınabilir olmayan API'leri tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="ffc9f-165">The tool can analyze assemblies that target the .NET Framework and identify APIs that aren't portable to other .NET platforms such as .NET Core.</span></span> <span data-ttu-id="ffc9f-166">Bir konsol uygulaması veya olarak aracını çalıştırabilirsiniz bir [Visual Studio Uzantısı](../../standard/analyzers/portability-analyzer.md).</span><span class="sxs-lookup"><span data-stu-id="ffc9f-166">You can run the tool as a console application or as a [Visual Studio extension](../../standard/analyzers/portability-analyzer.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="ffc9f-167">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="ffc9f-167">Next steps</span></span>

<span data-ttu-id="ffc9f-168">Kitaplığa bağlantı noktası oluşturma, kullanıma [Kitaplıklarınızı taşıma](libraries.md).</span><span class="sxs-lookup"><span data-stu-id="ffc9f-168">If you're porting a library, check out [Porting your Libraries](libraries.md).</span></span>
