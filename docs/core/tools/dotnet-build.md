---
title: DotNet derleme komutu
description: DotNet derleme komutu bir projeyi ve tüm bağımlılıklarını oluşturur.
ms.date: 08/08/2019
ms.openlocfilehash: 0b353d60691fb4bb85536c68dc4ab248f45c3a76
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117749"
---
# <a name="dotnet-build"></a><span data-ttu-id="e8d92-103">dotnet build</span><span class="sxs-lookup"><span data-stu-id="e8d92-103">dotnet build</span></span>

<span data-ttu-id="e8d92-104">**Bu makale şu şekilde geçerlidir: ✓** .NET Core 1. x SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="e8d92-104">**This article applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="e8d92-105">Ad</span><span class="sxs-lookup"><span data-stu-id="e8d92-105">Name</span></span>

<span data-ttu-id="e8d92-106">`dotnet build`-Bir projeyi ve tüm bağımlılıklarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e8d92-106">`dotnet build` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e8d92-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="e8d92-107">Synopsis</span></span>

```dotnetcli
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--force] [--interactive] [--no-dependencies]
    [--no-incremental] [--no-restore] [--nologo] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```

## <a name="description"></a><span data-ttu-id="e8d92-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e8d92-108">Description</span></span>

<span data-ttu-id="e8d92-109">`dotnet build` Komutu projeyi ve onun bağımlılıklarını bir ikili dosya kümesine oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e8d92-109">The `dotnet build` command builds the project and its dependencies into a set of binaries.</span></span> <span data-ttu-id="e8d92-110">İkililer, bir. *pdb* uzantısıyla hata ayıklama için kullanılan bir *. dll* uzantısına ve sembol dosyalarına sahip olan ara dil (IL) dosyalarındaki projenin kodunu içerir.</span><span class="sxs-lookup"><span data-stu-id="e8d92-110">The binaries include the project's code in Intermediate Language (IL) files with a *.dll* extension and symbol files used for debugging with a *.pdb* extension.</span></span> <span data-ttu-id="e8d92-111">Uygulamanın bağımlılıklarını listeleyen bir bağımlılıklar JSON dosyası ( *. Deps. JSON*) oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e8d92-111">A dependencies JSON file (*.deps.json*) is produced that lists the dependencies of the application.</span></span> <span data-ttu-id="e8d92-112">Bir *. runtimeconfig. JSON* dosyası oluşturulur, bu, paylaşılan çalışma zamanını ve uygulamanın sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="e8d92-112">A *.runtimeconfig.json* file is produced, which specifies the shared runtime and its version for the application.</span></span>

<span data-ttu-id="e8d92-113">Projenin NuGet kitaplığı gibi üçüncü taraf bağımlılıkları varsa, bunlar NuGet önbelleğinden çözülür ve projenin oluşturulan çıkışıyla birlikte kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e8d92-113">If the project has third-party dependencies, such as libraries from NuGet, they're resolved from the NuGet cache and aren't available with the project's built output.</span></span> <span data-ttu-id="e8d92-114">Göz önünde bulundurularak, ürünü `dotnet build` çalıştırmak için başka bir makineye aktarılmaya hazırlanın.</span><span class="sxs-lookup"><span data-stu-id="e8d92-114">With that in mind, the product of `dotnet build` isn't ready to be transferred to another machine to run.</span></span> <span data-ttu-id="e8d92-115">Bu, yürütülebilir bir proje (bir uygulama) oluşturmanın, .NET Framework yüklendiği herhangi bir makinede çalıştırılabilir bir çıktı oluşturduğu .NET Framework davranışına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="e8d92-115">This is in contrast to the behavior of the .NET Framework in which building an executable project (an application) produces output that's runnable on any machine where the .NET Framework is installed.</span></span> <span data-ttu-id="e8d92-116">.NET Core ile benzer bir deneyim sunmak için [DotNet Publish](dotnet-publish.md) komutunu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e8d92-116">To have a similar experience with .NET Core, you need to use the [dotnet publish](dotnet-publish.md) command.</span></span> <span data-ttu-id="e8d92-117">Daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="e8d92-117">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span>

<span data-ttu-id="e8d92-118">Oluşturma, uygulamanızın bağımlılıklarını listeleyen *Project. varlıklar. JSON* dosyasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e8d92-118">Building requires the *project.assets.json* file, which lists the dependencies of your application.</span></span> <span data-ttu-id="e8d92-119">Dosya yürütüldüğünde oluşturulur [`dotnet restore`](dotnet-restore.md) .</span><span class="sxs-lookup"><span data-stu-id="e8d92-119">The file is created when [`dotnet restore`](dotnet-restore.md) is executed.</span></span> <span data-ttu-id="e8d92-120">Varlıklar dosyası olmadan, Araçlar başvuru derlemelerini çözemez, bu da hatalara neden olur.</span><span class="sxs-lookup"><span data-stu-id="e8d92-120">Without the assets file in place, the tooling can't resolve reference assemblies, which results in errors.</span></span> <span data-ttu-id="e8d92-121">.NET Core 1. x SDK ile, çalıştırmadan `dotnet restore` `dotnet build`önce açık olarak çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e8d92-121">With .NET Core 1.x SDK, you needed to explicitly run the `dotnet restore` before running `dotnet build`.</span></span> <span data-ttu-id="e8d92-122">.NET Core 2,0 SDK ile başlayarak, `dotnet restore` çalıştırdığınızda `dotnet build`örtülü olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="e8d92-122">Starting with .NET Core 2.0 SDK, `dotnet restore` runs implicitly when you run `dotnet build`.</span></span> <span data-ttu-id="e8d92-123">Build komutunu çalıştırırken örtük geri yüklemeyi devre dışı bırakmak istiyorsanız, `--no-restore` seçeneğini geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8d92-123">If you want to disable implicit restore when running the build command, you can pass the `--no-restore` option.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

<span data-ttu-id="e8d92-124">Projenin yürütülebilir olup olmadığı veya proje dosyasındaki `<OutputType>` özelliği tarafından belirlenmediği.</span><span class="sxs-lookup"><span data-stu-id="e8d92-124">Whether the project is executable or not is determined by the `<OutputType>` property in the project file.</span></span> <span data-ttu-id="e8d92-125">Aşağıdaki örnekte yürütülebilir kod üreten bir proje gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="e8d92-125">The following example shows a project that produces executable code:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="e8d92-126">Bir kitaplık oluşturmak için `<OutputType>` özelliği atlayın.</span><span class="sxs-lookup"><span data-stu-id="e8d92-126">To produce a library, omit the `<OutputType>` property.</span></span> <span data-ttu-id="e8d92-127">Oluşturulan çıktıda ana fark, bir kitaplık için Il DLL 'sinin giriş noktaları içermemesi ve yürütülemeyecek.</span><span class="sxs-lookup"><span data-stu-id="e8d92-127">The main difference in built output is that the IL DLL for a library doesn't contain entry points and can't be executed.</span></span>

### <a name="msbuild"></a><span data-ttu-id="e8d92-128">MSBuild</span><span class="sxs-lookup"><span data-stu-id="e8d92-128">MSBuild</span></span>

<span data-ttu-id="e8d92-129">`dotnet build`, projeyi derlemek için MSBuild kullanır, bu nedenle hem paralel hem de artımlı yapıları destekler.</span><span class="sxs-lookup"><span data-stu-id="e8d92-129">`dotnet build` uses MSBuild to build the project, so it supports both parallel and incremental builds.</span></span> <span data-ttu-id="e8d92-130">Daha fazla bilgi için bkz. [Artımlı derlemeler](/visualstudio/msbuild/incremental-builds).</span><span class="sxs-lookup"><span data-stu-id="e8d92-130">For more information, see [Incremental Builds](/visualstudio/msbuild/incremental-builds).</span></span>

<span data-ttu-id="e8d92-131">Seçeneklerine `dotnet build` ek olarak komut, özellikleri ayarlama veya `-l` bir günlükçü tanımlama gibi MSBuild seçeneklerini `-p` kabul eder.</span><span class="sxs-lookup"><span data-stu-id="e8d92-131">In addition to its options, the `dotnet build` command accepts MSBuild options, such as `-p` for setting properties or `-l` to define a logger.</span></span> <span data-ttu-id="e8d92-132">Bu seçenekler hakkında daha fazla bilgi için bkz. [MSBuild komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="e8d92-132">For more information about these options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="e8d92-133">Ayrıca [DotNet MSBuild](dotnet-msbuild.md) komutunu da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8d92-133">Or you can also use the [dotnet msbuild](dotnet-msbuild.md) command.</span></span>

<span data-ttu-id="e8d92-134">Çalışıyor `dotnet build` , ile `dotnet msbuild -restore -target:Build`eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="e8d92-134">Running `dotnet build` is equivalent to `dotnet msbuild -restore -target:Build`.</span></span>

## <a name="arguments"></a><span data-ttu-id="e8d92-135">Arguments</span><span class="sxs-lookup"><span data-stu-id="e8d92-135">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="e8d92-136">Derlenecek proje veya çözüm dosyası.</span><span class="sxs-lookup"><span data-stu-id="e8d92-136">The project or solution file to build.</span></span> <span data-ttu-id="e8d92-137">Bir proje veya çözüm dosyası belirtilmemişse, MSBuild, *proj* veya *sln* 'de biten bir dosya uzantısına sahip bir dosya için geçerli çalışma dizinini arar ve bu dosyayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="e8d92-137">If a project or solution file isn't specified, MSBuild searches the current working directory for a file that has a file extension that ends in either *proj* or *sln* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="e8d92-138">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="e8d92-138">Options</span></span>

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="e8d92-139">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e8d92-139">Defines the build configuration.</span></span> <span data-ttu-id="e8d92-140">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e8d92-140">The default value is `Debug`.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="e8d92-141">Belirli bir [çerçeve](../../standard/frameworks.md)için derlenir.</span><span class="sxs-lookup"><span data-stu-id="e8d92-141">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="e8d92-142">Çerçeve [Proje dosyasında](csproj.md)tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e8d92-142">The framework must be defined in the [project file](csproj.md).</span></span>

* **`--force`**

  <span data-ttu-id="e8d92-143">Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar.</span><span class="sxs-lookup"><span data-stu-id="e8d92-143">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="e8d92-144">Bu bayrağın belirtilmesi, *Project. varlıklar. JSON* dosyasını silme ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="e8d92-144">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span> <span data-ttu-id="e8d92-145">.NET Core 2,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e8d92-145">Available since .NET Core 2.0 SDK.</span></span>

* **`-h|--help`**

  <span data-ttu-id="e8d92-146">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="e8d92-146">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="e8d92-147">Komutun Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="e8d92-147">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="e8d92-148">Örneğin, kimlik doğrulamasını tamamlamaya yönelik.</span><span class="sxs-lookup"><span data-stu-id="e8d92-148">For example, to complete authentication.</span></span> <span data-ttu-id="e8d92-149">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e8d92-149">Available since .NET Core 3.0 SDK.</span></span>

* **`--no-dependencies`**

  <span data-ttu-id="e8d92-150">Projeden projeye (P2P) başvurularını yoksayar ve yalnızca belirtilen kök projeyi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e8d92-150">Ignores project-to-project (P2P) references and only builds the specified root project.</span></span>

* **`--no-incremental`**

  <span data-ttu-id="e8d92-151">Derlemeyi Artımlı derleme için güvenli değil olarak işaretler.</span><span class="sxs-lookup"><span data-stu-id="e8d92-151">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="e8d92-152">Bu bayrak, artımlı derlemeyi kapatır ve projenin bağımlılık grafiğinin temiz bir yeniden oluşturulmasına zorlar.</span><span class="sxs-lookup"><span data-stu-id="e8d92-152">This flag turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

* **`--no-restore`**

  <span data-ttu-id="e8d92-153">Derleme sırasında örtük geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="e8d92-153">Doesn't execute an implicit restore during build.</span></span> <span data-ttu-id="e8d92-154">.NET Core 2,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e8d92-154">Available since .NET Core 2.0 SDK.</span></span>

* **`--nologo`**

  <span data-ttu-id="e8d92-155">Başlangıç başlığını veya telif hakkı iletisini görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="e8d92-155">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="e8d92-156">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e8d92-156">Available since .NET Core 3.0 SDK.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="e8d92-157">Oluşturulan ikililerin yerleştirileceği dizin.</span><span class="sxs-lookup"><span data-stu-id="e8d92-157">Directory in which to place the built binaries.</span></span> <span data-ttu-id="e8d92-158">Ayrıca, bu seçeneği ne `--framework` zaman belirttiğinizde tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e8d92-158">You also need to define `--framework` when you specify this option.</span></span> <span data-ttu-id="e8d92-159">Belirtilmemişse, varsayılan yol olur `./bin/<configuration>/<framework>/`.</span><span class="sxs-lookup"><span data-stu-id="e8d92-159">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="e8d92-160">Hedef çalışma zamanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e8d92-160">Specifies the target runtime.</span></span> <span data-ttu-id="e8d92-161">Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="e8d92-161">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="e8d92-162">MSBuild ayrıntı düzeyi düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e8d92-162">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="e8d92-163">İzin verilen değerler `q[uiet]` `m[inimal]` ,`n[ormal]`,, ve .`diag[nostic]` `d[etailed]`</span><span class="sxs-lookup"><span data-stu-id="e8d92-163">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="e8d92-164">Varsayılan, `minimal` değeridir.</span><span class="sxs-lookup"><span data-stu-id="e8d92-164">The default is `minimal`.</span></span>

* **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="e8d92-165">Proje oluşturulurken kullanılacak `$(VersionSuffix)` özelliğin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e8d92-165">Sets the value of the `$(VersionSuffix)` property to use when building the project.</span></span> <span data-ttu-id="e8d92-166">Bu yalnızca `$(Version)` özellik ayarlanmamışsa işe yarar.</span><span class="sxs-lookup"><span data-stu-id="e8d92-166">This only works if the `$(Version)` property isn't set.</span></span> <span data-ttu-id="e8d92-167">Daha sonra, ile `$(VersionPrefix)` `$(VersionSuffix)`birleştirilmiş olarak ayarlanır, tireyle ayrılır. `$(Version)`</span><span class="sxs-lookup"><span data-stu-id="e8d92-167">Then, `$(Version)` is set to the `$(VersionPrefix)` combined with the `$(VersionSuffix)`, separated by a dash.</span></span>

## <a name="examples"></a><span data-ttu-id="e8d92-168">Örnekler</span><span class="sxs-lookup"><span data-stu-id="e8d92-168">Examples</span></span>

* <span data-ttu-id="e8d92-169">Bir proje ve bağımlılıklarını oluşturun:</span><span class="sxs-lookup"><span data-stu-id="e8d92-169">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet build
  ```

* <span data-ttu-id="e8d92-170">Yayın yapılandırması kullanarak bir proje ve bağımlılıklarını oluşturun:</span><span class="sxs-lookup"><span data-stu-id="e8d92-170">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet build --configuration Release
  ```

* <span data-ttu-id="e8d92-171">Belirli bir çalışma zamanı için bir proje ve bağımlılıklarını oluşturun (Bu örnekte Ubuntu 18,04):</span><span class="sxs-lookup"><span data-stu-id="e8d92-171">Build a project and its dependencies for a specific runtime (in this example, Ubuntu 18.04):</span></span>

  ```dotnetcli
  dotnet build --runtime ubuntu.18.04-x64
  ```

* <span data-ttu-id="e8d92-172">Projeyi derleyin ve geri yükleme işlemi sırasında belirtilen NuGet paket kaynağını kullanın (.NET Core 2,0 SDK ve sonraki sürümleri):</span><span class="sxs-lookup"><span data-stu-id="e8d92-172">Build the project and use the specified NuGet package source during the restore operation (.NET Core 2.0 SDK and later versions):</span></span>

  ```dotnetcli
  dotnet build --source c:\packages\mypackages
  ```

* <span data-ttu-id="e8d92-173">`-p` [MSBuild seçeneğini](#msbuild)kullanarak projeyi derleyin ve derleme parametresi olarak 1.2.3.4 olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="e8d92-173">Build the project and set version 1.2.3.4 as a build parameter using the `-p` [MSBuild option](#msbuild):</span></span>

  ```dotnetcli
  dotnet build -p:Version=1.2.3.4
  ```
