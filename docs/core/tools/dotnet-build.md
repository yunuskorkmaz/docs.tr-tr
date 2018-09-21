---
title: DotNet - command .NET Core CLI oluşturun
description: Dotnet bir projeyi ve tüm bağımlılıklarını komut derlemeleri oluşturun.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: da33647e583af8441218f64fb8ac76d5de3cee38
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46537572"
---
# <a name="dotnet-build"></a><span data-ttu-id="a660c-103">DotNet derleme</span><span class="sxs-lookup"><span data-stu-id="a660c-103">dotnet build</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="a660c-104">Ad</span><span class="sxs-lookup"><span data-stu-id="a660c-104">Name</span></span>

<span data-ttu-id="a660c-105">`dotnet build` -Bir proje ve tüm bağımlılıklarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a660c-105">`dotnet build` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a660c-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="a660c-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="a660c-107">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="a660c-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet build [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--no-dependencies] [--no-incremental]
    [--no-restore] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]
dotnet build [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="a660c-108">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="a660c-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet build [<PROJECT>] [-c|--configuration] [-f|--framework] [--no-dependencies] [--no-incremental] [-o|--output]
    [-r|--runtime] [-v|--verbosity] [--version-suffix]
dotnet build [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="a660c-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a660c-109">Description</span></span>

<span data-ttu-id="a660c-110">`dotnet build` Komut projesi ve bağımlılıklarını ikili dosyaları kümesine oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a660c-110">The `dotnet build` command builds the project and its dependencies into a set of binaries.</span></span> <span data-ttu-id="a660c-111">Proje kodunuzun Ara dil (IL) dosyaları ile ikili dosyaları dahil bir *.dll* ile hata ayıklama için kullanılan uzantı ve sembol dosyalarını bir *.pdb* uzantısı.</span><span class="sxs-lookup"><span data-stu-id="a660c-111">The binaries include the project's code in Intermediate Language (IL) files with a *.dll* extension and symbol files used for debugging with a *.pdb* extension.</span></span> <span data-ttu-id="a660c-112">Bağımlılıkları JSON dosyası (*\*. deps.json*) üretilir, uygulama ile ilgili bağımlılıklar listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="a660c-112">A dependencies JSON file (*\*.deps.json*) is produced that lists the dependencies of the application.</span></span> <span data-ttu-id="a660c-113">A  *\*. runtimeconfig.json* dosyası oluşturulur, paylaşılan çalışma zamanı ve uygulamanın sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="a660c-113">A *\*.runtimeconfig.json* file is produced, which specifies the shared runtime and its version for the application.</span></span>

<span data-ttu-id="a660c-114">Proje, NuGet kitaplıklarından gibi üçüncü taraf bağımlılıkları varsa, NuGet önbellekten çözümlenen ve projenin çıkışı ile kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a660c-114">If the project has third-party dependencies, such as libraries from NuGet, they're resolved from the NuGet cache and aren't available with the project's built output.</span></span> <span data-ttu-id="a660c-115">Unutmayın, ürün, ile `dotnet build` çalıştırmak için başka bir makineye aktarılmak hazır değil.</span><span class="sxs-lookup"><span data-stu-id="a660c-115">With that in mind, the product of `dotnet build` isn't ready to be transferred to another machine to run.</span></span> <span data-ttu-id="a660c-116">Bu .NET Framework'ün aksine hangi binada bir yürütülebilir proje (uygulama), herhangi bir makinede çalıştırılabilir bir çıktı üretir. .NET Framework yüklendiği davranışıdır.</span><span class="sxs-lookup"><span data-stu-id="a660c-116">This is in contrast to the behavior of the .NET Framework in which building an executable project (an application) produces output that's runnable on any machine where the .NET Framework is installed.</span></span> <span data-ttu-id="a660c-117">.NET Core ile benzer bir deneyim sağlamak için kullanmanız gerekir [dotnet yayımlama](dotnet-publish.md) komutu.</span><span class="sxs-lookup"><span data-stu-id="a660c-117">To have a similar experience with .NET Core, you need to use the [dotnet publish](dotnet-publish.md) command.</span></span> <span data-ttu-id="a660c-118">Daha fazla bilgi için [.NET Core uygulaması dağıtımını](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="a660c-118">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span>

<span data-ttu-id="a660c-119">Yapı gerektirir *project.assets.json* dosyasını uygulamanızın bağımlılıklar listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="a660c-119">Building requires the *project.assets.json* file, which lists the dependencies of your application.</span></span> <span data-ttu-id="a660c-120">Bir dosya oluşturulur [ `dotnet restore` ](dotnet-restore.md) yürütülür.</span><span class="sxs-lookup"><span data-stu-id="a660c-120">The file is created when [`dotnet restore`](dotnet-restore.md) is executed.</span></span> <span data-ttu-id="a660c-121">Varlıklar dosyayı yerinde araç hataları sonuçlanır başvuru derlemelerini çözümlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="a660c-121">Without the assets file in place, the tooling cannot resolve reference assemblies, which results in errors.</span></span> <span data-ttu-id="a660c-122">.NET Core 1.x SDK'sı, gerekli açıkça çalıştırılacak `dotnet restore` çalıştırmadan önce `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="a660c-122">With .NET Core 1.x SDK, you needed to explicitly run the `dotnet restore` before running `dotnet build`.</span></span> <span data-ttu-id="a660c-123">.NET Core 2.0 SDK ile başlayarak `dotnet restore` çalıştırdığınızda örtülü olarak çalışan `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="a660c-123">Starting with .NET Core 2.0 SDK, `dotnet restore` runs implicitly when you run `dotnet build`.</span></span> <span data-ttu-id="a660c-124">Oluşturma komutu çalıştırırken örtük geri yükleme devre dışı bırakmak isterseniz, geçirebilirsiniz `--no-restore` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="a660c-124">If you want to disable implicit restore when running the build command, you can pass the `--no-restore` option.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

<span data-ttu-id="a660c-125">`dotnet build` Projeyi derlemek için MSBuild kullanır, hem paralel hem de artımlı destekler şekilde oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a660c-125">`dotnet build` uses MSBuild to build the project, so it supports both parallel and incremental builds.</span></span> <span data-ttu-id="a660c-126">Daha fazla bilgi için [artımlı derlemeler](/visualstudio/msbuild/incremental-builds).</span><span class="sxs-lookup"><span data-stu-id="a660c-126">For more information, see [Incremental Builds](/visualstudio/msbuild/incremental-builds).</span></span>

<span data-ttu-id="a660c-127">Kendi seçenekleri yanı sıra `dotnet build` komutu kabul MSBUILD seçenekleri gibi `-p` özelliklerini ayarlamak için veya `-l` bir Günlükçü tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="a660c-127">In addition to its options, the `dotnet build` command accepts MSBuild options, such as `-p` for setting properties or `-l` to define a logger.</span></span> <span data-ttu-id="a660c-128">Bu seçenekler hakkında daha fazla bilgi için bkz. [MSBuild komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="a660c-128">For more information about these options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

<span data-ttu-id="a660c-129">Projenin yürütülebilir olup olmamasına göre belirlenen `<OutputType>` proje dosyasındaki özellik.</span><span class="sxs-lookup"><span data-stu-id="a660c-129">Whether the project is executable or not is determined by the `<OutputType>` property in the project file.</span></span> <span data-ttu-id="a660c-130">Aşağıdaki örnek, yürütülebilir kod üreten bir proje gösterir:</span><span class="sxs-lookup"><span data-stu-id="a660c-130">The following example shows a project that produces executable code:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="a660c-131">Bir kitaplığı üretmek için atla `<OutputType>` özelliği.</span><span class="sxs-lookup"><span data-stu-id="a660c-131">In order to produce a library, omit the `<OutputType>` property.</span></span> <span data-ttu-id="a660c-132">Çıkışı ana fark, bir kitaplık için IL DLL giriş noktalarını içermiyor ve yürütülemez ' dir.</span><span class="sxs-lookup"><span data-stu-id="a660c-132">The main difference in built output is that the IL DLL for a library doesn't contain entry points and can't be executed.</span></span>

## <a name="arguments"></a><span data-ttu-id="a660c-133">Arguments</span><span class="sxs-lookup"><span data-stu-id="a660c-133">Arguments</span></span>

`PROJECT`

<span data-ttu-id="a660c-134">Derleme için proje dosyası.</span><span class="sxs-lookup"><span data-stu-id="a660c-134">The project file to build.</span></span> <span data-ttu-id="a660c-135">Bir proje dosyası belirtilmezse, MSBuild ile biten bir dosya uzantısına sahip bir dosya için geçerli çalışma dizini arar *proj* ve bu dosyayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="a660c-135">If a project file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="a660c-136">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="a660c-136">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="a660c-137">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="a660c-137">.NET Core 2.x</span></span>](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="a660c-138">Derleme yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a660c-138">Defines the build configuration.</span></span> <span data-ttu-id="a660c-139">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="a660c-139">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="a660c-140">Özel bir derleme [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="a660c-140">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="a660c-141">Framework tanımlanmalıdır [proje dosyası](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="a660c-141">The framework must be defined in the [project file](csproj.md).</span></span>

`--force`

<span data-ttu-id="a660c-142">Son geri yükleme başarılı olduysa bile çözülmesi için tüm bağımlılıkların zorlar.</span><span class="sxs-lookup"><span data-stu-id="a660c-142">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="a660c-143">Bu bayrak belirten aynıdır silme *project.assets.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="a660c-143">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="a660c-144">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="a660c-144">Prints out a short help for the command.</span></span>

`--no-dependencies`

<span data-ttu-id="a660c-145">Projeden projeye (P2P) başvurularını yoksayar ve yalnızca belirtilen kök projeyi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a660c-145">Ignores project-to-project (P2P) references and only builds the specified root project.</span></span>

`--no-incremental`

<span data-ttu-id="a660c-146">Derleme Artımlı derleme için güvensiz olarak işaretler.</span><span class="sxs-lookup"><span data-stu-id="a660c-146">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="a660c-147">Bu bayrak, Artımlı derlemeyi devre dışı bırakır ve temiz bir projenin bağımlılık grafiği yeniden zorlar.</span><span class="sxs-lookup"><span data-stu-id="a660c-147">This flag turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

`--no-restore`

<span data-ttu-id="a660c-148">Örtük bir geri yükleme derleme sırasında yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="a660c-148">Doesn't execute an implicit restore during build.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="a660c-149">Yerleşik ikili dosyaların yerleştirileceği dizin.</span><span class="sxs-lookup"><span data-stu-id="a660c-149">Directory in which to place the built binaries.</span></span> <span data-ttu-id="a660c-150">Tanımlamanız gereken `--framework` bu seçeneği belirttiğinizde.</span><span class="sxs-lookup"><span data-stu-id="a660c-150">You also need to define `--framework` when you specify this option.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="a660c-151">Hedef çalışma zamanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="a660c-151">Specifies the target runtime.</span></span> <span data-ttu-id="a660c-152">Çalışma zamanı tanımlayıcılarının (RID'ler) bir listesi için bkz. [RID Kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="a660c-152">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="a660c-153">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a660c-153">Sets the verbosity level of the command.</span></span> <span data-ttu-id="a660c-154">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="a660c-154">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="a660c-155">Sürüm soneki için bir yıldız işareti tanımlar (`*`) proje dosyasının sürümü alanında.</span><span class="sxs-lookup"><span data-stu-id="a660c-155">Defines the version suffix for an asterisk (`*`) in the version field of the project file.</span></span> <span data-ttu-id="a660c-156">NuGet'ın sürümü yönergeleri biçimdedir.</span><span class="sxs-lookup"><span data-stu-id="a660c-156">The format follows NuGet's version guidelines.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="a660c-157">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="a660c-157">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="a660c-158">Derleme yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a660c-158">Defines the build configuration.</span></span> <span data-ttu-id="a660c-159">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="a660c-159">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="a660c-160">Özel bir derleme [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="a660c-160">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="a660c-161">Framework tanımlanmalıdır [proje dosyası](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="a660c-161">The framework must be defined in the [project file](csproj.md).</span></span>

`-h|--help`

<span data-ttu-id="a660c-162">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="a660c-162">Prints out a short help for the command.</span></span>

`--no-dependencies`

<span data-ttu-id="a660c-163">Projeden projeye (P2P) başvurularını yoksayar ve yalnızca belirtilen kök projeyi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a660c-163">Ignores project-to-project (P2P) references and only builds the specified root project.</span></span>

`--no-incremental`

<span data-ttu-id="a660c-164">Derleme Artımlı derleme için güvensiz olarak işaretler.</span><span class="sxs-lookup"><span data-stu-id="a660c-164">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="a660c-165">Bu bayrak, Artımlı derlemeyi devre dışı bırakır ve temiz bir projenin bağımlılık grafiği yeniden zorlar.</span><span class="sxs-lookup"><span data-stu-id="a660c-165">This flag turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="a660c-166">Yerleşik ikili dosyaların yerleştirileceği dizin.</span><span class="sxs-lookup"><span data-stu-id="a660c-166">Directory in which to place the built binaries.</span></span> <span data-ttu-id="a660c-167">Tanımlamanız gereken `--framework` bu seçeneği belirttiğinizde.</span><span class="sxs-lookup"><span data-stu-id="a660c-167">You also need to define `--framework` when you specify this option.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="a660c-168">Hedef çalışma zamanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="a660c-168">Specifies the target runtime.</span></span> <span data-ttu-id="a660c-169">Çalışma zamanı tanımlayıcılarının (RID'ler) bir listesi için bkz. [RID Kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="a660c-169">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="a660c-170">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a660c-170">Sets the verbosity level of the command.</span></span> <span data-ttu-id="a660c-171">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="a660c-171">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="a660c-172">Sürüm soneki için bir yıldız işareti tanımlar (`*`) proje dosyasının sürümü alanında.</span><span class="sxs-lookup"><span data-stu-id="a660c-172">Defines the version suffix for an asterisk (`*`) in the version field of the project file.</span></span> <span data-ttu-id="a660c-173">NuGet'ın sürümü yönergeleri biçimdedir.</span><span class="sxs-lookup"><span data-stu-id="a660c-173">The format follows NuGet's version guidelines.</span></span>

---

## <a name="examples"></a><span data-ttu-id="a660c-174">Örnekler</span><span class="sxs-lookup"><span data-stu-id="a660c-174">Examples</span></span>

<span data-ttu-id="a660c-175">Bir proje ve bağımlılıkları derleme:</span><span class="sxs-lookup"><span data-stu-id="a660c-175">Build a project and its dependencies:</span></span>

`dotnet build`

<span data-ttu-id="a660c-176">Bir proje ve bağımlılıkları sürüm yapılandırmasını oluşturun:</span><span class="sxs-lookup"><span data-stu-id="a660c-176">Build a project and its dependencies using Release configuration:</span></span>

`dotnet build --configuration Release`

<span data-ttu-id="a660c-177">Bir proje ve bağımlılıkları (Bu örnekte, Ubuntu 16.04) belirli bir çalışma zamanı için derleme:</span><span class="sxs-lookup"><span data-stu-id="a660c-177">Build a project and its dependencies for a specific runtime (in this example, Ubuntu 16.04):</span></span>

`dotnet build --runtime ubuntu.16.04-x64`

<span data-ttu-id="a660c-178">Projeyi oluşturmak ve geri yükleme işlemi sırasında (.NET Core SDK 2.0 ve sonraki sürümler) belirtilen NuGet paket kaynağı kullanın:</span><span class="sxs-lookup"><span data-stu-id="a660c-178">Build the project and use the specified NuGet package source during the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet build --source c:\packages\mypackages`