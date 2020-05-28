---
title: .NET Core proje SDK 'sına genel bakış
titleSuffix: ''
description: .NET Core proje SDK 'Ları hakkında bilgi edinin.
ms.date: 02/02/2020
ms.topic: conceptual
ms.openlocfilehash: 67dede3caabd2967adca22e7563376c761829655
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144245"
---
# <a name="net-core-project-sdks"></a><span data-ttu-id="86d55-103">.NET Core proje SDK 'Ları</span><span class="sxs-lookup"><span data-stu-id="86d55-103">.NET Core project SDKs</span></span>

<span data-ttu-id="86d55-104">.NET Core projeleri bir yazılım geliştirme seti (SDK) ile ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="86d55-104">.NET Core projects are associated with a software development kit (SDK).</span></span> <span data-ttu-id="86d55-105">Her *Proje SDK 'sı* , bir dizi MSBuild [hedefi](/visualstudio/msbuild/msbuild-targets) ve kodu derleme, paketleme ve yayımlama ile ilgili [görevlerden](/visualstudio/msbuild/msbuild-tasks) oluşur.</span><span class="sxs-lookup"><span data-stu-id="86d55-105">Each *project SDK* is a set of MSBuild [targets](/visualstudio/msbuild/msbuild-targets) and associated [tasks](/visualstudio/msbuild/msbuild-tasks) that are responsible for compiling, packing, and publishing code.</span></span> <span data-ttu-id="86d55-106">Proje SDK 'Sına başvuran bir proje bazen bir *SDK stili proje*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="86d55-106">A project that references a project SDK is sometimes referred to as an *SDK-style project*.</span></span>

## <a name="available-sdks"></a><span data-ttu-id="86d55-107">Kullanılabilir SDK 'lar</span><span class="sxs-lookup"><span data-stu-id="86d55-107">Available SDKs</span></span>

<span data-ttu-id="86d55-108">.NET Core için aşağıdaki SDK 'lar mevcuttur:</span><span class="sxs-lookup"><span data-stu-id="86d55-108">The following SDKs are available for .NET Core:</span></span>

| <span data-ttu-id="86d55-109">ID</span><span class="sxs-lookup"><span data-stu-id="86d55-109">ID</span></span> | <span data-ttu-id="86d55-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86d55-110">Description</span></span> | <span data-ttu-id="86d55-111">Depo</span><span class="sxs-lookup"><span data-stu-id="86d55-111">Repo</span></span>|
| - | - | - |
| `Microsoft.NET.Sdk` | <span data-ttu-id="86d55-112">.NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="86d55-112">The .NET Core SDK</span></span> | <https://github.com/dotnet/sdk> |
| `Microsoft.NET.Sdk.Web` | <span data-ttu-id="86d55-113">.NET Core [Web SDK 'sı](/aspnet/core/razor-pages/web-sdk)</span><span class="sxs-lookup"><span data-stu-id="86d55-113">The .NET Core [Web SDK](/aspnet/core/razor-pages/web-sdk)</span></span> | <https://github.com/aspnet/websdk> |
| `Microsoft.NET.Sdk.Razor` | <span data-ttu-id="86d55-114">.NET Core [Razor SDK 'sı](/aspnet/core/razor-pages/sdk)</span><span class="sxs-lookup"><span data-stu-id="86d55-114">The .NET Core [Razor SDK](/aspnet/core/razor-pages/sdk)</span></span> |
| `Microsoft.NET.Sdk.Worker` | <span data-ttu-id="86d55-115">.NET Core Worker hizmeti SDK 'Sı</span><span class="sxs-lookup"><span data-stu-id="86d55-115">The .NET Core Worker Service SDK</span></span> |
| `Microsoft.NET.Sdk.WindowsDesktop` | <span data-ttu-id="86d55-116">.NET Core WinForms ve WPF SDK</span><span class="sxs-lookup"><span data-stu-id="86d55-116">The .NET Core WinForms and WPF SDK</span></span> |

<span data-ttu-id="86d55-117">.NET Core SDK, .NET Core için temel SDK 'dir.</span><span class="sxs-lookup"><span data-stu-id="86d55-117">The .NET Core SDK is the base SDK for .NET Core.</span></span> <span data-ttu-id="86d55-118">Diğer SDK 'lar .NET Core SDK başvuruda bulunur ve diğer SDK 'lar ile ilişkili projeler için kullanılabilen tüm .NET Core SDK özellikleri vardır.</span><span class="sxs-lookup"><span data-stu-id="86d55-118">The other SDKs reference the .NET Core SDK, and projects that are associated with the other SDKs have all the .NET Core SDK properties available to them.</span></span> <span data-ttu-id="86d55-119">Örneğin, Web SDK 'Sı, hem .NET Core SDK hem de Razor SDK 'sına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="86d55-119">The Web SDK, for example, depends on both the .NET Core SDK and the Razor SDK.</span></span>

<span data-ttu-id="86d55-120">Ayrıca kendi SDK 'nizi, NuGet aracılığıyla dağıtılabilecek şekilde yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86d55-120">You can also author your own SDK that can be distributed via NuGet.</span></span>

## <a name="project-files"></a><span data-ttu-id="86d55-121">Proje dosyaları</span><span class="sxs-lookup"><span data-stu-id="86d55-121">Project files</span></span>

<span data-ttu-id="86d55-122">.NET Core projeleri [MSBuild](/visualstudio/msbuild/msbuild) biçimine dayanır.</span><span class="sxs-lookup"><span data-stu-id="86d55-122">.NET Core projects are based on the [MSBuild](/visualstudio/msbuild/msbuild) format.</span></span> <span data-ttu-id="86d55-123">C# projeleri için *. csproj* ve F # projelerinde *. fsproj* gibi uzantılara sahıp proje dosyaları, XML biçimindedir.</span><span class="sxs-lookup"><span data-stu-id="86d55-123">Project files, which have extensions like *.csproj* for C# projects and *.fsproj* for F# projects, are in XML format.</span></span> <span data-ttu-id="86d55-124">MSBuild proje dosyasının kök öğesi [Proje](/visualstudio/msbuild/project-element-msbuild) öğesidir.</span><span class="sxs-lookup"><span data-stu-id="86d55-124">The root element of an MSBuild project file is the [Project](/visualstudio/msbuild/project-element-msbuild) element.</span></span> <span data-ttu-id="86d55-125">`Project`Öğesi `Sdk` Hangi SDK (ve sürümü) kullanacağınızı belirten isteğe bağlı bir özniteliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="86d55-125">The `Project` element has an optional `Sdk` attribute that specifies which SDK (and version) to use.</span></span> <span data-ttu-id="86d55-126">.NET Core araçlarını kullanmak ve kodunuzu derlemek için, `Sdk` özniteliğini [kullanılabilir SDK](#available-sdks) 'lar tablosundaki kimliklerden birine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="86d55-126">To use the .NET Core tools and build your code, set the `Sdk` attribute to one of the IDs in the [Available SDKs](#available-sdks) table.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

<span data-ttu-id="86d55-127">NuGet 'den gelen bir SDK belirtmek için, adın sonundaki sürümü ekleyin veya *Global. JSON* dosyasındaki adı ve sürümü belirtin.</span><span class="sxs-lookup"><span data-stu-id="86d55-127">To specify an SDK that comes from NuGet, include the version at the end of the name, or specify the name and version in the *global.json* file.</span></span>

```xml
<Project Sdk="MSBuild.Sdk.Extras/2.0.54">
  ...
</Project>
```

<span data-ttu-id="86d55-128">SDK 'yı belirtmenin bir başka yolu da en üst düzey [SDK](/visualstudio/msbuild/sdk-element-msbuild) öğesidir:</span><span class="sxs-lookup"><span data-stu-id="86d55-128">Another way to specify the SDK is with the top-level [Sdk](/visualstudio/msbuild/sdk-element-msbuild) element:</span></span>

```xml
<Project>
  <Sdk Name="Microsoft.NET.Sdk" />
  ...
</Project>
```

<span data-ttu-id="86d55-129">Bu yollarla bir SDK 'ya başvurmak, .NET Core için proje dosyalarını büyük ölçüde basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="86d55-129">Referencing an SDK in one of these ways greatly simplifies project files for .NET Core.</span></span> <span data-ttu-id="86d55-130">Proje değerlendirilirken MSBuild, `Sdk.props` Proje dosyasının üst kısmına ve alt kısmına örtük içeri aktarmalar ekler `Sdk.targets` .</span><span class="sxs-lookup"><span data-stu-id="86d55-130">While evaluating the project, MSBuild adds implicit imports for `Sdk.props` at the top of the project file and `Sdk.targets` at the bottom.</span></span>

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
> <span data-ttu-id="86d55-131">Bir Windows makinesinde, *%ProgramFiles%\dotnet\sdk \\ [Version] \Sdks\Microsoft.net.Sdk\Sdk* klasöründe *SDK. props* ve *SDK. targets* dosyaları bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="86d55-131">On a Windows machine, the *Sdk.props* and *Sdk.targets* files can be found in the *%ProgramFiles%\dotnet\sdk\\[version]\Sdks\Microsoft.NET.Sdk\Sdk* folder.</span></span>

### <a name="preprocess-the-project-file"></a><span data-ttu-id="86d55-132">Proje dosyasını ön işleme</span><span class="sxs-lookup"><span data-stu-id="86d55-132">Preprocess the project file</span></span>

<span data-ttu-id="86d55-133">SDK ve hedefleri komutu kullanılarak eklendikten sonra, tam genişletilmiş projeyi MSBuild olarak görebilirsiniz `dotnet msbuild -preprocess` .</span><span class="sxs-lookup"><span data-stu-id="86d55-133">You can see the fully expanded project as MSBuild sees it after the SDK and its targets are included by using the `dotnet msbuild -preprocess` command.</span></span> <span data-ttu-id="86d55-134">Komutun [ön işlem](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) anahtarı [`dotnet msbuild`](../tools/dotnet-msbuild.md) hangi dosyaların içeri aktarılacağını, kaynaklarını ve derleme için gerçekten projeyi oluşturmadan yapıya katkılarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="86d55-134">The [preprocess](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) switch of the [`dotnet msbuild`](../tools/dotnet-msbuild.md) command shows which files are imported, their sources, and their contributions to the build without actually building the project.</span></span>

<span data-ttu-id="86d55-135">Projede birden çok hedef çerçeve varsa, komutun sonuçlarını MSBuild özelliği olarak belirterek yalnızca bir çerçeveye odaklayın.</span><span class="sxs-lookup"><span data-stu-id="86d55-135">If the project has multiple target frameworks, focus the results of the command on only one framework by specifying it as an MSBuild property.</span></span> <span data-ttu-id="86d55-136">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="86d55-136">For example:</span></span>

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

### <a name="default-compilation-includes"></a><span data-ttu-id="86d55-137">Varsayılan derleme şunları içerir</span><span class="sxs-lookup"><span data-stu-id="86d55-137">Default compilation includes</span></span>

<span data-ttu-id="86d55-138">Derleme öğeleri, katıştırılmış kaynaklar ve öğeler için varsayılan içerir ve `None` DıŞLARDıR SDK 'da tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="86d55-138">The default includes and excludes for compile items, embedded resources, and `None` items are defined in the SDK.</span></span> <span data-ttu-id="86d55-139">SDK olmayan .NET Framework projelerinin aksine, varsayılanlar en yaygın kullanım durumlarını kapsadığından proje dosyanızda bu öğeleri belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="86d55-139">Unlike non-SDK .NET Framework projects, you don't need to specify these items in your project file, because the defaults cover most common use cases.</span></span> <span data-ttu-id="86d55-140">Bu, proje dosyasını daha küçük ve gerekirse, el ile anlamanız ve düzenlemeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="86d55-140">This makes the project file smaller and easier to understand and edit by hand, if needed.</span></span>

<span data-ttu-id="86d55-141">Aşağıdaki tablo, hangi öğelerin ve hangi [genelleştirmeler](https://en.wikipedia.org/wiki/Glob_(programming)) dahil edileceğini ve .NET Core SDK hariç tutulduğunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="86d55-141">The following table shows which elements and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are included and excluded in the .NET Core SDK:</span></span>

| <span data-ttu-id="86d55-142">Öğe</span><span class="sxs-lookup"><span data-stu-id="86d55-142">Element</span></span>           | <span data-ttu-id="86d55-143">Glob 'yi dahil et</span><span class="sxs-lookup"><span data-stu-id="86d55-143">Include glob</span></span>                              | <span data-ttu-id="86d55-144">Glob 'yi hariç tut</span><span class="sxs-lookup"><span data-stu-id="86d55-144">Exclude glob</span></span>                                                  | <span data-ttu-id="86d55-145">Glob 'yi kaldır</span><span class="sxs-lookup"><span data-stu-id="86d55-145">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| <span data-ttu-id="86d55-146">Se</span><span class="sxs-lookup"><span data-stu-id="86d55-146">Compile</span></span>           | <span data-ttu-id="86d55-147">\*\*/\*. cs (veya diğer dil uzantıları)</span><span class="sxs-lookup"><span data-stu-id="86d55-147">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="86d55-148">\*\*/\*kullanıcısını  \*\*/\*.\* PROJ  \*\*/\*. sln  \*\*/\*. vssscc</span><span class="sxs-lookup"><span data-stu-id="86d55-148">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="86d55-149">YOK</span><span class="sxs-lookup"><span data-stu-id="86d55-149">N/A</span></span>                      |
| <span data-ttu-id="86d55-150">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="86d55-150">EmbeddedResource</span></span>  | <span data-ttu-id="86d55-151">\*\*/\*. resx</span><span class="sxs-lookup"><span data-stu-id="86d55-151">\*\*/\*.resx</span></span>                              | <span data-ttu-id="86d55-152">\*\*/\*kullanıcısını \*\*/\*.\* PROJ \*\*/\*. sln \*\*/\*. vssscc</span><span class="sxs-lookup"><span data-stu-id="86d55-152">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="86d55-153">YOK</span><span class="sxs-lookup"><span data-stu-id="86d55-153">N/A</span></span>                      |
| <span data-ttu-id="86d55-154">Yok</span><span class="sxs-lookup"><span data-stu-id="86d55-154">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="86d55-155">\*\*/\*kullanıcısını \*\*/\*.\* PROJ \*\*/\*. sln \*\*/\*. vssscc</span><span class="sxs-lookup"><span data-stu-id="86d55-155">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="86d55-156">\*\*/\*.cs \*\*/\*. resx</span><span class="sxs-lookup"><span data-stu-id="86d55-156">\*\*/\*.cs; \*\*/\*.resx</span></span> |

> [!NOTE]
> <span data-ttu-id="86d55-157">Ve `./bin` `./obj` MSBuild özellikleriyle temsil edilen ve klasörleri, `$(BaseOutputPath)` `$(BaseIntermediateOutputPath)` Varsayılan olarak genelleştirmeler 'tan çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="86d55-157">The `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, are excluded from the globs by default.</span></span> <span data-ttu-id="86d55-158">Dışlayarak özelliği tarafından temsil edilir `$(DefaultItemExcludes)` .</span><span class="sxs-lookup"><span data-stu-id="86d55-158">Excludes are represented by the property `$(DefaultItemExcludes)`.</span></span>

#### <a name="build-errors"></a><span data-ttu-id="86d55-159">Derleme hataları</span><span class="sxs-lookup"><span data-stu-id="86d55-159">Build errors</span></span>

<span data-ttu-id="86d55-160">Proje dosyanızda bu öğelerden herhangi birini açıkça tanımlarsanız, büyük olasılıkla aşağıdakine benzer bir "NETSDK1022" derleme hatası alırsınız:</span><span class="sxs-lookup"><span data-stu-id="86d55-160">If you explicitly define any of these items in your project file, you're likely to get a "NETSDK1022" build error similar to the following:</span></span>

  > <span data-ttu-id="86d55-161">Yinelenen ' Compile ' öğeleri eklendi.</span><span class="sxs-lookup"><span data-stu-id="86d55-161">Duplicate 'Compile' items were included.</span></span> <span data-ttu-id="86d55-162">.NET SDK varsayılan olarak proje dizininizdeki ' derleme ' öğelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="86d55-162">The .NET SDK includes 'Compile' items from your project directory by default.</span></span> <span data-ttu-id="86d55-163">Bu öğeleri proje dosyanıza kaldırabilir ya da bunları proje dosyanıza açıkça dahil etmek istiyorsanız ' Enabledefaultcompileıtems ' özelliğini ' false ' olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86d55-163">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

  > <span data-ttu-id="86d55-164">Yinelenen ' EmbeddedResource ' öğeleri eklendi.</span><span class="sxs-lookup"><span data-stu-id="86d55-164">Duplicate 'EmbeddedResource' items were included.</span></span> <span data-ttu-id="86d55-165">.NET SDK varsayılan olarak proje dizininizdeki ' EmbeddedResource ' öğelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="86d55-165">The .NET SDK includes 'EmbeddedResource' items from your project directory by default.</span></span> <span data-ttu-id="86d55-166">Bu öğeleri proje dosyanıza kaldırabilir ya da bunları proje dosyanıza açıkça dahil etmek istiyorsanız ' Enabledefaultembeddedresourceıtems ' özelliğini ' false ' olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86d55-166">You can either remove these items from your project file, or set the 'EnableDefaultEmbeddedResourceItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

<span data-ttu-id="86d55-167">Hataları gidermek için aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="86d55-167">To resolve the errors, do one of the following:</span></span>

- <span data-ttu-id="86d55-168">`Compile` `EmbeddedResource` `None` Önceki tabloda listelenenlerin bulunduğu açık, veya öğeleri kaldırın.</span><span class="sxs-lookup"><span data-stu-id="86d55-168">Remove the explicit `Compile`, `EmbeddedResource`, or `None` items that match the implicit ones listed on the previous table.</span></span>

- <span data-ttu-id="86d55-169">`EnableDefaultItems` `false` Tüm örtük dosya eklemeyi devre dışı bırakmak için özelliğini olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="86d55-169">Set the `EnableDefaultItems` property to `false` to disable all implicit file inclusion:</span></span>

  ```xml
  <PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
  </PropertyGroup>
  ```

  <span data-ttu-id="86d55-170">Uygulamanızla yayımlanacak dosyaları belirtmek istiyorsanız, bu gibi bilinen MSBuild mekanizmalarını yine de kullanabilirsiniz (örneğin, `Content` öğesi).</span><span class="sxs-lookup"><span data-stu-id="86d55-170">If you want to specify files to be published with your app, you can still use the known MSBuild mechanisms for that, for example, the `Content` element.</span></span>

- <span data-ttu-id="86d55-171">,, Veya özelliğini olarak ayarlayarak yalnızca,, `Compile` veya genelleştirmeler öğesini seçime bağlı olarak devre dışı bırakın `EmbeddedResource` `None` `EnableDefaultCompileItems` `EnableDefaultEmbeddedResourceItems` `EnableDefaultNoneItems` `false` :</span><span class="sxs-lookup"><span data-stu-id="86d55-171">Selectively disable only `Compile`, `EmbeddedResource`, or `None` globs by setting the `EnableDefaultCompileItems`, `EnableDefaultEmbeddedResourceItems`, or `EnableDefaultNoneItems` property to `false`:</span></span>

  ```xml
  <PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
    <EnableDefaultEmbeddedResourceItems>false</EnableDefaultEmbeddedResourceItems>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
  </PropertyGroup>
  ```

  <span data-ttu-id="86d55-172">Yalnızca genelleştirmeler 'yi devre dışı bırakırsanız `Compile` , Visual Studio 'daki Çözüm Gezgini, \* öğe olarak da dahil olmak üzere projenin bir parçası olarak. cs öğelerini gösterir `None` .</span><span class="sxs-lookup"><span data-stu-id="86d55-172">If you only disable `Compile` globs, Solution Explorer in Visual Studio still shows \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="86d55-173">Örtük glob 'yi devre dışı bırakmak için `None` , `EnableDefaultNoneItems` çok olarak ayarlayın `false` .</span><span class="sxs-lookup"><span data-stu-id="86d55-173">To disable the implicit `None` glob, set `EnableDefaultNoneItems` to `false` too.</span></span>

## <a name="customize-the-build"></a><span data-ttu-id="86d55-174">Derlemeyi özelleştirme</span><span class="sxs-lookup"><span data-stu-id="86d55-174">Customize the build</span></span>

<span data-ttu-id="86d55-175">[Bir derlemeyi özelleştirmek](/visualstudio/msbuild/customize-your-build)için çeşitli yollar vardır.</span><span class="sxs-lookup"><span data-stu-id="86d55-175">There are various ways to [customize a build](/visualstudio/msbuild/customize-your-build).</span></span> <span data-ttu-id="86d55-176">Bir [MSBuild](/visualstudio/msbuild/msbuild-command-line-reference) veya [DotNet](../tools/index.md) komutuna bir bağımsız değişken olarak geçirerek bir özelliği geçersiz kılmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86d55-176">You may want to override a property by passing it as an argument to an [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) or [dotnet](../tools/index.md) command.</span></span> <span data-ttu-id="86d55-177">Ayrıca, özelliği proje dosyasına veya bir *Dizin. Build. props* dosyasına ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86d55-177">You can also add the property to the project file or to a *Directory.Build.props* file.</span></span> <span data-ttu-id="86d55-178">.NET Core projelerinin yararlı özelliklerinin bir listesi için bkz. [.NET Core SDK projeleri Için MSBuild başvurusu](msbuild-props.md).</span><span class="sxs-lookup"><span data-stu-id="86d55-178">For a list of useful properties for .NET Core projects, see [MSBuild reference for .NET Core SDK projects](msbuild-props.md).</span></span>

### <a name="custom-targets"></a><span data-ttu-id="86d55-179">Özel hedefler</span><span class="sxs-lookup"><span data-stu-id="86d55-179">Custom targets</span></span>

<span data-ttu-id="86d55-180">.NET Core projeleri, paketi tüketen projeler tarafından kullanılmak üzere özel MSBuild hedeflerini ve özelliklerini paketleyebilir.</span><span class="sxs-lookup"><span data-stu-id="86d55-180">.NET Core projects can package custom MSBuild targets and properties for use by projects that consume the package.</span></span> <span data-ttu-id="86d55-181">Şunları yapmak istediğinizde bu tür bir genişletilebilirlik kullanın:</span><span class="sxs-lookup"><span data-stu-id="86d55-181">Use this type of extensibility when you want to:</span></span>

- <span data-ttu-id="86d55-182">Yapı sürecini genişletin.</span><span class="sxs-lookup"><span data-stu-id="86d55-182">Extend the build process.</span></span>
- <span data-ttu-id="86d55-183">Oluşturulan dosyalar gibi yapı sürecinin yapılarına erişin.</span><span class="sxs-lookup"><span data-stu-id="86d55-183">Access artifacts of the build process, such as generated files.</span></span>
- <span data-ttu-id="86d55-184">Yapılandırmanın çağrıldığı yapılandırmayı inceleyin.</span><span class="sxs-lookup"><span data-stu-id="86d55-184">Inspect the configuration under which the build is invoked.</span></span>

<span data-ttu-id="86d55-185">Dosyaları forma `<package_id>.targets` veya `<package_id>.props` (örneğin, `Contoso.Utility.UsefulStuff.targets` ) projenin *Build* klasörüne yerleştirerek özel derleme hedefleri veya özellikleri eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="86d55-185">You add custom build targets or properties by placing files in the form `<package_id>.targets` or `<package_id>.props` (for example, `Contoso.Utility.UsefulStuff.targets`) in the *build* folder of the project.</span></span>

<span data-ttu-id="86d55-186">Aşağıdaki XML, bir *. csproj* dosyasındaki, [`dotnet pack`](../tools/dotnet-pack.md) komuta neyin paketlenecek olduğunu bildiren bir kod parçacıdır.</span><span class="sxs-lookup"><span data-stu-id="86d55-186">The following XML is a snippet from a *.csproj* file that instructs the [`dotnet pack`](../tools/dotnet-pack.md) command what to package.</span></span> <span data-ttu-id="86d55-187">`<ItemGroup Label="dotnet pack instructions">`Öğesi, hedef dosyalarını paketin içindeki *derleme* klasörüne koyar.</span><span class="sxs-lookup"><span data-stu-id="86d55-187">The `<ItemGroup Label="dotnet pack instructions">` element places the targets files into the *build* folder inside the package.</span></span> <span data-ttu-id="86d55-188">`<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">`Öğesi derlemeler ve *. JSON* dosyalarını *Build* klasörüne koyar.</span><span class="sxs-lookup"><span data-stu-id="86d55-188">The `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` element places the assemblies and *.json* files into the *build* folder.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  ...
  <ItemGroup Label="dotnet pack instructions">
    <Content Include="build\*.targets">
      <Pack>true</Pack>
      <PackagePath>build\</PackagePath>
    </Content>
  </ItemGroup>
  <Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">
    <!-- Collect these items inside a target that runs after build but before packaging. -->
    <ItemGroup>
      <Content Include="$(OutputPath)\*.dll;$(OutputPath)\*.json">
        <Pack>true</Pack>
        <PackagePath>build\</PackagePath>
      </Content>
    </ItemGroup>
  </Target>
  ...
  
</Project>
```

<span data-ttu-id="86d55-189">Projenizde özel bir hedef kullanmak için `PackageReference` pakete ve sürümüne işaret eden bir öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="86d55-189">To consume a custom target in your project, add a `PackageReference` element that points to the package and its version.</span></span> <span data-ttu-id="86d55-190">Araçların aksine, özel hedefler paketi, tüketen projenin bağımlılık kapanışına dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="86d55-190">Unlike the tools, the custom targets package is included in the consuming project's dependency closure.</span></span>

<span data-ttu-id="86d55-191">Özel hedefin nasıl kullanılacağını yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86d55-191">You can configure how to use the custom target.</span></span> <span data-ttu-id="86d55-192">Bir MSBuild hedefi olduğundan, belirli bir hedefe bağlı olabilir, başka bir hedeften sonra çalıştırılabilir veya komutu kullanılarak el ile çağrılabilir `dotnet msbuild -t:<target-name>` .</span><span class="sxs-lookup"><span data-stu-id="86d55-192">Since it's an MSBuild target, it can depend on a given target, run after another target, or be manually invoked by using the `dotnet msbuild -t:<target-name>` command.</span></span> <span data-ttu-id="86d55-193">Ancak, daha iyi bir kullanıcı deneyimi sağlamak için proje başına araçları ve özel hedefleri birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86d55-193">However, to provide a better user experience, you can combine per-project tools and custom targets.</span></span> <span data-ttu-id="86d55-194">Bu senaryoda, proje başına aracı her türlü parametreyi kabul eder ve [`dotnet msbuild`](../tools/dotnet-msbuild.md) hedefi yürüten gerekli çağrıya çevirir.</span><span class="sxs-lookup"><span data-stu-id="86d55-194">In this scenario, the per-project tool accepts whatever parameters are needed and translates that into the required [`dotnet msbuild`](../tools/dotnet-msbuild.md) invocation that executes the target.</span></span> <span data-ttu-id="86d55-195">Bu tür sinerjiden bahsederek denemelerini 'nin bir örneğini projede [MVP Zirvesi 2016 Hackathon örnekleri](https://github.com/dotnet/MVPSummitHackathon2016) deposunda görebilirsiniz [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) .</span><span class="sxs-lookup"><span data-stu-id="86d55-195">You can see a sample of this kind of synergy on the [MVP Summit 2016 Hackathon samples](https://github.com/dotnet/MVPSummitHackathon2016) repo in the [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) project.</span></span>

## <a name="see-also"></a><span data-ttu-id="86d55-196">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86d55-196">See also</span></span>

- [<span data-ttu-id="86d55-197">.NET Core 'ı yükler</span><span class="sxs-lookup"><span data-stu-id="86d55-197">Install .NET Core</span></span>](../install/index.md)
- [<span data-ttu-id="86d55-198">MSBuild proje SDK 'larını kullanma</span><span class="sxs-lookup"><span data-stu-id="86d55-198">How to use MSBuild project SDKs</span></span>](/visualstudio/msbuild/how-to-use-project-sdk)
- [<span data-ttu-id="86d55-199">NuGet ile özel MSBuild hedeflerini ve props paketleme</span><span class="sxs-lookup"><span data-stu-id="86d55-199">Package custom MSBuild targets and props with NuGet</span></span>](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package)
