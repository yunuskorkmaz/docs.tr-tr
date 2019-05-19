---
title: DotNet Paketi komutu
description: Dotnet paketi komut, .NET Core projesi için NuGet paketlerini oluşturur.
ms.date: 12/04/2018
ms.openlocfilehash: 5d48e5957e8095cc9ef4eaca2e1e1746c25a2a88
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65876038"
---
# <a name="dotnet-pack"></a><span data-ttu-id="6bc53-103">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="6bc53-103">dotnet pack</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="6bc53-104">Ad</span><span class="sxs-lookup"><span data-stu-id="6bc53-104">Name</span></span>

<span data-ttu-id="6bc53-105">`dotnet pack` -Kod bir NuGet paketine paketleri.</span><span class="sxs-lookup"><span data-stu-id="6bc53-105">`dotnet pack` - Packs the code into a NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="6bc53-106">Synopsis</span><span class="sxs-lookup"><span data-stu-id="6bc53-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="6bc53-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="6bc53-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet pack [<PROJECT>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [--runtime] [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6bc53-108">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="6bc53-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet pack [<PROJECT>] [-c|--configuration] [--include-source] [--include-symbols] [--no-build] [-o|--output]
    [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="6bc53-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6bc53-109">Description</span></span>

<span data-ttu-id="6bc53-110">`dotnet pack` Komut projeyi derler ve NuGet paketleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6bc53-110">The `dotnet pack` command builds the project and creates NuGet packages.</span></span> <span data-ttu-id="6bc53-111">Bu komutun sonucuna ilişkin bir NuGet paketidir.</span><span class="sxs-lookup"><span data-stu-id="6bc53-111">The result of this command is a NuGet package.</span></span> <span data-ttu-id="6bc53-112">Varsa `--include-symbols` seçeneği varsa, hata ayıklama sembolleri içeren başka bir paket oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6bc53-112">If the `--include-symbols` option is present, another package containing the debug symbols is created.</span></span>

<span data-ttu-id="6bc53-113">Paketlenmiş proje, NuGet bağımlılıklarını eklenir *.nuspec* düzgün bulunmaları dosyası, çözümlenen paketi yüklendiğinde.</span><span class="sxs-lookup"><span data-stu-id="6bc53-113">NuGet dependencies of the packed project are added to the *.nuspec* file, so they're properly resolved when the package is installed.</span></span> <span data-ttu-id="6bc53-114">Projeden projeye başvurular projesi içinde paketlendi değildir.</span><span class="sxs-lookup"><span data-stu-id="6bc53-114">Project-to-project references aren't packaged inside the project.</span></span> <span data-ttu-id="6bc53-115">Şu anda projeden projeye bağımlılıkları varsa, her proje bir paket olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6bc53-115">Currently, you must have a package per project if you have project-to-project dependencies.</span></span>

<span data-ttu-id="6bc53-116">Varsayılan olarak, `dotnet pack` önce projeyi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6bc53-116">By default, `dotnet pack` builds the project first.</span></span> <span data-ttu-id="6bc53-117">Bu davranışı engellemek istiyorsanız, geçmesi `--no-build` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="6bc53-117">If you wish to avoid this behavior, pass the `--no-build` option.</span></span> <span data-ttu-id="6bc53-118">Bu seçenek genellikle kod daha önce oluşturulmuş bildiğiniz sürekli tümleştirme (CI) derleme senaryolarda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="6bc53-118">This option is often useful in Continuous Integration (CI) build scenarios where you know the code was previously built.</span></span>

<span data-ttu-id="6bc53-119">MSBuild özellikleri sağlayabilir `dotnet pack` paketleme işlemi için komutu.</span><span class="sxs-lookup"><span data-stu-id="6bc53-119">You can provide MSBuild properties to the `dotnet pack` command for the packing process.</span></span> <span data-ttu-id="6bc53-120">Daha fazla bilgi için [NuGet meta veri özelliklerini](csproj.md#nuget-metadata-properties) ve [MSBuild komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="6bc53-120">For more information, see [NuGet metadata properties](csproj.md#nuget-metadata-properties) and the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="6bc53-121">[Örnekler](#examples) bölüm birkaç farklı senaryolar için MSBuild -p anahtar kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="6bc53-121">The [Examples](#examples) section shows how to use the MSBuild -p switch for a couple of different scenarios.</span></span>

<span data-ttu-id="6bc53-122">Web projeleri, varsayılan olarak packable değildir.</span><span class="sxs-lookup"><span data-stu-id="6bc53-122">Web projects aren't packable by default.</span></span> <span data-ttu-id="6bc53-123">Varsayılan davranışı geçersiz kılmak için aşağıdaki özelliği ekleyin, *.csproj* dosyası:</span><span class="sxs-lookup"><span data-stu-id="6bc53-123">To override the default behavior, add the following property to your *.csproj* file:</span></span>

```xml
<PropertyGroup>
   <IsPackable>true</IsPackable>
</PropertyGroup>
```

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="6bc53-124">Arguments</span><span class="sxs-lookup"><span data-stu-id="6bc53-124">Arguments</span></span>

* **`PROJECT`**

  <span data-ttu-id="6bc53-125">Paketi için proje.</span><span class="sxs-lookup"><span data-stu-id="6bc53-125">The project to pack.</span></span> <span data-ttu-id="6bc53-126">Ya da bir yolu olan bir [csproj dosyasını](csproj.md) veya bir dizine.</span><span class="sxs-lookup"><span data-stu-id="6bc53-126">It's either a path to a [csproj file](csproj.md) or to a directory.</span></span> <span data-ttu-id="6bc53-127">Belirtilmezse, geçerli dizin için varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="6bc53-127">If not specified, it defaults to the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="6bc53-128">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="6bc53-128">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="6bc53-129">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="6bc53-129">.NET Core 2.x</span></span>](#tab/netcore2x)

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="6bc53-130">Derleme yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6bc53-130">Defines the build configuration.</span></span> <span data-ttu-id="6bc53-131">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6bc53-131">The default value is `Debug`.</span></span>

* **`--force`**

  <span data-ttu-id="6bc53-132">Son geri yükleme başarılı olduysa bile çözülmesi için tüm bağımlılıkların zorlar.</span><span class="sxs-lookup"><span data-stu-id="6bc53-132">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="6bc53-133">Bu bayrak belirten aynıdır silme *project.assets.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="6bc53-133">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

* **`-h|--help`**

  <span data-ttu-id="6bc53-134">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="6bc53-134">Prints out a short help for the command.</span></span>

* **`--include-source`**

  <span data-ttu-id="6bc53-135">NuGet paketinin kaynak dosyaları içerir.</span><span class="sxs-lookup"><span data-stu-id="6bc53-135">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="6bc53-136">Kaynak dosyaların dahil `src` klasördeki `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="6bc53-136">The sources files are included in the `src` folder within the `nupkg`.</span></span>

* **`--include-symbols`**

  <span data-ttu-id="6bc53-137">Sembolleri oluşturur `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="6bc53-137">Generates the symbols `nupkg`.</span></span>

* **`--no-build`**

  <span data-ttu-id="6bc53-138">Paketleme önce projenizi değil.</span><span class="sxs-lookup"><span data-stu-id="6bc53-138">Doesn't build the project before packing.</span></span> <span data-ttu-id="6bc53-139">Ayrıca örtülü olarak ayarlar `--no-restore` bayrağı.</span><span class="sxs-lookup"><span data-stu-id="6bc53-139">It also implicitly sets the `--no-restore` flag.</span></span>

* **`--no-dependencies`**

  <span data-ttu-id="6bc53-140">Projeden projeye başvurular yoksayar ve yalnızca kök proje geri yükler.</span><span class="sxs-lookup"><span data-stu-id="6bc53-140">Ignores project-to-project references and only restores the root project.</span></span>

* **`--no-restore`**

  <span data-ttu-id="6bc53-141">Örtük bir geri yükleme komutu çalıştırırken yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="6bc53-141">Doesn't execute an implicit restore when running the command.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="6bc53-142">Yerleşik paketler belirtilen dizine yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="6bc53-142">Places the built packages in the directory specified.</span></span>

* **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="6bc53-143">Paketleri geri yüklemek için hedef çalışma zamanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="6bc53-143">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="6bc53-144">Çalışma zamanı tanımlayıcılarının (RID'ler) bir listesi için bkz. [RID Kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="6bc53-144">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

* **`-s|--serviceable`**

  <span data-ttu-id="6bc53-145">Pakette tutulabilmesi bayrağını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6bc53-145">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="6bc53-146">Daha fazla bilgi için [.NET Blog: .NET 4.5.1 destekleyen Microsoft güvenlik güncelleştirmeleri için .NET NuGet kitaplıklarını](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="6bc53-146">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

* **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="6bc53-147">Değerini tanımlayan `$(VersionSuffix)` projesinde MSBuild özelliği.</span><span class="sxs-lookup"><span data-stu-id="6bc53-147">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="6bc53-148">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6bc53-148">Sets the verbosity level of the command.</span></span> <span data-ttu-id="6bc53-149">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="6bc53-149">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6bc53-150">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="6bc53-150">.NET Core 1.x</span></span>](#tab/netcore1x)

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="6bc53-151">Derleme yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6bc53-151">Defines the build configuration.</span></span> <span data-ttu-id="6bc53-152">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6bc53-152">The default value is `Debug`.</span></span>

* **`-h|--help`**

  <span data-ttu-id="6bc53-153">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="6bc53-153">Prints out a short help for the command.</span></span>

* **`--include-source`**

  <span data-ttu-id="6bc53-154">NuGet paketinin kaynak dosyaları içerir.</span><span class="sxs-lookup"><span data-stu-id="6bc53-154">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="6bc53-155">Kaynak dosyaların dahil `src` klasördeki `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="6bc53-155">The sources files are included in the `src` folder within the `nupkg`.</span></span>

* **`--include-symbols`**

  <span data-ttu-id="6bc53-156">Sembolleri oluşturur `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="6bc53-156">Generates the symbols `nupkg`.</span></span>

* **`--no-build`**

  <span data-ttu-id="6bc53-157">Paketleme önce projenizi değil.</span><span class="sxs-lookup"><span data-stu-id="6bc53-157">Doesn't build the project before packing.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="6bc53-158">Yerleşik paketler belirtilen dizine yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="6bc53-158">Places the built packages in the directory specified.</span></span>

* **`-s|--serviceable`**

  <span data-ttu-id="6bc53-159">Pakette tutulabilmesi bayrağını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6bc53-159">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="6bc53-160">Daha fazla bilgi için [.NET Blog: .NET 4.5.1 destekleyen Microsoft güvenlik güncelleştirmeleri için .NET NuGet kitaplıklarını](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="6bc53-160">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

* **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="6bc53-161">Değerini tanımlayan `$(VersionSuffix)` projesinde MSBuild özelliği.</span><span class="sxs-lookup"><span data-stu-id="6bc53-161">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="6bc53-162">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6bc53-162">Sets the verbosity level of the command.</span></span> <span data-ttu-id="6bc53-163">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="6bc53-163">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="6bc53-164">Örnekler</span><span class="sxs-lookup"><span data-stu-id="6bc53-164">Examples</span></span>

* <span data-ttu-id="6bc53-165">Geçerli dizindeki proje paketi:</span><span class="sxs-lookup"><span data-stu-id="6bc53-165">Pack the project in the current directory:</span></span>

  ```console
  dotnet pack
  ```

* <span data-ttu-id="6bc53-166">Paketi `app1` proje:</span><span class="sxs-lookup"><span data-stu-id="6bc53-166">Pack the `app1` project:</span></span>

  ```console
  dotnet pack ~/projects/app1/project.csproj
  ```

* <span data-ttu-id="6bc53-167">Geçerli dizinde proje pack ve sonuçta elde edilen paketler halinde yerleştirin `nupkgs` klasörü:</span><span class="sxs-lookup"><span data-stu-id="6bc53-167">Pack the project in the current directory and place the resulting packages into the `nupkgs` folder:</span></span>

  ```console
  dotnet pack --output nupkgs
  ```

* <span data-ttu-id="6bc53-168">Geçerli dizinde içinde proje pack `nupkgs` klasörü ve derleme adımı atla:</span><span class="sxs-lookup"><span data-stu-id="6bc53-168">Pack the project in the current directory into the `nupkgs` folder and skip the build step:</span></span>

  ```console
  dotnet pack --no-build --output nupkgs
  ```

* <span data-ttu-id="6bc53-169">Projeyle Sürüm soneki olarak yapılandırılmış `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` içinde *.csproj* dosya, geçerli proje pack ve elde edilen paket sürümü ile belirtilen sonek güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="6bc53-169">With the project's version suffix configured as `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` in the *.csproj* file, pack the current project and update the resulting package version with the given suffix:</span></span>

  ```console
  dotnet pack --version-suffix "ci-1234"
  ```

* <span data-ttu-id="6bc53-170">Paket sürümü kümesine `2.1.0` ile `PackageVersion` MSBuild özelliği:</span><span class="sxs-lookup"><span data-stu-id="6bc53-170">Set the package version to `2.1.0` with the `PackageVersion` MSBuild property:</span></span>

  ```console
  dotnet pack -p:PackageVersion=2.1.0
  ```

* <span data-ttu-id="6bc53-171">Belirli bir proje pack [hedef Framework'ü](../../standard/frameworks.md):</span><span class="sxs-lookup"><span data-stu-id="6bc53-171">Pack the project for a specific [target framework](../../standard/frameworks.md):</span></span>

  ```console
  dotnet pack -p:TargetFrameworks=net45
  ```

* <span data-ttu-id="6bc53-172">Proje paketi ve belirli bir çalışma zamanı (Windows 10) geri yükleme işlemi için (.NET Core SDK 2.0 ve sonraki sürümler) kullanın:</span><span class="sxs-lookup"><span data-stu-id="6bc53-172">Pack the project and use a specific runtime (Windows 10) for the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

  ```console
  dotnet pack --runtime win10-x64
  ```

* <span data-ttu-id="6bc53-173">Project kullanarak paketi bir [.nuspec dosyası](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec):</span><span class="sxs-lookup"><span data-stu-id="6bc53-173">Pack the project using a [.nuspec file](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec):</span></span>

  ```console
  dotnet pack ~/projects/app1/project.csproj /p:NuspecFile=~/projects/app1/project.nuspec /p:NuspecBasePath=~/projects/app1/nuget
  ```
