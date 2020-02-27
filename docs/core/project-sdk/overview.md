---
title: .NET Core proje SDK 'sına genel bakış
description: .NET Core proje SDK 'Ları hakkında bilgi edinin.
ms.date: 02/02/2020
ms.topic: conceptual
ms.openlocfilehash: c41b25bf7933e7b1f6cb50da5e52dc0b312f5c74
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626251"
---
# <a name="net-core-project-sdks"></a><span data-ttu-id="6807c-103">.NET Core proje SDK 'Ları</span><span class="sxs-lookup"><span data-stu-id="6807c-103">.NET Core project SDKs</span></span>

<span data-ttu-id="6807c-104">.NET Core projeleri bir yazılım geliştirme seti (SDK) ile ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="6807c-104">.NET Core projects are associated with a software development kit (SDK).</span></span> <span data-ttu-id="6807c-105">Her proje SDK 'Sı, bir dizi MSBuild [hedefi](/visualstudio/msbuild/msbuild-targets) ve kodu derleme, paketleme ve yayımlama ile ilgili [görevlerden](/visualstudio/msbuild/msbuild-tasks) oluşur.</span><span class="sxs-lookup"><span data-stu-id="6807c-105">Each project SDK is a set of MSBuild [targets](/visualstudio/msbuild/msbuild-targets) and associated [tasks](/visualstudio/msbuild/msbuild-tasks) that are responsible for compiling, packing, and publishing code.</span></span>

## <a name="available-sdks"></a><span data-ttu-id="6807c-106">Kullanılabilir SDK 'lar</span><span class="sxs-lookup"><span data-stu-id="6807c-106">Available SDKs</span></span>

<span data-ttu-id="6807c-107">.NET Core için aşağıdaki SDK 'lar mevcuttur:</span><span class="sxs-lookup"><span data-stu-id="6807c-107">The following SDKs are available for .NET Core:</span></span>

| <span data-ttu-id="6807c-108">Kimlik</span><span class="sxs-lookup"><span data-stu-id="6807c-108">ID</span></span> | <span data-ttu-id="6807c-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6807c-109">Description</span></span> | <span data-ttu-id="6807c-110">Depo</span><span class="sxs-lookup"><span data-stu-id="6807c-110">Repo</span></span>|
| - | - | - |
| `Microsoft.NET.Sdk` | <span data-ttu-id="6807c-111">.NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="6807c-111">The .NET Core SDK</span></span> | https://github.com/dotnet/sdk |
| `Microsoft.NET.Sdk.Web` | <span data-ttu-id="6807c-112">.NET Core [Web SDK 'sı](/aspnet/core/razor-pages/web-sdk)</span><span class="sxs-lookup"><span data-stu-id="6807c-112">The .NET Core [Web SDK](/aspnet/core/razor-pages/web-sdk)</span></span> | https://github.com/aspnet/websdk |
| `Microsoft.NET.Sdk.Razor` | <span data-ttu-id="6807c-113">.NET Core [Razor SDK 'sı](/aspnet/core/razor-pages/sdk)</span><span class="sxs-lookup"><span data-stu-id="6807c-113">The .NET Core [Razor SDK](/aspnet/core/razor-pages/sdk)</span></span> |
| `Microsoft.NET.Sdk.Worker` | <span data-ttu-id="6807c-114">.NET Core Worker hizmeti SDK 'Sı</span><span class="sxs-lookup"><span data-stu-id="6807c-114">The .NET Core Worker Service SDK</span></span> |
| `Microsoft.NET.Sdk.WindowsDesktop` | <span data-ttu-id="6807c-115">.NET Core WinForms ve WPF SDK</span><span class="sxs-lookup"><span data-stu-id="6807c-115">The .NET Core WinForms and WPF SDK</span></span> |

<span data-ttu-id="6807c-116">.NET Core SDK, .NET Core için temel SDK 'dir.</span><span class="sxs-lookup"><span data-stu-id="6807c-116">The .NET Core SDK is the base SDK for .NET Core.</span></span> <span data-ttu-id="6807c-117">Diğer SDK 'lar .NET Core SDK başvuruda bulunur ve diğer SDK 'lar ile ilişkili projeler için kullanılabilen tüm .NET Core SDK özellikleri vardır.</span><span class="sxs-lookup"><span data-stu-id="6807c-117">The other SDKs reference the .NET Core SDK, and projects that are associated with the other SDKs have all the .NET Core SDK properties available to them.</span></span> <span data-ttu-id="6807c-118">Örneğin, Web SDK 'Sı, hem .NET Core SDK hem de Razor SDK 'sına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="6807c-118">The Web SDK, for example, depends on both the .NET Core SDK and the Razor SDK.</span></span>

<span data-ttu-id="6807c-119">Ayrıca kendi SDK 'nizi, NuGet aracılığıyla dağıtılabilecek şekilde yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6807c-119">You can also author your own SDK that can be distributed via NuGet.</span></span>

## <a name="project-files"></a><span data-ttu-id="6807c-120">Proje dosyaları</span><span class="sxs-lookup"><span data-stu-id="6807c-120">Project files</span></span>

<span data-ttu-id="6807c-121">.NET Core projeleri [MSBuild](/visualstudio/msbuild/msbuild) biçimine dayanır.</span><span class="sxs-lookup"><span data-stu-id="6807c-121">.NET Core projects are based on the [MSBuild](/visualstudio/msbuild/msbuild) format.</span></span> <span data-ttu-id="6807c-122">Projeler için *. csproj* ve projeler için F# *. fsproj* gıbı uzantılara sahip proje dosyaları, XML biçimindedir. C#</span><span class="sxs-lookup"><span data-stu-id="6807c-122">Project files, which have extensions like *.csproj* for C# projects and *.fsproj* for F# projects, are in XML format.</span></span> <span data-ttu-id="6807c-123">MSBuild proje dosyasının kök öğesi [Proje](/visualstudio/msbuild/project-element-msbuild) öğesidir.</span><span class="sxs-lookup"><span data-stu-id="6807c-123">The root element of an MSBuild project file is the [Project](/visualstudio/msbuild/project-element-msbuild) element.</span></span> <span data-ttu-id="6807c-124">`Project` öğesinin hangi SDK (ve sürümü) kullanacağınızı belirten isteğe bağlı bir `Sdk` özniteliği vardır.</span><span class="sxs-lookup"><span data-stu-id="6807c-124">The `Project` element has an optional `Sdk` attribute that specifies which SDK (and version) to use.</span></span> <span data-ttu-id="6807c-125">.NET Core araçlarını kullanmak ve kodunuzu derlemek için `Sdk` özniteliğini [kullanılabilir SDK](#available-sdks) 'Lar tablosundaki kimliklerden birine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6807c-125">To use the .NET Core tools and build your code, set the `Sdk` attribute to one of the IDs in the [Available SDKs](#available-sdks) table.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

<span data-ttu-id="6807c-126">NuGet 'den gelen bir SDK belirtmek için, adın sonundaki sürümü ekleyin veya *Global. JSON* dosyasındaki adı ve sürümü belirtin.</span><span class="sxs-lookup"><span data-stu-id="6807c-126">To specify an SDK that comes from NuGet, include the version at the end of the name, or specify the name and version in the *global.json* file.</span></span>

```xml
<Project Sdk="MSBuild.Sdk.Extras/2.0.54">
  ...
</Project>
```

<span data-ttu-id="6807c-127">SDK 'yı belirtmenin bir başka yolu da en üst düzey [SDK](/visualstudio/msbuild/sdk-element-msbuild) öğesidir:</span><span class="sxs-lookup"><span data-stu-id="6807c-127">Another way to specify the SDK is with the top-level [Sdk](/visualstudio/msbuild/sdk-element-msbuild) element:</span></span>

```xml
<Project>
  <Sdk Name="Microsoft.NET.Sdk" />
  ...
</Project>
```

<span data-ttu-id="6807c-128">Bu yollarla bir SDK 'ya başvurmak, .NET Core için proje dosyalarını büyük ölçüde basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="6807c-128">Referencing an SDK in one of these ways greatly simplifies project files for .NET Core.</span></span> <span data-ttu-id="6807c-129">Proje değerlendirilirken MSBuild, proje dosyasının en üstünde `Sdk.props` için örtük içeri aktarmalar ekler ve alt kısımdaki `Sdk.targets`.</span><span class="sxs-lookup"><span data-stu-id="6807c-129">While evaluating the project, MSBuild adds implicit imports for `Sdk.props` at the top of the project file and `Sdk.targets` at the bottom.</span></span>

```xml
<Project>
  <!-- Implicit top import -->
  <Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk" />
  ...
  <!-- Implicit bottom import -->
  <Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk" />
</Project>
```

> [!TIP]
> <span data-ttu-id="6807c-130">Bir Windows makinesinde, *%ProgramFiles%\dotnet\sdk\\[Version] \Sdks\Microsoft.net.Sdk\Sdk* klasöründe *SDK. props* ve *SDK. targets* dosyaları bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="6807c-130">On a Windows machine, the *Sdk.props* and *Sdk.targets* files can be found in the *%ProgramFiles%\dotnet\sdk\\[version]\Sdks\Microsoft.NET.Sdk\Sdk* folder.</span></span>

### <a name="preprocess-the-project-file"></a><span data-ttu-id="6807c-131">Proje dosyasını ön işleme</span><span class="sxs-lookup"><span data-stu-id="6807c-131">Preprocess the project file</span></span>

<span data-ttu-id="6807c-132">SDK ve hedefleri `dotnet msbuild -preprocess` komutu kullanılarak eklendikten sonra, tam genişletilmiş projeyi MSBuild olarak görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6807c-132">You can see the fully expanded project as MSBuild sees it after the SDK and its targets are included by using the `dotnet msbuild -preprocess` command.</span></span> <span data-ttu-id="6807c-133">[`dotnet msbuild`](../tools/dotnet-msbuild.md) komutunun [ön işleme](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) anahtarı, hangi dosyaların içeri aktarılacağını, kaynaklarını ve derleme için gerçekten projeyi oluşturmadan bunların katkılarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6807c-133">The [preprocess](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) switch of the [`dotnet msbuild`](../tools/dotnet-msbuild.md) command shows which files are imported, their sources, and their contributions to the build without actually building the project.</span></span>

<span data-ttu-id="6807c-134">Projede birden çok hedef çerçeve varsa, komutun sonuçlarını MSBuild özelliği olarak belirterek yalnızca bir çerçeveye odaklayın.</span><span class="sxs-lookup"><span data-stu-id="6807c-134">If the project has multiple target frameworks, focus the results of the command on only one framework by specifying it as an MSBuild property.</span></span> <span data-ttu-id="6807c-135">Örnek:</span><span class="sxs-lookup"><span data-stu-id="6807c-135">For example:</span></span>

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

### <a name="default-compilation-includes"></a><span data-ttu-id="6807c-136">Varsayılan derleme şunları içerir</span><span class="sxs-lookup"><span data-stu-id="6807c-136">Default compilation includes</span></span>

<span data-ttu-id="6807c-137">Derleme öğeleri ve katıştırılmış kaynaklar için varsayılan içerir ve dışlardır SDK 'da tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="6807c-137">The default includes and excludes for compile items and embedded resources are defined in the SDK.</span></span> <span data-ttu-id="6807c-138">SDK olmayan .NET Framework projelerinin aksine, varsayılanlar en yaygın kullanım durumlarını kapsadığından proje dosyanızda bu öğeleri belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="6807c-138">Unlike non-SDK .NET Framework projects, you don't need to specify these items in your project file, because the defaults cover most common use cases.</span></span> <span data-ttu-id="6807c-139">Bu, daha kolay anlaşılması gereken daha küçük proje dosyalarına ve gerekirse el ile düzenlemeye yol açar.</span><span class="sxs-lookup"><span data-stu-id="6807c-139">This leads to smaller project files that are easier to understand as well as edit by hand, if needed.</span></span>

<span data-ttu-id="6807c-140">Aşağıdaki tabloda, .NET Core SDK hangi öğe ve hangi [genelleştirmeler](https://en.wikipedia.org/wiki/Glob_(programming)) dahil olduğu ve dışarıda tutulduğu gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="6807c-140">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are included and excluded in the .NET Core SDK:</span></span>

| <span data-ttu-id="6807c-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="6807c-141">Element</span></span>           | <span data-ttu-id="6807c-142">Glob 'yi dahil et</span><span class="sxs-lookup"><span data-stu-id="6807c-142">Include glob</span></span>                              | <span data-ttu-id="6807c-143">Glob 'yi hariç tut</span><span class="sxs-lookup"><span data-stu-id="6807c-143">Exclude glob</span></span>                                                  | <span data-ttu-id="6807c-144">Glob 'yi kaldır</span><span class="sxs-lookup"><span data-stu-id="6807c-144">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| <span data-ttu-id="6807c-145">Derleme</span><span class="sxs-lookup"><span data-stu-id="6807c-145">Compile</span></span>           | <span data-ttu-id="6807c-146">\*\*/\*. cs (veya diğer dil uzantıları)</span><span class="sxs-lookup"><span data-stu-id="6807c-146">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="6807c-147">\*\*/\*. Kullanıcı;  \*\*/\*.\*PROJ;  \*\*/\*. sln;  \*\*/\*. vssscc</span><span class="sxs-lookup"><span data-stu-id="6807c-147">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="6807c-148">Yok</span><span class="sxs-lookup"><span data-stu-id="6807c-148">N/A</span></span>                      |
| <span data-ttu-id="6807c-149">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="6807c-149">EmbeddedResource</span></span>  | <span data-ttu-id="6807c-150">\*\*/\*. resx</span><span class="sxs-lookup"><span data-stu-id="6807c-150">\*\*/\*.resx</span></span>                              | <span data-ttu-id="6807c-151">\*\*/\*. Kullanıcı; \*\*/\*.\*PROJ; \*\*/\*. sln; \*\*/\*. vssscc</span><span class="sxs-lookup"><span data-stu-id="6807c-151">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="6807c-152">Yok</span><span class="sxs-lookup"><span data-stu-id="6807c-152">N/A</span></span>                      |
| <span data-ttu-id="6807c-153">None</span><span class="sxs-lookup"><span data-stu-id="6807c-153">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="6807c-154">\*\*/\*. Kullanıcı; \*\*/\*.\*PROJ; \*\*/\*. sln; \*\*/\*. vssscc</span><span class="sxs-lookup"><span data-stu-id="6807c-154">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="6807c-155">\*\*/\*. cs; \*\*/\*. resx</span><span class="sxs-lookup"><span data-stu-id="6807c-155">\*\*/\*.cs; \*\*/\*.resx</span></span> |

> [!NOTE]
> <span data-ttu-id="6807c-156">`$(BaseOutputPath)` ve `$(BaseIntermediateOutputPath)` MSBuild özellikleriyle temsil edilen `./bin` ve `./obj` klasörleri varsayılan olarak genelleştirmeler çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="6807c-156">The `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, are excluded from the globs by default.</span></span> <span data-ttu-id="6807c-157">Dışlayarak Özellik `$(DefaultItemExcludes)`temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="6807c-157">Excludes are represented by the property `$(DefaultItemExcludes)`.</span></span>

<span data-ttu-id="6807c-158">Bu öğeleri proje dosyanızda açıkça tanımlarsanız, muhtemelen şu hatayı alabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6807c-158">If you explicitly define these items in your project file, you're likely to get the following error:</span></span>

<span data-ttu-id="6807c-159">**Yinelenen derleme öğeleri eklendi. .NET SDK, varsayılan olarak proje dizininizdeki derleme öğelerini içerir. Bu öğeleri proje dosyanıza kaldırabilir ya da bunları proje dosyanıza açıkça dahil etmek istiyorsanız ' Enabledefaultcompileıtems ' özelliğini ' false ' olarak ayarlayabilirsiniz.**</span><span class="sxs-lookup"><span data-stu-id="6807c-159">**Duplicate Compile items were included. The .NET SDK includes Compile items from your project directory by default. You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.**</span></span>

<span data-ttu-id="6807c-160">Hatayı gidermek için, önceki tabloda listelenen örtük öğelerle eşleşen açık `Compile` öğelerini kaldırın veya `EnableDefaultCompileItems` özelliğini `false`olarak ayarlayın, bu da örtük eklemeyi devre dışı bırakır:</span><span class="sxs-lookup"><span data-stu-id="6807c-160">To resolve the error, either remove the explicit `Compile` items that match the implicit ones listed on the previous table, or set the `EnableDefaultCompileItems` property to `false`, which disables implicit inclusion:</span></span>

```xml
<PropertyGroup>
  <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

<span data-ttu-id="6807c-161">Uygulamanızda yayımlanacak bazı dosyalar gibi belirtmek istiyorsanız, bunun için bilinen MSBuild mekanizmalarını yine de kullanabilirsiniz Örneğin, `Content` öğesi.</span><span class="sxs-lookup"><span data-stu-id="6807c-161">If you want to specify, for example, some files to get published with your app, you can still use the known MSBuild mechanisms for that, for example, the `Content` element.</span></span>

<span data-ttu-id="6807c-162">`EnableDefaultCompileItems` yalnızca `Compile` genelleştirmeler devre dışı bırakır, ancak \*. cs öğelerine de geçerli olan örtük `None` glob gibi diğer genelleştirmeler 'yi etkilemez.</span><span class="sxs-lookup"><span data-stu-id="6807c-162">`EnableDefaultCompileItems` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob that also applies to \*.cs items.</span></span> <span data-ttu-id="6807c-163">Bu nedenle, Visual Studio 'daki Çözüm Gezgini, projenin bir parçası olan `None` öğeler olarak dahil \*. cs öğelerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6807c-163">Because of that, Solution Explorer in Visual Studio shows \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="6807c-164">Örtük `None` glob 'yi devre dışı bırakmak için `EnableDefaultNoneItems` `false`olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="6807c-164">To disable the implicit `None` glob, set `EnableDefaultNoneItems` to `false`:</span></span>

```xml
<PropertyGroup>
  <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

<span data-ttu-id="6807c-165">*Tüm* örtük genelleştirmeler devre dışı bırakmak için `EnableDefaultItems` özelliğini `false`olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="6807c-165">To disable *all* implicit globs, set the `EnableDefaultItems` property to `false`:</span></span>

```xml
<PropertyGroup>
  <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="customize-the-build"></a><span data-ttu-id="6807c-166">Derlemeyi özelleştirme</span><span class="sxs-lookup"><span data-stu-id="6807c-166">Customize the build</span></span>

<span data-ttu-id="6807c-167">[Bir derlemeyi özelleştirmek](/visualstudio/msbuild/customize-your-build)için çeşitli yollar vardır.</span><span class="sxs-lookup"><span data-stu-id="6807c-167">There are various ways to [customize a build](/visualstudio/msbuild/customize-your-build).</span></span> <span data-ttu-id="6807c-168">Bir [MSBuild](/visualstudio/msbuild/msbuild-command-line-reference) veya [DotNet](../tools/index.md) komutuna bir bağımsız değişken olarak geçirerek bir özelliği geçersiz kılmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6807c-168">You may want to override a property by passing it as an argument to an [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) or [dotnet](../tools/index.md) command.</span></span> <span data-ttu-id="6807c-169">Ayrıca, özelliği proje dosyasına veya bir *Dizin. Build. props* dosyasına ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6807c-169">You can also add the property to the project file or to a *Directory.Build.props* file.</span></span> <span data-ttu-id="6807c-170">.NET Core projelerinin yararlı özelliklerinin bir listesi için bkz. [.NET Core SDK projeleri Için MSBuild özellikleri](msbuild-props.md).</span><span class="sxs-lookup"><span data-stu-id="6807c-170">For a list of useful properties for .NET Core projects, see [MSBuild properties for .NET Core SDK projects](msbuild-props.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6807c-171">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6807c-171">See also</span></span>

- [<span data-ttu-id="6807c-172">.NET Core’u yükleme</span><span class="sxs-lookup"><span data-stu-id="6807c-172">Install .NET Core</span></span>](../install/index.md)
- [<span data-ttu-id="6807c-173">MSBuild proje SDK 'larını kullanma</span><span class="sxs-lookup"><span data-stu-id="6807c-173">How to use MSBuild project SDKs</span></span>](/visualstudio/msbuild/how-to-use-project-sdk)
