---
title: DotNet paketi komutu
description: DotNet Pack komutu .NET projeniz için NuGet paketleri oluşturur.
ms.date: 04/28/2020
ms.openlocfilehash: 3ca7947b4ed9902b163f09a7b57696f304610cce
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674807"
---
# <a name="dotnet-pack"></a><span data-ttu-id="6e320-103">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="6e320-103">dotnet pack</span></span>

<span data-ttu-id="6e320-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2. x SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="6e320-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="6e320-105">Name</span><span class="sxs-lookup"><span data-stu-id="6e320-105">Name</span></span>

<span data-ttu-id="6e320-106">`dotnet pack` -Kodu bir NuGet paketine paketler.</span><span class="sxs-lookup"><span data-stu-id="6e320-106">`dotnet pack` - Packs the code into a NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="6e320-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="6e320-107">Synopsis</span></span>

```dotnetcli
dotnet pack [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [--force] [--include-source] [--include-symbols] [--interactive]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo]
    [-o|--output <OUTPUT_DIRECTORY>] [--runtime <RUNTIME_IDENTIFIER>]
    [-s|--serviceable] [-v|--verbosity <LEVEL>]
    [--version-suffix <VERSION_SUFFIX>]

dotnet pack -h|--help
```

## <a name="description"></a><span data-ttu-id="6e320-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e320-108">Description</span></span>

<span data-ttu-id="6e320-109">`dotnet pack`Komut projeyi oluşturur ve NuGet paketleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6e320-109">The `dotnet pack` command builds the project and creates NuGet packages.</span></span> <span data-ttu-id="6e320-110">Bu komutun sonucu bir NuGet paketidir (yani, bir *. nupkg* dosyası).</span><span class="sxs-lookup"><span data-stu-id="6e320-110">The result of this command is a NuGet package (that is, a *.nupkg* file).</span></span>

<span data-ttu-id="6e320-111">Hata ayıklama sembollerini içeren bir paket oluşturmak istiyorsanız iki seçeneğiniz vardır:</span><span class="sxs-lookup"><span data-stu-id="6e320-111">If you want to generate a package that contains the debug symbols, you have two options available:</span></span>

- <span data-ttu-id="6e320-112">`--include-symbols` -Bu, semboller paketini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6e320-112">`--include-symbols` - it creates the symbols package.</span></span>
- <span data-ttu-id="6e320-113">`--include-source` -Bu, `src` kaynak dosyaları içeren içindeki bir klasörü içeren semboller paketini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6e320-113">`--include-source` - it creates the symbols package with a `src` folder inside containing the source files.</span></span>

<span data-ttu-id="6e320-114">Paketlenmiş projenin NuGet bağımlılıkları *. nuspec* dosyasına eklenir, bu nedenle paket yüklenirken düzgün şekilde çözülür.</span><span class="sxs-lookup"><span data-stu-id="6e320-114">NuGet dependencies of the packed project are added to the *.nuspec* file, so they're properly resolved when the package is installed.</span></span> <span data-ttu-id="6e320-115">Projeden projeye başvurular proje içinde paketlenmemiş.</span><span class="sxs-lookup"><span data-stu-id="6e320-115">Project-to-project references aren't packaged inside the project.</span></span> <span data-ttu-id="6e320-116">Şu anda, projeden projeye bağımlılıklar varsa proje başına bir pakete sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6e320-116">Currently, you must have a package per project if you have project-to-project dependencies.</span></span>

<span data-ttu-id="6e320-117">Varsayılan olarak, `dotnet pack` önce projeyi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6e320-117">By default, `dotnet pack` builds the project first.</span></span> <span data-ttu-id="6e320-118">Bu davranışı önlemek istiyorsanız, `--no-build` seçeneğini geçirin.</span><span class="sxs-lookup"><span data-stu-id="6e320-118">If you wish to avoid this behavior, pass the `--no-build` option.</span></span> <span data-ttu-id="6e320-119">Bu seçenek genellikle kodun daha önce oluşturulduğunu bildiğiniz sürekli tümleştirme (CI) derleme senaryolarında yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="6e320-119">This option is often useful in Continuous Integration (CI) build scenarios where you know the code was previously built.</span></span>

> [!NOTE]
> <span data-ttu-id="6e320-120">Bazı durumlarda, örtük derleme gerçekleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="6e320-120">In some cases, the implicit build cannot be performed.</span></span> <span data-ttu-id="6e320-121">Bu, `GeneratePackageOnBuild` ayarlandığında, derleme ve paket hedefleri arasındaki döngüsel bağımlılığı önlemek için oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="6e320-121">This can occur when `GeneratePackageOnBuild` is set, to avoid a cyclic dependency between build and pack targets.</span></span> <span data-ttu-id="6e320-122">Ayrıca, kilitli bir dosya veya başka bir sorun varsa derleme başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="6e320-122">The build can also fail if there is a locked file or other issue.</span></span>

<span data-ttu-id="6e320-123">`dotnet pack`Paketleme işlemi için komutuna MSBuild özellikleri sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e320-123">You can provide MSBuild properties to the `dotnet pack` command for the packing process.</span></span> <span data-ttu-id="6e320-124">Daha fazla bilgi için bkz. [NuGet meta veri özellikleri](csproj.md#nuget-metadata-properties) ve [MSBuild Command-Line başvurusu](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="6e320-124">For more information, see [NuGet metadata properties](csproj.md#nuget-metadata-properties) and the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="6e320-125">[Örnekler](#examples) bölümü, MSBuild-p anahtarının birkaç farklı senaryo için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6e320-125">The [Examples](#examples) section shows how to use the MSBuild -p switch for a couple of different scenarios.</span></span>

<span data-ttu-id="6e320-126">Web projeleri varsayılan olarak packable değildir.</span><span class="sxs-lookup"><span data-stu-id="6e320-126">Web projects aren't packable by default.</span></span> <span data-ttu-id="6e320-127">Varsayılan davranışı geçersiz kılmak için, *. csproj* dosyanıza aşağıdaki özelliği ekleyin:</span><span class="sxs-lookup"><span data-stu-id="6e320-127">To override the default behavior, add the following property to your *.csproj* file:</span></span>

```xml
<PropertyGroup>
   <IsPackable>true</IsPackable>
</PropertyGroup>
```

### <a name="implicit-restore"></a><span data-ttu-id="6e320-128">Örtük geri yükleme</span><span class="sxs-lookup"><span data-stu-id="6e320-128">Implicit restore</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="6e320-129">Arguments</span><span class="sxs-lookup"><span data-stu-id="6e320-129">Arguments</span></span>

`PROJECT | SOLUTION`

  <span data-ttu-id="6e320-130">Paket için proje veya çözüm.</span><span class="sxs-lookup"><span data-stu-id="6e320-130">The project or solution to pack.</span></span> <span data-ttu-id="6e320-131">Bu bir [csproj dosyası](csproj.md), VBPROJ dosyası, fsproj dosyası, çözüm dosyası ya da bir dizin yoludur.</span><span class="sxs-lookup"><span data-stu-id="6e320-131">It's either a path to a [csproj file](csproj.md), vbproj file, fsproj file, a solution file, or to a directory.</span></span> <span data-ttu-id="6e320-132">Belirtilmemişse, komut geçerli dizinde bir proje veya çözüm dosyası arar.</span><span class="sxs-lookup"><span data-stu-id="6e320-132">If not specified, the command searches the current directory for a project or solution file.</span></span>

## <a name="options"></a><span data-ttu-id="6e320-133">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="6e320-133">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="6e320-134">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6e320-134">Defines the build configuration.</span></span> <span data-ttu-id="6e320-135">Çoğu proje için varsayılandır `Debug` , ancak projenizde derleme yapılandırma ayarlarını geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e320-135">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`--force`**

  <span data-ttu-id="6e320-136">Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar.</span><span class="sxs-lookup"><span data-stu-id="6e320-136">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="6e320-137">Bu bayrağın belirtilmesi, dosyadaki *project.assets.js* silme ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="6e320-137">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="6e320-138">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="6e320-138">Prints out a short help for the command.</span></span>

- **`--include-source`**

  <span data-ttu-id="6e320-139">Çıkış dizinindeki normal NuGet paketlerine ek olarak hata ayıklama sembolleri NuGet paketlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="6e320-139">Includes the debug symbols NuGet packages in addition to the regular NuGet packages in the output directory.</span></span> <span data-ttu-id="6e320-140">Kaynak dosyaları, `src` semboller paketinin içindeki klasörüne dahil edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6e320-140">The sources files are included in the `src` folder within the symbols package.</span></span>

- **`--include-symbols`**

  <span data-ttu-id="6e320-141">Çıkış dizinindeki normal NuGet paketlerine ek olarak hata ayıklama sembolleri NuGet paketlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="6e320-141">Includes the debug symbols NuGet packages in addition to the regular NuGet packages in the output directory.</span></span>

- **`--interactive`**

  <span data-ttu-id="6e320-142">Komutun, Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir (örneğin, kimlik doğrulamasını tamamlamaya yönelik).</span><span class="sxs-lookup"><span data-stu-id="6e320-142">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="6e320-143">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6e320-143">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-build`**

  <span data-ttu-id="6e320-144">Paketleme öncesinde projeyi oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="6e320-144">Doesn't build the project before packing.</span></span> <span data-ttu-id="6e320-145">Ayrıca bayrağı örtülü olarak ayarlar `--no-restore` .</span><span class="sxs-lookup"><span data-stu-id="6e320-145">It also implicitly sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="6e320-146">Projeden projeye başvuruları yoksayar ve yalnızca kök projeyi geri yükler.</span><span class="sxs-lookup"><span data-stu-id="6e320-146">Ignores project-to-project references and only restores the root project.</span></span>

- **`--no-restore`**

  <span data-ttu-id="6e320-147">Komutu çalıştırılırken örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="6e320-147">Doesn't execute an implicit restore when running the command.</span></span>

- **`--nologo`**

  <span data-ttu-id="6e320-148">Başlangıç başlığını veya telif hakkı iletisini görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="6e320-148">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="6e320-149">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6e320-149">Available since .NET Core 3.0 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="6e320-150">Oluşturulan paketleri belirtilen dizine koyar.</span><span class="sxs-lookup"><span data-stu-id="6e320-150">Places the built packages in the directory specified.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="6e320-151">Paketlerinin geri yükleneceği hedef çalışma zamanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6e320-151">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="6e320-152">Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="6e320-152">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

- **`-s|--serviceable`**

  <span data-ttu-id="6e320-153">Paketteki hizmet verebilir bayrağını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6e320-153">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="6e320-154">Daha fazla bilgi için bkz. [.net blogu: .NET Framework 4.5.1, .net NuGet kitaplıkları Için Microsoft güvenlik güncelleştirmelerini destekler](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="6e320-154">For more information, see [.NET Blog: .NET Framework 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="6e320-155">`$(VersionSuffix)`Projedeki MSBuild özelliğinin değerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6e320-155">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="6e320-156">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6e320-156">Sets the verbosity level of the command.</span></span> <span data-ttu-id="6e320-157">İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="6e320-157">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="6e320-158">Örnekler</span><span class="sxs-lookup"><span data-stu-id="6e320-158">Examples</span></span>

- <span data-ttu-id="6e320-159">Projeyi geçerli dizinde paketleme:</span><span class="sxs-lookup"><span data-stu-id="6e320-159">Pack the project in the current directory:</span></span>

  ```dotnetcli
  dotnet pack
  ```

- <span data-ttu-id="6e320-160">Projeyi paketleme `app1` :</span><span class="sxs-lookup"><span data-stu-id="6e320-160">Pack the `app1` project:</span></span>

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj
  ```

- <span data-ttu-id="6e320-161">Projeyi geçerli dizinde paketedin ve elde edilen paketleri `nupkgs` klasörüne yerleştirin:</span><span class="sxs-lookup"><span data-stu-id="6e320-161">Pack the project in the current directory and place the resulting packages into the `nupkgs` folder:</span></span>

  ```dotnetcli
  dotnet pack --output nupkgs
  ```

- <span data-ttu-id="6e320-162">Geçerli dizindeki projeyi klasöre paketlayın `nupkgs` ve derleme adımını atlayın:</span><span class="sxs-lookup"><span data-stu-id="6e320-162">Pack the project in the current directory into the `nupkgs` folder and skip the build step:</span></span>

  ```dotnetcli
  dotnet pack --no-build --output nupkgs
  ```

- <span data-ttu-id="6e320-163">Projenin sürüm soneki `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` *. csproj* dosyasında olarak yapılandırıldığında, geçerli projeyi paketleyin ve elde edilen paket sürümünü verilen sonek ile güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="6e320-163">With the project's version suffix configured as `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` in the *.csproj* file, pack the current project and update the resulting package version with the given suffix:</span></span>

  ```dotnetcli
  dotnet pack --version-suffix "ci-1234"
  ```

- <span data-ttu-id="6e320-164">Paket sürümünü `2.1.0` MSBuild özelliği ile olarak ayarlayın `PackageVersion` :</span><span class="sxs-lookup"><span data-stu-id="6e320-164">Set the package version to `2.1.0` with the `PackageVersion` MSBuild property:</span></span>

  ```dotnetcli
  dotnet pack -p:PackageVersion=2.1.0
  ```

- <span data-ttu-id="6e320-165">Projeyi belirli bir [hedef çerçeve](../../standard/frameworks.md)için paketleme:</span><span class="sxs-lookup"><span data-stu-id="6e320-165">Pack the project for a specific [target framework](../../standard/frameworks.md):</span></span>

  ```dotnetcli
  dotnet pack -p:TargetFrameworks=net45
  ```

- <span data-ttu-id="6e320-166">Projeyi paketleme ve geri yükleme işlemi için belirli bir çalışma zamanı (Windows 10) kullanın:</span><span class="sxs-lookup"><span data-stu-id="6e320-166">Pack the project and use a specific runtime (Windows 10) for the restore operation:</span></span>

  ```dotnetcli
  dotnet pack --runtime win10-x64
  ```

- <span data-ttu-id="6e320-167">Bir *. nuspec* dosyası kullanarak projeyi paketleme:</span><span class="sxs-lookup"><span data-stu-id="6e320-167">Pack the project using a *.nuspec* file:</span></span>

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj -p:NuspecFile=~/projects/app1/project.nuspec -p:NuspecBasePath=~/projects/app1/nuget
  ```

  <span data-ttu-id="6e320-168">, Ve kullanma hakkında daha fazla bilgi için `NuspecFile` `NuspecBasePath` `NuspecProperties` aşağıdaki kaynaklara bakın:</span><span class="sxs-lookup"><span data-stu-id="6e320-168">For information about how to use `NuspecFile`, `NuspecBasePath`, and `NuspecProperties`, see the following resources:</span></span>

  - [<span data-ttu-id="6e320-169">. Nuspec kullanarak paketleme</span><span class="sxs-lookup"><span data-stu-id="6e320-169">Packing using a .nuspec</span></span>](/nuget/reference/msbuild-targets#packing-using-a-nuspec)
  - [<span data-ttu-id="6e320-170">Özelleştirilmiş paket oluşturmak için gelişmiş uzantı noktaları</span><span class="sxs-lookup"><span data-stu-id="6e320-170">Advanced extension points to create customized package</span></span>](/nuget/reference/msbuild-targets#advanced-extension-points-to-create-customized-package)
  - [<span data-ttu-id="6e320-171">Genel Özellikler</span><span class="sxs-lookup"><span data-stu-id="6e320-171">Global properties</span></span>](/visualstudio/msbuild/msbuild-properties#global-properties)
