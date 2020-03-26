---
title: .NET Core için csproj formatına eklemeler
description: Varolan ve .NET Core csproj dosyaları arasındaki farklar hakkında bilgi edinin
ms.date: 04/08/2019
ms.openlocfilehash: 9d9e212c9531828a8c2dd51fdd7488c17be41ba2
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134061"
---
# <a name="additions-to-the-csproj-format-for-net-core"></a><span data-ttu-id="4e059-103">.NET Core için csproj formatına eklemeler</span><span class="sxs-lookup"><span data-stu-id="4e059-103">Additions to the csproj format for .NET Core</span></span>

<span data-ttu-id="4e059-104">Bu belge, *project.json'dan* *csproj* ve [MSBuild'e](https://github.com/Microsoft/MSBuild)taşımanın bir parçası olarak proje dosyalarına eklenen değişiklikleri özetleyilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4e059-104">This document outlines the changes that were added to the project files as part of the move from *project.json* to *csproj* and [MSBuild](https://github.com/Microsoft/MSBuild).</span></span> <span data-ttu-id="4e059-105">Genel proje dosyası sözdizimi ve başvurusu hakkında daha fazla bilgi için [MSBuild proje dosya belgelerine](/visualstudio/msbuild/msbuild-project-file-schema-reference) bakın.</span><span class="sxs-lookup"><span data-stu-id="4e059-105">For more information about general project file syntax and reference, see [the MSBuild project file](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation.</span></span>

## <a name="implicit-package-references"></a><span data-ttu-id="4e059-106">Örtülü paket referansları</span><span class="sxs-lookup"><span data-stu-id="4e059-106">Implicit package references</span></span>

<span data-ttu-id="4e059-107">Metapaketler, proje dosyanızın `<TargetFramework>` veya `<TargetFrameworks>` özelliğinizde belirtilen hedef çerçevesine(ler) göre dolaylı olarak başvurulur.</span><span class="sxs-lookup"><span data-stu-id="4e059-107">Metapackages are implicitly referenced based on the target framework(s) specified in the `<TargetFramework>` or `<TargetFrameworks>` property of your project file.</span></span> <span data-ttu-id="4e059-108">`<TargetFrameworks>`belirtilirse, `<TargetFramework>` düzenden bağımsız olarak yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="4e059-108">`<TargetFrameworks>` is ignored if `<TargetFramework>` is specified, independent of order.</span></span> <span data-ttu-id="4e059-109">Daha fazla bilgi için [paketlere, meta paketlere ve çerçevelere](../packages.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="4e059-109">For more information, see [Packages, metapackages, and frameworks](../packages.md).</span></span>

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

### <a name="recommendations"></a><span data-ttu-id="4e059-110">Öneriler</span><span class="sxs-lookup"><span data-stu-id="4e059-110">Recommendations</span></span>

<span data-ttu-id="4e059-111">`Microsoft.NETCore.App` Veya `NETStandard.Library` metapaketler dolaylı olarak başvuruldığından, önerilen en iyi uygulamalar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="4e059-111">Since `Microsoft.NETCore.App` or `NETStandard.Library` metapackages are implicitly referenced, the following are our recommended best practices:</span></span>

- <span data-ttu-id="4e059-112">.NET Core veya .NET Standard'ı hedef alırken, `Microsoft.NETCore.App` `NETStandard.Library` proje dosyanızdaki `<PackageReference>` bir öğe aracılığıyla meta paketlere hiçbir zaman açık bir başvurunuz yoktur.</span><span class="sxs-lookup"><span data-stu-id="4e059-112">When targeting .NET Core or .NET Standard, never have an explicit reference to the `Microsoft.NETCore.App` or `NETStandard.Library` metapackages via a `<PackageReference>` item in your project file.</span></span>
- <span data-ttu-id="4e059-113">.NET Core'u hedefalırken çalışma zamanının belirli bir sürümüne `<RuntimeFrameworkVersion>` ihtiyacınız varsa, meta `1.0.4`pakete başvurmak yerine projenizdeki özelliği (örneğin) kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4e059-113">If you need a specific version of the runtime when targeting .NET Core, you should use the `<RuntimeFrameworkVersion>` property in your project (for example, `1.0.4`) instead of referencing the metapackage.</span></span>
  - <span data-ttu-id="4e059-114">Bu, [bağımsız dağıtımlar](../deploying/index.md#publish-self-contained) kullanıyorsanız ve örneğin 1.0.0 LTS çalışma zamanı belirli bir yama sürümüne ihtiyacınız varsa gerçekleşebilir.</span><span class="sxs-lookup"><span data-stu-id="4e059-114">This might happen if you are using [self-contained deployments](../deploying/index.md#publish-self-contained) and you need a specific patch version of 1.0.0 LTS runtime, for example.</span></span>
- <span data-ttu-id="4e059-115">.NET Standard'ı hedefalırken `NETStandard.Library` metapaketin belirli bir sürümüne ihtiyacınız `<NetStandardImplicitPackageVersion>` varsa, özelliği kullanabilir ve ihtiyacınız olan sürümü ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e059-115">If you need a specific version of the `NETStandard.Library` metapackage when targeting .NET Standard, you can use the `<NetStandardImplicitPackageVersion>` property and set the version you need.</span></span>
- <span data-ttu-id="4e059-116">.NET Framework projelerindeki `Microsoft.NETCore.App` veya meta paketine açıkça eklemeyin veya `NETStandard.Library` güncellemayın.</span><span class="sxs-lookup"><span data-stu-id="4e059-116">Don't explicitly add or update references to either the `Microsoft.NETCore.App` or `NETStandard.Library` metapackage in .NET Framework projects.</span></span> <span data-ttu-id="4e059-117">.NET Standart `NETStandard.Library` tabanlı NuGet paketi kullanırken herhangi bir sürümü gerekiyorsa, NuGet bu sürümü otomatik olarak yükler.</span><span class="sxs-lookup"><span data-stu-id="4e059-117">If any version of `NETStandard.Library` is needed when using a .NET Standard-based NuGet package, NuGet automatically installs that version.</span></span>

## <a name="implicit-version-for-some-package-references"></a><span data-ttu-id="4e059-118">Bazı paket başvuruları için örtülü sürüm</span><span class="sxs-lookup"><span data-stu-id="4e059-118">Implicit version for some package references</span></span>

<span data-ttu-id="4e059-119">Çoğu [`<PackageReference>`](#packagereference) kullanım, kullanılacak `Version` NuGet paket sürümünü belirtmek için özniteliğin ayarını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="4e059-119">Most usages of [`<PackageReference>`](#packagereference) require setting the `Version` attribute to specify the NuGet package version to be used.</span></span> <span data-ttu-id="4e059-120">.NET Core 2.1 veya 2.2'yi kullanırken ve [Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage-app) veya [Microsoft.AspNetCore.All'a](/aspnet/core/fundamentals/metapackage)başvururken, ancak öznitelik gereksizdir.</span><span class="sxs-lookup"><span data-stu-id="4e059-120">When using .NET Core 2.1 or 2.2 and referencing [Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage-app) or [Microsoft.AspNetCore.All](/aspnet/core/fundamentals/metapackage), however, the  attribute is unnecessary.</span></span> <span data-ttu-id="4e059-121">.NET Core SDK, bu paketlerin kullanılması gereken sürümünü otomatik olarak seçebilir.</span><span class="sxs-lookup"><span data-stu-id="4e059-121">The .NET Core SDK can automatically select the version of these packages that should be used.</span></span>

### <a name="recommendation"></a><span data-ttu-id="4e059-122">Öneri</span><span class="sxs-lookup"><span data-stu-id="4e059-122">Recommendation</span></span>

<span data-ttu-id="4e059-123">Paketlere `Microsoft.AspNetCore.App` başvururken, `Microsoft.AspNetCore.All` bunların sürümünü belirtmeyin.</span><span class="sxs-lookup"><span data-stu-id="4e059-123">When referencing the `Microsoft.AspNetCore.App` or `Microsoft.AspNetCore.All` packages, do not specify their version.</span></span> <span data-ttu-id="4e059-124">Bir sürüm belirtilirse, SDK uyarı NETSDK1071 üretebilir.</span><span class="sxs-lookup"><span data-stu-id="4e059-124">If a version is specified, the SDK may produce warning NETSDK1071.</span></span> <span data-ttu-id="4e059-125">Bu uyarıyı düzeltmek için aşağıdaki örnekteki gibi paket sürümünü kaldırın:</span><span class="sxs-lookup"><span data-stu-id="4e059-125">To fix this warning, remove the package version like in the following example:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.AspNetCore.App" />
</ItemGroup>
```

> <span data-ttu-id="4e059-126">Bilinen sorun: .NET Core 2.1 SDK, proje Microsoft.NET.Sdk.Web'i de kullandığında bu sözdizimini yalnızca desteklenebilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4e059-126">Known issue: the .NET Core 2.1 SDK only supported this syntax when the project also uses Microsoft.NET.Sdk.Web.</span></span> <span data-ttu-id="4e059-127">Bu işlem .NET Core 2.2 SDK'da çözülür.</span><span class="sxs-lookup"><span data-stu-id="4e059-127">This is resolved in the .NET Core 2.2 SDK.</span></span>

<span data-ttu-id="4e059-128">Core meta paketleriASP.NET ne atıfta bulunulan bu göndermeler, çoğu normal NuGet paketinden biraz farklı bir davranışa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="4e059-128">These references to ASP.NET Core metapackages have a slightly different behavior from most normal NuGet packages.</span></span> <span data-ttu-id="4e059-129">Bu meta paketleri kullanan uygulamaların [çerçeveye bağımlı dağıtımları,](../deploying/index.md#publish-runtime-dependent) core paylaşılan ASP.NET çerçevesinden otomatik olarak yararlanır.</span><span class="sxs-lookup"><span data-stu-id="4e059-129">[Framework-dependent deployments](../deploying/index.md#publish-runtime-dependent) of applications that use these metapackages automatically take advantage of the ASP.NET Core shared framework.</span></span> <span data-ttu-id="4e059-130">Meta paketleri kullandığınızda, başvurulan ASP.NET Core NuGet paketlerinden **hiçbir** varlık uygulamayla birlikte dağıtılmaz—ASP.NET Core paylaşılan çerçevesi bu varlıkları içerir.</span><span class="sxs-lookup"><span data-stu-id="4e059-130">When you use the metapackages, **no** assets from the referenced ASP.NET Core NuGet packages are deployed with the application—the ASP.NET Core shared framework contains these assets.</span></span> <span data-ttu-id="4e059-131">Paylaşılan çerçevedeki varlıklar, uygulama başlatma süresini iyileştirmek için hedef platform için optimize edilebiyi leştirir.</span><span class="sxs-lookup"><span data-stu-id="4e059-131">The assets in the shared framework are optimized for the target platform to improve application startup time.</span></span> <span data-ttu-id="4e059-132">Paylaşılan çerçeve hakkında daha fazla bilgi için [bkz.](../distribution-packaging.md)</span><span class="sxs-lookup"><span data-stu-id="4e059-132">For more information about shared framework, see [.NET Core distribution packaging](../distribution-packaging.md).</span></span>

<span data-ttu-id="4e059-133">Bir sürüm *belirtilirse,* bu sürüm, ASP.NET Core paylaşılan çerçevesinin çerçeveye bağımlı dağıtımlar için *en az* sürümü ve bağımsız dağıtımlar için *tam* sürüm olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="4e059-133">If a version *is* specified, it's treated as the *minimum* version of ASP.NET Core shared framework for framework-dependent deployments and as an *exact* version for self-contained deployments.</span></span> <span data-ttu-id="4e059-134">Bunun sonuçları aşağıdaki gibi olabilir:</span><span class="sxs-lookup"><span data-stu-id="4e059-134">This can have the following consequences:</span></span>

- <span data-ttu-id="4e059-135">Sunucuda yüklü ASP.NET Core sürümü PackageReference'da belirtilen sürümden daha azsa, .NET Core işlemi başlatılmaz.</span><span class="sxs-lookup"><span data-stu-id="4e059-135">If the version of ASP.NET Core installed on the server is less than the version specified on the PackageReference, the .NET Core process fails to launch.</span></span> <span data-ttu-id="4e059-136">Meta paketteki güncelleştirmeler genellikle Azure gibi barındırma ortamlarında güncelleştirmeler kullanıma sunulmadan önce NuGet.org kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4e059-136">Updates to the metapackage are often available on NuGet.org before updates have been made available in hosting environments such as Azure.</span></span> <span data-ttu-id="4e059-137">ASP.NET Core'a packagereference sürümü güncelleştirilmesi, dağıtılan bir uygulamanın başarısız lığa neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="4e059-137">Updating the version on the PackageReference to ASP.NET Core could cause a deployed application to fail.</span></span>
- <span data-ttu-id="4e059-138">Uygulama bağımsız bir [dağıtım](../deploying/index.md#publish-self-contained)olarak dağıtılırsa, uygulama .NET Core için en son güvenlik güncelleştirmelerini içermeyebilir.</span><span class="sxs-lookup"><span data-stu-id="4e059-138">If the application is deployed as a [self-contained deployment](../deploying/index.md#publish-self-contained), the application may not contain the latest security updates to .NET Core.</span></span> <span data-ttu-id="4e059-139">Bir sürüm belirtilmediğinde, SDK ASP.NET Core'un en yeni sürümünü otomatik olarak kendi kendine yeten dağıtıma ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="4e059-139">When a version isn't specified, the SDK can automatically include the newest version of ASP.NET Core in the self-contained deployment.</span></span>

## <a name="default-compilation-includes-in-net-core-projects"></a><span data-ttu-id="4e059-140">Varsayılan derleme .NET Core projelerinde içerir</span><span class="sxs-lookup"><span data-stu-id="4e059-140">Default compilation includes in .NET Core projects</span></span>

<span data-ttu-id="4e059-141">En son SDK sürümlerinde *csproj* biçimine taşınması yla, öğeleri ve katıştırılmış kaynakları SDK özellik dosyalarına derlemek için varsayılan içerir ve hariç tutsak ettik.</span><span class="sxs-lookup"><span data-stu-id="4e059-141">With the move to the *csproj* format in the latest SDK versions, we've moved the default includes and excludes for compile items and embedded resources to the SDK properties files.</span></span> <span data-ttu-id="4e059-142">Bu, proje dosyanızda bu öğeleri artık belirtmeniz gerekolmadığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="4e059-142">This means that you no longer need to specify these items in your project file.</span></span>

<span data-ttu-id="4e059-143">Bunu yapmanın temel nedeni, proje dosyanızdaki dağınıklığı azaltmaktır.</span><span class="sxs-lookup"><span data-stu-id="4e059-143">The main reason for doing this is to reduce the clutter in your project file.</span></span> <span data-ttu-id="4e059-144">SDK'da bulunan varsayılanlar en yaygın kullanım durumlarını kapsamalıdır, bu nedenle oluşturduğunuz her projede bunları yinelemeye gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="4e059-144">The defaults that are present in the SDK should cover most common use cases, so there is no need to repeat them in every project that you create.</span></span> <span data-ttu-id="4e059-145">Bu, anlaşılması çok daha kolay olan ve gerekirse elle düzenleme yapan daha küçük proje dosyalarına yol açar.</span><span class="sxs-lookup"><span data-stu-id="4e059-145">This leads to smaller project files that are much easier to understand as well as edit by hand, if needed.</span></span>

<span data-ttu-id="4e059-146">Aşağıdaki tabloda, SDK'da hangi elementin ve hangi [globs'lerin](https://en.wikipedia.org/wiki/Glob_(programming)) dahil edildiği ve dışlandığı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="4e059-146">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are both included and excluded in the SDK:</span></span>

| <span data-ttu-id="4e059-147">Öğe</span><span class="sxs-lookup"><span data-stu-id="4e059-147">Element</span></span>           | <span data-ttu-id="4e059-148">Glob dahil et</span><span class="sxs-lookup"><span data-stu-id="4e059-148">Include glob</span></span>                              | <span data-ttu-id="4e059-149">Glob hariç</span><span class="sxs-lookup"><span data-stu-id="4e059-149">Exclude glob</span></span>                                                  | <span data-ttu-id="4e059-150">Glob'u çıkarın</span><span class="sxs-lookup"><span data-stu-id="4e059-150">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| <span data-ttu-id="4e059-151">Derlemek</span><span class="sxs-lookup"><span data-stu-id="4e059-151">Compile</span></span>           | <span data-ttu-id="4e059-152">\*\*/\*.cs (veya diğer dil uzantıları)</span><span class="sxs-lookup"><span data-stu-id="4e059-152">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="4e059-153">\*\*/\*.kullanıcı;  \*\*/\*. \*proj;  \* \* / \*  \* \* / \*</span><span class="sxs-lookup"><span data-stu-id="4e059-153">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="4e059-154">Yok</span><span class="sxs-lookup"><span data-stu-id="4e059-154">N/A</span></span>                      |
| <span data-ttu-id="4e059-155">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="4e059-155">EmbeddedResource</span></span>  | <span data-ttu-id="4e059-156">\*\*/\*Resx</span><span class="sxs-lookup"><span data-stu-id="4e059-156">\*\*/\*.resx</span></span>                              | <span data-ttu-id="4e059-157">\*\*/\*.kullanıcı; \*\*/\*. \*proj; \* \* / \* \* \* / \*</span><span class="sxs-lookup"><span data-stu-id="4e059-157">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="4e059-158">Yok</span><span class="sxs-lookup"><span data-stu-id="4e059-158">N/A</span></span>                      |
| <span data-ttu-id="4e059-159">None</span><span class="sxs-lookup"><span data-stu-id="4e059-159">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="4e059-160">\*\*/\*.kullanıcı; \*\*/\*. \*proj; \* \* / \* \* \* / \*</span><span class="sxs-lookup"><span data-stu-id="4e059-160">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="4e059-161">\*\*/\*.cs; \* \* /.resx \*</span><span class="sxs-lookup"><span data-stu-id="4e059-161">\*\*/\*.cs; \*\*/\*.resx</span></span>   |

> [!NOTE]
> <span data-ttu-id="4e059-162">**Dışlama glob** her `./bin` zaman `./obj` ve `$(BaseIntermediateOutputPath)` MSBuild özellikleri tarafından `$(BaseOutputPath)` temsil edilen klasörleri hariç tutar.</span><span class="sxs-lookup"><span data-stu-id="4e059-162">**Exclude glob** always excludes the `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, respectively.</span></span> <span data-ttu-id="4e059-163">Bir bütün olarak, tüm dışlar `$(DefaultItemExcludes)`tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="4e059-163">As a whole, all excludes are represented by `$(DefaultItemExcludes)`.</span></span>

<span data-ttu-id="4e059-164">Projenizde globs varsa ve en yeni SDK kullanarak inşa etmeye çalışırsanız, aşağıdaki hatayı alırsınız:</span><span class="sxs-lookup"><span data-stu-id="4e059-164">If you have globs in your project and you try to build it using the newest SDK, you'll get the following error:</span></span>

> <span data-ttu-id="4e059-165">Yinelenen Derleme öğeleri dahil edildi.</span><span class="sxs-lookup"><span data-stu-id="4e059-165">Duplicate Compile items were included.</span></span> <span data-ttu-id="4e059-166">.NET SDK varsayılan olarak proje dizininizdeki öğeleri derle içerir.</span><span class="sxs-lookup"><span data-stu-id="4e059-166">The .NET SDK includes Compile items from your project directory by default.</span></span> <span data-ttu-id="4e059-167">Bu öğeleri proje dosyanızdan kaldırabilir veya proje dosyanıza açıkça eklemek istiyorsanız 'Varsayılan Derleme Öğeleri' özelliğini 'false' olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e059-167">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

<span data-ttu-id="4e059-168">Bu hatayı aşmak için, önceki tabloda `Compile` listelenenöğelerle eşleşen açık öğeleri kaldırabilir veya `<EnableDefaultCompileItems>` özelliği `false`aşağıdaki gibi olarak ayarlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="4e059-168">In order to get around this error, you can either remove the explicit `Compile` items that match the ones listed on the previous table, or you can set the `<EnableDefaultCompileItems>` property to `false`, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

<span data-ttu-id="4e059-169">Bu özelliği, `false` projenizdeki varsayılan kümeleri belirtmeniz gereken önceki SDK'ların davranışına geri dönerek, örtülü eklemeyi devre dışı bırakacaktır.</span><span class="sxs-lookup"><span data-stu-id="4e059-169">Setting this property to `false` will disable implicit inclusion, reverting to the behavior of previous SDKs where you had to specify the default globs in your project.</span></span>

<span data-ttu-id="4e059-170">Bu değişiklik diğer içerir ana mekaniği değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="4e059-170">This change does not modify the main mechanics of other includes.</span></span> <span data-ttu-id="4e059-171">Ancak, örneğin, uygulamanızla birlikte yayımlanmak üzere bazı dosyaları belirtmek isterseniz, bunun için *csproj'da* bilinen mekanizmaları `<Content>` (örneğin, öğe) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e059-171">However, if you wish to specify, for example, some files to get published with your app, you can still use the known mechanisms in *csproj* for that (for example, the `<Content>` element).</span></span>

<span data-ttu-id="4e059-172">`<EnableDefaultCompileItems>`yalnızca `Compile` globs devre dışı kalır, ancak .cs öğeleri `None` için \*de geçerli olan örtük glob gibi diğer globs etkilemez.</span><span class="sxs-lookup"><span data-stu-id="4e059-172">`<EnableDefaultCompileItems>` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob, which also applies to \*.cs items.</span></span> <span data-ttu-id="4e059-173">Bu nedenle, Solution \*Explorer,.cs öğelerini projenin bir parçası `None` olarak, öğeler olarak göstermeye devam eder. **Solution Explorer**</span><span class="sxs-lookup"><span data-stu-id="4e059-173">Because of that, **Solution Explorer** will continue show \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="4e059-174">Benzer bir şekilde, örtük glob devre `<EnableDefaultNoneItems>` dışı `None` kalmak için yanlış ayarlayabilirsiniz, aşağıdaki gibi:</span><span class="sxs-lookup"><span data-stu-id="4e059-174">In a similar way, you can set `<EnableDefaultNoneItems>` to false to disable the implicit `None` glob, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

<span data-ttu-id="4e059-175">**Tüm örtük globs**devre dışı kalmak `<EnableDefaultItems>` için, aşağıdaki örnekte `false` olduğu gibi özelliği ayarlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="4e059-175">To disable **all implicit globs**, you can set the `<EnableDefaultItems>` property to `false` as in the following example:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a><span data-ttu-id="4e059-176">MSBuild'in gördüğü gibi tüm proje nasıl görebilirsiniz?</span><span class="sxs-lookup"><span data-stu-id="4e059-176">How to see the whole project as MSBuild sees it</span></span>

<span data-ttu-id="4e059-177">Bu csproj değişiklikleri büyük ölçüde proje dosyalarını basitleştirmek iken, MSBuild SDK ve hedefleri dahil edildikten sonra gördüğü gibi tamamen genişletilmiş proje görmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e059-177">While those csproj changes greatly simplify project files, you might want to see the fully expanded project as MSBuild sees it once the SDK and its targets are included.</span></span> <span data-ttu-id="4e059-178">Projeyi, hangi dosyaların içe [`dotnet msbuild`](dotnet-msbuild.md) aktarıldığı, kaynaklarını ve projeye gerçekten yapılmadan yapıya katkılarını gösteren komut [ `/pp` un geçişi](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) ile projeyi önceden işleme koymak:</span><span class="sxs-lookup"><span data-stu-id="4e059-178">Preprocess the project with [the `/pp` switch](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) of the [`dotnet msbuild`](dotnet-msbuild.md) command, which shows which files are imported, their sources, and their contributions to the build without actually building the project:</span></span>

`dotnet msbuild -pp:fullproject.xml`

<span data-ttu-id="4e059-179">Projenin birden çok hedef çerçevesi varsa, komutun sonuçları msbuild özelliği olarak belirtilerek bunlardan yalnızca birine odaklanmalıdır:</span><span class="sxs-lookup"><span data-stu-id="4e059-179">If the project has multiple target frameworks, the results of the command should be focused on only one of them by specifying it as an MSBuild property:</span></span>

`dotnet msbuild -p:TargetFramework=netcoreapp2.0 -pp:fullproject.xml`

## <a name="additions"></a><span data-ttu-id="4e059-180">Ekleme</span><span class="sxs-lookup"><span data-stu-id="4e059-180">Additions</span></span>

### <a name="sdk-attribute"></a><span data-ttu-id="4e059-181">Sdk özniteliği</span><span class="sxs-lookup"><span data-stu-id="4e059-181">Sdk attribute</span></span>

<span data-ttu-id="4e059-182">*.csproj* dosyasının kök `Sdk` `<Project>` öğesi, ..</span><span class="sxs-lookup"><span data-stu-id="4e059-182">The root `<Project>` element of the *.csproj* file has a new attribute called `Sdk`.</span></span> <span data-ttu-id="4e059-183">`Sdk`proje de hangi SDK'nın kullanılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4e059-183">`Sdk` specifies which SDK will be used by the project.</span></span> <span data-ttu-id="4e059-184">SDK, [katmanlama belgesinin](cli-msbuild-architecture.md) açıkladığı gibi, .NET Core kodu oluşturabilen bir MSBuild [görevleri](/visualstudio/msbuild/msbuild-tasks) ve [hedefleri](/visualstudio/msbuild/msbuild-targets) kümesidir.</span><span class="sxs-lookup"><span data-stu-id="4e059-184">The SDK, as the [layering document](cli-msbuild-architecture.md) describes, is a set of MSBuild [tasks](/visualstudio/msbuild/msbuild-tasks) and [targets](/visualstudio/msbuild/msbuild-targets) that can build .NET Core code.</span></span> <span data-ttu-id="4e059-185">.NET Core için aşağıdaki SDK'lar mevcuttur:</span><span class="sxs-lookup"><span data-stu-id="4e059-185">The following SDKs are available for .NET Core:</span></span>

1. <span data-ttu-id="4e059-186">.NET Çekirdek SDK kimliği ile`Microsoft.NET.Sdk`</span><span class="sxs-lookup"><span data-stu-id="4e059-186">The .NET Core SDK with the ID of `Microsoft.NET.Sdk`</span></span>
2. <span data-ttu-id="4e059-187">.NET Core web SDK kimliği ile`Microsoft.NET.Sdk.Web`</span><span class="sxs-lookup"><span data-stu-id="4e059-187">The .NET Core web SDK with the ID of `Microsoft.NET.Sdk.Web`</span></span>
3. <span data-ttu-id="4e059-188">.NET Core Razor Class Library SDK kimlikli`Microsoft.NET.Sdk.Razor`</span><span class="sxs-lookup"><span data-stu-id="4e059-188">The .NET Core Razor Class Library SDK with the ID of `Microsoft.NET.Sdk.Razor`</span></span>
4. <span data-ttu-id="4e059-189">.NET Çekirdek İşçi Servisi kimliği `Microsoft.NET.Sdk.Worker` ile (.NET Çekirdek 3.0 beri)</span><span class="sxs-lookup"><span data-stu-id="4e059-189">The .NET Core Worker Service with the ID of `Microsoft.NET.Sdk.Worker` (since .NET Core 3.0)</span></span>
5. <span data-ttu-id="4e059-190">.NET Core WinForms ve WPF `Microsoft.NET.Sdk.WindowsDesktop` kimliği ile (beri .NET Core 3.0)</span><span class="sxs-lookup"><span data-stu-id="4e059-190">The .NET Core WinForms and WPF with the ID of `Microsoft.NET.Sdk.WindowsDesktop` (since .NET Core 3.0)</span></span>

<span data-ttu-id="4e059-191">.NET Core `Sdk` araçlarını kullanmak ve kodunuzu oluşturmak için `<Project>` özniteliğin öğedeki kişilerden birine ayarlatması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4e059-191">You need to have the `Sdk` attribute set to one of those IDs on the `<Project>` element in order to use the .NET Core tools and build your code.</span></span>

### <a name="packagereference"></a><span data-ttu-id="4e059-192">PaketReferans</span><span class="sxs-lookup"><span data-stu-id="4e059-192">PackageReference</span></span>

<span data-ttu-id="4e059-193">Madde `<PackageReference>` öğesi projede bir [NuGet bağımlılığı](/nuget/consume-packages/package-references-in-project-files)belirtir.</span><span class="sxs-lookup"><span data-stu-id="4e059-193">A `<PackageReference>` item element specifies a [NuGet dependency in the project](/nuget/consume-packages/package-references-in-project-files).</span></span> <span data-ttu-id="4e059-194">Öznitelik `Include` paket kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4e059-194">The `Include` attribute specifies the package ID.</span></span>

```xml
<PackageReference Include="package-id" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a><span data-ttu-id="4e059-195">Sürüm</span><span class="sxs-lookup"><span data-stu-id="4e059-195">Version</span></span>

<span data-ttu-id="4e059-196">Gerekli `Version` öznitelik geri yüklemek için paketin sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="4e059-196">The required `Version` attribute specifies the version of the package to restore.</span></span> <span data-ttu-id="4e059-197">Öznitelik [NuGet sürüm](/nuget/reference/package-versioning#version-ranges-and-wildcards) şemasının kurallarına saygı duyar.</span><span class="sxs-lookup"><span data-stu-id="4e059-197">The attribute respects the rules of the [NuGet versioning](/nuget/reference/package-versioning#version-ranges-and-wildcards) scheme.</span></span> <span data-ttu-id="4e059-198">Varsayılan davranış en az sürüm, kapsayıcı maç.</span><span class="sxs-lookup"><span data-stu-id="4e059-198">The default behavior is a minimum version, inclusive match.</span></span> <span data-ttu-id="4e059-199">Örneğin, belirtme `Version="1.2.3"` NuGet gösterimine `[1.2.3, )` eşdeğerdir ve çözülen paketin varsa 1.2.3 sürümüne sahip olacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="4e059-199">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3, )` and means the resolved package will have the version 1.2.3 if available or greater otherwise.</span></span>

#### <a name="includeassets-excludeassets-and-privateassets"></a><span data-ttu-id="4e059-200">Varlıkları Dahil Et, Hariç Kıymetler ve Özel Varlıklar</span><span class="sxs-lookup"><span data-stu-id="4e059-200">IncludeAssets, ExcludeAssets, and PrivateAssets</span></span>

<span data-ttu-id="4e059-201">`IncludeAssets`öznitelik, belirtilen pakete ait varlıkların `<PackageReference>` hangilerinin tüketilmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4e059-201">`IncludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed.</span></span> <span data-ttu-id="4e059-202">Varsayılan olarak, tüm paket varlıkları dahildir.</span><span class="sxs-lookup"><span data-stu-id="4e059-202">By default, all package assets are included.</span></span>

<span data-ttu-id="4e059-203">`ExcludeAssets`öznitelik, belirtilen pakete ait varlıkların `<PackageReference>` tüketilmemesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4e059-203">`ExcludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should not be consumed.</span></span>

<span data-ttu-id="4e059-204">`PrivateAssets`öznitelik, belirtilen pakete ait varlıkların `<PackageReference>` tüketilmesi gerektiğini, ancak bir sonraki projeye akmaması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4e059-204">`PrivateAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed but not flow to the next project.</span></span> <span data-ttu-id="4e059-205">Bu `Analyzers` `Build` öznitelik olmadığında , ve `ContentFiles` varlıklar varsayılan olarak özeldir.</span><span class="sxs-lookup"><span data-stu-id="4e059-205">The `Analyzers`, `Build` and `ContentFiles` assets are private by default when this attribute is not present.</span></span>

> [!NOTE]
> <span data-ttu-id="4e059-206">`PrivateAssets`*project.json*/*xproj* `SuppressParent` elemanına eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="4e059-206">`PrivateAssets` is equivalent to the *project.json*/*xproj* `SuppressParent` element.</span></span>

<span data-ttu-id="4e059-207">Bu öznitelikler, birden fazla listelenmişse, yarı `;` sütunlu karakterle ayrılmış aşağıdaki öğelerden birini veya birkaçını içerebilir:</span><span class="sxs-lookup"><span data-stu-id="4e059-207">These attributes can contain one or more of the following items, separated by the semicolon `;` character if more than one is listed:</span></span>

- <span data-ttu-id="4e059-208">`Compile`– *lib* klasörünün içeriğini karşı derlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4e059-208">`Compile` – the contents of the *lib* folder are available to compile against.</span></span>
- <span data-ttu-id="4e059-209">`Runtime`– *çalışma zamanı* klasörünün içeriği dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="4e059-209">`Runtime` – the contents of the *runtime* folder are distributed.</span></span>
- <span data-ttu-id="4e059-210">`ContentFiles`– *contentfiles* klasörünün içeriği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4e059-210">`ContentFiles` – the contents of the *contentfiles* folder are used.</span></span>
- <span data-ttu-id="4e059-211">`Build`– *yapı* klasöründeki sahne/hedefler kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4e059-211">`Build` – the props/targets in the *build* folder are used.</span></span>
- <span data-ttu-id="4e059-212">`Native`– yerel varlıklardan gelen içerikler çalışma süresi için *çıktı* klasörüne kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="4e059-212">`Native` – the contents from native assets are copied to the *output* folder for runtime.</span></span>
- <span data-ttu-id="4e059-213">`Analyzers`– analizörler kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4e059-213">`Analyzers` – the analyzers are used.</span></span>

<span data-ttu-id="4e059-214">Alternatif olarak, öznitelik içerebilir:</span><span class="sxs-lookup"><span data-stu-id="4e059-214">Alternatively, the attribute can contain:</span></span>

- <span data-ttu-id="4e059-215">`None`– varlıkların hiçbiri kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="4e059-215">`None` – none of the assets are used.</span></span>
- <span data-ttu-id="4e059-216">`All`– tüm varlıklar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4e059-216">`All` – all assets are used.</span></span>

### <a name="dotnetclitoolreference"></a><span data-ttu-id="4e059-217">DotNetCliToolReference</span><span class="sxs-lookup"><span data-stu-id="4e059-217">DotNetCliToolReference</span></span>

<span data-ttu-id="4e059-218">Bir `<DotNetCliToolReference>` öğe öğesi, kullanıcının proje bağlamında geri yüklemek istediği CLI aracını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4e059-218">A `<DotNetCliToolReference>` item element specifies the CLI tool that the user wants to restore in the context of the project.</span></span> <span data-ttu-id="4e059-219">*Project.json'daki* `tools` düğümün yerine geçecek.</span><span class="sxs-lookup"><span data-stu-id="4e059-219">It's a replacement for the `tools` node in *project.json*.</span></span>

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

<span data-ttu-id="4e059-220">Artık `DotNetCliToolReference` [.NET Core Yerel Araçlar](https://aka.ms/local-tools)lehine [amortismana uymuyorum.](https://github.com/dotnet/announcements/issues/107)</span><span class="sxs-lookup"><span data-stu-id="4e059-220">Note that `DotNetCliToolReference` is [now deprecated](https://github.com/dotnet/announcements/issues/107) in favor of [.NET Core Local Tools](https://aka.ms/local-tools).</span></span>

#### <a name="version"></a><span data-ttu-id="4e059-221">Sürüm</span><span class="sxs-lookup"><span data-stu-id="4e059-221">Version</span></span>

<span data-ttu-id="4e059-222">`Version`geri yüklemek için paketin sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="4e059-222">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="4e059-223">Öznitelik [NuGet sürüm](/nuget/create-packages/dependency-versions#version-ranges) şemasının kurallarına saygı duyar.</span><span class="sxs-lookup"><span data-stu-id="4e059-223">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="4e059-224">Varsayılan davranış en az sürüm, kapsayıcı maç.</span><span class="sxs-lookup"><span data-stu-id="4e059-224">The default behavior is a minimum version, inclusive match.</span></span> <span data-ttu-id="4e059-225">Örneğin, belirtme `Version="1.2.3"` NuGet gösterimine `[1.2.3, )` eşdeğerdir ve çözülen paketin varsa 1.2.3 sürümüne sahip olacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="4e059-225">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3, )` and means the resolved package will have the version 1.2.3 if available or greater otherwise.</span></span>

### <a name="runtimeidentifiers"></a><span data-ttu-id="4e059-226">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="4e059-226">RuntimeIdentifiers</span></span>

<span data-ttu-id="4e059-227">Özellik `<RuntimeIdentifiers>` öğesi, proje için yarı sütunlu sınırlı bir [Runtime Tanımlayıcıları (RIDs)](../rid-catalog.md) listesini belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="4e059-227">The `<RuntimeIdentifiers>` property element lets you specify a semicolon-delimited list of [Runtime Identifiers (RIDs)](../rid-catalog.md) for the project.</span></span>
<span data-ttu-id="4e059-228">RI'ler, bağımsız dağıtımların yayımlanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e059-228">RIDs enable publishing self-contained deployments.</span></span>

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a><span data-ttu-id="4e059-229">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="4e059-229">RuntimeIdentifier</span></span>

<span data-ttu-id="4e059-230">Özellik `<RuntimeIdentifier>` öğesi, proje için yalnızca bir [Runtime Tanımlayıcı (RID)](../rid-catalog.md) belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="4e059-230">The `<RuntimeIdentifier>` property element allows you to specify only one [Runtime Identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="4e059-231">RID, bağımsız bir dağıtımyayımlanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e059-231">The RID enables publishing a self-contained deployment.</span></span>

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

<span data-ttu-id="4e059-232">Bunun `<RuntimeIdentifiers>` yerine birden çok çalışma süreleri için yayımlamanız gerekiyorsa (çoğul) kullanın.</span><span class="sxs-lookup"><span data-stu-id="4e059-232">Use `<RuntimeIdentifiers>` (plural) instead if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="4e059-233">`<RuntimeIdentifier>`yalnızca tek bir çalışma süresi gerektiğinde daha hızlı yapılar sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="4e059-233">`<RuntimeIdentifier>` can provide faster builds when only a single runtime is required.</span></span>

### <a name="packagetargetfallback"></a><span data-ttu-id="4e059-234">PaketTargetFallback</span><span class="sxs-lookup"><span data-stu-id="4e059-234">PackageTargetFallback</span></span>

<span data-ttu-id="4e059-235">Özellik `<PackageTargetFallback>` öğesi, paketleri geri verirken kullanılacak uyumlu hedefler kümesini belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="4e059-235">The `<PackageTargetFallback>` property element allows you to specify a set of compatible targets to be used when restoring packages.</span></span> <span data-ttu-id="4e059-236">Dotnet [TxM (Target x Moniker)](/nuget/schema/target-frameworks) kullanan paketlerin, dotnet TxM beyan etmeyen paketlerle çalışmasına izin vermek üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4e059-236">It's designed to allow packages that use the dotnet [TxM (Target x Moniker)](/nuget/schema/target-frameworks) to operate with packages that don't declare a dotnet TxM.</span></span> <span data-ttu-id="4e059-237">Projeniz dotnet TxM kullanıyorsa, dotnet olmayan platformların dotnet ile uyumlu olması `<PackageTargetFallback>` için projenize eklemediğiniz sürece, bağlı olduğu tüm paketlerin de bir dotnet TxM'si olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4e059-237">If your project uses the dotnet TxM, then all the packages it depends on must also have a dotnet TxM, unless you add the `<PackageTargetFallback>` to your project in order to allow non-dotnet platforms to be compatible with dotnet.</span></span>

<span data-ttu-id="4e059-238">Aşağıdaki örnek, projenizdeki tüm hedefler için geri dönüşler sağlar:</span><span class="sxs-lookup"><span data-stu-id="4e059-238">The following example provides the fallbacks for all targets in your project:</span></span>

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

<span data-ttu-id="4e059-239">Aşağıdaki örnekte yalnızca `netcoreapp2.1` hedef için geri dönüşler belirtilir:</span><span class="sxs-lookup"><span data-stu-id="4e059-239">The following example specifies the fallbacks only for the `netcoreapp2.1` target:</span></span>

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp2.1'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="build-events"></a><span data-ttu-id="4e059-240">Etkinlikler oluşturma</span><span class="sxs-lookup"><span data-stu-id="4e059-240">Build events</span></span>

<span data-ttu-id="4e059-241">Proje dosyasında ön yapı ve yapı sonrası olayların belirtilme şekli değişti.</span><span class="sxs-lookup"><span data-stu-id="4e059-241">The way that pre-build and post-build events are specified in the project file has changed.</span></span> <span data-ttu-id="4e059-242">$(ProjectDir) gibi makrolar çözülmediği için PreBuildEvent ve PostBuildEvent özellikleri SDK stili proje biçiminde önerilmez.</span><span class="sxs-lookup"><span data-stu-id="4e059-242">The properties PreBuildEvent and PostBuildEvent are not recommended in the SDK-style project format, because macros such as $(ProjectDir) are not resolved.</span></span> <span data-ttu-id="4e059-243">Örneğin, aşağıdaki kod artık desteklenmez:</span><span class="sxs-lookup"><span data-stu-id="4e059-243">For example, the following code is no longer supported:</span></span>

```xml
<PropertyGroup>
    <PreBuildEvent>"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)"</PreBuildEvent>
</PropertyGroup>
```

<span data-ttu-id="4e059-244">SDK tarzı projelerde, `PreBuild` adı verilen bir `PostBuild` MSBuild `BeforeTargets` hedefi `PreBuild` kullanın `AfterTargets` veya `PostBuild`özelliği için veya mülkü .</span><span class="sxs-lookup"><span data-stu-id="4e059-244">In SDK-style projects, use an MSBuild target named `PreBuild` or `PostBuild` and set the `BeforeTargets` property for `PreBuild` or the `AfterTargets` property for `PostBuild`.</span></span> <span data-ttu-id="4e059-245">Önceki örnek için aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="4e059-245">For the preceding example, use the following code:</span></span>

```xml
<Target Name="PreBuild" BeforeTargets="PreBuildEvent">
    <Exec Command="&quot;$(ProjectDir)PreBuildEvent.bat&quot; &quot;$(ProjectDir)..\&quot; &quot;$(ProjectDir)&quot; &quot;$(TargetDir)&quot;" />
</Target>

<Target Name="PostBuild" AfterTargets="PostBuildEvent">
   <Exec Command="echo Output written to $(TargetDir)" />
</Target>
```

> [!NOTE]
><span data-ttu-id="4e059-246">MSBuild hedefleri için herhangi bir ad kullanabilirsiniz, ancak `PreBuild` Visual `PostBuild` Studio IDE tanır ve hedefler, bu nedenle Visual Studio IDE komutları edebilirsiniz böylece bu adları kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="4e059-246">You can use any name for the MSBuild targets, but the Visual Studio IDE recognizes `PreBuild` and `PostBuild` targets, so we recommend using those names so that you can edit the commands in the Visual Studio IDE.</span></span>

## <a name="nuget-metadata-properties"></a><span data-ttu-id="4e059-247">NuMeta veri özelliklerini alın</span><span class="sxs-lookup"><span data-stu-id="4e059-247">NuGet metadata properties</span></span>

<span data-ttu-id="4e059-248">MSBuild'e geçildiğinde, bir NuGet paketini *project.json'dan* *.csproj* dosyalarına paketlerken kullanılan giriş meta verilerini taşıdık.</span><span class="sxs-lookup"><span data-stu-id="4e059-248">With the move to MSBuild, we have moved the input metadata that is used when packing a NuGet package from *project.json* to *.csproj* files.</span></span> <span data-ttu-id="4e059-249">Girişler MSBuild özellikleridir, bu nedenle `<PropertyGroup>` bir grup içinde gitmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="4e059-249">The inputs are MSBuild properties so they have to go within a `<PropertyGroup>` group.</span></span> <span data-ttu-id="4e059-250">SDK'nın bir parçası olan `dotnet pack` komutu veya `Pack` MSBuild hedefini kullanırken paketleme işlemine girdi olarak kullanılan özelliklerin listesi aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="4e059-250">The following is the list of properties that are used as inputs to the packing process when using the `dotnet pack` command or the `Pack` MSBuild target that is part of the SDK:</span></span>

### <a name="ispackable"></a><span data-ttu-id="4e059-251">IsPackable</span><span class="sxs-lookup"><span data-stu-id="4e059-251">IsPackable</span></span>

<span data-ttu-id="4e059-252">Projenin paketlenip paketlenemeyeceğini belirten bir Boolean değeri.</span><span class="sxs-lookup"><span data-stu-id="4e059-252">A Boolean value that specifies whether the project can be packed.</span></span> <span data-ttu-id="4e059-253">Varsayılan değer: `true`.</span><span class="sxs-lookup"><span data-stu-id="4e059-253">The default value is `true`.</span></span>

### <a name="packageversion"></a><span data-ttu-id="4e059-254">PaketSürüm</span><span class="sxs-lookup"><span data-stu-id="4e059-254">PackageVersion</span></span>

<span data-ttu-id="4e059-255">Ortaya çıkan paketin sahip olacağı sürümü belirtir.</span><span class="sxs-lookup"><span data-stu-id="4e059-255">Specifies the version that the resulting package will have.</span></span> <span data-ttu-id="4e059-256">NuGet sürüm dizesinin tüm biçimlerini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="4e059-256">Accepts all forms of NuGet version string.</span></span> <span data-ttu-id="4e059-257">Varsayılan değer, `$(Version)`projedeki özelliğin `Version` değeridir.</span><span class="sxs-lookup"><span data-stu-id="4e059-257">Default is the value of `$(Version)`, that is, of the property `Version` in the project.</span></span>

### <a name="packageid"></a><span data-ttu-id="4e059-258">Packageıd</span><span class="sxs-lookup"><span data-stu-id="4e059-258">PackageId</span></span>

<span data-ttu-id="4e059-259">Ortaya çıkan paketin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4e059-259">Specifies the name for the resulting package.</span></span> <span data-ttu-id="4e059-260">Belirtilmemişse, `pack` işlem varsayılan olarak `AssemblyName` paketin adı olarak dizin adını kullanır.</span><span class="sxs-lookup"><span data-stu-id="4e059-260">If not specified, the `pack` operation will default to using the `AssemblyName` or directory name as the name of the package.</span></span>

### <a name="title"></a><span data-ttu-id="4e059-261">Başlık</span><span class="sxs-lookup"><span data-stu-id="4e059-261">Title</span></span>

<span data-ttu-id="4e059-262">Paketin insan dostu bir başlık, genellikle nuget.org ve Visual Studio Paket Yöneticisi olarak uI görüntüler kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4e059-262">A human-friendly title of the package, typically used in UI displays as on nuget.org and the Package Manager in Visual Studio.</span></span> <span data-ttu-id="4e059-263">Belirtilmemişse, bunun yerine paket kimliği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4e059-263">If not specified, the package ID is used instead.</span></span>

### <a name="authors"></a><span data-ttu-id="4e059-264">Yazarlar</span><span class="sxs-lookup"><span data-stu-id="4e059-264">Authors</span></span>

<span data-ttu-id="4e059-265">nuget.org'daki profil adlarıyla eşleşen, yarı sütunlu paket yazarlarılistesi. Bunlar nuget.org'daki NuGet Galerisi'nde görüntülenir ve aynı yazarlar tarafından çapraz başvuru paketleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4e059-265">A semicolon-separated list of packages authors, matching the profile names on nuget.org. These are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span>

### <a name="packagedescription"></a><span data-ttu-id="4e059-266">Packagedescription</span><span class="sxs-lookup"><span data-stu-id="4e059-266">PackageDescription</span></span>

<span data-ttu-id="4e059-267">UI ekran için paketin uzun bir açıklaması.</span><span class="sxs-lookup"><span data-stu-id="4e059-267">A long description of the package for UI display.</span></span>

### <a name="description"></a><span data-ttu-id="4e059-268">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4e059-268">Description</span></span>

<span data-ttu-id="4e059-269">Montaj için uzun bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="4e059-269">A long description for the assembly.</span></span> <span data-ttu-id="4e059-270">`PackageDescription` Belirtilmemişse, bu özellik paketin açıklaması olarak da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4e059-270">If `PackageDescription` is not specified, then this property is also used as the description of the package.</span></span>

### <a name="copyright"></a><span data-ttu-id="4e059-271">Telif Hakkı</span><span class="sxs-lookup"><span data-stu-id="4e059-271">Copyright</span></span>

<span data-ttu-id="4e059-272">Paketin telif hakkı ayrıntıları.</span><span class="sxs-lookup"><span data-stu-id="4e059-272">Copyright details for the package.</span></span>

### <a name="packagerequirelicenseacceptance"></a><span data-ttu-id="4e059-273">Paket GerektirirLisans Kabul</span><span class="sxs-lookup"><span data-stu-id="4e059-273">PackageRequireLicenseAcceptance</span></span>

<span data-ttu-id="4e059-274">Müşterinin paketi yüklemeden önce tüketiciden paket lisansını kabul etmesini isteyip istemeyeceğini belirten bir Boolean değeri.</span><span class="sxs-lookup"><span data-stu-id="4e059-274">A Boolean value that specifies whether the client must prompt the consumer to accept the package license before installing the package.</span></span> <span data-ttu-id="4e059-275">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="4e059-275">The default is `false`.</span></span>

### <a name="developmentdependency"></a><span data-ttu-id="4e059-276">GeliştirmeBağımlılık</span><span class="sxs-lookup"><span data-stu-id="4e059-276">DevelopmentDependency</span></span>

<span data-ttu-id="4e059-277">Paketin yalnızca geliştirme bağımlılığı olarak işaretlenip işaretlenmediğini belirten ve paketin diğer paketlere bağımlılık olarak dahil olmasını engelleyen Boolean değeri.</span><span class="sxs-lookup"><span data-stu-id="4e059-277">A Boolean value that specifies whether the package is marked as a development-only dependency, which prevents the package from being included as a dependency in other packages.</span></span> <span data-ttu-id="4e059-278">PackageReference (NuGet 4.8+) ile bu bayrak, derleme zamanı varlıklarının derlemenin dışında olduğu anlamına da gelir.</span><span class="sxs-lookup"><span data-stu-id="4e059-278">With PackageReference (NuGet 4.8+), this flag also means that compile-time assets are excluded from compilation.</span></span> <span data-ttu-id="4e059-279">Daha fazla bilgi [için PackageReference için DevelopmentDependency desteğine](https://github.com/NuGet/Home/wiki/DevelopmentDependency-support-for-PackageReference)bakın.</span><span class="sxs-lookup"><span data-stu-id="4e059-279">For more information, see [DevelopmentDependency support for PackageReference](https://github.com/NuGet/Home/wiki/DevelopmentDependency-support-for-PackageReference).</span></span>

### <a name="packagelicenseexpression"></a><span data-ttu-id="4e059-280">PaketLisans İfadesi</span><span class="sxs-lookup"><span data-stu-id="4e059-280">PackageLicenseExpression</span></span>

<span data-ttu-id="4e059-281">[SPDX lisans tanımlayıcısı](https://spdx.org/licenses/) veya ifadesi.</span><span class="sxs-lookup"><span data-stu-id="4e059-281">An [SPDX license identifier](https://spdx.org/licenses/) or expression.</span></span> <span data-ttu-id="4e059-282">Örneğin, `Apache-2.0`.</span><span class="sxs-lookup"><span data-stu-id="4e059-282">For example, `Apache-2.0`.</span></span>

<span data-ttu-id="4e059-283">İşte [SPDX lisans tanımlayıcılarının](https://spdx.org/licenses/)tam listesi.</span><span class="sxs-lookup"><span data-stu-id="4e059-283">Here is the complete list of [SPDX license identifiers](https://spdx.org/licenses/).</span></span> <span data-ttu-id="4e059-284">NuGet.org, lisans türü ifadesini kullanırken yalnızca OSI veya FSF onaylı lisansları kabul eder.</span><span class="sxs-lookup"><span data-stu-id="4e059-284">NuGet.org accepts only OSI or FSF approved licenses when using license type expression.</span></span>

<span data-ttu-id="4e059-285">Lisans ifadelerinin tam sözdizimi [ABNF'de](https://tools.ietf.org/html/rfc5234)aşağıda açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4e059-285">The exact syntax of the license expressions is described below in [ABNF](https://tools.ietf.org/html/rfc5234).</span></span>

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
> <span data-ttu-id="4e059-286">Yalnızca biri `PackageLicenseExpression` `PackageLicenseFile` , `PackageLicenseUrl` ve bir seferde belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="4e059-286">Only one of `PackageLicenseExpression`, `PackageLicenseFile` and `PackageLicenseUrl` can be specified at a time.</span></span>

### <a name="packagelicensefile"></a><span data-ttu-id="4e059-287">PaketLisans Dosyası</span><span class="sxs-lookup"><span data-stu-id="4e059-287">PackageLicenseFile</span></span>

<span data-ttu-id="4e059-288">SPDX tanımlayıcısı atanmamış bir lisans kullanıyorsanız veya özel bir lisanssa (Aksi takdirde `PackageLicenseExpression` tercih edilir)</span><span class="sxs-lookup"><span data-stu-id="4e059-288">Path to a license file within the package if you are using a license that hasn’t been assigned an SPDX identifier, or it is a custom license (Otherwise `PackageLicenseExpression` is preferred)</span></span>

<span data-ttu-id="4e059-289">Yerine `PackageLicenseUrl`, ile `PackageLicenseExpression`kombine edilemez , ve Visual Studio sürümü 15.9.4 ve .NET SDK 2.1.502 veya 2.2.101 veya daha yeni gerektirir.</span><span class="sxs-lookup"><span data-stu-id="4e059-289">Replaces `PackageLicenseUrl`, can't be combined with `PackageLicenseExpression`, and requires Visual Studio version 15.9.4 and .NET SDK 2.1.502 or 2.2.101 or newer.</span></span>

<span data-ttu-id="4e059-290">Lisans dosyasının projeye, örnek kullanıma açıkça ekleyerek paketlendirdiğinden emin olmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="4e059-290">You will need to ensure the license file is packed by adding it explicitly to the project, example usage:</span></span>

```xml
<PropertyGroup>
  <PackageLicenseFile>LICENSE.txt</PackageLicenseFile>
</PropertyGroup>
<ItemGroup>
  <None Include="licenses\LICENSE.txt" Pack="true" PackagePath="$(PackageLicenseFile)"/>
</ItemGroup>
```

### <a name="packagelicenseurl"></a><span data-ttu-id="4e059-291">PaketLisansUrl</span><span class="sxs-lookup"><span data-stu-id="4e059-291">PackageLicenseUrl</span></span>

<span data-ttu-id="4e059-292">Paket için geçerli olan lisansın URL'si.</span><span class="sxs-lookup"><span data-stu-id="4e059-292">A URL to the license that is applicable to the package.</span></span> <span data-ttu-id="4e059-293">(_Visual Studio 15.9.4, .NET SDK 2.1.502 ve 2.2.101' den itibaren amortismana uymuyet_)</span><span class="sxs-lookup"><span data-stu-id="4e059-293">(_deprecated since Visual Studio 15.9.4, .NET SDK 2.1.502 and 2.2.101_)</span></span>

### <a name="packageiconurl"></a><span data-ttu-id="4e059-294">PaketIconUrl</span><span class="sxs-lookup"><span data-stu-id="4e059-294">PackageIconUrl</span></span>

<span data-ttu-id="4e059-295">Kullanıcı Arabirimi ekranında paket simgesi olarak kullanılacak saydam arka plana sahip 64x64 görüntünün URL'si.</span><span class="sxs-lookup"><span data-stu-id="4e059-295">A URL for a 64x64 image with transparent background to use as the icon for the package in UI display.</span></span>

### <a name="packagereleasenotes"></a><span data-ttu-id="4e059-296">PaketYayın Notları</span><span class="sxs-lookup"><span data-stu-id="4e059-296">PackageReleaseNotes</span></span>

<span data-ttu-id="4e059-297">Paket için notları bırakın.</span><span class="sxs-lookup"><span data-stu-id="4e059-297">Release notes for the package.</span></span>

### <a name="packagetags"></a><span data-ttu-id="4e059-298">Paket Etiketler</span><span class="sxs-lookup"><span data-stu-id="4e059-298">PackageTags</span></span>

<span data-ttu-id="4e059-299">Paketi belirleyen yarı sütunlu etiket listesi.</span><span class="sxs-lookup"><span data-stu-id="4e059-299">A semicolon-delimited list of tags that designates the package.</span></span>

### <a name="packageoutputpath"></a><span data-ttu-id="4e059-300">PackageOutputPath</span><span class="sxs-lookup"><span data-stu-id="4e059-300">PackageOutputPath</span></span>

<span data-ttu-id="4e059-301">Paketlenmiş paketin bırakılalı çıkış yolunu belirler.</span><span class="sxs-lookup"><span data-stu-id="4e059-301">Determines the output path in which the packed package will be dropped.</span></span> <span data-ttu-id="4e059-302">`$(OutputPath)` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="4e059-302">Default is `$(OutputPath)`.</span></span>

### <a name="includesymbols"></a><span data-ttu-id="4e059-303">Sembolleri Dahil Et</span><span class="sxs-lookup"><span data-stu-id="4e059-303">IncludeSymbols</span></span>
<span data-ttu-id="4e059-304">Bu Boolean değeri, proje paketlendiğinde paketin ek bir sembol paketi oluşturup oluşturmaması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4e059-304">This Boolean value indicates whether the package should create an additional symbols package when the project is packed.</span></span> <span data-ttu-id="4e059-305">Semboller paketinin biçimi `SymbolPackageFormat` özellik tarafından denetlenir.</span><span class="sxs-lookup"><span data-stu-id="4e059-305">The symbols package's format is controlled by the `SymbolPackageFormat` property.</span></span>

### <a name="symbolpackageformat"></a><span data-ttu-id="4e059-306">SymbolPackageFormat</span><span class="sxs-lookup"><span data-stu-id="4e059-306">SymbolPackageFormat</span></span>
<span data-ttu-id="4e059-307">Semboller paketinin biçimini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4e059-307">Specifies the format of the symbols package.</span></span> <span data-ttu-id="4e059-308">"symbols.nupkg" ise, PDB'ler, LL'ler ve diğer çıktı dosyalarını içeren bir *.symbols.nupkg* uzantısı içeren eski semboller paketi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4e059-308">If "symbols.nupkg", a legacy symbols package will be created with a *.symbols.nupkg* extension containing PDBs, DLLs, and other output files.</span></span> <span data-ttu-id="4e059-309">"Snupkg" ise, taşınabilir PDB'leri içeren bir snupkg sembol paketi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4e059-309">If "snupkg", a snupkg symbol package will be created containing the portable PDBs.</span></span> <span data-ttu-id="4e059-310">Varsayılan "symbols.nupkg"dır.</span><span class="sxs-lookup"><span data-stu-id="4e059-310">Default is "symbols.nupkg".</span></span>

### <a name="includesource"></a><span data-ttu-id="4e059-311">IncludeSource</span><span class="sxs-lookup"><span data-stu-id="4e059-311">IncludeSource</span></span>

<span data-ttu-id="4e059-312">Bu Boolean değeri, paket işleminin bir kaynak paketi oluşturup oluşturmaması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4e059-312">This Boolean value indicates whether the pack process should create a source package.</span></span> <span data-ttu-id="4e059-313">Kaynak paketi, kitaplığın kaynak kodunun yanı sıra PDB dosyalarını da içerir.</span><span class="sxs-lookup"><span data-stu-id="4e059-313">The source package contains the library's source code as well as PDB files.</span></span> <span data-ttu-id="4e059-314">Kaynak dosyalar, ortaya `src/ProjectName` çıkan paket dosyasında dizinin altına konur.</span><span class="sxs-lookup"><span data-stu-id="4e059-314">Source files are put under the `src/ProjectName` directory in the resulting package file.</span></span>

### <a name="istool"></a><span data-ttu-id="4e059-315">ıstool</span><span class="sxs-lookup"><span data-stu-id="4e059-315">IsTool</span></span>

<span data-ttu-id="4e059-316">Tüm çıktı dosyalarının *lib* klasörü yerine *araçlar* klasörüne kopyalanıp kopyalanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4e059-316">Specifies whether all output files are copied to the *tools* folder instead of the *lib* folder.</span></span> <span data-ttu-id="4e059-317">Bu, `DotNetCliTool` *.csproj* `PackageType` dosyasında ayarlayarak belirtilen bir ,'dan farklıdır.</span><span class="sxs-lookup"><span data-stu-id="4e059-317">This is different from a `DotNetCliTool`, which is specified by setting the `PackageType` in the *.csproj* file.</span></span>

### <a name="repositoryurl"></a><span data-ttu-id="4e059-318">DepoUrl</span><span class="sxs-lookup"><span data-stu-id="4e059-318">RepositoryUrl</span></span>

<span data-ttu-id="4e059-319">Paketin kaynak kodunun bulunduğu ve/veya oluşturulmakta olduğu deponun URL'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4e059-319">Specifies the URL for the repository where the source code for the package resides and/or from which it's being built.</span></span>

### <a name="repositorytype"></a><span data-ttu-id="4e059-320">DepoTipi</span><span class="sxs-lookup"><span data-stu-id="4e059-320">RepositoryType</span></span>

<span data-ttu-id="4e059-321">Deponun türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="4e059-321">Specifies the type of the repository.</span></span> <span data-ttu-id="4e059-322">Varsayılan "git" dir.</span><span class="sxs-lookup"><span data-stu-id="4e059-322">Default is "git".</span></span>

### <a name="repositorybranch"></a><span data-ttu-id="4e059-323">DepoŞubesi</span><span class="sxs-lookup"><span data-stu-id="4e059-323">RepositoryBranch</span></span>
<span data-ttu-id="4e059-324">Depodaki kaynak dalanın adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4e059-324">Specifies the name of the source branch in the repository.</span></span> <span data-ttu-id="4e059-325">Proje bir NuGet paketinde paketlendiğinde, paket meta verilerine eklenir.</span><span class="sxs-lookup"><span data-stu-id="4e059-325">When the project is packaged in a NuGet package, it's added to the package metadata.</span></span>

### <a name="repositorycommit"></a><span data-ttu-id="4e059-326">DepoCommit</span><span class="sxs-lookup"><span data-stu-id="4e059-326">RepositoryCommit</span></span>
<span data-ttu-id="4e059-327">İsteğe bağlı depo, paketin hangi kaynağa karşı üretilmediğini belirtmek için işlemeyi veya değiştirin.</span><span class="sxs-lookup"><span data-stu-id="4e059-327">Optional repository commit or changeset to indicate which source the package was built against.</span></span> <span data-ttu-id="4e059-328">`RepositoryUrl`ayrıca bu özelliğin dahil edilmesi için belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="4e059-328">`RepositoryUrl` must also be specified for this property to be included.</span></span> <span data-ttu-id="4e059-329">Proje bir NuGet paketinde paketlendiğinde, bu commit veya changeset paket meta verilerine eklenir.</span><span class="sxs-lookup"><span data-stu-id="4e059-329">When the project is packaged in a NuGet package, this commit or changeset is added to the package metadata.</span></span>

### <a name="nopackageanalysis"></a><span data-ttu-id="4e059-330">NoPackageAnalysis</span><span class="sxs-lookup"><span data-stu-id="4e059-330">NoPackageAnalysis</span></span>

<span data-ttu-id="4e059-331">Bu paket, paketi yaptıktan sonra paket çözümlemesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4e059-331">Specifies that pack should not run package analysis after building the package.</span></span>

### <a name="minclientversion"></a><span data-ttu-id="4e059-332">MinClientVersion</span><span class="sxs-lookup"><span data-stu-id="4e059-332">MinClientVersion</span></span>

<span data-ttu-id="4e059-333">Nuget istemcisinin nuget.exe ve Visual Studio Package Manager tarafından uygulanan bu paketi yükleyebilecek minimum sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="4e059-333">Specifies the minimum version of the NuGet client that can install this package, enforced by nuget.exe and the Visual Studio Package Manager.</span></span>

### <a name="includebuildoutput"></a><span data-ttu-id="4e059-334">IncludeBuildOutput</span><span class="sxs-lookup"><span data-stu-id="4e059-334">IncludeBuildOutput</span></span>

<span data-ttu-id="4e059-335">Bu Boolean değeri, yapı çıktı derlemelerinin *.nupkg* dosyasına paketlenip paketlenmemesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4e059-335">This Boolean value specifies whether the build output assemblies should be packed into the *.nupkg* file or not.</span></span>

### <a name="includecontentinpack"></a><span data-ttu-id="4e059-336">IncludeContentInPack</span><span class="sxs-lookup"><span data-stu-id="4e059-336">IncludeContentInPack</span></span>

<span data-ttu-id="4e059-337">Bu Boolean değeri, türü olan öğelerin `Content` otomatik olarak ortaya çıkan pakete dahil edilip edilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4e059-337">This Boolean value specifies whether any items that have a type of `Content` will be included in the resulting package automatically.</span></span> <span data-ttu-id="4e059-338">Varsayılan değer: `true`.</span><span class="sxs-lookup"><span data-stu-id="4e059-338">The default is `true`.</span></span>

### <a name="buildoutputtargetfolder"></a><span data-ttu-id="4e059-339">YapıÇıktıHedef Klasörü</span><span class="sxs-lookup"><span data-stu-id="4e059-339">BuildOutputTargetFolder</span></span>

<span data-ttu-id="4e059-340">Çıktı derlemelerinin yerleştirilen klasörü belirtir.</span><span class="sxs-lookup"><span data-stu-id="4e059-340">Specifies the folder where to place the output assemblies.</span></span> <span data-ttu-id="4e059-341">Çıktı derlemeleri (ve diğer çıktı dosyaları) kendi çerçeve klasörlerine kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="4e059-341">The output assemblies (and other output files) are copied into their respective framework folders.</span></span>

### <a name="contenttargetfolders"></a><span data-ttu-id="4e059-342">İçerikHedef Klasörler</span><span class="sxs-lookup"><span data-stu-id="4e059-342">ContentTargetFolders</span></span>

<span data-ttu-id="4e059-343">Bu özellik, onlar için belirtilmemişse `PackagePath` tüm içerik dosyalarının gitmesi gereken varsayılan konumu belirtir.</span><span class="sxs-lookup"><span data-stu-id="4e059-343">This property specifies the default location of where all the content files should go if `PackagePath` is not specified for them.</span></span> <span data-ttu-id="4e059-344">Varsayılan değer "içerik;contentFiles"dır.</span><span class="sxs-lookup"><span data-stu-id="4e059-344">The default value is "content;contentFiles".</span></span>

### <a name="nuspecfile"></a><span data-ttu-id="4e059-345">NuspecDosya</span><span class="sxs-lookup"><span data-stu-id="4e059-345">NuspecFile</span></span>

<span data-ttu-id="4e059-346">Paketleme için kullanılan *.nuspec* dosyasına göreli veya mutlak yol.</span><span class="sxs-lookup"><span data-stu-id="4e059-346">Relative or absolute path to the *.nuspec* file being used for packing.</span></span>

> [!NOTE]
> <span data-ttu-id="4e059-347">*.nuspec* dosyası belirtilirse, **yalnızca** ambalaj bilgileri için kullanılır ve projelerdeki herhangi bir bilgi kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="4e059-347">If the *.nuspec* file is specified, it's used **exclusively** for packaging information and any information in the projects is not used.</span></span>

### <a name="nuspecbasepath"></a><span data-ttu-id="4e059-348">NuspecBasePath</span><span class="sxs-lookup"><span data-stu-id="4e059-348">NuspecBasePath</span></span>

<span data-ttu-id="4e059-349">*.nuspec* dosyası için temel yol.</span><span class="sxs-lookup"><span data-stu-id="4e059-349">Base path for the *.nuspec* file.</span></span>

### <a name="nuspecproperties"></a><span data-ttu-id="4e059-350">NuspecÖzellikleri</span><span class="sxs-lookup"><span data-stu-id="4e059-350">NuspecProperties</span></span>

<span data-ttu-id="4e059-351">Anahtar=değer çiftleri semicolon ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="4e059-351">Semicolon separated list of key=value pairs.</span></span>

## <a name="assemblyinfo-properties"></a><span data-ttu-id="4e059-352">AssemblyInfo özellikleri</span><span class="sxs-lookup"><span data-stu-id="4e059-352">AssemblyInfo properties</span></span>

<span data-ttu-id="4e059-353">Genellikle bir *AssemblyInfo* dosyasında bulunan [derleme öznitelikleri](../../standard/assembly/set-attributes.md) artık otomatik olarak özelliklerden oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4e059-353">[Assembly attributes](../../standard/assembly/set-attributes.md) that were typically present in an *AssemblyInfo* file are now automatically generated from properties.</span></span>

### <a name="properties-per-attribute"></a><span data-ttu-id="4e059-354">Öznitelik başına özellikler</span><span class="sxs-lookup"><span data-stu-id="4e059-354">Properties per attribute</span></span>

<span data-ttu-id="4e059-355">Aşağıdaki tabloda gösterildiği gibi, her öznitelik kendi içeriğini denetleyen bir özelliğe ve kendi kuşağını devre dışı devre dışı bir başkasına sahiptir:</span><span class="sxs-lookup"><span data-stu-id="4e059-355">As shown in the following table, each attribute has a property that controls its content and another that disables its generation:</span></span>

| <span data-ttu-id="4e059-356">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4e059-356">Attribute</span></span>                                                      | <span data-ttu-id="4e059-357">Özellik</span><span class="sxs-lookup"><span data-stu-id="4e059-357">Property</span></span>               | <span data-ttu-id="4e059-358">Devre dışı kalım özelliği</span><span class="sxs-lookup"><span data-stu-id="4e059-358">Property to disable</span></span>                             |
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

<span data-ttu-id="4e059-359">Notlar:</span><span class="sxs-lookup"><span data-stu-id="4e059-359">Notes:</span></span>

- <span data-ttu-id="4e059-360">`AssemblyVersion`ve `FileVersion` varsayılan sonek `$(Version)` olmadan değerini almaktır.</span><span class="sxs-lookup"><span data-stu-id="4e059-360">`AssemblyVersion` and `FileVersion` default is to take the value of `$(Version)` without suffix.</span></span> <span data-ttu-id="4e059-361">Örneğin, `$(Version)` ise, `1.2.3-beta.4`o zaman değeri `1.2.3`olacaktır.</span><span class="sxs-lookup"><span data-stu-id="4e059-361">For example, if `$(Version)` is `1.2.3-beta.4`, then the value would be `1.2.3`.</span></span>
- <span data-ttu-id="4e059-362">`InformationalVersion`değeri `$(Version)`varsayılan.</span><span class="sxs-lookup"><span data-stu-id="4e059-362">`InformationalVersion` defaults to the value of `$(Version)`.</span></span>
- <span data-ttu-id="4e059-363">`InformationalVersion`özellik `$(SourceRevisionId)` varsa eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="4e059-363">`InformationalVersion` has `$(SourceRevisionId)` appended if the property is present.</span></span> <span data-ttu-id="4e059-364">Bu kullanarak `IncludeSourceRevisionInInformationalVersion`devre dışı tutulabilir.</span><span class="sxs-lookup"><span data-stu-id="4e059-364">It can be disabled using `IncludeSourceRevisionInInformationalVersion`.</span></span>
- <span data-ttu-id="4e059-365">`Copyright`ve `Description` özellikleri nuget meta verileri için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4e059-365">`Copyright` and `Description` properties are also used for NuGet metadata.</span></span>
- <span data-ttu-id="4e059-366">`Configuration`tüm yapı işlemi ile paylaşılır `--configuration` ve `dotnet` komutların parametresi üzerinden ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="4e059-366">`Configuration` is shared with all the build process and set via the `--configuration` parameter of `dotnet` commands.</span></span>

### <a name="generateassemblyinfo"></a><span data-ttu-id="4e059-367">AssemblyInfo oluşturma</span><span class="sxs-lookup"><span data-stu-id="4e059-367">GenerateAssemblyInfo</span></span>

<span data-ttu-id="4e059-368">Tüm AssemblyInfo neslini etkinleştiren veya devre dışı eden bir Boolean.</span><span class="sxs-lookup"><span data-stu-id="4e059-368">A Boolean that enable or disable all the AssemblyInfo generation.</span></span> <span data-ttu-id="4e059-369">Varsayılan değer: `true`.</span><span class="sxs-lookup"><span data-stu-id="4e059-369">The default value is `true`.</span></span>

### <a name="generatedassemblyinfofile"></a><span data-ttu-id="4e059-370">OluşturulanAssemblyInfoFile</span><span class="sxs-lookup"><span data-stu-id="4e059-370">GeneratedAssemblyInfoFile</span></span>

<span data-ttu-id="4e059-371">Oluşturulan derleme bilgi dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="4e059-371">The path of the generated assembly info file.</span></span> <span data-ttu-id="4e059-372">`$(IntermediateOutputPath)` Varsayılan olarak (obj) dizinindeki bir dosya.</span><span class="sxs-lookup"><span data-stu-id="4e059-372">Default to a file in the `$(IntermediateOutputPath)` (obj) directory.</span></span>
