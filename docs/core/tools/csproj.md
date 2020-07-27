---
title: .NET Core için csproj biçimine eklemeler
description: Mevcut ve .NET Core csproj dosyaları arasındaki farklılıklar hakkında bilgi edinin
ms.date: 04/08/2019
ms.openlocfilehash: 619f6121d9d476726c3d422e50737ff3d622f444
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164922"
---
# <a name="additions-to-the-csproj-format-for-net-core"></a><span data-ttu-id="c44bb-103">.NET Core için csproj biçimine eklemeler</span><span class="sxs-lookup"><span data-stu-id="c44bb-103">Additions to the csproj format for .NET Core</span></span>

<span data-ttu-id="c44bb-104">Bu belgede, *project.js* 'tan *csproj* ve [MSBuild](https://github.com/Microsoft/MSBuild)'e taşıma kapsamında proje dosyalarına eklenen değişiklikler özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-104">This document outlines the changes that were added to the project files as part of the move from *project.json* to *csproj* and [MSBuild](https://github.com/Microsoft/MSBuild).</span></span> <span data-ttu-id="c44bb-105">Genel proje dosyası sözdizimi ve başvurusu hakkında daha fazla bilgi için bkz. [MSBuild proje dosyası](/visualstudio/msbuild/msbuild-project-file-schema-reference) belgeleri.</span><span class="sxs-lookup"><span data-stu-id="c44bb-105">For more information about general project file syntax and reference, see [the MSBuild project file](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation.</span></span>

## <a name="implicit-package-references"></a><span data-ttu-id="c44bb-106">Örtük paket başvuruları</span><span class="sxs-lookup"><span data-stu-id="c44bb-106">Implicit package references</span></span>

<span data-ttu-id="c44bb-107">Meta paketlere, `<TargetFramework>` proje dosyanızın veya özelliğinde belirtilen hedef çatılar temelinde örtülü olarak başvurulur `<TargetFrameworks>` .</span><span class="sxs-lookup"><span data-stu-id="c44bb-107">Metapackages are implicitly referenced based on the target framework(s) specified in the `<TargetFramework>` or `<TargetFrameworks>` property of your project file.</span></span> <span data-ttu-id="c44bb-108">`<TargetFrameworks>``<TargetFramework>`belirtilmişse, sıralamayla bağımsız olarak yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="c44bb-108">`<TargetFrameworks>` is ignored if `<TargetFramework>` is specified, independent of order.</span></span>

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

### <a name="recommendations"></a><span data-ttu-id="c44bb-109">Öneriler</span><span class="sxs-lookup"><span data-stu-id="c44bb-109">Recommendations</span></span>

<span data-ttu-id="c44bb-110">`Microsoft.NETCore.App`Veya `NETStandard.Library` Metapackages örtük olarak başvurulduğundan, önerilen en iyi yöntemler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="c44bb-110">Since `Microsoft.NETCore.App` or `NETStandard.Library` metapackages are implicitly referenced, the following are our recommended best practices:</span></span>

- <span data-ttu-id="c44bb-111">.NET Core veya .NET Standard hedeflenirken, `Microsoft.NETCore.App` `NETStandard.Library` proje dosyanızdaki bir öğe aracılığıyla veya metapaketlerine açık bir başvuruya sahip olmaz `<PackageReference>` .</span><span class="sxs-lookup"><span data-stu-id="c44bb-111">When targeting .NET Core or .NET Standard, never have an explicit reference to the `Microsoft.NETCore.App` or `NETStandard.Library` metapackages via a `<PackageReference>` item in your project file.</span></span>
- <span data-ttu-id="c44bb-112">.NET Core 'u hedeflerken çalışma zamanının belirli bir sürümüne ihtiyacınız varsa, `<RuntimeFrameworkVersion>` metapackage 'e başvurmak yerine projenizdeki özelliğini (örneğin,) kullanmanız gerekir `1.0.4` .</span><span class="sxs-lookup"><span data-stu-id="c44bb-112">If you need a specific version of the runtime when targeting .NET Core, you should use the `<RuntimeFrameworkVersion>` property in your project (for example, `1.0.4`) instead of referencing the metapackage.</span></span>
  - <span data-ttu-id="c44bb-113">Bu, [kendi kendine kapsanan dağıtımlar](../deploying/index.md#publish-self-contained) kullanıyorsanız ve örneğin 1.0.0 LTS çalışma zamanının belirli bir düzeltme eki sürümüne ihtiyaç duyuyorsanız meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-113">This might happen if you are using [self-contained deployments](../deploying/index.md#publish-self-contained) and you need a specific patch version of 1.0.0 LTS runtime, for example.</span></span>
- <span data-ttu-id="c44bb-114">.NET Standard hedeflenirken metapackage 'in belirli bir sürümüne ihtiyacınız varsa `NETStandard.Library` , `<NetStandardImplicitPackageVersion>` özelliğini kullanabilir ve ihtiyacınız olan sürümü ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c44bb-114">If you need a specific version of the `NETStandard.Library` metapackage when targeting .NET Standard, you can use the `<NetStandardImplicitPackageVersion>` property and set the version you need.</span></span>
- <span data-ttu-id="c44bb-115">`Microsoft.NETCore.App`.NET Framework projelerindeki veya metapackage ya da başvuruları açıkça eklemeyin veya güncelleştirin `NETStandard.Library` .</span><span class="sxs-lookup"><span data-stu-id="c44bb-115">Don't explicitly add or update references to either the `Microsoft.NETCore.App` or `NETStandard.Library` metapackage in .NET Framework projects.</span></span> <span data-ttu-id="c44bb-116">`NETStandard.Library`.NET Standard tabanlı bir NuGet paketi kullanılırken herhangi bir sürümü gerekiyorsa, NuGet bu sürümü otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-116">If any version of `NETStandard.Library` is needed when using a .NET Standard-based NuGet package, NuGet automatically installs that version.</span></span>

## <a name="implicit-version-for-some-package-references"></a><span data-ttu-id="c44bb-117">Bazı paket başvurularının örtük sürümü</span><span class="sxs-lookup"><span data-stu-id="c44bb-117">Implicit version for some package references</span></span>

<span data-ttu-id="c44bb-118">Çoğu kullanımları, [`<PackageReference>`](#packagereference) `Version` kullanılacak NuGet paket sürümünü belirtmek için özniteliğini ayarlamayı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-118">Most usages of [`<PackageReference>`](#packagereference) require setting the `Version` attribute to specify the NuGet package version to be used.</span></span> <span data-ttu-id="c44bb-119">.NET Core 2,1 veya 2,2 kullanırken ve [Microsoft. aspnetcore. app](/aspnet/core/fundamentals/metapackage-app) ya da [Microsoft. Aspnetcore. All](/aspnet/core/fundamentals/metapackage)ile başvurulduğunda öznitelik gereksizdir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-119">When using .NET Core 2.1 or 2.2 and referencing [Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage-app) or [Microsoft.AspNetCore.All](/aspnet/core/fundamentals/metapackage), however, the  attribute is unnecessary.</span></span> <span data-ttu-id="c44bb-120">.NET Core SDK, bu paketlerin kullanılması gereken sürümünü otomatik olarak seçebilir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-120">The .NET Core SDK can automatically select the version of these packages that should be used.</span></span>

### <a name="recommendation"></a><span data-ttu-id="c44bb-121">Öneri</span><span class="sxs-lookup"><span data-stu-id="c44bb-121">Recommendation</span></span>

<span data-ttu-id="c44bb-122">`Microsoft.AspNetCore.App`Veya `Microsoft.AspNetCore.All` paketlerine başvurulduğunda, sürümünü belirtmeyin.</span><span class="sxs-lookup"><span data-stu-id="c44bb-122">When referencing the `Microsoft.AspNetCore.App` or `Microsoft.AspNetCore.All` packages, do not specify their version.</span></span> <span data-ttu-id="c44bb-123">Bir sürüm belirtilmişse, SDK uyarı NETSDK1071 üretebilir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-123">If a version is specified, the SDK may produce warning NETSDK1071.</span></span> <span data-ttu-id="c44bb-124">Bu uyarıyı onarmak için aşağıdaki örnekteki gibi paket sürümünü kaldırın:</span><span class="sxs-lookup"><span data-stu-id="c44bb-124">To fix this warning, remove the package version like in the following example:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.AspNetCore.App" />
</ItemGroup>
```

> <span data-ttu-id="c44bb-125">Bilinen sorun: .NET Core 2,1 SDK 'Sı yalnızca proje Microsoft. NET. SDK. Web 'i kullandığında bu söz dizimini destekliyordu.</span><span class="sxs-lookup"><span data-stu-id="c44bb-125">Known issue: the .NET Core 2.1 SDK only supported this syntax when the project also uses Microsoft.NET.Sdk.Web.</span></span> <span data-ttu-id="c44bb-126">Bu, .NET Core 2,2 SDK 'sında çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-126">This is resolved in the .NET Core 2.2 SDK.</span></span>

<span data-ttu-id="c44bb-127">ASP.NET Core metapaketlerine yapılan bu başvuruların çoğu normal NuGet paketlerinden biraz farklı bir davranışı vardır.</span><span class="sxs-lookup"><span data-stu-id="c44bb-127">These references to ASP.NET Core metapackages have a slightly different behavior from most normal NuGet packages.</span></span> <span data-ttu-id="c44bb-128">Bu metapaketleri kullanan uygulamaların [çerçeveye bağımlı dağıtımları](../deploying/index.md#publish-runtime-dependent) ASP.NET Core paylaşılan çerçeveden otomatik olarak yararlanır.</span><span class="sxs-lookup"><span data-stu-id="c44bb-128">[Framework-dependent deployments](../deploying/index.md#publish-runtime-dependent) of applications that use these metapackages automatically take advantage of the ASP.NET Core shared framework.</span></span> <span data-ttu-id="c44bb-129">Meta paketleri kullandığınızda başvurulan ASP.NET Core NuGet paketlerinden **hiçbir** varlık uygulamayla birlikte dağıtılır — ASP.NET Core paylaşılan çerçeve bu varlıkları içerir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-129">When you use the metapackages, **no** assets from the referenced ASP.NET Core NuGet packages are deployed with the application—the ASP.NET Core shared framework contains these assets.</span></span> <span data-ttu-id="c44bb-130">Paylaşılan çerçevede bulunan varlıklar, uygulama başlatma süresini artırmak üzere hedef platform için iyileştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-130">The assets in the shared framework are optimized for the target platform to improve application startup time.</span></span> <span data-ttu-id="c44bb-131">Paylaşılan Framework hakkında daha fazla bilgi için bkz. [.NET Core dağıtım paketleme](../distribution-packaging.md).</span><span class="sxs-lookup"><span data-stu-id="c44bb-131">For more information about shared framework, see [.NET Core distribution packaging](../distribution-packaging.md).</span></span>

<span data-ttu-id="c44bb-132">Bir *Sürüm belirtilmişse* , çerçeveye bağımlı dağıtımlar için ASP.NET Core paylaşılan Framework 'ün *En düşük* sürümü ve kendi içinde olan dağıtımlar için *tam* sürüm olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-132">If a version *is* specified, it's treated as the *minimum* version of ASP.NET Core shared framework for framework-dependent deployments and as an *exact* version for self-contained deployments.</span></span> <span data-ttu-id="c44bb-133">Bu, aşağıdaki sonuçlara sahip olabilir:</span><span class="sxs-lookup"><span data-stu-id="c44bb-133">This can have the following consequences:</span></span>

- <span data-ttu-id="c44bb-134">Sunucuda yüklü ASP.NET Core sürümü, PackageReference üzerinde belirtilen sürümden küçükse .NET Core işlemi başlayamaz.</span><span class="sxs-lookup"><span data-stu-id="c44bb-134">If the version of ASP.NET Core installed on the server is less than the version specified on the PackageReference, the .NET Core process fails to launch.</span></span> <span data-ttu-id="c44bb-135">Metapackage güncelleştirmeleri, Azure gibi barındırma ortamlarında güncelleştirmeler kullanılabilir hale getirilinceye kadar sıklıkla NuGet.org üzerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-135">Updates to the metapackage are often available on NuGet.org before updates have been made available in hosting environments such as Azure.</span></span> <span data-ttu-id="c44bb-136">PackageReference üzerindeki sürümün ASP.NET Core güncelleştirilmesi, dağıtılan bir uygulamanın başarısız olmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-136">Updating the version on the PackageReference to ASP.NET Core could cause a deployed application to fail.</span></span>
- <span data-ttu-id="c44bb-137">Uygulama [kendi içindeki bir dağıtım](../deploying/index.md#publish-self-contained)olarak dağıtılırsa, uygulama .NET Core için en son güvenlik güncelleştirmelerini içermeyebilir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-137">If the application is deployed as a [self-contained deployment](../deploying/index.md#publish-self-contained), the application may not contain the latest security updates to .NET Core.</span></span> <span data-ttu-id="c44bb-138">Bir sürüm belirtilmediğinde, SDK otomatik olarak kapsanan dağıtıma en yeni ASP.NET Core sürümünü ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-138">When a version isn't specified, the SDK can automatically include the newest version of ASP.NET Core in the self-contained deployment.</span></span>

## <a name="default-compilation-includes-in-net-core-projects"></a><span data-ttu-id="c44bb-139">.NET Core projelerinde varsayılan derleme dahildir</span><span class="sxs-lookup"><span data-stu-id="c44bb-139">Default compilation includes in .NET Core projects</span></span>

<span data-ttu-id="c44bb-140">En son SDK sürümlerindeki *csproj* biçimine geçiş ile, derleme öğeleri ve katıştırılmış kaynaklar için varsayılan ekleme ve DıŞMALARı SDK Özellikler dosyalarına taşıdık.</span><span class="sxs-lookup"><span data-stu-id="c44bb-140">With the move to the *csproj* format in the latest SDK versions, we've moved the default includes and excludes for compile items and embedded resources to the SDK properties files.</span></span> <span data-ttu-id="c44bb-141">Bu, artık proje dosyanızda bu öğeleri belirtmeniz gerekmediği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-141">This means that you no longer need to specify these items in your project file.</span></span>

<span data-ttu-id="c44bb-142">Bunu yapmanın asıl nedeni, proje dosyanızdaki dağınıklığı azaltmaktır.</span><span class="sxs-lookup"><span data-stu-id="c44bb-142">The main reason for doing this is to reduce the clutter in your project file.</span></span> <span data-ttu-id="c44bb-143">SDK 'da bulunan varsayılanlar en yaygın kullanım durumlarını kapsamalıdır, bu nedenle bunları oluşturduğunuz her projede tekrarlamaya gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="c44bb-143">The defaults that are present in the SDK should cover most common use cases, so there is no need to repeat them in every project that you create.</span></span> <span data-ttu-id="c44bb-144">Bu, anlaşılması çok daha kolay olan daha küçük proje dosyalarına ve gerekirse el ile düzenlemeye yol açar.</span><span class="sxs-lookup"><span data-stu-id="c44bb-144">This leads to smaller project files that are much easier to understand as well as edit by hand, if needed.</span></span>

<span data-ttu-id="c44bb-145">Aşağıdaki tabloda, SDK 'nın hangi öğesi ve hangi [genelleştirmeler](https://en.wikipedia.org/wiki/Glob_(programming)) dahil olduğu ve hangilerinin hariç olduğu gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="c44bb-145">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are both included and excluded in the SDK:</span></span>

| <span data-ttu-id="c44bb-146">Öğe</span><span class="sxs-lookup"><span data-stu-id="c44bb-146">Element</span></span>           | <span data-ttu-id="c44bb-147">Glob 'yi dahil et</span><span class="sxs-lookup"><span data-stu-id="c44bb-147">Include glob</span></span>                              | <span data-ttu-id="c44bb-148">Glob 'yi hariç tut</span><span class="sxs-lookup"><span data-stu-id="c44bb-148">Exclude glob</span></span>                                                  | <span data-ttu-id="c44bb-149">Glob 'yi kaldır</span><span class="sxs-lookup"><span data-stu-id="c44bb-149">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| <span data-ttu-id="c44bb-150">Se</span><span class="sxs-lookup"><span data-stu-id="c44bb-150">Compile</span></span>           | <span data-ttu-id="c44bb-151">\*\*/\*. cs (veya diğer dil uzantıları)</span><span class="sxs-lookup"><span data-stu-id="c44bb-151">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="c44bb-152">\*\*/\*kullanıcısını  \*\*/\*.\* PROJ  \*\*/\*. sln  \*\*/\*. vssscc</span><span class="sxs-lookup"><span data-stu-id="c44bb-152">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="c44bb-153">Yok</span><span class="sxs-lookup"><span data-stu-id="c44bb-153">N/A</span></span>                      |
| <span data-ttu-id="c44bb-154">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="c44bb-154">EmbeddedResource</span></span>  | <span data-ttu-id="c44bb-155">\*\*/\*. resx</span><span class="sxs-lookup"><span data-stu-id="c44bb-155">\*\*/\*.resx</span></span>                              | <span data-ttu-id="c44bb-156">\*\*/\*kullanıcısını \*\*/\*.\* PROJ \*\*/\*. sln \*\*/\*. vssscc</span><span class="sxs-lookup"><span data-stu-id="c44bb-156">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="c44bb-157">Yok</span><span class="sxs-lookup"><span data-stu-id="c44bb-157">N/A</span></span>                      |
| <span data-ttu-id="c44bb-158">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="c44bb-158">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="c44bb-159">\*\*/\*kullanıcısını \*\*/\*.\* PROJ \*\*/\*. sln \*\*/\*. vssscc</span><span class="sxs-lookup"><span data-stu-id="c44bb-159">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="c44bb-160">\*\*/\*.cs \*\*/\*. resx</span><span class="sxs-lookup"><span data-stu-id="c44bb-160">\*\*/\*.cs; \*\*/\*.resx</span></span>   |

> [!NOTE]
> <span data-ttu-id="c44bb-161">**Glob 'Yi hariç tut** , `./bin` `./obj` `$(BaseOutputPath)` sırasıyla ve MSBuild özellikleriyle temsil edilen ve klasörlerini dışlar `$(BaseIntermediateOutputPath)` .</span><span class="sxs-lookup"><span data-stu-id="c44bb-161">**Exclude glob** always excludes the `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, respectively.</span></span> <span data-ttu-id="c44bb-162">Bütün olarak, tüm dışlar tarafından temsil edilir `$(DefaultItemExcludes)` .</span><span class="sxs-lookup"><span data-stu-id="c44bb-162">As a whole, all excludes are represented by `$(DefaultItemExcludes)`.</span></span>

<span data-ttu-id="c44bb-163">Projenizde genelleştirmeler varsa ve en yeni SDK kullanarak derlemeyi denerseniz, şu hatayı alırsınız:</span><span class="sxs-lookup"><span data-stu-id="c44bb-163">If you have globs in your project and you try to build it using the newest SDK, you'll get the following error:</span></span>

> <span data-ttu-id="c44bb-164">Yinelenen derleme öğeleri eklendi.</span><span class="sxs-lookup"><span data-stu-id="c44bb-164">Duplicate Compile items were included.</span></span> <span data-ttu-id="c44bb-165">.NET SDK, varsayılan olarak proje dizininizdeki derleme öğelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-165">The .NET SDK includes Compile items from your project directory by default.</span></span> <span data-ttu-id="c44bb-166">Bu öğeleri proje dosyanıza kaldırabilir ya da bunları proje dosyanıza açıkça dahil etmek istiyorsanız ' Enabledefaultcompileıtems ' özelliğini ' false ' olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c44bb-166">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

<span data-ttu-id="c44bb-167">Bu hatayı çözmek için, `Compile` önceki tabloda listelenenler ile eşleşen açık öğeleri kaldırabilir veya `<EnableDefaultCompileItems>` özelliği şu şekilde ayarlayabilirsiniz `false` :</span><span class="sxs-lookup"><span data-stu-id="c44bb-167">In order to get around this error, you can either remove the explicit `Compile` items that match the ones listed on the previous table, or you can set the `<EnableDefaultCompileItems>` property to `false`, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

<span data-ttu-id="c44bb-168">Bu özelliğin olarak ayarlanması `false` örtük eklemeyi devre dışı bırakacak ve projenizde varsayılan genelleştirmeler belirtmeniz gereken önceki SDK 'ların davranışına geri döndürülüyor.</span><span class="sxs-lookup"><span data-stu-id="c44bb-168">Setting this property to `false` will disable implicit inclusion, reverting to the behavior of previous SDKs where you had to specify the default globs in your project.</span></span>

<span data-ttu-id="c44bb-169">Bu değişiklik, diğer dahil olmak üzere ana mekana 'yi değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="c44bb-169">This change does not modify the main mechanics of other includes.</span></span> <span data-ttu-id="c44bb-170">Bununla birlikte, örneğin, uygulamanızla yayımlanacak bazı dosyalar belirtmek istiyorsanız, bilinen mekanizmaların *csproj* içinde yine de (örneğin, `<Content>` öğesi) kullanılmasını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c44bb-170">However, if you wish to specify, for example, some files to get published with your app, you can still use the known mechanisms in *csproj* for that (for example, the `<Content>` element).</span></span>

<span data-ttu-id="c44bb-171">`<EnableDefaultCompileItems>`yalnızca genelleştirmeler 'i devre dışı bırakır, `Compile` ancak `None` \* . cs öğeleri için de geçerli olan örtük glob gibi diğer genelleştirmeler 'yi etkilemez.</span><span class="sxs-lookup"><span data-stu-id="c44bb-171">`<EnableDefaultCompileItems>` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob, which also applies to \*.cs items.</span></span> <span data-ttu-id="c44bb-172">Bu nedenle **Çözüm Gezgini** , \* öğe olarak dahil olmak üzere projenin bir parçası olarak. cs öğelerini göstermeye devam edecektir `None` .</span><span class="sxs-lookup"><span data-stu-id="c44bb-172">Because of that, **Solution Explorer** will continue show \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="c44bb-173">Benzer bir şekilde, `<EnableDefaultNoneItems>` örtük glob 'yi devre dışı bırakmak için false olarak ayarlayabilirsiniz `None` :</span><span class="sxs-lookup"><span data-stu-id="c44bb-173">In a similar way, you can set `<EnableDefaultNoneItems>` to false to disable the implicit `None` glob, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

<span data-ttu-id="c44bb-174">**Tüm örtük genelleştirmeler**devre dışı bırakmak için, `<EnableDefaultItems>` özelliği `false` Aşağıdaki örnekte olduğu gibi olarak ayarlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c44bb-174">To disable **all implicit globs**, you can set the `<EnableDefaultItems>` property to `false` as in the following example:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a><span data-ttu-id="c44bb-175">Tüm projeyi MSBuild tarafından görüyor</span><span class="sxs-lookup"><span data-stu-id="c44bb-175">How to see the whole project as MSBuild sees it</span></span>

<span data-ttu-id="c44bb-176">Bu csproj proje dosyalarını büyük ölçüde basitleştirirken, SDK ve hedefleri dahil edildikten sonra MSBuild tarafından, tam genişletilmiş projeyi görmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c44bb-176">While those csproj changes greatly simplify project files, you might want to see the fully expanded project as MSBuild sees it once the SDK and its targets are included.</span></span> <span data-ttu-id="c44bb-177">Projeyi [ `/pp` ](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) [`dotnet msbuild`](dotnet-msbuild.md) gerçekten oluşturmadan, hangi dosyaların içeri aktarıldığını, kaynaklarını ve yapıya katkılarını gösteren komut anahtarıyla projeyi önceden işleyin:</span><span class="sxs-lookup"><span data-stu-id="c44bb-177">Preprocess the project with [the `/pp` switch](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) of the [`dotnet msbuild`](dotnet-msbuild.md) command, which shows which files are imported, their sources, and their contributions to the build without actually building the project:</span></span>

`dotnet msbuild -pp:fullproject.xml`

<span data-ttu-id="c44bb-178">Projede birden çok hedef çerçeve varsa, komutun sonuçları MSBuild özelliği olarak belirtilerek yalnızca birine odaklanmalıdır:</span><span class="sxs-lookup"><span data-stu-id="c44bb-178">If the project has multiple target frameworks, the results of the command should be focused on only one of them by specifying it as an MSBuild property:</span></span>

`dotnet msbuild -p:TargetFramework=netcoreapp2.0 -pp:fullproject.xml`

## <a name="additions"></a><span data-ttu-id="c44bb-179">Üzerine</span><span class="sxs-lookup"><span data-stu-id="c44bb-179">Additions</span></span>

### <a name="sdk-attribute"></a><span data-ttu-id="c44bb-180">SDK özniteliği</span><span class="sxs-lookup"><span data-stu-id="c44bb-180">Sdk attribute</span></span>

<span data-ttu-id="c44bb-181">`<Project>` *. Csproj* dosyasının kök öğesi adlı yeni bir özniteliğe sahiptir `Sdk` .</span><span class="sxs-lookup"><span data-stu-id="c44bb-181">The root `<Project>` element of the *.csproj* file has a new attribute called `Sdk`.</span></span> <span data-ttu-id="c44bb-182">`Sdk`Proje tarafından hangi SDK 'nın kullanılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-182">`Sdk` specifies which SDK will be used by the project.</span></span> <span data-ttu-id="c44bb-183">[Katman, katmanlama belgesinde](cli-msbuild-architecture.md) açıklandığı gibi, .NET Core kodu oluşturabileceğiniz MSBuild [görevleri](/visualstudio/msbuild/msbuild-tasks) ve [hedefleri](/visualstudio/msbuild/msbuild-targets) kümesidir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-183">The SDK, as the [layering document](cli-msbuild-architecture.md) describes, is a set of MSBuild [tasks](/visualstudio/msbuild/msbuild-tasks) and [targets](/visualstudio/msbuild/msbuild-targets) that can build .NET Core code.</span></span> <span data-ttu-id="c44bb-184">.NET Core için aşağıdaki SDK 'lar mevcuttur:</span><span class="sxs-lookup"><span data-stu-id="c44bb-184">The following SDKs are available for .NET Core:</span></span>

1. <span data-ttu-id="c44bb-185">KIMLIĞINE sahip .NET Core SDK`Microsoft.NET.Sdk`</span><span class="sxs-lookup"><span data-stu-id="c44bb-185">The .NET Core SDK with the ID of `Microsoft.NET.Sdk`</span></span>
2. <span data-ttu-id="c44bb-186">KIMLIĞINE sahip .NET Core Web SDK 'Sı`Microsoft.NET.Sdk.Web`</span><span class="sxs-lookup"><span data-stu-id="c44bb-186">The .NET Core web SDK with the ID of `Microsoft.NET.Sdk.Web`</span></span>
3. <span data-ttu-id="c44bb-187">KIMLIKLI .NET Core Razor sınıf kitaplığı SDK 'Sı`Microsoft.NET.Sdk.Razor`</span><span class="sxs-lookup"><span data-stu-id="c44bb-187">The .NET Core Razor Class Library SDK with the ID of `Microsoft.NET.Sdk.Razor`</span></span>
4. <span data-ttu-id="c44bb-188">KIMLIĞI `Microsoft.NET.Sdk.Worker` (.net core 3,0 ' den beri) olan .NET Core Worker hizmeti</span><span class="sxs-lookup"><span data-stu-id="c44bb-188">The .NET Core Worker Service with the ID of `Microsoft.NET.Sdk.Worker` (since .NET Core 3.0)</span></span>
5. <span data-ttu-id="c44bb-189">KIMLIĞI `Microsoft.NET.Sdk.WindowsDesktop` (.net core 3,0 ' den beri) olan .NET Core WinForms ve WPF</span><span class="sxs-lookup"><span data-stu-id="c44bb-189">The .NET Core WinForms and WPF with the ID of `Microsoft.NET.Sdk.WindowsDesktop` (since .NET Core 3.0)</span></span>

<span data-ttu-id="c44bb-190">`Sdk` `<Project>` .NET Core araçları 'nı kullanabilmeniz ve kodunuzu derlemek için öğesi Için bu kimliklerden birine ayarlanmış özniteliğin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-190">You need to have the `Sdk` attribute set to one of those IDs on the `<Project>` element in order to use the .NET Core tools and build your code.</span></span>

### <a name="packagereference"></a><span data-ttu-id="c44bb-191">PackageReference</span><span class="sxs-lookup"><span data-stu-id="c44bb-191">PackageReference</span></span>

<span data-ttu-id="c44bb-192">`<PackageReference>`Öğe öğesi [, projede bir NuGet bağımlılığını](/nuget/consume-packages/package-references-in-project-files)belirtir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-192">A `<PackageReference>` item element specifies a [NuGet dependency in the project](/nuget/consume-packages/package-references-in-project-files).</span></span> <span data-ttu-id="c44bb-193">`Include`Öznitelik, paket kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-193">The `Include` attribute specifies the package ID.</span></span>

```xml
<PackageReference Include="package-id" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a><span data-ttu-id="c44bb-194">Sürüm</span><span class="sxs-lookup"><span data-stu-id="c44bb-194">Version</span></span>

<span data-ttu-id="c44bb-195">Gerekli `Version` öznitelik, geri yüklenecek paketin sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-195">The required `Version` attribute specifies the version of the package to restore.</span></span> <span data-ttu-id="c44bb-196">Öznitelik, [NuGet sürüm aralığı](/nuget/concepts/package-versioning#version-ranges) düzeninin kurallarına uyar.</span><span class="sxs-lookup"><span data-stu-id="c44bb-196">The attribute respects the rules of the [NuGet version range](/nuget/concepts/package-versioning#version-ranges) scheme.</span></span> <span data-ttu-id="c44bb-197">Varsayılan davranış en düşük sürüm ve kapsamlı eşleşmedir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-197">The default behavior is a minimum version, inclusive match.</span></span> <span data-ttu-id="c44bb-198">Örneğin, öğesini belirleme, `Version="1.2.3"` NuGet gösterimi ile eşdeğerdir `[1.2.3, )` ve, çözümlenmiş paketin 1.2.3 sürümü varsa veya daha büyük değilse, sürümüne sahip olacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-198">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3, )` and means the resolved package will have the version 1.2.3 if available or greater otherwise.</span></span>

#### <a name="includeassets-excludeassets-and-privateassets"></a><span data-ttu-id="c44bb-199">Includevarlıklarını, Excludevarlıklarını ve Privatevarlıkları</span><span class="sxs-lookup"><span data-stu-id="c44bb-199">IncludeAssets, ExcludeAssets, and PrivateAssets</span></span>

<span data-ttu-id="c44bb-200">`IncludeAssets`öznitelik, tarafından belirtilen pakete ait olan varlıkların `<PackageReference>` tüketilmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-200">`IncludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed.</span></span> <span data-ttu-id="c44bb-201">Varsayılan olarak, tüm paket varlıkları dahil edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-201">By default, all package assets are included.</span></span>

<span data-ttu-id="c44bb-202">`ExcludeAssets`öznitelik, tarafından belirtilen pakete ait olan varlıkların `<PackageReference>` tüketilmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-202">`ExcludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should not be consumed.</span></span>

<span data-ttu-id="c44bb-203">`PrivateAssets`öznitelik, tarafından belirtilen pakete ait olan varlıkların `<PackageReference>` tüketilmesi gerektiğini, ancak bir sonraki projenin akışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-203">`PrivateAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed but not flow to the next project.</span></span> <span data-ttu-id="c44bb-204">`Analyzers` `Build` `ContentFiles` Bu öznitelik mevcut olmadığında, ve varlıkları varsayılan olarak özeldir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-204">The `Analyzers`, `Build` and `ContentFiles` assets are private by default when this attribute is not present.</span></span>

> [!NOTE]
> <span data-ttu-id="c44bb-205">`PrivateAssets`, *project.json* / *xproj* `SuppressParent` öğesindekiproject.jseşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-205">`PrivateAssets` is equivalent to the *project.json*/*xproj* `SuppressParent` element.</span></span>

<span data-ttu-id="c44bb-206">Bu öznitelikler, birden fazla listeleniyorsa noktalı virgül karakteriyle ayrılmış aşağıdaki öğelerden birini veya daha fazlasını içerebilir `;` :</span><span class="sxs-lookup"><span data-stu-id="c44bb-206">These attributes can contain one or more of the following items, separated by the semicolon `;` character if more than one is listed:</span></span>

- <span data-ttu-id="c44bb-207">`Compile`– *LIB* klasörünün içeriği, derleme için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-207">`Compile` – the contents of the *lib* folder are available to compile against.</span></span>
- <span data-ttu-id="c44bb-208">`Runtime`– *çalışma zamanı* klasörünün içeriği dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="c44bb-208">`Runtime` – the contents of the *runtime* folder are distributed.</span></span>
- <span data-ttu-id="c44bb-209">`ContentFiles`– *ContentFiles* klasörünün içeriği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c44bb-209">`ContentFiles` – the contents of the *contentfiles* folder are used.</span></span>
- <span data-ttu-id="c44bb-210">`Build`– *Build* klasöründeki props/targets kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c44bb-210">`Build` – the props/targets in the *build* folder are used.</span></span>
- <span data-ttu-id="c44bb-211">`Native`– Yerel varlıklardan içerik çalışma zamanı için *Çıkış* klasörüne kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="c44bb-211">`Native` – the contents from native assets are copied to the *output* folder for runtime.</span></span>
- <span data-ttu-id="c44bb-212">`Analyzers`– çözümleyiciler kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c44bb-212">`Analyzers` – the analyzers are used.</span></span>

<span data-ttu-id="c44bb-213">Alternatif olarak, öznitelik şunları içerebilir:</span><span class="sxs-lookup"><span data-stu-id="c44bb-213">Alternatively, the attribute can contain:</span></span>

- <span data-ttu-id="c44bb-214">`None`– varlıkların hiçbiri kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="c44bb-214">`None` – none of the assets are used.</span></span>
- <span data-ttu-id="c44bb-215">`All`– Tüm varlıklar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c44bb-215">`All` – all assets are used.</span></span>

### <a name="dotnetclitoolreference"></a><span data-ttu-id="c44bb-216">Dotnetclientoolreference</span><span class="sxs-lookup"><span data-stu-id="c44bb-216">DotNetCliToolReference</span></span>

<span data-ttu-id="c44bb-217">Bir `<DotNetCliToolReference>` öğe öğesi, kullanıcının proje bağlamında geri yüklemek ISTEDIĞI CLI aracını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-217">A `<DotNetCliToolReference>` item element specifies the CLI tool that the user wants to restore in the context of the project.</span></span> <span data-ttu-id="c44bb-218">`tools` *project.jsüzerindeki*düğüm için bir değiştirme.</span><span class="sxs-lookup"><span data-stu-id="c44bb-218">It's a replacement for the `tools` node in *project.json*.</span></span>

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

<span data-ttu-id="c44bb-219">`DotNetCliToolReference`Artık [.NET Core yerel araçlarının](https://aka.ms/local-tools) [kullanım dışı](https://github.com/dotnet/announcements/issues/107) olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c44bb-219">Note that `DotNetCliToolReference` is [now deprecated](https://github.com/dotnet/announcements/issues/107) in favor of [.NET Core Local Tools](https://aka.ms/local-tools).</span></span>

#### <a name="version"></a><span data-ttu-id="c44bb-220">Sürüm</span><span class="sxs-lookup"><span data-stu-id="c44bb-220">Version</span></span>

<span data-ttu-id="c44bb-221">`Version`geri yüklenecek paketin sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-221">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="c44bb-222">Öznitelik, [NuGet sürüm oluşturma](/nuget/create-packages/dependency-versions#version-ranges) şemasının kurallarına uyar.</span><span class="sxs-lookup"><span data-stu-id="c44bb-222">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="c44bb-223">Varsayılan davranış en düşük sürüm ve kapsamlı eşleşmedir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-223">The default behavior is a minimum version, inclusive match.</span></span> <span data-ttu-id="c44bb-224">Örneğin, öğesini belirleme, `Version="1.2.3"` NuGet gösterimi ile eşdeğerdir `[1.2.3, )` ve, çözümlenmiş paketin 1.2.3 sürümü varsa veya daha büyük değilse, sürümüne sahip olacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-224">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3, )` and means the resolved package will have the version 1.2.3 if available or greater otherwise.</span></span>

### <a name="runtimeidentifiers"></a><span data-ttu-id="c44bb-225">Runtimetanımlayıcıtanımlayıcıları</span><span class="sxs-lookup"><span data-stu-id="c44bb-225">RuntimeIdentifiers</span></span>

<span data-ttu-id="c44bb-226">`<RuntimeIdentifiers>`Property öğesi, proje için bir [çalışma zamanı tanımlayıcıları (RID 'ler)](../rid-catalog.md) için noktalı virgülle ayrılmış bir liste belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="c44bb-226">The `<RuntimeIdentifiers>` property element lets you specify a semicolon-delimited list of [Runtime Identifiers (RIDs)](../rid-catalog.md) for the project.</span></span>
<span data-ttu-id="c44bb-227">RID 'Ler, kendi kendine kapsanan dağıtımları yayımlamayı etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-227">RIDs enable publishing self-contained deployments.</span></span>

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a><span data-ttu-id="c44bb-228">Runtimeıdentifier</span><span class="sxs-lookup"><span data-stu-id="c44bb-228">RuntimeIdentifier</span></span>

<span data-ttu-id="c44bb-229">`<RuntimeIdentifier>`Property öğesi, proje için yalnızca bir [çalışma zamanı tanımlayıcısı (RID)](../rid-catalog.md) belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="c44bb-229">The `<RuntimeIdentifier>` property element allows you to specify only one [Runtime Identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="c44bb-230">RID, kendi kendine içerilen bir dağıtımı yayımlamayı mümkün.</span><span class="sxs-lookup"><span data-stu-id="c44bb-230">The RID enables publishing a self-contained deployment.</span></span>

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

<span data-ttu-id="c44bb-231">`<RuntimeIdentifiers>`Çoklu çalışma zamanları için yayımlamanız gerekiyorsa bunun yerine (plural) kullanın.</span><span class="sxs-lookup"><span data-stu-id="c44bb-231">Use `<RuntimeIdentifiers>` (plural) instead if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="c44bb-232">`<RuntimeIdentifier>`yalnızca tek bir çalışma zamanı gerektiğinde daha hızlı derlemeler sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-232">`<RuntimeIdentifier>` can provide faster builds when only a single runtime is required.</span></span>

### <a name="packagetargetfallback"></a><span data-ttu-id="c44bb-233">PackageTargetFallback</span><span class="sxs-lookup"><span data-stu-id="c44bb-233">PackageTargetFallback</span></span>

<span data-ttu-id="c44bb-234">`<PackageTargetFallback>`Özellik öğesi, paketler geri yüklenirken kullanılacak bir dizi uyumlu hedef belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="c44bb-234">The `<PackageTargetFallback>` property element allows you to specify a set of compatible targets to be used when restoring packages.</span></span> <span data-ttu-id="c44bb-235">DotNet [TXE (hedef x takma adı)](/nuget/schema/target-frameworks) kullanan paketlere bir DotNet TXD bildirmeyin paketlerle çalışmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c44bb-235">It's designed to allow packages that use the dotnet [TxM (Target x Moniker)](/nuget/schema/target-frameworks) to operate with packages that don't declare a dotnet TxM.</span></span> <span data-ttu-id="c44bb-236">Projeniz DotNet TXI kullanıyorsa, `<PackageTargetFallback>` DotNet olmayan platformların DotNet ile uyumlu olmasını sağlamak üzere projenize eklemediğiniz sürece, bağımlı olduğu tüm paketlerin DotNet TXD olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-236">If your project uses the dotnet TxM, then all the packages it depends on must also have a dotnet TxM, unless you add the `<PackageTargetFallback>` to your project in order to allow non-dotnet platforms to be compatible with dotnet.</span></span>

<span data-ttu-id="c44bb-237">Aşağıdaki örnek, projenizdeki tüm hedeflerin geri dönüşlerinizi sağlar:</span><span class="sxs-lookup"><span data-stu-id="c44bb-237">The following example provides the fallbacks for all targets in your project:</span></span>

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

<span data-ttu-id="c44bb-238">Aşağıdaki örnek yalnızca hedef için geri dönüşi belirtir `netcoreapp2.1` :</span><span class="sxs-lookup"><span data-stu-id="c44bb-238">The following example specifies the fallbacks only for the `netcoreapp2.1` target:</span></span>

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp2.1'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="build-events"></a><span data-ttu-id="c44bb-239">Derleme olayları</span><span class="sxs-lookup"><span data-stu-id="c44bb-239">Build events</span></span>

<span data-ttu-id="c44bb-240">Derleme öncesi ve derleme sonrası olaylarının proje dosyasında belirtilme biçimi değişmiştir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-240">The way that pre-build and post-build events are specified in the project file has changed.</span></span> <span data-ttu-id="c44bb-241">$ (ProjectDir) gibi makrolar çözümlenmediğinden, PreBuildEvent ve PostBuildEvent özelliklerinin SDK stili proje biçiminde kullanılması önerilmez.</span><span class="sxs-lookup"><span data-stu-id="c44bb-241">The properties PreBuildEvent and PostBuildEvent are not recommended in the SDK-style project format, because macros such as $(ProjectDir) are not resolved.</span></span> <span data-ttu-id="c44bb-242">Örneğin, aşağıdaki kod artık desteklenmemektedir:</span><span class="sxs-lookup"><span data-stu-id="c44bb-242">For example, the following code is no longer supported:</span></span>

```xml
<PropertyGroup>
    <PreBuildEvent>"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)"</PreBuildEvent>
</PropertyGroup>
```

<span data-ttu-id="c44bb-243">SDK stili projelerde, veya adında bir MSBuild hedefi kullanın `PreBuild` `PostBuild` ve `BeforeTargets` özelliğini `PreBuild` veya `AfterTargets` özelliğini ayarlayın `PostBuild` .</span><span class="sxs-lookup"><span data-stu-id="c44bb-243">In SDK-style projects, use an MSBuild target named `PreBuild` or `PostBuild` and set the `BeforeTargets` property for `PreBuild` or the `AfterTargets` property for `PostBuild`.</span></span> <span data-ttu-id="c44bb-244">Önceki örnek için aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="c44bb-244">For the preceding example, use the following code:</span></span>

```xml
<Target Name="PreBuild" BeforeTargets="PreBuildEvent">
    <Exec Command="&quot;$(ProjectDir)PreBuildEvent.bat&quot; &quot;$(ProjectDir)..\&quot; &quot;$(ProjectDir)&quot; &quot;$(TargetDir)&quot;" />
</Target>

<Target Name="PostBuild" AfterTargets="PostBuildEvent">
   <Exec Command="echo Output written to $(TargetDir)" />
</Target>
```

> [!NOTE]
><span data-ttu-id="c44bb-245">MSBuild hedefleri için herhangi bir ad kullanabilirsiniz, ancak Visual Studio IDE 'yi tanır `PreBuild` ve `PostBuild` hedefler. bu nedenle, VISUAL Studio IDE 'de komutları düzenleyebilmeniz için bu adları kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="c44bb-245">You can use any name for the MSBuild targets, but the Visual Studio IDE recognizes `PreBuild` and `PostBuild` targets, so we recommend using those names so that you can edit the commands in the Visual Studio IDE.</span></span>

## <a name="nuget-metadata-properties"></a><span data-ttu-id="c44bb-246">NuGet meta veri özellikleri</span><span class="sxs-lookup"><span data-stu-id="c44bb-246">NuGet metadata properties</span></span>

<span data-ttu-id="c44bb-247">MSBuild 'e taşıma ile, bir NuGet paketini *. csproj* dosyalarına *project.js* bir NuGet paketi paketleme sırasında kullanılan giriş meta verilerini taşıdık.</span><span class="sxs-lookup"><span data-stu-id="c44bb-247">With the move to MSBuild, we have moved the input metadata that is used when packing a NuGet package from *project.json* to *.csproj* files.</span></span> <span data-ttu-id="c44bb-248">Girdiler MSBuild özellikleridir, bu nedenle bir grup içinde gitmeleri gerekir `<PropertyGroup>` .</span><span class="sxs-lookup"><span data-stu-id="c44bb-248">The inputs are MSBuild properties so they have to go within a `<PropertyGroup>` group.</span></span> <span data-ttu-id="c44bb-249">Aşağıda, `dotnet pack` `Pack` SDK 'nın parçası olan komutu veya MSBuild hedefini kullanırken paketleme işlemine giriş olarak kullanılan özelliklerin listesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="c44bb-249">The following is the list of properties that are used as inputs to the packing process when using the `dotnet pack` command or the `Pack` MSBuild target that is part of the SDK:</span></span>

### <a name="ispackable"></a><span data-ttu-id="c44bb-250">Ispackable</span><span class="sxs-lookup"><span data-stu-id="c44bb-250">IsPackable</span></span>

<span data-ttu-id="c44bb-251">Projenin paketlenemeyeceğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="c44bb-251">A Boolean value that specifies whether the project can be packed.</span></span> <span data-ttu-id="c44bb-252">Varsayılan değer: `true`.</span><span class="sxs-lookup"><span data-stu-id="c44bb-252">The default value is `true`.</span></span>

### <a name="packageversion"></a><span data-ttu-id="c44bb-253">PackageVersion</span><span class="sxs-lookup"><span data-stu-id="c44bb-253">PackageVersion</span></span>

<span data-ttu-id="c44bb-254">Elde edilen paketin sahip olacağı sürümü belirtir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-254">Specifies the version that the resulting package will have.</span></span> <span data-ttu-id="c44bb-255">Tüm NuGet sürüm dizesi formlarını kabul eder.</span><span class="sxs-lookup"><span data-stu-id="c44bb-255">Accepts all forms of NuGet version string.</span></span> <span data-ttu-id="c44bb-256">Varsayılan değeri,, `$(Version)` Yani, projedeki özelliğinin değeridir `Version` .</span><span class="sxs-lookup"><span data-stu-id="c44bb-256">Default is the value of `$(Version)`, that is, of the property `Version` in the project.</span></span>

### <a name="packageid"></a><span data-ttu-id="c44bb-257">PackageID</span><span class="sxs-lookup"><span data-stu-id="c44bb-257">PackageId</span></span>

<span data-ttu-id="c44bb-258">Sonuç paketinin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-258">Specifies the name for the resulting package.</span></span> <span data-ttu-id="c44bb-259">Belirtilmemişse, `pack` işlem varsayılan `AssemblyName` olarak paketin adı ile veya dizin adını kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="c44bb-259">If not specified, the `pack` operation will default to using the `AssemblyName` or directory name as the name of the package.</span></span>

### <a name="title"></a><span data-ttu-id="c44bb-260">Başlık</span><span class="sxs-lookup"><span data-stu-id="c44bb-260">Title</span></span>

<span data-ttu-id="c44bb-261">Genellikle, Kullanıcı arabiriminde kullanılan ve Visual Studio 'da paket yöneticisi olarak görüntülenen, paketin kolay bir başlığı.</span><span class="sxs-lookup"><span data-stu-id="c44bb-261">A human-friendly title of the package, typically used in UI displays as on nuget.org and the Package Manager in Visual Studio.</span></span> <span data-ttu-id="c44bb-262">Belirtilmemişse, bunun yerine paket KIMLIĞI kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c44bb-262">If not specified, the package ID is used instead.</span></span>

### <a name="authors"></a><span data-ttu-id="c44bb-263">Yazarlar</span><span class="sxs-lookup"><span data-stu-id="c44bb-263">Authors</span></span>

<span data-ttu-id="c44bb-264">Nuget.org üzerindeki profil adlarıyla eşleşen paket yazarları için noktalı virgülle ayrılmış bir liste. Bunlar, nuget.org üzerindeki NuGet galerisinde görüntülenir ve aynı yazarlara göre çapraz başvuru için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c44bb-264">A semicolon-separated list of packages authors, matching the profile names on nuget.org. These are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span>

### <a name="packagedescription"></a><span data-ttu-id="c44bb-265">PackageDescription</span><span class="sxs-lookup"><span data-stu-id="c44bb-265">PackageDescription</span></span>

<span data-ttu-id="c44bb-266">UI görüntüleme paketinin uzun açıklaması.</span><span class="sxs-lookup"><span data-stu-id="c44bb-266">A long description of the package for UI display.</span></span>

### <a name="description"></a><span data-ttu-id="c44bb-267">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c44bb-267">Description</span></span>

<span data-ttu-id="c44bb-268">Derleme için uzun bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="c44bb-268">A long description for the assembly.</span></span> <span data-ttu-id="c44bb-269">`PackageDescription`Belirtilmezse, bu özellik paketin açıklaması olarak da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c44bb-269">If `PackageDescription` is not specified, then this property is also used as the description of the package.</span></span>

### <a name="copyright"></a><span data-ttu-id="c44bb-270">Telif Hakkı</span><span class="sxs-lookup"><span data-stu-id="c44bb-270">Copyright</span></span>

<span data-ttu-id="c44bb-271">Paket için telif hakkı ayrıntıları.</span><span class="sxs-lookup"><span data-stu-id="c44bb-271">Copyright details for the package.</span></span>

### <a name="packagerequirelicenseacceptance"></a><span data-ttu-id="c44bb-272">Packagerequirelicensekabulünü</span><span class="sxs-lookup"><span data-stu-id="c44bb-272">PackageRequireLicenseAcceptance</span></span>

<span data-ttu-id="c44bb-273">İstemcinin paketi yüklemeden önce paket lisansını kabul etmesini isteyip istemeyeceğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="c44bb-273">A Boolean value that specifies whether the client must prompt the consumer to accept the package license before installing the package.</span></span> <span data-ttu-id="c44bb-274">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="c44bb-274">The default is `false`.</span></span>

### <a name="developmentdependency"></a><span data-ttu-id="c44bb-275">DevelopmentDependency</span><span class="sxs-lookup"><span data-stu-id="c44bb-275">DevelopmentDependency</span></span>

<span data-ttu-id="c44bb-276">Paketin bir yalnızca geliştirme bağımlılığı olarak işaretlenip işaretlenmediğini belirten ve paketin diğer paketlere bağımlılık olarak eklenmesini önleyen bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="c44bb-276">A Boolean value that specifies whether the package is marked as a development-only dependency, which prevents the package from being included as a dependency in other packages.</span></span> <span data-ttu-id="c44bb-277">PackageReference (NuGet 4.8 +) ile bu bayrak Ayrıca derleme zamanı varlıklarının derlemeden dışlandığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-277">With PackageReference (NuGet 4.8+), this flag also means that compile-time assets are excluded from compilation.</span></span> <span data-ttu-id="c44bb-278">Daha fazla bilgi için bkz. [PackageReference Için Developmentdependency desteği](https://github.com/NuGet/Home/wiki/DevelopmentDependency-support-for-PackageReference).</span><span class="sxs-lookup"><span data-stu-id="c44bb-278">For more information, see [DevelopmentDependency support for PackageReference](https://github.com/NuGet/Home/wiki/DevelopmentDependency-support-for-PackageReference).</span></span>

### <a name="packagelicenseexpression"></a><span data-ttu-id="c44bb-279">PackageLicenseExpression</span><span class="sxs-lookup"><span data-stu-id="c44bb-279">PackageLicenseExpression</span></span>

<span data-ttu-id="c44bb-280">Bir [Spdx lisans tanımlayıcısı](https://spdx.org/licenses/) veya ifadesi.</span><span class="sxs-lookup"><span data-stu-id="c44bb-280">An [SPDX license identifier](https://spdx.org/licenses/) or expression.</span></span> <span data-ttu-id="c44bb-281">Örneğin, `Apache-2.0`.</span><span class="sxs-lookup"><span data-stu-id="c44bb-281">For example, `Apache-2.0`.</span></span>

<span data-ttu-id="c44bb-282">[Spdx lisans tanımlayıcılarının](https://spdx.org/licenses/)listesi aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-282">Here is the complete list of [SPDX license identifiers](https://spdx.org/licenses/).</span></span> <span data-ttu-id="c44bb-283">NuGet.org, lisans türü ifadesi kullanılırken yalnızca OSı veya FSF onaylı lisansları kabul eder.</span><span class="sxs-lookup"><span data-stu-id="c44bb-283">NuGet.org accepts only OSI or FSF approved licenses when using license type expression.</span></span>

<span data-ttu-id="c44bb-284">Lisans ifadelerinin tam sözdizimi aşağıda, [Abnf](https://tools.ietf.org/html/rfc5234)içinde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c44bb-284">The exact syntax of the license expressions is described below in [ABNF](https://tools.ietf.org/html/rfc5234).</span></span>

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
> <span data-ttu-id="c44bb-285">Tek seferde yalnızca `PackageLicenseExpression` biri `PackageLicenseFile` ve `PackageLicenseUrl` belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-285">Only one of `PackageLicenseExpression`, `PackageLicenseFile` and `PackageLicenseUrl` can be specified at a time.</span></span>

### <a name="packagelicensefile"></a><span data-ttu-id="c44bb-286">PackageLicenseFile</span><span class="sxs-lookup"><span data-stu-id="c44bb-286">PackageLicenseFile</span></span>

<span data-ttu-id="c44bb-287">Bir SPDX tanımlayıcısı atanmamış bir lisans kullanıyorsanız veya özel bir lisans ise (Aksi takdirde tercih edilir) paket içindeki bir lisans dosyasının yolu `PackageLicenseExpression`</span><span class="sxs-lookup"><span data-stu-id="c44bb-287">Path to a license file within the package if you are using a license that hasn’t been assigned an SPDX identifier, or it is a custom license (Otherwise `PackageLicenseExpression` is preferred)</span></span>

<span data-ttu-id="c44bb-288">, `PackageLicenseUrl` İle birleştirilemez `PackageLicenseExpression` ve Visual Studio Version 15.9.4 ve .NET SDK 2.1.502 ya da 2.2.101 ya da daha yeni bir sürüm gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-288">Replaces `PackageLicenseUrl`, can't be combined with `PackageLicenseExpression`, and requires Visual Studio version 15.9.4 and .NET SDK 2.1.502 or 2.2.101 or newer.</span></span>

<span data-ttu-id="c44bb-289">Lisans dosyasının paketlenmiş olduğundan emin olmanız gerekir, bu işlem, örnek kullanım:</span><span class="sxs-lookup"><span data-stu-id="c44bb-289">You will need to ensure the license file is packed by adding it explicitly to the project, example usage:</span></span>

```xml
<PropertyGroup>
  <PackageLicenseFile>LICENSE.txt</PackageLicenseFile>
</PropertyGroup>
<ItemGroup>
  <None Include="licenses\LICENSE.txt" Pack="true" PackagePath="$(PackageLicenseFile)"/>
</ItemGroup>
```

### <a name="packagelicenseurl"></a><span data-ttu-id="c44bb-290">PackageLicenseUrl 'Si</span><span class="sxs-lookup"><span data-stu-id="c44bb-290">PackageLicenseUrl</span></span>

<span data-ttu-id="c44bb-291">Pakete uygulanabilen lisansın URL 'SI.</span><span class="sxs-lookup"><span data-stu-id="c44bb-291">A URL to the license that is applicable to the package.</span></span> <span data-ttu-id="c44bb-292">(_Visual Studio 15.9.4, .NET SDK 2.1.502 ve 2.2.101 'den beri kullanım dışı_)</span><span class="sxs-lookup"><span data-stu-id="c44bb-292">(_deprecated since Visual Studio 15.9.4, .NET SDK 2.1.502 and 2.2.101_)</span></span>

### <a name="packageiconurl"></a><span data-ttu-id="c44bb-293">PackageIconUrl 'Si</span><span class="sxs-lookup"><span data-stu-id="c44bb-293">PackageIconUrl</span></span>

<span data-ttu-id="c44bb-294">Kullanıcı arabirimi görüntüsündeki paketin simgesi olarak kullanılacak, saydam arka planlı bir 64x64 görüntüsünün URL 'SI.</span><span class="sxs-lookup"><span data-stu-id="c44bb-294">A URL for a 64x64 image with transparent background to use as the icon for the package in UI display.</span></span>

### <a name="packagereleasenotes"></a><span data-ttu-id="c44bb-295">PackageReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="c44bb-295">PackageReleaseNotes</span></span>

<span data-ttu-id="c44bb-296">Paket için sürüm notları.</span><span class="sxs-lookup"><span data-stu-id="c44bb-296">Release notes for the package.</span></span>

### <a name="packagetags"></a><span data-ttu-id="c44bb-297">PackageTags</span><span class="sxs-lookup"><span data-stu-id="c44bb-297">PackageTags</span></span>

<span data-ttu-id="c44bb-298">Paketi atayan etiketlerin noktalı virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="c44bb-298">A semicolon-delimited list of tags that designates the package.</span></span>

### <a name="packageoutputpath"></a><span data-ttu-id="c44bb-299">PackageOutputPath</span><span class="sxs-lookup"><span data-stu-id="c44bb-299">PackageOutputPath</span></span>

<span data-ttu-id="c44bb-300">Paketlenmiş paketin bırakılacak çıkış yolunu belirler.</span><span class="sxs-lookup"><span data-stu-id="c44bb-300">Determines the output path in which the packed package will be dropped.</span></span> <span data-ttu-id="c44bb-301">`$(OutputPath)` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-301">Default is `$(OutputPath)`.</span></span>

### <a name="includesymbols"></a><span data-ttu-id="c44bb-302">Includesymbols</span><span class="sxs-lookup"><span data-stu-id="c44bb-302">IncludeSymbols</span></span>
<span data-ttu-id="c44bb-303">Bu Boole değeri, paketin proje paketedildiğinde ek bir sembol paketi oluşturup oluşturmayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-303">This Boolean value indicates whether the package should create an additional symbols package when the project is packed.</span></span> <span data-ttu-id="c44bb-304">Semboller paketinin biçimi, özelliği tarafından denetlenir `SymbolPackageFormat` .</span><span class="sxs-lookup"><span data-stu-id="c44bb-304">The symbols package's format is controlled by the `SymbolPackageFormat` property.</span></span>

### <a name="symbolpackageformat"></a><span data-ttu-id="c44bb-305">SymbolPackageFormat</span><span class="sxs-lookup"><span data-stu-id="c44bb-305">SymbolPackageFormat</span></span>
<span data-ttu-id="c44bb-306">Semboller paketinin biçimini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-306">Specifies the format of the symbols package.</span></span> <span data-ttu-id="c44bb-307">"Symbols. nupkg" ise, pdb 'leri, dll 'Ler ve diğer çıktı dosyalarını içeren *. Symbols. nupkg* Uzantısı ile eski bir sembol paketi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c44bb-307">If "symbols.nupkg", a legacy symbols package will be created with a *.symbols.nupkg* extension containing PDBs, DLLs, and other output files.</span></span> <span data-ttu-id="c44bb-308">"Snupkg" ise, taşınabilir pdb 'leri içeren bir snupkg sembol paketi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c44bb-308">If "snupkg", a snupkg symbol package will be created containing the portable PDBs.</span></span> <span data-ttu-id="c44bb-309">Varsayılan değer "symbols. nupkg" dır.</span><span class="sxs-lookup"><span data-stu-id="c44bb-309">Default is "symbols.nupkg".</span></span>

### <a name="includesource"></a><span data-ttu-id="c44bb-310">Includesource</span><span class="sxs-lookup"><span data-stu-id="c44bb-310">IncludeSource</span></span>

<span data-ttu-id="c44bb-311">Bu Boole değeri, paket işleminin bir kaynak paketi oluşturup oluşturmayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-311">This Boolean value indicates whether the pack process should create a source package.</span></span> <span data-ttu-id="c44bb-312">Kaynak paket, kitaplığın kaynak kodunu ve PDB dosyalarını içerir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-312">The source package contains the library's source code as well as PDB files.</span></span> <span data-ttu-id="c44bb-313">Kaynak dosyalar, `src/ProjectName` elde edilen paket dosyasındaki dizinin altına yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-313">Source files are put under the `src/ProjectName` directory in the resulting package file.</span></span>

### <a name="istool"></a><span data-ttu-id="c44bb-314">IsTool</span><span class="sxs-lookup"><span data-stu-id="c44bb-314">IsTool</span></span>

<span data-ttu-id="c44bb-315">Tüm çıkış dosyalarının *lib* klasörü yerine *Araçlar* klasörüne kopyalanıp kopyalanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-315">Specifies whether all output files are copied to the *tools* folder instead of the *lib* folder.</span></span> <span data-ttu-id="c44bb-316">Bu, `DotNetCliTool` `PackageType` *. csproj* dosyasında ayarıyla belirtilen öğesinden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="c44bb-316">This is different from a `DotNetCliTool`, which is specified by setting the `PackageType` in the *.csproj* file.</span></span>

### <a name="repositoryurl"></a><span data-ttu-id="c44bb-317">Depourl 'Si</span><span class="sxs-lookup"><span data-stu-id="c44bb-317">RepositoryUrl</span></span>

<span data-ttu-id="c44bb-318">Paketin kaynak kodunun bulunduğu ve/veya oluşturulduğu deponun URL 'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-318">Specifies the URL for the repository where the source code for the package resides and/or from which it's being built.</span></span>

### <a name="repositorytype"></a><span data-ttu-id="c44bb-319">Repositorytype parametrelerinin sağlanması</span><span class="sxs-lookup"><span data-stu-id="c44bb-319">RepositoryType</span></span>

<span data-ttu-id="c44bb-320">Deponun türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-320">Specifies the type of the repository.</span></span> <span data-ttu-id="c44bb-321">Varsayılan değer "git" dir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-321">Default is "git".</span></span>

### <a name="repositorybranch"></a><span data-ttu-id="c44bb-322">Depodalı</span><span class="sxs-lookup"><span data-stu-id="c44bb-322">RepositoryBranch</span></span>
<span data-ttu-id="c44bb-323">Depodaki kaynak dalın adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-323">Specifies the name of the source branch in the repository.</span></span> <span data-ttu-id="c44bb-324">Proje bir NuGet paketinde paketlenmişse, paket meta verilerine eklenir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-324">When the project is packaged in a NuGet package, it's added to the package metadata.</span></span>

### <a name="repositorycommit"></a><span data-ttu-id="c44bb-325">Kayıt yapma</span><span class="sxs-lookup"><span data-stu-id="c44bb-325">RepositoryCommit</span></span>
<span data-ttu-id="c44bb-326">Paketin hangi kaynağa göre oluşturulduğunu göstermek için isteğe bağlı depo kaydı veya değişiklik kümesi.</span><span class="sxs-lookup"><span data-stu-id="c44bb-326">Optional repository commit or changeset to indicate which source the package was built against.</span></span> <span data-ttu-id="c44bb-327">`RepositoryUrl`Bu özelliğin dahil edilmesini sağlamak için de belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-327">`RepositoryUrl` must also be specified for this property to be included.</span></span> <span data-ttu-id="c44bb-328">Proje bir NuGet paketinde paketlenmişse, bu tamamlama veya değişiklik kümesi paket meta verilerine eklenir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-328">When the project is packaged in a NuGet package, this commit or changeset is added to the package metadata.</span></span>

### <a name="nopackageanalysis"></a><span data-ttu-id="c44bb-329">NoPackageAnalysis</span><span class="sxs-lookup"><span data-stu-id="c44bb-329">NoPackageAnalysis</span></span>

<span data-ttu-id="c44bb-330">Paketi derlemeden sonra paketin paket analizini çalıştırmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="c44bb-330">Specifies that pack should not run package analysis after building the package.</span></span>

### <a name="minclientversion"></a><span data-ttu-id="c44bb-331">MinClientVersion</span><span class="sxs-lookup"><span data-stu-id="c44bb-331">MinClientVersion</span></span>

<span data-ttu-id="c44bb-332">Bu paketi yükleyecan nuget.exe ve Visual Studio Paket Yöneticisi tarafından zorlanan NuGet istemcisinin en düşük sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-332">Specifies the minimum version of the NuGet client that can install this package, enforced by nuget.exe and the Visual Studio Package Manager.</span></span>

### <a name="includebuildoutput"></a><span data-ttu-id="c44bb-333">IncludeBuildOutput</span><span class="sxs-lookup"><span data-stu-id="c44bb-333">IncludeBuildOutput</span></span>

<span data-ttu-id="c44bb-334">Bu Boole değeri, derleme çıkış derlemelerinin *. nupkg* dosyasına paketedilip edilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-334">This Boolean value specifies whether the build output assemblies should be packed into the *.nupkg* file or not.</span></span>

### <a name="includecontentinpack"></a><span data-ttu-id="c44bb-335">Includecontentınpack</span><span class="sxs-lookup"><span data-stu-id="c44bb-335">IncludeContentInPack</span></span>

<span data-ttu-id="c44bb-336">Bu Boole değeri, türüne sahip olan öğelerin `Content` elde edilen pakete otomatik olarak dahil edilip edilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-336">This Boolean value specifies whether any items that have a type of `Content` will be included in the resulting package automatically.</span></span> <span data-ttu-id="c44bb-337">Varsayılan değer: `true`.</span><span class="sxs-lookup"><span data-stu-id="c44bb-337">The default is `true`.</span></span>

### <a name="buildoutputtargetfolder"></a><span data-ttu-id="c44bb-338">BuildOutputTargetFolder</span><span class="sxs-lookup"><span data-stu-id="c44bb-338">BuildOutputTargetFolder</span></span>

<span data-ttu-id="c44bb-339">Çıkış derlemelerinin yerleştirileceği klasörü belirtir.</span><span class="sxs-lookup"><span data-stu-id="c44bb-339">Specifies the folder where to place the output assemblies.</span></span> <span data-ttu-id="c44bb-340">Çıkış derlemeleri (ve diğer çıkış dosyaları) ilgili çerçeve klasörlerine kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="c44bb-340">The output assemblies (and other output files) are copied into their respective framework folders.</span></span>

### <a name="contenttargetfolders"></a><span data-ttu-id="c44bb-341">ContentTargetFolders</span><span class="sxs-lookup"><span data-stu-id="c44bb-341">ContentTargetFolders</span></span>

<span data-ttu-id="c44bb-342">Bu özellik, kendileri için belirtilmemişse, tüm içerik dosyalarının gitmesi gereken varsayılan konumu belirtir `PackagePath` .</span><span class="sxs-lookup"><span data-stu-id="c44bb-342">This property specifies the default location of where all the content files should go if `PackagePath` is not specified for them.</span></span> <span data-ttu-id="c44bb-343">Varsayılan değer "Content; contentFiles" dır.</span><span class="sxs-lookup"><span data-stu-id="c44bb-343">The default value is "content;contentFiles".</span></span>

### <a name="nuspecfile"></a><span data-ttu-id="c44bb-344">Nusguus dosyası</span><span class="sxs-lookup"><span data-stu-id="c44bb-344">NuspecFile</span></span>

<span data-ttu-id="c44bb-345">Paketleme için kullanılan *. nuspec* dosyasının göreli veya mutlak yolu.</span><span class="sxs-lookup"><span data-stu-id="c44bb-345">Relative or absolute path to the *.nuspec* file being used for packing.</span></span>

> [!NOTE]
> <span data-ttu-id="c44bb-346">*. Nuspec* dosyası belirtilmişse, **yalnızca** paketleme bilgileri için kullanılır ve projelerdeki tüm bilgiler kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="c44bb-346">If the *.nuspec* file is specified, it's used **exclusively** for packaging information and any information in the projects is not used.</span></span>

### <a name="nuspecbasepath"></a><span data-ttu-id="c44bb-347">Nusgubasepath</span><span class="sxs-lookup"><span data-stu-id="c44bb-347">NuspecBasePath</span></span>

<span data-ttu-id="c44bb-348">*. Nuspec* dosyasının temel yolu.</span><span class="sxs-lookup"><span data-stu-id="c44bb-348">Base path for the *.nuspec* file.</span></span>

### <a name="nuspecproperties"></a><span data-ttu-id="c44bb-349">Nus, Properties</span><span class="sxs-lookup"><span data-stu-id="c44bb-349">NuspecProperties</span></span>

<span data-ttu-id="c44bb-350">Anahtar = değer çiftlerinin noktalı virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="c44bb-350">Semicolon separated list of key=value pairs.</span></span>

## <a name="assemblyinfo-properties"></a><span data-ttu-id="c44bb-351">AssemblyInfo özellikleri</span><span class="sxs-lookup"><span data-stu-id="c44bb-351">AssemblyInfo properties</span></span>

<span data-ttu-id="c44bb-352">Genellikle *AssemblyInfo* dosyasında bulunan [derleme öznitelikleri](../../standard/assembly/set-attributes.md) artık özelliklerden otomatik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c44bb-352">[Assembly attributes](../../standard/assembly/set-attributes.md) that were typically present in an *AssemblyInfo* file are now automatically generated from properties.</span></span>

### <a name="properties-per-attribute"></a><span data-ttu-id="c44bb-353">Öznitelik başına Özellikler</span><span class="sxs-lookup"><span data-stu-id="c44bb-353">Properties per attribute</span></span>

<span data-ttu-id="c44bb-354">Aşağıdaki tabloda gösterildiği gibi, her öznitelik, içeriğini denetleyen ve diğeri oluşturmayı devre dışı bırakan bir özelliğe sahiptir:</span><span class="sxs-lookup"><span data-stu-id="c44bb-354">As shown in the following table, each attribute has a property that controls its content and another that disables its generation:</span></span>

| <span data-ttu-id="c44bb-355">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c44bb-355">Attribute</span></span>                                                      | <span data-ttu-id="c44bb-356">Özellik</span><span class="sxs-lookup"><span data-stu-id="c44bb-356">Property</span></span>               | <span data-ttu-id="c44bb-357">Devre dışı bırakılacak Özellik</span><span class="sxs-lookup"><span data-stu-id="c44bb-357">Property to disable</span></span>                             |
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

<span data-ttu-id="c44bb-358">Notlar:</span><span class="sxs-lookup"><span data-stu-id="c44bb-358">Notes:</span></span>

- <span data-ttu-id="c44bb-359">`AssemblyVersion`ve `FileVersion` Varsayılan, `$(Version)` sonek olmadan değerini alır.</span><span class="sxs-lookup"><span data-stu-id="c44bb-359">`AssemblyVersion` and `FileVersion` default is to take the value of `$(Version)` without suffix.</span></span> <span data-ttu-id="c44bb-360">Örneğin, ise, `$(Version)` `1.2.3-beta.4` değer olacaktır `1.2.3` .</span><span class="sxs-lookup"><span data-stu-id="c44bb-360">For example, if `$(Version)` is `1.2.3-beta.4`, then the value would be `1.2.3`.</span></span>
- <span data-ttu-id="c44bb-361">`InformationalVersion`Varsayılan değer olarak değeridir `$(Version)` .</span><span class="sxs-lookup"><span data-stu-id="c44bb-361">`InformationalVersion` defaults to the value of `$(Version)`.</span></span>
- <span data-ttu-id="c44bb-362">`InformationalVersion``$(SourceRevisionId)`, özelliği varsa eklenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="c44bb-362">`InformationalVersion` has `$(SourceRevisionId)` appended if the property is present.</span></span> <span data-ttu-id="c44bb-363">Kullanılarak devre dışı bırakılabilir `IncludeSourceRevisionInInformationalVersion` .</span><span class="sxs-lookup"><span data-stu-id="c44bb-363">It can be disabled using `IncludeSourceRevisionInInformationalVersion`.</span></span>
- <span data-ttu-id="c44bb-364">`Copyright``Description`Ayrıca, NuGet meta verileri için de Özellikler kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c44bb-364">`Copyright` and `Description` properties are also used for NuGet metadata.</span></span>
- <span data-ttu-id="c44bb-365">`Configuration`Tüm derleme işlemiyle paylaşılır ve `--configuration` komutları parametresi aracılığıyla ayarlanır `dotnet` .</span><span class="sxs-lookup"><span data-stu-id="c44bb-365">`Configuration` is shared with all the build process and set via the `--configuration` parameter of `dotnet` commands.</span></span>

### <a name="generateassemblyinfo"></a><span data-ttu-id="c44bb-366">Generateassemblyınfo</span><span class="sxs-lookup"><span data-stu-id="c44bb-366">GenerateAssemblyInfo</span></span>

<span data-ttu-id="c44bb-367">Tüm AssemblyInfo üretimini etkinleştiren veya devre dışı bırakan bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="c44bb-367">A Boolean that enable or disable all the AssemblyInfo generation.</span></span> <span data-ttu-id="c44bb-368">Varsayılan değer: `true`.</span><span class="sxs-lookup"><span data-stu-id="c44bb-368">The default value is `true`.</span></span>

### <a name="generatedassemblyinfofile"></a><span data-ttu-id="c44bb-369">GeneratedAssemblyInfoFile</span><span class="sxs-lookup"><span data-stu-id="c44bb-369">GeneratedAssemblyInfoFile</span></span>

<span data-ttu-id="c44bb-370">Oluşturulan derleme bilgileri dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="c44bb-370">The path of the generated assembly info file.</span></span> <span data-ttu-id="c44bb-371">Varsayılan olarak `$(IntermediateOutputPath)` (obj) dizinindeki bir dosya.</span><span class="sxs-lookup"><span data-stu-id="c44bb-371">Default to a file in the `$(IntermediateOutputPath)` (obj) directory.</span></span>
