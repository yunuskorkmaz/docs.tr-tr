---
title: DotNet paketi command - .NET Core CLI
description: Dotnet paketi komut .NET Core projeniz için NuGet paketleri oluşturur.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 8c2569ec7598b21fe9b673176143d0e54b9eb065
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696825"
---
# <a name="dotnet-pack"></a><span data-ttu-id="dbb61-103">DotNet paketi</span><span class="sxs-lookup"><span data-stu-id="dbb61-103">dotnet pack</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="dbb61-104">Ad</span><span class="sxs-lookup"><span data-stu-id="dbb61-104">Name</span></span>

<span data-ttu-id="dbb61-105">`dotnet pack` -Kod bir NuGet paketi paketler.</span><span class="sxs-lookup"><span data-stu-id="dbb61-105">`dotnet pack` - Packs the code into a NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="dbb61-106">Özet</span><span class="sxs-lookup"><span data-stu-id="dbb61-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="dbb61-107">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="dbb61-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet pack [<PROJECT>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [--runtime] [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="dbb61-108">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="dbb61-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet pack [<PROJECT>] [-c|--configuration] [--include-source] [--include-symbols] [--no-build] [-o|--output]
    [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="dbb61-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dbb61-109">Description</span></span>

<span data-ttu-id="dbb61-110">`dotnet pack` Komutu Proje oluşturulur ve NuGet paketleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dbb61-110">The `dotnet pack` command builds the project and creates NuGet packages.</span></span> <span data-ttu-id="dbb61-111">Bu komut bir NuGet paketi sonucudur.</span><span class="sxs-lookup"><span data-stu-id="dbb61-111">The result of this command is a NuGet package.</span></span> <span data-ttu-id="dbb61-112">Varsa `--include-symbols` seçeneği varsa, hata ayıklama simgeleri içeren başka bir paket oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="dbb61-112">If the `--include-symbols` option is present, another package containing the debug symbols is created.</span></span>

<span data-ttu-id="dbb61-113">Paketlenmiş projenizin NuGet bağımlılıkları eklenir *.nuspec* düzgün bulunmaları dosya çözülmüş paketi yüklendiğinde.</span><span class="sxs-lookup"><span data-stu-id="dbb61-113">NuGet dependencies of the packed project are added to the *.nuspec* file, so they're properly resolved when the package is installed.</span></span> <span data-ttu-id="dbb61-114">Proje Proje başvuruları projesi içinde paketlenmiş değil.</span><span class="sxs-lookup"><span data-stu-id="dbb61-114">Project-to-project references aren't packaged inside the project.</span></span> <span data-ttu-id="dbb61-115">Şu anda proje proje bağımlılıkları varsa, her proje bir paket olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="dbb61-115">Currently, you must have a package per project if you have project-to-project dependencies.</span></span>

<span data-ttu-id="dbb61-116">Varsayılan olarak, `dotnet pack` projeyi ilk oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dbb61-116">By default, `dotnet pack` builds the project first.</span></span> <span data-ttu-id="dbb61-117">Bu davranışı önlemek isterseniz, geçirmek `--no-build` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="dbb61-117">If you wish to avoid this behavior, pass the `--no-build` option.</span></span> <span data-ttu-id="dbb61-118">Bu seçenek genellikle burada kodu daha önce oluşturulmuş bildiğiniz sürekli tümleştirme (CI) yapı senaryolarda kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="dbb61-118">This option is often useful in Continuous Integration (CI) build scenarios where you know the code was previously built.</span></span>

<span data-ttu-id="dbb61-119">MSBuild özellikleri sağlayabilir `dotnet pack` paketleme işleminin komutu.</span><span class="sxs-lookup"><span data-stu-id="dbb61-119">You can provide MSBuild properties to the `dotnet pack` command for the packing process.</span></span> <span data-ttu-id="dbb61-120">Daha fazla bilgi için bkz: [NuGet meta veri özelliklerini](csproj.md#nuget-metadata-properties) ve [MSBuild komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="dbb61-120">For more information, see [NuGet metadata properties](csproj.md#nuget-metadata-properties) and the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="dbb61-121">[Örnekler](#examples) bölüm nasıl MSBuild /p anahtarını birkaç farklı senaryo için kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="dbb61-121">The [Examples](#examples) section shows how to use the MSBuild /p switch for a couple of different scenarios.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="dbb61-122">Arguments</span><span class="sxs-lookup"><span data-stu-id="dbb61-122">Arguments</span></span>

`PROJECT`

<span data-ttu-id="dbb61-123">Paketi projesi.</span><span class="sxs-lookup"><span data-stu-id="dbb61-123">The project to pack.</span></span> <span data-ttu-id="dbb61-124">Her iki yolu olan bir [csproj dosya](csproj.md) veya bir dizin.</span><span class="sxs-lookup"><span data-stu-id="dbb61-124">It's either a path to a [csproj file](csproj.md) or to a directory.</span></span> <span data-ttu-id="dbb61-125">Belirtilmezse, geçerli dizine varsayılan olur.</span><span class="sxs-lookup"><span data-stu-id="dbb61-125">If not specified, it defaults to the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="dbb61-126">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="dbb61-126">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="dbb61-127">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="dbb61-127">.NET Core 2.x</span></span>](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="dbb61-128">Derleme yapılandırması tanımlar.</span><span class="sxs-lookup"><span data-stu-id="dbb61-128">Defines the build configuration.</span></span> <span data-ttu-id="dbb61-129">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="dbb61-129">The default value is `Debug`.</span></span>

`--force`

<span data-ttu-id="dbb61-130">Son geri yükleme başarılı olsa bile çözümlenmesi için tüm bağımlılıkları zorlar.</span><span class="sxs-lookup"><span data-stu-id="dbb61-130">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="dbb61-131">Bu bayrak belirten aynıdır silme *project.assets.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="dbb61-131">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="dbb61-132">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="dbb61-132">Prints out a short help for the command.</span></span>

`--include-source`

<span data-ttu-id="dbb61-133">NuGet paketi kaynak dosyaları içerir.</span><span class="sxs-lookup"><span data-stu-id="dbb61-133">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="dbb61-134">Kaynakları dosyaları içinde yer alan `src` klasör içinde `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="dbb61-134">The sources files are included in the `src` folder within the `nupkg`.</span></span>

`--include-symbols`

<span data-ttu-id="dbb61-135">Simgeler oluşturur `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="dbb61-135">Generates the symbols `nupkg`.</span></span>

`--no-build`

<span data-ttu-id="dbb61-136">Paketleme önce projeyi derleme değil.</span><span class="sxs-lookup"><span data-stu-id="dbb61-136">Doesn't build the project before packing.</span></span> <span data-ttu-id="dbb61-137">Ayrıca örtük ayarlar `--no-restore` bayrağı.</span><span class="sxs-lookup"><span data-stu-id="dbb61-137">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="dbb61-138">Proje Proje başvuruları yoksayar ve yalnızca kök proje geri yükler.</span><span class="sxs-lookup"><span data-stu-id="dbb61-138">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="dbb61-139">Örtük bir geri yükleme komutu çalıştırırken yürütmez.</span><span class="sxs-lookup"><span data-stu-id="dbb61-139">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="dbb61-140">Belirtilen dizinde yerleşik paketleri yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="dbb61-140">Places the built packages in the directory specified.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="dbb61-141">Paketler için geri yüklemek için hedef çalışma zamanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="dbb61-141">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="dbb61-142">Çalışma zamanı tanımlayıcıları (RID) bir listesi için bkz: [RID katalog](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="dbb61-142">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-s|--serviceable`

<span data-ttu-id="dbb61-143">Pakette hizmet verilebilen bayrağını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="dbb61-143">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="dbb61-144">Daha fazla bilgi için bkz: [.NET Blog: .NET 4.5.1'in destekleyen Microsoft güvenlik güncelleştirmeleri için .NET NuGet kitaplıkları](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="dbb61-144">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="dbb61-145">Değerini tanımlayan `$(VersionSuffix)` projesinde MSBuild özelliği.</span><span class="sxs-lookup"><span data-stu-id="dbb61-145">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="dbb61-146">Komutun ayrıntı düzeyi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="dbb61-146">Sets the verbosity level of the command.</span></span> <span data-ttu-id="dbb61-147">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="dbb61-147">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="dbb61-148">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="dbb61-148">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="dbb61-149">Derleme yapılandırması tanımlar.</span><span class="sxs-lookup"><span data-stu-id="dbb61-149">Defines the build configuration.</span></span> <span data-ttu-id="dbb61-150">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="dbb61-150">The default value is `Debug`.</span></span>

`-h|--help`

<span data-ttu-id="dbb61-151">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="dbb61-151">Prints out a short help for the command.</span></span>

`--include-source`

<span data-ttu-id="dbb61-152">NuGet paketi kaynak dosyaları içerir.</span><span class="sxs-lookup"><span data-stu-id="dbb61-152">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="dbb61-153">Kaynakları dosyaları içinde yer alan `src` klasör içinde `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="dbb61-153">The sources files are included in the `src` folder within the `nupkg`.</span></span>

`--include-symbols`

<span data-ttu-id="dbb61-154">Simgeler oluşturur `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="dbb61-154">Generates the symbols `nupkg`.</span></span>

`--no-build`

<span data-ttu-id="dbb61-155">Paketleme önce projeyi derleme değil.</span><span class="sxs-lookup"><span data-stu-id="dbb61-155">Doesn't build the project before packing.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="dbb61-156">Belirtilen dizinde yerleşik paketleri yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="dbb61-156">Places the built packages in the directory specified.</span></span>

`-s|--serviceable`

<span data-ttu-id="dbb61-157">Pakette hizmet verilebilen bayrağını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="dbb61-157">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="dbb61-158">Daha fazla bilgi için bkz: [.NET Blog: .NET 4.5.1'in destekleyen Microsoft güvenlik güncelleştirmeleri için .NET NuGet kitaplıkları](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="dbb61-158">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="dbb61-159">Değerini tanımlayan `$(VersionSuffix)` projesinde MSBuild özelliği.</span><span class="sxs-lookup"><span data-stu-id="dbb61-159">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="dbb61-160">Komutun ayrıntı düzeyi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="dbb61-160">Sets the verbosity level of the command.</span></span> <span data-ttu-id="dbb61-161">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="dbb61-161">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="dbb61-162">Örnekler</span><span class="sxs-lookup"><span data-stu-id="dbb61-162">Examples</span></span>

<span data-ttu-id="dbb61-163">Proje geçerli dizinde paketi:</span><span class="sxs-lookup"><span data-stu-id="dbb61-163">Pack the project in the current directory:</span></span>

`dotnet pack`

<span data-ttu-id="dbb61-164">Paketi `app1` proje:</span><span class="sxs-lookup"><span data-stu-id="dbb61-164">Pack the `app1` project:</span></span>

`dotnet pack ~/projects/app1/project.csproj`

<span data-ttu-id="dbb61-165">Geçerli dizinde projenin Paketle ve sonuçta elde edilen paketlere yerleştirin `nupkgs` klasörü:</span><span class="sxs-lookup"><span data-stu-id="dbb61-165">Pack the project in the current directory and place the resulting packages into the `nupkgs` folder:</span></span>

`dotnet pack --output nupkgs`

<span data-ttu-id="dbb61-166">Geçerli dizine içinde proje paketi `nupkgs` klasörü ve derleme adımı atla:</span><span class="sxs-lookup"><span data-stu-id="dbb61-166">Pack the project in the current directory into the `nupkgs` folder and skip the build step:</span></span>

`dotnet pack --no-build --output nupkgs`

<span data-ttu-id="dbb61-167">Proje ile Sürüm soneki olarak yapılandırılmış `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` içinde *.csproj* dosyası, geçerli projenin paketi ve sonuçta elde edilen paket sürümü verilen sonekiyle güncelleştirme:</span><span class="sxs-lookup"><span data-stu-id="dbb61-167">With the project's version suffix configured as `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` in the *.csproj* file, pack the current project and update the resulting package version with the given suffix:</span></span>

`dotnet pack --version-suffix "ci-1234"`

<span data-ttu-id="dbb61-168">Paket sürümü kümesine `2.1.0` ile `PackageVersion` MSBuild özelliği:</span><span class="sxs-lookup"><span data-stu-id="dbb61-168">Set the package version to `2.1.0` with the `PackageVersion` MSBuild property:</span></span>

`dotnet pack /p:PackageVersion=2.1.0`

<span data-ttu-id="dbb61-169">Belirli bir projenin paketi [hedef framework](../../standard/frameworks.md):</span><span class="sxs-lookup"><span data-stu-id="dbb61-169">Pack the project for a specific [target framework](../../standard/frameworks.md):</span></span>

`dotnet pack /p:TargetFrameworks=net45`

<span data-ttu-id="dbb61-170">Proje paketi ve geri yükleme işlemi (.NET Core SDK 2.0 ve sonraki sürümler) belirli bir çalışma zamanı (Windows 10) kullanın:</span><span class="sxs-lookup"><span data-stu-id="dbb61-170">Pack the project and use a specific runtime (Windows 10) for the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet pack --runtime win10-x64`