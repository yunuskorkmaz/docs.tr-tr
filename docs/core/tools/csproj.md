---
title: .NET Core için csproj biçimine eklemeler
description: Mevcut ve .NET Core csproj dosyaları arasındaki farklılıklar hakkında bilgi edinin
ms.date: 04/08/2019
ms.openlocfilehash: 89ab22f0c5e69f29ff31e13d46dce8ba278d08da
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216207"
---
# <a name="additions-to-the-csproj-format-for-net-core"></a><span data-ttu-id="87099-103">.NET Core için csproj biçimine eklemeler</span><span class="sxs-lookup"><span data-stu-id="87099-103">Additions to the csproj format for .NET Core</span></span>

<span data-ttu-id="87099-104">Bu belge, Project *. JSON* 'dan *csproj* ve [MSBuild](https://github.com/Microsoft/MSBuild)'e geçiş kapsamında proje dosyalarına eklenen değişiklikleri özetler.</span><span class="sxs-lookup"><span data-stu-id="87099-104">This document outlines the changes that were added to the project files as part of the move from *project.json* to *csproj* and [MSBuild](https://github.com/Microsoft/MSBuild).</span></span> <span data-ttu-id="87099-105">Genel proje dosyası sözdizimi ve başvurusu hakkında daha fazla bilgi için bkz. [MSBuild proje dosyası](/visualstudio/msbuild/msbuild-project-file-schema-reference) belgeleri.</span><span class="sxs-lookup"><span data-stu-id="87099-105">For more information about general project file syntax and reference, see [the MSBuild project file](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation.</span></span>

## <a name="implicit-package-references"></a><span data-ttu-id="87099-106">Örtük paket başvuruları</span><span class="sxs-lookup"><span data-stu-id="87099-106">Implicit package references</span></span>

<span data-ttu-id="87099-107">Meta paketlere, proje dosyanızın `<TargetFramework>` veya `<TargetFrameworks>` özelliğinde belirtilen hedef çatılar temelinde örtülü olarak başvurulur.</span><span class="sxs-lookup"><span data-stu-id="87099-107">Metapackages are implicitly referenced based on the target framework(s) specified in the `<TargetFramework>` or `<TargetFrameworks>` property of your project file.</span></span> <span data-ttu-id="87099-108">`<TargetFrameworks>`belirtilmişse, sıralamayla bağımsız olarak yoksayılır `<TargetFramework>` .</span><span class="sxs-lookup"><span data-stu-id="87099-108">`<TargetFrameworks>` is ignored if `<TargetFramework>` is specified, independent of order.</span></span> <span data-ttu-id="87099-109">Daha fazla bilgi için bkz. [paketler, Metapackages ve çerçeveler](../packages.md).</span><span class="sxs-lookup"><span data-stu-id="87099-109">For more information, see [Packages, metapackages and frameworks](../packages.md).</span></span> 

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

### <a name="recommendations"></a><span data-ttu-id="87099-110">Öneriler</span><span class="sxs-lookup"><span data-stu-id="87099-110">Recommendations</span></span>

<span data-ttu-id="87099-111">`Microsoft.NETCore.App` Veya`NETStandard.Library` Metapackages örtük olarak başvurulduğundan, önerilen en iyi yöntemler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="87099-111">Since `Microsoft.NETCore.App` or `NETStandard.Library` metapackages are implicitly referenced, the following are our recommended best practices:</span></span>

* <span data-ttu-id="87099-112">.NET Core veya .NET Standard hedeflenirken, proje dosyanızdaki bir `Microsoft.NETCore.App` `<PackageReference>` öğe aracılığıyla veya `NETStandard.Library` metapaketlerine açık bir başvuruya sahip olmaz.</span><span class="sxs-lookup"><span data-stu-id="87099-112">When targeting .NET Core or .NET Standard, never have an explicit reference to the `Microsoft.NETCore.App` or `NETStandard.Library` metapackages via a `<PackageReference>` item in your project file.</span></span>
* <span data-ttu-id="87099-113">.NET Core 'u hedeflerken çalışma zamanının belirli bir sürümüne ihtiyacınız varsa, metapackage 'e başvurmak yerine `<RuntimeFrameworkVersion>` projenizdeki özelliğini (örneğin, `1.0.4`) kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="87099-113">If you need a specific version of the runtime when targeting .NET Core, you should use the `<RuntimeFrameworkVersion>` property in your project (for example, `1.0.4`) instead of referencing the metapackage.</span></span>
  * <span data-ttu-id="87099-114">Bu, [kendi kendine kapsanan dağıtımlar](../deploying/index.md#self-contained-deployments-scd) kullanıyorsanız ve örneğin 1.0.0 LTS çalışma zamanının belirli bir düzeltme eki sürümüne ihtiyaç duyuyorsanız meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="87099-114">This might happen if you are using [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) and you need a specific patch version of 1.0.0 LTS runtime, for example.</span></span>
* <span data-ttu-id="87099-115">.NET Standard hedeflenirken `NETStandard.Library` metapackage 'in belirli bir sürümüne ihtiyacınız varsa, `<NetStandardImplicitPackageVersion>` özelliğini kullanabilir ve ihtiyacınız olan sürümü ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87099-115">If you need a specific version of the `NETStandard.Library` metapackage when targeting .NET Standard, you can use the `<NetStandardImplicitPackageVersion>` property and set the version you need.</span></span>
* <span data-ttu-id="87099-116">.NET Framework projelerindeki `Microsoft.NETCore.App` veya `NETStandard.Library` metapackage ya da başvuruları açıkça eklemeyin veya güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="87099-116">Don't explicitly add or update references to either the `Microsoft.NETCore.App` or `NETStandard.Library` metapackage in .NET Framework projects.</span></span> <span data-ttu-id="87099-117">.NET Standard tabanlı bir NuGet `NETStandard.Library` Paketi kullanılırken herhangi bir sürümü gerekiyorsa, NuGet bu sürümü otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="87099-117">If any version of `NETStandard.Library` is needed when using a .NET Standard-based NuGet package, NuGet automatically installs that version.</span></span>

## <a name="implicit-version-for-some-package-references"></a><span data-ttu-id="87099-118">Bazı paket başvurularının örtük sürümü</span><span class="sxs-lookup"><span data-stu-id="87099-118">Implicit version for some package references</span></span>

<span data-ttu-id="87099-119">Çoğu kullanımları [`<PackageReference>`](#packagereference) , kullanılacak NuGet paket `Version` sürümünü belirtmek için özniteliğini ayarlamayı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="87099-119">Most usages of [`<PackageReference>`](#packagereference) require setting the `Version` attribute to specify the NuGet package version to be used.</span></span> <span data-ttu-id="87099-120">.NET Core 2,1 veya 2,2 kullanırken ve [Microsoft. aspnetcore. app](/aspnet/core/fundamentals/metapackage-app) ya da [Microsoft. Aspnetcore. All](/aspnet/core/fundamentals/metapackage)ile başvurulduğunda öznitelik gereksizdir.</span><span class="sxs-lookup"><span data-stu-id="87099-120">When using .NET Core 2.1 or 2.2 and referencing [Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage-app) or [Microsoft.AspNetCore.All](/aspnet/core/fundamentals/metapackage), however, the  attribute is unnecessary.</span></span> <span data-ttu-id="87099-121">.NET Core SDK, bu paketlerin kullanılması gereken sürümünü otomatik olarak seçebilir.</span><span class="sxs-lookup"><span data-stu-id="87099-121">The .NET Core SDK can automatically select the version of these packages that should be used.</span></span>

### <a name="recommendation"></a><span data-ttu-id="87099-122">Öneri</span><span class="sxs-lookup"><span data-stu-id="87099-122">Recommendation</span></span>

<span data-ttu-id="87099-123">`Microsoft.AspNetCore.App` Veya`Microsoft.AspNetCore.All` paketlerine başvurulduğunda, sürümünü belirtmeyin.</span><span class="sxs-lookup"><span data-stu-id="87099-123">When referencing the `Microsoft.AspNetCore.App` or `Microsoft.AspNetCore.All` packages, do not specify their version.</span></span> <span data-ttu-id="87099-124">Bir sürüm belirtilmişse, SDK uyarı NETSDK1071 üretebilir.</span><span class="sxs-lookup"><span data-stu-id="87099-124">If a version is specified, the SDK may produce warning NETSDK1071.</span></span> <span data-ttu-id="87099-125">Bu uyarıyı onarmak için aşağıdaki örnekteki gibi paket sürümünü kaldırın:</span><span class="sxs-lookup"><span data-stu-id="87099-125">To fix this warning, remove the package version like in the following example:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.AspNetCore.App" />
</ItemGroup>
```

> <span data-ttu-id="87099-126">Bilinen sorun: .NET Core 2,1 SDK 'Sı yalnızca proje Microsoft. NET. SDK. Web 'i kullandığında bu söz dizimini destekliyordu.</span><span class="sxs-lookup"><span data-stu-id="87099-126">Known issue: the .NET Core 2.1 SDK only supported this syntax when the project also uses Microsoft.NET.Sdk.Web.</span></span> <span data-ttu-id="87099-127">Bu, .NET Core 2,2 SDK 'sında çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="87099-127">This is resolved in the .NET Core 2.2 SDK.</span></span>

<span data-ttu-id="87099-128">ASP.NET Core metapaketlerine yapılan bu başvuruların çoğu normal NuGet paketlerinden biraz farklı bir davranışı vardır.</span><span class="sxs-lookup"><span data-stu-id="87099-128">These references to ASP.NET Core metapackages have a slightly different behavior from most normal NuGet packages.</span></span> <span data-ttu-id="87099-129">Bu metapaketleri kullanan uygulamaların [çerçeveye bağımlı dağıtımları](../deploying/index.md#framework-dependent-deployments-fdd) ASP.NET Core paylaşılan çerçeveden otomatik olarak yararlanır.</span><span class="sxs-lookup"><span data-stu-id="87099-129">[Framework-dependent deployments](../deploying/index.md#framework-dependent-deployments-fdd) of applications that use these metapackages automatically take advantage of the ASP.NET Core shared framework.</span></span> <span data-ttu-id="87099-130">Meta paketleri kullandığınızda başvurulan ASP.NET Core NuGet paketlerinden **hiçbir** varlık uygulamayla birlikte dağıtılır — ASP.NET Core paylaşılan çerçeve bu varlıkları içerir.</span><span class="sxs-lookup"><span data-stu-id="87099-130">When you use the metapackages, **no** assets from the referenced ASP.NET Core NuGet packages are deployed with the application—the ASP.NET Core shared framework contains these assets.</span></span> <span data-ttu-id="87099-131">Paylaşılan çerçevede bulunan varlıklar, uygulama başlatma süresini artırmak üzere hedef platform için iyileştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="87099-131">The assets in the shared framework are optimized for the target platform to improve application startup time.</span></span> <span data-ttu-id="87099-132">Paylaşılan Framework hakkında daha fazla bilgi için bkz. [.NET Core dağıtım paketleme](../build/distribution-packaging.md).</span><span class="sxs-lookup"><span data-stu-id="87099-132">For more information about shared framework, see [.NET Core distribution packaging](../build/distribution-packaging.md).</span></span>

<span data-ttu-id="87099-133">Bir *Sürüm belirtilmişse* , çerçeveye bağımlı dağıtımlar için ASP.NET Core paylaşılan Framework 'ün *En düşük* sürümü ve kendi içinde olan dağıtımlar için *tam* sürüm olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="87099-133">If a version *is* specified, it's treated as the *minimum* version of ASP.NET Core shared framework for framework-dependent deployments and as an *exact* version for self-contained deployments.</span></span> <span data-ttu-id="87099-134">Bu, aşağıdaki sonuçlara sahip olabilir:</span><span class="sxs-lookup"><span data-stu-id="87099-134">This can have the following consequences:</span></span>

* <span data-ttu-id="87099-135">Sunucuda yüklü ASP.NET Core sürümü, PackageReference üzerinde belirtilen sürümden küçükse .NET Core işlemi başlayamaz.</span><span class="sxs-lookup"><span data-stu-id="87099-135">If the version of ASP.NET Core installed on the server is less than the version specified on the PackageReference, the .NET Core process fails to launch.</span></span> <span data-ttu-id="87099-136">Metapackage güncelleştirmeleri, Azure gibi barındırma ortamlarında güncelleştirmeler kullanılabilir hale getirilinceye kadar sıklıkla NuGet.org üzerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="87099-136">Updates to the metapackage are often available on NuGet.org before updates have been made available in hosting environments such as Azure.</span></span> <span data-ttu-id="87099-137">PackageReference üzerindeki sürümün ASP.NET Core güncelleştirilmesi, dağıtılan bir uygulamanın başarısız olmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="87099-137">Updating the version on the PackageReference to ASP.NET Core could cause a deployed application to fail.</span></span>
* <span data-ttu-id="87099-138">Uygulama [kendi içindeki bir dağıtım](../deploying/index.md#self-contained-deployments-scd)olarak dağıtılırsa, uygulama .NET Core için en son güvenlik güncelleştirmelerini içermeyebilir.</span><span class="sxs-lookup"><span data-stu-id="87099-138">If the application is deployed as a [self-contained deployment](../deploying/index.md#self-contained-deployments-scd), the application may not contain the latest security updates to .NET Core.</span></span> <span data-ttu-id="87099-139">Bir sürüm belirtilmediğinde, SDK otomatik olarak kapsanan dağıtıma en yeni ASP.NET Core sürümünü ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="87099-139">When a version isn't specified, the SDK can automatically include the newest version of ASP.NET Core in the self-contained deployment.</span></span>

## <a name="default-compilation-includes-in-net-core-projects"></a><span data-ttu-id="87099-140">.NET Core projelerinde varsayılan derleme dahildir</span><span class="sxs-lookup"><span data-stu-id="87099-140">Default compilation includes in .NET Core projects</span></span>

<span data-ttu-id="87099-141">En son SDK sürümlerindeki *csproj* biçimine geçiş ile, derleme öğeleri ve katıştırılmış kaynaklar için varsayılan ekleme ve DıŞMALARı SDK Özellikler dosyalarına taşıdık.</span><span class="sxs-lookup"><span data-stu-id="87099-141">With the move to the *csproj* format in the latest SDK versions, we've moved the default includes and excludes for compile items and embedded resources to the SDK properties files.</span></span> <span data-ttu-id="87099-142">Bu, artık proje dosyanızda bu öğeleri belirtmeniz gerekmediği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="87099-142">This means that you no longer need to specify these items in your project file.</span></span>

<span data-ttu-id="87099-143">Bunu yapmanın asıl nedeni, proje dosyanızdaki dağınıklığı azaltmaktır.</span><span class="sxs-lookup"><span data-stu-id="87099-143">The main reason for doing this is to reduce the clutter in your project file.</span></span> <span data-ttu-id="87099-144">SDK 'da bulunan varsayılanlar en yaygın kullanım durumlarını kapsamalıdır, bu nedenle bunları oluşturduğunuz her projede tekrarlamaya gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="87099-144">The defaults that are present in the SDK should cover most common use cases, so there is no need to repeat them in every project that you create.</span></span> <span data-ttu-id="87099-145">Bu, anlaşılması çok daha kolay olan daha küçük proje dosyalarına ve gerekirse el ile düzenlemeye yol açar.</span><span class="sxs-lookup"><span data-stu-id="87099-145">This leads to smaller project files that are much easier to understand as well as edit by hand, if needed.</span></span>

<span data-ttu-id="87099-146">Aşağıdaki tabloda, SDK 'nın hangi öğesi ve hangi [genelleştirmeler](https://en.wikipedia.org/wiki/Glob_(programming)) dahil olduğu ve hangilerinin hariç olduğu gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="87099-146">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are both included and excluded in the SDK:</span></span>

| <span data-ttu-id="87099-147">Öğe</span><span class="sxs-lookup"><span data-stu-id="87099-147">Element</span></span>           | <span data-ttu-id="87099-148">Glob 'yi dahil et</span><span class="sxs-lookup"><span data-stu-id="87099-148">Include glob</span></span>                              | <span data-ttu-id="87099-149">Glob 'yi hariç tut</span><span class="sxs-lookup"><span data-stu-id="87099-149">Exclude glob</span></span>                                                  | <span data-ttu-id="87099-150">Glob 'yi kaldır</span><span class="sxs-lookup"><span data-stu-id="87099-150">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| <span data-ttu-id="87099-151">Derleme</span><span class="sxs-lookup"><span data-stu-id="87099-151">Compile</span></span>           | <span data-ttu-id="87099-152">\*\*/\*. cs (veya diğer dil uzantıları)</span><span class="sxs-lookup"><span data-stu-id="87099-152">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="87099-153">\*\*/\*kullanıcısını  \*\*/\*.\* PROJ  .sln\* ;/ \* \*  \* \*. vssscc/ \*</span><span class="sxs-lookup"><span data-stu-id="87099-153">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="87099-154">Yok</span><span class="sxs-lookup"><span data-stu-id="87099-154">N/A</span></span>                      |
| <span data-ttu-id="87099-155">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="87099-155">EmbeddedResource</span></span>  | <span data-ttu-id="87099-156">\*\*/\*. resx</span><span class="sxs-lookup"><span data-stu-id="87099-156">\*\*/\*.resx</span></span>                              | <span data-ttu-id="87099-157">\*\*/\*kullanıcısını \*\*/\*.\* PROJ .sln\* ;/ \* \* \* \*. vssscc/ \*</span><span class="sxs-lookup"><span data-stu-id="87099-157">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="87099-158">Yok</span><span class="sxs-lookup"><span data-stu-id="87099-158">N/A</span></span>                      |
| <span data-ttu-id="87099-159">Yok.</span><span class="sxs-lookup"><span data-stu-id="87099-159">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="87099-160">\*\*/\*kullanıcısını \*\*/\*.\* PROJ .sln\* ;/ \* \* \* \*. vssscc/ \*</span><span class="sxs-lookup"><span data-stu-id="87099-160">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="87099-161">\*\*/\*.cs \* .resx\* / \*</span><span class="sxs-lookup"><span data-stu-id="87099-161">\*\*/\*.cs; \*\*/\*.resx</span></span>   |

> [!NOTE]
> <span data-ttu-id="87099-162">**Glob 'yi hariç tut** , `./bin` sırasıyla `./obj` `$(BaseOutputPath)` ve `$(BaseIntermediateOutputPath)` MSBuild özellikleriyle temsil edilen ve klasörlerini dışlar.</span><span class="sxs-lookup"><span data-stu-id="87099-162">**Exclude glob** always excludes the `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, respectively.</span></span> <span data-ttu-id="87099-163">Bütün olarak, tüm dışlar tarafından `$(DefaultItemExcludes)`temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="87099-163">As a whole, all excludes are represented by `$(DefaultItemExcludes)`.</span></span>

<span data-ttu-id="87099-164">Projenizde genelleştirmeler varsa ve en yeni SDK kullanarak derlemeyi denerseniz, şu hatayı alırsınız:</span><span class="sxs-lookup"><span data-stu-id="87099-164">If you have globs in your project and you try to build it using the newest SDK, you'll get the following error:</span></span>

> <span data-ttu-id="87099-165">Yinelenen derleme öğeleri eklendi.</span><span class="sxs-lookup"><span data-stu-id="87099-165">Duplicate Compile items were included.</span></span> <span data-ttu-id="87099-166">.NET SDK, varsayılan olarak proje dizininizdeki derleme öğelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="87099-166">The .NET SDK includes Compile items from your project directory by default.</span></span> <span data-ttu-id="87099-167">Bu öğeleri proje dosyanıza kaldırabilir ya da bunları proje dosyanıza açıkça dahil etmek istiyorsanız ' Enabledefaultcompileıtems ' özelliğini ' false ' olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87099-167">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

<span data-ttu-id="87099-168">Bu hatayı çözmek için, önceki tabloda listelenenler ile eşleşen açık `Compile` öğeleri kaldırabilir veya `<EnableDefaultCompileItems>` özelliği şu şekilde `false`ayarlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="87099-168">In order to get around this error, you can either remove the explicit `Compile` items that match the ones listed on the previous table, or you can set the `<EnableDefaultCompileItems>` property to `false`, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

<span data-ttu-id="87099-169">Bu özelliğin olarak `false` ayarlanması örtük eklemeyi devre dışı bırakacak ve projenizde varsayılan genelleştirmeler belirtmeniz gereken önceki SDK 'ların davranışına geri döndürülüyor.</span><span class="sxs-lookup"><span data-stu-id="87099-169">Setting this property to `false` will disable implicit inclusion, reverting to the behavior of previous SDKs where you had to specify the default globs in your project.</span></span>

<span data-ttu-id="87099-170">Bu değişiklik, diğer dahil olmak üzere ana mekana 'yi değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="87099-170">This change does not modify the main mechanics of other includes.</span></span> <span data-ttu-id="87099-171">Bununla birlikte, örneğin, uygulamanızla yayımlanacak bazı dosyalar belirtmek istiyorsanız, bilinen mekanizmaların *csproj* içinde yine de (örneğin, `<Content>` öğesi) kullanılmasını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87099-171">However, if you wish to specify, for example, some files to get published with your app, you can still use the known mechanisms in *csproj* for that (for example, the `<Content>` element).</span></span>

<span data-ttu-id="87099-172">`<EnableDefaultCompileItems>`yalnızca genelleştirmeler `Compile` 'i devre dışı bırakır, ancak. cs öğeleri için `None` \*de geçerli olan örtük glob gibi diğer genelleştirmeler 'yi etkilemez.</span><span class="sxs-lookup"><span data-stu-id="87099-172">`<EnableDefaultCompileItems>` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob, which also applies to \*.cs items.</span></span> <span data-ttu-id="87099-173">Bu nedenle **Çözüm Gezgini** , öğe olarak \* `None` dahil olmak üzere projenin bir parçası olarak. cs öğelerini göstermeye devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="87099-173">Because of that, **Solution Explorer** will continue show \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="87099-174">Benzer bir şekilde, örtük `<EnableDefaultNoneItems>` `None` glob 'yi devre dışı bırakmak için false olarak ayarlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="87099-174">In a similar way, you can set `<EnableDefaultNoneItems>` to false to disable the implicit `None` glob, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

<span data-ttu-id="87099-175">**Tüm örtük genelleştirmeler**devre dışı bırakmak için, `<EnableDefaultItems>` özelliği `false` aşağıdaki örnekte olduğu gibi olarak ayarlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="87099-175">To disable **all implicit globs**, you can set the `<EnableDefaultItems>` property to `false` as in the following example:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a><span data-ttu-id="87099-176">Tüm projeyi MSBuild tarafından görüyor</span><span class="sxs-lookup"><span data-stu-id="87099-176">How to see the whole project as MSBuild sees it</span></span>

<span data-ttu-id="87099-177">Bu csproj proje dosyalarını büyük ölçüde basitleştirirken, SDK ve hedefleri dahil edildikten sonra MSBuild tarafından, tam genişletilmiş projeyi görmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87099-177">While those csproj changes greatly simplify project files, you might want to see the fully expanded project as MSBuild sees it once the SDK and its targets are included.</span></span> <span data-ttu-id="87099-178">Projeyi gerçekten oluşturmadan, hangi dosyaların içeri aktarıldığını, [`dotnet msbuild`](dotnet-msbuild.md) kaynaklarını ve yapıya katkılarını gösteren komut [ `/pp` anahtarıyla](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) projeyi önceden işleyin:</span><span class="sxs-lookup"><span data-stu-id="87099-178">Preprocess the project with [the `/pp` switch](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) of the [`dotnet msbuild`](dotnet-msbuild.md) command, which shows which files are imported, their sources, and their contributions to the build without actually building the project:</span></span>

`dotnet msbuild -pp:fullproject.xml`

<span data-ttu-id="87099-179">Projede birden çok hedef çerçeve varsa, komutun sonuçları MSBuild özelliği olarak belirtilerek yalnızca birine odaklanmalıdır:</span><span class="sxs-lookup"><span data-stu-id="87099-179">If the project has multiple target frameworks, the results of the command should be focused on only one of them by specifying it as an MSBuild property:</span></span>

`dotnet msbuild -p:TargetFramework=netcoreapp2.0 -pp:fullproject.xml`

## <a name="additions"></a><span data-ttu-id="87099-180">Üzerine</span><span class="sxs-lookup"><span data-stu-id="87099-180">Additions</span></span>

### <a name="sdk-attribute"></a><span data-ttu-id="87099-181">SDK özniteliği</span><span class="sxs-lookup"><span data-stu-id="87099-181">Sdk attribute</span></span>

<span data-ttu-id="87099-182">`<Project>` *. Csproj* dosyasının kök öğesi adlı `Sdk`yeni bir özniteliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="87099-182">The root `<Project>` element of the *.csproj* file has a new attribute called `Sdk`.</span></span> <span data-ttu-id="87099-183">`Sdk`Proje tarafından hangi SDK 'nın kullanılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="87099-183">`Sdk` specifies which SDK will be used by the project.</span></span> <span data-ttu-id="87099-184">[Katman, katmanlama belgesinde](cli-msbuild-architecture.md) açıklandığı gibi, .NET Core kodu oluşturabileceğiniz MSBuild [görevleri](/visualstudio/msbuild/msbuild-tasks) ve [hedefleri](/visualstudio/msbuild/msbuild-targets) kümesidir.</span><span class="sxs-lookup"><span data-stu-id="87099-184">The SDK, as the [layering document](cli-msbuild-architecture.md) describes, is a set of MSBuild [tasks](/visualstudio/msbuild/msbuild-tasks) and [targets](/visualstudio/msbuild/msbuild-targets) that can build .NET Core code.</span></span> <span data-ttu-id="87099-185">.NET Core için aşağıdaki SDK 'lar mevcuttur:</span><span class="sxs-lookup"><span data-stu-id="87099-185">The following SDKs are available for .NET Core:</span></span>

1. <span data-ttu-id="87099-186">KIMLIĞINE sahip .NET Core SDK`Microsoft.NET.Sdk`</span><span class="sxs-lookup"><span data-stu-id="87099-186">The .NET Core SDK with the ID of `Microsoft.NET.Sdk`</span></span>
2. <span data-ttu-id="87099-187">KIMLIĞINE sahip .NET Core Web SDK 'Sı`Microsoft.NET.Sdk.Web`</span><span class="sxs-lookup"><span data-stu-id="87099-187">The .NET Core web SDK with the ID of `Microsoft.NET.Sdk.Web`</span></span>
3. <span data-ttu-id="87099-188">KIMLIKLI .NET Core Razor sınıf kitaplığı SDK 'Sı`Microsoft.NET.Sdk.Razor`</span><span class="sxs-lookup"><span data-stu-id="87099-188">The .NET Core Razor Class Library SDK with the ID of `Microsoft.NET.Sdk.Razor`</span></span>
4. <span data-ttu-id="87099-189">Kimliği `Microsoft.NET.Sdk.Worker` (.NET Core 3,0 ' den beri) olan .NET Core Worker hizmeti</span><span class="sxs-lookup"><span data-stu-id="87099-189">The .NET Core Worker Service with the ID of `Microsoft.NET.Sdk.Worker` (since .NET Core 3.0)</span></span>
5. <span data-ttu-id="87099-190">Kimliği `Microsoft.NET.Sdk.WindowsDesktop` (.NET Core 3,0 ' den beri) olan .NET Core WinForms ve WPF</span><span class="sxs-lookup"><span data-stu-id="87099-190">The .NET Core WinForms and WPF with the ID of `Microsoft.NET.Sdk.WindowsDesktop` (since .NET Core 3.0)</span></span>

<span data-ttu-id="87099-191">.NET Core araçları 'nı kullanabilmeniz `Sdk` ve kodunuzu derlemek için `<Project>` öğesi için bu kimliklerden birine ayarlanmış özniteliğin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="87099-191">You need to have the `Sdk` attribute set to one of those IDs on the `<Project>` element in order to use the .NET Core tools and build your code.</span></span>

### <a name="packagereference"></a><span data-ttu-id="87099-192">PackageReference</span><span class="sxs-lookup"><span data-stu-id="87099-192">PackageReference</span></span>

<span data-ttu-id="87099-193">Öğe öğesi [, projede bir NuGet bağımlılığını](/nuget/consume-packages/package-references-in-project-files)belirtir. `<PackageReference>`</span><span class="sxs-lookup"><span data-stu-id="87099-193">A `<PackageReference>` item element specifies a [NuGet dependency in the project](/nuget/consume-packages/package-references-in-project-files).</span></span> <span data-ttu-id="87099-194">`Include` Öznitelik, paket kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="87099-194">The `Include` attribute specifies the package ID.</span></span>

```xml
<PackageReference Include="<package-id>" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a><span data-ttu-id="87099-195">Sürüm</span><span class="sxs-lookup"><span data-stu-id="87099-195">Version</span></span>

<span data-ttu-id="87099-196">Gerekli `Version` öznitelik, geri yüklenecek paketin sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="87099-196">The required `Version` attribute specifies the version of the package to restore.</span></span> <span data-ttu-id="87099-197">Öznitelik, [NuGet sürüm oluşturma](/nuget/reference/package-versioning#version-ranges-and-wildcards) şemasının kurallarına uyar.</span><span class="sxs-lookup"><span data-stu-id="87099-197">The attribute respects the rules of the [NuGet versioning](/nuget/reference/package-versioning#version-ranges-and-wildcards) scheme.</span></span> <span data-ttu-id="87099-198">Varsayılan davranış, tam bir sürüm eşleşmedir.</span><span class="sxs-lookup"><span data-stu-id="87099-198">The default behavior is an exact version match.</span></span> <span data-ttu-id="87099-199">Örneğin belirtme `Version="1.2.3"` , paketin tam 1.2.3 sürümü için NuGet `[1.2.3]` gösterimine eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="87099-199">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

#### <a name="includeassets-excludeassets-and-privateassets"></a><span data-ttu-id="87099-200">Includevarlıklarını, Excludevarlıklarını ve Privatevarlıkları</span><span class="sxs-lookup"><span data-stu-id="87099-200">IncludeAssets, ExcludeAssets and PrivateAssets</span></span>

<span data-ttu-id="87099-201">`IncludeAssets`öznitelik, tarafından `<PackageReference>` belirtilen pakete ait olan varlıkların tüketilmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="87099-201">`IncludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed.</span></span> <span data-ttu-id="87099-202">Varsayılan olarak, tüm paket varlıkları dahil edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="87099-202">By default, all package assets are included.</span></span>

<span data-ttu-id="87099-203">`ExcludeAssets`öznitelik, tarafından `<PackageReference>` belirtilen pakete ait olan varlıkların tüketilmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="87099-203">`ExcludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should not be consumed.</span></span>

<span data-ttu-id="87099-204">`PrivateAssets`öznitelik, tarafından `<PackageReference>` belirtilen pakete ait olan varlıkların tüketilmesi gerektiğini, ancak bir sonraki projenin akışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="87099-204">`PrivateAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed but not flow to the next project.</span></span> <span data-ttu-id="87099-205">Bu öznitelik `Build` mevcut `ContentFiles` olmadığında, ve varlıkları varsayılan olarak özeldir. `Analyzers`</span><span class="sxs-lookup"><span data-stu-id="87099-205">The `Analyzers`, `Build` and `ContentFiles` assets are private by default when this attribute is not present.</span></span>

> [!NOTE]
> <span data-ttu-id="87099-206">`PrivateAssets`, *Project. JSON*/*xproj* `SuppressParent` öğesine eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="87099-206">`PrivateAssets` is equivalent to the *project.json*/*xproj* `SuppressParent` element.</span></span>

<span data-ttu-id="87099-207">Bu öznitelikler, birden fazla listeleniyorsa noktalı virgül `;` karakteriyle ayrılmış aşağıdaki öğelerden birini veya daha fazlasını içerebilir:</span><span class="sxs-lookup"><span data-stu-id="87099-207">These attributes can contain one or more of the following items, separated by the semicolon `;` character if more than one is listed:</span></span>

* <span data-ttu-id="87099-208">`Compile`– LIB klasörünün içeriği, derleme için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="87099-208">`Compile` – the contents of the lib folder are available to compile against.</span></span>
* <span data-ttu-id="87099-209">`Runtime`– çalışma zamanı klasörünün içeriği dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="87099-209">`Runtime` – the contents of the runtime folder are distributed.</span></span>
* <span data-ttu-id="87099-210">`ContentFiles`– *ContentFiles* klasörünün içeriği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="87099-210">`ContentFiles` – the contents of the *contentfiles* folder are used.</span></span>
* <span data-ttu-id="87099-211">`Build`– Build klasöründeki props/targets kullanılır.</span><span class="sxs-lookup"><span data-stu-id="87099-211">`Build` – the props/targets in the build folder are used.</span></span>
* <span data-ttu-id="87099-212">`Native`– Yerel varlıklardan içerik çalışma zamanı için çıkış klasörüne kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="87099-212">`Native` – the contents from native assets are copied to the output folder for runtime.</span></span>
* <span data-ttu-id="87099-213">`Analyzers`– çözümleyiciler kullanılır.</span><span class="sxs-lookup"><span data-stu-id="87099-213">`Analyzers` – the analyzers are used.</span></span>

<span data-ttu-id="87099-214">Alternatif olarak, öznitelik şunları içerebilir:</span><span class="sxs-lookup"><span data-stu-id="87099-214">Alternatively, the attribute can contain:</span></span>

* <span data-ttu-id="87099-215">`None`– varlıkların hiçbiri kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="87099-215">`None` – none of the assets are used.</span></span>
* <span data-ttu-id="87099-216">`All`– Tüm varlıklar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="87099-216">`All` – all assets are used.</span></span>

### <a name="dotnetclitoolreference"></a><span data-ttu-id="87099-217">Dotnetclientoolreference</span><span class="sxs-lookup"><span data-stu-id="87099-217">DotNetCliToolReference</span></span>
<span data-ttu-id="87099-218">Bir `<DotNetCliToolReference>` öğe öğesi, kullanıcının proje bağlamında geri yüklemek istediği CLI aracını belirtir.</span><span class="sxs-lookup"><span data-stu-id="87099-218">A `<DotNetCliToolReference>` item element specifies the CLI tool that the user wants to restore in the context of the project.</span></span> <span data-ttu-id="87099-219">Bu, `tools` *Project. JSON*içindeki düğümün yerini alır.</span><span class="sxs-lookup"><span data-stu-id="87099-219">It's a replacement for the `tools` node in *project.json*.</span></span>

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

#### <a name="version"></a><span data-ttu-id="87099-220">Sürüm</span><span class="sxs-lookup"><span data-stu-id="87099-220">Version</span></span>

<span data-ttu-id="87099-221">`Version`geri yüklenecek paketin sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="87099-221">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="87099-222">Öznitelik, [NuGet sürüm oluşturma](/nuget/create-packages/dependency-versions#version-ranges) şemasının kurallarına uyar.</span><span class="sxs-lookup"><span data-stu-id="87099-222">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="87099-223">Varsayılan davranış, tam bir sürüm eşleşmedir.</span><span class="sxs-lookup"><span data-stu-id="87099-223">The default behavior is an exact version match.</span></span> <span data-ttu-id="87099-224">Örneğin belirtme `Version="1.2.3"` , paketin tam 1.2.3 sürümü için NuGet `[1.2.3]` gösterimine eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="87099-224">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

### <a name="runtimeidentifiers"></a><span data-ttu-id="87099-225">Runtimetanımlayıcıtanımlayıcıları</span><span class="sxs-lookup"><span data-stu-id="87099-225">RuntimeIdentifiers</span></span>

<span data-ttu-id="87099-226">Property öğesi, proje için bir [çalışma zamanı tanımlayıcıları (RID 'ler)](../rid-catalog.md) için noktalı virgülle ayrılmış bir liste belirtmenize olanak tanır. `<RuntimeIdentifiers>`</span><span class="sxs-lookup"><span data-stu-id="87099-226">The `<RuntimeIdentifiers>` property element lets you specify a semicolon-delimited list of [Runtime Identifiers (RIDs)](../rid-catalog.md) for the project.</span></span>
<span data-ttu-id="87099-227">RID 'Ler, kendi kendine kapsanan dağıtımları yayımlamayı etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="87099-227">RIDs enable publishing self-contained deployments.</span></span>

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a><span data-ttu-id="87099-228">Runtimeıdentifier</span><span class="sxs-lookup"><span data-stu-id="87099-228">RuntimeIdentifier</span></span>

<span data-ttu-id="87099-229">Property öğesi, proje için yalnızca bir [çalışma zamanı tanımlayıcısı (RID)](../rid-catalog.md) belirtmenize olanak tanır. `<RuntimeIdentifier>`</span><span class="sxs-lookup"><span data-stu-id="87099-229">The `<RuntimeIdentifier>` property element allows you to specify only one [Runtime Identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="87099-230">RID, kendi kendine içerilen bir dağıtımı yayımlamayı mümkün.</span><span class="sxs-lookup"><span data-stu-id="87099-230">The RID enables publishing a self-contained deployment.</span></span>

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

<span data-ttu-id="87099-231">Çoklu `<RuntimeIdentifiers>` çalışma zamanları için yayımlamanız gerekiyorsa bunun yerine (plural) kullanın.</span><span class="sxs-lookup"><span data-stu-id="87099-231">Use `<RuntimeIdentifiers>` (plural) instead if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="87099-232">`<RuntimeIdentifier>`yalnızca tek bir çalışma zamanı gerektiğinde daha hızlı derlemeler sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="87099-232">`<RuntimeIdentifier>` can provide faster builds when only a single runtime is required.</span></span>

### <a name="packagetargetfallback"></a><span data-ttu-id="87099-233">PackageTargetFallback</span><span class="sxs-lookup"><span data-stu-id="87099-233">PackageTargetFallback</span></span>

<span data-ttu-id="87099-234">Özellik `<PackageTargetFallback>` öğesi, paketler geri yüklenirken kullanılacak bir dizi uyumlu hedef belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="87099-234">The `<PackageTargetFallback>` property element allows you to specify a set of compatible targets to be used when restoring packages.</span></span> <span data-ttu-id="87099-235">DotNet [TXE (hedef x takma adı)](/nuget/schema/target-frameworks) kullanan paketlere bir DotNet TXD bildirmeyin paketlerle çalışmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="87099-235">It's designed to allow packages that use the dotnet [TxM (Target x Moniker)](/nuget/schema/target-frameworks) to operate with packages that don't declare a dotnet TxM.</span></span> <span data-ttu-id="87099-236">Projeniz DotNet TXI kullanıyorsa, DotNet olmayan platformların DotNet ile uyumlu olmasını sağlamak üzere projenize eklemediğiniz sürece, `<PackageTargetFallback>` bağımlı olduğu tüm paketlerin DotNet TXD olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="87099-236">If your project uses the dotnet TxM, then all the packages it depends on must also have a dotnet TxM, unless you add the `<PackageTargetFallback>` to your project in order to allow non-dotnet platforms to be compatible with dotnet.</span></span>

<span data-ttu-id="87099-237">Aşağıdaki örnek, projenizdeki tüm hedeflerin geri dönüşlerinizi sağlar:</span><span class="sxs-lookup"><span data-stu-id="87099-237">The following example provides the fallbacks for all targets in your project:</span></span>

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

<span data-ttu-id="87099-238">Aşağıdaki örnek yalnızca `netcoreapp2.1` hedef için geri dönüşi belirtir:</span><span class="sxs-lookup"><span data-stu-id="87099-238">The following example specifies the fallbacks only for the `netcoreapp2.1` target:</span></span>

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp2.1'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="nuget-metadata-properties"></a><span data-ttu-id="87099-239">NuGet meta veri özellikleri</span><span class="sxs-lookup"><span data-stu-id="87099-239">NuGet metadata properties</span></span>

<span data-ttu-id="87099-240">MSBuild 'e taşıma ile, *Project. JSON* 'dan *. csproj* dosyalarına bir NuGet paketi paketleme sırasında kullanılan giriş meta verilerini taşıdık.</span><span class="sxs-lookup"><span data-stu-id="87099-240">With the move to MSBuild, we have moved the input metadata that is used when packing a NuGet package from *project.json* to *.csproj* files.</span></span> <span data-ttu-id="87099-241">Girdiler MSBuild özellikleridir, bu nedenle bir `<PropertyGroup>` grup içinde gitmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="87099-241">The inputs are MSBuild properties so they have to go within a `<PropertyGroup>` group.</span></span> <span data-ttu-id="87099-242">Aşağıda, SDK 'nın parçası olan `dotnet pack` komutu `Pack` veya MSBuild hedefini kullanırken paketleme işlemine giriş olarak kullanılan özelliklerin listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="87099-242">The following is the list of properties that are used as inputs to the packing process when using the `dotnet pack` command or the `Pack` MSBuild target that is part of the SDK.</span></span>

### <a name="ispackable"></a><span data-ttu-id="87099-243">Ispackable</span><span class="sxs-lookup"><span data-stu-id="87099-243">IsPackable</span></span>

<span data-ttu-id="87099-244">Projenin paketlenemeyeceğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="87099-244">A Boolean value that specifies whether the project can be packed.</span></span> <span data-ttu-id="87099-245">Varsayılan değer `true` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="87099-245">The default value is `true`.</span></span>

### <a name="packageversion"></a><span data-ttu-id="87099-246">PackageVersion</span><span class="sxs-lookup"><span data-stu-id="87099-246">PackageVersion</span></span>

<span data-ttu-id="87099-247">Elde edilen paketin sahip olacağı sürümü belirtir.</span><span class="sxs-lookup"><span data-stu-id="87099-247">Specifies the version that the resulting package will have.</span></span> <span data-ttu-id="87099-248">Tüm NuGet sürüm dizesi formlarını kabul eder.</span><span class="sxs-lookup"><span data-stu-id="87099-248">Accepts all forms of NuGet version string.</span></span> <span data-ttu-id="87099-249">Varsayılan değeri,, yani `$(Version)`, projedeki özelliğinin `Version` değeridir.</span><span class="sxs-lookup"><span data-stu-id="87099-249">Default is the value of `$(Version)`, that is, of the property `Version` in the project.</span></span>

### <a name="packageid"></a><span data-ttu-id="87099-250">PackageId</span><span class="sxs-lookup"><span data-stu-id="87099-250">PackageId</span></span>

<span data-ttu-id="87099-251">Sonuç paketinin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="87099-251">Specifies the name for the resulting package.</span></span> <span data-ttu-id="87099-252">Belirtilmemişse, `pack` işlem varsayılan `AssemblyName` olarak paketin adı ile veya dizin adını kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="87099-252">If not specified, the `pack` operation will default to using the `AssemblyName` or directory name as the name of the package.</span></span>

### <a name="title"></a><span data-ttu-id="87099-253">Başlık</span><span class="sxs-lookup"><span data-stu-id="87099-253">Title</span></span>

<span data-ttu-id="87099-254">Genellikle, Kullanıcı arabiriminde kullanılan ve Visual Studio 'da paket yöneticisi olarak görüntülenen, paketin kolay bir başlığı.</span><span class="sxs-lookup"><span data-stu-id="87099-254">A human-friendly title of the package, typically used in UI displays as on nuget.org and the Package Manager in Visual Studio.</span></span> <span data-ttu-id="87099-255">Belirtilmemişse, bunun yerine paket KIMLIĞI kullanılır.</span><span class="sxs-lookup"><span data-stu-id="87099-255">If not specified, the package ID is used instead.</span></span>

### <a name="authors"></a><span data-ttu-id="87099-256">Yazarlar</span><span class="sxs-lookup"><span data-stu-id="87099-256">Authors</span></span>

<span data-ttu-id="87099-257">Nuget.org üzerindeki profil adlarıyla eşleşen paket yazarları için noktalı virgülle ayrılmış bir liste. Bunlar, nuget.org üzerindeki NuGet galerisinde görüntülenir ve aynı yazarlara göre çapraz başvuru için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="87099-257">A semicolon-separated list of packages authors, matching the profile names on nuget.org. These are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span>

### <a name="packagedescription"></a><span data-ttu-id="87099-258">PackageDescription</span><span class="sxs-lookup"><span data-stu-id="87099-258">PackageDescription</span></span>

<span data-ttu-id="87099-259">UI görüntüleme paketinin uzun açıklaması.</span><span class="sxs-lookup"><span data-stu-id="87099-259">A long description of the package for UI display.</span></span>

### <a name="description"></a><span data-ttu-id="87099-260">Açıklama</span><span class="sxs-lookup"><span data-stu-id="87099-260">Description</span></span>

<span data-ttu-id="87099-261">Derleme için uzun bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="87099-261">A long description for the assembly.</span></span> <span data-ttu-id="87099-262">Belirtilmezse `PackageDescription` , bu özellik paketin açıklaması olarak da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="87099-262">If `PackageDescription` is not specified then this property is also used as the description of the package.</span></span>

### <a name="copyright"></a><span data-ttu-id="87099-263">Yaptırımlar</span><span class="sxs-lookup"><span data-stu-id="87099-263">Copyright</span></span>

<span data-ttu-id="87099-264">Paket için telif hakkı ayrıntıları.</span><span class="sxs-lookup"><span data-stu-id="87099-264">Copyright details for the package.</span></span>

### <a name="packagerequirelicenseacceptance"></a><span data-ttu-id="87099-265">PackageRequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="87099-265">PackageRequireLicenseAcceptance</span></span>

<span data-ttu-id="87099-266">İstemcinin paketi yüklemeden önce paket lisansını kabul etmesini isteyip istemeyeceğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="87099-266">A Boolean value that specifies whether the client must prompt the consumer to accept the package license before installing the package.</span></span> <span data-ttu-id="87099-267">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="87099-267">The default is `false`.</span></span>

### <a name="packagelicenseexpression"></a><span data-ttu-id="87099-268">PackageLicenseExpression</span><span class="sxs-lookup"><span data-stu-id="87099-268">PackageLicenseExpression</span></span>

<span data-ttu-id="87099-269">Bir [Spdx lisans tanımlayıcısı](https://spdx.org/licenses/) veya ifadesi.</span><span class="sxs-lookup"><span data-stu-id="87099-269">An [SPDX license identifier](https://spdx.org/licenses/) or expression.</span></span> <span data-ttu-id="87099-270">Örneğin, uygulamasında yönetilen Hyper-V konakları olarak eklemek için aşağıdaki yordamı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87099-270">For example, `Apache-2.0`.</span></span>

<span data-ttu-id="87099-271">[Spdx lisans tanımlayıcılarının](https://spdx.org/licenses/)listesi aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="87099-271">Here is the complete list of [SPDX license identifiers](https://spdx.org/licenses/).</span></span> <span data-ttu-id="87099-272">NuGet.org, lisans türü ifadesi kullanılırken yalnızca OSı veya FSF onaylı lisansları kabul eder.</span><span class="sxs-lookup"><span data-stu-id="87099-272">NuGet.org accepts only OSI or FSF approved licenses when using license type expression.</span></span>

<span data-ttu-id="87099-273">Lisans ifadelerinin tam sözdizimi aşağıda, [Abnf](https://tools.ietf.org/html/rfc5234)içinde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="87099-273">The exact syntax of the license expressions is described below in [ABNF](https://tools.ietf.org/html/rfc5234).</span></span>

```cli
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
> <span data-ttu-id="87099-274">Tek seferde yalnızca `PackageLicenseExpression`biri `PackageLicenseFile` ve `PackageLicenseUrl` belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="87099-274">Only one of `PackageLicenseExpression`, `PackageLicenseFile` and `PackageLicenseUrl` can be specified at a time.</span></span>

### <a name="packagelicensefile"></a><span data-ttu-id="87099-275">PackageLicenseFile</span><span class="sxs-lookup"><span data-stu-id="87099-275">PackageLicenseFile</span></span>

<span data-ttu-id="87099-276">Bir spdx tanımlayıcısı atanmamış bir lisans kullanıyorsanız veya özel bir lisans ise (Aksi takdirde `PackageLicenseExpression` tercih edilir) paket içindeki bir lisans dosyasının yolu</span><span class="sxs-lookup"><span data-stu-id="87099-276">Path to a license file within the package if you are using a license that hasn’t been assigned an SPDX identifier, or it is a custom license (Otherwise `PackageLicenseExpression` is preferred)</span></span>

<span data-ttu-id="87099-277">`PackageLicenseUrl`, İle`PackageLicenseExpression` birleştirilemez ve Visual Studio 15.9.4, .NET SDK 2.1.502 veya 2.2.101 ya da daha yeni bir sürümü gerektirir.</span><span class="sxs-lookup"><span data-stu-id="87099-277">Replaces `PackageLicenseUrl`, can't be combined with `PackageLicenseExpression` and requires Visual Studio 15.9.4, .NET SDK 2.1.502 or 2.2.101, or newer.</span></span>

<span data-ttu-id="87099-278">Lisans dosyasının paketlenmiş olduğundan emin olmanız gerekir, bu işlem, örnek kullanım:</span><span class="sxs-lookup"><span data-stu-id="87099-278">You will need to ensure the license file is packed by adding it explicitly to the project, example usage:</span></span>

```xml
<PropertyGroup>
  <PackageLicenseFile>LICENSE.txt</PackageLicenseFile>
</PropertyGroup>
<ItemGroup>
  <None Include="licenses\LICENSE.txt" Pack="true" PackagePath="$(PackageLicenseFile)"/>
</ItemGroup>
```

### <a name="packagelicenseurl"></a><span data-ttu-id="87099-279">PackageLicenseUrl</span><span class="sxs-lookup"><span data-stu-id="87099-279">PackageLicenseUrl</span></span>

<span data-ttu-id="87099-280">Pakete uygulanabilen lisansın URL 'SI.</span><span class="sxs-lookup"><span data-stu-id="87099-280">An URL to the license that is applicable to the package.</span></span> <span data-ttu-id="87099-281">(_Visual Studio 15.9.4, .NET SDK 2.1.502 ve 2.2.101 'den beri kullanım dışı_)</span><span class="sxs-lookup"><span data-stu-id="87099-281">(_deprecated since Visual Studio 15.9.4, .NET SDK 2.1.502 and 2.2.101_)</span></span>

### <a name="packageiconurl"></a><span data-ttu-id="87099-282">PackageIconUrl</span><span class="sxs-lookup"><span data-stu-id="87099-282">PackageIconUrl</span></span>

<span data-ttu-id="87099-283">Kullanıcı arabirimi görüntüsündeki paketin simgesi olarak kullanılacak, saydam arka planlı bir 64x64 görüntüsünün URL 'SI.</span><span class="sxs-lookup"><span data-stu-id="87099-283">A URL for a 64x64 image with transparent background to use as the icon for the package in UI display.</span></span>

### <a name="packagereleasenotes"></a><span data-ttu-id="87099-284">PackageReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="87099-284">PackageReleaseNotes</span></span>

<span data-ttu-id="87099-285">Paket için sürüm notları.</span><span class="sxs-lookup"><span data-stu-id="87099-285">Release notes for the package.</span></span>

### <a name="packagetags"></a><span data-ttu-id="87099-286">PackageTags</span><span class="sxs-lookup"><span data-stu-id="87099-286">PackageTags</span></span>

<span data-ttu-id="87099-287">Paketi atayan etiketlerin noktalı virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="87099-287">A semicolon-delimited list of tags that designates the package.</span></span>

### <a name="packageoutputpath"></a><span data-ttu-id="87099-288">PackageOutputPath</span><span class="sxs-lookup"><span data-stu-id="87099-288">PackageOutputPath</span></span>

<span data-ttu-id="87099-289">Paketlenmiş paketin bırakılacak çıkış yolunu belirler.</span><span class="sxs-lookup"><span data-stu-id="87099-289">Determines the output path in which the packed package will be dropped.</span></span> <span data-ttu-id="87099-290">Varsayılan değer `$(OutputPath)`.</span><span class="sxs-lookup"><span data-stu-id="87099-290">Default is `$(OutputPath)`.</span></span>

### <a name="includesymbols"></a><span data-ttu-id="87099-291">Includesymbols</span><span class="sxs-lookup"><span data-stu-id="87099-291">IncludeSymbols</span></span>
<span data-ttu-id="87099-292">Bu Boole değeri, paketin proje paketedildiğinde ek bir sembol paketi oluşturup oluşturmayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="87099-292">This Boolean value indicates whether the package should create an additional symbols package when the project is packed.</span></span> <span data-ttu-id="87099-293">Semboller paketinin biçimi, `SymbolPackageFormat` özelliği tarafından denetlenir.</span><span class="sxs-lookup"><span data-stu-id="87099-293">The symbols package's format is controlled by the `SymbolPackageFormat` property.</span></span>

### <a name="symbolpackageformat"></a><span data-ttu-id="87099-294">SymbolPackageFormat</span><span class="sxs-lookup"><span data-stu-id="87099-294">SymbolPackageFormat</span></span>
<span data-ttu-id="87099-295">Semboller paketinin biçimini belirtir.</span><span class="sxs-lookup"><span data-stu-id="87099-295">Specifies the format of the symbols package.</span></span> <span data-ttu-id="87099-296">"Symbols. nupkg" ise, pdb 'leri, dll 'Ler ve diğer çıktı dosyalarını içeren *. Symbols. nupkg* Uzantısı ile eski bir sembol paketi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="87099-296">If "symbols.nupkg", a legacy symbols package will be created with a *.symbols.nupkg* extension containing PDBs, DLLs, and other output files.</span></span> <span data-ttu-id="87099-297">"Snupkg" ise, taşınabilir pdb 'leri içeren bir snupkg sembol paketi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="87099-297">If "snupkg", a snupkg symbol package will be created containing the portable PDBs.</span></span> <span data-ttu-id="87099-298">Varsayılan değer "symbols. nupkg" dır.</span><span class="sxs-lookup"><span data-stu-id="87099-298">Default is "symbols.nupkg".</span></span>

### <a name="includesource"></a><span data-ttu-id="87099-299">IncludeSource</span><span class="sxs-lookup"><span data-stu-id="87099-299">IncludeSource</span></span>

<span data-ttu-id="87099-300">Bu Boole değeri, paket işleminin bir kaynak paketi oluşturup oluşturmayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="87099-300">This Boolean value indicates whether the pack process should create a source package.</span></span> <span data-ttu-id="87099-301">Kaynak paket, kitaplığın kaynak kodunu ve PDB dosyalarını içerir.</span><span class="sxs-lookup"><span data-stu-id="87099-301">The source package contains the library's source code as well as PDB files.</span></span> <span data-ttu-id="87099-302">Kaynak dosyalar, elde edilen paket `src/ProjectName` dosyasındaki dizinin altına yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="87099-302">Source files are put under the `src/ProjectName` directory in the resulting package file.</span></span>

### <a name="istool"></a><span data-ttu-id="87099-303">IsTool</span><span class="sxs-lookup"><span data-stu-id="87099-303">IsTool</span></span>

<span data-ttu-id="87099-304">Tüm çıkış dosyalarının *lib* klasörü yerine *Araçlar* klasörüne kopyalanıp kopyalanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="87099-304">Specifies whether all output files are copied to the *tools* folder instead of the *lib* folder.</span></span> <span data-ttu-id="87099-305">Bunun, `DotNetCliTool` `PackageType` *. csproj* dosyasında ayarıyla belirtilen öğesinden farklı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="87099-305">Note that this is different from a `DotNetCliTool` which is specified by setting the `PackageType` in the *.csproj* file.</span></span>

### <a name="repositoryurl"></a><span data-ttu-id="87099-306">Depourl 'Si</span><span class="sxs-lookup"><span data-stu-id="87099-306">RepositoryUrl</span></span>

<span data-ttu-id="87099-307">Paketin kaynak kodunun bulunduğu ve/veya oluşturulduğu deponun URL 'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="87099-307">Specifies the URL for the repository where the source code for the package resides and/or from which it's being built.</span></span>

### <a name="repositorytype"></a><span data-ttu-id="87099-308">Repositorytype parametrelerinin sağlanması</span><span class="sxs-lookup"><span data-stu-id="87099-308">RepositoryType</span></span>

<span data-ttu-id="87099-309">Deponun türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="87099-309">Specifies the type of the repository.</span></span> <span data-ttu-id="87099-310">Varsayılan değer "git" dir.</span><span class="sxs-lookup"><span data-stu-id="87099-310">Default is "git".</span></span>

### <a name="nopackageanalysis"></a><span data-ttu-id="87099-311">NoPackageAnalysis</span><span class="sxs-lookup"><span data-stu-id="87099-311">NoPackageAnalysis</span></span>

<span data-ttu-id="87099-312">Paketi derlemeden sonra paketin paket analizini çalıştırmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="87099-312">Specifies that pack should not run package analysis after building the package.</span></span>

### <a name="minclientversion"></a><span data-ttu-id="87099-313">minClientVersion</span><span class="sxs-lookup"><span data-stu-id="87099-313">MinClientVersion</span></span>

<span data-ttu-id="87099-314">NuGet. exe ve Visual Studio Paket Yöneticisi tarafından zorlanan, bu paketi yükleyesağlayan NuGet istemcisinin en düşük sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="87099-314">Specifies the minimum version of the NuGet client that can install this package, enforced by nuget.exe and the Visual Studio Package Manager.</span></span>

### <a name="includebuildoutput"></a><span data-ttu-id="87099-315">IncludeBuildOutput</span><span class="sxs-lookup"><span data-stu-id="87099-315">IncludeBuildOutput</span></span>

<span data-ttu-id="87099-316">Bu Boole değerleri, derleme çıkış derlemelerinin *. nupkg* dosyasına paketedilip edilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="87099-316">This Boolean values specifies whether the build output assemblies should be packed into the *.nupkg* file or not.</span></span>

### <a name="includecontentinpack"></a><span data-ttu-id="87099-317">IncludeContentInPack</span><span class="sxs-lookup"><span data-stu-id="87099-317">IncludeContentInPack</span></span>

<span data-ttu-id="87099-318">Bu Boole değeri, türüne `Content` sahip olan öğelerin elde edilen pakete otomatik olarak dahil edilip edilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="87099-318">This Boolean value specifies whether any items that have a type of `Content` will be included in the resulting package automatically.</span></span> <span data-ttu-id="87099-319">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="87099-319">The default is `true`.</span></span>

### <a name="buildoutputtargetfolder"></a><span data-ttu-id="87099-320">BuildOutputTargetFolder</span><span class="sxs-lookup"><span data-stu-id="87099-320">BuildOutputTargetFolder</span></span>

<span data-ttu-id="87099-321">Çıkış derlemelerinin yerleştirileceği klasörü belirtir.</span><span class="sxs-lookup"><span data-stu-id="87099-321">Specifies the folder where to place the output assemblies.</span></span> <span data-ttu-id="87099-322">Çıkış derlemeleri (ve diğer çıkış dosyaları) ilgili çerçeve klasörlerine kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="87099-322">The output assemblies (and other output files) are copied into their respective framework folders.</span></span>

### <a name="contenttargetfolders"></a><span data-ttu-id="87099-323">ContentTargetFolders</span><span class="sxs-lookup"><span data-stu-id="87099-323">ContentTargetFolders</span></span>

<span data-ttu-id="87099-324">Bu özellik, kendileri için belirtilmemişse, tüm içerik dosyalarının gitmesi `PackagePath` gereken varsayılan konumu belirtir.</span><span class="sxs-lookup"><span data-stu-id="87099-324">This property specifies the default location of where all the content files should go if `PackagePath` is not specified for them.</span></span> <span data-ttu-id="87099-325">Varsayılan değer "Content; contentFiles" dır.</span><span class="sxs-lookup"><span data-stu-id="87099-325">The default value is "content;contentFiles".</span></span>

### <a name="nuspecfile"></a><span data-ttu-id="87099-326">Nusguus dosyası</span><span class="sxs-lookup"><span data-stu-id="87099-326">NuspecFile</span></span>

<span data-ttu-id="87099-327">Paketleme için kullanılan *. nuspec* dosyasının göreli veya mutlak yolu.</span><span class="sxs-lookup"><span data-stu-id="87099-327">Relative or absolute path to the *.nuspec* file being used for packing.</span></span>

> [!NOTE]
> <span data-ttu-id="87099-328">*. Nuspec* dosyası belirtilmişse, **yalnızca** paketleme bilgileri için kullanılır ve projelerdeki tüm bilgiler kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="87099-328">If the *.nuspec* file is specified, it's used **exclusively** for packaging information and any information in the projects is not used.</span></span>

### <a name="nuspecbasepath"></a><span data-ttu-id="87099-329">Nusgubasepath</span><span class="sxs-lookup"><span data-stu-id="87099-329">NuspecBasePath</span></span>

<span data-ttu-id="87099-330">*. Nuspec* dosyasının temel yolu.</span><span class="sxs-lookup"><span data-stu-id="87099-330">Base path for the *.nuspec* file.</span></span>

### <a name="nuspecproperties"></a><span data-ttu-id="87099-331">Nus, Properties</span><span class="sxs-lookup"><span data-stu-id="87099-331">NuspecProperties</span></span>

<span data-ttu-id="87099-332">Anahtar = değer çiftlerinin noktalı virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="87099-332">Semicolon separated list of key=value pairs.</span></span>

## <a name="assemblyinfo-properties"></a><span data-ttu-id="87099-333">AssemblyInfo özellikleri</span><span class="sxs-lookup"><span data-stu-id="87099-333">AssemblyInfo properties</span></span>

<span data-ttu-id="87099-334">Genellikle *AssemblyInfo* dosyasında bulunan [derleme öznitelikleri](../../standard/assembly/set-attributes.md) artık özelliklerden otomatik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="87099-334">[Assembly attributes](../../standard/assembly/set-attributes.md) that were typically present in an *AssemblyInfo* file are now automatically generated from properties.</span></span>

### <a name="properties-per-attribute"></a><span data-ttu-id="87099-335">Öznitelik başına Özellikler</span><span class="sxs-lookup"><span data-stu-id="87099-335">Properties per attribute</span></span>

<span data-ttu-id="87099-336">Her öznitelik, aşağıdaki tabloda gösterildiği gibi, içeriğini denetleyen ve diğeri oluşturmayı devre dışı bırakan bir özelliğe sahiptir:</span><span class="sxs-lookup"><span data-stu-id="87099-336">Each attribute has a property that control its content and another to disable its generation as shown in the following table:</span></span>

| <span data-ttu-id="87099-337">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="87099-337">Attribute</span></span>                                                      | <span data-ttu-id="87099-338">Özellik</span><span class="sxs-lookup"><span data-stu-id="87099-338">Property</span></span>               | <span data-ttu-id="87099-339">Devre dışı bırakılacak Özellik</span><span class="sxs-lookup"><span data-stu-id="87099-339">Property to disable</span></span>                             |
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

<span data-ttu-id="87099-340">Notlar:</span><span class="sxs-lookup"><span data-stu-id="87099-340">Notes:</span></span>

* <span data-ttu-id="87099-341">`AssemblyVersion`ve `FileVersion` varsayılan, sonek `$(Version)` olmadan değerini alır.</span><span class="sxs-lookup"><span data-stu-id="87099-341">`AssemblyVersion` and `FileVersion` default is to take the value of `$(Version)` without suffix.</span></span> <span data-ttu-id="87099-342">Örneğin `$(Version)` , ise `1.2.3-beta.4`, değer olacaktır `1.2.3`.</span><span class="sxs-lookup"><span data-stu-id="87099-342">For example, if `$(Version)` is `1.2.3-beta.4`, then the value would be `1.2.3`.</span></span>
* <span data-ttu-id="87099-343">`InformationalVersion`Varsayılan değer olarak değeridir `$(Version)`.</span><span class="sxs-lookup"><span data-stu-id="87099-343">`InformationalVersion` defaults to the value of `$(Version)`.</span></span>
* <span data-ttu-id="87099-344">`InformationalVersion`, özelliği varsa eklenmiş olur. `$(SourceRevisionId)`</span><span class="sxs-lookup"><span data-stu-id="87099-344">`InformationalVersion` has `$(SourceRevisionId)` appended if the property is present.</span></span> <span data-ttu-id="87099-345">Kullanılarak `IncludeSourceRevisionInInformationalVersion`devre dışı bırakılabilir.</span><span class="sxs-lookup"><span data-stu-id="87099-345">It can be disabled using `IncludeSourceRevisionInInformationalVersion`.</span></span>
* <span data-ttu-id="87099-346">`Copyright`Ayrıca, NuGet meta verileri için de Özelliklerkullanılır.`Description`</span><span class="sxs-lookup"><span data-stu-id="87099-346">`Copyright` and `Description` properties are also used for NuGet metadata.</span></span>
* <span data-ttu-id="87099-347">`Configuration`Tüm derleme işlemiyle paylaşılır ve `--configuration` `dotnet` komutları parametresi aracılığıyla ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="87099-347">`Configuration` is shared with all the build process and set via the `--configuration` parameter of `dotnet` commands.</span></span>

### <a name="generateassemblyinfo"></a><span data-ttu-id="87099-348">Generateassemblyınfo</span><span class="sxs-lookup"><span data-stu-id="87099-348">GenerateAssemblyInfo</span></span>

<span data-ttu-id="87099-349">Tüm AssemblyInfo üretimini etkinleştiren veya devre dışı bırakan bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="87099-349">A Boolean that enable or disable all the AssemblyInfo generation.</span></span> <span data-ttu-id="87099-350">Varsayılan değer `true` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="87099-350">The default value is `true`.</span></span>

### <a name="generatedassemblyinfofile"></a><span data-ttu-id="87099-351">GeneratedAssemblyInfoFile</span><span class="sxs-lookup"><span data-stu-id="87099-351">GeneratedAssemblyInfoFile</span></span>

<span data-ttu-id="87099-352">Oluşturulan derleme bilgileri dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="87099-352">The path of the generated assembly info file.</span></span> <span data-ttu-id="87099-353">Varsayılan olarak `$(IntermediateOutputPath)` (obj) dizinindeki bir dosya.</span><span class="sxs-lookup"><span data-stu-id="87099-353">Default to a file in the `$(IntermediateOutputPath)` (obj) directory.</span></span>
