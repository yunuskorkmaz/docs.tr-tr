---
title: .NET proje SDK 'sına genel bakış
titleSuffix: ''
description: .NET proje SDK 'Ları hakkında bilgi edinin.
ms.date: 09/17/2020
ms.topic: conceptual
ms.openlocfilehash: 2adb0713fabda142d071425a2affe66cc9d4c172
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189674"
---
# <a name="net-project-sdks"></a><span data-ttu-id="292bf-103">.NET projesi SDK 'Ları</span><span class="sxs-lookup"><span data-stu-id="292bf-103">.NET project SDKs</span></span>

<span data-ttu-id="292bf-104">.NET Core ve .NET 5,0 ve üzeri projeler yazılım geliştirme seti (SDK) ile ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="292bf-104">.NET Core and .NET 5.0 and later projects are associated with a software development kit (SDK).</span></span> <span data-ttu-id="292bf-105">Her *Proje SDK 'sı* , bir dizi MSBuild [hedefi](/visualstudio/msbuild/msbuild-targets) ve kodu derleme, paketleme ve yayımlama ile ilgili [görevlerden](/visualstudio/msbuild/msbuild-tasks) oluşur.</span><span class="sxs-lookup"><span data-stu-id="292bf-105">Each *project SDK* is a set of MSBuild [targets](/visualstudio/msbuild/msbuild-targets) and associated [tasks](/visualstudio/msbuild/msbuild-tasks) that are responsible for compiling, packing, and publishing code.</span></span> <span data-ttu-id="292bf-106">Proje SDK 'Sına başvuran bir proje bazen bir *SDK stili proje* olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="292bf-106">A project that references a project SDK is sometimes referred to as an *SDK-style project*.</span></span>

## <a name="available-sdks"></a><span data-ttu-id="292bf-107">Kullanılabilir SDK 'lar</span><span class="sxs-lookup"><span data-stu-id="292bf-107">Available SDKs</span></span>

<span data-ttu-id="292bf-108">Aşağıdaki SDK 'lar kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="292bf-108">The following SDKs are available:</span></span>

| <span data-ttu-id="292bf-109">ID</span><span class="sxs-lookup"><span data-stu-id="292bf-109">ID</span></span> | <span data-ttu-id="292bf-110">Description</span><span class="sxs-lookup"><span data-stu-id="292bf-110">Description</span></span> | <span data-ttu-id="292bf-111">Depo</span><span class="sxs-lookup"><span data-stu-id="292bf-111">Repo</span></span>|
| - | - | - |
| `Microsoft.NET.Sdk` | <span data-ttu-id="292bf-112">.NET SDK</span><span class="sxs-lookup"><span data-stu-id="292bf-112">The .NET SDK</span></span> | <https://github.com/dotnet/sdk> |
| `Microsoft.NET.Sdk.Web` | <span data-ttu-id="292bf-113">.NET [Web SDK 'sı](/aspnet/core/razor-pages/web-sdk)</span><span class="sxs-lookup"><span data-stu-id="292bf-113">The .NET [Web SDK](/aspnet/core/razor-pages/web-sdk)</span></span> | <https://github.com/dotnet/sdk> |
| `Microsoft.NET.Sdk.Razor` | <span data-ttu-id="292bf-114">.NET [Razor SDK 'sı](/aspnet/core/razor-pages/sdk)</span><span class="sxs-lookup"><span data-stu-id="292bf-114">The .NET [Razor SDK](/aspnet/core/razor-pages/sdk)</span></span> |
| `Microsoft.NET.Sdk.Worker` | <span data-ttu-id="292bf-115">.NET Worker hizmeti SDK 'Sı</span><span class="sxs-lookup"><span data-stu-id="292bf-115">The .NET Worker Service SDK</span></span> |
| `Microsoft.NET.Sdk.WindowsDesktop` | <span data-ttu-id="292bf-116">WinForms ve WPF SDK 'Sı\*</span><span class="sxs-lookup"><span data-stu-id="292bf-116">The WinForms and WPF SDK\*</span></span> | <span data-ttu-id="292bf-117"><https://github.com/dotnet/winforms> ve <https://github.com/dotnet/wpf></span><span class="sxs-lookup"><span data-stu-id="292bf-117"><https://github.com/dotnet/winforms> and <https://github.com/dotnet/wpf></span></span> |

<span data-ttu-id="292bf-118">.NET SDK, .NET için temel SDK 'dir.</span><span class="sxs-lookup"><span data-stu-id="292bf-118">The .NET SDK is the base SDK for .NET.</span></span> <span data-ttu-id="292bf-119">Diğer SDK 'lar .NET SDK 'ya başvuru sağlar ve diğer SDK 'lar ile ilişkili projelere tüm .NET SDK özellikleri de mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="292bf-119">The other SDKs reference the .NET SDK, and projects that are associated with the other SDKs have all the .NET SDK properties available to them.</span></span> <span data-ttu-id="292bf-120">Örneğin, Web SDK 'sı, hem .NET SDK hem de Razor SDK 'ya bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="292bf-120">The Web SDK, for example, depends on both the .NET SDK and the Razor SDK.</span></span>

<span data-ttu-id="292bf-121">Ayrıca kendi SDK 'nizi, NuGet aracılığıyla dağıtılabilecek şekilde yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="292bf-121">You can also author your own SDK that can be distributed via NuGet.</span></span>

<span data-ttu-id="292bf-122">\* .NET 5,0 ' den başlayarak Windows Forms ve Windows Presentation Foundation (WPF) projeleri yerine .NET SDK () belirtmelidir `Microsoft.NET.Sdk` `Microsoft.NET.Sdk.WindowsDesktop` .</span><span class="sxs-lookup"><span data-stu-id="292bf-122">\* Starting in .NET 5.0, Windows Forms and Windows Presentation Foundation (WPF) projects should specify the .NET SDK (`Microsoft.NET.Sdk`) instead of `Microsoft.NET.Sdk.WindowsDesktop`.</span></span> <span data-ttu-id="292bf-123">Bu projeler için, `TargetFramework` ve için `net5.0-windows` ayarı `UseWPF` `UseWindowsForms` `true` Windows Masaüstü SDK 'sını otomatik olarak içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="292bf-123">For these projects, setting `TargetFramework` to `net5.0-windows` and `UseWPF` or `UseWindowsForms` to `true` will automatically import the Windows desktop SDK.</span></span> <span data-ttu-id="292bf-124">Projeniz .NET 5,0 veya üstünü hedefliyorsa ve `Microsoft.NET.Sdk.WindowsDesktop` SDK 'yı belirtirse, derleme uyarısı NETSDK1137 alırsınız.</span><span class="sxs-lookup"><span data-stu-id="292bf-124">If your project targets .NET 5.0 or later and specifies the `Microsoft.NET.Sdk.WindowsDesktop` SDK, you'll get build warning NETSDK1137.</span></span>

## <a name="project-files"></a><span data-ttu-id="292bf-125">Proje dosyaları</span><span class="sxs-lookup"><span data-stu-id="292bf-125">Project files</span></span>

<span data-ttu-id="292bf-126">.NET projeleri [MSBuild](/visualstudio/msbuild/msbuild) biçimine dayalıdır.</span><span class="sxs-lookup"><span data-stu-id="292bf-126">.NET projects are based on the [MSBuild](/visualstudio/msbuild/msbuild) format.</span></span> <span data-ttu-id="292bf-127">C# projeleri için *. csproj* ve F # projelerinde *. fsproj* gibi uzantılara sahıp proje dosyaları, XML biçimindedir.</span><span class="sxs-lookup"><span data-stu-id="292bf-127">Project files, which have extensions like *.csproj* for C# projects and *.fsproj* for F# projects, are in XML format.</span></span> <span data-ttu-id="292bf-128">MSBuild proje dosyasının kök öğesi [Proje](/visualstudio/msbuild/project-element-msbuild) öğesidir.</span><span class="sxs-lookup"><span data-stu-id="292bf-128">The root element of an MSBuild project file is the [Project](/visualstudio/msbuild/project-element-msbuild) element.</span></span> <span data-ttu-id="292bf-129">`Project`Öğesi `Sdk` Hangi SDK (ve sürümü) kullanacağınızı belirten isteğe bağlı bir özniteliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="292bf-129">The `Project` element has an optional `Sdk` attribute that specifies which SDK (and version) to use.</span></span> <span data-ttu-id="292bf-130">.NET araçlarını kullanmak ve kodunuzu derlemek için, `Sdk` özniteliğini [kullanılabilir SDK](#available-sdks) 'lar tablosundaki kimliklerden birine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="292bf-130">To use the .NET tools and build your code, set the `Sdk` attribute to one of the IDs in the [Available SDKs](#available-sdks) table.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

<span data-ttu-id="292bf-131">NuGet 'den gelen bir SDK belirtmek için, adın sonundaki sürümü ekleyin veya *global.js* dosyadaki adı ve sürümü belirtin.</span><span class="sxs-lookup"><span data-stu-id="292bf-131">To specify an SDK that comes from NuGet, include the version at the end of the name, or specify the name and version in the *global.json* file.</span></span>

```xml
<Project Sdk="MSBuild.Sdk.Extras/2.0.54">
  ...
</Project>
```

<span data-ttu-id="292bf-132">SDK 'yı belirtmenin bir başka yolu da en üst düzey [SDK](/visualstudio/msbuild/sdk-element-msbuild) öğesidir:</span><span class="sxs-lookup"><span data-stu-id="292bf-132">Another way to specify the SDK is with the top-level [Sdk](/visualstudio/msbuild/sdk-element-msbuild) element:</span></span>

```xml
<Project>
  <Sdk Name="Microsoft.NET.Sdk" />
  ...
</Project>
```

<span data-ttu-id="292bf-133">Bu yollarla bir SDK 'ya başvurmak, .NET için proje dosyalarını büyük ölçüde basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="292bf-133">Referencing an SDK in one of these ways greatly simplifies project files for .NET.</span></span> <span data-ttu-id="292bf-134">Proje değerlendirilirken MSBuild, `Sdk.props` Proje dosyasının üst kısmına ve alt kısmına örtük içeri aktarmalar ekler `Sdk.targets` .</span><span class="sxs-lookup"><span data-stu-id="292bf-134">While evaluating the project, MSBuild adds implicit imports for `Sdk.props` at the top of the project file and `Sdk.targets` at the bottom.</span></span>

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
> <span data-ttu-id="292bf-135">Bir Windows makinesinde, *%ProgramFiles%\dotnet\sdk \\ [Version] \Sdks\Microsoft.net.Sdk\Sdk* klasöründe *SDK. props* ve *SDK. targets* dosyaları bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="292bf-135">On a Windows machine, the *Sdk.props* and *Sdk.targets* files can be found in the *%ProgramFiles%\dotnet\sdk\\[version]\Sdks\Microsoft.NET.Sdk\Sdk* folder.</span></span>

### <a name="preprocess-the-project-file"></a><span data-ttu-id="292bf-136">Proje dosyasını ön işleme</span><span class="sxs-lookup"><span data-stu-id="292bf-136">Preprocess the project file</span></span>

<span data-ttu-id="292bf-137">SDK ve hedefleri komutu kullanılarak eklendikten sonra, tam genişletilmiş projeyi MSBuild olarak görebilirsiniz `dotnet msbuild -preprocess` .</span><span class="sxs-lookup"><span data-stu-id="292bf-137">You can see the fully expanded project as MSBuild sees it after the SDK and its targets are included by using the `dotnet msbuild -preprocess` command.</span></span> <span data-ttu-id="292bf-138">Komutun [ön işlem](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) anahtarı [`dotnet msbuild`](../tools/dotnet-msbuild.md) hangi dosyaların içeri aktarılacağını, kaynaklarını ve derleme için gerçekten projeyi oluşturmadan yapıya katkılarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="292bf-138">The [preprocess](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) switch of the [`dotnet msbuild`](../tools/dotnet-msbuild.md) command shows which files are imported, their sources, and their contributions to the build without actually building the project.</span></span>

<span data-ttu-id="292bf-139">Projede birden çok hedef çerçeve varsa, komutun sonuçlarını MSBuild özelliği olarak belirterek yalnızca bir çerçeveye odaklayın.</span><span class="sxs-lookup"><span data-stu-id="292bf-139">If the project has multiple target frameworks, focus the results of the command on only one framework by specifying it as an MSBuild property.</span></span> <span data-ttu-id="292bf-140">Örnek:</span><span class="sxs-lookup"><span data-stu-id="292bf-140">For example:</span></span>

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

## <a name="default-includes-and-excludes"></a><span data-ttu-id="292bf-141">Varsayılan içerme ve dışladığı</span><span class="sxs-lookup"><span data-stu-id="292bf-141">Default includes and excludes</span></span>

<span data-ttu-id="292bf-142">[ `Compile` Öğelerin](/visualstudio/msbuild/common-msbuild-project-items#compile), [katıştırılmış kaynakların](/visualstudio/msbuild/common-msbuild-project-items#embeddedresource)ve [ `None` öğelerin](/visualstudio/msbuild/common-msbuild-project-items#none) varsayılan dahil ve hariç olması SDK 'da tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="292bf-142">The default includes and excludes for [`Compile` items](/visualstudio/msbuild/common-msbuild-project-items#compile), [embedded resources](/visualstudio/msbuild/common-msbuild-project-items#embeddedresource), and [`None` items](/visualstudio/msbuild/common-msbuild-project-items#none) are defined in the SDK.</span></span> <span data-ttu-id="292bf-143">SDK olmayan .NET Framework projelerinin aksine, varsayılanlar en yaygın kullanım durumlarını kapsadığından proje dosyanızda bu öğeleri belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="292bf-143">Unlike non-SDK .NET Framework projects, you don't need to specify these items in your project file, because the defaults cover most common use cases.</span></span> <span data-ttu-id="292bf-144">Bu davranış, proje dosyasını daha küçük ve gerektiğinde daha kolay anlaşılır ve düzenlenebilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="292bf-144">This behavior makes the project file smaller and easier to understand and edit by hand, if needed.</span></span>

<span data-ttu-id="292bf-145">Aşağıdaki tabloda, .NET SDK 'sında hangi öğelerin ve hangi [genelleştirmeler](https://en.wikipedia.org/wiki/Glob_(programming)) dahil olduğu ve dışlandıkları gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="292bf-145">The following table shows which elements and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are included and excluded in the .NET SDK:</span></span>

| <span data-ttu-id="292bf-146">Öğe</span><span class="sxs-lookup"><span data-stu-id="292bf-146">Element</span></span>           | <span data-ttu-id="292bf-147">Glob 'yi dahil et</span><span class="sxs-lookup"><span data-stu-id="292bf-147">Include glob</span></span>                              | <span data-ttu-id="292bf-148">Glob 'yi hariç tut</span><span class="sxs-lookup"><span data-stu-id="292bf-148">Exclude glob</span></span>                                                  | <span data-ttu-id="292bf-149">Glob 'yi kaldır</span><span class="sxs-lookup"><span data-stu-id="292bf-149">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| <span data-ttu-id="292bf-150">Se</span><span class="sxs-lookup"><span data-stu-id="292bf-150">Compile</span></span>           | <span data-ttu-id="292bf-151">\*\*/\*. cs (veya diğer dil uzantıları)</span><span class="sxs-lookup"><span data-stu-id="292bf-151">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="292bf-152">\*\*/\*kullanıcısını  \*\*/\*.\* PROJ  \*\*/\*. sln  \*\*/\*. vssscc</span><span class="sxs-lookup"><span data-stu-id="292bf-152">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="292bf-153">Yok</span><span class="sxs-lookup"><span data-stu-id="292bf-153">N/A</span></span>                      |
| <span data-ttu-id="292bf-154">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="292bf-154">EmbeddedResource</span></span>  | <span data-ttu-id="292bf-155">\*\*/\*. resx</span><span class="sxs-lookup"><span data-stu-id="292bf-155">\*\*/\*.resx</span></span>                              | <span data-ttu-id="292bf-156">\*\*/\*kullanıcısını \*\*/\*.\* PROJ \*\*/\*. sln \*\*/\*. vssscc</span><span class="sxs-lookup"><span data-stu-id="292bf-156">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="292bf-157">Yok</span><span class="sxs-lookup"><span data-stu-id="292bf-157">N/A</span></span>                      |
| <span data-ttu-id="292bf-158">Yok</span><span class="sxs-lookup"><span data-stu-id="292bf-158">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="292bf-159">\*\*/\*kullanıcısını \*\*/\*.\* PROJ \*\*/\*. sln \*\*/\*. vssscc</span><span class="sxs-lookup"><span data-stu-id="292bf-159">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="292bf-160">\*\*/\*.cs \*\*/\*. resx</span><span class="sxs-lookup"><span data-stu-id="292bf-160">\*\*/\*.cs; \*\*/\*.resx</span></span> |

> [!NOTE]
> <span data-ttu-id="292bf-161">Ve `./bin` `./obj` MSBuild özellikleriyle temsil edilen ve klasörleri, `$(BaseOutputPath)` `$(BaseIntermediateOutputPath)` Varsayılan olarak genelleştirmeler 'tan çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="292bf-161">The `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, are excluded from the globs by default.</span></span> <span data-ttu-id="292bf-162">Dışlayarak [DefaultItemExcludes özelliği](msbuild-props.md#defaultitemexcludes)tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="292bf-162">Excludes are represented by the [DefaultItemExcludes property](msbuild-props.md#defaultitemexcludes).</span></span>

### <a name="build-errors"></a><span data-ttu-id="292bf-163">Derleme hataları</span><span class="sxs-lookup"><span data-stu-id="292bf-163">Build errors</span></span>

<span data-ttu-id="292bf-164">Proje dosyanızda bu öğelerden herhangi birini açıkça tanımlarsanız, büyük olasılıkla aşağıdakine benzer bir "NETSDK1022" derleme hatası alırsınız:</span><span class="sxs-lookup"><span data-stu-id="292bf-164">If you explicitly define any of these items in your project file, you're likely to get a "NETSDK1022" build error similar to the following:</span></span>

  > <span data-ttu-id="292bf-165">Yinelenen ' Compile ' öğeleri eklendi.</span><span class="sxs-lookup"><span data-stu-id="292bf-165">Duplicate 'Compile' items were included.</span></span> <span data-ttu-id="292bf-166">.NET SDK varsayılan olarak proje dizininizdeki ' derleme ' öğelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="292bf-166">The .NET SDK includes 'Compile' items from your project directory by default.</span></span> <span data-ttu-id="292bf-167">Bu öğeleri proje dosyanıza kaldırabilir ya da bunları proje dosyanıza açıkça dahil etmek istiyorsanız ' Enabledefaultcompileıtems ' özelliğini ' false ' olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="292bf-167">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

  > <span data-ttu-id="292bf-168">Yinelenen ' EmbeddedResource ' öğeleri eklendi.</span><span class="sxs-lookup"><span data-stu-id="292bf-168">Duplicate 'EmbeddedResource' items were included.</span></span> <span data-ttu-id="292bf-169">.NET SDK varsayılan olarak proje dizininizdeki ' EmbeddedResource ' öğelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="292bf-169">The .NET SDK includes 'EmbeddedResource' items from your project directory by default.</span></span> <span data-ttu-id="292bf-170">Bu öğeleri proje dosyanıza kaldırabilir ya da bunları proje dosyanıza açıkça dahil etmek istiyorsanız ' Enabledefaultembeddedresourceıtems ' özelliğini ' false ' olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="292bf-170">You can either remove these items from your project file, or set the 'EnableDefaultEmbeddedResourceItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

<span data-ttu-id="292bf-171">Hataları gidermek için aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="292bf-171">To resolve the errors, do one of the following:</span></span>

- <span data-ttu-id="292bf-172">`Compile` `EmbeddedResource` `None` Önceki tabloda listelenenlerin bulunduğu açık, veya öğeleri kaldırın.</span><span class="sxs-lookup"><span data-stu-id="292bf-172">Remove the explicit `Compile`, `EmbeddedResource`, or `None` items that match the implicit ones listed on the previous table.</span></span>

- <span data-ttu-id="292bf-173">Tüm örtük dosya eklemeyi devre dışı bırakmak için [Enabledefaultıtems özelliğini](msbuild-props.md#enabledefaultitems) olarak ayarlayın `false` :</span><span class="sxs-lookup"><span data-stu-id="292bf-173">Set the [EnableDefaultItems property](msbuild-props.md#enabledefaultitems) to `false` to disable all implicit file inclusion:</span></span>

  ```xml
  <PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
  </PropertyGroup>
  ```

  <span data-ttu-id="292bf-174">Uygulamanızla yayımlanacak dosyaları belirtmek istiyorsanız, bu gibi bilinen MSBuild mekanizmalarını yine de kullanabilirsiniz (örneğin, `Content` öğesi).</span><span class="sxs-lookup"><span data-stu-id="292bf-174">If you want to specify files to be published with your app, you can still use the known MSBuild mechanisms for that, for example, the `Content` element.</span></span>

- <span data-ttu-id="292bf-175">`Compile` `EmbeddedResource` `None` [Enabledefaultcompileıtems](msbuild-props.md#enabledefaultcompileitems), [enabledefaultembeddedresourceıtems](msbuild-props.md#enabledefaultembeddedresourceitems)veya [enabledefaultnoneıtems](msbuild-props.md#enabledefaultnoneitems) özelliğini şu şekilde ayarlayarak yalnızca, veya genelleştirmeler öğesini seçerek devre dışı bırakın `false` :</span><span class="sxs-lookup"><span data-stu-id="292bf-175">Selectively disable only `Compile`, `EmbeddedResource`, or `None` globs by setting the [EnableDefaultCompileItems](msbuild-props.md#enabledefaultcompileitems), [EnableDefaultEmbeddedResourceItems](msbuild-props.md#enabledefaultembeddedresourceitems), or [EnableDefaultNoneItems](msbuild-props.md#enabledefaultnoneitems) property to `false`:</span></span>

  ```xml
  <PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
    <EnableDefaultEmbeddedResourceItems>false</EnableDefaultEmbeddedResourceItems>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
  </PropertyGroup>
  ```

  <span data-ttu-id="292bf-176">Yalnızca genelleştirmeler 'yi devre dışı bırakırsanız `Compile` , Visual Studio 'daki Çözüm Gezgini, \* öğe olarak da dahil olmak üzere projenin bir parçası olarak. cs öğelerini gösterir `None` .</span><span class="sxs-lookup"><span data-stu-id="292bf-176">If you only disable `Compile` globs, Solution Explorer in Visual Studio still shows \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="292bf-177">Örtük glob 'yi devre dışı bırakmak için `None` , `EnableDefaultNoneItems` çok olarak ayarlayın `false` .</span><span class="sxs-lookup"><span data-stu-id="292bf-177">To disable the implicit `None` glob, set `EnableDefaultNoneItems` to `false` too.</span></span>

## <a name="build-events"></a><span data-ttu-id="292bf-178">Derleme olayları</span><span class="sxs-lookup"><span data-stu-id="292bf-178">Build events</span></span>

<span data-ttu-id="292bf-179">SDK stili projelerde, veya adında bir MSBuild hedefi kullanın `PreBuild` `PostBuild` ve `BeforeTargets` özelliğini `PreBuild` veya `AfterTargets` özelliğini ayarlayın `PostBuild` .</span><span class="sxs-lookup"><span data-stu-id="292bf-179">In SDK-style projects, use an MSBuild target named `PreBuild` or `PostBuild` and set the `BeforeTargets` property for `PreBuild` or the `AfterTargets` property for `PostBuild`.</span></span>

```xml
<Target Name="PreBuild" BeforeTargets="PreBuildEvent">
    <Exec Command="&quot;$(ProjectDir)PreBuildEvent.bat&quot; &quot;$(ProjectDir)..\&quot; &quot;$(ProjectDir)&quot; &quot;$(TargetDir)&quot;" />
</Target>

<Target Name="PostBuild" AfterTargets="PostBuildEvent">
   <Exec Command="echo Output written to $(TargetDir)" />
</Target>
```

> [!NOTE]
>
> - <span data-ttu-id="292bf-180">MSBuild hedefleri için herhangi bir ad kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="292bf-180">You can use any name for the MSBuild targets.</span></span> <span data-ttu-id="292bf-181">Ancak, Visual Studio IDE tanır `PreBuild` ve `PostBuild` hedefler, bu nedenle bu adları kullanarak IDE 'deki komutları düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="292bf-181">However, the Visual Studio IDE recognizes `PreBuild` and `PostBuild` targets, so by using those names, you can edit the commands in the IDE.</span></span>
> - <span data-ttu-id="292bf-182">Özellikler ve, gibi `PreBuildEvent` `PostBuildEvent` makrolar çözümlenmediği için SDK stili projelerde önerilmez `$(ProjectDir)` .</span><span class="sxs-lookup"><span data-stu-id="292bf-182">The properties `PreBuildEvent` and `PostBuildEvent` are not recommended in SDK-style projects, because macros such as `$(ProjectDir)` aren't resolved.</span></span> <span data-ttu-id="292bf-183">Örneğin, aşağıdaki kod desteklenmez:</span><span class="sxs-lookup"><span data-stu-id="292bf-183">For example, the following code is not supported:</span></span>
>
> ```xml
> <PropertyGroup>
>   <PreBuildEvent>"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)"</PreBuildEvent>
> </PropertyGroup>
> ```

## <a name="customize-the-build"></a><span data-ttu-id="292bf-184">Derlemeyi özelleştirme</span><span class="sxs-lookup"><span data-stu-id="292bf-184">Customize the build</span></span>

<span data-ttu-id="292bf-185">[Bir derlemeyi özelleştirmek](/visualstudio/msbuild/customize-your-build)için çeşitli yollar vardır.</span><span class="sxs-lookup"><span data-stu-id="292bf-185">There are various ways to [customize a build](/visualstudio/msbuild/customize-your-build).</span></span> <span data-ttu-id="292bf-186">Bir [MSBuild](/visualstudio/msbuild/msbuild-command-line-reference) veya [DotNet](../tools/index.md) komutuna bir bağımsız değişken olarak geçirerek bir özelliği geçersiz kılmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="292bf-186">You may want to override a property by passing it as an argument to an [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) or [dotnet](../tools/index.md) command.</span></span> <span data-ttu-id="292bf-187">Ayrıca, özelliği proje dosyasına veya bir *Dizin. Build. props* dosyasına ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="292bf-187">You can also add the property to the project file or to a *Directory.Build.props* file.</span></span> <span data-ttu-id="292bf-188">.NET projelerinin yararlı özelliklerinin bir listesi için bkz. [.NET SDK projeleri Için MSBuild başvurusu](msbuild-props.md).</span><span class="sxs-lookup"><span data-stu-id="292bf-188">For a list of useful properties for .NET projects, see [MSBuild reference for .NET SDK projects](msbuild-props.md).</span></span>

### <a name="custom-targets"></a><span data-ttu-id="292bf-189">Özel hedefler</span><span class="sxs-lookup"><span data-stu-id="292bf-189">Custom targets</span></span>

<span data-ttu-id="292bf-190">.NET projeleri, paketi tüketen projeler tarafından kullanılmak üzere özel MSBuild hedeflerini ve özelliklerini paketleyebilir.</span><span class="sxs-lookup"><span data-stu-id="292bf-190">.NET projects can package custom MSBuild targets and properties for use by projects that consume the package.</span></span> <span data-ttu-id="292bf-191">Şunları yapmak istediğinizde bu tür bir genişletilebilirlik kullanın:</span><span class="sxs-lookup"><span data-stu-id="292bf-191">Use this type of extensibility when you want to:</span></span>

- <span data-ttu-id="292bf-192">Yapı sürecini genişletin.</span><span class="sxs-lookup"><span data-stu-id="292bf-192">Extend the build process.</span></span>
- <span data-ttu-id="292bf-193">Oluşturulan dosyalar gibi yapı sürecinin yapılarına erişin.</span><span class="sxs-lookup"><span data-stu-id="292bf-193">Access artifacts of the build process, such as generated files.</span></span>
- <span data-ttu-id="292bf-194">Yapılandırmanın çağrıldığı yapılandırmayı inceleyin.</span><span class="sxs-lookup"><span data-stu-id="292bf-194">Inspect the configuration under which the build is invoked.</span></span>

<span data-ttu-id="292bf-195">Dosyaları forma `<package_id>.targets` veya `<package_id>.props` (örneğin, `Contoso.Utility.UsefulStuff.targets` ) projenin *Build* klasörüne yerleştirerek özel derleme hedefleri veya özellikleri eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="292bf-195">You add custom build targets or properties by placing files in the form `<package_id>.targets` or `<package_id>.props` (for example, `Contoso.Utility.UsefulStuff.targets`) in the *build* folder of the project.</span></span>

<span data-ttu-id="292bf-196">Aşağıdaki XML, bir *. csproj* dosyasındaki, [`dotnet pack`](../tools/dotnet-pack.md) komuta neyin paketlenecek olduğunu bildiren bir kod parçacıdır.</span><span class="sxs-lookup"><span data-stu-id="292bf-196">The following XML is a snippet from a *.csproj* file that instructs the [`dotnet pack`](../tools/dotnet-pack.md) command what to package.</span></span> <span data-ttu-id="292bf-197">`<ItemGroup Label="dotnet pack instructions">`Öğesi, hedef dosyalarını paketin içindeki *derleme* klasörüne koyar.</span><span class="sxs-lookup"><span data-stu-id="292bf-197">The `<ItemGroup Label="dotnet pack instructions">` element places the targets files into the *build* folder inside the package.</span></span> <span data-ttu-id="292bf-198">`<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">`Öğesi derlemeler ve *. JSON* dosyalarını *Build* klasörüne koyar.</span><span class="sxs-lookup"><span data-stu-id="292bf-198">The `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` element places the assemblies and *.json* files into the *build* folder.</span></span>

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

<span data-ttu-id="292bf-199">Projenizde özel bir hedef kullanmak için `PackageReference` pakete ve sürümüne işaret eden bir öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="292bf-199">To consume a custom target in your project, add a `PackageReference` element that points to the package and its version.</span></span> <span data-ttu-id="292bf-200">Araçların aksine, özel hedefler paketi, tüketen projenin bağımlılık kapanışına dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="292bf-200">Unlike the tools, the custom targets package is included in the consuming project's dependency closure.</span></span>

<span data-ttu-id="292bf-201">Özel hedefin nasıl kullanılacağını yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="292bf-201">You can configure how to use the custom target.</span></span> <span data-ttu-id="292bf-202">Bir MSBuild hedefi olduğundan, belirli bir hedefe bağlı olabilir, başka bir hedeften sonra çalıştırılabilir veya komutu kullanılarak el ile çağrılabilir `dotnet msbuild -t:<target-name>` .</span><span class="sxs-lookup"><span data-stu-id="292bf-202">Since it's an MSBuild target, it can depend on a given target, run after another target, or be manually invoked by using the `dotnet msbuild -t:<target-name>` command.</span></span> <span data-ttu-id="292bf-203">Ancak, daha iyi bir kullanıcı deneyimi sağlamak için proje başına araçları ve özel hedefleri birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="292bf-203">However, to provide a better user experience, you can combine per-project tools and custom targets.</span></span> <span data-ttu-id="292bf-204">Bu senaryoda, proje başına aracı her türlü parametreyi kabul eder ve [`dotnet msbuild`](../tools/dotnet-msbuild.md) hedefi yürüten gerekli çağrıya çevirir.</span><span class="sxs-lookup"><span data-stu-id="292bf-204">In this scenario, the per-project tool accepts whatever parameters are needed and translates that into the required [`dotnet msbuild`](../tools/dotnet-msbuild.md) invocation that executes the target.</span></span> <span data-ttu-id="292bf-205">Bu tür sinerjiden bahsederek denemelerini 'nin bir örneğini projede [MVP Zirvesi 2016 Hackathon örnekleri](https://github.com/dotnet/MVPSummitHackathon2016) deposunda görebilirsiniz [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) .</span><span class="sxs-lookup"><span data-stu-id="292bf-205">You can see a sample of this kind of synergy on the [MVP Summit 2016 Hackathon samples](https://github.com/dotnet/MVPSummitHackathon2016) repo in the [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) project.</span></span>

## <a name="see-also"></a><span data-ttu-id="292bf-206">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="292bf-206">See also</span></span>

- [<span data-ttu-id="292bf-207">.NET Core 'ı yükler</span><span class="sxs-lookup"><span data-stu-id="292bf-207">Install .NET Core</span></span>](../install/index.yml)
- [<span data-ttu-id="292bf-208">MSBuild proje SDK 'larını kullanma</span><span class="sxs-lookup"><span data-stu-id="292bf-208">How to use MSBuild project SDKs</span></span>](/visualstudio/msbuild/how-to-use-project-sdk)
- [<span data-ttu-id="292bf-209">NuGet ile özel MSBuild hedeflerini ve props paketleme</span><span class="sxs-lookup"><span data-stu-id="292bf-209">Package custom MSBuild targets and props with NuGet</span></span>](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package)
