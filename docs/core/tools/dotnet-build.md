---
title: DotNet derleme komutu
description: DotNet derleme komutu bir projeyi ve tüm bağımlılıklarını oluşturur.
ms.date: 10/14/2019
ms.openlocfilehash: ec37d82c9e22a59acf7617f80a7491c0bcab89c9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734319"
---
# <a name="dotnet-build"></a><span data-ttu-id="5fa0a-103">dotnet build</span><span class="sxs-lookup"><span data-stu-id="5fa0a-103">dotnet build</span></span>

<span data-ttu-id="5fa0a-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 1. x SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="5fa0a-104">**This article applies to:** ✔️ .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="5fa0a-105">Ad</span><span class="sxs-lookup"><span data-stu-id="5fa0a-105">Name</span></span>

<span data-ttu-id="5fa0a-106">`dotnet build`-bir projeyi ve tüm bağımlılıklarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-106">`dotnet build` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5fa0a-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="5fa0a-107">Synopsis</span></span>

```dotnetcli
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--force]
    [--interactive] [--no-dependencies] [--no-incremental] [--no-restore] [--nologo]
    [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```

## <a name="description"></a><span data-ttu-id="5fa0a-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5fa0a-108">Description</span></span>

<span data-ttu-id="5fa0a-109">`dotnet build` komutu projeyi ve onun bağımlılıklarını bir ikili dosya kümesine oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-109">The `dotnet build` command builds the project and its dependencies into a set of binaries.</span></span> <span data-ttu-id="5fa0a-110">İkili dosyalar, projenin kodunu *. dll* uzantılı ara DIL (IL) dosyalarına dahil eder.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-110">The binaries include the project's code in Intermediate Language (IL) files with a *.dll* extension.</span></span>  <span data-ttu-id="5fa0a-111">Proje türü ve ayarlarına bağlı olarak, şu gibi diğer dosyalar dahil edilebilir:</span><span class="sxs-lookup"><span data-stu-id="5fa0a-111">Depending on the project type and settings, other files may be included, such as:</span></span>

- <span data-ttu-id="5fa0a-112">Proje türü, .NET Core 3,0 veya üstünü hedefleyen bir yürütülebilir dosya ise, uygulamayı çalıştırmak için kullanılabilecek bir çalıştırılabilir dosya.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-112">An executable that can be used to run the application, if the project type is an executable targeting .NET Core 3.0 or later.</span></span>
- <span data-ttu-id="5fa0a-113">Bir *. pdb* uzantısıyla hata ayıklama için kullanılan sembol dosyaları.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-113">Symbol files used for debugging with a *.pdb* extension.</span></span>
- <span data-ttu-id="5fa0a-114">Uygulamanın veya kitaplığın bağımlılıklarını listeleyen *. Deps. JSON* dosyası.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-114">A *.deps.json* file, which lists the dependencies of the application or library.</span></span>
- <span data-ttu-id="5fa0a-115">Paylaşılan çalışma zamanını ve bir uygulamanın sürümünü belirten *. runtimeconfig. JSON* dosyası.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-115">A *.runtimeconfig.json* file, which specifies the shared runtime and its version for an application.</span></span>
- <span data-ttu-id="5fa0a-116">Projenin bağımlı olduğu diğer kitaplıklar (proje başvuruları veya NuGet paket başvuruları aracılığıyla).</span><span class="sxs-lookup"><span data-stu-id="5fa0a-116">Other libraries that the project depends on (via project references or NuGet package references).</span></span>

<span data-ttu-id="5fa0a-117">.NET Core 3,0 ' den önceki sürümleri hedefleyen yürütülebilir projeler için, NuGet 'deki kitaplık bağımlılıkları genellikle çıkış klasörüne kopyalanmaz.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-117">For executable projects targeting versions earlier than .NET Core 3.0, library dependencies from NuGet are typically NOT copied to the output folder.</span></span>  <span data-ttu-id="5fa0a-118">Bunlar, çalışma zamanında NuGet genel paketler klasöründen çözümlenirler.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-118">They're resolved from the NuGet global packages folder at run time.</span></span> <span data-ttu-id="5fa0a-119">Bu şekilde `dotnet build` ürünü, çalıştırmak için başka bir makineye aktarılmaya hazırlanmıyor.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-119">With that in mind, the product of `dotnet build` isn't ready to be transferred to another machine to run.</span></span> <span data-ttu-id="5fa0a-120">Uygulamasının dağıtılabilecek bir sürümünü oluşturmak için (örneğin, [DotNet Publish](dotnet-publish.md) komutuyla) yayımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-120">To create a version of the application that can be deployed, you need to publish it (for example, with the [dotnet publish](dotnet-publish.md) command).</span></span> <span data-ttu-id="5fa0a-121">Daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="5fa0a-121">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span>

<span data-ttu-id="5fa0a-122">.NET Core 3,0 ve üstünü hedefleyen yürütülebilir projelerde, kitaplık bağımlılıkları çıkış klasörüne kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-122">For executable projects targeting .NET Core 3.0 and later, library dependencies are copied to the output folder.</span></span> <span data-ttu-id="5fa0a-123">Bu, başka bir yayınla özel mantık (örneğin, Web projeleri) yoksa, yapı çıkışının dağıtılabilir olması anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-123">This means that if there isn't any other publish-specific logic (such as Web projects have), the build output should be deployable.</span></span>

<span data-ttu-id="5fa0a-124">Oluşturma, uygulamanızın bağımlılıklarını listeleyen *Project. varlıklar. JSON* dosyasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-124">Building requires the *project.assets.json* file, which lists the dependencies of your application.</span></span> <span data-ttu-id="5fa0a-125">[`dotnet restore`](dotnet-restore.md) yürütüldüğünde dosya oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-125">The file is created when [`dotnet restore`](dotnet-restore.md) is executed.</span></span> <span data-ttu-id="5fa0a-126">Varlıklar dosyası olmadan, Araçlar başvuru derlemelerini çözemez, bu da hatalara neden olur.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-126">Without the assets file in place, the tooling can't resolve reference assemblies, which results in errors.</span></span> <span data-ttu-id="5fa0a-127">.NET Core 1. x SDK ile `dotnet build`çalıştırmadan önce `dotnet restore` açık olarak çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-127">With .NET Core 1.x SDK, you needed to explicitly run `dotnet restore` before running `dotnet build`.</span></span> <span data-ttu-id="5fa0a-128">.NET Core 2,0 SDK ile başlayarak, `dotnet build`çalıştırdığınızda `dotnet restore` örtülü olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-128">Starting with .NET Core 2.0 SDK, `dotnet restore` runs implicitly when you run `dotnet build`.</span></span> <span data-ttu-id="5fa0a-129">Build komutunu çalıştırırken örtük geri yüklemeyi devre dışı bırakmak istiyorsanız `--no-restore` seçeneğini geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-129">If you want to disable implicit restore when running the build command, you can pass the `--no-restore` option.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

<span data-ttu-id="5fa0a-130">Projenin yürütülebilir olup olmadığı veya proje dosyasındaki `<OutputType>` özelliği tarafından belirlenmediği.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-130">Whether the project is executable or not is determined by the `<OutputType>` property in the project file.</span></span> <span data-ttu-id="5fa0a-131">Aşağıdaki örnekte yürütülebilir kod üreten bir proje gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="5fa0a-131">The following example shows a project that produces executable code:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="5fa0a-132">Bir kitaplık oluşturmak için `<OutputType>` özelliğini atlayın veya değerini `Library`olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-132">To produce a library, omit the `<OutputType>` property or change its value to `Library`.</span></span> <span data-ttu-id="5fa0a-133">Bir kitaplığın Il DLL 'SI giriş noktaları içermiyor ve yürütülemiyor.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-133">The IL DLL for a library doesn't contain entry points and can't be executed.</span></span>

### <a name="msbuild"></a><span data-ttu-id="5fa0a-134">MSBuild</span><span class="sxs-lookup"><span data-stu-id="5fa0a-134">MSBuild</span></span>

<span data-ttu-id="5fa0a-135">`dotnet build`, projeyi derlemek için MSBuild kullanır, bu nedenle hem paralel hem de artımlı yapıları destekler.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-135">`dotnet build` uses MSBuild to build the project, so it supports both parallel and incremental builds.</span></span> <span data-ttu-id="5fa0a-136">Daha fazla bilgi için bkz. [Artımlı derlemeler](/visualstudio/msbuild/incremental-builds).</span><span class="sxs-lookup"><span data-stu-id="5fa0a-136">For more information, see [Incremental Builds](/visualstudio/msbuild/incremental-builds).</span></span>

<span data-ttu-id="5fa0a-137">`dotnet build` komutu, seçeneklerine ek olarak, özellikleri ayarlamak için `-p` veya bir günlükçü tanımlamak için `-l` gibi MSBuild seçeneklerini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-137">In addition to its options, the `dotnet build` command accepts MSBuild options, such as `-p` for setting properties or `-l` to define a logger.</span></span> <span data-ttu-id="5fa0a-138">Bu seçenekler hakkında daha fazla bilgi için bkz. [MSBuild komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="5fa0a-138">For more information about these options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="5fa0a-139">Ayrıca [DotNet MSBuild](dotnet-msbuild.md) komutunu da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-139">Or you can also use the [dotnet msbuild](dotnet-msbuild.md) command.</span></span>

<span data-ttu-id="5fa0a-140">Çalışan `dotnet build`, çalışan `dotnet msbuild -restore`eşdeğerdir; Ancak, çıktının varsayılan ayrıntı düzeyi farklıdır.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-140">Running `dotnet build` is equivalent to running `dotnet msbuild -restore`; however, the default verbosity of the output is different.</span></span>

## <a name="arguments"></a><span data-ttu-id="5fa0a-141">Arguments</span><span class="sxs-lookup"><span data-stu-id="5fa0a-141">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="5fa0a-142">Derlenecek proje veya çözüm dosyası.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-142">The project or solution file to build.</span></span> <span data-ttu-id="5fa0a-143">Bir proje veya çözüm dosyası belirtilmemişse, MSBuild, *proj* veya *sln* 'de biten bir dosya uzantısına sahip bir dosya için geçerli çalışma dizinini arar ve bu dosyayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-143">If a project or solution file isn't specified, MSBuild searches the current working directory for a file that has a file extension that ends in either *proj* or *sln* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="5fa0a-144">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="5fa0a-144">Options</span></span>

- **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="5fa0a-145">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-145">Defines the build configuration.</span></span> <span data-ttu-id="5fa0a-146">Çoğu proje için varsayılan değer `Debug`, ancak projenizde derleme yapılandırma ayarlarını geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-146">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="5fa0a-147">Belirli bir [çerçeve](../../standard/frameworks.md)için derlenir.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-147">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="5fa0a-148">Çerçeve [Proje dosyasında](csproj.md)tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-148">The framework must be defined in the [project file](csproj.md).</span></span>

- **`--force`**

  <span data-ttu-id="5fa0a-149">Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-149">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="5fa0a-150">Bu bayrağın belirtilmesi, *Project. varlıklar. JSON* dosyasını silme ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-150">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span> <span data-ttu-id="5fa0a-151">.NET Core 2,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-151">Available since .NET Core 2.0 SDK.</span></span>

- **`-h|--help`**

  <span data-ttu-id="5fa0a-152">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-152">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="5fa0a-153">Komutun Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-153">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="5fa0a-154">Örneğin, kimlik doğrulamasını tamamlamaya yönelik.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-154">For example, to complete authentication.</span></span> <span data-ttu-id="5fa0a-155">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-155">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="5fa0a-156">Projeden projeye (P2P) başvurularını yoksayar ve yalnızca belirtilen kök projeyi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-156">Ignores project-to-project (P2P) references and only builds the specified root project.</span></span>

- **`--no-incremental`**

  <span data-ttu-id="5fa0a-157">Derlemeyi Artımlı derleme için güvenli değil olarak işaretler.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-157">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="5fa0a-158">Bu bayrak, artımlı derlemeyi kapatır ve projenin bağımlılık grafiğinin temiz bir yeniden oluşturulmasına zorlar.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-158">This flag turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

- **`--no-restore`**

  <span data-ttu-id="5fa0a-159">Derleme sırasında örtük geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-159">Doesn't execute an implicit restore during build.</span></span> <span data-ttu-id="5fa0a-160">.NET Core 2,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-160">Available since .NET Core 2.0 SDK.</span></span>

- **`--nologo`**

  <span data-ttu-id="5fa0a-161">Başlangıç başlığını veya telif hakkı iletisini görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-161">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="5fa0a-162">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-162">Available since .NET Core 3.0 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="5fa0a-163">Oluşturulan ikililerin yerleştirileceği dizin.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-163">Directory in which to place the built binaries.</span></span> <span data-ttu-id="5fa0a-164">Belirtilmemişse, varsayılan yol `./bin/<configuration>/<framework>/`.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-164">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="5fa0a-165">Birden çok hedef çerçevesi olan projeler için (`TargetFrameworks` özelliği aracılığıyla), bu seçeneği belirttiğinizde de `--framework` tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-165">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="5fa0a-166">Hedef çalışma zamanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-166">Specifies the target runtime.</span></span> <span data-ttu-id="5fa0a-167">Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="5fa0a-167">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="5fa0a-168">MSBuild ayrıntı düzeyi düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-168">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="5fa0a-169">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-169">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="5fa0a-170">Varsayılan, `minimal` değeridir.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-170">The default is `minimal`.</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="5fa0a-171">Projeyi oluştururken kullanılacak `$(VersionSuffix)` özelliğinin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-171">Sets the value of the `$(VersionSuffix)` property to use when building the project.</span></span> <span data-ttu-id="5fa0a-172">Bu yalnızca `$(Version)` özelliği ayarlanmamışsa işe yarar.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-172">This only works if the `$(Version)` property isn't set.</span></span> <span data-ttu-id="5fa0a-173">Daha sonra, `$(Version)`, bir çizgiyle ayırarak `$(VersionSuffix)`ile Birleşik `$(VersionPrefix)` ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="5fa0a-173">Then, `$(Version)` is set to the `$(VersionPrefix)` combined with the `$(VersionSuffix)`, separated by a dash.</span></span>

## <a name="examples"></a><span data-ttu-id="5fa0a-174">Örnekler</span><span class="sxs-lookup"><span data-stu-id="5fa0a-174">Examples</span></span>

- <span data-ttu-id="5fa0a-175">Bir proje ve bağımlılıklarını oluşturun:</span><span class="sxs-lookup"><span data-stu-id="5fa0a-175">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet build
  ```

- <span data-ttu-id="5fa0a-176">Yayın yapılandırması kullanarak bir proje ve bağımlılıklarını oluşturun:</span><span class="sxs-lookup"><span data-stu-id="5fa0a-176">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet build --configuration Release
  ```

- <span data-ttu-id="5fa0a-177">Belirli bir çalışma zamanı için bir proje ve bağımlılıklarını oluşturun (Bu örnekte Ubuntu 18,04):</span><span class="sxs-lookup"><span data-stu-id="5fa0a-177">Build a project and its dependencies for a specific runtime (in this example, Ubuntu 18.04):</span></span>

  ```dotnetcli
  dotnet build --runtime ubuntu.18.04-x64
  ```

- <span data-ttu-id="5fa0a-178">Projeyi derleyin ve geri yükleme işlemi sırasında belirtilen NuGet paket kaynağını kullanın (.NET Core 2,0 SDK ve sonraki sürümleri):</span><span class="sxs-lookup"><span data-stu-id="5fa0a-178">Build the project and use the specified NuGet package source during the restore operation (.NET Core 2.0 SDK and later versions):</span></span>

  ```dotnetcli
  dotnet build --source c:\packages\mypackages
  ```

- <span data-ttu-id="5fa0a-179">`-p` [MSBuild seçeneğini](#msbuild)kullanarak projeyi derleyin ve derleme parametresi olarak 1.2.3.4 olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="5fa0a-179">Build the project and set version 1.2.3.4 as a build parameter using the `-p` [MSBuild option](#msbuild):</span></span>

  ```dotnetcli
  dotnet build -p:Version=1.2.3.4
  ```
