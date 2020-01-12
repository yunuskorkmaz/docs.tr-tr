---
title: .NET Core için csproj biçimine eklemeler
description: Mevcut ve .NET Core csproj dosyaları arasındaki farklılıklar hakkında bilgi edinin
ms.date: 04/08/2019
ms.openlocfilehash: 4a05709da63c4f6a200039ba5dd59358c700130e
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899877"
---
# <a name="additions-to-the-csproj-format-for-net-core"></a><span data-ttu-id="b148c-103">.NET Core için csproj biçimine eklemeler</span><span class="sxs-lookup"><span data-stu-id="b148c-103">Additions to the csproj format for .NET Core</span></span>

<span data-ttu-id="b148c-104">Bu belge, Project *. JSON* 'dan *csproj* ve [MSBuild](https://github.com/Microsoft/MSBuild)'e geçiş kapsamında proje dosyalarına eklenen değişiklikleri özetler.</span><span class="sxs-lookup"><span data-stu-id="b148c-104">This document outlines the changes that were added to the project files as part of the move from *project.json* to *csproj* and [MSBuild](https://github.com/Microsoft/MSBuild).</span></span> <span data-ttu-id="b148c-105">Genel proje dosyası sözdizimi ve başvurusu hakkında daha fazla bilgi için bkz. [MSBuild proje dosyası](/visualstudio/msbuild/msbuild-project-file-schema-reference) belgeleri.</span><span class="sxs-lookup"><span data-stu-id="b148c-105">For more information about general project file syntax and reference, see [the MSBuild project file](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation.</span></span>

## <a name="implicit-package-references"></a><span data-ttu-id="b148c-106">Örtük paket başvuruları</span><span class="sxs-lookup"><span data-stu-id="b148c-106">Implicit package references</span></span>

<span data-ttu-id="b148c-107">Meta paketlere, proje dosyanızın `<TargetFramework>` veya `<TargetFrameworks>` özelliğinde belirtilen hedef çatılar temelinde örtülü olarak başvurulur.</span><span class="sxs-lookup"><span data-stu-id="b148c-107">Metapackages are implicitly referenced based on the target framework(s) specified in the `<TargetFramework>` or `<TargetFrameworks>` property of your project file.</span></span> <span data-ttu-id="b148c-108">`<TargetFramework>` belirtilmişse `<TargetFrameworks>` yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="b148c-108">`<TargetFrameworks>` is ignored if `<TargetFramework>` is specified, independent of order.</span></span> <span data-ttu-id="b148c-109">Daha fazla bilgi için bkz. [paketler, Metapackages ve çerçeveler](../packages.md).</span><span class="sxs-lookup"><span data-stu-id="b148c-109">For more information, see [Packages, metapackages and frameworks](../packages.md).</span></span> 

```xml
 <PropertyGroup>
   <TargetFramework>netcoreapp2.1</TargetFramework>
 </PropertyGroup>
 ```

 ```xml
 <PropertyGroup>
   <TargetFrameworks>netcoreapp2.1;net462</TargetFrameworks>
 </PropertyGroup>
 ```

### <a name="recommendations"></a><span data-ttu-id="b148c-110">Öneriler</span><span class="sxs-lookup"><span data-stu-id="b148c-110">Recommendations</span></span>

<span data-ttu-id="b148c-111">`Microsoft.NETCore.App` veya `NETStandard.Library` metapaketlerine örtük olarak başvurulduğundan, önerilen en iyi yöntemler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b148c-111">Since `Microsoft.NETCore.App` or `NETStandard.Library` metapackages are implicitly referenced, the following are our recommended best practices:</span></span>

- <span data-ttu-id="b148c-112">.NET Core veya .NET Standard hedeflenirken, proje dosyanızdaki bir `<PackageReference>` öğe aracılığıyla `Microsoft.NETCore.App` veya `NETStandard.Library` metapaketlerine açık bir başvuruya sahip olmaz.</span><span class="sxs-lookup"><span data-stu-id="b148c-112">When targeting .NET Core or .NET Standard, never have an explicit reference to the `Microsoft.NETCore.App` or `NETStandard.Library` metapackages via a `<PackageReference>` item in your project file.</span></span>
- <span data-ttu-id="b148c-113">.NET Core 'u hedeflerken çalışma zamanının belirli bir sürümüne ihtiyacınız varsa, metapackage 'e başvurmak yerine projenizdeki `<RuntimeFrameworkVersion>` özelliğini (örneğin, `1.0.4`) kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b148c-113">If you need a specific version of the runtime when targeting .NET Core, you should use the `<RuntimeFrameworkVersion>` property in your project (for example, `1.0.4`) instead of referencing the metapackage.</span></span>
  - <span data-ttu-id="b148c-114">Bu, [kendi kendine kapsanan dağıtımlar](../deploying/index.md#self-contained-deployments-scd) kullanıyorsanız ve örneğin 1.0.0 LTS çalışma zamanının belirli bir düzeltme eki sürümüne ihtiyaç duyuyorsanız meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="b148c-114">This might happen if you are using [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) and you need a specific patch version of 1.0.0 LTS runtime, for example.</span></span>
- <span data-ttu-id="b148c-115">.NET Standard hedef alırken `NETStandard.Library` metapackage belirli bir sürümüne ihtiyacınız varsa `<NetStandardImplicitPackageVersion>` özelliğini kullanabilir ve ihtiyacınız olan sürümü ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b148c-115">If you need a specific version of the `NETStandard.Library` metapackage when targeting .NET Standard, you can use the `<NetStandardImplicitPackageVersion>` property and set the version you need.</span></span>
- <span data-ttu-id="b148c-116">.NET Framework projelerindeki `Microsoft.NETCore.App` ya da `NETStandard.Library` metapackage 'e açıkça başvuru eklemeyin veya güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="b148c-116">Don't explicitly add or update references to either the `Microsoft.NETCore.App` or `NETStandard.Library` metapackage in .NET Framework projects.</span></span> <span data-ttu-id="b148c-117">.NET Standard tabanlı bir NuGet paketi kullanılırken `NETStandard.Library` herhangi bir sürümü gerekliyse, NuGet bu sürümü otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="b148c-117">If any version of `NETStandard.Library` is needed when using a .NET Standard-based NuGet package, NuGet automatically installs that version.</span></span>

## <a name="implicit-version-for-some-package-references"></a><span data-ttu-id="b148c-118">Bazı paket başvurularının örtük sürümü</span><span class="sxs-lookup"><span data-stu-id="b148c-118">Implicit version for some package references</span></span>

<span data-ttu-id="b148c-119">[`<PackageReference>`](#packagereference) çoğu kullanımları, kullanılacak NuGet paketi sürümünü belirtmek için `Version` özniteliğini ayarlamayı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b148c-119">Most usages of [`<PackageReference>`](#packagereference) require setting the `Version` attribute to specify the NuGet package version to be used.</span></span> <span data-ttu-id="b148c-120">.NET Core 2,1 veya 2,2 kullanırken ve [Microsoft. aspnetcore. app](/aspnet/core/fundamentals/metapackage-app) ya da [Microsoft. Aspnetcore. All](/aspnet/core/fundamentals/metapackage)ile başvurulduğunda öznitelik gereksizdir.</span><span class="sxs-lookup"><span data-stu-id="b148c-120">When using .NET Core 2.1 or 2.2 and referencing [Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage-app) or [Microsoft.AspNetCore.All](/aspnet/core/fundamentals/metapackage), however, the  attribute is unnecessary.</span></span> <span data-ttu-id="b148c-121">.NET Core SDK, bu paketlerin kullanılması gereken sürümünü otomatik olarak seçebilir.</span><span class="sxs-lookup"><span data-stu-id="b148c-121">The .NET Core SDK can automatically select the version of these packages that should be used.</span></span>

### <a name="recommendation"></a><span data-ttu-id="b148c-122">Öneri</span><span class="sxs-lookup"><span data-stu-id="b148c-122">Recommendation</span></span>

<span data-ttu-id="b148c-123">`Microsoft.AspNetCore.App` veya `Microsoft.AspNetCore.All` paketlerine başvurulduğunda, sürümünü belirtmeyin.</span><span class="sxs-lookup"><span data-stu-id="b148c-123">When referencing the `Microsoft.AspNetCore.App` or `Microsoft.AspNetCore.All` packages, do not specify their version.</span></span> <span data-ttu-id="b148c-124">Bir sürüm belirtilmişse, SDK uyarı NETSDK1071 üretebilir.</span><span class="sxs-lookup"><span data-stu-id="b148c-124">If a version is specified, the SDK may produce warning NETSDK1071.</span></span> <span data-ttu-id="b148c-125">Bu uyarıyı onarmak için aşağıdaki örnekteki gibi paket sürümünü kaldırın:</span><span class="sxs-lookup"><span data-stu-id="b148c-125">To fix this warning, remove the package version like in the following example:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.AspNetCore.App" />
</ItemGroup>
```

> <span data-ttu-id="b148c-126">Bilinen sorun: .NET Core 2,1 SDK 'Sı yalnızca proje Microsoft. NET. SDK. Web 'i kullandığında bu söz dizimini destekliyordu.</span><span class="sxs-lookup"><span data-stu-id="b148c-126">Known issue: the .NET Core 2.1 SDK only supported this syntax when the project also uses Microsoft.NET.Sdk.Web.</span></span> <span data-ttu-id="b148c-127">Bu, .NET Core 2,2 SDK 'sında çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="b148c-127">This is resolved in the .NET Core 2.2 SDK.</span></span>

<span data-ttu-id="b148c-128">ASP.NET Core metapaketlerine yapılan bu başvuruların çoğu normal NuGet paketlerinden biraz farklı bir davranışı vardır.</span><span class="sxs-lookup"><span data-stu-id="b148c-128">These references to ASP.NET Core metapackages have a slightly different behavior from most normal NuGet packages.</span></span> <span data-ttu-id="b148c-129">Bu metapaketleri kullanan uygulamaların [çerçeveye bağımlı dağıtımları](../deploying/index.md#framework-dependent-deployments-fdd) ASP.NET Core paylaşılan çerçeveden otomatik olarak yararlanır.</span><span class="sxs-lookup"><span data-stu-id="b148c-129">[Framework-dependent deployments](../deploying/index.md#framework-dependent-deployments-fdd) of applications that use these metapackages automatically take advantage of the ASP.NET Core shared framework.</span></span> <span data-ttu-id="b148c-130">Meta paketleri kullandığınızda başvurulan ASP.NET Core NuGet paketlerinden **hiçbir** varlık uygulamayla birlikte dağıtılır — ASP.NET Core paylaşılan çerçeve bu varlıkları içerir.</span><span class="sxs-lookup"><span data-stu-id="b148c-130">When you use the metapackages, **no** assets from the referenced ASP.NET Core NuGet packages are deployed with the application—the ASP.NET Core shared framework contains these assets.</span></span> <span data-ttu-id="b148c-131">Paylaşılan çerçevede bulunan varlıklar, uygulama başlatma süresini artırmak üzere hedef platform için iyileştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b148c-131">The assets in the shared framework are optimized for the target platform to improve application startup time.</span></span> <span data-ttu-id="b148c-132">Paylaşılan Framework hakkında daha fazla bilgi için bkz. [.NET Core dağıtım paketleme](../build/distribution-packaging.md).</span><span class="sxs-lookup"><span data-stu-id="b148c-132">For more information about shared framework, see [.NET Core distribution packaging](../build/distribution-packaging.md).</span></span>

<span data-ttu-id="b148c-133">Bir *Sürüm belirtilmişse* , çerçeveye bağımlı dağıtımlar için ASP.NET Core paylaşılan Framework 'ün *En düşük* sürümü ve kendi içinde olan dağıtımlar için *tam* sürüm olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="b148c-133">If a version *is* specified, it's treated as the *minimum* version of ASP.NET Core shared framework for framework-dependent deployments and as an *exact* version for self-contained deployments.</span></span> <span data-ttu-id="b148c-134">Bu, aşağıdaki sonuçlara sahip olabilir:</span><span class="sxs-lookup"><span data-stu-id="b148c-134">This can have the following consequences:</span></span>

- <span data-ttu-id="b148c-135">Sunucuda yüklü ASP.NET Core sürümü, PackageReference üzerinde belirtilen sürümden küçükse .NET Core işlemi başlayamaz.</span><span class="sxs-lookup"><span data-stu-id="b148c-135">If the version of ASP.NET Core installed on the server is less than the version specified on the PackageReference, the .NET Core process fails to launch.</span></span> <span data-ttu-id="b148c-136">Metapackage güncelleştirmeleri, Azure gibi barındırma ortamlarında güncelleştirmeler kullanılabilir hale getirilinceye kadar sıklıkla NuGet.org üzerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b148c-136">Updates to the metapackage are often available on NuGet.org before updates have been made available in hosting environments such as Azure.</span></span> <span data-ttu-id="b148c-137">PackageReference üzerindeki sürümün ASP.NET Core güncelleştirilmesi, dağıtılan bir uygulamanın başarısız olmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="b148c-137">Updating the version on the PackageReference to ASP.NET Core could cause a deployed application to fail.</span></span>
- <span data-ttu-id="b148c-138">Uygulama [kendi içindeki bir dağıtım](../deploying/index.md#self-contained-deployments-scd)olarak dağıtılırsa, uygulama .NET Core için en son güvenlik güncelleştirmelerini içermeyebilir.</span><span class="sxs-lookup"><span data-stu-id="b148c-138">If the application is deployed as a [self-contained deployment](../deploying/index.md#self-contained-deployments-scd), the application may not contain the latest security updates to .NET Core.</span></span> <span data-ttu-id="b148c-139">Bir sürüm belirtilmediğinde, SDK otomatik olarak kapsanan dağıtıma en yeni ASP.NET Core sürümünü ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="b148c-139">When a version isn't specified, the SDK can automatically include the newest version of ASP.NET Core in the self-contained deployment.</span></span>

## <a name="default-compilation-includes-in-net-core-projects"></a><span data-ttu-id="b148c-140">.NET Core projelerinde varsayılan derleme dahildir</span><span class="sxs-lookup"><span data-stu-id="b148c-140">Default compilation includes in .NET Core projects</span></span>

<span data-ttu-id="b148c-141">En son SDK sürümlerindeki *csproj* biçimine geçiş ile, derleme öğeleri ve katıştırılmış kaynaklar için varsayılan ekleme ve DıŞMALARı SDK Özellikler dosyalarına taşıdık.</span><span class="sxs-lookup"><span data-stu-id="b148c-141">With the move to the *csproj* format in the latest SDK versions, we've moved the default includes and excludes for compile items and embedded resources to the SDK properties files.</span></span> <span data-ttu-id="b148c-142">Bu, artık proje dosyanızda bu öğeleri belirtmeniz gerekmediği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b148c-142">This means that you no longer need to specify these items in your project file.</span></span>

<span data-ttu-id="b148c-143">Bunu yapmanın asıl nedeni, proje dosyanızdaki dağınıklığı azaltmaktır.</span><span class="sxs-lookup"><span data-stu-id="b148c-143">The main reason for doing this is to reduce the clutter in your project file.</span></span> <span data-ttu-id="b148c-144">SDK 'da bulunan varsayılanlar en yaygın kullanım durumlarını kapsamalıdır, bu nedenle bunları oluşturduğunuz her projede tekrarlamaya gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="b148c-144">The defaults that are present in the SDK should cover most common use cases, so there is no need to repeat them in every project that you create.</span></span> <span data-ttu-id="b148c-145">Bu, anlaşılması çok daha kolay olan daha küçük proje dosyalarına ve gerekirse el ile düzenlemeye yol açar.</span><span class="sxs-lookup"><span data-stu-id="b148c-145">This leads to smaller project files that are much easier to understand as well as edit by hand, if needed.</span></span>

<span data-ttu-id="b148c-146">Aşağıdaki tabloda, SDK 'nın hangi öğesi ve hangi [genelleştirmeler](https://en.wikipedia.org/wiki/Glob_(programming)) dahil olduğu ve hangilerinin hariç olduğu gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="b148c-146">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are both included and excluded in the SDK:</span></span>

| <span data-ttu-id="b148c-147">Öğe</span><span class="sxs-lookup"><span data-stu-id="b148c-147">Element</span></span>           | <span data-ttu-id="b148c-148">Glob 'yi dahil et</span><span class="sxs-lookup"><span data-stu-id="b148c-148">Include glob</span></span>                              | <span data-ttu-id="b148c-149">Glob 'yi hariç tut</span><span class="sxs-lookup"><span data-stu-id="b148c-149">Exclude glob</span></span>                                                  | <span data-ttu-id="b148c-150">Glob 'yi kaldır</span><span class="sxs-lookup"><span data-stu-id="b148c-150">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| <span data-ttu-id="b148c-151">Derleme</span><span class="sxs-lookup"><span data-stu-id="b148c-151">Compile</span></span>           | <span data-ttu-id="b148c-152">\*\*/\*. cs (veya diğer dil uzantıları)</span><span class="sxs-lookup"><span data-stu-id="b148c-152">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="b148c-153">\*\*/\*. Kullanıcı;  \*\*/\*.\*PROJ;  \*\*/\*. sln;  \*\*/\*. vssscc</span><span class="sxs-lookup"><span data-stu-id="b148c-153">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="b148c-154">YOK</span><span class="sxs-lookup"><span data-stu-id="b148c-154">N/A</span></span>                      |
| <span data-ttu-id="b148c-155">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="b148c-155">EmbeddedResource</span></span>  | <span data-ttu-id="b148c-156">\*\*/\*. resx</span><span class="sxs-lookup"><span data-stu-id="b148c-156">\*\*/\*.resx</span></span>                              | <span data-ttu-id="b148c-157">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="b148c-157">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="b148c-158">YOK</span><span class="sxs-lookup"><span data-stu-id="b148c-158">N/A</span></span>                      |
| <span data-ttu-id="b148c-159">Yok.</span><span class="sxs-lookup"><span data-stu-id="b148c-159">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="b148c-160">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="b148c-160">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="b148c-161">\*\*/\*.cs; \*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="b148c-161">\*\*/\*.cs; \*\*/\*.resx</span></span>   |

> [!NOTE]
> <span data-ttu-id="b148c-162">**Exclude glob** always excludes the `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, respectively.</span><span class="sxs-lookup"><span data-stu-id="b148c-162">**Exclude glob** always excludes the `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, respectively.</span></span> <span data-ttu-id="b148c-163">As a whole, all excludes are represented by `$(DefaultItemExcludes)`.</span><span class="sxs-lookup"><span data-stu-id="b148c-163">As a whole, all excludes are represented by `$(DefaultItemExcludes)`.</span></span>

<span data-ttu-id="b148c-164">If you have globs in your project and you try to build it using the newest SDK, you'll get the following error:</span><span class="sxs-lookup"><span data-stu-id="b148c-164">If you have globs in your project and you try to build it using the newest SDK, you'll get the following error:</span></span>

> <span data-ttu-id="b148c-165">Duplicate Compile items were included.</span><span class="sxs-lookup"><span data-stu-id="b148c-165">Duplicate Compile items were included.</span></span> <span data-ttu-id="b148c-166">The .NET SDK includes Compile items from your project directory by default.</span><span class="sxs-lookup"><span data-stu-id="b148c-166">The .NET SDK includes Compile items from your project directory by default.</span></span> <span data-ttu-id="b148c-167">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span><span class="sxs-lookup"><span data-stu-id="b148c-167">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

<span data-ttu-id="b148c-168">In order to get around this error, you can either remove the explicit `Compile` items that match the ones listed on the previous table, or you can set the `<EnableDefaultCompileItems>` property to `false`, like this:</span><span class="sxs-lookup"><span data-stu-id="b148c-168">In order to get around this error, you can either remove the explicit `Compile` items that match the ones listed on the previous table, or you can set the `<EnableDefaultCompileItems>` property to `false`, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

<span data-ttu-id="b148c-169">Setting this property to `false` will disable implicit inclusion, reverting to the behavior of previous SDKs where you had to specify the default globs in your project.</span><span class="sxs-lookup"><span data-stu-id="b148c-169">Setting this property to `false` will disable implicit inclusion, reverting to the behavior of previous SDKs where you had to specify the default globs in your project.</span></span>

<span data-ttu-id="b148c-170">This change does not modify the main mechanics of other includes.</span><span class="sxs-lookup"><span data-stu-id="b148c-170">This change does not modify the main mechanics of other includes.</span></span> <span data-ttu-id="b148c-171">However, if you wish to specify, for example, some files to get published with your app, you can still use the known mechanisms in *csproj* for that (for example, the `<Content>` element).</span><span class="sxs-lookup"><span data-stu-id="b148c-171">However, if you wish to specify, for example, some files to get published with your app, you can still use the known mechanisms in *csproj* for that (for example, the `<Content>` element).</span></span>

<span data-ttu-id="b148c-172">`<EnableDefaultCompileItems>` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob, which also applies to \*.cs items.</span><span class="sxs-lookup"><span data-stu-id="b148c-172">`<EnableDefaultCompileItems>` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob, which also applies to \*.cs items.</span></span> <span data-ttu-id="b148c-173">Because of that, **Solution Explorer** will continue show \*.cs items as part of the project, included as `None` items.</span><span class="sxs-lookup"><span data-stu-id="b148c-173">Because of that, **Solution Explorer** will continue show \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="b148c-174">In a similar way, you can set `<EnableDefaultNoneItems>` to false to disable the implicit `None` glob, like this:</span><span class="sxs-lookup"><span data-stu-id="b148c-174">In a similar way, you can set `<EnableDefaultNoneItems>` to false to disable the implicit `None` glob, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

<span data-ttu-id="b148c-175">To disable **all implicit globs**, you can set the `<EnableDefaultItems>` property to `false` as in the following example:</span><span class="sxs-lookup"><span data-stu-id="b148c-175">To disable **all implicit globs**, you can set the `<EnableDefaultItems>` property to `false` as in the following example:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a><span data-ttu-id="b148c-176">How to see the whole project as MSBuild sees it</span><span class="sxs-lookup"><span data-stu-id="b148c-176">How to see the whole project as MSBuild sees it</span></span>

<span data-ttu-id="b148c-177">While those csproj changes greatly simplify project files, you might want to see the fully expanded project as MSBuild sees it once the SDK and its targets are included.</span><span class="sxs-lookup"><span data-stu-id="b148c-177">While those csproj changes greatly simplify project files, you might want to see the fully expanded project as MSBuild sees it once the SDK and its targets are included.</span></span> <span data-ttu-id="b148c-178">Preprocess the project with [the `/pp` switch](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) of the [`dotnet msbuild`](dotnet-msbuild.md) command, which shows which files are imported, their sources, and their contributions to the build without actually building the project:</span><span class="sxs-lookup"><span data-stu-id="b148c-178">Preprocess the project with [the `/pp` switch](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) of the [`dotnet msbuild`](dotnet-msbuild.md) command, which shows which files are imported, their sources, and their contributions to the build without actually building the project:</span></span>

`dotnet msbuild -pp:fullproject.xml`

<span data-ttu-id="b148c-179">Projede birden çok hedef çerçeve varsa, komutun sonuçları MSBuild özelliği olarak belirtilerek yalnızca birine odaklanmalıdır:</span><span class="sxs-lookup"><span data-stu-id="b148c-179">If the project has multiple target frameworks, the results of the command should be focused on only one of them by specifying it as an MSBuild property:</span></span>

`dotnet msbuild -p:TargetFramework=netcoreapp2.0 -pp:fullproject.xml`

## <a name="additions"></a><span data-ttu-id="b148c-180">Üzerine</span><span class="sxs-lookup"><span data-stu-id="b148c-180">Additions</span></span>

### <a name="sdk-attribute"></a><span data-ttu-id="b148c-181">SDK özniteliği</span><span class="sxs-lookup"><span data-stu-id="b148c-181">Sdk attribute</span></span>

<span data-ttu-id="b148c-182">*. Csproj* dosyasının kök `<Project>` öğesi `Sdk`adlı yeni bir özniteliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="b148c-182">The root `<Project>` element of the *.csproj* file has a new attribute called `Sdk`.</span></span> <span data-ttu-id="b148c-183">`Sdk`, proje tarafından hangi SDK 'nın kullanılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b148c-183">`Sdk` specifies which SDK will be used by the project.</span></span> <span data-ttu-id="b148c-184">[Katman, katmanlama belgesinde](cli-msbuild-architecture.md) açıklandığı gibi, .NET Core kodu oluşturabileceğiniz MSBuild [görevleri](/visualstudio/msbuild/msbuild-tasks) ve [hedefleri](/visualstudio/msbuild/msbuild-targets) kümesidir.</span><span class="sxs-lookup"><span data-stu-id="b148c-184">The SDK, as the [layering document](cli-msbuild-architecture.md) describes, is a set of MSBuild [tasks](/visualstudio/msbuild/msbuild-tasks) and [targets](/visualstudio/msbuild/msbuild-targets) that can build .NET Core code.</span></span> <span data-ttu-id="b148c-185">.NET Core için aşağıdaki SDK 'lar mevcuttur:</span><span class="sxs-lookup"><span data-stu-id="b148c-185">The following SDKs are available for .NET Core:</span></span>

1. <span data-ttu-id="b148c-186">`Microsoft.NET.Sdk` KIMLIĞINE sahip .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="b148c-186">The .NET Core SDK with the ID of `Microsoft.NET.Sdk`</span></span>
2. <span data-ttu-id="b148c-187">`Microsoft.NET.Sdk.Web` KIMLIKLI .NET Core Web SDK 'Sı</span><span class="sxs-lookup"><span data-stu-id="b148c-187">The .NET Core web SDK with the ID of `Microsoft.NET.Sdk.Web`</span></span>
3. <span data-ttu-id="b148c-188">`Microsoft.NET.Sdk.Razor` KIMLIKLI .NET Core Razor sınıf kitaplığı SDK 'Sı</span><span class="sxs-lookup"><span data-stu-id="b148c-188">The .NET Core Razor Class Library SDK with the ID of `Microsoft.NET.Sdk.Razor`</span></span>
4. <span data-ttu-id="b148c-189">KIMLIĞI `Microsoft.NET.Sdk.Worker` olan .NET Core Worker hizmeti (.NET Core 3,0 ' den itibaren)</span><span class="sxs-lookup"><span data-stu-id="b148c-189">The .NET Core Worker Service with the ID of `Microsoft.NET.Sdk.Worker` (since .NET Core 3.0)</span></span>
5. <span data-ttu-id="b148c-190">`Microsoft.NET.Sdk.WindowsDesktop` KIMLIKLI .NET Core WinForms ve WPF (.NET Core 3,0 ' den itibaren)</span><span class="sxs-lookup"><span data-stu-id="b148c-190">The .NET Core WinForms and WPF with the ID of `Microsoft.NET.Sdk.WindowsDesktop` (since .NET Core 3.0)</span></span>

<span data-ttu-id="b148c-191">.NET Core araçları 'nı kullanabilmeniz ve kodunuzu derlemek için `<Project>` öğesindeki bu kimliklerden birine ayarlanmış `Sdk` özniteliğine sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b148c-191">You need to have the `Sdk` attribute set to one of those IDs on the `<Project>` element in order to use the .NET Core tools and build your code.</span></span>

### <a name="packagereference"></a><span data-ttu-id="b148c-192">PackageReference</span><span class="sxs-lookup"><span data-stu-id="b148c-192">PackageReference</span></span>

<span data-ttu-id="b148c-193">`<PackageReference>` item öğesi [, projede bir NuGet bağımlılığı](/nuget/consume-packages/package-references-in-project-files)belirtir.</span><span class="sxs-lookup"><span data-stu-id="b148c-193">A `<PackageReference>` item element specifies a [NuGet dependency in the project](/nuget/consume-packages/package-references-in-project-files).</span></span> <span data-ttu-id="b148c-194">`Include` özniteliği paket KIMLIĞINI belirtir.</span><span class="sxs-lookup"><span data-stu-id="b148c-194">The `Include` attribute specifies the package ID.</span></span>

```xml
<PackageReference Include="<package-id>" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a><span data-ttu-id="b148c-195">Sürüm</span><span class="sxs-lookup"><span data-stu-id="b148c-195">Version</span></span>

<span data-ttu-id="b148c-196">Gerekli `Version` özniteliği geri yüklenecek paketin sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="b148c-196">The required `Version` attribute specifies the version of the package to restore.</span></span> <span data-ttu-id="b148c-197">Öznitelik, [NuGet sürüm oluşturma](/nuget/reference/package-versioning#version-ranges-and-wildcards) şemasının kurallarına uyar.</span><span class="sxs-lookup"><span data-stu-id="b148c-197">The attribute respects the rules of the [NuGet versioning](/nuget/reference/package-versioning#version-ranges-and-wildcards) scheme.</span></span> <span data-ttu-id="b148c-198">Varsayılan davranış, tam bir sürüm eşleşmedir.</span><span class="sxs-lookup"><span data-stu-id="b148c-198">The default behavior is an exact version match.</span></span> <span data-ttu-id="b148c-199">Örneğin, `Version="1.2.3"` belirtilmesi, paketin tam 1.2.3 sürümü için NuGet gösterimi `[1.2.3]` eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="b148c-199">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

#### <a name="includeassets-excludeassets-and-privateassets"></a><span data-ttu-id="b148c-200">Includevarlıklarını, Excludevarlıklarını ve Privatevarlıkları</span><span class="sxs-lookup"><span data-stu-id="b148c-200">IncludeAssets, ExcludeAssets and PrivateAssets</span></span>

<span data-ttu-id="b148c-201">`IncludeAssets` öznitelik, `<PackageReference>` tarafından belirtilen pakete ait olan varlıkların tüketilmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b148c-201">`IncludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed.</span></span> <span data-ttu-id="b148c-202">Varsayılan olarak, tüm paket varlıkları dahil edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b148c-202">By default, all package assets are included.</span></span>

<span data-ttu-id="b148c-203">`ExcludeAssets` öznitelik, `<PackageReference>` tarafından belirtilen pakete ait olan varlıkların tüketilmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b148c-203">`ExcludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should not be consumed.</span></span>

<span data-ttu-id="b148c-204">`PrivateAssets` öznitelik, `<PackageReference>` tarafından belirtilen pakete ait olan varlıkların tüketilmesi ancak bir sonraki projede akolmaması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b148c-204">`PrivateAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed but not flow to the next project.</span></span> <span data-ttu-id="b148c-205">`Analyzers`, `Build` ve `ContentFiles` varlıkları bu öznitelik mevcut olmadığında varsayılan olarak özeldir.</span><span class="sxs-lookup"><span data-stu-id="b148c-205">The `Analyzers`, `Build` and `ContentFiles` assets are private by default when this attribute is not present.</span></span>

> [!NOTE]
> <span data-ttu-id="b148c-206">`PrivateAssets`, *Project. json*/*xproj* `SuppressParent` öğesi ile eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="b148c-206">`PrivateAssets` is equivalent to the *project.json*/*xproj* `SuppressParent` element.</span></span>

<span data-ttu-id="b148c-207">Bu öznitelikler, birden fazla listeleniyorsa noktalı virgül `;` karakteriyle ayrılmış aşağıdaki öğelerden bir veya daha fazlasını içerebilir:</span><span class="sxs-lookup"><span data-stu-id="b148c-207">These attributes can contain one or more of the following items, separated by the semicolon `;` character if more than one is listed:</span></span>

- <span data-ttu-id="b148c-208">`Compile` – *LIB* klasörünün içeriği, derleme için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b148c-208">`Compile` – the contents of the *lib* folder are available to compile against.</span></span>
- <span data-ttu-id="b148c-209">`Runtime`: *çalışma zamanı* klasörünün içeriği dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="b148c-209">`Runtime` – the contents of the *runtime* folder are distributed.</span></span>
- <span data-ttu-id="b148c-210">`ContentFiles`: *ContentFiles* klasörünün içeriği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b148c-210">`ContentFiles` – the contents of the *contentfiles* folder are used.</span></span>
- <span data-ttu-id="b148c-211">`Build` – *Build* klasöründeki props/targets kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b148c-211">`Build` – the props/targets in the *build* folder are used.</span></span>
- <span data-ttu-id="b148c-212">`Native`: yerel varlıklardan içerik çalışma zamanı için *Çıkış* klasörüne kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="b148c-212">`Native` – the contents from native assets are copied to the *output* folder for runtime.</span></span>
- <span data-ttu-id="b148c-213">`Analyzers` – çözümleyiciler kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b148c-213">`Analyzers` – the analyzers are used.</span></span>

<span data-ttu-id="b148c-214">Alternatif olarak, öznitelik şunları içerebilir:</span><span class="sxs-lookup"><span data-stu-id="b148c-214">Alternatively, the attribute can contain:</span></span>

- <span data-ttu-id="b148c-215">`None` – varlıkların hiçbiri kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="b148c-215">`None` – none of the assets are used.</span></span>
- <span data-ttu-id="b148c-216">`All` – tüm varlıklar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b148c-216">`All` – all assets are used.</span></span>

### <a name="dotnetclitoolreference"></a><span data-ttu-id="b148c-217">Dotnetclientoolreference</span><span class="sxs-lookup"><span data-stu-id="b148c-217">DotNetCliToolReference</span></span>

<span data-ttu-id="b148c-218">`<DotNetCliToolReference>` item öğesi, kullanıcının proje bağlamında geri yüklemek istediği CLı aracını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b148c-218">A `<DotNetCliToolReference>` item element specifies the CLI tool that the user wants to restore in the context of the project.</span></span> <span data-ttu-id="b148c-219">*Project. JSON*içindeki `tools` düğümünün yerini alır.</span><span class="sxs-lookup"><span data-stu-id="b148c-219">It's a replacement for the `tools` node in *project.json*.</span></span>

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

<span data-ttu-id="b148c-220">`DotNetCliToolReference` artık [.NET Core yerel araçlarının](https://aka.ms/local-tools)yararına [kullanım dışı](https://github.com/dotnet/announcements/issues/107) olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b148c-220">Note that `DotNetCliToolReference` is [now deprecated](https://github.com/dotnet/announcements/issues/107) in favor of [.NET Core Local Tools](https://aka.ms/local-tools).</span></span>

#### <a name="version"></a><span data-ttu-id="b148c-221">Sürüm</span><span class="sxs-lookup"><span data-stu-id="b148c-221">Version</span></span>

<span data-ttu-id="b148c-222">`Version` geri yüklenecek paketin sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="b148c-222">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="b148c-223">Öznitelik, [NuGet sürüm oluşturma](/nuget/create-packages/dependency-versions#version-ranges) şemasının kurallarına uyar.</span><span class="sxs-lookup"><span data-stu-id="b148c-223">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="b148c-224">Varsayılan davranış, tam bir sürüm eşleşmedir.</span><span class="sxs-lookup"><span data-stu-id="b148c-224">The default behavior is an exact version match.</span></span> <span data-ttu-id="b148c-225">Örneğin, `Version="1.2.3"` belirtilmesi, paketin tam 1.2.3 sürümü için NuGet gösterimi `[1.2.3]` eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="b148c-225">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

### <a name="runtimeidentifiers"></a><span data-ttu-id="b148c-226">Runtimetanımlayıcıtanımlayıcıları</span><span class="sxs-lookup"><span data-stu-id="b148c-226">RuntimeIdentifiers</span></span>

<span data-ttu-id="b148c-227">`<RuntimeIdentifiers>` Property öğesi, proje için bir [çalışma zamanı tanımlayıcıları (RID 'ler)](../rid-catalog.md) için noktalı virgülle ayrılmış bir liste belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="b148c-227">The `<RuntimeIdentifiers>` property element lets you specify a semicolon-delimited list of [Runtime Identifiers (RIDs)](../rid-catalog.md) for the project.</span></span>
<span data-ttu-id="b148c-228">RID 'Ler, kendi kendine kapsanan dağıtımları yayımlamayı etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="b148c-228">RIDs enable publishing self-contained deployments.</span></span>

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a><span data-ttu-id="b148c-229">Runtimeıdentifier</span><span class="sxs-lookup"><span data-stu-id="b148c-229">RuntimeIdentifier</span></span>

<span data-ttu-id="b148c-230">`<RuntimeIdentifier>` Property öğesi, proje için yalnızca bir [çalışma zamanı tanımlayıcısı (RID)](../rid-catalog.md) belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="b148c-230">The `<RuntimeIdentifier>` property element allows you to specify only one [Runtime Identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="b148c-231">RID, kendi kendine içerilen bir dağıtımı yayımlamayı mümkün.</span><span class="sxs-lookup"><span data-stu-id="b148c-231">The RID enables publishing a self-contained deployment.</span></span>

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

<span data-ttu-id="b148c-232">Birden çok çalışma zamanı için yayımlamanız gerekiyorsa bunun yerine `<RuntimeIdentifiers>` (plural) kullanın.</span><span class="sxs-lookup"><span data-stu-id="b148c-232">Use `<RuntimeIdentifiers>` (plural) instead if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="b148c-233">`<RuntimeIdentifier>`, yalnızca tek bir çalışma zamanı gerektiğinde daha hızlı derlemeler sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="b148c-233">`<RuntimeIdentifier>` can provide faster builds when only a single runtime is required.</span></span>

### <a name="packagetargetfallback"></a><span data-ttu-id="b148c-234">PackageTargetFallback</span><span class="sxs-lookup"><span data-stu-id="b148c-234">PackageTargetFallback</span></span>

<span data-ttu-id="b148c-235">`<PackageTargetFallback>` Property öğesi, paketler geri yüklenirken kullanılacak bir dizi uyumlu hedef belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="b148c-235">The `<PackageTargetFallback>` property element allows you to specify a set of compatible targets to be used when restoring packages.</span></span> <span data-ttu-id="b148c-236">DotNet [TXE (hedef x takma adı)](/nuget/schema/target-frameworks) kullanan paketlere bir DotNet TXD bildirmeyin paketlerle çalışmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="b148c-236">It's designed to allow packages that use the dotnet [TxM (Target x Moniker)](/nuget/schema/target-frameworks) to operate with packages that don't declare a dotnet TxM.</span></span> <span data-ttu-id="b148c-237">Projeniz DotNet TXI kullanıyorsa, DotNet olmayan platformların DotNet ile uyumlu olmasına izin vermek için `<PackageTargetFallback>` projenize eklemediğiniz tüm paketlerin DotNet TXD olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b148c-237">If your project uses the dotnet TxM, then all the packages it depends on must also have a dotnet TxM, unless you add the `<PackageTargetFallback>` to your project in order to allow non-dotnet platforms to be compatible with dotnet.</span></span>

<span data-ttu-id="b148c-238">Aşağıdaki örnek, projenizdeki tüm hedeflerin geri dönüşlerinizi sağlar:</span><span class="sxs-lookup"><span data-stu-id="b148c-238">The following example provides the fallbacks for all targets in your project:</span></span>

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

<span data-ttu-id="b148c-239">Aşağıdaki örnek yalnızca `netcoreapp2.1` hedefi için fallyedekler belirtir:</span><span class="sxs-lookup"><span data-stu-id="b148c-239">The following example specifies the fallbacks only for the `netcoreapp2.1` target:</span></span>

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp2.1'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="build-events"></a><span data-ttu-id="b148c-240">Derleme olayları</span><span class="sxs-lookup"><span data-stu-id="b148c-240">Build events</span></span>

<span data-ttu-id="b148c-241">Derleme öncesi ve derleme sonrası olaylarının proje dosyasında belirtilme biçimi değişmiştir.</span><span class="sxs-lookup"><span data-stu-id="b148c-241">The way that pre-build and post-build events are specified in the project file has changed.</span></span> <span data-ttu-id="b148c-242">$ (ProjectDir) gibi makrolar çözümlenmediğinden, PreBuildEvent ve PostBuildEvent özelliklerinin SDK stili proje biçiminde kullanılması önerilmez.</span><span class="sxs-lookup"><span data-stu-id="b148c-242">The properties PreBuildEvent and PostBuildEvent are not recommended in the SDK-style project format, because macros such as $(ProjectDir) are not resolved.</span></span> <span data-ttu-id="b148c-243">Örneğin, aşağıdaki kod artık desteklenmemektedir:</span><span class="sxs-lookup"><span data-stu-id="b148c-243">For example, the following code is no longer supported:</span></span>

```xml
<PropertyGroup>
    <PreBuildEvent>"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)" />
</PropertyGroup>
```

<span data-ttu-id="b148c-244">SDK stili projelerde `PreBuild` veya `PostBuild` adlı bir MSBuild hedefi kullanın ve `PreBuild` veya `AfterTargets` özelliği için `BeforeTargets` özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b148c-244">In SDK-style projects, use an MSBuild target named `PreBuild` or `PostBuild` and set the `BeforeTargets` property for `PreBuild` or the `AfterTargets` property for `PostBuild`.</span></span> <span data-ttu-id="b148c-245">Önceki örnek için aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="b148c-245">For the preceding example, use the following code:</span></span>

```xml
<Target Name="PreBuild" BeforeTargets="PreBuildEvent">
    <Exec Command="&quot;$(ProjectDir)PreBuildEvent.bat&quot; &quot;$(ProjectDir)..\&quot; &quot;$(ProjectDir)&quot; &quot;$(TargetDir)&quot;" />
</Target>

<Target Name="PostBuild" AfterTargets="PostBuildEvent">
   <Exec Command="echo Output written to $(TargetDir)" />
</Target>
```

> [!NOTE]
><span data-ttu-id="b148c-246">MSBuild hedefleri için herhangi bir ad kullanabilirsiniz, ancak Visual Studio IDE `PreBuild` ve `PostBuild` hedeflerini tanır. bu nedenle, Visual Studio IDE 'de komutları düzenleyebilmeniz için bu adları kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="b148c-246">You can use any name for the MSBuild targets, but the Visual Studio IDE recognizes `PreBuild` and `PostBuild` targets, so we recommend using those names so that you can edit the commands in the Visual Studio IDE.</span></span> 

## <a name="nuget-metadata-properties"></a><span data-ttu-id="b148c-247">NuGet meta veri özellikleri</span><span class="sxs-lookup"><span data-stu-id="b148c-247">NuGet metadata properties</span></span>

<span data-ttu-id="b148c-248">MSBuild 'e taşıma ile, *Project. JSON* 'dan *. csproj* dosyalarına bir NuGet paketi paketleme sırasında kullanılan giriş meta verilerini taşıdık.</span><span class="sxs-lookup"><span data-stu-id="b148c-248">With the move to MSBuild, we have moved the input metadata that is used when packing a NuGet package from *project.json* to *.csproj* files.</span></span> <span data-ttu-id="b148c-249">Girdiler MSBuild özellikleridir, bu nedenle bir `<PropertyGroup>` grubu içinde gitmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="b148c-249">The inputs are MSBuild properties so they have to go within a `<PropertyGroup>` group.</span></span> <span data-ttu-id="b148c-250">Aşağıda, `dotnet pack` komutunu veya SDK 'nın parçası olan `Pack` MSBuild hedefini kullanırken paketleme işlemine giriş olarak kullanılan özelliklerin listesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="b148c-250">The following is the list of properties that are used as inputs to the packing process when using the `dotnet pack` command or the `Pack` MSBuild target that is part of the SDK:</span></span>

### <a name="ispackable"></a><span data-ttu-id="b148c-251">Ispackable</span><span class="sxs-lookup"><span data-stu-id="b148c-251">IsPackable</span></span>

<span data-ttu-id="b148c-252">Projenin paketlenemeyeceğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="b148c-252">A Boolean value that specifies whether the project can be packed.</span></span> <span data-ttu-id="b148c-253">Varsayılan değer `true` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b148c-253">The default value is `true`.</span></span>

### <a name="packageversion"></a><span data-ttu-id="b148c-254">PackageVersion</span><span class="sxs-lookup"><span data-stu-id="b148c-254">PackageVersion</span></span>

<span data-ttu-id="b148c-255">Elde edilen paketin sahip olacağı sürümü belirtir.</span><span class="sxs-lookup"><span data-stu-id="b148c-255">Specifies the version that the resulting package will have.</span></span> <span data-ttu-id="b148c-256">Tüm NuGet sürüm dizesi formlarını kabul eder.</span><span class="sxs-lookup"><span data-stu-id="b148c-256">Accepts all forms of NuGet version string.</span></span> <span data-ttu-id="b148c-257">Varsayılan değer `$(Version)`, diğer bir deyişle, projedeki `Version` özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="b148c-257">Default is the value of `$(Version)`, that is, of the property `Version` in the project.</span></span>

### <a name="packageid"></a><span data-ttu-id="b148c-258">PackageId</span><span class="sxs-lookup"><span data-stu-id="b148c-258">PackageId</span></span>

<span data-ttu-id="b148c-259">Sonuç paketinin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b148c-259">Specifies the name for the resulting package.</span></span> <span data-ttu-id="b148c-260">Belirtilmezse, `pack` işlem varsayılan olarak paketin adı olarak `AssemblyName` veya dizin adını kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="b148c-260">If not specified, the `pack` operation will default to using the `AssemblyName` or directory name as the name of the package.</span></span>

### <a name="title"></a><span data-ttu-id="b148c-261">Başlık</span><span class="sxs-lookup"><span data-stu-id="b148c-261">Title</span></span>

<span data-ttu-id="b148c-262">Genellikle, Kullanıcı arabiriminde kullanılan ve Visual Studio 'da paket yöneticisi olarak görüntülenen, paketin kolay bir başlığı.</span><span class="sxs-lookup"><span data-stu-id="b148c-262">A human-friendly title of the package, typically used in UI displays as on nuget.org and the Package Manager in Visual Studio.</span></span> <span data-ttu-id="b148c-263">Belirtilmemişse, bunun yerine paket KIMLIĞI kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b148c-263">If not specified, the package ID is used instead.</span></span>

### <a name="authors"></a><span data-ttu-id="b148c-264">Yazarlar</span><span class="sxs-lookup"><span data-stu-id="b148c-264">Authors</span></span>

<span data-ttu-id="b148c-265">Nuget.org üzerindeki profil adlarıyla eşleşen paket yazarları için noktalı virgülle ayrılmış bir liste. Bunlar, nuget.org üzerindeki NuGet galerisinde görüntülenir ve aynı yazarlara göre çapraz başvuru için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b148c-265">A semicolon-separated list of packages authors, matching the profile names on nuget.org. These are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span>

### <a name="packagedescription"></a><span data-ttu-id="b148c-266">PackageDescription</span><span class="sxs-lookup"><span data-stu-id="b148c-266">PackageDescription</span></span>

<span data-ttu-id="b148c-267">UI görüntüleme paketinin uzun açıklaması.</span><span class="sxs-lookup"><span data-stu-id="b148c-267">A long description of the package for UI display.</span></span>

### <a name="description"></a><span data-ttu-id="b148c-268">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b148c-268">Description</span></span>

<span data-ttu-id="b148c-269">Derleme için uzun bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="b148c-269">A long description for the assembly.</span></span> <span data-ttu-id="b148c-270">`PackageDescription` belirtilmezse, bu özellik paketin açıklaması olarak da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b148c-270">If `PackageDescription` is not specified then this property is also used as the description of the package.</span></span>

### <a name="copyright"></a><span data-ttu-id="b148c-271">Telif hakkı</span><span class="sxs-lookup"><span data-stu-id="b148c-271">Copyright</span></span>

<span data-ttu-id="b148c-272">Paket için telif hakkı ayrıntıları.</span><span class="sxs-lookup"><span data-stu-id="b148c-272">Copyright details for the package.</span></span>

### <a name="packagerequirelicenseacceptance"></a><span data-ttu-id="b148c-273">PackageRequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="b148c-273">PackageRequireLicenseAcceptance</span></span>

<span data-ttu-id="b148c-274">İstemcinin paketi yüklemeden önce paket lisansını kabul etmesini isteyip istemeyeceğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="b148c-274">A Boolean value that specifies whether the client must prompt the consumer to accept the package license before installing the package.</span></span> <span data-ttu-id="b148c-275">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="b148c-275">The default is `false`.</span></span>

### <a name="packagelicenseexpression"></a><span data-ttu-id="b148c-276">PackageLicenseExpression</span><span class="sxs-lookup"><span data-stu-id="b148c-276">PackageLicenseExpression</span></span>

<span data-ttu-id="b148c-277">Bir [Spdx lisans tanımlayıcısı](https://spdx.org/licenses/) veya ifadesi.</span><span class="sxs-lookup"><span data-stu-id="b148c-277">An [SPDX license identifier](https://spdx.org/licenses/) or expression.</span></span> <span data-ttu-id="b148c-278">Örneğin: `Apache-2.0`.</span><span class="sxs-lookup"><span data-stu-id="b148c-278">For example, `Apache-2.0`.</span></span>

<span data-ttu-id="b148c-279">[Spdx lisans tanımlayıcılarının](https://spdx.org/licenses/)listesi aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b148c-279">Here is the complete list of [SPDX license identifiers](https://spdx.org/licenses/).</span></span> <span data-ttu-id="b148c-280">NuGet.org, lisans türü ifadesi kullanılırken yalnızca OSı veya FSF onaylı lisansları kabul eder.</span><span class="sxs-lookup"><span data-stu-id="b148c-280">NuGet.org accepts only OSI or FSF approved licenses when using license type expression.</span></span>

<span data-ttu-id="b148c-281">Lisans ifadelerinin tam sözdizimi aşağıda, [Abnf](https://tools.ietf.org/html/rfc5234)içinde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="b148c-281">The exact syntax of the license expressions is described below in [ABNF](https://tools.ietf.org/html/rfc5234).</span></span>

```abnf
license-id            = <short form license identifier from https://spdx.org/spdx-specification-21-web-version#h.luq9dgcle9mo>

license-exception-id  = <short form license exception identifier from https://spdx.org/spdx-specification-21-web-version#h.ruv3yl8g6czd>

simple-expression = license-id / license-id”+”

compound-expression =  1*1(simple-expression /
                simple-expression "WITH" license-exception-id /
                compound-expression "AND" compound-expression /
                compound-expression "OR" compound-expression ) /
                "(" compound-expression ")" )

license-expression =  1*1(simple-expression / compound-expression / UNLICENSED)
```

> [!NOTE]
> <span data-ttu-id="b148c-282">Tek seferde `PackageLicenseExpression`, `PackageLicenseFile` ve `PackageLicenseUrl` yalnızca biri belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="b148c-282">Only one of `PackageLicenseExpression`, `PackageLicenseFile` and `PackageLicenseUrl` can be specified at a time.</span></span>

### <a name="packagelicensefile"></a><span data-ttu-id="b148c-283">PackageLicenseFile</span><span class="sxs-lookup"><span data-stu-id="b148c-283">PackageLicenseFile</span></span>

<span data-ttu-id="b148c-284">Bir SPDX tanımlayıcısı atanmamış bir lisans kullanıyorsanız veya özel bir lisans (Aksi takdirde `PackageLicenseExpression` tercih edilir) paket içindeki bir lisans dosyasının yolu</span><span class="sxs-lookup"><span data-stu-id="b148c-284">Path to a license file within the package if you are using a license that hasn’t been assigned an SPDX identifier, or it is a custom license (Otherwise `PackageLicenseExpression` is preferred)</span></span>

<span data-ttu-id="b148c-285">`PackageLicenseUrl`, `PackageLicenseExpression` ile birleştirilemez ve Visual Studio 15.9.4, .NET SDK 2.1.502 veya 2.2.101 ya da daha yeni bir sürümü gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b148c-285">Replaces `PackageLicenseUrl`, can't be combined with `PackageLicenseExpression` and requires Visual Studio 15.9.4, .NET SDK 2.1.502 or 2.2.101, or newer.</span></span>

<span data-ttu-id="b148c-286">Lisans dosyasının paketlenmiş olduğundan emin olmanız gerekir, bu işlem, örnek kullanım:</span><span class="sxs-lookup"><span data-stu-id="b148c-286">You will need to ensure the license file is packed by adding it explicitly to the project, example usage:</span></span>

```xml
<PropertyGroup>
  <PackageLicenseFile>LICENSE.txt</PackageLicenseFile>
</PropertyGroup>
<ItemGroup>
  <None Include="licenses\LICENSE.txt" Pack="true" PackagePath="$(PackageLicenseFile)"/>
</ItemGroup>
```

### <a name="packagelicenseurl"></a><span data-ttu-id="b148c-287">PackageLicenseUrl</span><span class="sxs-lookup"><span data-stu-id="b148c-287">PackageLicenseUrl</span></span>

<span data-ttu-id="b148c-288">Pakete uygulanabilen lisansın URL 'SI.</span><span class="sxs-lookup"><span data-stu-id="b148c-288">An URL to the license that is applicable to the package.</span></span> <span data-ttu-id="b148c-289">(_Visual Studio 15.9.4, .NET SDK 2.1.502 ve 2.2.101 'den beri kullanım dışı_)</span><span class="sxs-lookup"><span data-stu-id="b148c-289">(_deprecated since Visual Studio 15.9.4, .NET SDK 2.1.502 and 2.2.101_)</span></span>

### <a name="packageiconurl"></a><span data-ttu-id="b148c-290">PackageIconUrl</span><span class="sxs-lookup"><span data-stu-id="b148c-290">PackageIconUrl</span></span>

<span data-ttu-id="b148c-291">Kullanıcı arabirimi görüntüsündeki paketin simgesi olarak kullanılacak, saydam arka planlı bir 64x64 görüntüsünün URL 'SI.</span><span class="sxs-lookup"><span data-stu-id="b148c-291">A URL for a 64x64 image with transparent background to use as the icon for the package in UI display.</span></span>

### <a name="packagereleasenotes"></a><span data-ttu-id="b148c-292">PackageReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="b148c-292">PackageReleaseNotes</span></span>

<span data-ttu-id="b148c-293">Paket için sürüm notları.</span><span class="sxs-lookup"><span data-stu-id="b148c-293">Release notes for the package.</span></span>

### <a name="packagetags"></a><span data-ttu-id="b148c-294">PackageTags</span><span class="sxs-lookup"><span data-stu-id="b148c-294">PackageTags</span></span>

<span data-ttu-id="b148c-295">Paketi atayan etiketlerin noktalı virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="b148c-295">A semicolon-delimited list of tags that designates the package.</span></span>

### <a name="packageoutputpath"></a><span data-ttu-id="b148c-296">PackageOutputPath</span><span class="sxs-lookup"><span data-stu-id="b148c-296">PackageOutputPath</span></span>

<span data-ttu-id="b148c-297">Paketlenmiş paketin bırakılacak çıkış yolunu belirler.</span><span class="sxs-lookup"><span data-stu-id="b148c-297">Determines the output path in which the packed package will be dropped.</span></span> <span data-ttu-id="b148c-298">Varsayılan değer `$(OutputPath)`.</span><span class="sxs-lookup"><span data-stu-id="b148c-298">Default is `$(OutputPath)`.</span></span>

### <a name="includesymbols"></a><span data-ttu-id="b148c-299">Includesymbols</span><span class="sxs-lookup"><span data-stu-id="b148c-299">IncludeSymbols</span></span>
<span data-ttu-id="b148c-300">Bu Boole değeri, paketin proje paketedildiğinde ek bir sembol paketi oluşturup oluşturmayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b148c-300">This Boolean value indicates whether the package should create an additional symbols package when the project is packed.</span></span> <span data-ttu-id="b148c-301">Semboller paketinin biçimi `SymbolPackageFormat` özelliği tarafından denetlenir.</span><span class="sxs-lookup"><span data-stu-id="b148c-301">The symbols package's format is controlled by the `SymbolPackageFormat` property.</span></span>

### <a name="symbolpackageformat"></a><span data-ttu-id="b148c-302">SymbolPackageFormat</span><span class="sxs-lookup"><span data-stu-id="b148c-302">SymbolPackageFormat</span></span>
<span data-ttu-id="b148c-303">Semboller paketinin biçimini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b148c-303">Specifies the format of the symbols package.</span></span> <span data-ttu-id="b148c-304">"Symbols. nupkg" ise, pdb 'leri, dll 'Ler ve diğer çıktı dosyalarını içeren *. Symbols. nupkg* Uzantısı ile eski bir sembol paketi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b148c-304">If "symbols.nupkg", a legacy symbols package will be created with a *.symbols.nupkg* extension containing PDBs, DLLs, and other output files.</span></span> <span data-ttu-id="b148c-305">"Snupkg" ise, taşınabilir pdb 'leri içeren bir snupkg sembol paketi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b148c-305">If "snupkg", a snupkg symbol package will be created containing the portable PDBs.</span></span> <span data-ttu-id="b148c-306">Varsayılan değer "symbols. nupkg" dır.</span><span class="sxs-lookup"><span data-stu-id="b148c-306">Default is "symbols.nupkg".</span></span>

### <a name="includesource"></a><span data-ttu-id="b148c-307">IncludeSource</span><span class="sxs-lookup"><span data-stu-id="b148c-307">IncludeSource</span></span>

<span data-ttu-id="b148c-308">Bu Boole değeri, paket işleminin bir kaynak paketi oluşturup oluşturmayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b148c-308">This Boolean value indicates whether the pack process should create a source package.</span></span> <span data-ttu-id="b148c-309">Kaynak paket, kitaplığın kaynak kodunu ve PDB dosyalarını içerir.</span><span class="sxs-lookup"><span data-stu-id="b148c-309">The source package contains the library's source code as well as PDB files.</span></span> <span data-ttu-id="b148c-310">Kaynak dosyalar, elde edilen paket dosyasında `src/ProjectName` dizininin altına konur.</span><span class="sxs-lookup"><span data-stu-id="b148c-310">Source files are put under the `src/ProjectName` directory in the resulting package file.</span></span>

### <a name="istool"></a><span data-ttu-id="b148c-311">IsTool</span><span class="sxs-lookup"><span data-stu-id="b148c-311">IsTool</span></span>

<span data-ttu-id="b148c-312">Tüm çıkış dosyalarının *lib* klasörü yerine *Araçlar* klasörüne kopyalanıp kopyalanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b148c-312">Specifies whether all output files are copied to the *tools* folder instead of the *lib* folder.</span></span> <span data-ttu-id="b148c-313">Bu, *. csproj* dosyasındaki `PackageType` ayarlanarak belirtilen `DotNetCliTool` farklı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b148c-313">Note that this is different from a `DotNetCliTool` which is specified by setting the `PackageType` in the *.csproj* file.</span></span>

### <a name="repositoryurl"></a><span data-ttu-id="b148c-314">Depourl 'Si</span><span class="sxs-lookup"><span data-stu-id="b148c-314">RepositoryUrl</span></span>

<span data-ttu-id="b148c-315">Paketin kaynak kodunun bulunduğu ve/veya oluşturulduğu deponun URL 'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b148c-315">Specifies the URL for the repository where the source code for the package resides and/or from which it's being built.</span></span>

### <a name="repositorytype"></a><span data-ttu-id="b148c-316">Repositorytype parametrelerinin sağlanması</span><span class="sxs-lookup"><span data-stu-id="b148c-316">RepositoryType</span></span>

<span data-ttu-id="b148c-317">Deponun türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="b148c-317">Specifies the type of the repository.</span></span> <span data-ttu-id="b148c-318">Varsayılan değer "git" dir.</span><span class="sxs-lookup"><span data-stu-id="b148c-318">Default is "git".</span></span>

### <a name="repositorybranch"></a><span data-ttu-id="b148c-319">Depodalı</span><span class="sxs-lookup"><span data-stu-id="b148c-319">RepositoryBranch</span></span>
<span data-ttu-id="b148c-320">Depodaki kaynak dalın adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b148c-320">Specifies the name of the source branch in the repository.</span></span> <span data-ttu-id="b148c-321">Proje bir NuGet paketinde paketlenmişse, paket meta verilerine eklenir.</span><span class="sxs-lookup"><span data-stu-id="b148c-321">When the project is packaged in a NuGet package, it's added to the package metadata.</span></span>

### <a name="repositorycommit"></a><span data-ttu-id="b148c-322">Kayıt yapma</span><span class="sxs-lookup"><span data-stu-id="b148c-322">RepositoryCommit</span></span>
<span data-ttu-id="b148c-323">Paketin hangi kaynağa göre oluşturulduğunu göstermek için isteğe bağlı depo kaydı veya değişiklik kümesi.</span><span class="sxs-lookup"><span data-stu-id="b148c-323">Optional repository commit or changeset to indicate which source the package was built against.</span></span> <span data-ttu-id="b148c-324">Bu özelliğin dahil olması için `RepositoryUrl` de belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="b148c-324">`RepositoryUrl` must also be specified for this property to be included.</span></span> <span data-ttu-id="b148c-325">Proje bir NuGet paketinde paketlenmişse, bu tamamlama veya değişiklik kümesi paket meta verilerine eklenir.</span><span class="sxs-lookup"><span data-stu-id="b148c-325">When the project is packaged in a NuGet package, this commit or changeset is added to the package metadata.</span></span>

### <a name="nopackageanalysis"></a><span data-ttu-id="b148c-326">NoPackageAnalysis</span><span class="sxs-lookup"><span data-stu-id="b148c-326">NoPackageAnalysis</span></span>

<span data-ttu-id="b148c-327">Paketi derlemeden sonra paketin paket analizini çalıştırmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="b148c-327">Specifies that pack should not run package analysis after building the package.</span></span>

### <a name="minclientversion"></a><span data-ttu-id="b148c-328">MinClientVersion</span><span class="sxs-lookup"><span data-stu-id="b148c-328">MinClientVersion</span></span>

<span data-ttu-id="b148c-329">NuGet. exe ve Visual Studio Paket Yöneticisi tarafından zorlanan, bu paketi yükleyesağlayan NuGet istemcisinin en düşük sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="b148c-329">Specifies the minimum version of the NuGet client that can install this package, enforced by nuget.exe and the Visual Studio Package Manager.</span></span>

### <a name="includebuildoutput"></a><span data-ttu-id="b148c-330">IncludeBuildOutput</span><span class="sxs-lookup"><span data-stu-id="b148c-330">IncludeBuildOutput</span></span>

<span data-ttu-id="b148c-331">Bu Boole değerleri, derleme çıkış derlemelerinin *. nupkg* dosyasına paketedilip edilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b148c-331">This Boolean values specifies whether the build output assemblies should be packed into the *.nupkg* file or not.</span></span>

### <a name="includecontentinpack"></a><span data-ttu-id="b148c-332">IncludeContentInPack</span><span class="sxs-lookup"><span data-stu-id="b148c-332">IncludeContentInPack</span></span>

<span data-ttu-id="b148c-333">Bu Boole değeri, `Content` türüne sahip herhangi bir öğenin, elde edilen pakete otomatik olarak dahil edilip edilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b148c-333">This Boolean value specifies whether any items that have a type of `Content` will be included in the resulting package automatically.</span></span> <span data-ttu-id="b148c-334">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="b148c-334">The default is `true`.</span></span>

### <a name="buildoutputtargetfolder"></a><span data-ttu-id="b148c-335">BuildOutputTargetFolder</span><span class="sxs-lookup"><span data-stu-id="b148c-335">BuildOutputTargetFolder</span></span>

<span data-ttu-id="b148c-336">Çıkış derlemelerinin yerleştirileceği klasörü belirtir.</span><span class="sxs-lookup"><span data-stu-id="b148c-336">Specifies the folder where to place the output assemblies.</span></span> <span data-ttu-id="b148c-337">Çıkış derlemeleri (ve diğer çıkış dosyaları) ilgili çerçeve klasörlerine kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="b148c-337">The output assemblies (and other output files) are copied into their respective framework folders.</span></span>

### <a name="contenttargetfolders"></a><span data-ttu-id="b148c-338">ContentTargetFolders</span><span class="sxs-lookup"><span data-stu-id="b148c-338">ContentTargetFolders</span></span>

<span data-ttu-id="b148c-339">Bu özellik, `PackagePath` kendileri için belirtilmemişse, tüm içerik dosyalarının gitmesi gereken varsayılan konumu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b148c-339">This property specifies the default location of where all the content files should go if `PackagePath` is not specified for them.</span></span> <span data-ttu-id="b148c-340">Varsayılan değer "Content; contentFiles" dır.</span><span class="sxs-lookup"><span data-stu-id="b148c-340">The default value is "content;contentFiles".</span></span>

### <a name="nuspecfile"></a><span data-ttu-id="b148c-341">Nusguus dosyası</span><span class="sxs-lookup"><span data-stu-id="b148c-341">NuspecFile</span></span>

<span data-ttu-id="b148c-342">Paketleme için kullanılan *. nuspec* dosyasının göreli veya mutlak yolu.</span><span class="sxs-lookup"><span data-stu-id="b148c-342">Relative or absolute path to the *.nuspec* file being used for packing.</span></span>

> [!NOTE]
> <span data-ttu-id="b148c-343">*. Nuspec* dosyası belirtilmişse, **yalnızca** paketleme bilgileri için kullanılır ve projelerdeki tüm bilgiler kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="b148c-343">If the *.nuspec* file is specified, it's used **exclusively** for packaging information and any information in the projects is not used.</span></span>

### <a name="nuspecbasepath"></a><span data-ttu-id="b148c-344">Nusgubasepath</span><span class="sxs-lookup"><span data-stu-id="b148c-344">NuspecBasePath</span></span>

<span data-ttu-id="b148c-345">*. Nuspec* dosyasının temel yolu.</span><span class="sxs-lookup"><span data-stu-id="b148c-345">Base path for the *.nuspec* file.</span></span>

### <a name="nuspecproperties"></a><span data-ttu-id="b148c-346">Nus, Properties</span><span class="sxs-lookup"><span data-stu-id="b148c-346">NuspecProperties</span></span>

<span data-ttu-id="b148c-347">Anahtar = değer çiftlerinin noktalı virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="b148c-347">Semicolon separated list of key=value pairs.</span></span>

## <a name="assemblyinfo-properties"></a><span data-ttu-id="b148c-348">AssemblyInfo özellikleri</span><span class="sxs-lookup"><span data-stu-id="b148c-348">AssemblyInfo properties</span></span>

<span data-ttu-id="b148c-349">Genellikle *AssemblyInfo* dosyasında bulunan [derleme öznitelikleri](../../standard/assembly/set-attributes.md) artık özelliklerden otomatik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b148c-349">[Assembly attributes](../../standard/assembly/set-attributes.md) that were typically present in an *AssemblyInfo* file are now automatically generated from properties.</span></span>

### <a name="properties-per-attribute"></a><span data-ttu-id="b148c-350">Öznitelik başına Özellikler</span><span class="sxs-lookup"><span data-stu-id="b148c-350">Properties per attribute</span></span>

<span data-ttu-id="b148c-351">Her öznitelik, aşağıdaki tabloda gösterildiği gibi, içeriğini denetleyen ve diğeri oluşturmayı devre dışı bırakan bir özelliğe sahiptir:</span><span class="sxs-lookup"><span data-stu-id="b148c-351">Each attribute has a property that control its content and another to disable its generation as shown in the following table:</span></span>

| <span data-ttu-id="b148c-352">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b148c-352">Attribute</span></span>                                                      | <span data-ttu-id="b148c-353">Özellik</span><span class="sxs-lookup"><span data-stu-id="b148c-353">Property</span></span>               | <span data-ttu-id="b148c-354">Devre dışı bırakılacak Özellik</span><span class="sxs-lookup"><span data-stu-id="b148c-354">Property to disable</span></span>                             |
|----------------------------------------------------------------|------------------------|-------------------------------------------------|
| <xref:System.Reflection.AssemblyCompanyAttribute>              | `Company`              | `GenerateAssemblyCompanyAttribute`              |
| <xref:System.Reflection.AssemblyConfigurationAttribute>        | `Configuration`        | `GenerateAssemblyConfigurationAttribute`        |
| <xref:System.Reflection.AssemblyCopyrightAttribute>            | `Copyright`            | `GenerateAssemblyCopyrightAttribute`            |
| <xref:System.Reflection.AssemblyDescriptionAttribute>          | `Description`          | `GenerateAssemblyDescriptionAttribute`          |
| <xref:System.Reflection.AssemblyFileVersionAttribute>          | `FileVersion`          | `GenerateAssemblyFileVersionAttribute`          |
| <xref:System.Reflection.AssemblyInformationalVersionAttribute> | `InformationalVersion` | `GenerateAssemblyInformationalVersionAttribute` |
| <xref:System.Reflection.AssemblyProductAttribute>              | `Product`              | `GenerateAssemblyProductAttribute`              |
| <xref:System.Reflection.AssemblyTitleAttribute>                | `AssemblyTitle`        | `GenerateAssemblyTitleAttribute`                |
| <xref:System.Reflection.AssemblyVersionAttribute>              | `AssemblyVersion`      | `GenerateAssemblyVersionAttribute`              |
| <xref:System.Resources.NeutralResourcesLanguageAttribute>      | `NeutralLanguage`      | `GenerateNeutralResourcesLanguageAttribute`     |

<span data-ttu-id="b148c-355">Notlar:</span><span class="sxs-lookup"><span data-stu-id="b148c-355">Notes:</span></span>

- <span data-ttu-id="b148c-356">`AssemblyVersion` ve `FileVersion` varsayılan, sonek olmadan `$(Version)` değerini alır.</span><span class="sxs-lookup"><span data-stu-id="b148c-356">`AssemblyVersion` and `FileVersion` default is to take the value of `$(Version)` without suffix.</span></span> <span data-ttu-id="b148c-357">Örneğin, `$(Version)` `1.2.3-beta.4`, değer `1.2.3`olur.</span><span class="sxs-lookup"><span data-stu-id="b148c-357">For example, if `$(Version)` is `1.2.3-beta.4`, then the value would be `1.2.3`.</span></span>
- <span data-ttu-id="b148c-358">Varsayılan değer olan `$(Version)``InformationalVersion`.</span><span class="sxs-lookup"><span data-stu-id="b148c-358">`InformationalVersion` defaults to the value of `$(Version)`.</span></span>
- <span data-ttu-id="b148c-359">`InformationalVersion`, özellik varsa `$(SourceRevisionId)` eklenmiş.</span><span class="sxs-lookup"><span data-stu-id="b148c-359">`InformationalVersion` has `$(SourceRevisionId)` appended if the property is present.</span></span> <span data-ttu-id="b148c-360">`IncludeSourceRevisionInInformationalVersion`kullanılarak devre dışı bırakılabilir.</span><span class="sxs-lookup"><span data-stu-id="b148c-360">It can be disabled using `IncludeSourceRevisionInInformationalVersion`.</span></span>
- <span data-ttu-id="b148c-361">`Copyright` ve `Description` özellikleri NuGet meta verileri için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b148c-361">`Copyright` and `Description` properties are also used for NuGet metadata.</span></span>
- <span data-ttu-id="b148c-362">`Configuration` tüm derleme işlemiyle paylaşılır ve `dotnet` komutlarının `--configuration` parametresi aracılığıyla ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="b148c-362">`Configuration` is shared with all the build process and set via the `--configuration` parameter of `dotnet` commands.</span></span>

### <a name="generateassemblyinfo"></a><span data-ttu-id="b148c-363">Generateassemblyınfo</span><span class="sxs-lookup"><span data-stu-id="b148c-363">GenerateAssemblyInfo</span></span>

<span data-ttu-id="b148c-364">Tüm AssemblyInfo üretimini etkinleştiren veya devre dışı bırakan bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="b148c-364">A Boolean that enable or disable all the AssemblyInfo generation.</span></span> <span data-ttu-id="b148c-365">Varsayılan değer `true` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b148c-365">The default value is `true`.</span></span>

### <a name="generatedassemblyinfofile"></a><span data-ttu-id="b148c-366">GeneratedAssemblyInfoFile</span><span class="sxs-lookup"><span data-stu-id="b148c-366">GeneratedAssemblyInfoFile</span></span>

<span data-ttu-id="b148c-367">Oluşturulan derleme bilgileri dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="b148c-367">The path of the generated assembly info file.</span></span> <span data-ttu-id="b148c-368">`$(IntermediateOutputPath)` (obj) dizinindeki bir dosya için varsayılan değer.</span><span class="sxs-lookup"><span data-stu-id="b148c-368">Default to a file in the `$(IntermediateOutputPath)` (obj) directory.</span></span>
