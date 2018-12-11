---
title: DotNet oluşturma komutu
description: Dotnet bir projeyi ve tüm bağımlılıklarını komut derlemeleri oluşturun.
ms.date: 12/04/2018
ms.openlocfilehash: 1e5e05d51f98394b2b77e3a8fc645cf9712b0a0f
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169716"
---
# <a name="dotnet-build"></a><span data-ttu-id="71497-103">DotNet derleme</span><span class="sxs-lookup"><span data-stu-id="71497-103">dotnet build</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="71497-104">Ad</span><span class="sxs-lookup"><span data-stu-id="71497-104">Name</span></span>

<span data-ttu-id="71497-105">`dotnet build` -Bir proje ve tüm bağımlılıklarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="71497-105">`dotnet build` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="71497-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="71497-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="71497-107">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="71497-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--force] [--no-dependencies] [--no-incremental]
    [--no-restore] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="71497-108">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="71497-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--no-dependencies] [--no-incremental] [-o|--output]
    [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="71497-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="71497-109">Description</span></span>

<span data-ttu-id="71497-110">`dotnet build` Komut projesi ve bağımlılıklarını ikili dosyaları kümesine oluşturur.</span><span class="sxs-lookup"><span data-stu-id="71497-110">The `dotnet build` command builds the project and its dependencies into a set of binaries.</span></span> <span data-ttu-id="71497-111">Proje kodunuzun Ara dil (IL) dosyaları ile ikili dosyaları dahil bir *.dll* ile hata ayıklama için kullanılan uzantı ve sembol dosyalarını bir *.pdb* uzantısı.</span><span class="sxs-lookup"><span data-stu-id="71497-111">The binaries include the project's code in Intermediate Language (IL) files with a *.dll* extension and symbol files used for debugging with a *.pdb* extension.</span></span> <span data-ttu-id="71497-112">Bağımlılıkları JSON dosyası (*\*. deps.json*) üretilir, uygulama ile ilgili bağımlılıklar listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="71497-112">A dependencies JSON file (*\*.deps.json*) is produced that lists the dependencies of the application.</span></span> <span data-ttu-id="71497-113">A  *\*. runtimeconfig.json* dosyası oluşturulur, paylaşılan çalışma zamanı ve uygulamanın sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="71497-113">A *\*.runtimeconfig.json* file is produced, which specifies the shared runtime and its version for the application.</span></span>

<span data-ttu-id="71497-114">Proje, NuGet kitaplıklarından gibi üçüncü taraf bağımlılıkları varsa, NuGet önbellekten çözümlenen ve projenin çıkışı ile kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="71497-114">If the project has third-party dependencies, such as libraries from NuGet, they're resolved from the NuGet cache and aren't available with the project's built output.</span></span> <span data-ttu-id="71497-115">Unutmayın, ürün, ile `dotnet build` çalıştırmak için başka bir makineye aktarılmak hazır değil.</span><span class="sxs-lookup"><span data-stu-id="71497-115">With that in mind, the product of `dotnet build` isn't ready to be transferred to another machine to run.</span></span> <span data-ttu-id="71497-116">Bu .NET Framework'ün aksine hangi binada bir yürütülebilir proje (uygulama), herhangi bir makinede çalıştırılabilir bir çıktı üretir. .NET Framework yüklendiği davranışıdır.</span><span class="sxs-lookup"><span data-stu-id="71497-116">This is in contrast to the behavior of the .NET Framework in which building an executable project (an application) produces output that's runnable on any machine where the .NET Framework is installed.</span></span> <span data-ttu-id="71497-117">.NET Core ile benzer bir deneyim sağlamak için kullanmanız gerekir [dotnet yayımlama](dotnet-publish.md) komutu.</span><span class="sxs-lookup"><span data-stu-id="71497-117">To have a similar experience with .NET Core, you need to use the [dotnet publish](dotnet-publish.md) command.</span></span> <span data-ttu-id="71497-118">Daha fazla bilgi için [.NET Core uygulaması dağıtımını](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="71497-118">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span>

<span data-ttu-id="71497-119">Yapı gerektirir *project.assets.json* dosyasını uygulamanızın bağımlılıklar listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="71497-119">Building requires the *project.assets.json* file, which lists the dependencies of your application.</span></span> <span data-ttu-id="71497-120">Bir dosya oluşturulur [ `dotnet restore` ](dotnet-restore.md) yürütülür.</span><span class="sxs-lookup"><span data-stu-id="71497-120">The file is created when [`dotnet restore`](dotnet-restore.md) is executed.</span></span> <span data-ttu-id="71497-121">Varlıklar dosyayı yerinde araç hataları sonuçlanır başvuru derlemelerini çözümlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="71497-121">Without the assets file in place, the tooling cannot resolve reference assemblies, which results in errors.</span></span> <span data-ttu-id="71497-122">.NET Core 1.x SDK'sı, gerekli açıkça çalıştırılacak `dotnet restore` çalıştırmadan önce `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="71497-122">With .NET Core 1.x SDK, you needed to explicitly run the `dotnet restore` before running `dotnet build`.</span></span> <span data-ttu-id="71497-123">.NET Core 2.0 SDK ile başlayarak `dotnet restore` çalıştırdığınızda örtülü olarak çalışan `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="71497-123">Starting with .NET Core 2.0 SDK, `dotnet restore` runs implicitly when you run `dotnet build`.</span></span> <span data-ttu-id="71497-124">Oluşturma komutu çalıştırırken örtük geri yükleme devre dışı bırakmak isterseniz, geçirebilirsiniz `--no-restore` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="71497-124">If you want to disable implicit restore when running the build command, you can pass the `--no-restore` option.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

<span data-ttu-id="71497-125">Projenin yürütülebilir olup olmamasına göre belirlenen `<OutputType>` proje dosyasındaki özellik.</span><span class="sxs-lookup"><span data-stu-id="71497-125">Whether the project is executable or not is determined by the `<OutputType>` property in the project file.</span></span> <span data-ttu-id="71497-126">Aşağıdaki örnek, yürütülebilir kod üreten bir proje gösterir:</span><span class="sxs-lookup"><span data-stu-id="71497-126">The following example shows a project that produces executable code:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="71497-127">Bir kitaplığı üretmek için atla `<OutputType>` özelliği.</span><span class="sxs-lookup"><span data-stu-id="71497-127">In order to produce a library, omit the `<OutputType>` property.</span></span> <span data-ttu-id="71497-128">Çıkışı ana fark, bir kitaplık için IL DLL giriş noktalarını içermiyor ve yürütülemez ' dir.</span><span class="sxs-lookup"><span data-stu-id="71497-128">The main difference in built output is that the IL DLL for a library doesn't contain entry points and can't be executed.</span></span>

### <a name="msbuild"></a><span data-ttu-id="71497-129">MSBuild</span><span class="sxs-lookup"><span data-stu-id="71497-129">MSBuild</span></span>

<span data-ttu-id="71497-130">`dotnet build` Projeyi derlemek için MSBuild kullanır, hem paralel hem de artımlı destekler şekilde oluşturur.</span><span class="sxs-lookup"><span data-stu-id="71497-130">`dotnet build` uses MSBuild to build the project, so it supports both parallel and incremental builds.</span></span> <span data-ttu-id="71497-131">Daha fazla bilgi için [artımlı derlemeler](/visualstudio/msbuild/incremental-builds).</span><span class="sxs-lookup"><span data-stu-id="71497-131">For more information, see [Incremental Builds](/visualstudio/msbuild/incremental-builds).</span></span>

<span data-ttu-id="71497-132">Kendi seçenekleri yanı sıra `dotnet build` komutu kabul MSBUILD seçenekleri gibi `-p` özelliklerini ayarlamak için veya `-l` bir Günlükçü tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="71497-132">In addition to its options, the `dotnet build` command accepts MSBuild options, such as `-p` for setting properties or `-l` to define a logger.</span></span> <span data-ttu-id="71497-133">Bu seçenekler hakkında daha fazla bilgi için bkz. [MSBuild komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="71497-133">For more information about these options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="71497-134">Ya da ayrıca [dotnet msbuild](dotnet-msbuild.md) komutu.</span><span class="sxs-lookup"><span data-stu-id="71497-134">Or you can also use the [dotnet msbuild](dotnet-msbuild.md) command.</span></span>

<span data-ttu-id="71497-135">Çalışan `dotnet build` eşdeğerdir `dotnet msbuild -restore -target:Build`.</span><span class="sxs-lookup"><span data-stu-id="71497-135">Running `dotnet build` is equivalent to `dotnet msbuild -restore -target:Build`.</span></span>

## <a name="arguments"></a><span data-ttu-id="71497-136">Arguments</span><span class="sxs-lookup"><span data-stu-id="71497-136">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="71497-137">Derleme için proje veya çözüm dosyası.</span><span class="sxs-lookup"><span data-stu-id="71497-137">The project or solution file to build.</span></span> <span data-ttu-id="71497-138">Bir proje veya çözüm dosyası belirtilmezse, MSBuild içinde biten bir dosya uzantısına sahip bir dosya için geçerli çalışma dizini arar *proj* veya *sln* ve bu dosyayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="71497-138">If a project or solution file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in either *proj* or *sln* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="71497-139">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="71497-139">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="71497-140">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="71497-140">.NET Core 2.x</span></span>](#tab/netcore2x)

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="71497-141">Derleme yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="71497-141">Defines the build configuration.</span></span> <span data-ttu-id="71497-142">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="71497-142">The default value is `Debug`.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="71497-143">Özel bir derleme [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="71497-143">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="71497-144">Framework tanımlanmalıdır [proje dosyası](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="71497-144">The framework must be defined in the [project file](csproj.md).</span></span>

* **`--force`**

  <span data-ttu-id="71497-145">Son geri yükleme başarılı olduysa bile çözülmesi için tüm bağımlılıkların zorlar.</span><span class="sxs-lookup"><span data-stu-id="71497-145">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="71497-146">Bu bayrak belirten aynıdır silme *project.assets.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="71497-146">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

* **`-h|--help`**

  <span data-ttu-id="71497-147">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="71497-147">Prints out a short help for the command.</span></span>

* **`--no-dependencies`**

  <span data-ttu-id="71497-148">Projeden projeye (P2P) başvurularını yoksayar ve yalnızca belirtilen kök projeyi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="71497-148">Ignores project-to-project (P2P) references and only builds the specified root project.</span></span>

* **`--no-incremental`**

  <span data-ttu-id="71497-149">Derleme Artımlı derleme için güvensiz olarak işaretler.</span><span class="sxs-lookup"><span data-stu-id="71497-149">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="71497-150">Bu bayrak, Artımlı derlemeyi devre dışı bırakır ve temiz bir projenin bağımlılık grafiği yeniden zorlar.</span><span class="sxs-lookup"><span data-stu-id="71497-150">This flag turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

* **`--no-restore`**

  <span data-ttu-id="71497-151">Örtük bir geri yükleme derleme sırasında yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="71497-151">Doesn't execute an implicit restore during build.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="71497-152">Yerleşik ikili dosyaların yerleştirileceği dizin.</span><span class="sxs-lookup"><span data-stu-id="71497-152">Directory in which to place the built binaries.</span></span> <span data-ttu-id="71497-153">Tanımlamanız gereken `--framework` bu seçeneği belirttiğinizde.</span><span class="sxs-lookup"><span data-stu-id="71497-153">You also need to define `--framework` when you specify this option.</span></span> <span data-ttu-id="71497-154">Belirtilmezse, varsayılan yoldur `./bin/<configuration>/<framework>/`.</span><span class="sxs-lookup"><span data-stu-id="71497-154">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="71497-155">Hedef çalışma zamanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="71497-155">Specifies the target runtime.</span></span> <span data-ttu-id="71497-156">Çalışma zamanı tanımlayıcılarının (RID'ler) bir listesi için bkz. [RID Kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="71497-156">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="71497-157">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="71497-157">Sets the verbosity level of the command.</span></span> <span data-ttu-id="71497-158">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="71497-158">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

* **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="71497-159">Sürüm soneki için bir yıldız işareti tanımlar (`*`) proje dosyasının sürümü alanında.</span><span class="sxs-lookup"><span data-stu-id="71497-159">Defines the version suffix for an asterisk (`*`) in the version field of the project file.</span></span> <span data-ttu-id="71497-160">NuGet'ın sürümü yönergeleri biçimdedir.</span><span class="sxs-lookup"><span data-stu-id="71497-160">The format follows NuGet's version guidelines.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="71497-161">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="71497-161">.NET Core 1.x</span></span>](#tab/netcore1x)

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="71497-162">Derleme yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="71497-162">Defines the build configuration.</span></span> <span data-ttu-id="71497-163">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="71497-163">The default value is `Debug`.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="71497-164">Özel bir derleme [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="71497-164">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="71497-165">Framework tanımlanmalıdır [proje dosyası](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="71497-165">The framework must be defined in the [project file](csproj.md).</span></span>

* **`-h|--help`**

  <span data-ttu-id="71497-166">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="71497-166">Prints out a short help for the command.</span></span>

* **`--no-dependencies`**

  <span data-ttu-id="71497-167">Projeden projeye (P2P) başvurularını yoksayar ve yalnızca belirtilen kök projeyi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="71497-167">Ignores project-to-project (P2P) references and only builds the specified root project.</span></span>

* **`--no-incremental`**

  <span data-ttu-id="71497-168">Derleme Artımlı derleme için güvensiz olarak işaretler.</span><span class="sxs-lookup"><span data-stu-id="71497-168">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="71497-169">Bu bayrak, Artımlı derlemeyi devre dışı bırakır ve temiz bir projenin bağımlılık grafiği yeniden zorlar.</span><span class="sxs-lookup"><span data-stu-id="71497-169">This flag turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="71497-170">Yerleşik ikili dosyaların yerleştirileceği dizin.</span><span class="sxs-lookup"><span data-stu-id="71497-170">Directory in which to place the built binaries.</span></span> <span data-ttu-id="71497-171">Tanımlamanız gereken `--framework` bu seçeneği belirttiğinizde.</span><span class="sxs-lookup"><span data-stu-id="71497-171">You also need to define `--framework` when you specify this option.</span></span>

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="71497-172">Hedef çalışma zamanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="71497-172">Specifies the target runtime.</span></span> <span data-ttu-id="71497-173">Çalışma zamanı tanımlayıcılarının (RID'ler) bir listesi için bkz. [RID Kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="71497-173">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="71497-174">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="71497-174">Sets the verbosity level of the command.</span></span> <span data-ttu-id="71497-175">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="71497-175">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

* **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="71497-176">Sürüm soneki için bir yıldız işareti tanımlar (`*`) proje dosyasının sürümü alanında.</span><span class="sxs-lookup"><span data-stu-id="71497-176">Defines the version suffix for an asterisk (`*`) in the version field of the project file.</span></span> <span data-ttu-id="71497-177">NuGet'ın sürümü yönergeleri biçimdedir.</span><span class="sxs-lookup"><span data-stu-id="71497-177">The format follows NuGet's version guidelines.</span></span>

---

## <a name="examples"></a><span data-ttu-id="71497-178">Örnekler</span><span class="sxs-lookup"><span data-stu-id="71497-178">Examples</span></span>

* <span data-ttu-id="71497-179">Bir proje ve bağımlılıkları derleme:</span><span class="sxs-lookup"><span data-stu-id="71497-179">Build a project and its dependencies:</span></span>

  ```console
  dotnet build
  ```

* <span data-ttu-id="71497-180">Bir proje ve bağımlılıkları sürüm yapılandırmasını oluşturun:</span><span class="sxs-lookup"><span data-stu-id="71497-180">Build a project and its dependencies using Release configuration:</span></span>

  ```console
  dotnet build --configuration Release
  ```

* <span data-ttu-id="71497-181">Bir proje ve bağımlılıkları (Bu örnekte, Ubuntu 16.04) belirli bir çalışma zamanı için derleme:</span><span class="sxs-lookup"><span data-stu-id="71497-181">Build a project and its dependencies for a specific runtime (in this example, Ubuntu 16.04):</span></span>

  ```console
  dotnet build --runtime ubuntu.16.04-x64
  ```

* <span data-ttu-id="71497-182">Projeyi oluşturmak ve geri yükleme işlemi sırasında (.NET Core 2.0 SDK'sını ve sonraki sürümler) belirtilen NuGet paket kaynağı kullanın:</span><span class="sxs-lookup"><span data-stu-id="71497-182">Build the project and use the specified NuGet package source during the restore operation (.NET Core 2.0 SDK and later versions):</span></span>

  ```console
  dotnet build --source c:\packages\mypackages
  ```

* <span data-ttu-id="71497-183">Projeyi oluşturmak ve ayarlamak 1.2.3.4 derleme parametre olarak sürüm:</span><span class="sxs-lookup"><span data-stu-id="71497-183">Build the project and set 1.2.3.4 version as a build parameter:</span></span>

  ```console
  dotnet build -p:Version=1.2.3.4
  ```