---
title: DotNet paketi command - .NET Core CLI
description: "Dotnet paketi komut .NET Core projeniz için NuGet paketleri oluşturur."
author: mairaw
ms.author: mairaw
ms.date: 12/13/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: ac1ff90cb97fa4802883e70b0abdf4e77b58dd65
ms.sourcegitcommit: 8ed4ebc15b5ef89d06a7507dc9d5e306e30accf7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2017
---
# <a name="dotnet-pack"></a><span data-ttu-id="9e64d-103">DotNet paketi</span><span class="sxs-lookup"><span data-stu-id="9e64d-103">dotnet pack</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="9e64d-104">Ad</span><span class="sxs-lookup"><span data-stu-id="9e64d-104">Name</span></span>

<span data-ttu-id="9e64d-105">`dotnet pack`-Kod bir NuGet paketi paketler.</span><span class="sxs-lookup"><span data-stu-id="9e64d-105">`dotnet pack` - Packs the code into a NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9e64d-106">Özet</span><span class="sxs-lookup"><span data-stu-id="9e64d-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="9e64d-107">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="9e64d-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet pack [<PROJECT>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--no-build] [--no-dependencies] [--no-restore] [-o|--output] [--runtime] [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="9e64d-108">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="9e64d-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet pack [<PROJECT>] [-c|--configuration] [--include-source] [--include-symbols] [--no-build] [-o|--output] [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="9e64d-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9e64d-109">Description</span></span>

<span data-ttu-id="9e64d-110">`dotnet pack` Komutu Proje oluşturulur ve NuGet paketleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9e64d-110">The `dotnet pack` command builds the project and creates NuGet packages.</span></span> <span data-ttu-id="9e64d-111">Bu komut bir NuGet paketi sonucudur.</span><span class="sxs-lookup"><span data-stu-id="9e64d-111">The result of this command is a NuGet package.</span></span> <span data-ttu-id="9e64d-112">Varsa `--include-symbols` seçeneği varsa, hata ayıklama simgeleri içeren başka bir paket oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9e64d-112">If the `--include-symbols` option is present, another package containing the debug symbols is created.</span></span>

<span data-ttu-id="9e64d-113">Paketlenmiş projenizin NuGet bağımlılıkları eklenir *.nuspec* düzgün bulunmaları dosya çözülmüş paketi yüklendiğinde.</span><span class="sxs-lookup"><span data-stu-id="9e64d-113">NuGet dependencies of the packed project are added to the *.nuspec* file, so they're properly resolved when the package is installed.</span></span> <span data-ttu-id="9e64d-114">Proje Proje başvuruları projesi içinde paketlenmiş değil.</span><span class="sxs-lookup"><span data-stu-id="9e64d-114">Project-to-project references aren't packaged inside the project.</span></span> <span data-ttu-id="9e64d-115">Şu anda proje proje bağımlılıkları varsa, her proje bir paket olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9e64d-115">Currently, you must have a package per project if you have project-to-project dependencies.</span></span>

<span data-ttu-id="9e64d-116">Varsayılan olarak, `dotnet pack` projeyi ilk oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9e64d-116">By default, `dotnet pack` builds the project first.</span></span> <span data-ttu-id="9e64d-117">Bu davranışı önlemek isterseniz, geçirmek `--no-build` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="9e64d-117">If you wish to avoid this behavior, pass the `--no-build` option.</span></span> <span data-ttu-id="9e64d-118">Bu genellikle burada kodu daha önce oluşturulmuş bildiğiniz sürekli tümleştirme (CI) yapı senaryolarda kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="9e64d-118">This is often useful in Continuous Integration (CI) build scenarios where you know the code was previously built.</span></span>

<span data-ttu-id="9e64d-119">MSBuild özellikleri sağlayabilir `dotnet pack` paketleme işleminin komutu.</span><span class="sxs-lookup"><span data-stu-id="9e64d-119">You can provide MSBuild properties to the `dotnet pack` command for the packing process.</span></span> <span data-ttu-id="9e64d-120">Daha fazla bilgi için bkz: [NuGet meta veri özelliklerini](csproj.md#nuget-metadata-properties) ve [MSBuild komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="9e64d-120">For more information, see [NuGet metadata properties](csproj.md#nuget-metadata-properties) and the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="9e64d-121">[Örnekler](#examples) bölüm nasıl MSBuild /p anahtarını birkaç farklı senaryo için kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9e64d-121">The [Examples](#examples) section shows how to use the MSBuild /p switch for a couple of different scenarios.</span></span>

## <a name="arguments"></a><span data-ttu-id="9e64d-122">Arguments</span><span class="sxs-lookup"><span data-stu-id="9e64d-122">Arguments</span></span>

`PROJECT`

<span data-ttu-id="9e64d-123">Paketi projesi.</span><span class="sxs-lookup"><span data-stu-id="9e64d-123">The project to pack.</span></span> <span data-ttu-id="9e64d-124">Her iki yolu olan bir [csproj dosya](csproj.md) veya bir dizin.</span><span class="sxs-lookup"><span data-stu-id="9e64d-124">It's either a path to a [csproj file](csproj.md) or to a directory.</span></span> <span data-ttu-id="9e64d-125">Atlanırsa, geçerli dizine varsayılan olarak belirlenir.</span><span class="sxs-lookup"><span data-stu-id="9e64d-125">If omitted, it defaults to the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="9e64d-126">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="9e64d-126">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="9e64d-127">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="9e64d-127">.NET Core 2.x</span></span>](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="9e64d-128">Derleme yapılandırması tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9e64d-128">Defines the build configuration.</span></span> <span data-ttu-id="9e64d-129">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="9e64d-129">The default value is `Debug`.</span></span>

<span data-ttu-id="9e64d-130">`--force`Son geri yükleme başarılı olsa bile çözümlenmesi için tüm bağımlılıkları zorlar.</span><span class="sxs-lookup"><span data-stu-id="9e64d-130">`--force` Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="9e64d-131">Bu silme ile eşdeğerdir *project.assets.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="9e64d-131">This is equivalent to deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="9e64d-132">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="9e64d-132">Prints out a short help for the command.</span></span>

`--include-source`

<span data-ttu-id="9e64d-133">NuGet paketi kaynak dosyaları içerir.</span><span class="sxs-lookup"><span data-stu-id="9e64d-133">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="9e64d-134">Kaynakları dosyaları içinde yer alan `src` klasör içinde `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="9e64d-134">The sources files are included in the `src` folder within the `nupkg`.</span></span>

`--include-symbols`

<span data-ttu-id="9e64d-135">Simgeler oluşturur `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="9e64d-135">Generates the symbols `nupkg`.</span></span>

`--no-build`

<span data-ttu-id="9e64d-136">Paketleme önce projeyi derleme değil.</span><span class="sxs-lookup"><span data-stu-id="9e64d-136">Doesn't build the project before packing.</span></span>

`--no-dependencies`

<span data-ttu-id="9e64d-137">Proje Proje başvuruları yoksayar ve yalnızca kök proje geri yükler.</span><span class="sxs-lookup"><span data-stu-id="9e64d-137">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="9e64d-138">Örtük bir geri yükleme komutu çalıştırırken gerçekleştirmez.</span><span class="sxs-lookup"><span data-stu-id="9e64d-138">Doesn't perform an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="9e64d-139">Belirtilen dizinde yerleşik paketleri yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="9e64d-139">Places the built packages in the directory specified.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="9e64d-140">Paketler için geri yüklemek için hedef çalışma zamanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="9e64d-140">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="9e64d-141">Çalışma zamanı tanımlayıcıları (RID) bir listesi için bkz: [RID katalog](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="9e64d-141">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-s|--serviceable`

<span data-ttu-id="9e64d-142">Pakette hizmet verilebilen bayrağını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9e64d-142">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="9e64d-143">Daha fazla bilgi için bkz: [.NET Blog: .NET 4.5.1'in destekleyen Microsoft güvenlik güncelleştirmeleri için .NET NuGet kitaplıkları](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="9e64d-143">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="9e64d-144">Değerini tanımlayan `$(VersionSuffix)` projesinde MSBuild özelliği.</span><span class="sxs-lookup"><span data-stu-id="9e64d-144">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="9e64d-145">Komutun ayrıntı düzeyi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9e64d-145">Sets the verbosity level of the command.</span></span> <span data-ttu-id="9e64d-146">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="9e64d-146">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="9e64d-147">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="9e64d-147">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="9e64d-148">Derleme yapılandırması tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9e64d-148">Defines the build configuration.</span></span> <span data-ttu-id="9e64d-149">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="9e64d-149">The default value is `Debug`.</span></span>

`-h|--help`

<span data-ttu-id="9e64d-150">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="9e64d-150">Prints out a short help for the command.</span></span>

`--include-source`

<span data-ttu-id="9e64d-151">NuGet paketi kaynak dosyaları içerir.</span><span class="sxs-lookup"><span data-stu-id="9e64d-151">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="9e64d-152">Kaynakları dosyaları içinde yer alan `src` klasör içinde `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="9e64d-152">The sources files are included in the `src` folder within the `nupkg`.</span></span>

`--include-symbols`

<span data-ttu-id="9e64d-153">Simgeler oluşturur `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="9e64d-153">Generates the symbols `nupkg`.</span></span>

`--no-build`

<span data-ttu-id="9e64d-154">Paketleme önce projeyi derleme değil.</span><span class="sxs-lookup"><span data-stu-id="9e64d-154">Doesn't build the project before packing.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="9e64d-155">Belirtilen dizinde yerleşik paketleri yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="9e64d-155">Places the built packages in the directory specified.</span></span>

`-s|--serviceable`

<span data-ttu-id="9e64d-156">Pakette hizmet verilebilen bayrağını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9e64d-156">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="9e64d-157">Daha fazla bilgi için bkz: [.NET Blog: .NET 4.5.1'in destekleyen Microsoft güvenlik güncelleştirmeleri için .NET NuGet kitaplıkları](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="9e64d-157">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="9e64d-158">Değerini tanımlayan `$(VersionSuffix)` projesinde MSBuild özelliği.</span><span class="sxs-lookup"><span data-stu-id="9e64d-158">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="9e64d-159">Komutun ayrıntı düzeyi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9e64d-159">Sets the verbosity level of the command.</span></span> <span data-ttu-id="9e64d-160">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="9e64d-160">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="9e64d-161">Örnekler</span><span class="sxs-lookup"><span data-stu-id="9e64d-161">Examples</span></span>

<span data-ttu-id="9e64d-162">Proje geçerli dizinde paketi:</span><span class="sxs-lookup"><span data-stu-id="9e64d-162">Pack the project in the current directory:</span></span>

`dotnet pack`

<span data-ttu-id="9e64d-163">Paketi `app1` proje:</span><span class="sxs-lookup"><span data-stu-id="9e64d-163">Pack the `app1` project:</span></span>

`dotnet pack ~/projects/app1/project.csproj`
    
<span data-ttu-id="9e64d-164">Geçerli dizinde projenin Paketle ve sonuçta elde edilen paketlere yerleştirin `nupkgs` klasörü:</span><span class="sxs-lookup"><span data-stu-id="9e64d-164">Pack the project in the current directory and place the resulting packages into the `nupkgs` folder:</span></span>

`dotnet pack --output nupkgs`

<span data-ttu-id="9e64d-165">Geçerli dizine içinde proje paketi `nupkgs` klasörü ve derleme adımı atla:</span><span class="sxs-lookup"><span data-stu-id="9e64d-165">Pack the project in the current directory into the `nupkgs` folder and skip the build step:</span></span>

`dotnet pack --no-build --output nupkgs`

<span data-ttu-id="9e64d-166">Proje ile Sürüm soneki olarak yapılandırılmış `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` içinde *.csproj* dosyası, geçerli projenin paketi ve sonuçta elde edilen paket sürümü verilen sonekiyle güncelleştirme:</span><span class="sxs-lookup"><span data-stu-id="9e64d-166">With the project's version suffix configured as `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` in the *.csproj* file, pack the current project and update the resulting package version with the given suffix:</span></span>

`dotnet pack --version-suffix "ci-1234"`

<span data-ttu-id="9e64d-167">Paket sürümü kümesine `2.1.0` ile `PackageVersion` MSBuild özelliği:</span><span class="sxs-lookup"><span data-stu-id="9e64d-167">Set the package version to `2.1.0` with the `PackageVersion` MSBuild property:</span></span>

`dotnet pack /p:PackageVersion=2.1.0`

<span data-ttu-id="9e64d-168">Belirli bir projenin paketi [hedef framework](../../standard/frameworks.md):</span><span class="sxs-lookup"><span data-stu-id="9e64d-168">Pack the project for a specific [target framework](../../standard/frameworks.md):</span></span>

`dotnet pack /p:TargetFrameworks=net45`
