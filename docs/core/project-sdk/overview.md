---
title: .NET Core projesi SDK'ya genel bakış
description: .NET Core projesi SDK'ları hakkında bilgi edinin.
ms.date: 02/02/2020
ms.topic: conceptual
ms.openlocfilehash: 32e14993326c6f17d6470249fe5a545180348631
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399177"
---
# <a name="net-core-project-sdks"></a><span data-ttu-id="0cf4a-103">.NET Çekirdek projesi SDK'ları</span><span class="sxs-lookup"><span data-stu-id="0cf4a-103">.NET Core project SDKs</span></span>

<span data-ttu-id="0cf4a-104">.NET Core projeleri bir yazılım geliştirme kiti (SDK) ile ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-104">.NET Core projects are associated with a software development kit (SDK).</span></span> <span data-ttu-id="0cf4a-105">Her proje SDK, kod derleme, paketleme ve yayımlamadan sorumlu bir MSBuild [hedefleri](/visualstudio/msbuild/msbuild-targets) ve ilişkili [görevler](/visualstudio/msbuild/msbuild-tasks) kümesidir.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-105">Each project SDK is a set of MSBuild [targets](/visualstudio/msbuild/msbuild-targets) and associated [tasks](/visualstudio/msbuild/msbuild-tasks) that are responsible for compiling, packing, and publishing code.</span></span>

## <a name="available-sdks"></a><span data-ttu-id="0cf4a-106">Kullanılabilir SDK'lar</span><span class="sxs-lookup"><span data-stu-id="0cf4a-106">Available SDKs</span></span>

<span data-ttu-id="0cf4a-107">.NET Core için aşağıdaki SDK'lar mevcuttur:</span><span class="sxs-lookup"><span data-stu-id="0cf4a-107">The following SDKs are available for .NET Core:</span></span>

| <span data-ttu-id="0cf4a-108">Kimlik</span><span class="sxs-lookup"><span data-stu-id="0cf4a-108">ID</span></span> | <span data-ttu-id="0cf4a-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0cf4a-109">Description</span></span> | <span data-ttu-id="0cf4a-110">Repo</span><span class="sxs-lookup"><span data-stu-id="0cf4a-110">Repo</span></span>|
| - | - | - |
| `Microsoft.NET.Sdk` | <span data-ttu-id="0cf4a-111">.NET Çekirdek SDK</span><span class="sxs-lookup"><span data-stu-id="0cf4a-111">The .NET Core SDK</span></span> | https://github.com/dotnet/sdk |
| `Microsoft.NET.Sdk.Web` | <span data-ttu-id="0cf4a-112">.NET Çekirdek [Web SDK](/aspnet/core/razor-pages/web-sdk)</span><span class="sxs-lookup"><span data-stu-id="0cf4a-112">The .NET Core [Web SDK](/aspnet/core/razor-pages/web-sdk)</span></span> | https://github.com/aspnet/websdk |
| `Microsoft.NET.Sdk.Razor` | <span data-ttu-id="0cf4a-113">.NET [ÇekirdekLi Jilet SDK](/aspnet/core/razor-pages/sdk)</span><span class="sxs-lookup"><span data-stu-id="0cf4a-113">The .NET Core [Razor SDK](/aspnet/core/razor-pages/sdk)</span></span> |
| `Microsoft.NET.Sdk.Worker` | <span data-ttu-id="0cf4a-114">.NET Çekirdek İşçi Servisi SDK</span><span class="sxs-lookup"><span data-stu-id="0cf4a-114">The .NET Core Worker Service SDK</span></span> |
| `Microsoft.NET.Sdk.WindowsDesktop` | <span data-ttu-id="0cf4a-115">.NET Çekirdek Kazanç Formları ve WPF SDK</span><span class="sxs-lookup"><span data-stu-id="0cf4a-115">The .NET Core WinForms and WPF SDK</span></span> |

<span data-ttu-id="0cf4a-116">.NET Core SDK, .NET Core'un temel SDK'sudur.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-116">The .NET Core SDK is the base SDK for .NET Core.</span></span> <span data-ttu-id="0cf4a-117">Diğer SDK'lar .NET Core SDK'ya başvurur ve diğer SDK'larla ilişkili projeler de mevcut tüm .NET Core SDK özelliklerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-117">The other SDKs reference the .NET Core SDK, and projects that are associated with the other SDKs have all the .NET Core SDK properties available to them.</span></span> <span data-ttu-id="0cf4a-118">Örneğin Web SDK hem .NET Core SDK'ya hem de Razor SDK'ya bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-118">The Web SDK, for example, depends on both the .NET Core SDK and the Razor SDK.</span></span>

<span data-ttu-id="0cf4a-119">Ayrıca NuGet üzerinden dağıtılabilir kendi SDK yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-119">You can also author your own SDK that can be distributed via NuGet.</span></span>

## <a name="project-files"></a><span data-ttu-id="0cf4a-120">Proje dosyaları</span><span class="sxs-lookup"><span data-stu-id="0cf4a-120">Project files</span></span>

<span data-ttu-id="0cf4a-121">.NET Core projeleri [MSBuild](/visualstudio/msbuild/msbuild) formatına dayanır.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-121">.NET Core projects are based on the [MSBuild](/visualstudio/msbuild/msbuild) format.</span></span> <span data-ttu-id="0cf4a-122">C# projeleri için *.csproj* ve F# projeleri için *.fsproj* gibi uzantıları olan proje dosyaları XML formatındadır.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-122">Project files, which have extensions like *.csproj* for C# projects and *.fsproj* for F# projects, are in XML format.</span></span> <span data-ttu-id="0cf4a-123">MSBuild proje dosyasının kök öğesi [Proje](/visualstudio/msbuild/project-element-msbuild) öğesidir.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-123">The root element of an MSBuild project file is the [Project](/visualstudio/msbuild/project-element-msbuild) element.</span></span> <span data-ttu-id="0cf4a-124">Öğe, `Project` hangi `Sdk` SDK'nın (ve sürümünün) kullanılacağını belirten isteğe bağlı bir özniteliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-124">The `Project` element has an optional `Sdk` attribute that specifies which SDK (and version) to use.</span></span> <span data-ttu-id="0cf4a-125">.NET Core araçlarını kullanmak ve kodunuzu `Sdk` oluşturmak için, özniteliği [Kullanılabilir SDK'lar](#available-sdks) tablosundaki iYe'lerden birine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-125">To use the .NET Core tools and build your code, set the `Sdk` attribute to one of the IDs in the [Available SDKs](#available-sdks) table.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

<span data-ttu-id="0cf4a-126">NuGet'den gelen bir SDK belirtmek için, adın sonundaki sürümü ekleyin veya *global.json* dosyasında adı ve sürümü belirtin.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-126">To specify an SDK that comes from NuGet, include the version at the end of the name, or specify the name and version in the *global.json* file.</span></span>

```xml
<Project Sdk="MSBuild.Sdk.Extras/2.0.54">
  ...
</Project>
```

<span data-ttu-id="0cf4a-127">SDK belirtmek için başka bir yolu üst düzey [Sdk](/visualstudio/msbuild/sdk-element-msbuild) elemanı ile:</span><span class="sxs-lookup"><span data-stu-id="0cf4a-127">Another way to specify the SDK is with the top-level [Sdk](/visualstudio/msbuild/sdk-element-msbuild) element:</span></span>

```xml
<Project>
  <Sdk Name="Microsoft.NET.Sdk" />
  ...
</Project>
```

<span data-ttu-id="0cf4a-128">Bir SDK'ya bu yollardan biriyle başvurmak ,NET Core için proje dosyalarını büyük ölçüde basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-128">Referencing an SDK in one of these ways greatly simplifies project files for .NET Core.</span></span> <span data-ttu-id="0cf4a-129">MSBuild, projeyi değerlendirirken proje `Sdk.props` dosyasının üst kısmında ve `Sdk.targets` en altta örtülü içeri aktarım ekler.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-129">While evaluating the project, MSBuild adds implicit imports for `Sdk.props` at the top of the project file and `Sdk.targets` at the bottom.</span></span>

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
> <span data-ttu-id="0cf4a-130">Bir Windows makinesinde, *Sdk.props* ve *Sdk.targets* dosyaları *%ProgramFiles%\dotnet\sdk\\[sürüm]\Sdks\Microsoft.NET.Sdk\Sdk* klasöründe bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-130">On a Windows machine, the *Sdk.props* and *Sdk.targets* files can be found in the *%ProgramFiles%\dotnet\sdk\\[version]\Sdks\Microsoft.NET.Sdk\Sdk* folder.</span></span>

### <a name="preprocess-the-project-file"></a><span data-ttu-id="0cf4a-131">Proje dosyasını ön işleme</span><span class="sxs-lookup"><span data-stu-id="0cf4a-131">Preprocess the project file</span></span>

<span data-ttu-id="0cf4a-132">MSBuild SDK ve hedefleri `dotnet msbuild -preprocess` komutu kullanarak dahil edildikten sonra gördüğü gibi tamamen genişletilmiş proje görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-132">You can see the fully expanded project as MSBuild sees it after the SDK and its targets are included by using the `dotnet msbuild -preprocess` command.</span></span> <span data-ttu-id="0cf4a-133">Komutun [`dotnet msbuild`](../tools/dotnet-msbuild.md) [ön işlem](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) anahtarı, hangi dosyaların içe aktarıldığı, kaynakları ve projeyi gerçekten oluşturmadan yapıya katkıları gösterir.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-133">The [preprocess](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) switch of the [`dotnet msbuild`](../tools/dotnet-msbuild.md) command shows which files are imported, their sources, and their contributions to the build without actually building the project.</span></span>

<span data-ttu-id="0cf4a-134">Projenin birden çok hedef çerçevesi varsa, komutun sonuçlarını MSBuild özelliği olarak belirterek yalnızca bir çerçeveye odakla.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-134">If the project has multiple target frameworks, focus the results of the command on only one framework by specifying it as an MSBuild property.</span></span> <span data-ttu-id="0cf4a-135">Örnek:</span><span class="sxs-lookup"><span data-stu-id="0cf4a-135">For example:</span></span>

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

### <a name="default-compilation-includes"></a><span data-ttu-id="0cf4a-136">Varsayılan derleme içerir</span><span class="sxs-lookup"><span data-stu-id="0cf4a-136">Default compilation includes</span></span>

<span data-ttu-id="0cf4a-137">Varsayılan öğeler ve katıştırılmış kaynaklar derlemek için içerir ve hariç SDK tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-137">The default includes and excludes for compile items and embedded resources are defined in the SDK.</span></span> <span data-ttu-id="0cf4a-138">SDK dışı .NET Framework projelerinin aksine, varsayılanlar en yaygın kullanım durumlarını kapsadığından, bu öğeleri proje dosyanızda belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-138">Unlike non-SDK .NET Framework projects, you don't need to specify these items in your project file, because the defaults cover most common use cases.</span></span> <span data-ttu-id="0cf4a-139">Bu, anlaşılması daha kolay olan ve gerekirse elle düzenleme nin daha kolay olduğu daha küçük proje dosyalarına yol açar.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-139">This leads to smaller project files that are easier to understand as well as edit by hand, if needed.</span></span>

<span data-ttu-id="0cf4a-140">Aşağıdaki tabloda .NET Core SDK'da hangi elementin ve hangi [globs'lerin](https://en.wikipedia.org/wiki/Glob_(programming)) dahil edildiği ve dışlandığı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="0cf4a-140">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are included and excluded in the .NET Core SDK:</span></span>

| <span data-ttu-id="0cf4a-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="0cf4a-141">Element</span></span>           | <span data-ttu-id="0cf4a-142">Glob dahil et</span><span class="sxs-lookup"><span data-stu-id="0cf4a-142">Include glob</span></span>                              | <span data-ttu-id="0cf4a-143">Glob hariç</span><span class="sxs-lookup"><span data-stu-id="0cf4a-143">Exclude glob</span></span>                                                  | <span data-ttu-id="0cf4a-144">Glob'u çıkarın</span><span class="sxs-lookup"><span data-stu-id="0cf4a-144">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| <span data-ttu-id="0cf4a-145">Derlemek</span><span class="sxs-lookup"><span data-stu-id="0cf4a-145">Compile</span></span>           | <span data-ttu-id="0cf4a-146">\*\*/\*.cs (veya diğer dil uzantıları)</span><span class="sxs-lookup"><span data-stu-id="0cf4a-146">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="0cf4a-147">\*\*/\*.kullanıcı;  \*\*/\*. \*proj;  \* \* / \*  \* \* / \*</span><span class="sxs-lookup"><span data-stu-id="0cf4a-147">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="0cf4a-148">Yok</span><span class="sxs-lookup"><span data-stu-id="0cf4a-148">N/A</span></span>                      |
| <span data-ttu-id="0cf4a-149">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="0cf4a-149">EmbeddedResource</span></span>  | <span data-ttu-id="0cf4a-150">\*\*/\*Resx</span><span class="sxs-lookup"><span data-stu-id="0cf4a-150">\*\*/\*.resx</span></span>                              | <span data-ttu-id="0cf4a-151">\*\*/\*.kullanıcı; \*\*/\*. \*proj; \* \* / \* \* \* / \*</span><span class="sxs-lookup"><span data-stu-id="0cf4a-151">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="0cf4a-152">Yok</span><span class="sxs-lookup"><span data-stu-id="0cf4a-152">N/A</span></span>                      |
| <span data-ttu-id="0cf4a-153">None</span><span class="sxs-lookup"><span data-stu-id="0cf4a-153">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="0cf4a-154">\*\*/\*.kullanıcı; \*\*/\*. \*proj; \* \* / \* \* \* / \*</span><span class="sxs-lookup"><span data-stu-id="0cf4a-154">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="0cf4a-155">\*\*/\*.cs; \* \* /.resx \*</span><span class="sxs-lookup"><span data-stu-id="0cf4a-155">\*\*/\*.cs; \*\*/\*.resx</span></span> |

> [!NOTE]
> <span data-ttu-id="0cf4a-156">`./bin` VE `./obj` `$(BaseOutputPath)` `$(BaseIntermediateOutputPath)` MSBuild özellikleri tarafından temsil edilen klasörler varsayılan olarak globs dışında tutulur.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-156">The `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, are excluded from the globs by default.</span></span> <span data-ttu-id="0cf4a-157">Hariç tutmalar özellik `$(DefaultItemExcludes)`tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-157">Excludes are represented by the property `$(DefaultItemExcludes)`.</span></span>

<span data-ttu-id="0cf4a-158">Proje dosyanızda bu öğeleri açıkça tanımlarsanız, büyük olasılıkla aşağıdaki hatayı alırsınız:</span><span class="sxs-lookup"><span data-stu-id="0cf4a-158">If you explicitly define these items in your project file, you're likely to get the following error:</span></span>

<span data-ttu-id="0cf4a-159">**Yinelenen Derleme öğeleri dahil edildi. .NET SDK varsayılan olarak proje dizininizdeki öğeleri derle içerir. Bu öğeleri proje dosyanızdan kaldırabilir veya proje dosyanıza açıkça eklemek istiyorsanız 'Varsayılan Derleme Öğeleri' özelliğini 'false' olarak ayarlayabilirsiniz.**</span><span class="sxs-lookup"><span data-stu-id="0cf4a-159">**Duplicate Compile items were included. The .NET SDK includes Compile items from your project directory by default. You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.**</span></span>

<span data-ttu-id="0cf4a-160">Hatayı gidermek için, önceki `Compile` tabloda listelenen örtük öğelerle eşleşen açık `EnableDefaultCompileItems` öğeleri `false`kaldırın veya özelliği örtük eklemeyi devre dışı bırakan "aşağıdakilere" göre ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="0cf4a-160">To resolve the error, either remove the explicit `Compile` items that match the implicit ones listed on the previous table, or set the `EnableDefaultCompileItems` property to `false`, which disables implicit inclusion:</span></span>

```xml
<PropertyGroup>
  <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

<span data-ttu-id="0cf4a-161">Örneğin, uygulamanızla birlikte yayımlanmak üzere bazı dosyaların belirtilmek isterseniz, örneğin bu öğe için bilinen MSBuild mekanizmalarını `Content` kullanmaya devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-161">If you want to specify, for example, some files to get published with your app, you can still use the known MSBuild mechanisms for that, for example, the `Content` element.</span></span>

<span data-ttu-id="0cf4a-162">`EnableDefaultCompileItems`yalnızca `Compile` globs devre dışı kalır, ancak .cs öğeleri `None` için \*de geçerli olan örtük glob gibi diğer globs etkilemez.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-162">`EnableDefaultCompileItems` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob that also applies to \*.cs items.</span></span> <span data-ttu-id="0cf4a-163">Bu nedenle, Visual Studio'daki \*Solution Explorer,.cs öğelerini projenin `None` bir parçası olarak, öğe olarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-163">Because of that, Solution Explorer in Visual Studio shows \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="0cf4a-164">Örtük `None` glob devre dışı `EnableDefaultNoneItems` kalmak `false`için, ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="0cf4a-164">To disable the implicit `None` glob, set `EnableDefaultNoneItems` to `false`:</span></span>

```xml
<PropertyGroup>
  <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

<span data-ttu-id="0cf4a-165">*Tüm* örtük globs devre dışı `EnableDefaultItems` kalmak `false`için, özelliği ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="0cf4a-165">To disable *all* implicit globs, set the `EnableDefaultItems` property to `false`:</span></span>

```xml
<PropertyGroup>
  <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="customize-the-build"></a><span data-ttu-id="0cf4a-166">Yapıyı özelleştirme</span><span class="sxs-lookup"><span data-stu-id="0cf4a-166">Customize the build</span></span>

<span data-ttu-id="0cf4a-167">Bir [yapıyı özelleştirmenin](/visualstudio/msbuild/customize-your-build)çeşitli yolları vardır.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-167">There are various ways to [customize a build](/visualstudio/msbuild/customize-your-build).</span></span> <span data-ttu-id="0cf4a-168">Bir özelliği bir [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) veya [dotnet](../tools/index.md) komutuna bağımsız değişken olarak geçirerek geçersiz kılmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-168">You may want to override a property by passing it as an argument to an [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) or [dotnet](../tools/index.md) command.</span></span> <span data-ttu-id="0cf4a-169">Özelliği proje dosyasına veya *Dizin.Build.props* dosyasına da ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-169">You can also add the property to the project file or to a *Directory.Build.props* file.</span></span> <span data-ttu-id="0cf4a-170">.NET Core projelerinin yararlı özelliklerinin listesi [için ,.NET Core SDK projeleri için MSBuild özelliklerine](msbuild-props.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-170">For a list of useful properties for .NET Core projects, see [MSBuild properties for .NET Core SDK projects](msbuild-props.md).</span></span>

### <a name="custom-targets"></a><span data-ttu-id="0cf4a-171">Özel hedefler</span><span class="sxs-lookup"><span data-stu-id="0cf4a-171">Custom targets</span></span>

<span data-ttu-id="0cf4a-172">.NET Core projeleri, paketi tüketen projeler tarafından kullanılmak üzere özel MSBuild hedeflerini ve özelliklerini paketleyebilir.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-172">.NET Core projects can package custom MSBuild targets and properties for use by projects that consume the package.</span></span> <span data-ttu-id="0cf4a-173">İstediğince bu tür genişletilebilirlik kullanın:</span><span class="sxs-lookup"><span data-stu-id="0cf4a-173">Use this type of extensibility when you want to:</span></span>

- <span data-ttu-id="0cf4a-174">Yapı işlemini genişletin.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-174">Extend the build process.</span></span>
- <span data-ttu-id="0cf4a-175">Oluşturulan dosyalar gibi yapı işleminin yapı yapılarının yapı yapılarına erişin.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-175">Access artifacts of the build process, such as generated files.</span></span>
- <span data-ttu-id="0cf4a-176">Yapının çağrıldığı yapılandırmayı denetleyin.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-176">Inspect the configuration under which the build is invoked.</span></span>

<span data-ttu-id="0cf4a-177">Dosyaları `<package_id>.targets` forma `<package_id>.props` veya (örneğin) `Contoso.Utility.UsefulStuff.targets`projenin *yapı* klasörüne yerleştirerek özel yapı hedefleri veya özellikleri eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-177">You add custom build targets or properties by placing files in the form `<package_id>.targets` or `<package_id>.props` (for example, `Contoso.Utility.UsefulStuff.targets`) in the *build* folder of the project.</span></span>

<span data-ttu-id="0cf4a-178">Aşağıdaki XML, [`dotnet pack`](../tools/dotnet-pack.md) ne paketlenir komutu söyleyen bir *.csproj* dosyasından bir parçacıktır.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-178">The following XML is a snippet from a *.csproj* file that instructs the [`dotnet pack`](../tools/dotnet-pack.md) command what to package.</span></span> <span data-ttu-id="0cf4a-179">Öğe, `<ItemGroup Label="dotnet pack instructions">` hedef dosyalarını paketin içindeki *yapı* klasörüne yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-179">The `<ItemGroup Label="dotnet pack instructions">` element places the targets files into the *build* folder inside the package.</span></span> <span data-ttu-id="0cf4a-180">Öğe `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` derlemeleri ve *.json* dosyalarını *yapı* klasörüne yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-180">The `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` element places the assemblies and *.json* files into the *build* folder.</span></span>

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

<span data-ttu-id="0cf4a-181">Projenizde özel bir hedef tüketmek `PackageReference` için pakete ve sürümüne işaret eden bir öğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-181">To consume a custom target in your project, add a `PackageReference` element that points to the package and its version.</span></span> <span data-ttu-id="0cf4a-182">Araçlardan farklı olarak, özel hedefler paketi, tüketen projenin bağımlılık kapatması dahildir.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-182">Unlike the tools, the custom targets package is included in the consuming project's dependency closure.</span></span>

<span data-ttu-id="0cf4a-183">Özel hedefin nasıl kullanılacağını yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-183">You can configure how to use the custom target.</span></span> <span data-ttu-id="0cf4a-184">Bir MSBuild hedefi olduğundan, belirli bir hedefe bağlı olabilir, başka bir hedefin peşinden koşabilir veya `dotnet msbuild -t:<target-name>` komutu kullanarak el ile çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-184">Since it's an MSBuild target, it can depend on a given target, run after another target, or be manually invoked by using the `dotnet msbuild -t:<target-name>` command.</span></span> <span data-ttu-id="0cf4a-185">Ancak, daha iyi bir kullanıcı deneyimi sağlamak için proje başına araçları ve özel hedefleri birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-185">However, to provide a better user experience, you can combine per-project tools and custom targets.</span></span> <span data-ttu-id="0cf4a-186">Bu senaryoda, proje başına araç gereken parametreleri kabul eder ve [`dotnet msbuild`](../tools/dotnet-msbuild.md) bunu hedefi yürüten gerekli çağrıya çevirir.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-186">In this scenario, the per-project tool accepts whatever parameters are needed and translates that into the required [`dotnet msbuild`](../tools/dotnet-msbuild.md) invocation that executes the target.</span></span> <span data-ttu-id="0cf4a-187">[Projedeki MVP Summit 2016 Hackathon örnekleri](https://github.com/dotnet/MVPSummitHackathon2016) repo'da [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) bu tür bir sinerji örneği görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-187">You can see a sample of this kind of synergy on the [MVP Summit 2016 Hackathon samples](https://github.com/dotnet/MVPSummitHackathon2016) repo in the [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) project.</span></span>

## <a name="see-also"></a><span data-ttu-id="0cf4a-188">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0cf4a-188">See also</span></span>

- [<span data-ttu-id="0cf4a-189">.NET Core'u yükle</span><span class="sxs-lookup"><span data-stu-id="0cf4a-189">Install .NET Core</span></span>](../install/index.md)
- [<span data-ttu-id="0cf4a-190">MSBuild proje SDK'ları nasıl kullanılır?</span><span class="sxs-lookup"><span data-stu-id="0cf4a-190">How to use MSBuild project SDKs</span></span>](/visualstudio/msbuild/how-to-use-project-sdk)
- [<span data-ttu-id="0cf4a-191">NuGet ile özel MSBuild hedeflerini ve sahnelerini paketle</span><span class="sxs-lookup"><span data-stu-id="0cf4a-191">Package custom MSBuild targets and props with NuGet</span></span>](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package)
