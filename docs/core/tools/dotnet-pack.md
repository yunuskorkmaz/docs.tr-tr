---
title: DotNet paketi komutu
description: DotNet Pack komutu, .NET Core projeniz için NuGet paketleri oluşturur.
ms.date: 08/08/2019
ms.openlocfilehash: c230fa201fce02ab537afc4e14468788d32b8c8a
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71039475"
---
# <a name="dotnet-pack"></a><span data-ttu-id="d617d-103">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="d617d-103">dotnet pack</span></span>

<span data-ttu-id="d617d-104">**Bu konu şu şekilde geçerlidir: ✓** .NET Core 1. x SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="d617d-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="d617d-105">Ad</span><span class="sxs-lookup"><span data-stu-id="d617d-105">Name</span></span>

<span data-ttu-id="d617d-106">`dotnet pack`-Kodu bir NuGet paketine paketler.</span><span class="sxs-lookup"><span data-stu-id="d617d-106">`dotnet pack` - Packs the code into a NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d617d-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="d617d-107">Synopsis</span></span>

```console
dotnet pack [<PROJECT>|<SOLUTION>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--interactive] 
    [--no-build] [--no-dependencies] [--no-restore] [--nologo] [-o|--output] [--runtime] [-s|--serviceable] 
    [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

## <a name="description"></a><span data-ttu-id="d617d-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d617d-108">Description</span></span>

<span data-ttu-id="d617d-109">`dotnet pack` Komut projeyi oluşturur ve NuGet paketleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d617d-109">The `dotnet pack` command builds the project and creates NuGet packages.</span></span> <span data-ttu-id="d617d-110">Bu komutun sonucu bir NuGet paketidir (yani, bir *. nupkg* dosyası).</span><span class="sxs-lookup"><span data-stu-id="d617d-110">The result of this command is a NuGet package (that is, a *.nupkg* file).</span></span> 

<span data-ttu-id="d617d-111">Hata ayıklama sembollerini içeren bir paket oluşturmak istiyorsanız iki seçeneğiniz vardır:</span><span class="sxs-lookup"><span data-stu-id="d617d-111">If you want to generate a package that contains the debug symbols, you have two options available:</span></span>

- <span data-ttu-id="d617d-112">`--include-symbols`-Bu, semboller paketini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d617d-112">`--include-symbols` - it creates the symbols package.</span></span>
- <span data-ttu-id="d617d-113">`--include-source`-Bu, kaynak dosyaları içeren içindeki bir `src` klasörü içeren semboller paketini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d617d-113">`--include-source` - it creates the symbols package with a `src` folder inside containing the source files.</span></span>

<span data-ttu-id="d617d-114">Paketlenmiş projenin NuGet bağımlılıkları *. nuspec* dosyasına eklenir, bu nedenle paket yüklenirken düzgün şekilde çözülür.</span><span class="sxs-lookup"><span data-stu-id="d617d-114">NuGet dependencies of the packed project are added to the *.nuspec* file, so they're properly resolved when the package is installed.</span></span> <span data-ttu-id="d617d-115">Projeden projeye başvurular proje içinde paketlenmemiş.</span><span class="sxs-lookup"><span data-stu-id="d617d-115">Project-to-project references aren't packaged inside the project.</span></span> <span data-ttu-id="d617d-116">Şu anda, projeden projeye bağımlılıklar varsa proje başına bir pakete sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d617d-116">Currently, you must have a package per project if you have project-to-project dependencies.</span></span>

<span data-ttu-id="d617d-117">Varsayılan olarak, `dotnet pack` önce projeyi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d617d-117">By default, `dotnet pack` builds the project first.</span></span> <span data-ttu-id="d617d-118">Bu davranışı önlemek istiyorsanız, `--no-build` seçeneğini geçirin.</span><span class="sxs-lookup"><span data-stu-id="d617d-118">If you wish to avoid this behavior, pass the `--no-build` option.</span></span> <span data-ttu-id="d617d-119">Bu seçenek genellikle kodun daha önce oluşturulduğunu bildiğiniz sürekli tümleştirme (CI) derleme senaryolarında yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="d617d-119">This option is often useful in Continuous Integration (CI) build scenarios where you know the code was previously built.</span></span>

<span data-ttu-id="d617d-120">Paketleme işlemi için `dotnet pack` komutuna MSBuild özellikleri sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d617d-120">You can provide MSBuild properties to the `dotnet pack` command for the packing process.</span></span> <span data-ttu-id="d617d-121">Daha fazla bilgi için bkz. [NuGet meta veri özellikleri](csproj.md#nuget-metadata-properties) ve [MSBuild komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="d617d-121">For more information, see [NuGet metadata properties](csproj.md#nuget-metadata-properties) and the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="d617d-122">[Örnekler](#examples) bölümü, MSBuild-p anahtarının birkaç farklı senaryo için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d617d-122">The [Examples](#examples) section shows how to use the MSBuild -p switch for a couple of different scenarios.</span></span>

<span data-ttu-id="d617d-123">Web projeleri varsayılan olarak packable değildir.</span><span class="sxs-lookup"><span data-stu-id="d617d-123">Web projects aren't packable by default.</span></span> <span data-ttu-id="d617d-124">Varsayılan davranışı geçersiz kılmak için, *. csproj* dosyanıza aşağıdaki özelliği ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d617d-124">To override the default behavior, add the following property to your *.csproj* file:</span></span>

```xml
<PropertyGroup>
   <IsPackable>true</IsPackable>
</PropertyGroup>
```

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="d617d-125">Arguments</span><span class="sxs-lookup"><span data-stu-id="d617d-125">Arguments</span></span>

`PROJECT | SOLUTION`

  <span data-ttu-id="d617d-126">Paket için proje veya çözüm.</span><span class="sxs-lookup"><span data-stu-id="d617d-126">The project or solution to pack.</span></span> <span data-ttu-id="d617d-127">Bu, bir [csproj dosyası](csproj.md), çözüm dosyası veya bir dizin yoludur.</span><span class="sxs-lookup"><span data-stu-id="d617d-127">It's either a path to a [csproj file](csproj.md), a solution file, or to a directory.</span></span> <span data-ttu-id="d617d-128">Belirtilmemişse, komut geçerli dizinde bir proje veya çözüm dosyası arar.</span><span class="sxs-lookup"><span data-stu-id="d617d-128">If not specified, the command searches the current directory for a project or solution file.</span></span>

## <a name="options"></a><span data-ttu-id="d617d-129">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="d617d-129">Options</span></span>

- **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="d617d-130">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d617d-130">Defines the build configuration.</span></span> <span data-ttu-id="d617d-131">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="d617d-131">The default value is `Debug`.</span></span>

- **`--force`**

  <span data-ttu-id="d617d-132">Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar.</span><span class="sxs-lookup"><span data-stu-id="d617d-132">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="d617d-133">Bu bayrağın belirtilmesi, *Project. varlıklar. JSON* dosyasını silme ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="d617d-133">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span> <span data-ttu-id="d617d-134">.NET Core 2,0 SDK 'dan beri kullanılabilir seçeneği.</span><span class="sxs-lookup"><span data-stu-id="d617d-134">Option available since .NET Core 2.0 SDK.</span></span>

- **`-h|--help`**

  <span data-ttu-id="d617d-135">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="d617d-135">Prints out a short help for the command.</span></span>

- **`--include-source`**

  <span data-ttu-id="d617d-136">Çıkış dizinindeki normal NuGet paketlerine ek olarak hata ayıklama sembolleri NuGet paketlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="d617d-136">Includes the debug symbols NuGet packages in addition to the regular NuGet packages in the output directory.</span></span> <span data-ttu-id="d617d-137">Kaynak dosyaları, semboller paketinin içindeki `src` klasörüne dahil edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d617d-137">The sources files are included in the `src` folder within the symbols package.</span></span>

- **`--include-symbols`**

  <span data-ttu-id="d617d-138">Çıkış dizinindeki normal NuGet paketlerine ek olarak hata ayıklama sembolleri NuGet paketlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="d617d-138">Includes the debug symbols NuGet packages in addition to the regular NuGet packages in the output directory.</span></span>

- **`--interactive`**

  <span data-ttu-id="d617d-139">Komutun, Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir (örneğin, kimlik doğrulamasını tamamlamaya yönelik).</span><span class="sxs-lookup"><span data-stu-id="d617d-139">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="d617d-140">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d617d-140">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-build`**

  <span data-ttu-id="d617d-141">Paketleme öncesinde projeyi oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="d617d-141">Doesn't build the project before packing.</span></span> <span data-ttu-id="d617d-142">Ayrıca `--no-restore` bayrağı örtülü olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d617d-142">It also implicitly sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="d617d-143">Projeden projeye başvuruları yoksayar ve yalnızca kök projeyi geri yükler.</span><span class="sxs-lookup"><span data-stu-id="d617d-143">Ignores project-to-project references and only restores the root project.</span></span> <span data-ttu-id="d617d-144">.NET Core 2,0 SDK 'dan beri kullanılabilir seçeneği.</span><span class="sxs-lookup"><span data-stu-id="d617d-144">Option available since .NET Core 2.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="d617d-145">Komutu çalıştırılırken örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="d617d-145">Doesn't execute an implicit restore when running the command.</span></span> <span data-ttu-id="d617d-146">.NET Core 2,0 SDK 'dan beri kullanılabilir seçeneği.</span><span class="sxs-lookup"><span data-stu-id="d617d-146">Option available since .NET Core 2.0 SDK.</span></span>

- **`--nologo`**

  <span data-ttu-id="d617d-147">Başlangıç başlığını veya telif hakkı iletisini görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="d617d-147">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="d617d-148">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d617d-148">Available since .NET Core 3.0 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="d617d-149">Oluşturulan paketleri belirtilen dizine koyar.</span><span class="sxs-lookup"><span data-stu-id="d617d-149">Places the built packages in the directory specified.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="d617d-150">Paketlerinin geri yükleneceği hedef çalışma zamanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d617d-150">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="d617d-151">Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="d617d-151">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="d617d-152">.NET Core 2,0 SDK 'dan beri kullanılabilir seçeneği.</span><span class="sxs-lookup"><span data-stu-id="d617d-152">Option available since .NET Core 2.0 SDK.</span></span>

- **`-s|--serviceable`**

  <span data-ttu-id="d617d-153">Paketteki hizmet verebilir bayrağını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d617d-153">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="d617d-154">Daha fazla bilgi için bkz. [.net blogu: .NET 4.5.1, .net NuGet kitaplıkları Için Microsoft güvenlik güncelleştirmelerini destekler](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="d617d-154">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="d617d-155">Projedeki `$(VersionSuffix)` MSBuild özelliğinin değerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d617d-155">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="d617d-156">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d617d-156">Sets the verbosity level of the command.</span></span> <span data-ttu-id="d617d-157">İzin verilen değerler `q[uiet]` `m[inimal]` ,`n[ormal]`,, ve .`diag[nostic]` `d[etailed]`</span><span class="sxs-lookup"><span data-stu-id="d617d-157">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="d617d-158">Örnekler</span><span class="sxs-lookup"><span data-stu-id="d617d-158">Examples</span></span>

- <span data-ttu-id="d617d-159">Projeyi geçerli dizinde paketleme:</span><span class="sxs-lookup"><span data-stu-id="d617d-159">Pack the project in the current directory:</span></span>

  ```console
  dotnet pack
  ```

- <span data-ttu-id="d617d-160">`app1` Projeyi paketleme:</span><span class="sxs-lookup"><span data-stu-id="d617d-160">Pack the `app1` project:</span></span>

  ```console
  dotnet pack ~/projects/app1/project.csproj
  ```

- <span data-ttu-id="d617d-161">Projeyi geçerli dizinde paketedin ve elde edilen paketleri `nupkgs` klasörüne yerleştirin:</span><span class="sxs-lookup"><span data-stu-id="d617d-161">Pack the project in the current directory and place the resulting packages into the `nupkgs` folder:</span></span>

  ```console
  dotnet pack --output nupkgs
  ```

- <span data-ttu-id="d617d-162">Geçerli dizindeki `nupkgs` projeyi klasöre paketlayın ve derleme adımını atlayın:</span><span class="sxs-lookup"><span data-stu-id="d617d-162">Pack the project in the current directory into the `nupkgs` folder and skip the build step:</span></span>

  ```console
  dotnet pack --no-build --output nupkgs
  ```

- <span data-ttu-id="d617d-163">Projenin sürüm soneki `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` *. csproj* dosyasında olarak yapılandırıldığında, geçerli projeyi paketleyin ve elde edilen paket sürümünü verilen sonek ile güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="d617d-163">With the project's version suffix configured as `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` in the *.csproj* file, pack the current project and update the resulting package version with the given suffix:</span></span>

  ```console
  dotnet pack --version-suffix "ci-1234"
  ```

- <span data-ttu-id="d617d-164">Paket sürümünü `PackageVersion` MSBuild özelliği ile `2.1.0` olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="d617d-164">Set the package version to `2.1.0` with the `PackageVersion` MSBuild property:</span></span>

  ```console
  dotnet pack -p:PackageVersion=2.1.0
  ```

- <span data-ttu-id="d617d-165">Projeyi belirli bir [hedef çerçeve](../../standard/frameworks.md)için paketleme:</span><span class="sxs-lookup"><span data-stu-id="d617d-165">Pack the project for a specific [target framework](../../standard/frameworks.md):</span></span>

  ```console
  dotnet pack -p:TargetFrameworks=net45
  ```

- <span data-ttu-id="d617d-166">Projeyi paketleme ve geri yükleme işlemi için belirli bir çalışma zamanı (Windows 10) kullanın (.NET Core SDK 2,0 ve sonraki sürümler):</span><span class="sxs-lookup"><span data-stu-id="d617d-166">Pack the project and use a specific runtime (Windows 10) for the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

  ```console
  dotnet pack --runtime win10-x64
  ```

- <span data-ttu-id="d617d-167">Bir [. nuspec dosyası](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec)kullanarak projeyi paketleme:</span><span class="sxs-lookup"><span data-stu-id="d617d-167">Pack the project using a [.nuspec file](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec):</span></span>

  ```console
  dotnet pack ~/projects/app1/project.csproj -p:NuspecFile=~/projects/app1/project.nuspec -p:NuspecBasePath=~/projects/app1/nuget
  ```
