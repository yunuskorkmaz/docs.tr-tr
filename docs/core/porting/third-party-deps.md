---
title: .NET Core 'a bağlantı noktası kodu bağımlılıklarını çözümleyin
description: Projenizin .NET Framework .NET Core 'a bağlantı noktası olması için dış bağımlılıkları çözümlemeyi öğrenin.
author: cartermp
ms.date: 12/07/2018
ms.custom: seodec18
ms.openlocfilehash: 36d1c1d2090a0fb9e6f48fe519d15897579df2d5
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72521477"
---
# <a name="analyze-your-dependencies-to-port-code-to-net-core"></a><span data-ttu-id="d4282-103">.NET Core 'a bağlantı noktası kodu için bağımlılıklarınızı çözümleyin</span><span class="sxs-lookup"><span data-stu-id="d4282-103">Analyze your dependencies to port code to .NET Core</span></span>

<span data-ttu-id="d4282-104">Kodunuzun .NET Core veya .NET Standard bağlantı noktası olması için bağımlılıklarınızı anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d4282-104">To port your code to .NET Core or .NET Standard, you must understand your dependencies.</span></span> <span data-ttu-id="d4282-105">Dış bağımlılıklar, projenizde başvurduğunuz, ancak derlemeniz gereken [NuGet paketlerdir](#analyze-referenced-nuget-packages-in-your-projects) veya [DLL 'lardır](#analyze-dependencies-that-arent-nuget-packages) .</span><span class="sxs-lookup"><span data-stu-id="d4282-105">External dependencies are the [NuGet packages](#analyze-referenced-nuget-packages-in-your-projects) or [DLLs](#analyze-dependencies-that-arent-nuget-packages) you reference in your project, but that you don't build.</span></span> <span data-ttu-id="d4282-106">Her bağımlılığı değerlendirin ve .NET Core ile uyumlu olmayan bir yedek plan geliştirin.</span><span class="sxs-lookup"><span data-stu-id="d4282-106">Evaluate each dependency and develop a contingency plan for the ones that aren't compatible with .NET Core.</span></span> <span data-ttu-id="d4282-107">Bir bağımlılığın .NET Core ile uyumlu olup olmadığını belirleme hakkında daha fazla bilgiyi burada bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4282-107">Here's how to determine if a dependency is compatible with .NET Core.</span></span>

## <a name="analyze-referenced-nuget-packages-in-your-projects"></a><span data-ttu-id="d4282-108">Projelerinizde başvurulan NuGet paketlerini çözümleyin</span><span class="sxs-lookup"><span data-stu-id="d4282-108">Analyze referenced NuGet packages in your projects</span></span>

<span data-ttu-id="d4282-109">Projenizde NuGet paketlerine başvursanız, .NET Core ile uyumlu olup olmadığını doğrulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d4282-109">If you reference NuGet packages in your project, you need to verify if they're compatible with .NET Core.</span></span>
<span data-ttu-id="d4282-110">Bunu yapmanın iki yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="d4282-110">There are two ways to accomplish that:</span></span>

- [<span data-ttu-id="d4282-111">NuGet Paket Gezgini uygulamasını kullanma</span><span class="sxs-lookup"><span data-stu-id="d4282-111">Using the NuGet Package Explorer app</span></span>](#analyze-nuget-packages-using-nuget-package-explorer)
- [<span data-ttu-id="d4282-112">Nuget.org sitesini kullanma</span><span class="sxs-lookup"><span data-stu-id="d4282-112">Using the nuget.org site</span></span>](#analyze-nuget-packages-using-nugetorg)

<span data-ttu-id="d4282-113">Paketler çözümlendikten sonra, .NET Core ile uyumlu olmadıkları ve yalnızca hedef .NET Framework, [.NET Framework uyumluluk modunun](#net-framework-compatibility-mode) taşıma süreciyle ilgili olup olmadığını kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4282-113">After analyzing the packages, if they're not compatible with .NET Core and only target .NET Framework, you can check if the [.NET Framework compatibility mode](#net-framework-compatibility-mode) can help with your porting process.</span></span>

### <a name="analyze-nuget-packages-using-nuget-package-explorer"></a><span data-ttu-id="d4282-114">NuGet paket gezginini kullanarak NuGet paketlerini çözümleme</span><span class="sxs-lookup"><span data-stu-id="d4282-114">Analyze NuGet packages using NuGet Package Explorer</span></span>

<span data-ttu-id="d4282-115">Bir NuGet paketi, platforma özgü derlemeler içeren bir klasörler kümesidir.</span><span class="sxs-lookup"><span data-stu-id="d4282-115">A NuGet package is itself a set of folders that contain platform-specific assemblies.</span></span> <span data-ttu-id="d4282-116">Bu nedenle, paketin içinde uyumlu bir derlemeyi içeren bir klasör olup olmadığını denetlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d4282-116">So you need to check if there's a folder that contains a compatible assembly inside the package.</span></span>

<span data-ttu-id="d4282-117">NuGet paket klasörlerini incelemeyi en kolay yolu, [NuGet Paket Gezgini](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) aracını kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="d4282-117">The easiest way to inspect NuGet Package folders is to use the [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) tool.</span></span> <span data-ttu-id="d4282-118">Yükledikten sonra klasör adlarını görmek için aşağıdaki adımları kullanın:</span><span class="sxs-lookup"><span data-stu-id="d4282-118">After installing it, use the following steps to see the folder names:</span></span>

1. <span data-ttu-id="d4282-119">NuGet paket Gezginini açın.</span><span class="sxs-lookup"><span data-stu-id="d4282-119">Open the NuGet Package Explorer.</span></span>
2. <span data-ttu-id="d4282-120">**Çevrimiçi akıştan paketi aç**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d4282-120">Click **Open package from online feed**.</span></span>
3. <span data-ttu-id="d4282-121">Paketin adını arayın.</span><span class="sxs-lookup"><span data-stu-id="d4282-121">Search for the name of the package.</span></span>
4. <span data-ttu-id="d4282-122">Arama sonuçlarından paket adı ' nı seçin ve **Aç**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d4282-122">Select the package name from the search results and click **open**.</span></span>
5. <span data-ttu-id="d4282-123">Sağ taraftaki *LIB* klasörünü genişletin ve klasör adlarına bakın.</span><span class="sxs-lookup"><span data-stu-id="d4282-123">Expand the *lib* folder on the right-hand side and look at folder names.</span></span>

<span data-ttu-id="d4282-124">Aşağıdaki adlardan birini içeren bir klasör arayın:</span><span class="sxs-lookup"><span data-stu-id="d4282-124">Look for a folder with any of the following names:</span></span>

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

<span data-ttu-id="d4282-125">Bu değerler, .NET Core ile uyumlu [.NET Standard](../../standard/net-standard.md), .NET Core ve geleneksel taşınabilir sınıf KITAPLıĞı (PCL) profillerinin sürümleriyle eşlenen [hedef çerçeve takma adları (tfms)](../../standard/frameworks.md) .</span><span class="sxs-lookup"><span data-stu-id="d4282-125">These values are the [Target Framework Monikers (TFMs)](../../standard/frameworks.md) that map to versions of the [.NET Standard](../../standard/net-standard.md), .NET Core, and traditional Portable Class Library (PCL) profiles that are compatible with .NET Core.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d4282-126">Bir paketin desteklediği TFMs 'e baktığınızda, `netcoreapp*`, uyumlu iken yalnızca .NET Core projeleri için olduğunu ve .NET Standard projelerine yönelik olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d4282-126">When looking at the TFMs that a package supports, note that `netcoreapp*`, while compatible, is for .NET Core projects only and not for .NET Standard projects.</span></span>
> <span data-ttu-id="d4282-127">Yalnızca `netcoreapp*` ve `netstandard*` hedefleyen bir kitaplık yalnızca diğer .NET Core uygulamaları tarafından tüketilebilir.</span><span class="sxs-lookup"><span data-stu-id="d4282-127">A library that only targets `netcoreapp*` and not `netstandard*` can only be consumed by other .NET Core apps.</span></span>

### <a name="analyze-nuget-packages-using-nugetorg"></a><span data-ttu-id="d4282-128">Nuget.org kullanarak NuGet paketlerini çözümleme</span><span class="sxs-lookup"><span data-stu-id="d4282-128">Analyze NuGet packages using nuget.org</span></span>

<span data-ttu-id="d4282-129">Alternatif olarak, paket sayfasındaki **Bağımlılıklar** bölümünde her bir paketin [NuGet.org](https://www.nuget.org/) üzerinde desteklediği tfms 'yi görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4282-129">Alternatively, you can see the TFMs that each package supports on [nuget.org](https://www.nuget.org/) under the **Dependencies** section of the package page.</span></span>

<span data-ttu-id="d4282-130">Siteyi kullanmak uyumluluğu doğrulamak için daha kolay bir yöntem olsa da, tüm paketler için sitede **Bağımlılıklar** bilgisi yok.</span><span class="sxs-lookup"><span data-stu-id="d4282-130">Although using the site is an easier method to verify the compatibility, **Dependencies** information is not available on the site for all packages.</span></span>

### <a name="net-framework-compatibility-mode"></a><span data-ttu-id="d4282-131">Uyumluluk modu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d4282-131">.NET Framework compatibility mode</span></span>

<span data-ttu-id="d4282-132">NuGet paketlerini analiz ettikten sonra, çoğu NuGet paketi olduğu için yalnızca .NET Framework hedeflemesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4282-132">After analyzing the NuGet packages, you might find that they only target the .NET Framework, as most NuGet packages do.</span></span>

<span data-ttu-id="d4282-133">.NET Standard 2,0 ' den başlayarak .NET Framework uyumluluk modu sunuldu.</span><span class="sxs-lookup"><span data-stu-id="d4282-133">Starting with .NET Standard 2.0, the .NET Framework compatibility mode was introduced.</span></span> <span data-ttu-id="d4282-134">Bu uyumluluk modu, .NET Standard ve .NET Core projelerinin .NET Framework kitaplıklarına başvurmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="d4282-134">This compatibility mode allows .NET Standard and .NET Core projects to reference .NET Framework libraries.</span></span> <span data-ttu-id="d4282-135">.NET Framework kütüphaneleri, kitaplığın Windows Presentation Foundation (WPF) API 'Leri kullanması gibi tüm projeler için çalışmaz, ancak birçok taşıma senaryosunun engellemesini kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="d4282-135">Referencing .NET Framework libraries doesn't work for all projects, such as if the library uses Windows Presentation Foundation (WPF) APIs, but it does unblock many porting scenarios.</span></span>

<span data-ttu-id="d4282-136">Projenizde, [Kuban. PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections)gibi .NET Framework hedefleyen NuGet paketlerine başvurduğunuzda, aşağıdaki örneğe benzer bir paket geri dönüş Uyarısı ([NU1701](/nuget/reference/errors-and-warnings/nu1701)) alırsınız:</span><span class="sxs-lookup"><span data-stu-id="d4282-136">When you reference NuGet packages that target the .NET Framework in your project, such as [Huitian.PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections), you get a package fallback warning ([NU1701](/nuget/reference/errors-and-warnings/nu1701)) similar to the following example:</span></span>

`NU1701: Package ‘Huitian.PowerCollections 1.0.0’ was restored using ‘.NETFramework,Version=v4.6.1’ instead of the project target framework ‘.NETStandard,Version=v2.0’. This package may not be fully compatible with your project.`

<span data-ttu-id="d4282-137">Bu uyarı, paketi eklediğinizde ve bu paketi projenizle test ettiğinizden emin olmak için her oluşturduğunuzda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d4282-137">That warning is displayed when you add the package and every time you build to make sure you test that package with your project.</span></span> <span data-ttu-id="d4282-138">Projeniz beklendiği gibi çalışıyorsa, Visual Studio 'da paket özelliklerini düzenleyerek veya en sevdiğiniz kod düzenleyicinizdeki proje dosyasını el ile düzenleyerek söz konusu uyarıyı gizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4282-138">If your project is working as expected, you can suppress that warning by editing the package properties in Visual Studio or by manually editing the project file in your favorite code editor.</span></span>

<span data-ttu-id="d4282-139">Proje dosyasını düzenleyerek uyarıyı bastırmak için, uyarıyı bastırmak istediğiniz paketin `PackageReference` girdisini bulun ve `NoWarn` özniteliğini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d4282-139">To suppress the warning by editing the project file, find the `PackageReference` entry for the package you want to suppress the warning for and add the `NoWarn` attribute.</span></span> <span data-ttu-id="d4282-140">@No__t_0 öznitelik, tüm uyarı kimliklerinin virgülle ayrılmış bir listesini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="d4282-140">The `NoWarn` attribute accepts a comma-separated list of all the warning IDs.</span></span> <span data-ttu-id="d4282-141">Aşağıdaki örnek, proje dosyanızı el ile düzenleyerek `Huitian.PowerCollections` paketi için `NU1701` uyarısının nasıl bastıralınacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="d4282-141">The following example shows how to suppress the `NU1701` warning for the `Huitian.PowerCollections` package by editing your project file manually:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Huitian.PowerCollections" Version="1.0.0" NoWarn="NU1701" />
</ItemGroup>
```

<span data-ttu-id="d4282-142">Visual Studio 'da derleyici uyarılarını gösterme hakkında daha fazla bilgi için bkz. [NuGet paketleri uyarılarını gizleme](/visualstudio/ide/how-to-suppress-compiler-warnings#suppress-warnings-for-nuget-packages).</span><span class="sxs-lookup"><span data-stu-id="d4282-142">For more information on how to suppress compiler warnings in Visual Studio, see [Suppressing warnings for NuGet packages](/visualstudio/ide/how-to-suppress-compiler-warnings#suppress-warnings-for-nuget-packages).</span></span>

## <a name="port-your-packages-to-packagereference"></a><span data-ttu-id="d4282-143">Paketlerinizin `PackageReference` için bağlantı noktası</span><span class="sxs-lookup"><span data-stu-id="d4282-143">Port your packages to `PackageReference`</span></span>

<span data-ttu-id="d4282-144">.NET Core, paket bağımlılıklarını belirtmek için [Packagereference](/nuget/consume-packages/package-references-in-project-files) kullanır.</span><span class="sxs-lookup"><span data-stu-id="d4282-144">.NET Core uses [PackageReference](/nuget/consume-packages/package-references-in-project-files) to specify package dependencies.</span></span> <span data-ttu-id="d4282-145">Paketlerinizi belirtmek için [Packages. config](/nuget/reference/packages-config) kullanıyorsanız, `PackageReference` ' ye dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d4282-145">If you are using [packages.config](/nuget/reference/packages-config) to specify your packages, you will need to convert over to `PackageReference`.</span></span>

<span data-ttu-id="d4282-146">[Packages. config biçiminden PackageReference 'A geçiş](/nuget/reference/migrate-packages-config-to-package-reference)sırasında daha fazla bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4282-146">You can learn more at [Migrate from packages.config to PackageReference](/nuget/reference/migrate-packages-config-to-package-reference).</span></span>

## <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a><span data-ttu-id="d4282-147">NuGet paket bağımlılığının .NET Core üzerinde çalıştırılmadıkça yapmanız gerekenler</span><span class="sxs-lookup"><span data-stu-id="d4282-147">What to do when your NuGet package dependency doesn't run on .NET Core</span></span>

<span data-ttu-id="d4282-148">Bağlı olduğunuz bir NuGet paketi .NET Core üzerinde çalıştırılmazsa, yapabileceğiniz birkaç şey vardır:</span><span class="sxs-lookup"><span data-stu-id="d4282-148">There are a few things you can do if a NuGet package you depend on doesn't run on .NET Core:</span></span>

1. <span data-ttu-id="d4282-149">Proje açık kaynaktır ve GitHub gibi bir yerde barındırılıyorsa, geliştiricilerle doğrudan etkileşim sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4282-149">If the project is open source and hosted somewhere like GitHub, you can engage the developers directly.</span></span>
2. <span data-ttu-id="d4282-150">Yazarla doğrudan [NuGet.org](https://www.nuget.org/)üzerinde iletişim kurabilmeniz gerekir. Paketi arayın ve paketin sayfasının sol tarafındaki **kişi sahipleri** ' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d4282-150">You can contact the author directly on [nuget.org](https://www.nuget.org/). Search for the package and click **Contact Owners** on the left-hand side of the package's page.</span></span>
3. <span data-ttu-id="d4282-151">Kullandığınız paketle aynı görevi gerçekleştiren .NET Core üzerinde çalışan başka bir paket arayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4282-151">You can search for another package that runs on .NET Core that accomplishes the same task as the package you were using.</span></span>
4. <span data-ttu-id="d4282-152">Paketin kendi yaptığına yaptığı kodu yazmayı deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4282-152">You can attempt to write the code the package was doing yourself.</span></span>
5. <span data-ttu-id="d4282-153">En azından paketin uyumlu bir sürümü kullanılabilir hale gelene kadar, uygulamanızın işlevselliğini değiştirerek paketteki bağımlılığı ortadan kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4282-153">You could eliminate the dependency on the package by changing the functionality of your app, at least until a compatible version of the package becomes available.</span></span>

<span data-ttu-id="d4282-154">Açık kaynaklı proje bakım ve NuGet paket yayımcılarının genellikle gönüllü teers olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d4282-154">Remember that open-source project maintainers and NuGet package publishers are often volunteers.</span></span> <span data-ttu-id="d4282-155">Bunlar, belirli bir etki alanı hakkında ilgilendiğinden, ücretsiz olarak yaptığı ve genellikle farklı bir Daytime işi olan için katkıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="d4282-155">They contribute because they care about a given domain, do it for free, and often have a different daytime job.</span></span> <span data-ttu-id="d4282-156">Bu nedenle, .NET Core desteği istemek için onlara başvururken bu, en az bir anlayış olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d4282-156">So be mindful of that when contacting them to ask for .NET Core support.</span></span>

<span data-ttu-id="d4282-157">Yukarıdaki sorunları giderebiliyorsanız, daha sonraki bir tarihte .NET Core 'a bağlantı noktası yazmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="d4282-157">If you can't resolve your issue with any of the above, you may have to port to .NET Core at a later date.</span></span>

<span data-ttu-id="d4282-158">.NET ekibi, .NET Core ile desteklemek için hangi kitaplıkların en önemli olduğunu bilmesini istiyor.</span><span class="sxs-lookup"><span data-stu-id="d4282-158">The .NET Team would like to know which libraries are the most important to support with .NET Core.</span></span> <span data-ttu-id="d4282-159">Kullanmak istediğiniz kitaplıklar hakkında dotnet@microsoft.com bir e-posta gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4282-159">You can send an email to dotnet@microsoft.com about the libraries you'd like to use.</span></span>

## <a name="analyze-dependencies-that-arent-nuget-packages"></a><span data-ttu-id="d4282-160">NuGet paketleri olmayan bağımlılıkları analiz etme</span><span class="sxs-lookup"><span data-stu-id="d4282-160">Analyze dependencies that aren't NuGet packages</span></span>

<span data-ttu-id="d4282-161">Dosya sistemindeki DLL gibi bir NuGet paketi olmayan bir bağımlılığa sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4282-161">You may have a dependency that isn't a NuGet package, such as a DLL in the file system.</span></span> <span data-ttu-id="d4282-162">Bu bağımlılığın taşınabilirliği belirlemenin tek yolu [.net taşınabilirlik Çözümleyicisi](https://github.com/Microsoft/dotnet-apiport) aracını çalıştırmak içindir.</span><span class="sxs-lookup"><span data-stu-id="d4282-162">The only way to determine the portability of that dependency is to run the [.NET Portability Analyzer](https://github.com/Microsoft/dotnet-apiport) tool.</span></span> <span data-ttu-id="d4282-163">Araç, .NET Framework hedef olan derlemeleri çözümleyebilir ve .NET Core gibi diğer .NET platformlarına taşınmayan API 'Leri tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="d4282-163">The tool can analyze assemblies that target the .NET Framework and identify APIs that aren't portable to other .NET platforms such as .NET Core.</span></span> <span data-ttu-id="d4282-164">Aracı bir konsol uygulaması veya [Visual Studio uzantısı](../../standard/analyzers/portability-analyzer.md)olarak çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4282-164">You can run the tool as a console application or as a [Visual Studio extension](../../standard/analyzers/portability-analyzer.md).</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="d4282-165">Next</span><span class="sxs-lookup"><span data-stu-id="d4282-165">Next</span></span>](libraries.md)
