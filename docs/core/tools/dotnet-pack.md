---
title: DotNet paketi command - .NET Core CLI
description: Dotnet paketi komut, .NET Core projesi için NuGet paketlerini oluşturur.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 434f1c97af24d1417cd79edd52b63814fd4c6512
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47231194"
---
# <a name="dotnet-pack"></a><span data-ttu-id="59cb3-103">DotNet paketi</span><span class="sxs-lookup"><span data-stu-id="59cb3-103">dotnet pack</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="59cb3-104">Ad</span><span class="sxs-lookup"><span data-stu-id="59cb3-104">Name</span></span>

<span data-ttu-id="59cb3-105">`dotnet pack` -Kod bir NuGet paketine paketleri.</span><span class="sxs-lookup"><span data-stu-id="59cb3-105">`dotnet pack` - Packs the code into a NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="59cb3-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="59cb3-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="59cb3-107">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="59cb3-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet pack [<PROJECT>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [--runtime] [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="59cb3-108">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="59cb3-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet pack [<PROJECT>] [-c|--configuration] [--include-source] [--include-symbols] [--no-build] [-o|--output]
    [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="59cb3-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="59cb3-109">Description</span></span>

<span data-ttu-id="59cb3-110">`dotnet pack` Komut projeyi derler ve NuGet paketleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="59cb3-110">The `dotnet pack` command builds the project and creates NuGet packages.</span></span> <span data-ttu-id="59cb3-111">Bu komutun sonucuna ilişkin bir NuGet paketidir.</span><span class="sxs-lookup"><span data-stu-id="59cb3-111">The result of this command is a NuGet package.</span></span> <span data-ttu-id="59cb3-112">Varsa `--include-symbols` seçeneği varsa, hata ayıklama sembolleri içeren başka bir paket oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="59cb3-112">If the `--include-symbols` option is present, another package containing the debug symbols is created.</span></span>

<span data-ttu-id="59cb3-113">Paketlenmiş proje, NuGet bağımlılıklarını eklenir *.nuspec* düzgün bulunmaları dosyası, çözümlenen paketi yüklendiğinde.</span><span class="sxs-lookup"><span data-stu-id="59cb3-113">NuGet dependencies of the packed project are added to the *.nuspec* file, so they're properly resolved when the package is installed.</span></span> <span data-ttu-id="59cb3-114">Projeden projeye başvurular projesi içinde paketlendi değildir.</span><span class="sxs-lookup"><span data-stu-id="59cb3-114">Project-to-project references aren't packaged inside the project.</span></span> <span data-ttu-id="59cb3-115">Şu anda projeden projeye bağımlılıkları varsa, her proje bir paket olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="59cb3-115">Currently, you must have a package per project if you have project-to-project dependencies.</span></span>

<span data-ttu-id="59cb3-116">Varsayılan olarak, `dotnet pack` önce projeyi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="59cb3-116">By default, `dotnet pack` builds the project first.</span></span> <span data-ttu-id="59cb3-117">Bu davranışı engellemek istiyorsanız, geçmesi `--no-build` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="59cb3-117">If you wish to avoid this behavior, pass the `--no-build` option.</span></span> <span data-ttu-id="59cb3-118">Bu seçenek genellikle kod daha önce oluşturulmuş bildiğiniz sürekli tümleştirme (CI) derleme senaryolarda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="59cb3-118">This option is often useful in Continuous Integration (CI) build scenarios where you know the code was previously built.</span></span>

<span data-ttu-id="59cb3-119">MSBuild özellikleri sağlayabilir `dotnet pack` paketleme işlemi için komutu.</span><span class="sxs-lookup"><span data-stu-id="59cb3-119">You can provide MSBuild properties to the `dotnet pack` command for the packing process.</span></span> <span data-ttu-id="59cb3-120">Daha fazla bilgi için [NuGet meta veri özelliklerini](csproj.md#nuget-metadata-properties) ve [MSBuild komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="59cb3-120">For more information, see [NuGet metadata properties](csproj.md#nuget-metadata-properties) and the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="59cb3-121">[Örnekler](#examples) bölüm birkaç farklı senaryolar için MSBuild -p anahtar kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="59cb3-121">The [Examples](#examples) section shows how to use the MSBuild -p switch for a couple of different scenarios.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="59cb3-122">Arguments</span><span class="sxs-lookup"><span data-stu-id="59cb3-122">Arguments</span></span>

`PROJECT`

<span data-ttu-id="59cb3-123">Paketi için proje.</span><span class="sxs-lookup"><span data-stu-id="59cb3-123">The project to pack.</span></span> <span data-ttu-id="59cb3-124">Ya da bir yolu olan bir [csproj dosyasını](csproj.md) veya bir dizine.</span><span class="sxs-lookup"><span data-stu-id="59cb3-124">It's either a path to a [csproj file](csproj.md) or to a directory.</span></span> <span data-ttu-id="59cb3-125">Belirtilmezse, geçerli dizin için varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="59cb3-125">If not specified, it defaults to the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="59cb3-126">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="59cb3-126">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="59cb3-127">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="59cb3-127">.NET Core 2.x</span></span>](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="59cb3-128">Derleme yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="59cb3-128">Defines the build configuration.</span></span> <span data-ttu-id="59cb3-129">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="59cb3-129">The default value is `Debug`.</span></span>

`--force`

<span data-ttu-id="59cb3-130">Son geri yükleme başarılı olduysa bile çözülmesi için tüm bağımlılıkların zorlar.</span><span class="sxs-lookup"><span data-stu-id="59cb3-130">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="59cb3-131">Bu bayrak belirten aynıdır silme *project.assets.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="59cb3-131">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="59cb3-132">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="59cb3-132">Prints out a short help for the command.</span></span>

`--include-source`

<span data-ttu-id="59cb3-133">NuGet paketinin kaynak dosyaları içerir.</span><span class="sxs-lookup"><span data-stu-id="59cb3-133">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="59cb3-134">Kaynak dosyaların dahil `src` klasördeki `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="59cb3-134">The sources files are included in the `src` folder within the `nupkg`.</span></span>

`--include-symbols`

<span data-ttu-id="59cb3-135">Sembolleri oluşturur `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="59cb3-135">Generates the symbols `nupkg`.</span></span>

`--no-build`

<span data-ttu-id="59cb3-136">Paketleme önce projenizi değil.</span><span class="sxs-lookup"><span data-stu-id="59cb3-136">Doesn't build the project before packing.</span></span> <span data-ttu-id="59cb3-137">Ayrıca örtülü ayarlar `--no-restore` bayrağı.</span><span class="sxs-lookup"><span data-stu-id="59cb3-137">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="59cb3-138">Projeden projeye başvurular yoksayar ve yalnızca kök proje geri yükler.</span><span class="sxs-lookup"><span data-stu-id="59cb3-138">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="59cb3-139">Örtük bir geri yükleme komutu çalıştırırken yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="59cb3-139">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="59cb3-140">Yerleşik paketler belirtilen dizine yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="59cb3-140">Places the built packages in the directory specified.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="59cb3-141">Paketleri geri yüklemek için hedef çalışma zamanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="59cb3-141">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="59cb3-142">Çalışma zamanı tanımlayıcılarının (RID'ler) bir listesi için bkz. [RID Kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="59cb3-142">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-s|--serviceable`

<span data-ttu-id="59cb3-143">Pakette tutulabilmesi bayrağını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="59cb3-143">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="59cb3-144">Daha fazla bilgi için [.NET Blog: .NET 4.5.1 destekleyen Microsoft güvenlik güncelleştirmeleri için .NET NuGet kitaplıklarını](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="59cb3-144">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="59cb3-145">Değerini tanımlayan `$(VersionSuffix)` projesinde MSBuild özelliği.</span><span class="sxs-lookup"><span data-stu-id="59cb3-145">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="59cb3-146">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="59cb3-146">Sets the verbosity level of the command.</span></span> <span data-ttu-id="59cb3-147">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="59cb3-147">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

> [!NOTE]
> <span data-ttu-id="59cb3-148">Web projeleri, varsayılan olarak packable değildir.</span><span class="sxs-lookup"><span data-stu-id="59cb3-148">Web projects aren't packable by default.</span></span> <span data-ttu-id="59cb3-149">Varsayılan davranışı geçersiz kılmak için aşağıdaki özelliği ekleyin, *.csproj* dosyası:</span><span class="sxs-lookup"><span data-stu-id="59cb3-149">To override the default behavior, add the following property to your *.csproj* file:</span></span>
> ```xml
> <PropertyGroup>
>    <IsPackable>true</IsPackable>
> </PropertyGroup>
> ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="59cb3-150">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="59cb3-150">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="59cb3-151">Derleme yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="59cb3-151">Defines the build configuration.</span></span> <span data-ttu-id="59cb3-152">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="59cb3-152">The default value is `Debug`.</span></span>

`-h|--help`

<span data-ttu-id="59cb3-153">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="59cb3-153">Prints out a short help for the command.</span></span>

`--include-source`

<span data-ttu-id="59cb3-154">NuGet paketinin kaynak dosyaları içerir.</span><span class="sxs-lookup"><span data-stu-id="59cb3-154">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="59cb3-155">Kaynak dosyaların dahil `src` klasördeki `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="59cb3-155">The sources files are included in the `src` folder within the `nupkg`.</span></span>

`--include-symbols`

<span data-ttu-id="59cb3-156">Sembolleri oluşturur `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="59cb3-156">Generates the symbols `nupkg`.</span></span>

`--no-build`

<span data-ttu-id="59cb3-157">Paketleme önce projenizi değil.</span><span class="sxs-lookup"><span data-stu-id="59cb3-157">Doesn't build the project before packing.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="59cb3-158">Yerleşik paketler belirtilen dizine yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="59cb3-158">Places the built packages in the directory specified.</span></span>

`-s|--serviceable`

<span data-ttu-id="59cb3-159">Pakette tutulabilmesi bayrağını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="59cb3-159">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="59cb3-160">Daha fazla bilgi için [.NET Blog: .NET 4.5.1 destekleyen Microsoft güvenlik güncelleştirmeleri için .NET NuGet kitaplıklarını](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="59cb3-160">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="59cb3-161">Değerini tanımlayan `$(VersionSuffix)` projesinde MSBuild özelliği.</span><span class="sxs-lookup"><span data-stu-id="59cb3-161">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="59cb3-162">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="59cb3-162">Sets the verbosity level of the command.</span></span> <span data-ttu-id="59cb3-163">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="59cb3-163">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="59cb3-164">Örnekler</span><span class="sxs-lookup"><span data-stu-id="59cb3-164">Examples</span></span>

<span data-ttu-id="59cb3-165">Geçerli dizindeki proje paketi:</span><span class="sxs-lookup"><span data-stu-id="59cb3-165">Pack the project in the current directory:</span></span>

`dotnet pack`

<span data-ttu-id="59cb3-166">Paketi `app1` proje:</span><span class="sxs-lookup"><span data-stu-id="59cb3-166">Pack the `app1` project:</span></span>

`dotnet pack ~/projects/app1/project.csproj`

<span data-ttu-id="59cb3-167">Geçerli dizinde proje pack ve sonuçta elde edilen paketler halinde yerleştirin `nupkgs` klasörü:</span><span class="sxs-lookup"><span data-stu-id="59cb3-167">Pack the project in the current directory and place the resulting packages into the `nupkgs` folder:</span></span>

`dotnet pack --output nupkgs`

<span data-ttu-id="59cb3-168">Geçerli dizinde içinde proje pack `nupkgs` klasörü ve derleme adımı atla:</span><span class="sxs-lookup"><span data-stu-id="59cb3-168">Pack the project in the current directory into the `nupkgs` folder and skip the build step:</span></span>

`dotnet pack --no-build --output nupkgs`

<span data-ttu-id="59cb3-169">Projeyle Sürüm soneki olarak yapılandırılmış `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` içinde *.csproj* dosya, geçerli proje pack ve elde edilen paket sürümü ile belirtilen sonek güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="59cb3-169">With the project's version suffix configured as `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` in the *.csproj* file, pack the current project and update the resulting package version with the given suffix:</span></span>

`dotnet pack --version-suffix "ci-1234"`

<span data-ttu-id="59cb3-170">Paket sürümü kümesine `2.1.0` ile `PackageVersion` MSBuild özelliği:</span><span class="sxs-lookup"><span data-stu-id="59cb3-170">Set the package version to `2.1.0` with the `PackageVersion` MSBuild property:</span></span>

`dotnet pack -p:PackageVersion=2.1.0`

<span data-ttu-id="59cb3-171">Belirli bir proje pack [hedef Framework'ü](../../standard/frameworks.md):</span><span class="sxs-lookup"><span data-stu-id="59cb3-171">Pack the project for a specific [target framework](../../standard/frameworks.md):</span></span>

`dotnet pack -p:TargetFrameworks=net45`

<span data-ttu-id="59cb3-172">Proje paketi ve belirli bir çalışma zamanı (Windows 10) geri yükleme işlemi için (.NET Core SDK 2.0 ve sonraki sürümler) kullanın:</span><span class="sxs-lookup"><span data-stu-id="59cb3-172">Pack the project and use a specific runtime (Windows 10) for the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet pack --runtime win10-x64`
