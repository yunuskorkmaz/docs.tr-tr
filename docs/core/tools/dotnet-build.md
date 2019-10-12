---
title: DotNet derleme komutu
description: DotNet derleme komutu bir projeyi ve tüm bağımlılıklarını oluşturur.
ms.date: 10/07/2019
ms.openlocfilehash: db353feebab920dc8f63b9854d14f050adeb0b79
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250187"
---
# <a name="dotnet-build"></a><span data-ttu-id="c8d6c-103">dotnet build</span><span class="sxs-lookup"><span data-stu-id="c8d6c-103">dotnet build</span></span>

<span data-ttu-id="c8d6c-104">**Bu makale şu şekilde geçerlidir: ✓** .NET Core 1. x SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="c8d6c-104">**This article applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="c8d6c-105">Name</span><span class="sxs-lookup"><span data-stu-id="c8d6c-105">Name</span></span>

<span data-ttu-id="c8d6c-106">`dotnet build`-bir projeyi ve tüm bağımlılıklarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-106">`dotnet build` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c8d6c-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="c8d6c-107">Synopsis</span></span>

```dotnetcli
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--force] [--interactive] [--no-dependencies]
    [--no-incremental] [--no-restore] [--nologo] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```

## <a name="description"></a><span data-ttu-id="c8d6c-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c8d6c-108">Description</span></span>

<span data-ttu-id="c8d6c-109">@No__t-0 komutu, projeyi ve onun bağımlılıklarını bir ikili dosya kümesine oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-109">The `dotnet build` command builds the project and its dependencies into a set of binaries.</span></span> <span data-ttu-id="c8d6c-110">İkililer, bir. *pdb* uzantısıyla hata ayıklama için kullanılan bir *. dll* uzantısına ve sembol dosyalarına sahip olan ara dil (IL) dosyalarındaki projenin kodunu içerir.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-110">The binaries include the project's code in Intermediate Language (IL) files with a *.dll* extension and symbol files used for debugging with a *.pdb* extension.</span></span> <span data-ttu-id="c8d6c-111">Uygulamanın bağımlılıklarını listeleyen bir bağımlılıklar JSON dosyası ( *. Deps. JSON*) oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-111">A dependencies JSON file (*.deps.json*) is produced that lists the dependencies of the application.</span></span> <span data-ttu-id="c8d6c-112">Bir *. runtimeconfig. JSON* dosyası oluşturulur, bu, paylaşılan çalışma zamanını ve uygulamanın sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-112">A *.runtimeconfig.json* file is produced, which specifies the shared runtime and its version for the application.</span></span>

<span data-ttu-id="c8d6c-113">Projenin NuGet kitaplığı gibi üçüncü taraf bağımlılıkları varsa, bunlar NuGet önbelleğinden çözülür ve projenin oluşturulan çıkışıyla birlikte kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-113">If the project has third-party dependencies, such as libraries from NuGet, they're resolved from the NuGet cache and aren't available with the project's built output.</span></span> <span data-ttu-id="c8d6c-114">Bu şekilde `dotnet build` ürünü, çalıştırmak için başka bir makineye aktarılmaya hazırlanmıyor.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-114">With that in mind, the product of `dotnet build` isn't ready to be transferred to another machine to run.</span></span> <span data-ttu-id="c8d6c-115">Bu, yürütülebilir bir proje (bir uygulama) oluşturmanın, .NET Framework yüklendiği herhangi bir makinede çalıştırılabilir bir çıktı oluşturduğu .NET Framework davranışına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-115">This is in contrast to the behavior of the .NET Framework in which building an executable project (an application) produces output that's runnable on any machine where the .NET Framework is installed.</span></span> <span data-ttu-id="c8d6c-116">.NET Core ile benzer bir deneyim sunmak için [DotNet Publish](dotnet-publish.md) komutunu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-116">To have a similar experience with .NET Core, you need to use the [dotnet publish](dotnet-publish.md) command.</span></span> <span data-ttu-id="c8d6c-117">Daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="c8d6c-117">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span>

<span data-ttu-id="c8d6c-118">Oluşturma, uygulamanızın bağımlılıklarını listeleyen *Project. varlıklar. JSON* dosyasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-118">Building requires the *project.assets.json* file, which lists the dependencies of your application.</span></span> <span data-ttu-id="c8d6c-119">[@No__t-1](dotnet-restore.md) yürütüldüğünde dosya oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-119">The file is created when [`dotnet restore`](dotnet-restore.md) is executed.</span></span> <span data-ttu-id="c8d6c-120">Varlıklar dosyası olmadan, Araçlar başvuru derlemelerini çözemez, bu da hatalara neden olur.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-120">Without the assets file in place, the tooling can't resolve reference assemblies, which results in errors.</span></span> <span data-ttu-id="c8d6c-121">.NET Core 1. x SDK ile, `dotnet build` ' i çalıştırmadan önce `dotnet restore` ' ı açık olarak çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-121">With .NET Core 1.x SDK, you needed to explicitly run `dotnet restore` before running `dotnet build`.</span></span> <span data-ttu-id="c8d6c-122">@No__t-1 ' i çalıştırdığınızda `dotnet restore`, .NET Core 2,0 SDK ile başlayarak örtülü olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-122">Starting with .NET Core 2.0 SDK, `dotnet restore` runs implicitly when you run `dotnet build`.</span></span> <span data-ttu-id="c8d6c-123">Build komutunu çalıştırırken örtük geri yüklemeyi devre dışı bırakmak istiyorsanız, `--no-restore` seçeneğini geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-123">If you want to disable implicit restore when running the build command, you can pass the `--no-restore` option.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

<span data-ttu-id="c8d6c-124">Projenin yürütülebilir olup olmadığı veya proje dosyasındaki `<OutputType>` özelliği tarafından belirlenmediği.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-124">Whether the project is executable or not is determined by the `<OutputType>` property in the project file.</span></span> <span data-ttu-id="c8d6c-125">Aşağıdaki örnekte yürütülebilir kod üreten bir proje gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="c8d6c-125">The following example shows a project that produces executable code:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="c8d6c-126">Bir kitaplık oluşturmak için `<OutputType>` özelliğini atlayın.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-126">To produce a library, omit the `<OutputType>` property.</span></span> <span data-ttu-id="c8d6c-127">Oluşturulan çıktıda ana fark, bir kitaplık için Il DLL 'sinin giriş noktaları içermemesi ve yürütülemeyecek.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-127">The main difference in built output is that the IL DLL for a library doesn't contain entry points and can't be executed.</span></span>

### <a name="msbuild"></a><span data-ttu-id="c8d6c-128">MSBuild</span><span class="sxs-lookup"><span data-stu-id="c8d6c-128">MSBuild</span></span>

<span data-ttu-id="c8d6c-129">`dotnet build`, projeyi derlemek için MSBuild kullanır, bu nedenle hem paralel hem de artımlı yapıları destekler.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-129">`dotnet build` uses MSBuild to build the project, so it supports both parallel and incremental builds.</span></span> <span data-ttu-id="c8d6c-130">Daha fazla bilgi için bkz. [Artımlı derlemeler](/visualstudio/msbuild/incremental-builds).</span><span class="sxs-lookup"><span data-stu-id="c8d6c-130">For more information, see [Incremental Builds](/visualstudio/msbuild/incremental-builds).</span></span>

<span data-ttu-id="c8d6c-131">@No__t-0 komutu, seçeneklerini ayarlamak için `-p` veya bir günlükçü tanımlamak için `-l` gibi MSBuild seçeneklerini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-131">In addition to its options, the `dotnet build` command accepts MSBuild options, such as `-p` for setting properties or `-l` to define a logger.</span></span> <span data-ttu-id="c8d6c-132">Bu seçenekler hakkında daha fazla bilgi için bkz. [MSBuild komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="c8d6c-132">For more information about these options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="c8d6c-133">Ayrıca [DotNet MSBuild](dotnet-msbuild.md) komutunu da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-133">Or you can also use the [dotnet msbuild](dotnet-msbuild.md) command.</span></span>

<span data-ttu-id="c8d6c-134">@No__t-0 ' ın çalıştırılması `dotnet msbuild -restore -target:Build` ' e eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-134">Running `dotnet build` is equivalent to `dotnet msbuild -restore -target:Build`.</span></span>

## <a name="arguments"></a><span data-ttu-id="c8d6c-135">Arguments</span><span class="sxs-lookup"><span data-stu-id="c8d6c-135">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="c8d6c-136">Derlenecek proje veya çözüm dosyası.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-136">The project or solution file to build.</span></span> <span data-ttu-id="c8d6c-137">Bir proje veya çözüm dosyası belirtilmemişse, MSBuild, *proj* veya *sln* 'de biten bir dosya uzantısına sahip bir dosya için geçerli çalışma dizinini arar ve bu dosyayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-137">If a project or solution file isn't specified, MSBuild searches the current working directory for a file that has a file extension that ends in either *proj* or *sln* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="c8d6c-138">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="c8d6c-138">Options</span></span>

* **`-c|--configuration {CONFIGURATION}`**

  <span data-ttu-id="c8d6c-139">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-139">Defines the build configuration.</span></span> <span data-ttu-id="c8d6c-140">Çoğu proje için varsayılan değer `Debug` ' dır, ancak projenizde derleme yapılandırma ayarlarını geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-140">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c8d6c-141">Belirli bir [çerçeve](../../standard/frameworks.md)için derlenir.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-141">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="c8d6c-142">Çerçeve [Proje dosyasında](csproj.md)tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-142">The framework must be defined in the [project file](csproj.md).</span></span>

* **`--force`**

  <span data-ttu-id="c8d6c-143">Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-143">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="c8d6c-144">Bu bayrağın belirtilmesi, *Project. varlıklar. JSON* dosyasını silme ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-144">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span> <span data-ttu-id="c8d6c-145">.NET Core 2,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-145">Available since .NET Core 2.0 SDK.</span></span>

* **`-h|--help`**

  <span data-ttu-id="c8d6c-146">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-146">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="c8d6c-147">Komutun Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-147">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="c8d6c-148">Örneğin, kimlik doğrulamasını tamamlamaya yönelik.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-148">For example, to complete authentication.</span></span> <span data-ttu-id="c8d6c-149">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-149">Available since .NET Core 3.0 SDK.</span></span>

* **`--no-dependencies`**

  <span data-ttu-id="c8d6c-150">Projeden projeye (P2P) başvurularını yoksayar ve yalnızca belirtilen kök projeyi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-150">Ignores project-to-project (P2P) references and only builds the specified root project.</span></span>

* **`--no-incremental`**

  <span data-ttu-id="c8d6c-151">Derlemeyi Artımlı derleme için güvenli değil olarak işaretler.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-151">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="c8d6c-152">Bu bayrak, artımlı derlemeyi kapatır ve projenin bağımlılık grafiğinin temiz bir yeniden oluşturulmasına zorlar.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-152">This flag turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

* **`--no-restore`**

  <span data-ttu-id="c8d6c-153">Derleme sırasında örtük geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-153">Doesn't execute an implicit restore during build.</span></span> <span data-ttu-id="c8d6c-154">.NET Core 2,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-154">Available since .NET Core 2.0 SDK.</span></span>

* **`--nologo`**

  <span data-ttu-id="c8d6c-155">Başlangıç başlığını veya telif hakkı iletisini görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-155">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="c8d6c-156">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-156">Available since .NET Core 3.0 SDK.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="c8d6c-157">Oluşturulan ikililerin yerleştirileceği dizin.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-157">Directory in which to place the built binaries.</span></span> <span data-ttu-id="c8d6c-158">Ayrıca, bu seçeneği belirttiğinizde `--framework` tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-158">You also need to define `--framework` when you specify this option.</span></span> <span data-ttu-id="c8d6c-159">Belirtilmemişse, varsayılan yol `./bin/<configuration>/<framework>/` ' dır.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-159">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="c8d6c-160">Hedef çalışma zamanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-160">Specifies the target runtime.</span></span> <span data-ttu-id="c8d6c-161">Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="c8d6c-161">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="c8d6c-162">MSBuild ayrıntı düzeyi düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-162">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="c8d6c-163">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` ve `diag[nostic]` ' dir.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-163">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="c8d6c-164">Varsayılan, `minimal` değeridir.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-164">The default is `minimal`.</span></span>

* **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="c8d6c-165">Projeyi oluştururken kullanılacak `$(VersionSuffix)` özelliğinin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-165">Sets the value of the `$(VersionSuffix)` property to use when building the project.</span></span> <span data-ttu-id="c8d6c-166">Bu yalnızca `$(Version)` özelliği ayarlanmamışsa işe yarar.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-166">This only works if the `$(Version)` property isn't set.</span></span> <span data-ttu-id="c8d6c-167">Sonra, `$(Version)`, `$(VersionSuffix)` ile Birleşik @no__t bir çizgiyle ayrılmış şekilde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="c8d6c-167">Then, `$(Version)` is set to the `$(VersionPrefix)` combined with the `$(VersionSuffix)`, separated by a dash.</span></span>

## <a name="examples"></a><span data-ttu-id="c8d6c-168">Örnekler</span><span class="sxs-lookup"><span data-stu-id="c8d6c-168">Examples</span></span>

* <span data-ttu-id="c8d6c-169">Bir proje ve bağımlılıklarını oluşturun:</span><span class="sxs-lookup"><span data-stu-id="c8d6c-169">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet build
  ```

* <span data-ttu-id="c8d6c-170">Yayın yapılandırması kullanarak bir proje ve bağımlılıklarını oluşturun:</span><span class="sxs-lookup"><span data-stu-id="c8d6c-170">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet build --configuration Release
  ```

* <span data-ttu-id="c8d6c-171">Belirli bir çalışma zamanı için bir proje ve bağımlılıklarını oluşturun (Bu örnekte Ubuntu 18,04):</span><span class="sxs-lookup"><span data-stu-id="c8d6c-171">Build a project and its dependencies for a specific runtime (in this example, Ubuntu 18.04):</span></span>

  ```dotnetcli
  dotnet build --runtime ubuntu.18.04-x64
  ```

* <span data-ttu-id="c8d6c-172">Projeyi derleyin ve geri yükleme işlemi sırasında belirtilen NuGet paket kaynağını kullanın (.NET Core 2,0 SDK ve sonraki sürümleri):</span><span class="sxs-lookup"><span data-stu-id="c8d6c-172">Build the project and use the specified NuGet package source during the restore operation (.NET Core 2.0 SDK and later versions):</span></span>

  ```dotnetcli
  dotnet build --source c:\packages\mypackages
  ```

* <span data-ttu-id="c8d6c-173">Projeyi derleyin ve `-p` [MSBuild seçeneğini](#msbuild)kullanarak bir yapı parametresi olarak 1.2.3.4 öğesini ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="c8d6c-173">Build the project and set version 1.2.3.4 as a build parameter using the `-p` [MSBuild option](#msbuild):</span></span>

  ```dotnetcli
  dotnet build -p:Version=1.2.3.4
  ```
