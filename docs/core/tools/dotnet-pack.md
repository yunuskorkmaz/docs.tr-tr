---
title: DotNet paketi komutu
description: DotNet Pack komutu, .NET Core projeniz için NuGet paketleri oluşturur.
ms.date: 12/04/2018
ms.openlocfilehash: c5c00f3bb06e5bc5579c0d3d6bdd39fbdf3db656
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202848"
---
# <a name="dotnet-pack"></a><span data-ttu-id="d2605-103">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="d2605-103">dotnet pack</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="d2605-104">Ad</span><span class="sxs-lookup"><span data-stu-id="d2605-104">Name</span></span>

<span data-ttu-id="d2605-105">`dotnet pack`-Kodu bir NuGet paketine paketler.</span><span class="sxs-lookup"><span data-stu-id="d2605-105">`dotnet pack` - Packs the code into a NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d2605-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="d2605-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="d2605-107">.NET Core 2. x</span><span class="sxs-lookup"><span data-stu-id="d2605-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```console
dotnet pack [<PROJECT>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [--runtime] [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d2605-108">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="d2605-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet pack [<PROJECT>] [-c|--configuration] [--include-source] [--include-symbols] [--no-build] [-o|--output]
    [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="d2605-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d2605-109">Description</span></span>

<span data-ttu-id="d2605-110">`dotnet pack` Komut projeyi oluşturur ve NuGet paketleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d2605-110">The `dotnet pack` command builds the project and creates NuGet packages.</span></span> <span data-ttu-id="d2605-111">Bu komutun sonucu bir NuGet paketidir.</span><span class="sxs-lookup"><span data-stu-id="d2605-111">The result of this command is a NuGet package.</span></span> <span data-ttu-id="d2605-112">`--include-symbols` Seçenek varsa, hata ayıklama sembollerini içeren başka bir paket oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d2605-112">If the `--include-symbols` option is present, another package containing the debug symbols is created.</span></span>

<span data-ttu-id="d2605-113">Paketlenmiş projenin NuGet bağımlılıkları *. nuspec* dosyasına eklenir, bu nedenle paket yüklenirken düzgün şekilde çözülür.</span><span class="sxs-lookup"><span data-stu-id="d2605-113">NuGet dependencies of the packed project are added to the *.nuspec* file, so they're properly resolved when the package is installed.</span></span> <span data-ttu-id="d2605-114">Projeden projeye başvurular proje içinde paketlenmemiş.</span><span class="sxs-lookup"><span data-stu-id="d2605-114">Project-to-project references aren't packaged inside the project.</span></span> <span data-ttu-id="d2605-115">Şu anda, projeden projeye bağımlılıklar varsa proje başına bir pakete sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d2605-115">Currently, you must have a package per project if you have project-to-project dependencies.</span></span>

<span data-ttu-id="d2605-116">Varsayılan olarak, `dotnet pack` önce projeyi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d2605-116">By default, `dotnet pack` builds the project first.</span></span> <span data-ttu-id="d2605-117">Bu davranışı önlemek istiyorsanız, `--no-build` seçeneğini geçirin.</span><span class="sxs-lookup"><span data-stu-id="d2605-117">If you wish to avoid this behavior, pass the `--no-build` option.</span></span> <span data-ttu-id="d2605-118">Bu seçenek genellikle kodun daha önce oluşturulduğunu bildiğiniz sürekli tümleştirme (CI) derleme senaryolarında yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="d2605-118">This option is often useful in Continuous Integration (CI) build scenarios where you know the code was previously built.</span></span>

<span data-ttu-id="d2605-119">Paketleme işlemi için `dotnet pack` komutuna MSBuild özellikleri sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2605-119">You can provide MSBuild properties to the `dotnet pack` command for the packing process.</span></span> <span data-ttu-id="d2605-120">Daha fazla bilgi için bkz. [NuGet meta veri özellikleri](csproj.md#nuget-metadata-properties) ve [MSBuild komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="d2605-120">For more information, see [NuGet metadata properties](csproj.md#nuget-metadata-properties) and the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="d2605-121">[Örnekler](#examples) bölümü, MSBuild-p anahtarının birkaç farklı senaryo için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d2605-121">The [Examples](#examples) section shows how to use the MSBuild -p switch for a couple of different scenarios.</span></span>

<span data-ttu-id="d2605-122">Web projeleri varsayılan olarak packable değildir.</span><span class="sxs-lookup"><span data-stu-id="d2605-122">Web projects aren't packable by default.</span></span> <span data-ttu-id="d2605-123">Varsayılan davranışı geçersiz kılmak için, *. csproj* dosyanıza aşağıdaki özelliği ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d2605-123">To override the default behavior, add the following property to your *.csproj* file:</span></span>

```xml
<PropertyGroup>
   <IsPackable>true</IsPackable>
</PropertyGroup>
```

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="d2605-124">Arguments</span><span class="sxs-lookup"><span data-stu-id="d2605-124">Arguments</span></span>

* **`PROJECT`**

  <span data-ttu-id="d2605-125">Paketedilecek proje.</span><span class="sxs-lookup"><span data-stu-id="d2605-125">The project to pack.</span></span> <span data-ttu-id="d2605-126">Bu, [csproj dosyasının](csproj.md) veya bir dizinin yoludur.</span><span class="sxs-lookup"><span data-stu-id="d2605-126">It's either a path to a [csproj file](csproj.md) or to a directory.</span></span> <span data-ttu-id="d2605-127">Belirtilmezse, varsayılan olarak geçerli dizini alır.</span><span class="sxs-lookup"><span data-stu-id="d2605-127">If not specified, it defaults to the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="d2605-128">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="d2605-128">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="d2605-129">.NET Core 2. x</span><span class="sxs-lookup"><span data-stu-id="d2605-129">.NET Core 2.x</span></span>](#tab/netcore2x)

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="d2605-130">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d2605-130">Defines the build configuration.</span></span> <span data-ttu-id="d2605-131">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="d2605-131">The default value is `Debug`.</span></span>

* **`--force`**

  <span data-ttu-id="d2605-132">Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar.</span><span class="sxs-lookup"><span data-stu-id="d2605-132">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="d2605-133">Bu bayrağın belirtilmesi, *Project. varlıklar. JSON* dosyasını silme ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="d2605-133">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

* **`-h|--help`**

  <span data-ttu-id="d2605-134">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="d2605-134">Prints out a short help for the command.</span></span>

* **`--include-source`**

  <span data-ttu-id="d2605-135">NuGet paketindeki kaynak dosyalarını içerir.</span><span class="sxs-lookup"><span data-stu-id="d2605-135">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="d2605-136">Kaynak dosyaları `src` `nupkg`içindeki klasörüne dahil edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d2605-136">The sources files are included in the `src` folder within the `nupkg`.</span></span>

* **`--include-symbols`**

  <span data-ttu-id="d2605-137">Sembolleri `nupkg`oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d2605-137">Generates the symbols `nupkg`.</span></span>

* **`--no-build`**

  <span data-ttu-id="d2605-138">Paketleme öncesinde projeyi oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="d2605-138">Doesn't build the project before packing.</span></span> <span data-ttu-id="d2605-139">Ayrıca `--no-restore` bayrağı örtülü olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d2605-139">It also implicitly sets the `--no-restore` flag.</span></span>

* **`--no-dependencies`**

  <span data-ttu-id="d2605-140">Projeden projeye başvuruları yoksayar ve yalnızca kök projeyi geri yükler.</span><span class="sxs-lookup"><span data-stu-id="d2605-140">Ignores project-to-project references and only restores the root project.</span></span>

* **`--no-restore`**

  <span data-ttu-id="d2605-141">Komutu çalıştırılırken örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="d2605-141">Doesn't execute an implicit restore when running the command.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="d2605-142">Oluşturulan paketleri belirtilen dizine koyar.</span><span class="sxs-lookup"><span data-stu-id="d2605-142">Places the built packages in the directory specified.</span></span>

* **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="d2605-143">Paketlerinin geri yükleneceği hedef çalışma zamanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2605-143">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="d2605-144">Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="d2605-144">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

* **`-s|--serviceable`**

  <span data-ttu-id="d2605-145">Paketteki hizmet verebilir bayrağını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d2605-145">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="d2605-146">Daha fazla bilgi için bkz. [.net blogu: .NET 4.5.1, .net NuGet kitaplıkları Için Microsoft güvenlik güncelleştirmelerini destekler](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="d2605-146">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

* **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="d2605-147">Projedeki `$(VersionSuffix)` MSBuild özelliğinin değerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d2605-147">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="d2605-148">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d2605-148">Sets the verbosity level of the command.</span></span> <span data-ttu-id="d2605-149">İzin verilen değerler `q[uiet]` `m[inimal]` ,`n[ormal]`,, ve .`diag[nostic]` `d[etailed]`</span><span class="sxs-lookup"><span data-stu-id="d2605-149">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d2605-150">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="d2605-150">.NET Core 1.x</span></span>](#tab/netcore1x)

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="d2605-151">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d2605-151">Defines the build configuration.</span></span> <span data-ttu-id="d2605-152">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="d2605-152">The default value is `Debug`.</span></span>

* **`-h|--help`**

  <span data-ttu-id="d2605-153">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="d2605-153">Prints out a short help for the command.</span></span>

* **`--include-source`**

  <span data-ttu-id="d2605-154">NuGet paketindeki kaynak dosyalarını içerir.</span><span class="sxs-lookup"><span data-stu-id="d2605-154">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="d2605-155">Kaynak dosyaları `src` `nupkg`içindeki klasörüne dahil edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d2605-155">The sources files are included in the `src` folder within the `nupkg`.</span></span>

* **`--include-symbols`**

  <span data-ttu-id="d2605-156">Sembolleri `nupkg`oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d2605-156">Generates the symbols `nupkg`.</span></span>

* **`--no-build`**

  <span data-ttu-id="d2605-157">Paketleme öncesinde projeyi oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="d2605-157">Doesn't build the project before packing.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="d2605-158">Oluşturulan paketleri belirtilen dizine koyar.</span><span class="sxs-lookup"><span data-stu-id="d2605-158">Places the built packages in the directory specified.</span></span>

* **`-s|--serviceable`**

  <span data-ttu-id="d2605-159">Paketteki hizmet verebilir bayrağını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d2605-159">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="d2605-160">Daha fazla bilgi için bkz. [.net blogu: .NET 4.5.1, .net NuGet kitaplıkları Için Microsoft güvenlik güncelleştirmelerini destekler](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="d2605-160">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

* **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="d2605-161">Projedeki `$(VersionSuffix)` MSBuild özelliğinin değerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d2605-161">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="d2605-162">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d2605-162">Sets the verbosity level of the command.</span></span> <span data-ttu-id="d2605-163">İzin verilen değerler `q[uiet]` `m[inimal]` ,`n[ormal]`,, ve .`diag[nostic]` `d[etailed]`</span><span class="sxs-lookup"><span data-stu-id="d2605-163">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="d2605-164">Örnekler</span><span class="sxs-lookup"><span data-stu-id="d2605-164">Examples</span></span>

* <span data-ttu-id="d2605-165">Projeyi geçerli dizinde paketleme:</span><span class="sxs-lookup"><span data-stu-id="d2605-165">Pack the project in the current directory:</span></span>

  ```console
  dotnet pack
  ```

* <span data-ttu-id="d2605-166">`app1` Projeyi paketleme:</span><span class="sxs-lookup"><span data-stu-id="d2605-166">Pack the `app1` project:</span></span>

  ```console
  dotnet pack ~/projects/app1/project.csproj
  ```

* <span data-ttu-id="d2605-167">Projeyi geçerli dizinde paketedin ve elde edilen paketleri `nupkgs` klasörüne yerleştirin:</span><span class="sxs-lookup"><span data-stu-id="d2605-167">Pack the project in the current directory and place the resulting packages into the `nupkgs` folder:</span></span>

  ```console
  dotnet pack --output nupkgs
  ```

* <span data-ttu-id="d2605-168">Geçerli dizindeki `nupkgs` projeyi klasöre paketlayın ve derleme adımını atlayın:</span><span class="sxs-lookup"><span data-stu-id="d2605-168">Pack the project in the current directory into the `nupkgs` folder and skip the build step:</span></span>

  ```console
  dotnet pack --no-build --output nupkgs
  ```

* <span data-ttu-id="d2605-169">Projenin sürüm soneki `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` *. csproj* dosyasında olarak yapılandırıldığında, geçerli projeyi paketleyin ve elde edilen paket sürümünü verilen sonek ile güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="d2605-169">With the project's version suffix configured as `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` in the *.csproj* file, pack the current project and update the resulting package version with the given suffix:</span></span>

  ```console
  dotnet pack --version-suffix "ci-1234"
  ```

* <span data-ttu-id="d2605-170">Paket sürümünü `PackageVersion` MSBuild özelliği ile `2.1.0` olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="d2605-170">Set the package version to `2.1.0` with the `PackageVersion` MSBuild property:</span></span>

  ```console
  dotnet pack -p:PackageVersion=2.1.0
  ```

* <span data-ttu-id="d2605-171">Projeyi belirli bir [hedef çerçeve](../../standard/frameworks.md)için paketleme:</span><span class="sxs-lookup"><span data-stu-id="d2605-171">Pack the project for a specific [target framework](../../standard/frameworks.md):</span></span>

  ```console
  dotnet pack -p:TargetFrameworks=net45
  ```

* <span data-ttu-id="d2605-172">Projeyi paketleme ve geri yükleme işlemi için belirli bir çalışma zamanı (Windows 10) kullanın (.NET Core SDK 2,0 ve sonraki sürümler):</span><span class="sxs-lookup"><span data-stu-id="d2605-172">Pack the project and use a specific runtime (Windows 10) for the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

  ```console
  dotnet pack --runtime win10-x64
  ```

* <span data-ttu-id="d2605-173">Bir [. nuspec dosyası](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec)kullanarak projeyi paketleme:</span><span class="sxs-lookup"><span data-stu-id="d2605-173">Pack the project using a [.nuspec file](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec):</span></span>

  ```console
  dotnet pack ~/projects/app1/project.csproj /p:NuspecFile=~/projects/app1/project.nuspec /p:NuspecBasePath=~/projects/app1/nuget
  ```
