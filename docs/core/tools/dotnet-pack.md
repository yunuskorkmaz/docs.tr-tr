---
title: dotnet paketi komutu
description: Dotnet paketi komutu,.NET Core projeniz için NuGet paketleri oluşturur.
ms.date: 02/14/2020
ms.openlocfilehash: 865262f1eb314f9b7e8ee713c573a965e89ded93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503651"
---
# <a name="dotnet-pack"></a><span data-ttu-id="5e714-103">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="5e714-103">dotnet pack</span></span>

<span data-ttu-id="5e714-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 2.x SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="5e714-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="5e714-105">Adı</span><span class="sxs-lookup"><span data-stu-id="5e714-105">Name</span></span>

<span data-ttu-id="5e714-106">`dotnet pack`- Kodu NuGet paketine paketler.</span><span class="sxs-lookup"><span data-stu-id="5e714-106">`dotnet pack` - Packs the code into a NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5e714-107">Özet</span><span class="sxs-lookup"><span data-stu-id="5e714-107">Synopsis</span></span>

```dotnetcli
dotnet pack [<PROJECT>|<SOLUTION>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--interactive]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo] [-o|--output] [--runtime] [-s|--serviceable]
    [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

## <a name="description"></a><span data-ttu-id="5e714-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5e714-108">Description</span></span>

<span data-ttu-id="5e714-109">Komut `dotnet pack` projeyi oluşturur ve NuGet paketleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5e714-109">The `dotnet pack` command builds the project and creates NuGet packages.</span></span> <span data-ttu-id="5e714-110">Bu komutun sonucu bir NuGet paketidir *(yani.nupkg* dosyası).</span><span class="sxs-lookup"><span data-stu-id="5e714-110">The result of this command is a NuGet package (that is, a *.nupkg* file).</span></span>

<span data-ttu-id="5e714-111">Hata ayıklama sembollerini içeren bir paket oluşturmak istiyorsanız, iki seçeneğiniz vardır:</span><span class="sxs-lookup"><span data-stu-id="5e714-111">If you want to generate a package that contains the debug symbols, you have two options available:</span></span>

- <span data-ttu-id="5e714-112">`--include-symbols`- semboller paketini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5e714-112">`--include-symbols` - it creates the symbols package.</span></span>
- <span data-ttu-id="5e714-113">`--include-source`- kaynak dosyaları içeren bir `src` klasör ile semboller paketi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5e714-113">`--include-source` - it creates the symbols package with a `src` folder inside containing the source files.</span></span>

<span data-ttu-id="5e714-114">Paketlenmiş projenin NuGet bağımlılıkları *.nuspec* dosyasına eklenir, böylece paket yüklendiğinde düzgün bir şekilde çözülürler.</span><span class="sxs-lookup"><span data-stu-id="5e714-114">NuGet dependencies of the packed project are added to the *.nuspec* file, so they're properly resolved when the package is installed.</span></span> <span data-ttu-id="5e714-115">Projeden projeye başvurular proje içinde paketlenmemiştir.</span><span class="sxs-lookup"><span data-stu-id="5e714-115">Project-to-project references aren't packaged inside the project.</span></span> <span data-ttu-id="5e714-116">Şu anda, projeden projeye bağımlılıklarınız varsa, proje başına bir paketiniz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5e714-116">Currently, you must have a package per project if you have project-to-project dependencies.</span></span>

<span data-ttu-id="5e714-117">Varsayılan olarak, `dotnet pack` önce projeyi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5e714-117">By default, `dotnet pack` builds the project first.</span></span> <span data-ttu-id="5e714-118">Bu davranıştan kaçınmak istiyorsanız, `--no-build` seçeneği geçirin.</span><span class="sxs-lookup"><span data-stu-id="5e714-118">If you wish to avoid this behavior, pass the `--no-build` option.</span></span> <span data-ttu-id="5e714-119">Bu seçenek genellikle, kodun daha önce üretildiği senaryoları sürekli tümleştirme (CI) oluşturmada yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="5e714-119">This option is often useful in Continuous Integration (CI) build scenarios where you know the code was previously built.</span></span>

<span data-ttu-id="5e714-120">Paketleme işlemi için `dotnet pack` komuta MSBuild özellikleri sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e714-120">You can provide MSBuild properties to the `dotnet pack` command for the packing process.</span></span> <span data-ttu-id="5e714-121">Daha fazla bilgi için [NuGet meta veri özellikleri](csproj.md#nuget-metadata-properties) ve [MSBuild Komut Satırı Başvurusu'na](/visualstudio/msbuild/msbuild-command-line-reference)bakın.</span><span class="sxs-lookup"><span data-stu-id="5e714-121">For more information, see [NuGet metadata properties](csproj.md#nuget-metadata-properties) and the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="5e714-122">[Örnekler](#examples) bölümünde, birkaç farklı senaryo için MSBuild -p anahtarının nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5e714-122">The [Examples](#examples) section shows how to use the MSBuild -p switch for a couple of different scenarios.</span></span>

<span data-ttu-id="5e714-123">Web projeleri varsayılan olarak paketlenebilir değildir.</span><span class="sxs-lookup"><span data-stu-id="5e714-123">Web projects aren't packable by default.</span></span> <span data-ttu-id="5e714-124">Varsayılan davranışı geçersiz kılmak için *.csproj* dosyanıza aşağıdaki özelliği ekleyin:</span><span class="sxs-lookup"><span data-stu-id="5e714-124">To override the default behavior, add the following property to your *.csproj* file:</span></span>

```xml
<PropertyGroup>
   <IsPackable>true</IsPackable>
</PropertyGroup>
```

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="5e714-125">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="5e714-125">Arguments</span></span>

`PROJECT | SOLUTION`

  <span data-ttu-id="5e714-126">Proje veya çözüm paketi.</span><span class="sxs-lookup"><span data-stu-id="5e714-126">The project or solution to pack.</span></span> <span data-ttu-id="5e714-127">Ya bir [csproj dosyasına,](csproj.md)bir çözüm dosyasına veya bir dizine giden bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="5e714-127">It's either a path to a [csproj file](csproj.md), a solution file, or to a directory.</span></span> <span data-ttu-id="5e714-128">Belirtilmemişse, komut bir proje veya çözüm dosyası için geçerli dizini arar.</span><span class="sxs-lookup"><span data-stu-id="5e714-128">If not specified, the command searches the current directory for a project or solution file.</span></span>

## <a name="options"></a><span data-ttu-id="5e714-129">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="5e714-129">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="5e714-130">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5e714-130">Defines the build configuration.</span></span> <span data-ttu-id="5e714-131">Çoğu proje için `Debug`varsayılan değer, ancak projenizdeki yapı yapılandırma ayarlarını geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e714-131">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`--force`**

  <span data-ttu-id="5e714-132">Son geri yükleme başarılı olsa bile tüm bağımlılıkları çözüme kavuşturmaya zorlar.</span><span class="sxs-lookup"><span data-stu-id="5e714-132">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="5e714-133">Bu bayrağı *belirtmek, project.assets.json* dosyasını silmekle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="5e714-133">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="5e714-134">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="5e714-134">Prints out a short help for the command.</span></span>

- **`--include-source`**

  <span data-ttu-id="5e714-135">Çıkış dizinindeki normal NuGet paketlerine ek olarak hata ayıklama sembollerini NuGet paketlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="5e714-135">Includes the debug symbols NuGet packages in addition to the regular NuGet packages in the output directory.</span></span> <span data-ttu-id="5e714-136">Kaynak dosyaları semboller paketinin `src` içindeki klasöre dahildir.</span><span class="sxs-lookup"><span data-stu-id="5e714-136">The sources files are included in the `src` folder within the symbols package.</span></span>

- **`--include-symbols`**

  <span data-ttu-id="5e714-137">Çıkış dizinindeki normal NuGet paketlerine ek olarak hata ayıklama sembollerini NuGet paketlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="5e714-137">Includes the debug symbols NuGet packages in addition to the regular NuGet packages in the output directory.</span></span>

- **`--interactive`**

  <span data-ttu-id="5e714-138">Komutun durmasına ve kullanıcı girişinin veya eylemini beklemesine (örneğin, kimlik doğrulamasını tamamlamak için) izin verir.</span><span class="sxs-lookup"><span data-stu-id="5e714-138">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="5e714-139">.NET Core 3.0 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="5e714-139">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-build`**

  <span data-ttu-id="5e714-140">Paketlemeden önce projeyi inşa etmez.</span><span class="sxs-lookup"><span data-stu-id="5e714-140">Doesn't build the project before packing.</span></span> <span data-ttu-id="5e714-141">Ayrıca bayrağı da `--no-restore` örtülü olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5e714-141">It also implicitly sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="5e714-142">Projeden projeye başvuruları yoksa ve yalnızca kök projeyi geri yükler.</span><span class="sxs-lookup"><span data-stu-id="5e714-142">Ignores project-to-project references and only restores the root project.</span></span>

- **`--no-restore`**

  <span data-ttu-id="5e714-143">Komutu çalıştırırken örtük bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="5e714-143">Doesn't execute an implicit restore when running the command.</span></span>

- **`--nologo`**

  <span data-ttu-id="5e714-144">Başlangıç bayrağını veya telif hakkı iletisini görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="5e714-144">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="5e714-145">.NET Core 3.0 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="5e714-145">Available since .NET Core 3.0 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="5e714-146">Yapılı paketleri belirtilen dizine yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="5e714-146">Places the built packages in the directory specified.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="5e714-147">Paketleri geri yüklemek için hedef çalışma süresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5e714-147">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="5e714-148">Runtime Tanımlayıcıları (RID'ler) listesi için RID [kataloğuna](../rid-catalog.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="5e714-148">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

- **`-s|--serviceable`**

  <span data-ttu-id="5e714-149">Paketteki servis edilebilir bayrağı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5e714-149">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="5e714-150">Daha fazla bilgi için [.NET Blog: .NET 4.5.1 .NET NuGet Kitaplıkları için Microsoft Güvenlik Güncelleştirmelerini Destekler.](https://aka.ms/nupkgservicing)</span><span class="sxs-lookup"><span data-stu-id="5e714-150">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="5e714-151">Projedeki MSBuild `$(VersionSuffix)` özelliğinin değerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5e714-151">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="5e714-152">Komutun ayrıntılı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5e714-152">Sets the verbosity level of the command.</span></span> <span data-ttu-id="5e714-153">İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve .</span><span class="sxs-lookup"><span data-stu-id="5e714-153">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="5e714-154">Örnekler</span><span class="sxs-lookup"><span data-stu-id="5e714-154">Examples</span></span>

- <span data-ttu-id="5e714-155">Projeyi geçerli dizinde paketle:</span><span class="sxs-lookup"><span data-stu-id="5e714-155">Pack the project in the current directory:</span></span>

  ```dotnetcli
  dotnet pack
  ```

- <span data-ttu-id="5e714-156">Projeyi `app1` paketle:</span><span class="sxs-lookup"><span data-stu-id="5e714-156">Pack the `app1` project:</span></span>

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj
  ```

- <span data-ttu-id="5e714-157">Projeyi geçerli dizine yerleştirin ve ortaya çıkan `nupkgs` paketleri klasöre yerleştirin:</span><span class="sxs-lookup"><span data-stu-id="5e714-157">Pack the project in the current directory and place the resulting packages into the `nupkgs` folder:</span></span>

  ```dotnetcli
  dotnet pack --output nupkgs
  ```

- <span data-ttu-id="5e714-158">Projeyi geçerli dizindeki `nupkgs` klasöre paketleyin ve yapı adımını atlayın:</span><span class="sxs-lookup"><span data-stu-id="5e714-158">Pack the project in the current directory into the `nupkgs` folder and skip the build step:</span></span>

  ```dotnetcli
  dotnet pack --no-build --output nupkgs
  ```

- <span data-ttu-id="5e714-159">*.csproj* dosyasında olduğu gibi `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` yapılandırılan projenin sürümüyle, geçerli projeyi paketleyin ve elde edilen paket sürümünü verilen sonekle güncelleyin:</span><span class="sxs-lookup"><span data-stu-id="5e714-159">With the project's version suffix configured as `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` in the *.csproj* file, pack the current project and update the resulting package version with the given suffix:</span></span>

  ```dotnetcli
  dotnet pack --version-suffix "ci-1234"
  ```

- <span data-ttu-id="5e714-160">Paket sürümünü MSBuild `2.1.0` `PackageVersion` özelliğine göre ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="5e714-160">Set the package version to `2.1.0` with the `PackageVersion` MSBuild property:</span></span>

  ```dotnetcli
  dotnet pack -p:PackageVersion=2.1.0
  ```

- <span data-ttu-id="5e714-161">Belirli bir hedef [çerçevesi](../../standard/frameworks.md)için proje paketi:</span><span class="sxs-lookup"><span data-stu-id="5e714-161">Pack the project for a specific [target framework](../../standard/frameworks.md):</span></span>

  ```dotnetcli
  dotnet pack -p:TargetFrameworks=net45
  ```

- <span data-ttu-id="5e714-162">Projeyi paketleyin ve geri yükleme işlemi için belirli bir çalışma süresi (Windows 10) kullanın:</span><span class="sxs-lookup"><span data-stu-id="5e714-162">Pack the project and use a specific runtime (Windows 10) for the restore operation:</span></span>

  ```dotnetcli
  dotnet pack --runtime win10-x64
  ```

- <span data-ttu-id="5e714-163">[.nuspec dosyasını](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec)kullanarak projeyi paketle:</span><span class="sxs-lookup"><span data-stu-id="5e714-163">Pack the project using a [.nuspec file](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec):</span></span>

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj -p:NuspecFile=~/projects/app1/project.nuspec -p:NuspecBasePath=~/projects/app1/nuget
  ```
