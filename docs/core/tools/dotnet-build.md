---
title: DotNet oluşturma komutu
description: Dotnet bir projeyi ve tüm bağımlılıklarını komut derlemeleri oluşturun.
ms.date: 04/24/2019
ms.openlocfilehash: df264fe830259832e5c75db9fd71230ba70a9f18
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65959198"
---
# <a name="dotnet-build"></a><span data-ttu-id="45596-103">dotnet build</span><span class="sxs-lookup"><span data-stu-id="45596-103">dotnet build</span></span>

<span data-ttu-id="45596-104">**Bu makale için geçerlidir: ✓** .NET Core SDK'sı 1.x ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="45596-104">**This article applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="45596-105">Ad</span><span class="sxs-lookup"><span data-stu-id="45596-105">Name</span></span>

<span data-ttu-id="45596-106">`dotnet build` -Bir proje ve tüm bağımlılıklarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="45596-106">`dotnet build` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="45596-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="45596-107">Synopsis</span></span>

```
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--force] [--interactive] [--no-dependencies]
    [--no-incremental] [--nologo] [--no-restore] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```

## <a name="description"></a><span data-ttu-id="45596-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="45596-108">Description</span></span>

<span data-ttu-id="45596-109">`dotnet build` Komut projesi ve bağımlılıklarını ikili dosyaları kümesine oluşturur.</span><span class="sxs-lookup"><span data-stu-id="45596-109">The `dotnet build` command builds the project and its dependencies into a set of binaries.</span></span> <span data-ttu-id="45596-110">Proje kodunuzun Ara dil (IL) dosyaları ile ikili dosyaları dahil bir *.dll* ile hata ayıklama için kullanılan uzantı ve sembol dosyalarını bir *.pdb* uzantısı.</span><span class="sxs-lookup"><span data-stu-id="45596-110">The binaries include the project's code in Intermediate Language (IL) files with a *.dll* extension and symbol files used for debugging with a *.pdb* extension.</span></span> <span data-ttu-id="45596-111">Bağımlılıkları JSON dosyası (*\*. deps.json*) üretilir, uygulama ile ilgili bağımlılıklar listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="45596-111">A dependencies JSON file (*\*.deps.json*) is produced that lists the dependencies of the application.</span></span> <span data-ttu-id="45596-112">A  *\*. runtimeconfig.json* dosyası oluşturulur, paylaşılan çalışma zamanı ve uygulamanın sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="45596-112">A *\*.runtimeconfig.json* file is produced, which specifies the shared runtime and its version for the application.</span></span>

<span data-ttu-id="45596-113">Proje, NuGet kitaplıklarından gibi üçüncü taraf bağımlılıkları varsa, NuGet önbellekten çözümlenen ve projenin çıkışı ile kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="45596-113">If the project has third-party dependencies, such as libraries from NuGet, they're resolved from the NuGet cache and aren't available with the project's built output.</span></span> <span data-ttu-id="45596-114">Unutmayın, ürün, ile `dotnet build` çalıştırmak için başka bir makineye aktarılmak hazır değil.</span><span class="sxs-lookup"><span data-stu-id="45596-114">With that in mind, the product of `dotnet build` isn't ready to be transferred to another machine to run.</span></span> <span data-ttu-id="45596-115">Bu .NET Framework'ün aksine hangi binada bir yürütülebilir proje (uygulama), herhangi bir makinede çalıştırılabilir bir çıktı üretir. .NET Framework yüklendiği davranışıdır.</span><span class="sxs-lookup"><span data-stu-id="45596-115">This is in contrast to the behavior of the .NET Framework in which building an executable project (an application) produces output that's runnable on any machine where the .NET Framework is installed.</span></span> <span data-ttu-id="45596-116">.NET Core ile benzer bir deneyim sağlamak için kullanmanız gerekir [dotnet yayımlama](dotnet-publish.md) komutu.</span><span class="sxs-lookup"><span data-stu-id="45596-116">To have a similar experience with .NET Core, you need to use the [dotnet publish](dotnet-publish.md) command.</span></span> <span data-ttu-id="45596-117">Daha fazla bilgi için [.NET Core uygulaması dağıtımını](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="45596-117">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span>

<span data-ttu-id="45596-118">Yapı gerektirir *project.assets.json* dosyasını uygulamanızın bağımlılıklar listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="45596-118">Building requires the *project.assets.json* file, which lists the dependencies of your application.</span></span> <span data-ttu-id="45596-119">Bir dosya oluşturulur [ `dotnet restore` ](dotnet-restore.md) yürütülür.</span><span class="sxs-lookup"><span data-stu-id="45596-119">The file is created when [`dotnet restore`](dotnet-restore.md) is executed.</span></span> <span data-ttu-id="45596-120">Varlıklar dosyayı yerinde araç hataları sonuçlanır başvuru derlemelerini çözümlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="45596-120">Without the assets file in place, the tooling can't resolve reference assemblies, which results in errors.</span></span> <span data-ttu-id="45596-121">.NET Core 1.x SDK'sı, gerekli açıkça çalıştırılacak `dotnet restore` çalıştırmadan önce `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="45596-121">With .NET Core 1.x SDK, you needed to explicitly run the `dotnet restore` before running `dotnet build`.</span></span> <span data-ttu-id="45596-122">.NET Core 2.0 SDK ile başlayarak `dotnet restore` çalıştırdığınızda örtülü olarak çalışan `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="45596-122">Starting with .NET Core 2.0 SDK, `dotnet restore` runs implicitly when you run `dotnet build`.</span></span> <span data-ttu-id="45596-123">Oluşturma komutu çalıştırırken örtük geri yükleme devre dışı bırakmak isterseniz, geçirebilirsiniz `--no-restore` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="45596-123">If you want to disable implicit restore when running the build command, you can pass the `--no-restore` option.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

<span data-ttu-id="45596-124">Projenin yürütülebilir olup olmamasına göre belirlenen `<OutputType>` proje dosyasındaki özellik.</span><span class="sxs-lookup"><span data-stu-id="45596-124">Whether the project is executable or not is determined by the `<OutputType>` property in the project file.</span></span> <span data-ttu-id="45596-125">Aşağıdaki örnek, yürütülebilir kod üreten bir proje gösterir:</span><span class="sxs-lookup"><span data-stu-id="45596-125">The following example shows a project that produces executable code:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="45596-126">Bir kitaplığı üretmek için atla `<OutputType>` özelliği.</span><span class="sxs-lookup"><span data-stu-id="45596-126">To produce a library, omit the `<OutputType>` property.</span></span> <span data-ttu-id="45596-127">Çıkışı ana fark, bir kitaplık için IL DLL giriş noktalarını içermiyor ve yürütülemez ' dir.</span><span class="sxs-lookup"><span data-stu-id="45596-127">The main difference in built output is that the IL DLL for a library doesn't contain entry points and can't be executed.</span></span>

### <a name="msbuild"></a><span data-ttu-id="45596-128">MSBuild</span><span class="sxs-lookup"><span data-stu-id="45596-128">MSBuild</span></span>

<span data-ttu-id="45596-129">`dotnet build` Projeyi derlemek için MSBuild kullanır, hem paralel hem de artımlı destekler şekilde oluşturur.</span><span class="sxs-lookup"><span data-stu-id="45596-129">`dotnet build` uses MSBuild to build the project, so it supports both parallel and incremental builds.</span></span> <span data-ttu-id="45596-130">Daha fazla bilgi için [artımlı derlemeler](/visualstudio/msbuild/incremental-builds).</span><span class="sxs-lookup"><span data-stu-id="45596-130">For more information, see [Incremental Builds](/visualstudio/msbuild/incremental-builds).</span></span>

<span data-ttu-id="45596-131">Kendi seçenekleri yanı sıra `dotnet build` komutu kabul MSBUILD seçenekleri gibi `-p` özelliklerini ayarlamak için veya `-l` bir Günlükçü tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="45596-131">In addition to its options, the `dotnet build` command accepts MSBuild options, such as `-p` for setting properties or `-l` to define a logger.</span></span> <span data-ttu-id="45596-132">Bu seçenekler hakkında daha fazla bilgi için bkz. [MSBuild komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="45596-132">For more information about these options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="45596-133">Ya da ayrıca [dotnet msbuild](dotnet-msbuild.md) komutu.</span><span class="sxs-lookup"><span data-stu-id="45596-133">Or you can also use the [dotnet msbuild](dotnet-msbuild.md) command.</span></span>

<span data-ttu-id="45596-134">Çalışan `dotnet build` eşdeğerdir `dotnet msbuild -restore -target:Build`.</span><span class="sxs-lookup"><span data-stu-id="45596-134">Running `dotnet build` is equivalent to `dotnet msbuild -restore -target:Build`.</span></span>

## <a name="arguments"></a><span data-ttu-id="45596-135">Arguments</span><span class="sxs-lookup"><span data-stu-id="45596-135">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="45596-136">Derleme için proje veya çözüm dosyası.</span><span class="sxs-lookup"><span data-stu-id="45596-136">The project or solution file to build.</span></span> <span data-ttu-id="45596-137">Bir proje veya çözüm dosyası belirtilmezse, MSBuild içinde biten bir dosya uzantısına sahip bir dosya için geçerli çalışma dizini arar *proj* veya *sln* ve bu dosyayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="45596-137">If a project or solution file isn't specified, MSBuild searches the current working directory for a file that has a file extension that ends in either *proj* or *sln* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="45596-138">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="45596-138">Options</span></span>

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="45596-139">Derleme yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="45596-139">Defines the build configuration.</span></span> <span data-ttu-id="45596-140">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="45596-140">The default value is `Debug`.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="45596-141">Özel bir derleme [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="45596-141">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="45596-142">Framework tanımlanmalıdır [proje dosyası](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="45596-142">The framework must be defined in the [project file](csproj.md).</span></span>

* **`--force`**

  <span data-ttu-id="45596-143">Son geri yükleme başarılı olduysa bile çözülmesi için tüm bağımlılıkların zorlar.</span><span class="sxs-lookup"><span data-stu-id="45596-143">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="45596-144">Bu bayrak belirten aynıdır silme *project.assets.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="45596-144">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span> <span data-ttu-id="45596-145">.NET Core 2.0 SDK'sı bu yana kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="45596-145">Available since .NET Core 2.0 SDK.</span></span>

* **`-h|--help`**

  <span data-ttu-id="45596-146">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="45596-146">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="45596-147">Durdurmak ve kullanıcı girişi ya da eylem için beklemek için komutu sağlar.</span><span class="sxs-lookup"><span data-stu-id="45596-147">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="45596-148">Örneğin, kimlik doğrulamasını tamamlamak için.</span><span class="sxs-lookup"><span data-stu-id="45596-148">For example, to complete authentication.</span></span> <span data-ttu-id="45596-149">.NET Core SDK 3.0 bu yana kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="45596-149">Available since .NET Core 3.0 SDK.</span></span>

* **`--no-dependencies`**

  <span data-ttu-id="45596-150">Projeden projeye (P2P) başvurularını yoksayar ve yalnızca belirtilen kök projeyi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="45596-150">Ignores project-to-project (P2P) references and only builds the specified root project.</span></span>

* **`--no-incremental`**

  <span data-ttu-id="45596-151">Derleme Artımlı derleme için güvensiz olarak işaretler.</span><span class="sxs-lookup"><span data-stu-id="45596-151">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="45596-152">Bu bayrak, Artımlı derlemeyi devre dışı bırakır ve temiz bir projenin bağımlılık grafiği yeniden zorlar.</span><span class="sxs-lookup"><span data-stu-id="45596-152">This flag turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

* **`--no-logo`**

  <span data-ttu-id="45596-153">Başlangıç başlığını veya telif hakkı iletisini görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="45596-153">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="45596-154">.NET Core SDK 3.0 bu yana kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="45596-154">Available since .NET Core 3.0 SDK.</span></span>

* **`--no-restore`**

  <span data-ttu-id="45596-155">Örtük bir geri yükleme derleme sırasında yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="45596-155">Doesn't execute an implicit restore during build.</span></span> <span data-ttu-id="45596-156">.NET Core 2.0 SDK'sı bu yana kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="45596-156">Available since .NET Core 2.0 SDK.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="45596-157">Yerleşik ikili dosyaların yerleştirileceği dizin.</span><span class="sxs-lookup"><span data-stu-id="45596-157">Directory in which to place the built binaries.</span></span> <span data-ttu-id="45596-158">Tanımlamanız gereken `--framework` bu seçeneği belirttiğinizde.</span><span class="sxs-lookup"><span data-stu-id="45596-158">You also need to define `--framework` when you specify this option.</span></span> <span data-ttu-id="45596-159">Belirtilmezse, varsayılan yoldur `./bin/<configuration>/<framework>/`.</span><span class="sxs-lookup"><span data-stu-id="45596-159">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="45596-160">Hedef çalışma zamanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="45596-160">Specifies the target runtime.</span></span> <span data-ttu-id="45596-161">Çalışma zamanı tanımlayıcılarının (RID'ler) bir listesi için bkz. [RID Kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="45596-161">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="45596-162">MSBuild ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="45596-162">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="45596-163">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="45596-163">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="45596-164">Varsayılan, `minimal` değeridir.</span><span class="sxs-lookup"><span data-stu-id="45596-164">The default is `minimal`.</span></span>

* **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="45596-165">Ayarlar `$(VersionSuffix)` proje derlenirken kullanılacak özellik.</span><span class="sxs-lookup"><span data-stu-id="45596-165">Sets the value of the `$(VersionSuffix)` property to use when building the project.</span></span> <span data-ttu-id="45596-166">Bu, yalnızca çalışır `$(Version)` özelliği ayarlanmamış.</span><span class="sxs-lookup"><span data-stu-id="45596-166">This only works if the `$(Version)` property isn't set.</span></span> <span data-ttu-id="45596-167">Ardından, `$(Version)` ayarlanır `$(VersionPrefix)` birlikte `$(VersionSuffix)`kısa çizgiyle ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="45596-167">Then, `$(Version)` is set to the `$(VersionPrefix)` combined with the `$(VersionSuffix)`, separated by a dash.</span></span>

## <a name="examples"></a><span data-ttu-id="45596-168">Örnekler</span><span class="sxs-lookup"><span data-stu-id="45596-168">Examples</span></span>

* <span data-ttu-id="45596-169">Bir proje ve bağımlılıkları derleme:</span><span class="sxs-lookup"><span data-stu-id="45596-169">Build a project and its dependencies:</span></span>

  ```console
  dotnet build
  ```

* <span data-ttu-id="45596-170">Bir proje ve bağımlılıkları sürüm yapılandırmasını oluşturun:</span><span class="sxs-lookup"><span data-stu-id="45596-170">Build a project and its dependencies using Release configuration:</span></span>

  ```console
  dotnet build --configuration Release
  ```

* <span data-ttu-id="45596-171">Bir proje ve bağımlılıkları (Bu örnekte, Ubuntu 18.04) belirli bir çalışma zamanı için derleme:</span><span class="sxs-lookup"><span data-stu-id="45596-171">Build a project and its dependencies for a specific runtime (in this example, Ubuntu 18.04):</span></span>

  ```console
  dotnet build --runtime ubuntu.18.04-x64
  ```

* <span data-ttu-id="45596-172">Projeyi oluşturmak ve geri yükleme işlemi sırasında (.NET Core 2.0 SDK'sını ve sonraki sürümler) belirtilen NuGet paket kaynağı kullanın:</span><span class="sxs-lookup"><span data-stu-id="45596-172">Build the project and use the specified NuGet package source during the restore operation (.NET Core 2.0 SDK and later versions):</span></span>

  ```console
  dotnet build --source c:\packages\mypackages
  ```

* <span data-ttu-id="45596-173">Projeyi oluşturmak ve bir yapı parametresini kullanarak olarak sürüm 1.2.3.4 ayarlayın `-p` [MSBuild seçeneği](#msbuild):</span><span class="sxs-lookup"><span data-stu-id="45596-173">Build the project and set version 1.2.3.4 as a build parameter using the `-p` [MSBuild option](#msbuild):</span></span>

  ```console
  dotnet build -p:Version=1.2.3.4
  ```
