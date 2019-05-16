---
title: .NET Core csproj biçimine eklemeler
description: Varolan ve .NET Core csproj dosyalarına arasındaki farklar hakkında bilgi edinin
ms.date: 04/08/2019
ms.openlocfilehash: 9c1f084af68010632cbe595858b2f242d37af598
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65631812"
---
# <a name="additions-to-the-csproj-format-for-net-core"></a><span data-ttu-id="6a84a-103">.NET Core csproj biçimine eklemeler</span><span class="sxs-lookup"><span data-stu-id="6a84a-103">Additions to the csproj format for .NET Core</span></span>

<span data-ttu-id="6a84a-104">Bu belge proje dosyaları taşımak bir parçası olarak eklenmiş olan değişiklikler özetlenmektedir *project.json* için *csproj* ve [MSBuild](https://github.com/Microsoft/MSBuild).</span><span class="sxs-lookup"><span data-stu-id="6a84a-104">This document outlines the changes that were added to the project files as part of the move from *project.json* to *csproj* and [MSBuild](https://github.com/Microsoft/MSBuild).</span></span> <span data-ttu-id="6a84a-105">Genel proje dosyasının söz dizimi ve başvurusu hakkında daha fazla bilgi için bkz: [MSBuild proje dosyası](/visualstudio/msbuild/msbuild-project-file-schema-reference) belgeleri.</span><span class="sxs-lookup"><span data-stu-id="6a84a-105">For more information about general project file syntax and reference, see [the MSBuild project file](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation.</span></span>

## <a name="implicit-package-references"></a><span data-ttu-id="6a84a-106">Örtük paket başvuruları</span><span class="sxs-lookup"><span data-stu-id="6a84a-106">Implicit package references</span></span>

<span data-ttu-id="6a84a-107">Meta paketler dolaylı olarak başvurulan belirtilen hedef çerçeveleri göre `<TargetFramework>` veya `<TargetFrameworks>` proje dosyanızın özelliği.</span><span class="sxs-lookup"><span data-stu-id="6a84a-107">Metapackages are implicitly referenced based on the target framework(s) specified in the `<TargetFramework>` or `<TargetFrameworks>` property of your project file.</span></span> <span data-ttu-id="6a84a-108">`<TargetFrameworks>` yoksayılır `<TargetFramework>` olduğu belirtildiğinde, sipariş bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="6a84a-108">`<TargetFrameworks>` is ignored if `<TargetFramework>` is specified, independent of order.</span></span> <span data-ttu-id="6a84a-109">Daha fazla bilgi için [paketler, meta paketler ve çerçeveler](../packages.md).</span><span class="sxs-lookup"><span data-stu-id="6a84a-109">For more information, see [Packages, metapackages and frameworks](../packages.md).</span></span> 

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

### <a name="recommendations"></a><span data-ttu-id="6a84a-110">Öneriler</span><span class="sxs-lookup"><span data-stu-id="6a84a-110">Recommendations</span></span>

<span data-ttu-id="6a84a-111">Bu yana `Microsoft.NETCore.App` veya `NETStandard.Library` meta paketler dolaylı olarak başvurulan, önerilen en iyi yöntemlerimizi aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="6a84a-111">Since `Microsoft.NETCore.App` or `NETStandard.Library` metapackages are implicitly referenced, the following are our recommended best practices:</span></span>

* <span data-ttu-id="6a84a-112">.NET Core veya .NET Standard hedeflenirken açık bir başvuru hiçbir zaman sahip `Microsoft.NETCore.App` veya `NETStandard.Library` meta paketler aracılığıyla bir `<PackageReference>` proje dosyanızda öğesi.</span><span class="sxs-lookup"><span data-stu-id="6a84a-112">When targeting .NET Core or .NET Standard, never have an explicit reference to the `Microsoft.NETCore.App` or `NETStandard.Library` metapackages via a `<PackageReference>` item in your project file.</span></span>
* <span data-ttu-id="6a84a-113">.NET Core'u hedefleyen, belirli bir çalışma zamanı sürümünü gerekiyorsa kullanmalısınız `<RuntimeFrameworkVersion>` projenizdeki özelliği (örneğin, `1.0.4`) metapackage başvuran yerine.</span><span class="sxs-lookup"><span data-stu-id="6a84a-113">If you need a specific version of the runtime when targeting .NET Core, you should use the `<RuntimeFrameworkVersion>` property in your project (for example, `1.0.4`) instead of referencing the metapackage.</span></span>
  * <span data-ttu-id="6a84a-114">Kullanıyorsanız gerçekleşebilir [müstakil dağıtımları](../deploying/index.md#self-contained-deployments-scd) 1.0.0 belirli bir düzeltme eki sürümü ihtiyacınız ve örneğin LTS çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="6a84a-114">This might happen if you are using [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) and you need a specific patch version of 1.0.0 LTS runtime, for example.</span></span>
* <span data-ttu-id="6a84a-115">Belirli bir sürümünü gerekiyorsa `NETStandard.Library` kullanabileceğiniz .NET Standard hedeflenirken metapackage `<NetStandardImplicitPackageVersion>` özelliği ve kümesi sürümü ihtiyacınız.</span><span class="sxs-lookup"><span data-stu-id="6a84a-115">If you need a specific version of the `NETStandard.Library` metapackage when targeting .NET Standard, you can use the `<NetStandardImplicitPackageVersion>` property and set the version you need.</span></span>
* <span data-ttu-id="6a84a-116">Açıkça eklemeyin veya güncelleştirme ya da başvuruları `Microsoft.NETCore.App` veya `NETStandard.Library` metapackage .NET Framework projelerindeki.</span><span class="sxs-lookup"><span data-stu-id="6a84a-116">Don't explicitly add or update references to either the `Microsoft.NETCore.App` or `NETStandard.Library` metapackage in .NET Framework projects.</span></span> <span data-ttu-id="6a84a-117">Herhangi bir sürümünü `NETStandard.Library` NuGet bir .NET Standard tabanlı NuGet paketini otomatik olarak kullanarak bu sürümü yüklendiğinde gereklidir.</span><span class="sxs-lookup"><span data-stu-id="6a84a-117">If any version of `NETStandard.Library` is needed when using a .NET Standard-based NuGet package, NuGet automatically installs that version.</span></span>

## <a name="implicit-version-for-some-package-references"></a><span data-ttu-id="6a84a-118">Bazı paket başvuruları için örtük sürümü</span><span class="sxs-lookup"><span data-stu-id="6a84a-118">Implicit version for some package references</span></span>

<span data-ttu-id="6a84a-119">Çoğu açık olan [ `<PackageReference>` ](#packagereference) ayarının gerekli olmasını `Version` kullanılacak NuGet Paket sürümü belirtmek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="6a84a-119">Most usages of [`<PackageReference>`](#packagereference) require setting the `Version` attribute to specify the NuGet package version to be used.</span></span> <span data-ttu-id="6a84a-120">.NET Core 2.1 veya 2.2 ve başvuru kullanırken [Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage-app) veya [Microsoft.AspNetCore.All](/aspnet/core/fundamentals/metapackage), ancak öznitelik gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="6a84a-120">When using .NET Core 2.1 or 2.2 and referencing [Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage-app) or [Microsoft.AspNetCore.All](/aspnet/core/fundamentals/metapackage), however, the  attribute is unnecessary.</span></span> <span data-ttu-id="6a84a-121">.NET Core SDK'sı sürümü kullanılmalıdır bu paketlerin otomatik olarak seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6a84a-121">The .NET Core SDK can automatically select the version of these packages that should be used.</span></span>

### <a name="recommendation"></a><span data-ttu-id="6a84a-122">Öneri</span><span class="sxs-lookup"><span data-stu-id="6a84a-122">Recommendation</span></span>

<span data-ttu-id="6a84a-123">Başvururken `Microsoft.AspNetCore.App` veya `Microsoft.AspNetCore.All` paketleri kendi sürüm belirtmeyin.</span><span class="sxs-lookup"><span data-stu-id="6a84a-123">When referencing the `Microsoft.AspNetCore.App` or `Microsoft.AspNetCore.All` packages, do not specify their version.</span></span> <span data-ttu-id="6a84a-124">Bir sürüm belirtilmezse, SDK'sı uyarı NETSDK1071 üretebilir.</span><span class="sxs-lookup"><span data-stu-id="6a84a-124">If a version is specified, the SDK may produce warning NETSDK1071.</span></span> <span data-ttu-id="6a84a-125">Bu uyarıyı düzeltmek için aşağıdaki örnekte Paket sürümü gibi kaldırın:</span><span class="sxs-lookup"><span data-stu-id="6a84a-125">To fix this warning, remove the package version like in the following example:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.AspNetCore.App" />
</ItemGroup>
```

> <span data-ttu-id="6a84a-126">Bilinen sorun: .NET Core 2.1 SDK proje Microsoft.NET.Sdk.Web kullandığında, yalnızca bu söz dizimi desteklenir.</span><span class="sxs-lookup"><span data-stu-id="6a84a-126">Known issue: the .NET Core 2.1 SDK only supported this syntax when the project also uses Microsoft.NET.Sdk.Web.</span></span> <span data-ttu-id="6a84a-127">Bu .NET Core 2.2 SDK çözülür.</span><span class="sxs-lookup"><span data-stu-id="6a84a-127">This is resolved in the .NET Core 2.2 SDK.</span></span>

<span data-ttu-id="6a84a-128">ASP.NET Core meta paketler bu başvuruları normal NuGet paketlerini biraz farklı bir davranış vardır.</span><span class="sxs-lookup"><span data-stu-id="6a84a-128">These references to ASP.NET Core metapackages have a slightly different behavior from most normal NuGet packages.</span></span> <span data-ttu-id="6a84a-129">[Framework bağımlı dağıtımları](../deploying/index.md#framework-dependent-deployments-fdd) otomatik olarak bu meta paketler kullanan uygulamalar ASP.NET Core paylaşılan çerçeve yararlanın.</span><span class="sxs-lookup"><span data-stu-id="6a84a-129">[Framework-dependent deployments](../deploying/index.md#framework-dependent-deployments-fdd) of applications that use these metapackages automatically take advantage of the ASP.NET Core shared framework.</span></span> <span data-ttu-id="6a84a-130">Meta paketler kullandığınızda **hiçbir** başvurulan bir ASP.NET Core NuGet paket varlıklarından uygulamayla dağıtılan — ASP.NET Core paylaşılan çerçeve bu varlıkları içerir.</span><span class="sxs-lookup"><span data-stu-id="6a84a-130">When you use the metapackages, **no** assets from the referenced ASP.NET Core NuGet packages are deployed with the application—the ASP.NET Core shared framework contains these assets.</span></span> <span data-ttu-id="6a84a-131">Paylaşılan çerçevesindeki varlıkları, uygulama başlatma süresini kısaltmak hedef platform için en iyi duruma getirilir.</span><span class="sxs-lookup"><span data-stu-id="6a84a-131">The assets in the shared framework are optimized for the target platform to improve application startup time.</span></span> <span data-ttu-id="6a84a-132">Paylaşılan altyapısı hakkında daha fazla bilgi için bkz. [.NET Core dağıtımı paketleme](../build/distribution-packaging.md).</span><span class="sxs-lookup"><span data-stu-id="6a84a-132">For more information about shared framework, see [.NET Core distribution packaging](../build/distribution-packaging.md).</span></span>

<span data-ttu-id="6a84a-133">Bir sürüm varsa *olduğu* belirtilen bunu olarak işlem görür *minimum* ASP.NET Core paylaşılan framework framework bağımlı dağıtımları ve olarak sürümü bir *tam* sürümü için bağımsız dağıtımlar.</span><span class="sxs-lookup"><span data-stu-id="6a84a-133">If a version *is* specified, it's treated as the *minimum* version of ASP.NET Core shared framework for framework-dependent deployments and as an *exact* version for self-contained deployments.</span></span> <span data-ttu-id="6a84a-134">Bu, aşağıdaki sonuçları sahip olabilir:</span><span class="sxs-lookup"><span data-stu-id="6a84a-134">This can have the following consequences:</span></span>

* <span data-ttu-id="6a84a-135">ASP.NET Core sürümünün yüklü sunucu PackageReference belirtilen sürümünden küçük, başlatmak .NET Core işlemi başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="6a84a-135">If the version of ASP.NET Core installed on the server is less than the version specified on the PackageReference, the .NET Core process fails to launch.</span></span> <span data-ttu-id="6a84a-136">Güncelleştirmeleri barındırma ortamları gibi Azure içinde kullanılabilir yapılmıştır. önce güncelleştirmeleri metapackage için genellikle NuGet.org üzerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6a84a-136">Updates to the metapackage are often available on NuGet.org before updates have been made available in hosting environments such as Azure.</span></span> <span data-ttu-id="6a84a-137">ASP.NET Core PackageReference sürümüne güncelleştirme dağıtılan bir uygulama başarısız olmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="6a84a-137">Updating the version on the PackageReference to ASP.NET Core could cause a deployed application to fail.</span></span>
* <span data-ttu-id="6a84a-138">Uygulama olarak dağıtılırsa bir [müstakil dağıtım](../deploying/index.md#self-contained-deployments-scd), .NET Core için en son güvenlik güncelleştirmelerini uygulama içeremez.</span><span class="sxs-lookup"><span data-stu-id="6a84a-138">If the application is deployed as a [self-contained deployment](../deploying/index.md#self-contained-deployments-scd), the application may not contain the latest security updates to .NET Core.</span></span> <span data-ttu-id="6a84a-139">Bir sürüm belirtilmezse, SDK'sını ASP.NET Core en yeni sürümünü otomatik olarak kendi başına dağıtım içerebilir.</span><span class="sxs-lookup"><span data-stu-id="6a84a-139">When a version isn't specified, the SDK can automatically include the newest version of ASP.NET Core in the self-contained deployment.</span></span>

## <a name="default-compilation-includes-in-net-core-projects"></a><span data-ttu-id="6a84a-140">.NET Core projelerinde varsayılan derleme içerir</span><span class="sxs-lookup"><span data-stu-id="6a84a-140">Default compilation includes in .NET Core projects</span></span>

<span data-ttu-id="6a84a-141">Git ile *csproj* biçimi en son SDK sürümlerinde, varsayılan içerir ve derleme öğeleri ve SDK'sı özellikleri dosyalarının gömülü kaynaklar için dışlar Taşındık.</span><span class="sxs-lookup"><span data-stu-id="6a84a-141">With the move to the *csproj* format in the latest SDK versions, we've moved the default includes and excludes for compile items and embedded resources to the SDK properties files.</span></span> <span data-ttu-id="6a84a-142">Bu, artık bu öğeler, proje dosyanızda belirtmek gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="6a84a-142">This means that you no longer need to specify these items in your project file.</span></span>

<span data-ttu-id="6a84a-143">Bunu yapmak için ana nedeni, proje dosyanızda dağınıklık azaltmaktır.</span><span class="sxs-lookup"><span data-stu-id="6a84a-143">The main reason for doing this is to reduce the clutter in your project file.</span></span> <span data-ttu-id="6a84a-144">Oluşturduğunuz her projede tekrarlamanız gerekmez. Bu nedenle en yaygın kullanım örnekleri, SDK'da bulunan Varsayılanları kapsamalıdır.</span><span class="sxs-lookup"><span data-stu-id="6a84a-144">The defaults that are present in the SDK should cover most common use cases, so there is no need to repeat them in every project that you create.</span></span> <span data-ttu-id="6a84a-145">Bu, gerekirse yanı sıra anlamak, el ile düzenlemek çok daha kolay olan daha küçük proje dosyaları için yol açar.</span><span class="sxs-lookup"><span data-stu-id="6a84a-145">This leads to smaller project files that are much easier to understand as well as edit by hand, if needed.</span></span>

<span data-ttu-id="6a84a-146">Aşağıdaki tablo, hangi öğe ve hangi gösterir [eğik çizgi genelleştirmeler](https://en.wikipedia.org/wiki/Glob_(programming)) her ikisi de dahil ve hariç SDK'yı:</span><span class="sxs-lookup"><span data-stu-id="6a84a-146">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are both included and excluded in the SDK:</span></span>

| <span data-ttu-id="6a84a-147">Öğe</span><span class="sxs-lookup"><span data-stu-id="6a84a-147">Element</span></span>           | <span data-ttu-id="6a84a-148">Glob içerir</span><span class="sxs-lookup"><span data-stu-id="6a84a-148">Include glob</span></span>                              | <span data-ttu-id="6a84a-149">Glob Dışla</span><span class="sxs-lookup"><span data-stu-id="6a84a-149">Exclude glob</span></span>                                                  | <span data-ttu-id="6a84a-150">Glob Kaldır</span><span class="sxs-lookup"><span data-stu-id="6a84a-150">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| <span data-ttu-id="6a84a-151">Derleme</span><span class="sxs-lookup"><span data-stu-id="6a84a-151">Compile</span></span>           | <span data-ttu-id="6a84a-152">\*\*/\*.cs (veya diğer dil uzantıları)</span><span class="sxs-lookup"><span data-stu-id="6a84a-152">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="6a84a-153">\*\*/\*.user;  \*\*/\*.\* Proj;  \* \* / \*.sln;  \* \* / \*.vssscc</span><span class="sxs-lookup"><span data-stu-id="6a84a-153">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="6a84a-154">Yok</span><span class="sxs-lookup"><span data-stu-id="6a84a-154">N/A</span></span>                      |
| <span data-ttu-id="6a84a-155">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="6a84a-155">EmbeddedResource</span></span>  | <span data-ttu-id="6a84a-156">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="6a84a-156">\*\*/\*.resx</span></span>                              | <span data-ttu-id="6a84a-157">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="6a84a-157">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="6a84a-158">Yok</span><span class="sxs-lookup"><span data-stu-id="6a84a-158">N/A</span></span>                      |
| <span data-ttu-id="6a84a-159">None</span><span class="sxs-lookup"><span data-stu-id="6a84a-159">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="6a84a-160">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="6a84a-160">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="6a84a-161">\*\*/\*.cs; \* \* / \*.resx</span><span class="sxs-lookup"><span data-stu-id="6a84a-161">\*\*/\*.cs; \*\*/\*.resx</span></span>   |

> [!NOTE]
> <span data-ttu-id="6a84a-162">**Glob hariç** her zaman hariç `./bin` ve `./obj` tarafından temsil edilen klasörleri `$(BaseOutputPath)` ve `$(BaseIntermediateOutputPath)` MSBuild özellikleri sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="6a84a-162">**Exclude glob** always excludes the `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, respectively.</span></span> <span data-ttu-id="6a84a-163">Bir bütün olarak tüm dışlar tarafından temsil edilen `$(DefaultItemExcludes)`.</span><span class="sxs-lookup"><span data-stu-id="6a84a-163">As a whole, all excludes are represented by `$(DefaultItemExcludes)`.</span></span>

<span data-ttu-id="6a84a-164">Projenizde eğik çizgi genelleştirmeler sahip ve en son SDK'sını kullanarak oluşturmaya çalışırsanız, aşağıdaki hatayı alırsınız:</span><span class="sxs-lookup"><span data-stu-id="6a84a-164">If you have globs in your project and you try to build it using the newest SDK, you'll get the following error:</span></span>

> <span data-ttu-id="6a84a-165">Yinelenen Derleme öğeleri dahil.</span><span class="sxs-lookup"><span data-stu-id="6a84a-165">Duplicate Compile items were included.</span></span> <span data-ttu-id="6a84a-166">.NET SDK'sı varsayılan olarak, proje dizinine derleme öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="6a84a-166">The .NET SDK includes Compile items from your project directory by default.</span></span> <span data-ttu-id="6a84a-167">Bu öğeler proje dosyanızdan kaldırın ya da proje dosyanızda bunları açıkça eklemek istiyorsanız 'EnableDefaultCompileItems' özelliği 'false' ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6a84a-167">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

<span data-ttu-id="6a84a-168">Bu hataya almak için ya da açık kaldırabilirsiniz `Compile` olanlarla eşleşmesi öğeleri önceki tabloda listelenen veya ayarlayabilirsiniz `<EnableDefaultCompileItems>` özelliğini `false`, şöyle:</span><span class="sxs-lookup"><span data-stu-id="6a84a-168">In order to get around this error, you can either remove the explicit `Compile` items that match the ones listed on the previous table, or you can set the `<EnableDefaultCompileItems>` property to `false`, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

<span data-ttu-id="6a84a-169">Bu özelliği ayarlamak `false` burada b varsayılan eğik çizgi genelleştirmeler projenizde belirlemek için önceki SDK'ları davranışını geri dönülüyor örtük ekleme, devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="6a84a-169">Setting this property to `false` will disable implicit inclusion, reverting to the behavior of previous SDKs where you had to specify the default globs in your project.</span></span>

<span data-ttu-id="6a84a-170">Bu değişiklik, ana değiştirmez, diğer mekanizması içerir.</span><span class="sxs-lookup"><span data-stu-id="6a84a-170">This change does not modify the main mechanics of other includes.</span></span> <span data-ttu-id="6a84a-171">Örneğin, uygulamanız ile yayımlanan için bazı dosyaları belirtmek istiyorsanız ancak içinde bilinen mekanizmaları kullanmaya devam edebilirsiniz *csproj* söz konusu (örneğin, `<Content>` öğesi).</span><span class="sxs-lookup"><span data-stu-id="6a84a-171">However, if you wish to specify, for example, some files to get published with your app, you can still use the known mechanisms in *csproj* for that (for example, the `<Content>` element).</span></span>

<span data-ttu-id="6a84a-172">`<EnableDefaultCompileItems>` yalnızca devre dışı bırakır `Compile` eğik çizgi genelleştirmeler diğer eğik çizgi genelleştirmeler, örtük gibi etkilemez ancak `None` için de geçerli glob \*.cs öğeleri.</span><span class="sxs-lookup"><span data-stu-id="6a84a-172">`<EnableDefaultCompileItems>` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob, which also applies to \*.cs items.</span></span> <span data-ttu-id="6a84a-173">Nedeniyle **Çözüm Gezgini** show devam edecek \*.cs öğeleri dahil, bir projenin parçası olarak `None` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="6a84a-173">Because of that, **Solution Explorer** will continue show \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="6a84a-174">Benzer şekilde, ayarladığınız `<EnableDefaultNoneItems>` örtük devre dışı bırakmak için false `None` glob, şöyle:</span><span class="sxs-lookup"><span data-stu-id="6a84a-174">In a similar way, you can set `<EnableDefaultNoneItems>` to false to disable the implicit `None` glob, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

<span data-ttu-id="6a84a-175">Devre dışı bırakmak için **tüm örtük eğik çizgi genelleştirmeler**, ayarlayabileceğiniz `<EnableDefaultItems>` özelliğini `false` aşağıdaki örnekteki gibi:</span><span class="sxs-lookup"><span data-stu-id="6a84a-175">To disable **all implicit globs**, you can set the `<EnableDefaultItems>` property to `false` as in the following example:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a><span data-ttu-id="6a84a-176">MSBuild gördüğünde gibi tüm proje görme</span><span class="sxs-lookup"><span data-stu-id="6a84a-176">How to see the whole project as MSBuild sees it</span></span>

<span data-ttu-id="6a84a-177">Csproj değişiklikleri proje dosyaları büyük ölçüde basitleştirme olsa da, SDK ve hedeflerine dahil olduğunda gördüğünde MSBuild gibi tam olarak genişletilmiş proje görmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6a84a-177">While those csproj changes greatly simplify project files, you might want to see the fully expanded project as MSBuild sees it once the SDK and its targets are included.</span></span> <span data-ttu-id="6a84a-178">Projeyle önişle [ `/pp` geçiş](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) , [ `dotnet msbuild` ](dotnet-msbuild.md) komutunu Katkıları derleme için hangi dosyaların içeri aktarılan hangi gösterir ve kaynakları gerçekten Proje oluşturma:</span><span class="sxs-lookup"><span data-stu-id="6a84a-178">Preprocess the project with [the `/pp` switch](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) of the [`dotnet msbuild`](dotnet-msbuild.md) command, which shows which files are imported, their sources, and their contributions to the build without actually building the project:</span></span>

`dotnet msbuild -pp:fullproject.xml`

<span data-ttu-id="6a84a-179">Birden çok hedef çerçeve proje varsa komutun sonuçlarını yalnızca bunlardan birine bir MSBuild özellik olarak belirterek odaklanmış olur:</span><span class="sxs-lookup"><span data-stu-id="6a84a-179">If the project has multiple target frameworks, the results of the command should be focused on only one of them by specifying it as an MSBuild property:</span></span>

`dotnet msbuild -p:TargetFramework=netcoreapp2.0 -pp:fullproject.xml`

## <a name="additions"></a><span data-ttu-id="6a84a-180">Eklemeleri</span><span class="sxs-lookup"><span data-stu-id="6a84a-180">Additions</span></span>

### <a name="sdk-attribute"></a><span data-ttu-id="6a84a-181">SDK'sı özniteliği</span><span class="sxs-lookup"><span data-stu-id="6a84a-181">Sdk attribute</span></span>

<span data-ttu-id="6a84a-182">Kök `<Project>` öğesinin *.csproj* dosya adlı yeni bir öznitelik sahip `Sdk`.</span><span class="sxs-lookup"><span data-stu-id="6a84a-182">The root `<Project>` element of the *.csproj* file has a new attribute called `Sdk`.</span></span> <span data-ttu-id="6a84a-183">`Sdk` SDK'sı olacağı belirtir proje tarafından kullanılan.</span><span class="sxs-lookup"><span data-stu-id="6a84a-183">`Sdk` specifies which SDK will be used by the project.</span></span> <span data-ttu-id="6a84a-184">SDK'sı olarak [katmanlama belge](cli-msbuild-architecture.md) açıklar, MSBuild kümesidir [görevleri](/visualstudio/msbuild/msbuild-tasks) ve [hedefleri](/visualstudio/msbuild/msbuild-targets) .NET Core kod oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6a84a-184">The SDK, as the [layering document](cli-msbuild-architecture.md) describes, is a set of MSBuild [tasks](/visualstudio/msbuild/msbuild-tasks) and [targets](/visualstudio/msbuild/msbuild-targets) that can build .NET Core code.</span></span> <span data-ttu-id="6a84a-185">Şu üç ana SDK'ları ile .NET Core araçları ve ek bir iki SDK'ları .NET Core 3.0 Önizleme kullanırken gönderin:</span><span class="sxs-lookup"><span data-stu-id="6a84a-185">We ship three main SDKs with the .NET Core tools and an additional two SDKs when using .NET Core 3.0 Preview:</span></span>

1. <span data-ttu-id="6a84a-186">.NET Core SDK kimliği `Microsoft.NET.Sdk`</span><span class="sxs-lookup"><span data-stu-id="6a84a-186">The .NET Core SDK with the ID of `Microsoft.NET.Sdk`</span></span>
2. <span data-ttu-id="6a84a-187">.NET Core web SDK kimliği `Microsoft.NET.Sdk.Web`</span><span class="sxs-lookup"><span data-stu-id="6a84a-187">The .NET Core web SDK with the ID of `Microsoft.NET.Sdk.Web`</span></span>
3. <span data-ttu-id="6a84a-188">SDK kimliği ile .NET Core Razor sınıf kitaplığı, `Microsoft.NET.Sdk.Razor`</span><span class="sxs-lookup"><span data-stu-id="6a84a-188">The .NET Core Razor Class Library SDK with the ID of `Microsoft.NET.Sdk.Razor`</span></span>
4. <span data-ttu-id="6a84a-189">.NET Core çalışan hizmet kimliği `Microsoft.NET.Sdk.Worker` (.NET Core 3.0 Önizleme)</span><span class="sxs-lookup"><span data-stu-id="6a84a-189">The .NET Core Worker Service with the ID of `Microsoft.NET.Sdk.Worker` (.NET Core 3.0 Preview)</span></span>
5. <span data-ttu-id="6a84a-190">.NET Core WinForms ve WPF kimliği `Microsoft.NET.Sdk.WindowsDesktop` (.NET Core 3.0 Önizleme)</span><span class="sxs-lookup"><span data-stu-id="6a84a-190">The .NET Core WinForms and WPF with the ID of `Microsoft.NET.Sdk.WindowsDesktop` (.NET Core 3.0 Preview)</span></span>

<span data-ttu-id="6a84a-191">İhtiyacınız `Sdk` öznitelik kümesi bu kimlikler birine üzerinde `<Project>` .NET Core araçları kullanın ve kodu derleyebilmeniz için öğesi.</span><span class="sxs-lookup"><span data-stu-id="6a84a-191">You need to have the `Sdk` attribute set to one of those IDs on the `<Project>` element in order to use the .NET Core tools and build your code.</span></span>

### <a name="packagereference"></a><span data-ttu-id="6a84a-192">PackageReference</span><span class="sxs-lookup"><span data-stu-id="6a84a-192">PackageReference</span></span>

<span data-ttu-id="6a84a-193">A `<PackageReference>` öğesi öğeyi belirten bir [projedeki NuGet bağımlılık](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="6a84a-193">A `<PackageReference>` item element specifies a [NuGet dependency in the project](/nuget/consume-packages/package-references-in-project-files).</span></span> <span data-ttu-id="6a84a-194">`Include` Özniteliği paket kimliğini belirtir</span><span class="sxs-lookup"><span data-stu-id="6a84a-194">The `Include` attribute specifies the package ID.</span></span>

```xml
<PackageReference Include="<package-id>" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a><span data-ttu-id="6a84a-195">Sürüm</span><span class="sxs-lookup"><span data-stu-id="6a84a-195">Version</span></span>

<span data-ttu-id="6a84a-196">Gerekli `Version` özniteliği geri yüklemek için paket sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="6a84a-196">The required `Version` attribute specifies the version of the package to restore.</span></span> <span data-ttu-id="6a84a-197">Öznitelik kurallarına uyar [NuGet sürüm](/nuget/reference/package-versioning#version-ranges-and-wildcards) düzeni.</span><span class="sxs-lookup"><span data-stu-id="6a84a-197">The attribute respects the rules of the [NuGet versioning](/nuget/reference/package-versioning#version-ranges-and-wildcards) scheme.</span></span> <span data-ttu-id="6a84a-198">Bir tam sürüm eşleşiyorsa varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="6a84a-198">The default behavior is an exact version match.</span></span> <span data-ttu-id="6a84a-199">Örneğin, belirten `Version="1.2.3"` NuGet gösterimine eşdeğerdir `[1.2.3]` tam 1.2.3-Beta için Paket sürümü.</span><span class="sxs-lookup"><span data-stu-id="6a84a-199">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

#### <a name="includeassets-excludeassets-and-privateassets"></a><span data-ttu-id="6a84a-200">IncludeAssets ve ExcludeAssets PrivateAssets</span><span class="sxs-lookup"><span data-stu-id="6a84a-200">IncludeAssets, ExcludeAssets and PrivateAssets</span></span>

<span data-ttu-id="6a84a-201">`IncludeAssets` öznitelik belirtir ait hangi varlıklar tarafından paket belirtilen `<PackageReference>` kullanılması.</span><span class="sxs-lookup"><span data-stu-id="6a84a-201">`IncludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed.</span></span> <span data-ttu-id="6a84a-202">Varsayılan olarak, tüm paket varlıklar dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="6a84a-202">By default, all package assets are included.</span></span>

<span data-ttu-id="6a84a-203">`ExcludeAssets` öznitelik belirtir ait hangi varlıklar tarafından paket belirtilen `<PackageReference>` değil kullanılması.</span><span class="sxs-lookup"><span data-stu-id="6a84a-203">`ExcludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should not be consumed.</span></span>

<span data-ttu-id="6a84a-204">`PrivateAssets` öznitelik belirtir ait hangi varlıklar tarafından paket belirtilen `<PackageReference>` kullanılması ancak sonraki projeye akış değil.</span><span class="sxs-lookup"><span data-stu-id="6a84a-204">`PrivateAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed but not flow to the next project.</span></span> <span data-ttu-id="6a84a-205">`Analyzers`, `Build` Ve `ContentFiles` bu özniteliği mevcut olmadığında varlıkları varsayılan olarak özel.</span><span class="sxs-lookup"><span data-stu-id="6a84a-205">The `Analyzers`, `Build` and `ContentFiles` assets are private by default when this attribute is not present.</span></span>

> [!NOTE]
> <span data-ttu-id="6a84a-206">`PrivateAssets` eşdeğerdir *project.json*/*xproj* `SuppressParent` öğesi.</span><span class="sxs-lookup"><span data-stu-id="6a84a-206">`PrivateAssets` is equivalent to the *project.json*/*xproj* `SuppressParent` element.</span></span>

<span data-ttu-id="6a84a-207">Bu öznitelik, bir veya daha fazla noktalı virgülle ayrılmış aşağıdaki öğeleri içerebilir `;` listeleniyorsa, birden fazla karakter:</span><span class="sxs-lookup"><span data-stu-id="6a84a-207">These attributes can contain one or more of the following items, separated by the semicolon `;` character if more than one is listed:</span></span>

* <span data-ttu-id="6a84a-208">`Compile` -lib klasörünün içeriğini karşı derleme kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6a84a-208">`Compile` – the contents of the lib folder are available to compile against.</span></span>
* <span data-ttu-id="6a84a-209">`Runtime` – çalışma zamanı klasörünün içeriğini dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="6a84a-209">`Runtime` – the contents of the runtime folder are distributed.</span></span>
* <span data-ttu-id="6a84a-210">`ContentFiles` – içeriği *contentfiles* klasörü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6a84a-210">`ContentFiles` – the contents of the *contentfiles* folder are used.</span></span>
* <span data-ttu-id="6a84a-211">`Build` – derleme klasörü özellikler/hedeflerin kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6a84a-211">`Build` – the props/targets in the build folder are used.</span></span>
* <span data-ttu-id="6a84a-212">`Native` – içeriği yerel varlıklar, çalışma zamanı için çıktı klasörüne kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="6a84a-212">`Native` – the contents from native assets are copied to the output folder for runtime.</span></span>
* <span data-ttu-id="6a84a-213">`Analyzers` – Çözümleyicileri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6a84a-213">`Analyzers` – the analyzers are used.</span></span>

<span data-ttu-id="6a84a-214">Alternatif olarak, öznitelik içerebilir:</span><span class="sxs-lookup"><span data-stu-id="6a84a-214">Alternatively, the attribute can contain:</span></span>

* <span data-ttu-id="6a84a-215">`None` – varlıkları hiçbiri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6a84a-215">`None` – none of the assets are used.</span></span>
* <span data-ttu-id="6a84a-216">`All` – tüm varlıkları kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6a84a-216">`All` – all assets are used.</span></span>

### <a name="dotnetclitoolreference"></a><span data-ttu-id="6a84a-217">DotNetCliToolReference</span><span class="sxs-lookup"><span data-stu-id="6a84a-217">DotNetCliToolReference</span></span>
<span data-ttu-id="6a84a-218">A `<DotNetCliToolReference>` öğesi öğesi, kullanıcının proje bağlamında geri yüklemek için istediği CLI aracı belirtir.</span><span class="sxs-lookup"><span data-stu-id="6a84a-218">A `<DotNetCliToolReference>` item element specifies the CLI tool that the user wants to restore in the context of the project.</span></span> <span data-ttu-id="6a84a-219">Bir ardılı olan `tools` düğümünde *project.json*.</span><span class="sxs-lookup"><span data-stu-id="6a84a-219">It's a replacement for the `tools` node in *project.json*.</span></span>

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

#### <a name="version"></a><span data-ttu-id="6a84a-220">Sürüm</span><span class="sxs-lookup"><span data-stu-id="6a84a-220">Version</span></span>

<span data-ttu-id="6a84a-221">`Version` geri yüklemek için paket sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="6a84a-221">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="6a84a-222">Öznitelik kurallarına uyar [NuGet sürüm](/nuget/create-packages/dependency-versions#version-ranges) düzeni.</span><span class="sxs-lookup"><span data-stu-id="6a84a-222">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="6a84a-223">Bir tam sürüm eşleşiyorsa varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="6a84a-223">The default behavior is an exact version match.</span></span> <span data-ttu-id="6a84a-224">Örneğin, belirten `Version="1.2.3"` NuGet gösterimine eşdeğerdir `[1.2.3]` tam 1.2.3-Beta için Paket sürümü.</span><span class="sxs-lookup"><span data-stu-id="6a84a-224">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

### <a name="runtimeidentifiers"></a><span data-ttu-id="6a84a-225">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="6a84a-225">RuntimeIdentifiers</span></span>

<span data-ttu-id="6a84a-226">`<RuntimeIdentifiers>` Özellik öğesi noktalı virgülle ayrılmış bir listesini belirtmenize olanak tanır [çalışma zamanı tanımlayıcılarının (RID'ler)](../rid-catalog.md) projesi için.</span><span class="sxs-lookup"><span data-stu-id="6a84a-226">The `<RuntimeIdentifiers>` property element lets you specify a semicolon-delimited list of [Runtime Identifiers (RIDs)](../rid-catalog.md) for the project.</span></span>
<span data-ttu-id="6a84a-227">RID yayımlama müstakil dağıtımları etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="6a84a-227">RIDs enable publishing self-contained deployments.</span></span>

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a><span data-ttu-id="6a84a-228">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="6a84a-228">RuntimeIdentifier</span></span>

<span data-ttu-id="6a84a-229">`<RuntimeIdentifier>` Özellik öğesi yalnızca bir belirtmenize olanak verir [çalışma zamanı tanımlayıcı (RID)](../rid-catalog.md) projesi için.</span><span class="sxs-lookup"><span data-stu-id="6a84a-229">The `<RuntimeIdentifier>` property element allows you to specify only one [Runtime Identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="6a84a-230">RID kendi içinde bir dağıtım yayımlama sağlar.</span><span class="sxs-lookup"><span data-stu-id="6a84a-230">The RID enables publishing a self-contained deployment.</span></span>

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

<span data-ttu-id="6a84a-231">Kullanım `<RuntimeIdentifiers>` (çoğul) bunun yerine birden çok çalışma zamanlarını yayımlamak gerekiyorsa.</span><span class="sxs-lookup"><span data-stu-id="6a84a-231">Use `<RuntimeIdentifiers>` (plural) instead if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="6a84a-232">`<RuntimeIdentifier>` tek bir çalışma zamanı gerektiğinde daha hızlı derlemeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6a84a-232">`<RuntimeIdentifier>` can provide faster builds when only a single runtime is required.</span></span>

### <a name="packagetargetfallback"></a><span data-ttu-id="6a84a-233">PackageTargetFallback</span><span class="sxs-lookup"><span data-stu-id="6a84a-233">PackageTargetFallback</span></span>

<span data-ttu-id="6a84a-234">`<PackageTargetFallback>` Özellik öğesi, bir dizi paketler geri yüklenirken kullanılacak uyumlu hedefleri belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="6a84a-234">The `<PackageTargetFallback>` property element allows you to specify a set of compatible targets to be used when restoring packages.</span></span> <span data-ttu-id="6a84a-235">Dotnet kullanan paketleri izin vermek için tasarlanmış [TxM (x hedef ad)](/nuget/schema/target-frameworks) bir dotnet TxM bildirmeyin paketlerle çalışılacak.</span><span class="sxs-lookup"><span data-stu-id="6a84a-235">It's designed to allow packages that use the dotnet [TxM (Target x Moniker)](/nuget/schema/target-frameworks) to operate with packages that don't declare a dotnet TxM.</span></span> <span data-ttu-id="6a84a-236">Projenizin kullandığı dotnet TxM sonra eklediğiniz sürece bir dotnet TxM, duruma göre değişir üzerinde gerekir ayrıca tüm paketlere sahip `<PackageTargetFallback>` dotnet ile uyumlu olacak şekilde dotnet olmayan platformlar için projenize.</span><span class="sxs-lookup"><span data-stu-id="6a84a-236">If your project uses the dotnet TxM, then all the packages it depends on must also have a dotnet TxM, unless you add the `<PackageTargetFallback>` to your project in order to allow non-dotnet platforms to be compatible with dotnet.</span></span>

<span data-ttu-id="6a84a-237">Aşağıdaki örnek, projenizdeki tüm hedefleri için geri dönüşler sağlar:</span><span class="sxs-lookup"><span data-stu-id="6a84a-237">The following example provides the fallbacks for all targets in your project:</span></span>

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

<span data-ttu-id="6a84a-238">Aşağıdaki örnek, geri dönüşler yalnızca belirtir `netcoreapp2.1` hedef:</span><span class="sxs-lookup"><span data-stu-id="6a84a-238">The following example specifies the fallbacks only for the `netcoreapp2.1` target:</span></span>

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp2.1'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="nuget-metadata-properties"></a><span data-ttu-id="6a84a-239">NuGet meta veri özelliklerini</span><span class="sxs-lookup"><span data-stu-id="6a84a-239">NuGet metadata properties</span></span>

<span data-ttu-id="6a84a-240">MSBuild için taşıma ile NuGet paketinden paketleme sırasında kullanılan giriş meta verileri geçtiğimizi *project.json* için *.csproj* dosyaları.</span><span class="sxs-lookup"><span data-stu-id="6a84a-240">With the move to MSBuild, we have moved the input metadata that is used when packing a NuGet package from *project.json* to *.csproj* files.</span></span> <span data-ttu-id="6a84a-241">Kullanıcılarınızın içinde gitmek zorunda MSBuild özellikleri girişleri bir `<PropertyGroup>` grubu.</span><span class="sxs-lookup"><span data-stu-id="6a84a-241">The inputs are MSBuild properties so they have to go within a `<PropertyGroup>` group.</span></span> <span data-ttu-id="6a84a-242">Paketleme işleminin girdi olarak kullanılırken kullanılacak özellikleri listesi aşağıdadır `dotnet pack` komutu veya `Pack` MSBuild hedef diğer bir deyişle SDK'ın bir parçası.</span><span class="sxs-lookup"><span data-stu-id="6a84a-242">The following is the list of properties that are used as inputs to the packing process when using the `dotnet pack` command or the `Pack` MSBuild target that is part of the SDK.</span></span>

### <a name="ispackable"></a><span data-ttu-id="6a84a-243">IsPackable</span><span class="sxs-lookup"><span data-stu-id="6a84a-243">IsPackable</span></span>

<span data-ttu-id="6a84a-244">Proje paketlenmiş olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="6a84a-244">A Boolean value that specifies whether the project can be packed.</span></span> <span data-ttu-id="6a84a-245">Varsayılan değer `true` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6a84a-245">The default value is `true`.</span></span>

### <a name="packageversion"></a><span data-ttu-id="6a84a-246">PackageVersion</span><span class="sxs-lookup"><span data-stu-id="6a84a-246">PackageVersion</span></span>

<span data-ttu-id="6a84a-247">Sonuç paketine sahip olacak sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="6a84a-247">Specifies the version that the resulting package will have.</span></span> <span data-ttu-id="6a84a-248">NuGet sürüm dizesinin tüm forms kabul eder.</span><span class="sxs-lookup"><span data-stu-id="6a84a-248">Accepts all forms of NuGet version string.</span></span> <span data-ttu-id="6a84a-249">Varsayılan değer değeri `$(Version)`, diğer bir deyişle, özelliğin `Version` projedeki.</span><span class="sxs-lookup"><span data-stu-id="6a84a-249">Default is the value of `$(Version)`, that is, of the property `Version` in the project.</span></span>

### <a name="packageid"></a><span data-ttu-id="6a84a-250">PackageId</span><span class="sxs-lookup"><span data-stu-id="6a84a-250">PackageId</span></span>

<span data-ttu-id="6a84a-251">Sonuçta elde edilen paket adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6a84a-251">Specifies the name for the resulting package.</span></span> <span data-ttu-id="6a84a-252">Belirtilmezse, `pack` işlemi için kullanılacak varsayılan `AssemblyName` veya dizin adı olarak paketin adı.</span><span class="sxs-lookup"><span data-stu-id="6a84a-252">If not specified, the `pack` operation will default to using the `AssemblyName` or directory name as the name of the package.</span></span>

### <a name="title"></a><span data-ttu-id="6a84a-253">Başlık</span><span class="sxs-lookup"><span data-stu-id="6a84a-253">Title</span></span>

<span data-ttu-id="6a84a-254">Nuget.org ve Visual Studio'da Paket Yöneticisi UI görünümlerde genellikle kullanılan paket bir insan dostu başlığı.</span><span class="sxs-lookup"><span data-stu-id="6a84a-254">A human-friendly title of the package, typically used in UI displays as on nuget.org and the Package Manager in Visual Studio.</span></span> <span data-ttu-id="6a84a-255">Belirtilmezse, paket kimliği yerine kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6a84a-255">If not specified, the package ID is used instead.</span></span>

### <a name="authors"></a><span data-ttu-id="6a84a-256">Yazarlar</span><span class="sxs-lookup"><span data-stu-id="6a84a-256">Authors</span></span>

<span data-ttu-id="6a84a-257">Nuget.org profil adları eşleşen paketleri yazar, noktalı virgülle ayrılmış listesi. Bunlar nuget.org NuGet galerisinde görüntülenir ve paketleri çapraz başvuru için aynı yazarları tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6a84a-257">A semicolon-separated list of packages authors, matching the profile names on nuget.org. These are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span>

### <a name="packagedescription"></a><span data-ttu-id="6a84a-258">PackageDescription</span><span class="sxs-lookup"><span data-stu-id="6a84a-258">PackageDescription</span></span>

<span data-ttu-id="6a84a-259">Kullanıcı Arabirimi ekranı için paketinin uzun açıklaması.</span><span class="sxs-lookup"><span data-stu-id="6a84a-259">A long description of the package for UI display.</span></span>

### <a name="description"></a><span data-ttu-id="6a84a-260">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a84a-260">Description</span></span>

<span data-ttu-id="6a84a-261">Derleme için uzun açıklaması.</span><span class="sxs-lookup"><span data-stu-id="6a84a-261">A long description for the assembly.</span></span> <span data-ttu-id="6a84a-262">Varsa `PackageDescription` bu özellik paketi açıklama olarak da kullanılır belirtilmedi.</span><span class="sxs-lookup"><span data-stu-id="6a84a-262">If `PackageDescription` is not specified then this property is also used as the description of the package.</span></span>

### <a name="copyright"></a><span data-ttu-id="6a84a-263">Telif Hakkı</span><span class="sxs-lookup"><span data-stu-id="6a84a-263">Copyright</span></span>

<span data-ttu-id="6a84a-264">Paketi için telif hakkı ayrıntıları.</span><span class="sxs-lookup"><span data-stu-id="6a84a-264">Copyright details for the package.</span></span>

### <a name="packagerequirelicenseacceptance"></a><span data-ttu-id="6a84a-265">PackageRequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="6a84a-265">PackageRequireLicenseAcceptance</span></span>

<span data-ttu-id="6a84a-266">İstemci paketi yüklemeden önce paket lisansını kabul etmek için tüketici sor olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="6a84a-266">A Boolean value that specifies whether the client must prompt the consumer to accept the package license before installing the package.</span></span> <span data-ttu-id="6a84a-267">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="6a84a-267">The default is `false`.</span></span>

### <a name="packagelicenseexpression"></a><span data-ttu-id="6a84a-268">PackageLicenseExpression</span><span class="sxs-lookup"><span data-stu-id="6a84a-268">PackageLicenseExpression</span></span>

<span data-ttu-id="6a84a-269">Bir [SPDX lisans tanımlayıcısı](https://spdx.org/licenses/) veya ifade.</span><span class="sxs-lookup"><span data-stu-id="6a84a-269">An [SPDX license identifier](https://spdx.org/licenses/) or expression.</span></span> <span data-ttu-id="6a84a-270">Örneğin: `Apache-2.0`</span><span class="sxs-lookup"><span data-stu-id="6a84a-270">For example, `Apache-2.0`.</span></span>

<span data-ttu-id="6a84a-271">Tam listesi sunulmaktadır [SPDX lisans tanımlayıcıları](https://spdx.org/licenses/).</span><span class="sxs-lookup"><span data-stu-id="6a84a-271">Here is the complete list of [SPDX license identifiers](https://spdx.org/licenses/).</span></span> <span data-ttu-id="6a84a-272">NuGet.org yalnızca OSI kabul eder veya kullanırken onaylanan FSF lisans türü ifadesi lisansı.</span><span class="sxs-lookup"><span data-stu-id="6a84a-272">NuGet.org accepts only OSI or FSF approved licenses when using license type expression.</span></span>

<span data-ttu-id="6a84a-273">Bir lisans ifadenin tam sözdizimi aşağıda açıklanan [ABNF](https://tools.ietf.org/html/rfc5234).</span><span class="sxs-lookup"><span data-stu-id="6a84a-273">The exact syntax of the license expressions is described below in [ABNF](https://tools.ietf.org/html/rfc5234).</span></span>

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
> <span data-ttu-id="6a84a-274">Yalnızca biri `PackageLicenseExpression`, `PackageLicenseFile` ve `PackageLicenseUrl` teker teker belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="6a84a-274">Only one of `PackageLicenseExpression`, `PackageLicenseFile` and `PackageLicenseUrl` can be specified at a time.</span></span>

### <a name="packagelicensefile"></a><span data-ttu-id="6a84a-275">PackageLicenseFile</span><span class="sxs-lookup"><span data-stu-id="6a84a-275">PackageLicenseFile</span></span>

<span data-ttu-id="6a84a-276">SPDX tanımlayıcı atanmamış lisans kullandığınız ya da özel bir lisanstır paket içindeki bir lisans dosyası yolu (Aksi takdirde `PackageLicenseExpression` VPN'ye olan)</span><span class="sxs-lookup"><span data-stu-id="6a84a-276">Path to a license file within the package if you are using a license that hasn’t been assigned an SPDX identifier, or it is a custom license (Otherwise `PackageLicenseExpression` is prefered)</span></span>

<span data-ttu-id="6a84a-277">Değiştirir `PackageLicenseUrl`, ile birleştirilemez `PackageLicenseExpression` ve Visual Studio 15.9.4, .NET SDK'sı 2.1.502 veya 2.2.101, gerektirir ya da daha yeni.</span><span class="sxs-lookup"><span data-stu-id="6a84a-277">Replaces `PackageLicenseUrl`, can't be combined with `PackageLicenseExpression` and requires Visual Studio 15.9.4, .NET SDK 2.1.502 or 2.2.101, or newer.</span></span>

<span data-ttu-id="6a84a-278">Lisans dosyası, proje için örnek kullanım açıkça ekleyerek iyileştirmesiyle doludur emin olmak ihtiyacınız olacak:</span><span class="sxs-lookup"><span data-stu-id="6a84a-278">You will need to ensure the license file is packed by adding it explicitly to the project, example usage:</span></span>

```xml
<PropertyGroup>
  <PackageLicenseFile>LICENSE.txt</PackageLicenseFile>
</PropertyGroup>
<ItemGroup>
  <None Include="licenses\LICENSE.txt" Pack="true" PackagePath="$(PackageLicenseFile)"/>
</ItemGroup>
```

### <a name="packagelicenseurl"></a><span data-ttu-id="6a84a-279">PackageLicenseUrl</span><span class="sxs-lookup"><span data-stu-id="6a84a-279">PackageLicenseUrl</span></span>

<span data-ttu-id="6a84a-280">Bir paket için uygun olan lisans URL'si.</span><span class="sxs-lookup"><span data-stu-id="6a84a-280">An URL to the license that is applicable to the package.</span></span> <span data-ttu-id="6a84a-281">(_Visual Studio 15.9.4, .NET SDK'sı 2.1.502 ve 2.2.101 beri kullanım dışı_)</span><span class="sxs-lookup"><span data-stu-id="6a84a-281">(_deprecated since Visual Studio 15.9.4, .NET SDK 2.1.502 and 2.2.101_)</span></span>

### <a name="packageiconurl"></a><span data-ttu-id="6a84a-282">PackageIconUrl</span><span class="sxs-lookup"><span data-stu-id="6a84a-282">PackageIconUrl</span></span>

<span data-ttu-id="6a84a-283">Kullanıcı Arabirimi ekranı pakette için simge olarak kullanılacak bir URL saydam arka plana sahip 64 x 64 görüntüsü.</span><span class="sxs-lookup"><span data-stu-id="6a84a-283">A URL for a 64x64 image with transparent background to use as the icon for the package in UI display.</span></span>

### <a name="packagereleasenotes"></a><span data-ttu-id="6a84a-284">PackageReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="6a84a-284">PackageReleaseNotes</span></span>

<span data-ttu-id="6a84a-285">Paket için sürüm notları.</span><span class="sxs-lookup"><span data-stu-id="6a84a-285">Release notes for the package.</span></span>

### <a name="packagetags"></a><span data-ttu-id="6a84a-286">PackageTags</span><span class="sxs-lookup"><span data-stu-id="6a84a-286">PackageTags</span></span>

<span data-ttu-id="6a84a-287">Etiketleri noktalı virgülle ayrılmış bir listesini, paketi belirler.</span><span class="sxs-lookup"><span data-stu-id="6a84a-287">A semicolon-delimited list of tags that designates the package.</span></span>

### <a name="packageoutputpath"></a><span data-ttu-id="6a84a-288">PackageOutputPath</span><span class="sxs-lookup"><span data-stu-id="6a84a-288">PackageOutputPath</span></span>

<span data-ttu-id="6a84a-289">Paketlenmiş paket bırakılır çıkış yolu belirler.</span><span class="sxs-lookup"><span data-stu-id="6a84a-289">Determines the output path in which the packed package will be dropped.</span></span> <span data-ttu-id="6a84a-290">Varsayılan değer `$(OutputPath)`.</span><span class="sxs-lookup"><span data-stu-id="6a84a-290">Default is `$(OutputPath)`.</span></span>

### <a name="includesymbols"></a><span data-ttu-id="6a84a-291">IncludeSymbols</span><span class="sxs-lookup"><span data-stu-id="6a84a-291">IncludeSymbols</span></span>
<span data-ttu-id="6a84a-292">Proje dolu olduğunda paketi bir ek sembol paketi oluşturmak bu Boolean değerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6a84a-292">This Boolean value indicates whether the package should create an additional symbols package when the project is packed.</span></span> <span data-ttu-id="6a84a-293">Semboller paket biçimi tarafından denetlenir `SymbolPackageFormat` özelliği.</span><span class="sxs-lookup"><span data-stu-id="6a84a-293">The symbols package's format is controlled by the `SymbolPackageFormat` property.</span></span>

### <a name="symbolpackageformat"></a><span data-ttu-id="6a84a-294">SymbolPackageFormat</span><span class="sxs-lookup"><span data-stu-id="6a84a-294">SymbolPackageFormat</span></span>
<span data-ttu-id="6a84a-295">Semboller paket biçimi belirtir.</span><span class="sxs-lookup"><span data-stu-id="6a84a-295">Specifies the format of the symbols package.</span></span> <span data-ttu-id="6a84a-296">"Symbols.nupkg" eski sembolleri paket oluşturulur, bir *. symbols.nupkg* pdb, DLL'ler ve diğer çıkış dosyalarını içeren bir uzantı.</span><span class="sxs-lookup"><span data-stu-id="6a84a-296">If "symbols.nupkg", a legacy symbols package will be created with a *.symbols.nupkg* extension containing PDBs, DLLs, and other output files.</span></span> <span data-ttu-id="6a84a-297">"Snupkg" snupkg sembol paketi içeren taşınabilir pdb oluşturulacak durumunda.</span><span class="sxs-lookup"><span data-stu-id="6a84a-297">If "snupkg", a snupkg symbol package will be created containing the portable PDBs.</span></span> <span data-ttu-id="6a84a-298">"Symbols.nupkg" varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="6a84a-298">Default is "symbols.nupkg".</span></span>

### <a name="includesource"></a><span data-ttu-id="6a84a-299">IncludeSource</span><span class="sxs-lookup"><span data-stu-id="6a84a-299">IncludeSource</span></span>

<span data-ttu-id="6a84a-300">Paketi işlemi bir kaynak paketi oluşturmanız gerekir, bu Boolean değeri gösterir.</span><span class="sxs-lookup"><span data-stu-id="6a84a-300">This Boolean value indicates whether the pack process should create a source package.</span></span> <span data-ttu-id="6a84a-301">Kaynak Paketi kitaplığın kaynak kodunun yanı sıra PDB dosyaları içerir.</span><span class="sxs-lookup"><span data-stu-id="6a84a-301">The source package contains the library's source code as well as PDB files.</span></span> <span data-ttu-id="6a84a-302">Kaynak dosyaları altında isimlerine `src/ProjectName` elde edilen paket dosyasındaki dizin.</span><span class="sxs-lookup"><span data-stu-id="6a84a-302">Source files are put under the `src/ProjectName` directory in the resulting package file.</span></span>

### <a name="istool"></a><span data-ttu-id="6a84a-303">IsTool</span><span class="sxs-lookup"><span data-stu-id="6a84a-303">IsTool</span></span>

<span data-ttu-id="6a84a-304">Tüm çıkış dosyalarını kopyalanıp kopyalanmayacağını belirtir *Araçları* klasörü yerine *LIB* klasör.</span><span class="sxs-lookup"><span data-stu-id="6a84a-304">Specifies whether all output files are copied to the *tools* folder instead of the *lib* folder.</span></span> <span data-ttu-id="6a84a-305">Bu farklı olduğunu unutmayın bir `DotNetCliTool` , belirtilen ayarlayarak `PackageType` içinde *.csproj* dosya.</span><span class="sxs-lookup"><span data-stu-id="6a84a-305">Note that this is different from a `DotNetCliTool` which is specified by setting the `PackageType` in the *.csproj* file.</span></span>

### <a name="repositoryurl"></a><span data-ttu-id="6a84a-306">RepositoryUrl</span><span class="sxs-lookup"><span data-stu-id="6a84a-306">RepositoryUrl</span></span>

<span data-ttu-id="6a84a-307">Depo URL'si, paket için kaynak kodu bulunduğu yerde ve/veya hangi, oluşturulmakta olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="6a84a-307">Specifies the URL for the repository where the source code for the package resides and/or from which it's being built.</span></span>

### <a name="repositorytype"></a><span data-ttu-id="6a84a-308">RepositoryType</span><span class="sxs-lookup"><span data-stu-id="6a84a-308">RepositoryType</span></span>

<span data-ttu-id="6a84a-309">Depo türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="6a84a-309">Specifies the type of the repository.</span></span> <span data-ttu-id="6a84a-310">"Git" varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="6a84a-310">Default is "git".</span></span>

### <a name="nopackageanalysis"></a><span data-ttu-id="6a84a-311">NoPackageAnalysis</span><span class="sxs-lookup"><span data-stu-id="6a84a-311">NoPackageAnalysis</span></span>

<span data-ttu-id="6a84a-312">Paketi paket analiz paketini oluşturduktan sonra çalışmaması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6a84a-312">Specifies that pack should not run package analysis after building the package.</span></span>

### <a name="minclientversion"></a><span data-ttu-id="6a84a-313">MinClientVersion</span><span class="sxs-lookup"><span data-stu-id="6a84a-313">MinClientVersion</span></span>

<span data-ttu-id="6a84a-314">Nuget.exe ve Visual Studio Paket Yöneticisi tarafından zorlanan, bu paketi yüklemek NuGet istemci en düşük sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="6a84a-314">Specifies the minimum version of the NuGet client that can install this package, enforced by nuget.exe and the Visual Studio Package Manager.</span></span>

### <a name="includebuildoutput"></a><span data-ttu-id="6a84a-315">IncludeBuildOutput</span><span class="sxs-lookup"><span data-stu-id="6a84a-315">IncludeBuildOutput</span></span>

<span data-ttu-id="6a84a-316">Bu Boolean değerleri belirten derleme çıktı derlemeleri halinde paketlenmiş olup olmadığını *.nupkg* dosya ya da değil.</span><span class="sxs-lookup"><span data-stu-id="6a84a-316">This Boolean values specifies whether the build output assemblies should be packed into the *.nupkg* file or not.</span></span>

### <a name="includecontentinpack"></a><span data-ttu-id="6a84a-317">IncludeContentInPack</span><span class="sxs-lookup"><span data-stu-id="6a84a-317">IncludeContentInPack</span></span>

<span data-ttu-id="6a84a-318">Bu Boolean değerini tüm öğeleri, bir türü sahip olup olmadığını belirtir `Content` sonuç paketine otomatik olarak dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="6a84a-318">This Boolean value specifies whether any items that have a type of `Content` will be included in the resulting package automatically.</span></span> <span data-ttu-id="6a84a-319">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="6a84a-319">The default is `true`.</span></span>

### <a name="buildoutputtargetfolder"></a><span data-ttu-id="6a84a-320">BuildOutputTargetFolder</span><span class="sxs-lookup"><span data-stu-id="6a84a-320">BuildOutputTargetFolder</span></span>

<span data-ttu-id="6a84a-321">Klasörü çıkış derlemelerin yerleştirileceği yeri belirtir.</span><span class="sxs-lookup"><span data-stu-id="6a84a-321">Specifies the folder where to place the output assemblies.</span></span> <span data-ttu-id="6a84a-322">Çıkış bütünleştirilmiş kodları (ve diğer çıktı dosyalarının) ilgili framework klasörlerine kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="6a84a-322">The output assemblies (and other output files) are copied into their respective framework folders.</span></span>

### <a name="contenttargetfolders"></a><span data-ttu-id="6a84a-323">ContentTargetFolders</span><span class="sxs-lookup"><span data-stu-id="6a84a-323">ContentTargetFolders</span></span>

<span data-ttu-id="6a84a-324">Bu özellik tüm içerik dosyalarını, nereye varsayılan konumu belirtir `PackagePath` kendileri için belirtilmedi.</span><span class="sxs-lookup"><span data-stu-id="6a84a-324">This property specifies the default location of where all the content files should go if `PackagePath` is not specified for them.</span></span> <span data-ttu-id="6a84a-325">Varsayılan değer: "içerik; contentFiles".</span><span class="sxs-lookup"><span data-stu-id="6a84a-325">The default value is "content;contentFiles".</span></span>

### <a name="nuspecfile"></a><span data-ttu-id="6a84a-326">NuspecFile</span><span class="sxs-lookup"><span data-stu-id="6a84a-326">NuspecFile</span></span>

<span data-ttu-id="6a84a-327">Göreli veya mutlak yolunu *.nuspec* paketleme için kullanılan dosya.</span><span class="sxs-lookup"><span data-stu-id="6a84a-327">Relative or absolute path to the *.nuspec* file being used for packing.</span></span>

> [!NOTE]
> <span data-ttu-id="6a84a-328">Varsa *.nuspec* dosya belirtilir, kullanıldığı **özel** için bilgi ve herhangi bir bilgi projelerindeki paketleme kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="6a84a-328">If the *.nuspec* file is specified, it's used **exclusively** for packaging information and any information in the projects is not used.</span></span>

### <a name="nuspecbasepath"></a><span data-ttu-id="6a84a-329">NuspecBasePath</span><span class="sxs-lookup"><span data-stu-id="6a84a-329">NuspecBasePath</span></span>

<span data-ttu-id="6a84a-330">Temel yolunu *.nuspec* dosya.</span><span class="sxs-lookup"><span data-stu-id="6a84a-330">Base path for the *.nuspec* file.</span></span>

### <a name="nuspecproperties"></a><span data-ttu-id="6a84a-331">NuspecProperties</span><span class="sxs-lookup"><span data-stu-id="6a84a-331">NuspecProperties</span></span>

<span data-ttu-id="6a84a-332">Noktalı virgülle ayrılmış listesi anahtar = değer çiftleri.</span><span class="sxs-lookup"><span data-stu-id="6a84a-332">Semicolon separated list of key=value pairs.</span></span>

## <a name="assemblyinfo-properties"></a><span data-ttu-id="6a84a-333">AssemblyInfo özellikleri</span><span class="sxs-lookup"><span data-stu-id="6a84a-333">AssemblyInfo properties</span></span>

<span data-ttu-id="6a84a-334">[Derleme özniteliklerinin](../../framework/app-domains/set-assembly-attributes.md) , genellikle mevcut bir *AssemblyInfo* dosya artık otomatik olarak üretilen özellikleri.</span><span class="sxs-lookup"><span data-stu-id="6a84a-334">[Assembly attributes](../../framework/app-domains/set-assembly-attributes.md) that were typically present in an *AssemblyInfo* file are now automatically generated from properties.</span></span>

### <a name="properties-per-attribute"></a><span data-ttu-id="6a84a-335">Öznitelik başına özellikleri</span><span class="sxs-lookup"><span data-stu-id="6a84a-335">Properties per attribute</span></span>

<span data-ttu-id="6a84a-336">Her öznitelik içeriği ve başka neslini aşağıdaki tabloda gösterildiği gibi devre dışı bırakmak için denetleyen bir özelliğe sahiptir:</span><span class="sxs-lookup"><span data-stu-id="6a84a-336">Each attribute has a property that control its content and another to disable its generation as shown in the following table:</span></span>

| <span data-ttu-id="6a84a-337">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6a84a-337">Attribute</span></span>                                                      | <span data-ttu-id="6a84a-338">Özellik</span><span class="sxs-lookup"><span data-stu-id="6a84a-338">Property</span></span>               | <span data-ttu-id="6a84a-339">Özelliği devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="6a84a-339">Property to disable</span></span>                             |
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

<span data-ttu-id="6a84a-340">Notlar:</span><span class="sxs-lookup"><span data-stu-id="6a84a-340">Notes:</span></span>

* <span data-ttu-id="6a84a-341">`AssemblyVersion` ve `FileVersion` değerini almak için varsayılandır `$(Version)` soneki olmadan.</span><span class="sxs-lookup"><span data-stu-id="6a84a-341">`AssemblyVersion` and `FileVersion` default is to take the value of `$(Version)` without suffix.</span></span> <span data-ttu-id="6a84a-342">Örneğin, varsa `$(Version)` olduğu `1.2.3-beta.4`, değer sonra `1.2.3`.</span><span class="sxs-lookup"><span data-stu-id="6a84a-342">For example, if `$(Version)` is `1.2.3-beta.4`, then the value would be `1.2.3`.</span></span>
* <span data-ttu-id="6a84a-343">`InformationalVersion` değerini varsayılan olarak `$(Version)`.</span><span class="sxs-lookup"><span data-stu-id="6a84a-343">`InformationalVersion` defaults to the value of `$(Version)`.</span></span>
* <span data-ttu-id="6a84a-344">`InformationalVersion` sahip `$(SourceRevisionId)` özelliği varsa eklenir.</span><span class="sxs-lookup"><span data-stu-id="6a84a-344">`InformationalVersion` has `$(SourceRevisionId)` appended if the property is present.</span></span> <span data-ttu-id="6a84a-345">Bunu kullanarak devre dışı bırakılabilir `IncludeSourceRevisionInInformationalVersion`.</span><span class="sxs-lookup"><span data-stu-id="6a84a-345">It can be disabled using `IncludeSourceRevisionInInformationalVersion`.</span></span>
* <span data-ttu-id="6a84a-346">`Copyright` ve `Description` özellikleri NuGet meta veriler için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6a84a-346">`Copyright` and `Description` properties are also used for NuGet metadata.</span></span>
* <span data-ttu-id="6a84a-347">`Configuration` tüm yapı işlemi ile paylaşılır ve aracılığıyla ayarlanan `--configuration` parametresinin `dotnet` komutları.</span><span class="sxs-lookup"><span data-stu-id="6a84a-347">`Configuration` is shared with all the build process and set via the `--configuration` parameter of `dotnet` commands.</span></span>

### <a name="generateassemblyinfo"></a><span data-ttu-id="6a84a-348">GenerateAssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="6a84a-348">GenerateAssemblyInfo</span></span>

<span data-ttu-id="6a84a-349">Etkinleştirme veya tüm AssemblyInfo oluşturma devre dışı bırakan bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="6a84a-349">A Boolean that enable or disable all the AssemblyInfo generation.</span></span> <span data-ttu-id="6a84a-350">Varsayılan değer `true` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6a84a-350">The default value is `true`.</span></span>

### <a name="generatedassemblyinfofile"></a><span data-ttu-id="6a84a-351">GeneratedAssemblyInfoFile</span><span class="sxs-lookup"><span data-stu-id="6a84a-351">GeneratedAssemblyInfoFile</span></span>

<span data-ttu-id="6a84a-352">Oluşturulan derleme bilgileri dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="6a84a-352">The path of the generated assembly info file.</span></span> <span data-ttu-id="6a84a-353">Varsayılan bir dosyaya `$(IntermediateOutputPath)` (obj) dizini.</span><span class="sxs-lookup"><span data-stu-id="6a84a-353">Default to a file in the `$(IntermediateOutputPath)` (obj) directory.</span></span>
