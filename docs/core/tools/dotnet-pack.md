---
title: dotnet paketi komutu
description: Dotnet paketi komutu,.NET Core projeniz için NuGet paketleri oluşturur.
ms.date: 02/14/2020
ms.openlocfilehash: 2df096a088a177b77256b5d717f31e185507b249
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102820"
---
# <a name="dotnet-pack"></a><span data-ttu-id="908d9-103">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="908d9-103">dotnet pack</span></span>

<span data-ttu-id="908d9-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 2.x SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="908d9-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="908d9-105">Adı</span><span class="sxs-lookup"><span data-stu-id="908d9-105">Name</span></span>

<span data-ttu-id="908d9-106">`dotnet pack`- Kodu NuGet paketine paketler.</span><span class="sxs-lookup"><span data-stu-id="908d9-106">`dotnet pack` - Packs the code into a NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="908d9-107">Özet</span><span class="sxs-lookup"><span data-stu-id="908d9-107">Synopsis</span></span>

```dotnetcli
dotnet pack [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [--force] [--include-source] [--include-symbols] [--interactive]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo]
    [-o|--output <OUTPUT_DIRECTORY>] [--runtime <RUNTIME_IDENTIFIER>]
    [-s|--serviceable] [-v|--verbosity <LEVEL>]
    [--version-suffix <VERSION_SUFFIX>]

dotnet pack -h|--help
```

## <a name="description"></a><span data-ttu-id="908d9-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="908d9-108">Description</span></span>

<span data-ttu-id="908d9-109">Komut `dotnet pack` projeyi oluşturur ve NuGet paketleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="908d9-109">The `dotnet pack` command builds the project and creates NuGet packages.</span></span> <span data-ttu-id="908d9-110">Bu komutun sonucu bir NuGet paketidir *(yani.nupkg* dosyası).</span><span class="sxs-lookup"><span data-stu-id="908d9-110">The result of this command is a NuGet package (that is, a *.nupkg* file).</span></span>

<span data-ttu-id="908d9-111">Hata ayıklama sembollerini içeren bir paket oluşturmak istiyorsanız, iki seçeneğiniz vardır:</span><span class="sxs-lookup"><span data-stu-id="908d9-111">If you want to generate a package that contains the debug symbols, you have two options available:</span></span>

- <span data-ttu-id="908d9-112">`--include-symbols`- semboller paketini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="908d9-112">`--include-symbols` - it creates the symbols package.</span></span>
- <span data-ttu-id="908d9-113">`--include-source`- kaynak dosyaları içeren bir `src` klasör ile semboller paketi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="908d9-113">`--include-source` - it creates the symbols package with a `src` folder inside containing the source files.</span></span>

<span data-ttu-id="908d9-114">Paketlenmiş projenin NuGet bağımlılıkları *.nuspec* dosyasına eklenir, böylece paket yüklendiğinde düzgün bir şekilde çözülürler.</span><span class="sxs-lookup"><span data-stu-id="908d9-114">NuGet dependencies of the packed project are added to the *.nuspec* file, so they're properly resolved when the package is installed.</span></span> <span data-ttu-id="908d9-115">Projeden projeye başvurular proje içinde paketlenmemiştir.</span><span class="sxs-lookup"><span data-stu-id="908d9-115">Project-to-project references aren't packaged inside the project.</span></span> <span data-ttu-id="908d9-116">Şu anda, projeden projeye bağımlılıklarınız varsa, proje başına bir paketiniz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="908d9-116">Currently, you must have a package per project if you have project-to-project dependencies.</span></span>

<span data-ttu-id="908d9-117">Varsayılan olarak, `dotnet pack` önce projeyi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="908d9-117">By default, `dotnet pack` builds the project first.</span></span> <span data-ttu-id="908d9-118">Bu davranıştan kaçınmak istiyorsanız, `--no-build` seçeneği geçirin.</span><span class="sxs-lookup"><span data-stu-id="908d9-118">If you wish to avoid this behavior, pass the `--no-build` option.</span></span> <span data-ttu-id="908d9-119">Bu seçenek genellikle, kodun daha önce üretildiği senaryoları sürekli tümleştirme (CI) oluşturmada yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="908d9-119">This option is often useful in Continuous Integration (CI) build scenarios where you know the code was previously built.</span></span>

> [!NOTE]
> <span data-ttu-id="908d9-120">Bazı durumlarda, örtülü yapı gerçekleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="908d9-120">In some cases, the implicit build cannot be performed.</span></span> <span data-ttu-id="908d9-121">Bu, yapı `GeneratePackageOnBuild` ve paket hedefleri arasında döngüsel bağımlılıktan kaçınmak için ayarlandığında oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="908d9-121">This can occur when `GeneratePackageOnBuild` is set, to avoid a cyclic dependency between build and pack targets.</span></span> <span data-ttu-id="908d9-122">Kilitli bir dosya veya başka bir sorun varsa yapı da başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="908d9-122">The build can also fail if there is a locked file or other issue.</span></span>

<span data-ttu-id="908d9-123">Paketleme işlemi için `dotnet pack` komuta MSBuild özellikleri sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="908d9-123">You can provide MSBuild properties to the `dotnet pack` command for the packing process.</span></span> <span data-ttu-id="908d9-124">Daha fazla bilgi için [NuGet meta veri özellikleri](csproj.md#nuget-metadata-properties) ve [MSBuild Komut Satırı Başvurusu'na](/visualstudio/msbuild/msbuild-command-line-reference)bakın.</span><span class="sxs-lookup"><span data-stu-id="908d9-124">For more information, see [NuGet metadata properties](csproj.md#nuget-metadata-properties) and the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="908d9-125">[Örnekler](#examples) bölümünde, birkaç farklı senaryo için MSBuild -p anahtarının nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="908d9-125">The [Examples](#examples) section shows how to use the MSBuild -p switch for a couple of different scenarios.</span></span>

<span data-ttu-id="908d9-126">Web projeleri varsayılan olarak paketlenebilir değildir.</span><span class="sxs-lookup"><span data-stu-id="908d9-126">Web projects aren't packable by default.</span></span> <span data-ttu-id="908d9-127">Varsayılan davranışı geçersiz kılmak için *.csproj* dosyanıza aşağıdaki özelliği ekleyin:</span><span class="sxs-lookup"><span data-stu-id="908d9-127">To override the default behavior, add the following property to your *.csproj* file:</span></span>

```xml
<PropertyGroup>
   <IsPackable>true</IsPackable>
</PropertyGroup>
```

### <a name="implicit-restore"></a><span data-ttu-id="908d9-128">Örtük geri yükleme</span><span class="sxs-lookup"><span data-stu-id="908d9-128">Implicit restore</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="908d9-129">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="908d9-129">Arguments</span></span>

`PROJECT | SOLUTION`

  <span data-ttu-id="908d9-130">Proje veya çözüm paketi.</span><span class="sxs-lookup"><span data-stu-id="908d9-130">The project or solution to pack.</span></span> <span data-ttu-id="908d9-131">Ya bir [csproj dosyasına,](csproj.md)bir çözüm dosyasına veya bir dizine giden bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="908d9-131">It's either a path to a [csproj file](csproj.md), a solution file, or to a directory.</span></span> <span data-ttu-id="908d9-132">Belirtilmemişse, komut bir proje veya çözüm dosyası için geçerli dizini arar.</span><span class="sxs-lookup"><span data-stu-id="908d9-132">If not specified, the command searches the current directory for a project or solution file.</span></span>

## <a name="options"></a><span data-ttu-id="908d9-133">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="908d9-133">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="908d9-134">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="908d9-134">Defines the build configuration.</span></span> <span data-ttu-id="908d9-135">Çoğu proje için `Debug`varsayılan değer, ancak projenizdeki yapı yapılandırma ayarlarını geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="908d9-135">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`--force`**

  <span data-ttu-id="908d9-136">Son geri yükleme başarılı olsa bile tüm bağımlılıkları çözüme kavuşturmaya zorlar.</span><span class="sxs-lookup"><span data-stu-id="908d9-136">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="908d9-137">Bu bayrağı *belirtmek, project.assets.json* dosyasını silmekle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="908d9-137">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="908d9-138">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="908d9-138">Prints out a short help for the command.</span></span>

- **`--include-source`**

  <span data-ttu-id="908d9-139">Çıkış dizinindeki normal NuGet paketlerine ek olarak hata ayıklama sembollerini NuGet paketlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="908d9-139">Includes the debug symbols NuGet packages in addition to the regular NuGet packages in the output directory.</span></span> <span data-ttu-id="908d9-140">Kaynak dosyaları semboller paketinin `src` içindeki klasöre dahildir.</span><span class="sxs-lookup"><span data-stu-id="908d9-140">The sources files are included in the `src` folder within the symbols package.</span></span>

- **`--include-symbols`**

  <span data-ttu-id="908d9-141">Çıkış dizinindeki normal NuGet paketlerine ek olarak hata ayıklama sembollerini NuGet paketlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="908d9-141">Includes the debug symbols NuGet packages in addition to the regular NuGet packages in the output directory.</span></span>

- **`--interactive`**

  <span data-ttu-id="908d9-142">Komutun durmasına ve kullanıcı girişinin veya eylemini beklemesine (örneğin, kimlik doğrulamasını tamamlamak için) izin verir.</span><span class="sxs-lookup"><span data-stu-id="908d9-142">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="908d9-143">.NET Core 3.0 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="908d9-143">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-build`**

  <span data-ttu-id="908d9-144">Paketlemeden önce projeyi inşa etmez.</span><span class="sxs-lookup"><span data-stu-id="908d9-144">Doesn't build the project before packing.</span></span> <span data-ttu-id="908d9-145">Ayrıca bayrağı da `--no-restore` örtülü olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="908d9-145">It also implicitly sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="908d9-146">Projeden projeye başvuruları yoksa ve yalnızca kök projeyi geri yükler.</span><span class="sxs-lookup"><span data-stu-id="908d9-146">Ignores project-to-project references and only restores the root project.</span></span>

- **`--no-restore`**

  <span data-ttu-id="908d9-147">Komutu çalıştırırken örtük bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="908d9-147">Doesn't execute an implicit restore when running the command.</span></span>

- **`--nologo`**

  <span data-ttu-id="908d9-148">Başlangıç bayrağını veya telif hakkı iletisini görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="908d9-148">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="908d9-149">.NET Core 3.0 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="908d9-149">Available since .NET Core 3.0 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="908d9-150">Yapılı paketleri belirtilen dizine yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="908d9-150">Places the built packages in the directory specified.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="908d9-151">Paketleri geri yüklemek için hedef çalışma süresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="908d9-151">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="908d9-152">Runtime Tanımlayıcıları (RID'ler) listesi için RID [kataloğuna](../rid-catalog.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="908d9-152">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

- **`-s|--serviceable`**

  <span data-ttu-id="908d9-153">Paketteki servis edilebilir bayrağı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="908d9-153">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="908d9-154">Daha fazla bilgi için [.NET Blog: .NET 4.5.1 .NET NuGet Kitaplıkları için Microsoft Güvenlik Güncelleştirmelerini Destekler.](https://aka.ms/nupkgservicing)</span><span class="sxs-lookup"><span data-stu-id="908d9-154">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="908d9-155">Projedeki MSBuild `$(VersionSuffix)` özelliğinin değerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="908d9-155">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="908d9-156">Komutun ayrıntılı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="908d9-156">Sets the verbosity level of the command.</span></span> <span data-ttu-id="908d9-157">İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve .</span><span class="sxs-lookup"><span data-stu-id="908d9-157">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="908d9-158">Örnekler</span><span class="sxs-lookup"><span data-stu-id="908d9-158">Examples</span></span>

- <span data-ttu-id="908d9-159">Projeyi geçerli dizinde paketle:</span><span class="sxs-lookup"><span data-stu-id="908d9-159">Pack the project in the current directory:</span></span>

  ```dotnetcli
  dotnet pack
  ```

- <span data-ttu-id="908d9-160">Projeyi `app1` paketle:</span><span class="sxs-lookup"><span data-stu-id="908d9-160">Pack the `app1` project:</span></span>

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj
  ```

- <span data-ttu-id="908d9-161">Projeyi geçerli dizine yerleştirin ve ortaya çıkan `nupkgs` paketleri klasöre yerleştirin:</span><span class="sxs-lookup"><span data-stu-id="908d9-161">Pack the project in the current directory and place the resulting packages into the `nupkgs` folder:</span></span>

  ```dotnetcli
  dotnet pack --output nupkgs
  ```

- <span data-ttu-id="908d9-162">Projeyi geçerli dizindeki `nupkgs` klasöre paketleyin ve yapı adımını atlayın:</span><span class="sxs-lookup"><span data-stu-id="908d9-162">Pack the project in the current directory into the `nupkgs` folder and skip the build step:</span></span>

  ```dotnetcli
  dotnet pack --no-build --output nupkgs
  ```

- <span data-ttu-id="908d9-163">*.csproj* dosyasında olduğu gibi `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` yapılandırılan projenin sürümüyle, geçerli projeyi paketleyin ve elde edilen paket sürümünü verilen sonekle güncelleyin:</span><span class="sxs-lookup"><span data-stu-id="908d9-163">With the project's version suffix configured as `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` in the *.csproj* file, pack the current project and update the resulting package version with the given suffix:</span></span>

  ```dotnetcli
  dotnet pack --version-suffix "ci-1234"
  ```

- <span data-ttu-id="908d9-164">Paket sürümünü MSBuild `2.1.0` `PackageVersion` özelliğine göre ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="908d9-164">Set the package version to `2.1.0` with the `PackageVersion` MSBuild property:</span></span>

  ```dotnetcli
  dotnet pack -p:PackageVersion=2.1.0
  ```

- <span data-ttu-id="908d9-165">Belirli bir hedef [çerçevesi](../../standard/frameworks.md)için proje paketi:</span><span class="sxs-lookup"><span data-stu-id="908d9-165">Pack the project for a specific [target framework](../../standard/frameworks.md):</span></span>

  ```dotnetcli
  dotnet pack -p:TargetFrameworks=net45
  ```

- <span data-ttu-id="908d9-166">Projeyi paketleyin ve geri yükleme işlemi için belirli bir çalışma süresi (Windows 10) kullanın:</span><span class="sxs-lookup"><span data-stu-id="908d9-166">Pack the project and use a specific runtime (Windows 10) for the restore operation:</span></span>

  ```dotnetcli
  dotnet pack --runtime win10-x64
  ```

- <span data-ttu-id="908d9-167">[.nuspec dosyasını](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec)kullanarak projeyi paketle:</span><span class="sxs-lookup"><span data-stu-id="908d9-167">Pack the project using a [.nuspec file](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec):</span></span>

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj -p:NuspecFile=~/projects/app1/project.nuspec -p:NuspecBasePath=~/projects/app1/nuget
  ```
