---
title: .NET Core csproj biçimine eklemeler
description: Varolan ve .NET Core csproj dosyalarına arasındaki farklar hakkında bilgi edinin
author: blackdwarf
ms.author: mairaw
ms.date: 09/22/2017
ms.openlocfilehash: d868eb689af1d87ea2adb1f0069345cbb8195af7
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2018
ms.locfileid: "45646382"
---
# <a name="additions-to-the-csproj-format-for-net-core"></a><span data-ttu-id="6e36f-103">.NET Core csproj biçimine eklemeler</span><span class="sxs-lookup"><span data-stu-id="6e36f-103">Additions to the csproj format for .NET Core</span></span>

<span data-ttu-id="6e36f-104">Bu belge proje dosyaları taşımak bir parçası olarak eklenmiş olan değişiklikler özetlenmektedir *project.json* için *csproj* ve [MSBuild](https://github.com/Microsoft/MSBuild).</span><span class="sxs-lookup"><span data-stu-id="6e36f-104">This document outlines the changes that were added to the project files as part of the move from *project.json* to *csproj* and [MSBuild](https://github.com/Microsoft/MSBuild).</span></span> <span data-ttu-id="6e36f-105">Genel proje dosyasının söz dizimi ve başvurusu hakkında daha fazla bilgi için bkz: [MSBuild proje dosyası](/visualstudio/msbuild/msbuild-project-file-schema-reference) belgeleri.</span><span class="sxs-lookup"><span data-stu-id="6e36f-105">For more information about general project file syntax and reference, see [the MSBuild project file](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation.</span></span>  

## <a name="implicit-package-references"></a><span data-ttu-id="6e36f-106">Örtük paket başvuruları</span><span class="sxs-lookup"><span data-stu-id="6e36f-106">Implicit package references</span></span>
<span data-ttu-id="6e36f-107">Meta paketler dolaylı olarak başvurulan belirtilen hedef çerçeveleri göre `<TargetFramework>` veya `<TargetFrameworks>` proje dosyanızın özelliği.</span><span class="sxs-lookup"><span data-stu-id="6e36f-107">Metapackages are implicitly referenced based on the target framework(s) specified in the `<TargetFramework>` or `<TargetFrameworks>` property of your project file.</span></span> <span data-ttu-id="6e36f-108">`<TargetFrameworks>` yoksayılır `<TargetFramework>` olduğu belirtildiğinde, sipariş bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="6e36f-108">`<TargetFrameworks>` is ignored if `<TargetFramework>` is specified, independent of order.</span></span>

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

### <a name="recommendations"></a><span data-ttu-id="6e36f-109">Önerileri</span><span class="sxs-lookup"><span data-stu-id="6e36f-109">Recommendations</span></span>
<span data-ttu-id="6e36f-110">Bu yana `Microsoft.NETCore.App` veya `NetStandard.Library` meta paketler dolaylı olarak başvurulan, önerilen en iyi yöntemlerimizi aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="6e36f-110">Since `Microsoft.NETCore.App` or `NetStandard.Library` metapackages are implicitly referenced, the following are our recommended best practices:</span></span>

* <span data-ttu-id="6e36f-111">.NET Core veya .NET Standard hedeflenirken açık bir başvuru hiçbir zaman sahip `Microsoft.NETCore.App` veya `NetStandard.Library` meta paketler aracılığıyla bir `<PackageReference>` proje dosyanızda öğesi.</span><span class="sxs-lookup"><span data-stu-id="6e36f-111">When targeting .NET Core or .NET Standard, never have an explicit reference to the `Microsoft.NETCore.App` or `NetStandard.Library` metapackages via a `<PackageReference>` item in your project file.</span></span>
* <span data-ttu-id="6e36f-112">.NET Core'u hedefleyen, belirli bir çalışma zamanı sürümünü gerekiyorsa kullanmalısınız `<RuntimeFrameworkVersion>` projenizdeki özelliği (örneğin, `1.0.4`) metapackage başvuran yerine.</span><span class="sxs-lookup"><span data-stu-id="6e36f-112">If you need a specific version of the runtime when targeting .NET Core, you should use the `<RuntimeFrameworkVersion>` property in your project (for example, `1.0.4`) instead of referencing the metapackage.</span></span>
    * <span data-ttu-id="6e36f-113">Kullanıyorsanız gerçekleşebilir [müstakil dağıtımları](../deploying/index.md#self-contained-deployments-scd) 1.0.0 belirli bir düzeltme eki sürümü ihtiyacınız ve örneğin LTS çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="6e36f-113">This might happen if you are using [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) and you need a specific patch version of 1.0.0 LTS runtime, for example.</span></span>
* <span data-ttu-id="6e36f-114">Belirli bir sürümünü gerekiyorsa `NetStandard.Library` kullanabileceğiniz .NET Standard hedeflenirken metapackage `<NetStandardImplicitPackageVersion>` özelliği ve kümesi sürümü ihtiyacınız.</span><span class="sxs-lookup"><span data-stu-id="6e36f-114">If you need a specific version of the `NetStandard.Library` metapackage when targeting .NET Standard, you can use the `<NetStandardImplicitPackageVersion>` property and set the version you need.</span></span>
* <span data-ttu-id="6e36f-115">Açıkça eklemeyin veya güncelleştirme ya da başvuruları `Microsoft.NETCore.App` veya `NetStandard.Library` metapackage .NET Framework projelerindeki.</span><span class="sxs-lookup"><span data-stu-id="6e36f-115">Don't explicitly add or update references to either the `Microsoft.NETCore.App` or `NetStandard.Library` metapackage in .NET Framework projects.</span></span> <span data-ttu-id="6e36f-116">Herhangi bir sürümünü `NetStandard.Library` NuGet bir .NET Standard tabanlı NuGet paketini otomatik olarak kullanarak bu sürümü yüklendiğinde gereklidir.</span><span class="sxs-lookup"><span data-stu-id="6e36f-116">If any version of `NetStandard.Library` is needed when using a .NET Standard-based NuGet package, NuGet automatically installs that version.</span></span>

## <a name="default-compilation-includes-in-net-core-projects"></a><span data-ttu-id="6e36f-117">.NET Core projelerinde varsayılan derleme içerir</span><span class="sxs-lookup"><span data-stu-id="6e36f-117">Default compilation includes in .NET Core projects</span></span>
<span data-ttu-id="6e36f-118">Git ile *csproj* biçimi en son SDK sürümlerinde, varsayılan içerir ve derleme öğeleri ve SDK'sı özellikleri dosyalarının gömülü kaynaklar için dışlar Taşındık.</span><span class="sxs-lookup"><span data-stu-id="6e36f-118">With the move to the *csproj* format in the latest SDK versions, we've moved the default includes and excludes for compile items and embedded resources to the SDK properties files.</span></span> <span data-ttu-id="6e36f-119">Bu, artık bu öğeler, proje dosyanızda belirtmek gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="6e36f-119">This means that you no longer need to specify these items in your project file.</span></span> 

<span data-ttu-id="6e36f-120">Bunu yapmak için ana nedeni, proje dosyanızda dağınıklık azaltmaktır.</span><span class="sxs-lookup"><span data-stu-id="6e36f-120">The main reason for doing this is to reduce the clutter in your project file.</span></span> <span data-ttu-id="6e36f-121">Oluşturduğunuz her projede tekrarlamanız gerekmez. Bu nedenle en yaygın kullanım örnekleri, SDK'da bulunan Varsayılanları kapsamalıdır.</span><span class="sxs-lookup"><span data-stu-id="6e36f-121">The defaults that are present in the SDK should cover most common use cases, so there is no need to repeat them in every project that you create.</span></span> <span data-ttu-id="6e36f-122">Bu, gerekirse yanı sıra anlamak, el ile düzenlemek çok daha kolay olan daha küçük proje dosyaları için yol açar.</span><span class="sxs-lookup"><span data-stu-id="6e36f-122">This leads to smaller project files that are much easier to understand as well as edit by hand, if needed.</span></span> 

<span data-ttu-id="6e36f-123">Aşağıdaki tablo, hangi öğe ve hangi gösterir [eğik çizgi genelleştirmeler](https://en.wikipedia.org/wiki/Glob_(programming)) her ikisi de dahil ve hariç SDK'yı:</span><span class="sxs-lookup"><span data-stu-id="6e36f-123">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are both included and excluded in the SDK:</span></span> 

| <span data-ttu-id="6e36f-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="6e36f-124">Element</span></span>           | <span data-ttu-id="6e36f-125">Glob içerir</span><span class="sxs-lookup"><span data-stu-id="6e36f-125">Include glob</span></span>                              | <span data-ttu-id="6e36f-126">Glob Dışla</span><span class="sxs-lookup"><span data-stu-id="6e36f-126">Exclude glob</span></span>                                                  | <span data-ttu-id="6e36f-127">Glob Kaldır</span><span class="sxs-lookup"><span data-stu-id="6e36f-127">Remove glob</span></span>                |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| <span data-ttu-id="6e36f-128">Derleme</span><span class="sxs-lookup"><span data-stu-id="6e36f-128">Compile</span></span>           | <span data-ttu-id="6e36f-129">\*\*/\*.cs (veya diğer dil uzantıları)</span><span class="sxs-lookup"><span data-stu-id="6e36f-129">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="6e36f-130">\*\*/\*.user;  \*\*/\*.\* Proj;  \* \* / \*.sln;  \* \* / \*.vssscc</span><span class="sxs-lookup"><span data-stu-id="6e36f-130">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="6e36f-131">Yok</span><span class="sxs-lookup"><span data-stu-id="6e36f-131">N/A</span></span>                        |
| <span data-ttu-id="6e36f-132">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="6e36f-132">EmbeddedResource</span></span>  | <span data-ttu-id="6e36f-133">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="6e36f-133">\*\*/\*.resx</span></span>                              | <span data-ttu-id="6e36f-134">\*\*/\*.user; \*\*/\*.\* Proj; \* \* / \*.sln; \* \* / \*.vssscc</span><span class="sxs-lookup"><span data-stu-id="6e36f-134">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="6e36f-135">Yok</span><span class="sxs-lookup"><span data-stu-id="6e36f-135">N/A</span></span>                        |
| <span data-ttu-id="6e36f-136">Yok.</span><span class="sxs-lookup"><span data-stu-id="6e36f-136">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="6e36f-137">\*\*/\*.user; \*\*/\*.\* Proj; \* \* / \*.sln; \* \* / \*.vssscc</span><span class="sxs-lookup"><span data-stu-id="6e36f-137">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="6e36f-138">- \*\*/\*.cs; \* \* / \*.resx</span><span class="sxs-lookup"><span data-stu-id="6e36f-138">- \*\*/\*.cs; \*\*/\*.resx</span></span> |

<span data-ttu-id="6e36f-139">Projenizde eğik çizgi genelleştirmeler sahip ve en son SDK'sını kullanarak oluşturmaya çalışırsanız, aşağıdaki hatayı alırsınız:</span><span class="sxs-lookup"><span data-stu-id="6e36f-139">If you have globs in your project and you try to build it using the newest SDK, you'll get the following error:</span></span>

> <span data-ttu-id="6e36f-140">Yinelenen Derleme öğeleri dahil.</span><span class="sxs-lookup"><span data-stu-id="6e36f-140">Duplicate Compile items were included.</span></span> <span data-ttu-id="6e36f-141">.NET SDK'sı varsayılan olarak, proje dizinine derleme öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="6e36f-141">The .NET SDK includes Compile items from your project directory by default.</span></span> <span data-ttu-id="6e36f-142">Bu öğeler proje dosyanızdan kaldırın ya da proje dosyanızda bunları açıkça eklemek istiyorsanız 'EnableDefaultCompileItems' özelliği 'false' ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6e36f-142">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span> 

<span data-ttu-id="6e36f-143">Bu hataya almak için ya da açık kaldırabilirsiniz `Compile` olanlarla eşleşmesi öğeleri önceki tabloda listelenen veya ayarlayabilirsiniz `<EnableDefaultCompileItems>` özelliğini `false`, şöyle:</span><span class="sxs-lookup"><span data-stu-id="6e36f-143">In order to get around this error, you can either remove the explicit `Compile` items that match the ones listed on the previous table, or you can set the `<EnableDefaultCompileItems>` property to `false`, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```
<span data-ttu-id="6e36f-144">Bu özelliği ayarlamak `false` örtük ekleme geçersiz kılar ve davranışı burada b varsayılan eğik çizgi genelleştirmeler projenizde belirlemek için önceki SDK'lar geri döner.</span><span class="sxs-lookup"><span data-stu-id="6e36f-144">Setting this property to `false` will override implicit inclusion and the behavior will revert back to the previous SDKs where you had to specify the default globs in your project.</span></span> 

<span data-ttu-id="6e36f-145">Bu değişiklik, ana değiştirmez, diğer mekanizması içerir.</span><span class="sxs-lookup"><span data-stu-id="6e36f-145">This change does not modify the main mechanics of other includes.</span></span> <span data-ttu-id="6e36f-146">Örneğin, uygulamanız ile yayımlanan için bazı dosyaları belirtmek istiyorsanız ancak içinde bilinen mekanizmaları kullanmaya devam edebilirsiniz *csproj* söz konusu (örneğin, `<Content>` öğesi).</span><span class="sxs-lookup"><span data-stu-id="6e36f-146">However, if you wish to specify, for example, some files to get published with your app, you can still use the known mechanisms in *csproj* for that (for example, the `<Content>` element).</span></span>

<span data-ttu-id="6e36f-147">`<EnableDefaultCompileItems>` yalnızca devre dışı bırakır `Compile` eğik çizgi genelleştirmeler diğer eğik çizgi genelleştirmeler, örtük gibi etkilemez ancak `None` için de geçerli glob \*.cs öğeleri.</span><span class="sxs-lookup"><span data-stu-id="6e36f-147">`<EnableDefaultCompileItems>` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob, which also applies to \*.cs items.</span></span> <span data-ttu-id="6e36f-148">Nedeniyle **Çözüm Gezgini** show devam edecek \*.cs öğeleri dahil, bir projenin parçası olarak `None` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="6e36f-148">Because of that, **Solution Explorer** will continue show \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="6e36f-149">Benzer şekilde, kullandığınız `<EnableDefaultNoneItems>` örtük devre dışı bırakmak için `None` glob.</span><span class="sxs-lookup"><span data-stu-id="6e36f-149">In a similar way, you can use `<EnableDefaultNoneItems>` to disable the implicit `None` glob.</span></span>

<span data-ttu-id="6e36f-150">Devre dışı bırakmak için **tüm örtük eğik çizgi genelleştirmeler**, ayarlayabileceğiniz `<EnableDefaultItems>` özelliğini `false` aşağıdaki örnekteki gibi:</span><span class="sxs-lookup"><span data-stu-id="6e36f-150">To disable **all implicit globs**, you can set the `<EnableDefaultItems>` property to `false` as in the following example:</span></span>
```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

### <a name="recommendation"></a><span data-ttu-id="6e36f-151">Öneri</span><span class="sxs-lookup"><span data-stu-id="6e36f-151">Recommendation</span></span>
<span data-ttu-id="6e36f-152">Csproj ile varsayılan eğik çizgi genelleştirmeler projenizden kaldırmak ve eğik çizgi genelleştirmeler için çeşitli senaryolar için (örneğin, çalışma zamanı ve NuGet paket) uygulamasını/kitaplık gerektiren yapıların ile dosya yolları yalnızca ekleme öneririz.</span><span class="sxs-lookup"><span data-stu-id="6e36f-152">With csproj, we recommend that you remove the default globs from your project and only add file paths with globs for those artifacts that your app/library needs for various scenarios (for example, runtime and NuGet packaging).</span></span>

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a><span data-ttu-id="6e36f-153">MSBuild gördüğünde gibi tüm proje görme</span><span class="sxs-lookup"><span data-stu-id="6e36f-153">How to see the whole project as MSBuild sees it</span></span>

<span data-ttu-id="6e36f-154">Csproj değişiklikleri proje dosyaları büyük ölçüde basitleştirme olsa da, SDK ve hedeflerine dahil olduğunda gördüğünde MSBuild gibi tam olarak genişletilmiş proje görmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e36f-154">While those csproj changes greatly simplify project files, you might want to see the fully expanded project as MSBuild sees it once the SDK and its targets are included.</span></span> <span data-ttu-id="6e36f-155">Projeyle önişle [ `/pp` geçiş](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) , [ `dotnet msbuild` ](dotnet-msbuild.md) komutunu Katkıları derleme için hangi dosyaların içeri aktarılan hangi gösterir ve kaynakları gerçekten Proje oluşturma:</span><span class="sxs-lookup"><span data-stu-id="6e36f-155">Preprocess the project with [the `/pp` switch](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) of the [`dotnet msbuild`](dotnet-msbuild.md) command, which shows which files are imported, their sources, and their contributions to the build without actually building the project:</span></span>

`dotnet msbuild /pp:fullproject.xml`

<span data-ttu-id="6e36f-156">Birden çok hedef çerçeve proje varsa komutun sonuçlarını yalnızca bunlardan birine bir MSBuild özellik olarak belirterek odaklanmış olur:</span><span class="sxs-lookup"><span data-stu-id="6e36f-156">If the project has multiple target frameworks, the results of the command should be focused on only one of them by specifying it as an MSBuild property:</span></span>

`dotnet msbuild /p:TargetFramework=netcoreapp2.0 /pp:fullproject.xml`

## <a name="additions"></a><span data-ttu-id="6e36f-157">Eklemeleri</span><span class="sxs-lookup"><span data-stu-id="6e36f-157">Additions</span></span>

### <a name="sdk-attribute"></a><span data-ttu-id="6e36f-158">SDK'sı özniteliği</span><span class="sxs-lookup"><span data-stu-id="6e36f-158">Sdk attribute</span></span> 
<span data-ttu-id="6e36f-159">`<Project>` Öğesinin *.csproj* dosya adlı yeni bir öznitelik sahip `Sdk`.</span><span class="sxs-lookup"><span data-stu-id="6e36f-159">The `<Project>` element of the *.csproj* file has a new attribute called `Sdk`.</span></span> <span data-ttu-id="6e36f-160">`Sdk` SDK'sı olacağı belirtir proje tarafından kullanılan.</span><span class="sxs-lookup"><span data-stu-id="6e36f-160">`Sdk` specifies which SDK will be used by the project.</span></span> <span data-ttu-id="6e36f-161">SDK'sı olarak [katmanlama belge](cli-msbuild-architecture.md) açıklar, MSBuild kümesidir [görevleri](/visualstudio/msbuild/msbuild-tasks) ve [hedefleri](/visualstudio/msbuild/msbuild-targets) .NET Core kod oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e36f-161">The SDK, as the [layering document](cli-msbuild-architecture.md) describes, is a set of MSBuild [tasks](/visualstudio/msbuild/msbuild-tasks) and [targets](/visualstudio/msbuild/msbuild-targets) that can build .NET Core code.</span></span> <span data-ttu-id="6e36f-162">Biz, .NET Core araçları ile iki ana SDK'ları gönderin:</span><span class="sxs-lookup"><span data-stu-id="6e36f-162">We ship two main SDKs with the .NET Core tools:</span></span>

1. <span data-ttu-id="6e36f-163">.NET Core SDK kimliği `Microsoft.NET.Sdk`</span><span class="sxs-lookup"><span data-stu-id="6e36f-163">The .NET Core SDK with the ID of `Microsoft.NET.Sdk`</span></span>
2. <span data-ttu-id="6e36f-164">.NET Core web SDK kimliği `Microsoft.NET.Sdk.Web`</span><span class="sxs-lookup"><span data-stu-id="6e36f-164">The .NET Core web SDK with the ID of `Microsoft.NET.Sdk.Web`</span></span>

<span data-ttu-id="6e36f-165">İhtiyacınız `Sdk` öznitelik kümesi bu kimlikler birine üzerinde `<Project>` .NET Core araçları kullanın ve kodu derleyebilmeniz için öğesi.</span><span class="sxs-lookup"><span data-stu-id="6e36f-165">You need to have the `Sdk` attribute set to one of those IDs on the `<Project>` element in order to use the .NET Core tools and build your code.</span></span> 

### <a name="packagereference"></a><span data-ttu-id="6e36f-166">PackageReference</span><span class="sxs-lookup"><span data-stu-id="6e36f-166">PackageReference</span></span>
<span data-ttu-id="6e36f-167">Öğesi projedeki NuGet bağımlılık belirtir.</span><span class="sxs-lookup"><span data-stu-id="6e36f-167">Item that specifies a NuGet dependency in the project.</span></span> <span data-ttu-id="6e36f-168">`Include` Özniteliği paket kimliğini belirtir</span><span class="sxs-lookup"><span data-stu-id="6e36f-168">The `Include` attribute specifies the package ID.</span></span> 

```xml
<PackageReference Include="<package-id>" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a><span data-ttu-id="6e36f-169">Sürüm</span><span class="sxs-lookup"><span data-stu-id="6e36f-169">Version</span></span>
<span data-ttu-id="6e36f-170">`Version` geri yüklemek için paket sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="6e36f-170">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="6e36f-171">Öznitelik kurallarına uyar [NuGet sürüm](/nuget/create-packages/dependency-versions#version-ranges) düzeni.</span><span class="sxs-lookup"><span data-stu-id="6e36f-171">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="6e36f-172">Bir tam sürüm eşleşiyorsa varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="6e36f-172">The default behavior is an exact version match.</span></span> <span data-ttu-id="6e36f-173">Örneğin, belirten `Version="1.2.3"` NuGet gösterimine eşdeğerdir `[1.2.3]` tam 1.2.3-Beta için Paket sürümü.</span><span class="sxs-lookup"><span data-stu-id="6e36f-173">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

#### <a name="includeassets-excludeassets-and-privateassets"></a><span data-ttu-id="6e36f-174">IncludeAssets ve ExcludeAssets PrivateAssets</span><span class="sxs-lookup"><span data-stu-id="6e36f-174">IncludeAssets, ExcludeAssets and PrivateAssets</span></span>
<span data-ttu-id="6e36f-175">`IncludeAssets` öznitelik belirtir pakete ait varlıklar tarafından belirtilen `<PackageReference>` kullanılması.</span><span class="sxs-lookup"><span data-stu-id="6e36f-175">`IncludeAssets` attribute specifies what assets belonging to the package specified by `<PackageReference>` should be consumed.</span></span> 

<span data-ttu-id="6e36f-176">`ExcludeAssets` öznitelik belirtir pakete ait varlıklar tarafından belirtilen `<PackageReference>` değil kullanılması.</span><span class="sxs-lookup"><span data-stu-id="6e36f-176">`ExcludeAssets` attribute specifies what assets belonging to the package specified by `<PackageReference>` should not be consumed.</span></span>

<span data-ttu-id="6e36f-177">`PrivateAssets` öznitelik belirtir pakete ait varlıklar tarafından belirtilen `<PackageReference>` bunlar sonraki projeye akmaması gerektiğini ancak kullanılması.</span><span class="sxs-lookup"><span data-stu-id="6e36f-177">`PrivateAssets` attribute specifies what assets belonging to the package specified by `<PackageReference>` should be consumed but that they should not flow to the next project.</span></span> 

> [!NOTE]
> <span data-ttu-id="6e36f-178">`PrivateAssets` eşdeğerdir *project.json*/*xproj* `SuppressParent` öğesi.</span><span class="sxs-lookup"><span data-stu-id="6e36f-178">`PrivateAssets` is equivalent to the *project.json*/*xproj* `SuppressParent` element.</span></span>

<span data-ttu-id="6e36f-179">Bu öznitelikler, bir veya daha fazla aşağıdaki öğelerden birini içerebilir:</span><span class="sxs-lookup"><span data-stu-id="6e36f-179">These attributes can contain one or more of the following items:</span></span>

* <span data-ttu-id="6e36f-180">`Compile` -lib klasörünün içeriğini karşı derleme kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6e36f-180">`Compile` – the contents of the lib folder are available to compile against.</span></span>
* <span data-ttu-id="6e36f-181">`Runtime` – çalışma zamanı klasörünün içeriğini dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="6e36f-181">`Runtime` – the contents of the runtime folder are distributed.</span></span>
* <span data-ttu-id="6e36f-182">`ContentFiles` – içeriği *contentfiles* klasörü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6e36f-182">`ContentFiles` – the contents of the *contentfiles* folder are used.</span></span>
* <span data-ttu-id="6e36f-183">`Build` – derleme klasörü özellikler/hedeflerin kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6e36f-183">`Build` – the props/targets in the build folder are used.</span></span>
* <span data-ttu-id="6e36f-184">`Native` – içeriği yerel varlıklar, çalışma zamanı için çıktı klasörüne kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="6e36f-184">`Native` – the contents from native assets are copied to the output folder for runtime.</span></span>
* <span data-ttu-id="6e36f-185">`Analyzers` – Çözümleyicileri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6e36f-185">`Analyzers` – the analyzers are used.</span></span>

<span data-ttu-id="6e36f-186">Alternatif olarak, öznitelik içerebilir:</span><span class="sxs-lookup"><span data-stu-id="6e36f-186">Alternatively, the attribute can contain:</span></span>

* <span data-ttu-id="6e36f-187">`None` – varlıkları hiçbiri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6e36f-187">`None` – none of the assets are used.</span></span>
* <span data-ttu-id="6e36f-188">`All` – tüm varlıkları kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6e36f-188">`All` – all assets are used.</span></span>

### <a name="dotnetclitoolreference"></a><span data-ttu-id="6e36f-189">DotNetCliToolReference</span><span class="sxs-lookup"><span data-stu-id="6e36f-189">DotNetCliToolReference</span></span>
<span data-ttu-id="6e36f-190">`<DotNetCliToolReference>` öğe unsuru kullanıcının proje bağlamında geri yüklemek için istediği CLI aracı belirtir.</span><span class="sxs-lookup"><span data-stu-id="6e36f-190">`<DotNetCliToolReference>` item element specifies the CLI tool that the user wants to restore in the context of the project.</span></span> <span data-ttu-id="6e36f-191">Bir ardılı olan `tools` düğümünde *project.json*.</span><span class="sxs-lookup"><span data-stu-id="6e36f-191">It's a replacement for the `tools` node in *project.json*.</span></span> 

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

#### <a name="version"></a><span data-ttu-id="6e36f-192">Sürüm</span><span class="sxs-lookup"><span data-stu-id="6e36f-192">Version</span></span>
<span data-ttu-id="6e36f-193">`Version` geri yüklemek için paket sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="6e36f-193">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="6e36f-194">Öznitelik kurallarına uyar [NuGet sürüm](/nuget/create-packages/dependency-versions#version-ranges) düzeni.</span><span class="sxs-lookup"><span data-stu-id="6e36f-194">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="6e36f-195">Bir tam sürüm eşleşiyorsa varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="6e36f-195">The default behavior is an exact version match.</span></span> <span data-ttu-id="6e36f-196">Örneğin, belirten `Version="1.2.3"` NuGet gösterimine eşdeğerdir `[1.2.3]` tam 1.2.3-Beta için Paket sürümü.</span><span class="sxs-lookup"><span data-stu-id="6e36f-196">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

### <a name="runtimeidentifiers"></a><span data-ttu-id="6e36f-197">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="6e36f-197">RuntimeIdentifiers</span></span>
<span data-ttu-id="6e36f-198">`<RuntimeIdentifiers>` Öğesi noktalı virgülle ayrılmış bir listesini belirtmenize olanak tanır [çalışma zamanı tanımlayıcılarının (RID'ler)](../rid-catalog.md) projesi için.</span><span class="sxs-lookup"><span data-stu-id="6e36f-198">The `<RuntimeIdentifiers>` element lets you specify a semicolon-delimited list of [Runtime Identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="6e36f-199">Bağımsız dağıtımlar yayımlama RID'ler etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="6e36f-199">RIDs enable publishing a self-contained deployments.</span></span> 

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a><span data-ttu-id="6e36f-200">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="6e36f-200">RuntimeIdentifier</span></span>
<span data-ttu-id="6e36f-201">`<RuntimeIdentifier>` Öğesi yalnızca bir belirtmenize olanak verir [çalışma zamanı tanımlayıcı (RID)](../rid-catalog.md) projesi için.</span><span class="sxs-lookup"><span data-stu-id="6e36f-201">The `<RuntimeIdentifier>` element allows you to specify only one [Runtime Identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="6e36f-202">RID kendi içinde bir dağıtım yayımlamayı etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="6e36f-202">RIDs enable publishing a self-contained deployment.</span></span> 

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

### <a name="packagetargetfallback"></a><span data-ttu-id="6e36f-203">PackageTargetFallback</span><span class="sxs-lookup"><span data-stu-id="6e36f-203">PackageTargetFallback</span></span> 
<span data-ttu-id="6e36f-204">`<PackageTargetFallback>` Öğesi, bir dizi paketler geri yüklenirken kullanılacak uyumlu hedefleri belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="6e36f-204">The `<PackageTargetFallback>` element allows you to specify a set of compatible targets to be used when restoring packages.</span></span> <span data-ttu-id="6e36f-205">Dotnet kullanan paketleri izin vermek için tasarlanmış [TxM (x hedef ad)](/nuget/schema/target-frameworks) bir dotnet TxM bildirmeyin paketlerle çalışılacak.</span><span class="sxs-lookup"><span data-stu-id="6e36f-205">It's designed to allow packages that use the dotnet [TxM (Target x Moniker)](/nuget/schema/target-frameworks) to operate with packages that don't declare a dotnet TxM.</span></span> <span data-ttu-id="6e36f-206">Projenizin kullandığı dotnet TxM sonra eklediğiniz sürece bir dotnet TxM, duruma göre değişir üzerinde gerekir ayrıca tüm paketlere sahip `<PackageTargetFallback>` dotnet ile uyumlu olacak şekilde dotnet olmayan platformlar için projenize.</span><span class="sxs-lookup"><span data-stu-id="6e36f-206">If your project uses the dotnet TxM, then all the packages it depends on must also have a dotnet TxM, unless you add the `<PackageTargetFallback>` to your project in order to allow non-dotnet platforms to be compatible with dotnet.</span></span> 

<span data-ttu-id="6e36f-207">Aşağıdaki örnek, projenizdeki tüm hedefleri için geri dönüşler sağlar:</span><span class="sxs-lookup"><span data-stu-id="6e36f-207">The following example provides the fallbacks for all targets in your project:</span></span> 

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

<span data-ttu-id="6e36f-208">Aşağıdaki örnek, geri dönüşler yalnızca belirtir `netcoreapp2.1` hedef:</span><span class="sxs-lookup"><span data-stu-id="6e36f-208">The following example specifies the fallbacks only for the `netcoreapp2.1` target:</span></span>

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp2.1'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="nuget-metadata-properties"></a><span data-ttu-id="6e36f-209">NuGet meta veri özelliklerini</span><span class="sxs-lookup"><span data-stu-id="6e36f-209">NuGet metadata properties</span></span>
<span data-ttu-id="6e36f-210">MSbuild için taşıma ile NuGet paketinden paketleme sırasında kullanılan giriş meta verileri geçtiğimizi *project.json* için *.csproj* dosyaları.</span><span class="sxs-lookup"><span data-stu-id="6e36f-210">With the move to MSbuild, we have moved the input metadata that is used when packing a NuGet package from *project.json* to *.csproj* files.</span></span> <span data-ttu-id="6e36f-211">Kullanıcılarınızın içinde gitmek zorunda MSBuild özellikleri girişleri bir `<PropertyGroup>` grubu.</span><span class="sxs-lookup"><span data-stu-id="6e36f-211">The inputs are MSBuild properties so they have to go within a `<PropertyGroup>` group.</span></span> <span data-ttu-id="6e36f-212">Paketleme işleminin girdi olarak kullanılırken kullanılacak özellikleri listesi aşağıdadır `dotnet pack` komutu veya `Pack` MSBuild hedef diğer bir deyişle SDK'ın bir parçası.</span><span class="sxs-lookup"><span data-stu-id="6e36f-212">The following is the list of properties that are used as inputs to the packing process when using the `dotnet pack` command or the `Pack` MSBuild target that is part of the SDK.</span></span> 

### <a name="ispackable"></a><span data-ttu-id="6e36f-213">IsPackable</span><span class="sxs-lookup"><span data-stu-id="6e36f-213">IsPackable</span></span>
<span data-ttu-id="6e36f-214">Proje paketlenmiş olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="6e36f-214">A Boolean value that specifies whether the project can be packed.</span></span> <span data-ttu-id="6e36f-215">Varsayılan değer `true` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6e36f-215">The default value is `true`.</span></span> 

### <a name="packageversion"></a><span data-ttu-id="6e36f-216">PackageVersion</span><span class="sxs-lookup"><span data-stu-id="6e36f-216">PackageVersion</span></span>
<span data-ttu-id="6e36f-217">Sonuç paketine sahip olacak sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="6e36f-217">Specifies the version that the resulting package will have.</span></span> <span data-ttu-id="6e36f-218">NuGet sürüm dizesinin tüm forms kabul eder.</span><span class="sxs-lookup"><span data-stu-id="6e36f-218">Accepts all forms of NuGet version string.</span></span> <span data-ttu-id="6e36f-219">Varsayılan değer değeri `$(Version)`, diğer bir deyişle, özelliğin `Version` projedeki.</span><span class="sxs-lookup"><span data-stu-id="6e36f-219">Default is the value of `$(Version)`, that is, of the property `Version` in the project.</span></span> 

### <a name="packageid"></a><span data-ttu-id="6e36f-220">PackageId</span><span class="sxs-lookup"><span data-stu-id="6e36f-220">PackageId</span></span>
<span data-ttu-id="6e36f-221">Sonuçta elde edilen paket adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6e36f-221">Specifies the name for the resulting package.</span></span> <span data-ttu-id="6e36f-222">Belirtilmezse, `pack` işlemi için kullanılacak varsayılan `AssemblyName` veya dizin adı olarak paketin adı.</span><span class="sxs-lookup"><span data-stu-id="6e36f-222">If not specified, the `pack` operation will default to using the `AssemblyName` or directory name as the name of the package.</span></span> 

### <a name="title"></a><span data-ttu-id="6e36f-223">Başlık</span><span class="sxs-lookup"><span data-stu-id="6e36f-223">Title</span></span>
<span data-ttu-id="6e36f-224">Nuget.org ve Visual Studio'da Paket Yöneticisi UI görünümlerde genellikle kullanılan paket bir insan dostu başlığı.</span><span class="sxs-lookup"><span data-stu-id="6e36f-224">A human-friendly title of the package, typically used in UI displays as on nuget.org and the Package Manager in Visual Studio.</span></span> <span data-ttu-id="6e36f-225">Belirtilmezse, paket kimliği yerine kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6e36f-225">If not specified, the package ID is used instead.</span></span>

### <a name="authors"></a><span data-ttu-id="6e36f-226">Yazarlar</span><span class="sxs-lookup"><span data-stu-id="6e36f-226">Authors</span></span>
<span data-ttu-id="6e36f-227">Nuget.org profil adları eşleşen paketleri yazar, noktalı virgülle ayrılmış listesi. Bunlar nuget.org NuGet galerisinde görüntülenir ve paketleri çapraz başvuru için aynı yazarları tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6e36f-227">A semicolon-separated list of packages authors, matching the profile names on nuget.org. These are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span>

### <a name="description"></a><span data-ttu-id="6e36f-228">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e36f-228">Description</span></span>
<span data-ttu-id="6e36f-229">Kullanıcı Arabirimi ekranı için paketinin uzun açıklaması.</span><span class="sxs-lookup"><span data-stu-id="6e36f-229">A long description of the package for UI display.</span></span>

### <a name="copyright"></a><span data-ttu-id="6e36f-230">Telif Hakkı</span><span class="sxs-lookup"><span data-stu-id="6e36f-230">Copyright</span></span>
<span data-ttu-id="6e36f-231">Paketi için telif hakkı ayrıntıları.</span><span class="sxs-lookup"><span data-stu-id="6e36f-231">Copyright details for the package.</span></span>

### <a name="packagerequirelicenseacceptance"></a><span data-ttu-id="6e36f-232">PackageRequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="6e36f-232">PackageRequireLicenseAcceptance</span></span>
<span data-ttu-id="6e36f-233">İstemci paketi yüklemeden önce paket lisansını kabul etmek için tüketici sor olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="6e36f-233">A Boolean value that specifies whether the client must prompt the consumer to accept the package license before installing the package.</span></span> <span data-ttu-id="6e36f-234">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="6e36f-234">The default is `false`.</span></span>

### <a name="packagelicenseurl"></a><span data-ttu-id="6e36f-235">PackageLicenseUrl</span><span class="sxs-lookup"><span data-stu-id="6e36f-235">PackageLicenseUrl</span></span>
<span data-ttu-id="6e36f-236">Bir paket için uygun olan lisans URL'si.</span><span class="sxs-lookup"><span data-stu-id="6e36f-236">An URL to the license that is applicable to the package.</span></span>

### <a name="packageprojecturl"></a><span data-ttu-id="6e36f-237">PackageProjectUrl</span><span class="sxs-lookup"><span data-stu-id="6e36f-237">PackageProjectUrl</span></span>
<span data-ttu-id="6e36f-238">Genellikle kullanıcı Arabiriminde gösterilir paketin giriş sayfası için bir URL yanı sıra nuget.org görüntüler.</span><span class="sxs-lookup"><span data-stu-id="6e36f-238">A URL for the package's home page, often shown in UI displays as well as nuget.org.</span></span>

### <a name="packageiconurl"></a><span data-ttu-id="6e36f-239">PackageIconUrl</span><span class="sxs-lookup"><span data-stu-id="6e36f-239">PackageIconUrl</span></span>
<span data-ttu-id="6e36f-240">Kullanıcı Arabirimi ekranı pakette için simge olarak kullanılacak bir URL saydam arka plana sahip 64 x 64 görüntüsü.</span><span class="sxs-lookup"><span data-stu-id="6e36f-240">A URL for a 64x64 image with transparent background to use as the icon for the package in UI display.</span></span>

### <a name="packagereleasenotes"></a><span data-ttu-id="6e36f-241">PackageReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="6e36f-241">PackageReleaseNotes</span></span>
<span data-ttu-id="6e36f-242">Paket için sürüm notları.</span><span class="sxs-lookup"><span data-stu-id="6e36f-242">Release notes for the package.</span></span>

### <a name="packagetags"></a><span data-ttu-id="6e36f-243">PackageTags</span><span class="sxs-lookup"><span data-stu-id="6e36f-243">PackageTags</span></span>
<span data-ttu-id="6e36f-244">Etiketleri noktalı virgülle ayrılmış bir listesini, paketi belirler.</span><span class="sxs-lookup"><span data-stu-id="6e36f-244">A semicolon-delimited list of tags that designates the package.</span></span>

### <a name="packageoutputpath"></a><span data-ttu-id="6e36f-245">PackageOutputPath</span><span class="sxs-lookup"><span data-stu-id="6e36f-245">PackageOutputPath</span></span>
<span data-ttu-id="6e36f-246">Paketlenmiş paket bırakılır çıkış yolu belirler.</span><span class="sxs-lookup"><span data-stu-id="6e36f-246">Determines the output path in which the packed package will be dropped.</span></span> <span data-ttu-id="6e36f-247">Varsayılan değer `$(OutputPath)`.</span><span class="sxs-lookup"><span data-stu-id="6e36f-247">Default is `$(OutputPath)`.</span></span> 

### <a name="includesymbols"></a><span data-ttu-id="6e36f-248">IncludeSymbols</span><span class="sxs-lookup"><span data-stu-id="6e36f-248">IncludeSymbols</span></span>
<span data-ttu-id="6e36f-249">Proje dolu olduğunda paketi bir ek sembol paketi oluşturmak bu Boolean değerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6e36f-249">This Boolean value indicates whether the package should create an additional symbols package when the project is packed.</span></span> <span data-ttu-id="6e36f-250">Bu paket olacaktır bir *. symbols.nupkg* uzantısı ve PDB dosyaları DLL ile birlikte ve diğer çıktı dosyalarını kopyalar.</span><span class="sxs-lookup"><span data-stu-id="6e36f-250">This package will have a *.symbols.nupkg* extension and will copy the PDB files along with the DLL and other output files.</span></span>

### <a name="includesource"></a><span data-ttu-id="6e36f-251">IncludeSource</span><span class="sxs-lookup"><span data-stu-id="6e36f-251">IncludeSource</span></span>
<span data-ttu-id="6e36f-252">Paketi işlemi bir kaynak paketi oluşturmanız gerekir, bu Boolean değeri gösterir.</span><span class="sxs-lookup"><span data-stu-id="6e36f-252">This Boolean value indicates whether the pack process should create a source package.</span></span> <span data-ttu-id="6e36f-253">Kaynak Paketi kitaplığın kaynak kodunun yanı sıra PDB dosyaları içerir.</span><span class="sxs-lookup"><span data-stu-id="6e36f-253">The source package contains the library's source code as well as PDB files.</span></span> <span data-ttu-id="6e36f-254">Kaynak dosyaları altında isimlerine `src/ProjectName` elde edilen paket dosyasındaki dizin.</span><span class="sxs-lookup"><span data-stu-id="6e36f-254">Source files are put under the `src/ProjectName` directory in the resulting package file.</span></span> 

### <a name="istool"></a><span data-ttu-id="6e36f-255">IsTool</span><span class="sxs-lookup"><span data-stu-id="6e36f-255">IsTool</span></span>
<span data-ttu-id="6e36f-256">Tüm çıkış dosyalarını kopyalanıp kopyalanmayacağını belirtir *Araçları* klasörü yerine *LIB* klasör.</span><span class="sxs-lookup"><span data-stu-id="6e36f-256">Specifies whether all output files are copied to the *tools* folder instead of the *lib* folder.</span></span> <span data-ttu-id="6e36f-257">Bu farklı olduğunu unutmayın bir `DotNetCliTool` , belirtilen ayarlayarak `PackageType` içinde *.csproj* dosya.</span><span class="sxs-lookup"><span data-stu-id="6e36f-257">Note that this is different from a `DotNetCliTool` which is specified by setting the `PackageType` in the *.csproj* file.</span></span>

### <a name="repositoryurl"></a><span data-ttu-id="6e36f-258">RepositoryUrl</span><span class="sxs-lookup"><span data-stu-id="6e36f-258">RepositoryUrl</span></span>
<span data-ttu-id="6e36f-259">Depo URL'si, paket için kaynak kodu bulunduğu yerde ve/veya hangi, oluşturulmakta olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="6e36f-259">Specifies the URL for the repository where the source code for the package resides and/or from which it's being built.</span></span> 

### <a name="repositorytype"></a><span data-ttu-id="6e36f-260">RepositoryType</span><span class="sxs-lookup"><span data-stu-id="6e36f-260">RepositoryType</span></span>
<span data-ttu-id="6e36f-261">Depo türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="6e36f-261">Specifies the type of the repository.</span></span> <span data-ttu-id="6e36f-262">"Git" varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="6e36f-262">Default is "git".</span></span> 

### <a name="nopackageanalysis"></a><span data-ttu-id="6e36f-263">NoPackageAnalysis</span><span class="sxs-lookup"><span data-stu-id="6e36f-263">NoPackageAnalysis</span></span>
<span data-ttu-id="6e36f-264">Paketi paket analiz paketini oluşturduktan sonra çalışmaması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6e36f-264">Specifies that pack should not run package analysis after building the package.</span></span>

### <a name="minclientversion"></a><span data-ttu-id="6e36f-265">MinClientVersion</span><span class="sxs-lookup"><span data-stu-id="6e36f-265">MinClientVersion</span></span>
<span data-ttu-id="6e36f-266">Nuget.exe ve Visual Studio Paket Yöneticisi tarafından zorlanan, bu paketi yüklemek NuGet istemci en düşük sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="6e36f-266">Specifies the minimum version of the NuGet client that can install this package, enforced by nuget.exe and the Visual Studio Package Manager.</span></span>

### <a name="includebuildoutput"></a><span data-ttu-id="6e36f-267">IncludeBuildOutput</span><span class="sxs-lookup"><span data-stu-id="6e36f-267">IncludeBuildOutput</span></span>
<span data-ttu-id="6e36f-268">Bu Boolean değerleri belirten derleme çıktı derlemeleri halinde paketlenmiş olup olmadığını *.nupkg* dosya ya da değil.</span><span class="sxs-lookup"><span data-stu-id="6e36f-268">This Boolean values specifies whether the build output assemblies should be packed into the *.nupkg* file or not.</span></span>

### <a name="includecontentinpack"></a><span data-ttu-id="6e36f-269">IncludeContentInPack</span><span class="sxs-lookup"><span data-stu-id="6e36f-269">IncludeContentInPack</span></span>
<span data-ttu-id="6e36f-270">Bu Boolean değerini tüm öğeleri, bir türü sahip olup olmadığını belirtir `Content` sonuç paketine otomatik olarak dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="6e36f-270">This Boolean value specifies whether any items that have a type of `Content` will be included in the resulting package automatically.</span></span> <span data-ttu-id="6e36f-271">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="6e36f-271">The default is `true`.</span></span> 

### <a name="buildoutputtargetfolder"></a><span data-ttu-id="6e36f-272">BuildOutputTargetFolder</span><span class="sxs-lookup"><span data-stu-id="6e36f-272">BuildOutputTargetFolder</span></span>
<span data-ttu-id="6e36f-273">Klasörü çıkış derlemelerin yerleştirileceği yeri belirtir.</span><span class="sxs-lookup"><span data-stu-id="6e36f-273">Specifies the folder where to place the output assemblies.</span></span> <span data-ttu-id="6e36f-274">Çıkış bütünleştirilmiş kodları (ve diğer çıktı dosyalarının) ilgili framework klasörlerine kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="6e36f-274">The output assemblies (and other output files) are copied into their respective framework folders.</span></span>

### <a name="contenttargetfolders"></a><span data-ttu-id="6e36f-275">ContentTargetFolders</span><span class="sxs-lookup"><span data-stu-id="6e36f-275">ContentTargetFolders</span></span>
<span data-ttu-id="6e36f-276">Bu özellik tüm içerik dosyalarını, nereye varsayılan konumu belirtir `PackagePath` kendileri için belirtilmedi.</span><span class="sxs-lookup"><span data-stu-id="6e36f-276">This property specifies the default location of where all the content files should go if `PackagePath` is not specified for them.</span></span> <span data-ttu-id="6e36f-277">Varsayılan değer: "içerik; contentFiles".</span><span class="sxs-lookup"><span data-stu-id="6e36f-277">The default value is "content;contentFiles".</span></span>

### <a name="nuspecfile"></a><span data-ttu-id="6e36f-278">NuspecFile</span><span class="sxs-lookup"><span data-stu-id="6e36f-278">NuspecFile</span></span>
<span data-ttu-id="6e36f-279">Göreli veya mutlak yolunu *.nuspec* paketleme için kullanılan dosya.</span><span class="sxs-lookup"><span data-stu-id="6e36f-279">Relative or absolute path to the *.nuspec* file being used for packing.</span></span> 

> [!NOTE]
> <span data-ttu-id="6e36f-280">Varsa *.nuspec* dosya belirtilir, kullanıldığı **özel** için bilgi ve herhangi bir bilgi projelerindeki paketleme kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="6e36f-280">If the *.nuspec* file is specified, it's used **exclusively** for packaging information and any information in the projects is not used.</span></span> 

### <a name="nuspecbasepath"></a><span data-ttu-id="6e36f-281">NuspecBasePath</span><span class="sxs-lookup"><span data-stu-id="6e36f-281">NuspecBasePath</span></span>
<span data-ttu-id="6e36f-282">Temel yolunu *.nuspec* dosya.</span><span class="sxs-lookup"><span data-stu-id="6e36f-282">Base path for the *.nuspec* file.</span></span>

### <a name="nuspecproperties"></a><span data-ttu-id="6e36f-283">NuspecProperties</span><span class="sxs-lookup"><span data-stu-id="6e36f-283">NuspecProperties</span></span>
<span data-ttu-id="6e36f-284">Noktalı virgülle ayrılmış listesi anahtar = değer çiftleri.</span><span class="sxs-lookup"><span data-stu-id="6e36f-284">Semicolon separated list of key=value pairs.</span></span>
