---
title: DotNet .NET Core CLI command - derleme
description: Dotnet bir proje ve tüm bağımlılıkları komutu derlemeleri oluşturun.
author: mairaw
ms.author: mairaw
ms.date: 03/10/2018
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 2c258f2906be43436b57b9795b5851af88804443
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-build"></a><span data-ttu-id="af92c-103">DotNet derleme</span><span class="sxs-lookup"><span data-stu-id="af92c-103">dotnet-build</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="af92c-104">Ad</span><span class="sxs-lookup"><span data-stu-id="af92c-104">Name</span></span>

<span data-ttu-id="af92c-105">`dotnet build` -Bir proje ve tüm bağımlılıkları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="af92c-105">`dotnet build` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="af92c-106">Özet</span><span class="sxs-lookup"><span data-stu-id="af92c-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="af92c-107">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="af92c-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet build [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--no-dependencies] [--no-incremental]
    [--no-restore] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]
dotnet build [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="af92c-108">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="af92c-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet build [<PROJECT>] [-c|--configuration] [-f|--framework] [--no-dependencies] [--no-incremental] [-o|--output]
    [-r|--runtime] [-v|--verbosity] [--version-suffix]
dotnet build [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="af92c-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="af92c-109">Description</span></span>

<span data-ttu-id="af92c-110">`dotnet build` Komut, ikili dosyalar kümesine proje ve bağımlılıklarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="af92c-110">The `dotnet build` command builds the project and its dependencies into a set of binaries.</span></span> <span data-ttu-id="af92c-111">İkili dosyaları ara dile (IL) dosyalarıyla projenin kod dahil bir *.dll* ile hata ayıklama için kullanılan uzantı ve sembol dosyalarını bir *.pdb* uzantısı.</span><span class="sxs-lookup"><span data-stu-id="af92c-111">The binaries include the project's code in Intermediate Language (IL) files with a *.dll* extension and symbol files used for debugging with a *.pdb* extension.</span></span> <span data-ttu-id="af92c-112">Bağımlılıklar JSON dosyası (*\*. deps.json*) üretilir, uygulama bağımlılıkları listeler.</span><span class="sxs-lookup"><span data-stu-id="af92c-112">A dependencies JSON file (*\*.deps.json*) is produced that lists the dependencies of the application.</span></span> <span data-ttu-id="af92c-113">A  *\*. runtimeconfig.json* dosyası oluşturulur, paylaşılan çalışma zamanı ve uygulama için sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="af92c-113">A *\*.runtimeconfig.json* file is produced, which specifies the shared runtime and its version for the application.</span></span>

<span data-ttu-id="af92c-114">Proje NuGet kitaplıklarından gibi üçüncü taraf bağımlılıkları varsa, NuGet önbellekten çözülmüş ve projenin yerleşik çıktı ile kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="af92c-114">If the project has third-party dependencies, such as libraries from NuGet, they're resolved from the NuGet cache and aren't available with the project's built output.</span></span> <span data-ttu-id="af92c-115">Unutmayın, ürün alanıyla `dotnet build` çalıştırmak için başka bir makineye aktarılması hazır değil.</span><span class="sxs-lookup"><span data-stu-id="af92c-115">With that in mind, the product of `dotnet build` isn't ready to be transferred to another machine to run.</span></span> <span data-ttu-id="af92c-116">Bu .NET Framework'ün aksine hangi binada yürütülebilir bir proje (uygulama) herhangi bir makinede runnable bir çıktı üretir, .NET Framework yüklü olduğu davranıştır.</span><span class="sxs-lookup"><span data-stu-id="af92c-116">This is in contrast to the behavior of the .NET Framework in which building an executable project (an application) produces output that's runnable on any machine where the .NET Framework is installed.</span></span> <span data-ttu-id="af92c-117">.NET Core benzer bir deneyim sağlamak için kullanmanız gereken [dotnet yayımlama](dotnet-publish.md) komutu.</span><span class="sxs-lookup"><span data-stu-id="af92c-117">To have a similar experience with .NET Core, you need to use the [dotnet publish](dotnet-publish.md) command.</span></span> <span data-ttu-id="af92c-118">Daha fazla bilgi için bkz: [.NET Core uygulama dağıtımı](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="af92c-118">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span>

<span data-ttu-id="af92c-119">Yapı gerektirir *project.assets.json* uygulamanızın bağımlılıkları listeler dosya.</span><span class="sxs-lookup"><span data-stu-id="af92c-119">Building requires the *project.assets.json* file, which lists the dependencies of your application.</span></span> <span data-ttu-id="af92c-120">Dosyanın ne zaman oluşturulur [ `dotnet restore` ](dotnet-restore.md) yürütülür.</span><span class="sxs-lookup"><span data-stu-id="af92c-120">The file is created when [`dotnet restore`](dotnet-restore.md) is executed.</span></span> <span data-ttu-id="af92c-121">Varlıklar dosyayı yerinde hangi hatalar sonuçları başvuru derlemeleri araç çözümlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="af92c-121">Without the assets file in place, the tooling cannot resolve reference assemblies, which results in errors.</span></span> <span data-ttu-id="af92c-122">.NET Core 1.x, explicitily için gereken SDK çalıştırmak ile `dotnet restore` çalıştırmadan önce `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="af92c-122">With .NET Core 1.x SDK, you needed to explicitily run the `dotnet restore` before running `dotnet build`.</span></span> <span data-ttu-id="af92c-123">.NET Core 2.0 SDK ile başlayan `dotnet restore` çalıştırdığınızda implicitily çalıştıran `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="af92c-123">Starting with .NET Core 2.0 SDK, `dotnet restore` runs implicitily when you run `dotnet build`.</span></span> <span data-ttu-id="af92c-124">Yapı komutu çalıştırırken örtük geri yükleme devre dışı bırakmak istiyorsanız, geçirebilirsiniz `--no-restore` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="af92c-124">If you want to disable implicit restore when running the build command, you can pass the `--no-restore` option.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

<span data-ttu-id="af92c-125">`dotnet build` MSBuild Projesi derlemek için kullanır; Bu nedenle, paralel ve artımlı derlemelerini destekler.</span><span class="sxs-lookup"><span data-stu-id="af92c-125">`dotnet build` uses MSBuild to build the project; thus, it supports both parallel and incremental builds.</span></span> <span data-ttu-id="af92c-126">Başvurmak [artımlı derlemeler](/visualstudio/msbuild/incremental-builds) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="af92c-126">Refer to [Incremental Builds](/visualstudio/msbuild/incremental-builds) for more information.</span></span>

<span data-ttu-id="af92c-127">Kendi seçenekleri yanı sıra `dotnet build` komutu kabul MSBuild seçenekleri gibi `/p` özelliklerini ayarlamak için veya `/l` Günlükçü tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="af92c-127">In addition to its options, the `dotnet build` command accepts MSBuild options, such as `/p` for setting properties or `/l` to define a logger.</span></span> <span data-ttu-id="af92c-128">Bu seçenekler hakkında daha fazla bilgi [MSBuild komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="af92c-128">Learn more about these options in the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> 

<span data-ttu-id="af92c-129">Proje yürütülebilir olup olmamasına göre belirlenir. `<OutputType>` proje dosyası bir özellik.</span><span class="sxs-lookup"><span data-stu-id="af92c-129">Whether the project is executable or not is determined by the `<OutputType>` property in the project file.</span></span> <span data-ttu-id="af92c-130">Aşağıdaki örnek, yürütülebilir kod oluşturacak olan bir projeyi gösterir:</span><span class="sxs-lookup"><span data-stu-id="af92c-130">The following example shows a project that will produce executable code:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="af92c-131">Bir kitaplık üretmek için atlayın `<OutputType>` özelliği.</span><span class="sxs-lookup"><span data-stu-id="af92c-131">In order to produce a library, omit the `<OutputType>` property.</span></span> <span data-ttu-id="af92c-132">Ana yerleşik çıktıda bir kitaplık için IL DLL giriş noktaları içermiyor ve yürütülemez farktır.</span><span class="sxs-lookup"><span data-stu-id="af92c-132">The main difference in built output is that the IL DLL for a library doesn't contain entry points and can't be executed.</span></span> 

## <a name="arguments"></a><span data-ttu-id="af92c-133">Arguments</span><span class="sxs-lookup"><span data-stu-id="af92c-133">Arguments</span></span>

`PROJECT`

<span data-ttu-id="af92c-134">Derleme projesi dosyası.</span><span class="sxs-lookup"><span data-stu-id="af92c-134">The project file to build.</span></span> <span data-ttu-id="af92c-135">MSBuild proje dosyası belirtilmezse, geçerli çalışma dizini ile biten bir dosya uzantısına sahip bir dosya için arar *proj* ve bu dosyayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="af92c-135">If a project file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="af92c-136">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="af92c-136">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="af92c-137">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="af92c-137">.NET Core 2.x</span></span>](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="af92c-138">Derleme yapılandırması tanımlar.</span><span class="sxs-lookup"><span data-stu-id="af92c-138">Defines the build configuration.</span></span> <span data-ttu-id="af92c-139">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="af92c-139">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="af92c-140">Özel bir derler [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="af92c-140">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="af92c-141">Framework tanımlanmalıdır [proje dosyası](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="af92c-141">The framework must be defined in the [project file](csproj.md).</span></span>

`--force`

 <span data-ttu-id="af92c-142">Son geri yükleme başarılı olsa bile çözümlenmesi için tüm bağımlılıkları zorlar.</span><span class="sxs-lookup"><span data-stu-id="af92c-142">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="af92c-143">Bu silme ile eşdeğerdir *project.assets.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="af92c-143">This is equivalent to deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="af92c-144">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="af92c-144">Prints out a short help for the command.</span></span>

`--no-dependencies`

<span data-ttu-id="af92c-145">Proje Proje (P2P) başvuruları yoksayar ve yalnızca oluşturmak için belirtilen kök proje oluşturur.</span><span class="sxs-lookup"><span data-stu-id="af92c-145">Ignores project-to-project (P2P) references and only builds the root project specified to build.</span></span>

`--no-incremental`

<span data-ttu-id="af92c-146">Yapı Artımlı derleme için güvensiz olarak işaretler.</span><span class="sxs-lookup"><span data-stu-id="af92c-146">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="af92c-147">Bu Artımlı derlemeyi devre dışı bırakır ve temiz bir yeniden oluşturma, projenin bağımlılık grafiğinin zorlar.</span><span class="sxs-lookup"><span data-stu-id="af92c-147">This turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

`--no-restore`

<span data-ttu-id="af92c-148">Derleme sırasında örtük bir geri yükleme gerçekleştirmez.</span><span class="sxs-lookup"><span data-stu-id="af92c-148">Doesn't perform an implicit restore during build.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="af92c-149">Dizin oluşturulmuş ikili dosyalarının yerleştirileceği.</span><span class="sxs-lookup"><span data-stu-id="af92c-149">Directory in which to place the built binaries.</span></span> <span data-ttu-id="af92c-150">Tanımlamanız gereken `--framework` bu seçeneği belirlediğinizde.</span><span class="sxs-lookup"><span data-stu-id="af92c-150">You also need to define `--framework` when you specify this option.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="af92c-151">Hedef çalışma zamanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="af92c-151">Specifies the target runtime.</span></span> <span data-ttu-id="af92c-152">Çalışma zamanı tanımlayıcıları (RID) bir listesi için bkz: [RID katalog](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="af92c-152">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="af92c-153">Komutun ayrıntı düzeyi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="af92c-153">Sets the verbosity level of the command.</span></span> <span data-ttu-id="af92c-154">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="af92c-154">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="af92c-155">Sürüm soneki için bir yıldız işareti tanımlar (`*`) proje dosyasının sürüm alanında.</span><span class="sxs-lookup"><span data-stu-id="af92c-155">Defines the version suffix for an asterisk (`*`) in the version field of the project file.</span></span> <span data-ttu-id="af92c-156">NuGet sürümü yönergeleri biçimdedir.</span><span class="sxs-lookup"><span data-stu-id="af92c-156">The format follows NuGet's version guidelines.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="af92c-157">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="af92c-157">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="af92c-158">Derleme yapılandırması tanımlar.</span><span class="sxs-lookup"><span data-stu-id="af92c-158">Defines the build configuration.</span></span> <span data-ttu-id="af92c-159">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="af92c-159">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="af92c-160">Özel bir derler [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="af92c-160">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="af92c-161">Framework tanımlanmalıdır [proje dosyası](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="af92c-161">The framework must be defined in the [project file](csproj.md).</span></span>

`-h|--help`

<span data-ttu-id="af92c-162">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="af92c-162">Prints out a short help for the command.</span></span>

`--no-dependencies`

<span data-ttu-id="af92c-163">Proje Proje (P2P) başvuruları yoksayar ve yalnızca oluşturmak için belirtilen kök proje oluşturur.</span><span class="sxs-lookup"><span data-stu-id="af92c-163">Ignores project-to-project (P2P) references and only builds the root project specified to build.</span></span>

`--no-incremental`

<span data-ttu-id="af92c-164">Yapı Artımlı derleme için güvensiz olarak işaretler.</span><span class="sxs-lookup"><span data-stu-id="af92c-164">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="af92c-165">Bu Artımlı derlemeyi devre dışı bırakır ve temiz bir yeniden oluşturma, projenin bağımlılık grafiğinin zorlar.</span><span class="sxs-lookup"><span data-stu-id="af92c-165">This turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="af92c-166">Dizin oluşturulmuş ikili dosyalarının yerleştirileceği.</span><span class="sxs-lookup"><span data-stu-id="af92c-166">Directory in which to place the built binaries.</span></span> <span data-ttu-id="af92c-167">Tanımlamanız gereken `--framework` bu seçeneği belirlediğinizde.</span><span class="sxs-lookup"><span data-stu-id="af92c-167">You also need to define `--framework` when you specify this option.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="af92c-168">Hedef çalışma zamanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="af92c-168">Specifies the target runtime.</span></span> <span data-ttu-id="af92c-169">Çalışma zamanı tanımlayıcıları (RID) bir listesi için bkz: [RID katalog](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="af92c-169">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="af92c-170">Komutun ayrıntı düzeyi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="af92c-170">Sets the verbosity level of the command.</span></span> <span data-ttu-id="af92c-171">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="af92c-171">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="af92c-172">Sürüm soneki için bir yıldız işareti tanımlar (`*`) proje dosyasının sürüm alanında.</span><span class="sxs-lookup"><span data-stu-id="af92c-172">Defines the version suffix for an asterisk (`*`) in the version field of the project file.</span></span> <span data-ttu-id="af92c-173">NuGet sürümü yönergeleri biçimdedir.</span><span class="sxs-lookup"><span data-stu-id="af92c-173">The format follows NuGet's version guidelines.</span></span>

---

## <a name="examples"></a><span data-ttu-id="af92c-174">Örnekler</span><span class="sxs-lookup"><span data-stu-id="af92c-174">Examples</span></span>

<span data-ttu-id="af92c-175">Proje ve bağımlılıklarını oluşturun:</span><span class="sxs-lookup"><span data-stu-id="af92c-175">Build a project and its dependencies:</span></span>

`dotnet build`

<span data-ttu-id="af92c-176">Proje ve bağımlılıklarını yayın Yapılandırması'nı kullanarak oluşturun:</span><span class="sxs-lookup"><span data-stu-id="af92c-176">Build a project and its dependencies using Release configuration:</span></span>

`dotnet build --configuration Release`

<span data-ttu-id="af92c-177">Proje ve bağımlılıklarını belirli bir çalışma zamanı (Bu örnekte, Ubuntu 16.04) için yapı:</span><span class="sxs-lookup"><span data-stu-id="af92c-177">Build a project and its dependencies for a specific runtime (in this example, Ubuntu 16.04):</span></span>

`dotnet build --runtime ubuntu.16.04-x64`

<span data-ttu-id="af92c-178">Projeyi derlemek ve geri yükleme işlemi sırasında (.NET Core SDK 2.0 ve sonraki sürümler) belirtilen NuGet paket kaynağı kullanın:</span><span class="sxs-lookup"><span data-stu-id="af92c-178">Build the project and use the specified NuGet package source during the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet build --source c:\packages\mypackages`