---
title: DotNet paketi command - .NET Core CLI
description: "Dotnet paketi komut .NET Core projeniz için NuGet paketleri oluşturur."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 8594c863d67baf0237b63e61f28ca9ee315eeddf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-pack"></a><span data-ttu-id="46b00-103">DotNet paketi</span><span class="sxs-lookup"><span data-stu-id="46b00-103">dotnet pack</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="46b00-104">Ad</span><span class="sxs-lookup"><span data-stu-id="46b00-104">Name</span></span>

<span data-ttu-id="46b00-105">`dotnet pack`-Kod bir NuGet paketi paketler.</span><span class="sxs-lookup"><span data-stu-id="46b00-105">`dotnet pack` - Packs the code into a NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="46b00-106">Özet</span><span class="sxs-lookup"><span data-stu-id="46b00-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="46b00-107">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="46b00-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet pack [<PROJECT>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--no-build] [--no-dependencies] [--no-restore] [-o|--output] [--runtime] [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="46b00-108">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="46b00-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet pack [<PROJECT>] [-c|--configuration] [--include-source] [--include-symbols] [--no-build] [-o|--output] [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="46b00-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="46b00-109">Description</span></span>

<span data-ttu-id="46b00-110">`dotnet pack` Komutu Proje oluşturulur ve NuGet paketleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="46b00-110">The `dotnet pack` command builds the project and creates NuGet packages.</span></span> <span data-ttu-id="46b00-111">Bu komut bir NuGet paketi sonucudur.</span><span class="sxs-lookup"><span data-stu-id="46b00-111">The result of this command is a NuGet package.</span></span> <span data-ttu-id="46b00-112">Varsa `--include-symbols` seçeneği varsa, hata ayıklama simgeleri içeren başka bir paket oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="46b00-112">If the `--include-symbols` option is present, another package containing the debug symbols is created.</span></span>

<span data-ttu-id="46b00-113">Paketlenmiş projenizin NuGet bağımlılıkları eklenir *.nuspec* düzgün bulunmaları dosya çözülmüş paketi yüklendiğinde.</span><span class="sxs-lookup"><span data-stu-id="46b00-113">NuGet dependencies of the packed project are added to the *.nuspec* file, so they're properly resolved when the package is installed.</span></span> <span data-ttu-id="46b00-114">Proje Proje başvuruları projesi içinde paketlenmiş değil.</span><span class="sxs-lookup"><span data-stu-id="46b00-114">Project-to-project references aren't packaged inside the project.</span></span> <span data-ttu-id="46b00-115">Şu anda proje proje bağımlılıkları varsa, her proje bir paket olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="46b00-115">Currently, you must have a package per project if you have project-to-project dependencies.</span></span>

<span data-ttu-id="46b00-116">Varsayılan olarak, `dotnet pack` projeyi ilk oluşturur.</span><span class="sxs-lookup"><span data-stu-id="46b00-116">By default, `dotnet pack` builds the project first.</span></span> <span data-ttu-id="46b00-117">Bu davranışı önlemek isterseniz, geçirmek `--no-build` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="46b00-117">If you wish to avoid this behavior, pass the `--no-build` option.</span></span> <span data-ttu-id="46b00-118">Bu genellikle burada kodu daha önce oluşturulmuş bildiğiniz sürekli tümleştirme (CI) yapı senaryolarda kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="46b00-118">This is often useful in Continuous Integration (CI) build scenarios where you know the code was previously built.</span></span>

<span data-ttu-id="46b00-119">MSBuild özellikleri sağlayabilir `dotnet pack` paketleme işleminin komutu.</span><span class="sxs-lookup"><span data-stu-id="46b00-119">You can provide MSBuild properties to the `dotnet pack` command for the packing process.</span></span> <span data-ttu-id="46b00-120">Daha fazla bilgi için bkz: [NuGet meta veri özelliklerini](csproj.md#nuget-metadata-properties) ve [MSBuild komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="46b00-120">For more information, see [NuGet metadata properties](csproj.md#nuget-metadata-properties) and the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

## <a name="arguments"></a><span data-ttu-id="46b00-121">Arguments</span><span class="sxs-lookup"><span data-stu-id="46b00-121">Arguments</span></span>

`PROJECT`

<span data-ttu-id="46b00-122">Paketi projesi.</span><span class="sxs-lookup"><span data-stu-id="46b00-122">The project to pack.</span></span> <span data-ttu-id="46b00-123">Her iki yolu olan bir [csproj dosya](csproj.md) veya bir dizin.</span><span class="sxs-lookup"><span data-stu-id="46b00-123">It's either a path to a [csproj file](csproj.md) or to a directory.</span></span> <span data-ttu-id="46b00-124">Atlanırsa, geçerli dizine varsayılan olarak belirlenir.</span><span class="sxs-lookup"><span data-stu-id="46b00-124">If omitted, it defaults to the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="46b00-125">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="46b00-125">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="46b00-126">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="46b00-126">.NET Core 2.x</span></span>](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="46b00-127">Derleme yapılandırması tanımlar.</span><span class="sxs-lookup"><span data-stu-id="46b00-127">Defines the build configuration.</span></span> <span data-ttu-id="46b00-128">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="46b00-128">The default value is `Debug`.</span></span>

<span data-ttu-id="46b00-129">`--force`Son geri yükleme başarılı olsa bile çözümlenmesi için tüm bağımlılıkları zorlar.</span><span class="sxs-lookup"><span data-stu-id="46b00-129">`--force` Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="46b00-130">Bu silme ile eşdeğerdir *project.assets.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="46b00-130">This is equivalent to deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="46b00-131">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="46b00-131">Prints out a short help for the command.</span></span>

`--include-source`

<span data-ttu-id="46b00-132">NuGet paketi kaynak dosyaları içerir.</span><span class="sxs-lookup"><span data-stu-id="46b00-132">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="46b00-133">Kaynakları dosyaları içinde yer alan `src` klasör içinde `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="46b00-133">The sources files are included in the `src` folder within the `nupkg`.</span></span>

`--include-symbols`

<span data-ttu-id="46b00-134">Simgeler oluşturur `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="46b00-134">Generates the symbols `nupkg`.</span></span>

`--no-build`

<span data-ttu-id="46b00-135">Paketleme önce projeyi derleme değil.</span><span class="sxs-lookup"><span data-stu-id="46b00-135">Doesn't build the project before packing.</span></span>

`--no-dependencies`

<span data-ttu-id="46b00-136">Proje Proje başvuruları yoksayar ve yalnızca kök proje geri yükler.</span><span class="sxs-lookup"><span data-stu-id="46b00-136">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="46b00-137">Örtük bir geri yükleme komutu çalıştırırken gerçekleştirmez.</span><span class="sxs-lookup"><span data-stu-id="46b00-137">Doesn't perform an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="46b00-138">Belirtilen dizinde yerleşik paketleri yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="46b00-138">Places the built packages in the directory specified.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="46b00-139">Paketler için geri yüklemek için hedef çalışma zamanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="46b00-139">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="46b00-140">Çalışma zamanı tanımlayıcıları (RID) bir listesi için bkz: [RID katalog](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="46b00-140">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-s|--serviceable`

<span data-ttu-id="46b00-141">Pakette hizmet verilebilen bayrağını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="46b00-141">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="46b00-142">Daha fazla bilgi için bkz: [.NET Blog: .NET 4.5.1'in destekleyen Microsoft güvenlik güncelleştirmeleri için .NET NuGet kitaplıkları](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="46b00-142">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="46b00-143">Değerini tanımlayan `$(VersionSuffix)` projesinde MSBuild özelliği.</span><span class="sxs-lookup"><span data-stu-id="46b00-143">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="46b00-144">Komutun ayrıntı düzeyi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="46b00-144">Sets the verbosity level of the command.</span></span> <span data-ttu-id="46b00-145">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="46b00-145">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="46b00-146">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="46b00-146">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="46b00-147">Derleme yapılandırması tanımlar.</span><span class="sxs-lookup"><span data-stu-id="46b00-147">Defines the build configuration.</span></span> <span data-ttu-id="46b00-148">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="46b00-148">The default value is `Debug`.</span></span>

`-h|--help`

<span data-ttu-id="46b00-149">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="46b00-149">Prints out a short help for the command.</span></span>

`--include-source`

<span data-ttu-id="46b00-150">NuGet paketi kaynak dosyaları içerir.</span><span class="sxs-lookup"><span data-stu-id="46b00-150">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="46b00-151">Kaynakları dosyaları içinde yer alan `src` klasör içinde `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="46b00-151">The sources files are included in the `src` folder within the `nupkg`.</span></span>

`--include-symbols`

<span data-ttu-id="46b00-152">Simgeler oluşturur `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="46b00-152">Generates the symbols `nupkg`.</span></span>

`--no-build`

<span data-ttu-id="46b00-153">Paketleme önce projeyi derleme değil.</span><span class="sxs-lookup"><span data-stu-id="46b00-153">Doesn't build the project before packing.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="46b00-154">Belirtilen dizinde yerleşik paketleri yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="46b00-154">Places the built packages in the directory specified.</span></span>

`-s|--serviceable`

<span data-ttu-id="46b00-155">Pakette hizmet verilebilen bayrağını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="46b00-155">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="46b00-156">Daha fazla bilgi için bkz: [.NET Blog: .NET 4.5.1'in destekleyen Microsoft güvenlik güncelleştirmeleri için .NET NuGet kitaplıkları](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="46b00-156">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="46b00-157">Değerini tanımlayan `$(VersionSuffix)` projesinde MSBuild özelliği.</span><span class="sxs-lookup"><span data-stu-id="46b00-157">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="46b00-158">Komutun ayrıntı düzeyi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="46b00-158">Sets the verbosity level of the command.</span></span> <span data-ttu-id="46b00-159">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="46b00-159">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="46b00-160">Örnekler</span><span class="sxs-lookup"><span data-stu-id="46b00-160">Examples</span></span>

<span data-ttu-id="46b00-161">Proje geçerli dizinde paketi:</span><span class="sxs-lookup"><span data-stu-id="46b00-161">Pack the project in the current directory:</span></span>

`dotnet pack`

<span data-ttu-id="46b00-162">Paketi `app1` proje:</span><span class="sxs-lookup"><span data-stu-id="46b00-162">Pack the `app1` project:</span></span>

`dotnet pack ~/projects/app1/project.csproj`
    
<span data-ttu-id="46b00-163">Geçerli dizinde projenin Paketle ve sonuçta elde edilen paketlere yerleştirin `nupkgs` klasörü:</span><span class="sxs-lookup"><span data-stu-id="46b00-163">Pack the project in the current directory and place the resulting packages into the `nupkgs` folder:</span></span>

`dotnet pack --output nupkgs`

<span data-ttu-id="46b00-164">Geçerli dizine içinde proje paketi `nupkgs` klasörü ve derleme adımı atla:</span><span class="sxs-lookup"><span data-stu-id="46b00-164">Pack the project in the current directory into the `nupkgs` folder and skip the build step:</span></span>

`dotnet pack --no-build --output nupkgs`

<span data-ttu-id="46b00-165">Proje ile Sürüm soneki olarak yapılandırılmış `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` içinde *.csproj* dosyası, geçerli projenin paketi ve sonuçta elde edilen paket sürümü verilen sonekiyle güncelleştirme:</span><span class="sxs-lookup"><span data-stu-id="46b00-165">With the project's version suffix configured as `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` in the *.csproj* file, pack the current project and update the resulting package version with the given suffix:</span></span>

`dotnet pack --version-suffix "ci-1234"`

<span data-ttu-id="46b00-166">Paket sürümü kümesine `2.1.0` ile `PackageVersion` MSBuild özelliği:</span><span class="sxs-lookup"><span data-stu-id="46b00-166">Set the package version to `2.1.0` with the `PackageVersion` MSBuild property:</span></span>

`dotnet pack /p:PackageVersion=2.1.0`
