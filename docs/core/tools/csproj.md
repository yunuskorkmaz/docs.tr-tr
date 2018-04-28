---
title: .NET Core csproj biçimine eklemeler
description: Varolan ve .NET Core csproj dosyaları arasındaki farklar hakkında bilgi edinin
author: blackdwarf
ms.author: mairaw
ms.date: 09/22/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: ed1a25337ac1594d4ca748d0c6f79bdcc038a1e8
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="additions-to-the-csproj-format-for-net-core"></a><span data-ttu-id="d5b67-103">.NET Core csproj biçimine eklemeler</span><span class="sxs-lookup"><span data-stu-id="d5b67-103">Additions to the csproj format for .NET Core</span></span>

<span data-ttu-id="d5b67-104">Bu belge için proje dosyalarını taşımak bir parçası olarak eklenen değişiklikleri özetlenmektedir *project.json* için *csproj* ve [MSBuild](https://github.com/Microsoft/MSBuild).</span><span class="sxs-lookup"><span data-stu-id="d5b67-104">This document outlines the changes that were added to the project files as part of the move from *project.json* to *csproj* and [MSBuild](https://github.com/Microsoft/MSBuild).</span></span> <span data-ttu-id="d5b67-105">Genel proje dosyasının söz dizimi ve başvuru hakkında daha fazla bilgi için bkz: [MSBuild proje dosyası](/visualstudio/msbuild/msbuild-project-file-schema-reference) belgeleri.</span><span class="sxs-lookup"><span data-stu-id="d5b67-105">For more information about general project file syntax and reference, see [the MSBuild project file](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation.</span></span>  

## <a name="implicit-package-references"></a><span data-ttu-id="d5b67-106">Örtük paket başvuruları</span><span class="sxs-lookup"><span data-stu-id="d5b67-106">Implicit package references</span></span>
<span data-ttu-id="d5b67-107">Metapackages örtük olarak başvuru belirtilen hedef framework(s) göre `<TargetFramework>` veya `<TargetFrameworks>` proje dosyanızın özelliği.</span><span class="sxs-lookup"><span data-stu-id="d5b67-107">Metapackages are implicitly referenced based on the target framework(s) specified in the `<TargetFramework>` or `<TargetFrameworks>` property of your project file.</span></span> <span data-ttu-id="d5b67-108">`<TargetFrameworks>` yoksayılır `<TargetFramework>` olduğu belirtildiğinde, sipariş bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="d5b67-108">`<TargetFrameworks>` is ignored if `<TargetFramework>` is specified, independent of order.</span></span>

```xml
 <PropertyGroup>
   <TargetFramework>netcoreapp1.1</TargetFramework>
 </PropertyGroup>
 ```
 
 ```xml
 <PropertyGroup>
   <TargetFrameworks>netcoreapp1.1;net462</TargetFrameworks>
 </PropertyGroup>
 ```

### <a name="recommendations"></a><span data-ttu-id="d5b67-109">Önerileri</span><span class="sxs-lookup"><span data-stu-id="d5b67-109">Recommendations</span></span>
<span data-ttu-id="d5b67-110">Bu yana `Microsoft.NETCore.App` veya `NetStandard.Library` metapackages dolaylı olarak başvurulan, bizim önerilen en iyi uygulamalar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d5b67-110">Since `Microsoft.NETCore.App` or `NetStandard.Library` metapackages are implicitly referenced, the following are our recommended best practices:</span></span>

* <span data-ttu-id="d5b67-111">.NET Core veya .NET standart hedeflerken açık bir başvuru hiçbir zaman sahip `Microsoft.NETCore.App` veya `NetStandard.Library` metapackages aracılığıyla bir `<PackageReference>` , proje dosyasında öğesi.</span><span class="sxs-lookup"><span data-stu-id="d5b67-111">When targeting .NET Core or .NET Standard, never have an explicit reference to the `Microsoft.NETCore.App` or `NetStandard.Library` metapackages via a `<PackageReference>` item in your project file.</span></span>
* <span data-ttu-id="d5b67-112">Belirli bir çalışma zamanı sürümü .NET Core hedeflerken gerekiyorsa, kullanması gereken `<RuntimeFrameworkVersion>` projenizdeki özelliği (örneğin, `1.0.4`) metapackage başvuran yerine.</span><span class="sxs-lookup"><span data-stu-id="d5b67-112">If you need a specific version of the runtime when targeting .NET Core, you should use the `<RuntimeFrameworkVersion>` property in your project (for example, `1.0.4`) instead of referencing the metapackage.</span></span>
    * <span data-ttu-id="d5b67-113">Kullanıyorsanız bu durum oluşabilir [müstakil dağıtımları](../deploying/index.md#self-contained-deployments-scd) ve 1.0.0 belirli düzeltme eki sürümü gerekir, örneğin LTS çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="d5b67-113">This might happen if you are using [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) and you need a specific patch version of 1.0.0 LTS runtime, for example.</span></span>
* <span data-ttu-id="d5b67-114">Belirli bir sürümünü gerekiyorsa `NetStandard.Library` .NET standart hedeflerken metapackage kullanabilir `<NetStandardImplicitPackageVersion>` özelliği ve kümesi sürümü, gerekir.</span><span class="sxs-lookup"><span data-stu-id="d5b67-114">If you need a specific version of the `NetStandard.Library` metapackage when targeting .NET Standard, you can use the `<NetStandardImplicitPackageVersion>` property and set the version you need.</span></span>
* <span data-ttu-id="d5b67-115">Açıkça ekleme yok veya güncelleştirme ya da başvurular `Microsoft.NETCore.App` veya `NetStandard.Library` .NET Framework projelerinde metapackage.</span><span class="sxs-lookup"><span data-stu-id="d5b67-115">Don't explicitly add or update references to either the `Microsoft.NETCore.App` or `NetStandard.Library` metapackage in .NET Framework projects.</span></span> <span data-ttu-id="d5b67-116">Herhangi bir sürümünü `NetStandard.Library` NuGet bir .NET standart tabanlı NuGet paketini otomatik olarak kullanarak bu sürümü yüklendiğinde gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d5b67-116">If any version of `NetStandard.Library` is needed when using a .NET Standard-based NuGet package, NuGet automatically installs that version.</span></span>

## <a name="default-compilation-includes-in-net-core-projects"></a><span data-ttu-id="d5b67-117">Varsayılan derleme .NET Core projelerinde içerir</span><span class="sxs-lookup"><span data-stu-id="d5b67-117">Default compilation includes in .NET Core projects</span></span>
<span data-ttu-id="d5b67-118">Git ile *csproj* biçimi son SDK sürümlerde, yeni varsayılan içerir ve derleme öğeleri ve katıştırılmış kaynaklar SDK özellikler dosyalar için dışlar yerimize.</span><span class="sxs-lookup"><span data-stu-id="d5b67-118">With the move to the *csproj* format in the latest SDK versions, we've moved the default includes and excludes for compile items and embedded resources to the SDK properties files.</span></span> <span data-ttu-id="d5b67-119">Bu, artık bu öğeler, proje dosyasında belirtmek gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d5b67-119">This means that you no longer need to specify these items in your project file.</span></span> 

<span data-ttu-id="d5b67-120">Bunu yapmak için ana nedeni, proje dosyanızdaki gösterip azaltmaktır.</span><span class="sxs-lookup"><span data-stu-id="d5b67-120">The main reason for doing this is to reduce the clutter in your project file.</span></span> <span data-ttu-id="d5b67-121">Oluşturduğunuz her projede tekrarlamanız gerekmez; böylece SDK'ın mevcut Varsayılanları en yaygın kullanım örnekleri, kapsamalıdır.</span><span class="sxs-lookup"><span data-stu-id="d5b67-121">The defaults that are present in the SDK should cover most common use cases, so there is no need to repeat them in every project that you create.</span></span> <span data-ttu-id="d5b67-122">Bu, gerektiğinde el ile düzenleme yanı sıra anlamak daha kolay küçük proje dosyalarına yol açar.</span><span class="sxs-lookup"><span data-stu-id="d5b67-122">This leads to smaller project files that are much easier to understand as well as edit by hand, if needed.</span></span> 

<span data-ttu-id="d5b67-123">Aşağıdaki tabloda hangi öğesi ve hangi gösterilmektedir [globs](https://en.wikipedia.org/wiki/Glob_(programming)) her ikisi de dahil ve SDK'ın dışlanan:</span><span class="sxs-lookup"><span data-stu-id="d5b67-123">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are both included and excluded in the SDK:</span></span> 

| <span data-ttu-id="d5b67-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="d5b67-124">Element</span></span>           | <span data-ttu-id="d5b67-125">Glob içerir</span><span class="sxs-lookup"><span data-stu-id="d5b67-125">Include glob</span></span>                              | <span data-ttu-id="d5b67-126">Glob Dışla</span><span class="sxs-lookup"><span data-stu-id="d5b67-126">Exclude glob</span></span>                                                  | <span data-ttu-id="d5b67-127">Glob Kaldır</span><span class="sxs-lookup"><span data-stu-id="d5b67-127">Remove glob</span></span>                |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| <span data-ttu-id="d5b67-128">Derleme</span><span class="sxs-lookup"><span data-stu-id="d5b67-128">Compile</span></span>           | <span data-ttu-id="d5b67-129">\*\*/\*.cs (veya diğer dil uzantıları)</span><span class="sxs-lookup"><span data-stu-id="d5b67-129">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="d5b67-130">\*\*/\*.kullanıcı;  \*\*/\*.\* Proj;  \* \* / \*.sln;  \* \* / \*.vssscc</span><span class="sxs-lookup"><span data-stu-id="d5b67-130">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="d5b67-131">Yok</span><span class="sxs-lookup"><span data-stu-id="d5b67-131">N/A</span></span>                        |
| <span data-ttu-id="d5b67-132">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="d5b67-132">EmbeddedResource</span></span>  | <span data-ttu-id="d5b67-133">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="d5b67-133">\*\*/\*.resx</span></span>                              | <span data-ttu-id="d5b67-134">\*\*/\*.kullanıcı; \*\*/\*.\* Proj; \* \* / \*.sln; \* \* / \*.vssscc</span><span class="sxs-lookup"><span data-stu-id="d5b67-134">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="d5b67-135">Yok</span><span class="sxs-lookup"><span data-stu-id="d5b67-135">N/A</span></span>                        |
| <span data-ttu-id="d5b67-136">Yok.</span><span class="sxs-lookup"><span data-stu-id="d5b67-136">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="d5b67-137">\*\*/\*.kullanıcı; \*\*/\*.\* Proj; \* \* / \*.sln; \* \* / \*.vssscc</span><span class="sxs-lookup"><span data-stu-id="d5b67-137">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="d5b67-138">- \*\*/\*.cs; \* \* / \*.resx</span><span class="sxs-lookup"><span data-stu-id="d5b67-138">- \*\*/\*.cs; \*\*/\*.resx</span></span> |

<span data-ttu-id="d5b67-139">Projenizde globs varsa ve en yeni SDK kullanarak oluşturmak denerseniz, aşağıdaki hata iletisi alırsınız:</span><span class="sxs-lookup"><span data-stu-id="d5b67-139">If you have globs in your project and you try to build it using the newest SDK, you'll get the following error:</span></span>

> <span data-ttu-id="d5b67-140">Yinelenen Derleme öğeleri dahil.</span><span class="sxs-lookup"><span data-stu-id="d5b67-140">Duplicate Compile items were included.</span></span> <span data-ttu-id="d5b67-141">.NET SDK'sı, varsayılan olarak proje dizininizden derleme öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="d5b67-141">The .NET SDK includes Compile items from your project directory by default.</span></span> <span data-ttu-id="d5b67-142">Proje dosyasından bu öğeleri kaldırmak veya açıkça bunları proje dosyanızda dahil etmek istiyorsanız 'false' 'EnableDefaultCompileItems' özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d5b67-142">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span> 

<span data-ttu-id="d5b67-143">Bu hataya alabilmek için ya da açık kaldırabilirsiniz `Compile` olanlarla eşleşmesi öğeleri önceki tabloda listelenen veya ayarlayabilirsiniz `<EnableDefaultCompileItems>` özelliğine `false`, şöyle:</span><span class="sxs-lookup"><span data-stu-id="d5b67-143">In order to get around this error, you can either remove the explicit `Compile` items that match the ones listed on the previous table, or you can set the `<EnableDefaultCompileItems>` property to `false`, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```
<span data-ttu-id="d5b67-144">Bu özelliği ayarlamak `false` örtük ekleme geçersiz kılar ve davranışı geri burada b projenizde varsayılan globs belirlemek için önceki SDK döner.</span><span class="sxs-lookup"><span data-stu-id="d5b67-144">Setting this property to `false` will override implicit inclusion and the behavior will revert back to the previous SDKs where you had to specify the default globs in your project.</span></span> 

<span data-ttu-id="d5b67-145">Bu değişiklik ana değiştirmez, diğer mekanizması içerir.</span><span class="sxs-lookup"><span data-stu-id="d5b67-145">This change does not modify the main mechanics of other includes.</span></span> <span data-ttu-id="d5b67-146">Örneğin, uygulamanız ile yayımlanan için bazı dosyaları belirlemek istiyorsanız, ancak içinde bilinen mekanizmaları kullanmaya devam edebilirsiniz *csproj* söz konusu (örneğin, `<Content>` öğesi).</span><span class="sxs-lookup"><span data-stu-id="d5b67-146">However, if you wish to specify, for example, some files to get published with your app, you can still use the known mechanisms in *csproj* for that (for example, the `<Content>` element).</span></span>

<span data-ttu-id="d5b67-147">`<EnableDefaultCompileItems>` yalnızca devre dışı bırakır `Compile` globs örtük gibi diğer globs etkilemez ancak `None` için de geçerlidir glob \*.cs öğeleri.</span><span class="sxs-lookup"><span data-stu-id="d5b67-147">`<EnableDefaultCompileItems>` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob, which also applies to \*.cs items.</span></span> <span data-ttu-id="d5b67-148">Nedeniyle **Çözüm Gezgini** Göster devam edecek \*.cs öğeleri olarak eklenen projenin bir parçası olarak `None` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="d5b67-148">Because of that, **Solution Explorer** will continue show \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="d5b67-149">Benzer şekilde, kullandığınız `<EnableDefaultNoneItems>` örtük devre dışı bırakmak için `None` glob.</span><span class="sxs-lookup"><span data-stu-id="d5b67-149">In a similar way, you can use `<EnableDefaultNoneItems>` to disable the implicit `None` glob.</span></span>

<span data-ttu-id="d5b67-150">Devre dışı bırakmak için **tüm örtük globs**, ayarlayabileceğiniz `<EnableDefaultItems>` özelliğine `false` aşağıdaki örnekteki gibi:</span><span class="sxs-lookup"><span data-stu-id="d5b67-150">To disable **all implicit globs**, you can set the `<EnableDefaultItems>` property to `false` as in the following example:</span></span>
```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

### <a name="recommendation"></a><span data-ttu-id="d5b67-151">Öneri</span><span class="sxs-lookup"><span data-stu-id="d5b67-151">Recommendation</span></span>
<span data-ttu-id="d5b67-152">Csproj ile varsayılan globs projenizden kaldırın ve yalnızca uygulama/kitaplığınızın çeşitli senaryolar için (örneğin, çalışma zamanı ve NuGet paketleme) gereken yapıların globs ile dosya yollarını ekleyin öneririz.</span><span class="sxs-lookup"><span data-stu-id="d5b67-152">With csproj, we recommend that you remove the default globs from your project and only add file paths with globs for those artifacts that your app/library needs for various scenarios (for example, runtime and NuGet packaging).</span></span>

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a><span data-ttu-id="d5b67-153">MSBuild tarafından görülen şekilde tüm proje görme</span><span class="sxs-lookup"><span data-stu-id="d5b67-153">How to see the whole project as MSBuild sees it</span></span>

<span data-ttu-id="d5b67-154">Bu csproj değişiklikleri proje dosyalarını büyük ölçüde kolaylaştırma olsa da, SDK'sı ve hedeflerine dahil edilen sonra MSBuild tarafından görülen şekilde tam olarak genişletilmiş proje görmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5b67-154">While those csproj changes greatly simplify project files, you might want to see the fully expanded project as MSBuild sees it once the SDK and its targets are included.</span></span> <span data-ttu-id="d5b67-155">Proje ile önişle [ `/pp` geçiş](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) , [ `dotnet msbuild` ](dotnet-msbuild.md) komutu, hangi dosyaların içeri aktarılan hangi gösterir, kaynakları ve Katkıları oluşturulacak gerçekte Proje oluşturma:</span><span class="sxs-lookup"><span data-stu-id="d5b67-155">Preprocess the project with [the `/pp` switch](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) of the [`dotnet msbuild`](dotnet-msbuild.md) command, which shows which files are imported, their sources, and their contributions to the build without actually building the project:</span></span>

`dotnet msbuild /pp:fullproject.xml`

<span data-ttu-id="d5b67-156">Projenin birden çok hedef çerçeveyi varsa, komutun sonuçlarını yalnızca bunlardan biri üzerinde bir MSBuild özelliği olarak belirterek odaklanmış olur:</span><span class="sxs-lookup"><span data-stu-id="d5b67-156">If the project has multiple target frameworks, the results of the command should be focused on only one of them by specifying it as an MSBuild property:</span></span>

`dotnet msbuild /p:TargetFramework=netcoreapp2.0 /pp:fullproject.xml`

## <a name="additions"></a><span data-ttu-id="d5b67-157">Eklemeler</span><span class="sxs-lookup"><span data-stu-id="d5b67-157">Additions</span></span>

### <a name="sdk-attribute"></a><span data-ttu-id="d5b67-158">SDK özniteliği</span><span class="sxs-lookup"><span data-stu-id="d5b67-158">Sdk attribute</span></span> 
<span data-ttu-id="d5b67-159">`<Project>` Öğesinin *.csproj* dosya adlı yeni bir öznitelik sahip `Sdk`.</span><span class="sxs-lookup"><span data-stu-id="d5b67-159">The `<Project>` element of the *.csproj* file has a new attribute called `Sdk`.</span></span> <span data-ttu-id="d5b67-160">`Sdk` SDK olacağı belirtir projesi tarafından kullanılan.</span><span class="sxs-lookup"><span data-stu-id="d5b67-160">`Sdk` specifies which SDK will be used by the project.</span></span> <span data-ttu-id="d5b67-161">SDK'sı olarak [katmanlama belge](cli-msbuild-architecture.md) açıklar, MSBuild kümesidir [görevleri](/visualstudio/msbuild/msbuild-tasks) ve [hedefleri](/visualstudio/msbuild/msbuild-targets) .NET Core kodu oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="d5b67-161">The SDK, as the [layering document](cli-msbuild-architecture.md) describes, is a set of MSBuild [tasks](/visualstudio/msbuild/msbuild-tasks) and [targets](/visualstudio/msbuild/msbuild-targets) that can build .NET Core code.</span></span> <span data-ttu-id="d5b67-162">İki ana SDK'ları ile .NET Core araçları gönderdiğimiz:</span><span class="sxs-lookup"><span data-stu-id="d5b67-162">We ship two main SDKs with the .NET Core tools:</span></span>

1. <span data-ttu-id="d5b67-163">.NET Core SDK kimliği `Microsoft.NET.Sdk`</span><span class="sxs-lookup"><span data-stu-id="d5b67-163">The .NET Core SDK with the ID of `Microsoft.NET.Sdk`</span></span>
2. <span data-ttu-id="d5b67-164">.NET Core web SDK kimliği `Microsoft.NET.Sdk.Web`</span><span class="sxs-lookup"><span data-stu-id="d5b67-164">The .NET Core web SDK with the ID of `Microsoft.NET.Sdk.Web`</span></span>

<span data-ttu-id="d5b67-165">Olmasına gerek `Sdk` özniteliği bu kimlikleri birine üzerinde `<Project>` .NET Core araçlarını kullanın ve kodunuzu oluşturmak için öğesi.</span><span class="sxs-lookup"><span data-stu-id="d5b67-165">You need to have the `Sdk` attribute set to one of those IDs on the `<Project>` element in order to use the .NET Core tools and build your code.</span></span> 

### <a name="packagereference"></a><span data-ttu-id="d5b67-166">PackageReference</span><span class="sxs-lookup"><span data-stu-id="d5b67-166">PackageReference</span></span>
<span data-ttu-id="d5b67-167">Öğesi, bir NuGet bağımlılığı projede belirtir.</span><span class="sxs-lookup"><span data-stu-id="d5b67-167">Item that specifies a NuGet dependency in the project.</span></span> <span data-ttu-id="d5b67-168">`Include` Özniteliği paket kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d5b67-168">The `Include` attribute specifies the package ID.</span></span> 

```xml
<PackageReference Include="<package-id>" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a><span data-ttu-id="d5b67-169">Sürüm</span><span class="sxs-lookup"><span data-stu-id="d5b67-169">Version</span></span>
<span data-ttu-id="d5b67-170">`Version` geri yüklemek için paketin sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="d5b67-170">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="d5b67-171">Öznitelik kurallarına uyar [NuGet sürüm](/nuget/create-packages/dependency-versions#version-ranges) düzeni.</span><span class="sxs-lookup"><span data-stu-id="d5b67-171">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="d5b67-172">Bir tam sürüm eşleşiyorsa varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="d5b67-172">The default behavior is an exact version match.</span></span> <span data-ttu-id="d5b67-173">Örneğin, belirten `Version="1.2.3"` NuGet gösterime eşdeğerdir `[1.2.3]` tam 1.2.3 için paketin sürümü.</span><span class="sxs-lookup"><span data-stu-id="d5b67-173">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

#### <a name="includeassets-excludeassets-and-privateassets"></a><span data-ttu-id="d5b67-174">IncludeAssets, ExcludeAssets ve PrivateAssets</span><span class="sxs-lookup"><span data-stu-id="d5b67-174">IncludeAssets, ExcludeAssets and PrivateAssets</span></span>
<span data-ttu-id="d5b67-175">`IncludeAssets` özniteliği belirtir. pakete ait varlıklar tarafından belirtilen `<PackageReference>` kullanılması.</span><span class="sxs-lookup"><span data-stu-id="d5b67-175">`IncludeAssets` attribute specifies what assets belonging to the package specified by `<PackageReference>` should be consumed.</span></span> 

<span data-ttu-id="d5b67-176">`ExcludeAssets` özniteliği belirtir. pakete ait varlıklar tarafından belirtilen `<PackageReference>` değil kullanılması.</span><span class="sxs-lookup"><span data-stu-id="d5b67-176">`ExcludeAssets` attribute specifies what assets belonging to the package specified by `<PackageReference>` should not be consumed.</span></span>

<span data-ttu-id="d5b67-177">`PrivateAssets` özniteliği belirtir. pakete ait varlıklar tarafından belirtilen `<PackageReference>` bunlar sonraki projeye akış değil ancak bu kullanılması.</span><span class="sxs-lookup"><span data-stu-id="d5b67-177">`PrivateAssets` attribute specifies what assets belonging to the package specified by `<PackageReference>` should be consumed but that they should not flow to the next project.</span></span> 

> [!NOTE]
> <span data-ttu-id="d5b67-178">`PrivateAssets` eşdeğer olan *project.json*/*xproj* `SuppressParent` öğesi.</span><span class="sxs-lookup"><span data-stu-id="d5b67-178">`PrivateAssets` is equivalent to the *project.json*/*xproj* `SuppressParent` element.</span></span>

<span data-ttu-id="d5b67-179">Bu öznitelik, bir veya daha fazla aşağıdaki öğeleri içerebilir:</span><span class="sxs-lookup"><span data-stu-id="d5b67-179">These attributes can contain one or more of the following items:</span></span>

* <span data-ttu-id="d5b67-180">`Compile` – lib klasörünün içeriğini karşı derlemek kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d5b67-180">`Compile` – the contents of the lib folder are available to compile against.</span></span>
* <span data-ttu-id="d5b67-181">`Runtime` – çalışma zamanı klasörünün içeriğini dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="d5b67-181">`Runtime` – the contents of the runtime folder are distributed.</span></span>
* <span data-ttu-id="d5b67-182">`ContentFiles` – içeriği *Content dosyaları* klasörü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d5b67-182">`ContentFiles` – the contents of the *contentfiles* folder are used.</span></span>
* <span data-ttu-id="d5b67-183">`Build` – özellik/hedefleri oluşturma klasöründe kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d5b67-183">`Build` – the props/targets in the build folder are used.</span></span>
* <span data-ttu-id="d5b67-184">`Native` – içeriği yerel varlıklar çalışma zamanı için çıkış klasörüne kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="d5b67-184">`Native` – the contents from native assets are copied to the output folder for runtime.</span></span>
* <span data-ttu-id="d5b67-185">`Analyzers` – Çözümleyiciler kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d5b67-185">`Analyzers` – the analyzers are used.</span></span>

<span data-ttu-id="d5b67-186">Alternatif olarak, öznitelik içerebilir:</span><span class="sxs-lookup"><span data-stu-id="d5b67-186">Alternatively, the attribute can contain:</span></span>

* <span data-ttu-id="d5b67-187">`None` – varlıklar hiçbiri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d5b67-187">`None` – none of the assets are used.</span></span>
* <span data-ttu-id="d5b67-188">`All` – Tüm varlıklar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d5b67-188">`All` – all assets are used.</span></span>

### <a name="dotnetclitoolreference"></a><span data-ttu-id="d5b67-189">DotNetCliToolReference</span><span class="sxs-lookup"><span data-stu-id="d5b67-189">DotNetCliToolReference</span></span>
<span data-ttu-id="d5b67-190">`<DotNetCliToolReference>` öğe unsuru, proje bağlamında geri yüklemek için kullanıcının istediği CLI aracı belirtir.</span><span class="sxs-lookup"><span data-stu-id="d5b67-190">`<DotNetCliToolReference>` item element specifies the CLI tool that the user wants to restore in the context of the project.</span></span> <span data-ttu-id="d5b67-191">Bir yerini alır `tools` düğümünde *project.json*.</span><span class="sxs-lookup"><span data-stu-id="d5b67-191">It's a replacement for the `tools` node in *project.json*.</span></span> 

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

#### <a name="version"></a><span data-ttu-id="d5b67-192">Sürüm</span><span class="sxs-lookup"><span data-stu-id="d5b67-192">Version</span></span>
<span data-ttu-id="d5b67-193">`Version` geri yüklemek için paketin sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="d5b67-193">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="d5b67-194">Öznitelik kurallarına uyar [NuGet sürüm](/nuget/create-packages/dependency-versions#version-ranges) düzeni.</span><span class="sxs-lookup"><span data-stu-id="d5b67-194">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="d5b67-195">Bir tam sürüm eşleşiyorsa varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="d5b67-195">The default behavior is an exact version match.</span></span> <span data-ttu-id="d5b67-196">Örneğin, belirten `Version="1.2.3"` NuGet gösterime eşdeğerdir `[1.2.3]` tam 1.2.3 için paketin sürümü.</span><span class="sxs-lookup"><span data-stu-id="d5b67-196">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

### <a name="runtimeidentifiers"></a><span data-ttu-id="d5b67-197">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="d5b67-197">RuntimeIdentifiers</span></span>
<span data-ttu-id="d5b67-198">`<RuntimeIdentifiers>` Öğesi noktalı virgülle ayrılmış bir listesini belirtmenize olanak sağlar [çalışma zamanı tanımlayıcıları (RID)](../rid-catalog.md) projesi için.</span><span class="sxs-lookup"><span data-stu-id="d5b67-198">The `<RuntimeIdentifiers>` element lets you specify a semicolon-delimited list of [Runtime Identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="d5b67-199">RID müstakil dağıtımları yayımlamayı etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="d5b67-199">RIDs enable publishing a self-contained deployments.</span></span> 

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a><span data-ttu-id="d5b67-200">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="d5b67-200">RuntimeIdentifier</span></span>
<span data-ttu-id="d5b67-201">`<RuntimeIdentifier>` Öğesi yalnızca bir belirtmenize olanak verir [çalışma zamanı tanımlayıcı (RID)](../rid-catalog.md) projesi için.</span><span class="sxs-lookup"><span data-stu-id="d5b67-201">The `<RuntimeIdentifier>` element allows you to specify only one [Runtime Identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="d5b67-202">RID kendi içinde bulunan bir dağıtım yayımlamayı etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="d5b67-202">RIDs enable publishing a self-contained deployment.</span></span> 

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

### <a name="packagetargetfallback"></a><span data-ttu-id="d5b67-203">PackageTargetFallback</span><span class="sxs-lookup"><span data-stu-id="d5b67-203">PackageTargetFallback</span></span> 
<span data-ttu-id="d5b67-204">`<PackageTargetFallback>` Öğesi paketleri geri yüklenirken kullanılacak uyumlu hedefleri kümesi belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="d5b67-204">The `<PackageTargetFallback>` element allows you to specify a set of compatible targets to be used when restoring packages.</span></span> <span data-ttu-id="d5b67-205">Dotnet kullanmak paketleri izin vermek için tasarlanmış [TxM (hedef x takma ad)](/nuget/schema/target-frameworks) dotnet TxM bildirmeyin paketlerle çalışılacak.</span><span class="sxs-lookup"><span data-stu-id="d5b67-205">It's designed to allow packages that use the dotnet [TxM (Target x Moniker)](/nuget/schema/target-frameworks) to operate with packages that don't declare a dotnet TxM.</span></span> <span data-ttu-id="d5b67-206">Projenizi TxM dotnet kullanan sonra bağlı olduğu gereken üzerinde de tüm paketler dotnet TxM, sahiptir ve eklediğiniz sürece `<PackageTargetFallback>` dotnet ile uyumlu olacak şekilde dotnet olmayan platformları izin vermek üzere projenize.</span><span class="sxs-lookup"><span data-stu-id="d5b67-206">If your project uses the dotnet TxM, then all the packages it depends on must also have a dotnet TxM, unless you add the `<PackageTargetFallback>` to your project in order to allow non-dotnet platforms to be compatible with dotnet.</span></span> 

<span data-ttu-id="d5b67-207">Aşağıdaki örnek, projenizdeki tüm hedefleri için geri dönüşler sağlar:</span><span class="sxs-lookup"><span data-stu-id="d5b67-207">The following example provides the fallbacks for all targets in your project:</span></span> 

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

<span data-ttu-id="d5b67-208">Aşağıdaki örnekte yalnızca geri dönüşler belirtir `netcoreapp1.0` hedef:</span><span class="sxs-lookup"><span data-stu-id="d5b67-208">The following example specifies the fallbacks only for the `netcoreapp1.0` target:</span></span>

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp1.0'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="nuget-metadata-properties"></a><span data-ttu-id="d5b67-209">NuGet meta veri özellikleri</span><span class="sxs-lookup"><span data-stu-id="d5b67-209">NuGet metadata properties</span></span>
<span data-ttu-id="d5b67-210">MSbuild için taşıma ile biz bir NuGet paketi sevk kullanıldığında giriş meta verileri taşınmış *project.json* için *.csproj* dosyaları.</span><span class="sxs-lookup"><span data-stu-id="d5b67-210">With the move to MSbuild, we have moved the input metadata that is used when packing a NuGet package from *project.json* to *.csproj* files.</span></span> <span data-ttu-id="d5b67-211">İçinde gitmek sahip oldukları için MSBuild özellikleri girdileridir bir `<PropertyGroup>` grubu.</span><span class="sxs-lookup"><span data-stu-id="d5b67-211">The inputs are MSBuild properties so they have to go within a `<PropertyGroup>` group.</span></span> <span data-ttu-id="d5b67-212">Paketleme işleminin girdi olarak kullanılırken kullanılan özelliklerin listesi aşağıda verilmiştir `dotnet pack` komut veya `Pack` MSBuild hedef başka bir deyişle SDK'ın bir parçası.</span><span class="sxs-lookup"><span data-stu-id="d5b67-212">The following is the list of properties that are used as inputs to the packing process when using the `dotnet pack` command or the `Pack` MSBuild target that is part of the SDK.</span></span> 

### <a name="ispackable"></a><span data-ttu-id="d5b67-213">IsPackable</span><span class="sxs-lookup"><span data-stu-id="d5b67-213">IsPackable</span></span>
<span data-ttu-id="d5b67-214">Proje dolu olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="d5b67-214">A Boolean value that specifies whether the project can be packed.</span></span> <span data-ttu-id="d5b67-215">Varsayılan değer `true` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="d5b67-215">The default value is `true`.</span></span> 

### <a name="packageversion"></a><span data-ttu-id="d5b67-216">PackageVersion</span><span class="sxs-lookup"><span data-stu-id="d5b67-216">PackageVersion</span></span>
<span data-ttu-id="d5b67-217">Sonuçta elde edilen paket olacaktır sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="d5b67-217">Specifies the version that the resulting package will have.</span></span> <span data-ttu-id="d5b67-218">NuGet sürüm dizesi biçimlerinin kabul eder.</span><span class="sxs-lookup"><span data-stu-id="d5b67-218">Accepts all forms of NuGet version string.</span></span> <span data-ttu-id="d5b67-219">Varsayılan değer değerini `$(Version)`, diğer bir deyişle, özelliğin `Version` projesinde.</span><span class="sxs-lookup"><span data-stu-id="d5b67-219">Default is the value of `$(Version)`, that is, of the property `Version` in the project.</span></span> 

### <a name="packageid"></a><span data-ttu-id="d5b67-220">Paket kimliği</span><span class="sxs-lookup"><span data-stu-id="d5b67-220">PackageId</span></span>
<span data-ttu-id="d5b67-221">Sonuçta elde edilen paket adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d5b67-221">Specifies the name for the resulting package.</span></span> <span data-ttu-id="d5b67-222">Belirtilmezse, `pack` işlemi varsayılan olarak kullanmaya `AssemblyName` veya dizin adıyla paketin adı.</span><span class="sxs-lookup"><span data-stu-id="d5b67-222">If not specified, the `pack` operation will default to using the `AssemblyName` or directory name as the name of the package.</span></span> 

### <a name="title"></a><span data-ttu-id="d5b67-223">Başlık</span><span class="sxs-lookup"><span data-stu-id="d5b67-223">Title</span></span>
<span data-ttu-id="d5b67-224">Nuget.org ve Visual Studio'da Paket Yöneticisi gibi UI görünümlerde genellikle kullanılan paket, bir insan kolay başlığı.</span><span class="sxs-lookup"><span data-stu-id="d5b67-224">A human-friendly title of the package, typically used in UI displays as on nuget.org and the Package Manager in Visual Studio.</span></span> <span data-ttu-id="d5b67-225">Paket kimliği belirtilmezse, bunun yerine kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d5b67-225">If not specified, the package ID is used instead.</span></span>

### <a name="authors"></a><span data-ttu-id="d5b67-226">Yazarlar</span><span class="sxs-lookup"><span data-stu-id="d5b67-226">Authors</span></span>
<span data-ttu-id="d5b67-227">Nuget.org profil adları eşleşen paketleri yazarlar noktalı virgülle ayrılmış listesi. Bunlar nuget.org NuGet galerisinde görüntülenir ve paketleri çapraz başvuru için aynı yazarlar tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d5b67-227">A semicolon-separated list of packages authors, matching the profile names on nuget.org. These are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span>

### <a name="description"></a><span data-ttu-id="d5b67-228">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d5b67-228">Description</span></span>
<span data-ttu-id="d5b67-229">Paket UI görüntü için uzun bir açıklaması.</span><span class="sxs-lookup"><span data-stu-id="d5b67-229">A long description of the package for UI display.</span></span>

### <a name="copyright"></a><span data-ttu-id="d5b67-230">Telif Hakkı</span><span class="sxs-lookup"><span data-stu-id="d5b67-230">Copyright</span></span>
<span data-ttu-id="d5b67-231">Telif Hakkı ayrıntıları paketi için.</span><span class="sxs-lookup"><span data-stu-id="d5b67-231">Copyright details for the package.</span></span>

### <a name="packagerequirelicenseacceptance"></a><span data-ttu-id="d5b67-232">PackageRequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="d5b67-232">PackageRequireLicenseAcceptance</span></span>
<span data-ttu-id="d5b67-233">İstemci paketi lisans paketi yüklemeden önce kabul etmek için tüketici sor olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="d5b67-233">A Boolean value that specifies whether the client must prompt the consumer to accept the package license before installing the package.</span></span> <span data-ttu-id="d5b67-234">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="d5b67-234">The default is `false`.</span></span>

### <a name="packagelicenseurl"></a><span data-ttu-id="d5b67-235">PackageLicenseUrl</span><span class="sxs-lookup"><span data-stu-id="d5b67-235">PackageLicenseUrl</span></span>
<span data-ttu-id="d5b67-236">Paketi uygulanabilir lisans bir URL.</span><span class="sxs-lookup"><span data-stu-id="d5b67-236">An URL to the license that is applicable to the package.</span></span>

### <a name="packageprojecturl"></a><span data-ttu-id="d5b67-237">PackageProjectUrl</span><span class="sxs-lookup"><span data-stu-id="d5b67-237">PackageProjectUrl</span></span>
<span data-ttu-id="d5b67-238">Paketin giriş sayfası, genellikle kullanıcı Arabiriminde gösterilen URL'sini nuget.org yanı sıra görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d5b67-238">A URL for the package's home page, often shown in UI displays as well as nuget.org.</span></span>

### <a name="packageiconurl"></a><span data-ttu-id="d5b67-239">PackageIconUrl</span><span class="sxs-lookup"><span data-stu-id="d5b67-239">PackageIconUrl</span></span>
<span data-ttu-id="d5b67-240">UI görüntü paketinde simgesi olarak kullanılacak bir URL saydam arka plan 64 x 64 görüntüsüyle.</span><span class="sxs-lookup"><span data-stu-id="d5b67-240">A URL for a 64x64 image with transparent background to use as the icon for the package in UI display.</span></span>

### <a name="packagereleasenotes"></a><span data-ttu-id="d5b67-241">PackageReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="d5b67-241">PackageReleaseNotes</span></span>
<span data-ttu-id="d5b67-242">Paket için sürüm notları.</span><span class="sxs-lookup"><span data-stu-id="d5b67-242">Release notes for the package.</span></span>

### <a name="packagetags"></a><span data-ttu-id="d5b67-243">PackageTags</span><span class="sxs-lookup"><span data-stu-id="d5b67-243">PackageTags</span></span>
<span data-ttu-id="d5b67-244">Etiketleri noktalı virgülle ayrılmış bir listesi, paket belirler.</span><span class="sxs-lookup"><span data-stu-id="d5b67-244">A semicolon-delimited list of tags that designates the package.</span></span>

### <a name="packageoutputpath"></a><span data-ttu-id="d5b67-245">PackageOutputPath</span><span class="sxs-lookup"><span data-stu-id="d5b67-245">PackageOutputPath</span></span>
<span data-ttu-id="d5b67-246">Paketlenmiş paket bırakılacak çıkış yolu belirler.</span><span class="sxs-lookup"><span data-stu-id="d5b67-246">Determines the output path in which the packed package will be dropped.</span></span> <span data-ttu-id="d5b67-247">Varsayılan değer `$(OutputPath)`.</span><span class="sxs-lookup"><span data-stu-id="d5b67-247">Default is `$(OutputPath)`.</span></span> 

### <a name="includesymbols"></a><span data-ttu-id="d5b67-248">IncludeSymbols</span><span class="sxs-lookup"><span data-stu-id="d5b67-248">IncludeSymbols</span></span>
<span data-ttu-id="d5b67-249">Bu Boole değeri, projenin dolu olduğunda paketi bir ek simge paketi oluşturmak gösterir.</span><span class="sxs-lookup"><span data-stu-id="d5b67-249">This Boolean value indicates whether the package should create an additional symbols package when the project is packed.</span></span> <span data-ttu-id="d5b67-250">Bu paket sahip bir *. symbols.nupkg* uzantısı ve DLL birlikte PDB dosyalarını ve diğer çıktı dosyalarını kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="d5b67-250">This package will have a *.symbols.nupkg* extension and will copy the PDB files along with the DLL and other output files.</span></span>

### <a name="includesource"></a><span data-ttu-id="d5b67-251">IncludeSource</span><span class="sxs-lookup"><span data-stu-id="d5b67-251">IncludeSource</span></span>
<span data-ttu-id="d5b67-252">Bu Boole değeri paketi işlemi bir kaynak paketi oluşturmalısınız olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d5b67-252">This Boolean value indicates whether the pack process should create a source package.</span></span> <span data-ttu-id="d5b67-253">Kaynak Paketi kitaplığın kaynak kodu yanı sıra PDB dosyalarını içerir.</span><span class="sxs-lookup"><span data-stu-id="d5b67-253">The source package contains the library's source code as well as PDB files.</span></span> <span data-ttu-id="d5b67-254">Kaynak dosyaları altında konur `src/ProjectName` elde edilen paket dosyasındaki dizin.</span><span class="sxs-lookup"><span data-stu-id="d5b67-254">Source files are put under the `src/ProjectName` directory in the resulting package file.</span></span> 

### <a name="istool"></a><span data-ttu-id="d5b67-255">IsTool</span><span class="sxs-lookup"><span data-stu-id="d5b67-255">IsTool</span></span>
<span data-ttu-id="d5b67-256">Tüm çıktı dosyaları için kopyalanıp kopyalanmayacağını belirtir *Araçları* klasörü yerine *lib* klasör.</span><span class="sxs-lookup"><span data-stu-id="d5b67-256">Specifies whether all output files are copied to the *tools* folder instead of the *lib* folder.</span></span> <span data-ttu-id="d5b67-257">Bu farklı olduğuna dikkat edin bir `DotNetCliTool` , belirtilen ayarlayarak `PackageType` içinde *.csproj* dosya.</span><span class="sxs-lookup"><span data-stu-id="d5b67-257">Note that this is different from a `DotNetCliTool` which is specified by setting the `PackageType` in the *.csproj* file.</span></span>

### <a name="repositoryurl"></a><span data-ttu-id="d5b67-258">RepositoryUrl</span><span class="sxs-lookup"><span data-stu-id="d5b67-258">RepositoryUrl</span></span>
<span data-ttu-id="d5b67-259">Depo URL'si paket için kaynak kodunu bulunduğu yerde ve/veya hangi onu oluşturulmakta olan gelen belirtir.</span><span class="sxs-lookup"><span data-stu-id="d5b67-259">Specifies the URL for the repository where the source code for the package resides and/or from which it's being built.</span></span> 

### <a name="repositorytype"></a><span data-ttu-id="d5b67-260">RepositoryType</span><span class="sxs-lookup"><span data-stu-id="d5b67-260">RepositoryType</span></span>
<span data-ttu-id="d5b67-261">Depo türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="d5b67-261">Specifies the type of the repository.</span></span> <span data-ttu-id="d5b67-262">Varsayılan değer "git" dir.</span><span class="sxs-lookup"><span data-stu-id="d5b67-262">Default is "git".</span></span> 

### <a name="nopackageanalysis"></a><span data-ttu-id="d5b67-263">NoPackageAnalysis</span><span class="sxs-lookup"><span data-stu-id="d5b67-263">NoPackageAnalysis</span></span>
<span data-ttu-id="d5b67-264">Paketi paket analiz paketi oluşturduktan sonra çalışmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d5b67-264">Specifies that pack should not run package analysis after building the package.</span></span>

### <a name="minclientversion"></a><span data-ttu-id="d5b67-265">MinClientVersion</span><span class="sxs-lookup"><span data-stu-id="d5b67-265">MinClientVersion</span></span>
<span data-ttu-id="d5b67-266">Nuget.exe ve Visual Studio Paket Yöneticisi tarafından zorlanan bu paketi yükleyebilmek için NuGet istemci en düşük sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="d5b67-266">Specifies the minimum version of the NuGet client that can install this package, enforced by nuget.exe and the Visual Studio Package Manager.</span></span>

### <a name="includebuildoutput"></a><span data-ttu-id="d5b67-267">IncludeBuildOutput</span><span class="sxs-lookup"><span data-stu-id="d5b67-267">IncludeBuildOutput</span></span>
<span data-ttu-id="d5b67-268">Bu Boole değerleri belirtir yapı çıktı derlemeler halinde dolu olup olmadığını *.nupkg* dosya ya da değil.</span><span class="sxs-lookup"><span data-stu-id="d5b67-268">This Boolean values specifies whether the build output assemblies should be packed into the *.nupkg* file or not.</span></span>

### <a name="includecontentinpack"></a><span data-ttu-id="d5b67-269">IncludeContentInPack</span><span class="sxs-lookup"><span data-stu-id="d5b67-269">IncludeContentInPack</span></span>
<span data-ttu-id="d5b67-270">Bu Boole değeri tüm öğeler, bir tür sahip olup olmadığını belirtir `Content` elde edilen paketinde otomatik olarak eklenecektir.</span><span class="sxs-lookup"><span data-stu-id="d5b67-270">This Boolean value specifies whether any items that have a type of `Content` will be included in the resulting package automatically.</span></span> <span data-ttu-id="d5b67-271">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="d5b67-271">The default is `true`.</span></span> 

### <a name="buildoutputtargetfolder"></a><span data-ttu-id="d5b67-272">BuildOutputTargetFolder</span><span class="sxs-lookup"><span data-stu-id="d5b67-272">BuildOutputTargetFolder</span></span>
<span data-ttu-id="d5b67-273">Çıktı derlemelerinin nereye yerleştireceğinizi klasörü belirtir.</span><span class="sxs-lookup"><span data-stu-id="d5b67-273">Specifies the folder where to place the output assemblies.</span></span> <span data-ttu-id="d5b67-274">Çıktı derlemelerinin (ve diğer çıktı dosyaları) ilgili framework klasörlerine kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="d5b67-274">The output assemblies (and other output files) are copied into their respective framework folders.</span></span>

### <a name="contenttargetfolders"></a><span data-ttu-id="d5b67-275">ContentTargetFolders</span><span class="sxs-lookup"><span data-stu-id="d5b67-275">ContentTargetFolders</span></span>
<span data-ttu-id="d5b67-276">Bu özellik, tüm içerik dosyalarının nerede tamamlamalıdır, varsayılan konumu belirtir `PackagePath` kendileri için belirtilmemiş.</span><span class="sxs-lookup"><span data-stu-id="d5b67-276">This property specifies the default location of where all the content files should go if `PackagePath` is not specified for them.</span></span> <span data-ttu-id="d5b67-277">Varsayılan değer "içerik; Content dosyaları".</span><span class="sxs-lookup"><span data-stu-id="d5b67-277">The default value is "content;contentFiles".</span></span>

### <a name="nuspecfile"></a><span data-ttu-id="d5b67-278">NuspecFile</span><span class="sxs-lookup"><span data-stu-id="d5b67-278">NuspecFile</span></span>
<span data-ttu-id="d5b67-279">Göreli veya mutlak bir yol *.nuspec* paketleme için kullanılan dosya.</span><span class="sxs-lookup"><span data-stu-id="d5b67-279">Relative or absolute path to the *.nuspec* file being used for packing.</span></span> 

> [!NOTE]
> <span data-ttu-id="d5b67-280">Varsa *.nuspec* dosyası belirtilmediyse, kullanıldığı **özel olarak** bilgileri ve herhangi bir bilgi projelerinde paketleme kullanılmadığı için.</span><span class="sxs-lookup"><span data-stu-id="d5b67-280">If the *.nuspec* file is specified, it's used **exclusively** for packaging information and any information in the projects is not used.</span></span> 

### <a name="nuspecbasepath"></a><span data-ttu-id="d5b67-281">NuspecBasePath</span><span class="sxs-lookup"><span data-stu-id="d5b67-281">NuspecBasePath</span></span>
<span data-ttu-id="d5b67-282">Temel yolu *.nuspec* dosya.</span><span class="sxs-lookup"><span data-stu-id="d5b67-282">Base path for the *.nuspec* file.</span></span>

### <a name="nuspecproperties"></a><span data-ttu-id="d5b67-283">NuspecProperties</span><span class="sxs-lookup"><span data-stu-id="d5b67-283">NuspecProperties</span></span>
<span data-ttu-id="d5b67-284">Noktalı virgülle ayrılmış listesini anahtar = değer çiftleri.</span><span class="sxs-lookup"><span data-stu-id="d5b67-284">Semicolon separated list of key=value pairs.</span></span>
