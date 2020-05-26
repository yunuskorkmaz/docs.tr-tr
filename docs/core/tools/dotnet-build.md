---
title: DotNet derleme komutu
description: DotNet derleme komutu bir projeyi ve tüm bağımlılıklarını oluşturur.
ms.date: 02/14/2020
ms.openlocfilehash: 5375df61dbf8e9b4db8772b0e2767e9bca0bb254
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83840916"
---
# <a name="dotnet-build"></a><span data-ttu-id="57d42-103">dotnet build</span><span class="sxs-lookup"><span data-stu-id="57d42-103">dotnet build</span></span>

<span data-ttu-id="57d42-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2. x SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="57d42-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="57d42-105">Name</span><span class="sxs-lookup"><span data-stu-id="57d42-105">Name</span></span>

<span data-ttu-id="57d42-106">`dotnet build`-Bir projeyi ve tüm bağımlılıklarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="57d42-106">`dotnet build` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="57d42-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="57d42-107">Synopsis</span></span>

```dotnetcli
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [-f|--framework <FRAMEWORK>] [--force] [--interactive] [--no-dependencies]
    [--no-incremental] [--no-restore] [--nologo] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [-s|--source <SOURCE>]
    [-v|--verbosity <LEVEL>] [--version-suffix <VERSION_SUFFIX>]

dotnet build -h|--help
```

## <a name="description"></a><span data-ttu-id="57d42-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57d42-108">Description</span></span>

<span data-ttu-id="57d42-109">`dotnet build`Komutu projeyi ve onun bağımlılıklarını bir ikili dosya kümesine oluşturur.</span><span class="sxs-lookup"><span data-stu-id="57d42-109">The `dotnet build` command builds the project and its dependencies into a set of binaries.</span></span> <span data-ttu-id="57d42-110">İkili dosyalar, projenin kodunu *. dll* uzantılı ara DIL (IL) dosyalarına dahil eder.</span><span class="sxs-lookup"><span data-stu-id="57d42-110">The binaries include the project's code in Intermediate Language (IL) files with a *.dll* extension.</span></span>  <span data-ttu-id="57d42-111">Proje türü ve ayarlarına bağlı olarak, şu gibi diğer dosyalar dahil edilebilir:</span><span class="sxs-lookup"><span data-stu-id="57d42-111">Depending on the project type and settings, other files may be included, such as:</span></span>

- <span data-ttu-id="57d42-112">Proje türü, .NET Core 3,0 veya üstünü hedefleyen bir yürütülebilir dosya ise, uygulamayı çalıştırmak için kullanılabilecek bir çalıştırılabilir dosya.</span><span class="sxs-lookup"><span data-stu-id="57d42-112">An executable that can be used to run the application, if the project type is an executable targeting .NET Core 3.0 or later.</span></span>
- <span data-ttu-id="57d42-113">Bir *. pdb* uzantısıyla hata ayıklama için kullanılan sembol dosyaları.</span><span class="sxs-lookup"><span data-stu-id="57d42-113">Symbol files used for debugging with a *.pdb* extension.</span></span>
- <span data-ttu-id="57d42-114">Uygulamanın veya kitaplığın bağımlılıklarını listeleyen *. Deps. JSON* dosyası.</span><span class="sxs-lookup"><span data-stu-id="57d42-114">A *.deps.json* file, which lists the dependencies of the application or library.</span></span>
- <span data-ttu-id="57d42-115">Paylaşılan çalışma zamanını ve bir uygulamanın sürümünü belirten *. runtimeconfig. JSON* dosyası.</span><span class="sxs-lookup"><span data-stu-id="57d42-115">A *.runtimeconfig.json* file, which specifies the shared runtime and its version for an application.</span></span>
- <span data-ttu-id="57d42-116">Projenin bağımlı olduğu diğer kitaplıklar (proje başvuruları veya NuGet paket başvuruları aracılığıyla).</span><span class="sxs-lookup"><span data-stu-id="57d42-116">Other libraries that the project depends on (via project references or NuGet package references).</span></span>

<span data-ttu-id="57d42-117">.NET Core 3,0 ' den önceki sürümleri hedefleyen yürütülebilir projeler için, NuGet 'deki kitaplık bağımlılıkları genellikle çıkış klasörüne kopyalanmaz.</span><span class="sxs-lookup"><span data-stu-id="57d42-117">For executable projects targeting versions earlier than .NET Core 3.0, library dependencies from NuGet are typically NOT copied to the output folder.</span></span>  <span data-ttu-id="57d42-118">Bunlar, çalışma zamanında NuGet genel paketler klasöründen çözümlenirler.</span><span class="sxs-lookup"><span data-stu-id="57d42-118">They're resolved from the NuGet global packages folder at run time.</span></span> <span data-ttu-id="57d42-119">Göz önünde bulundurularak, ürünü `dotnet build` çalıştırmak için başka bir makineye aktarılmaya hazırlanın.</span><span class="sxs-lookup"><span data-stu-id="57d42-119">With that in mind, the product of `dotnet build` isn't ready to be transferred to another machine to run.</span></span> <span data-ttu-id="57d42-120">Uygulamasının dağıtılabilecek bir sürümünü oluşturmak için (örneğin, [DotNet Publish](dotnet-publish.md) komutuyla) yayımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="57d42-120">To create a version of the application that can be deployed, you need to publish it (for example, with the [dotnet publish](dotnet-publish.md) command).</span></span> <span data-ttu-id="57d42-121">Daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="57d42-121">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span>

<span data-ttu-id="57d42-122">.NET Core 3,0 ve üstünü hedefleyen yürütülebilir projelerde, kitaplık bağımlılıkları çıkış klasörüne kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="57d42-122">For executable projects targeting .NET Core 3.0 and later, library dependencies are copied to the output folder.</span></span> <span data-ttu-id="57d42-123">Bu, başka bir yayınla özel mantık (örneğin, Web projeleri) yoksa, yapı çıkışının dağıtılabilir olması anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="57d42-123">This means that if there isn't any other publish-specific logic (such as Web projects have), the build output should be deployable.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="57d42-124">Örtük geri yükleme</span><span class="sxs-lookup"><span data-stu-id="57d42-124">Implicit restore</span></span>

<span data-ttu-id="57d42-125">Oluşturma, uygulamanızın bağımlılıklarını listeleyen *Project. varlıklar. JSON* dosyasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="57d42-125">Building requires the *project.assets.json* file, which lists the dependencies of your application.</span></span> <span data-ttu-id="57d42-126">Dosya [`dotnet restore`](dotnet-restore.md) yürütüldüğünde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="57d42-126">The file is created when [`dotnet restore`](dotnet-restore.md) is executed.</span></span> <span data-ttu-id="57d42-127">Varlıklar dosyası olmadan, Araçlar başvuru derlemelerini çözemez, bu da hatalara neden olur.</span><span class="sxs-lookup"><span data-stu-id="57d42-127">Without the assets file in place, the tooling can't resolve reference assemblies, which results in errors.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

### <a name="executable-or-library-output"></a><span data-ttu-id="57d42-128">Yürütülebilir veya kitaplık çıkışı</span><span class="sxs-lookup"><span data-stu-id="57d42-128">Executable or library output</span></span>

<span data-ttu-id="57d42-129">Projenin yürütülebilir olup olmadığı veya proje dosyasındaki özelliği tarafından belirlenmediği `<OutputType>` .</span><span class="sxs-lookup"><span data-stu-id="57d42-129">Whether the project is executable or not is determined by the `<OutputType>` property in the project file.</span></span> <span data-ttu-id="57d42-130">Aşağıdaki örnekte yürütülebilir kod üreten bir proje gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="57d42-130">The following example shows a project that produces executable code:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="57d42-131">Bir kitaplık oluşturmak için, özelliği atlayın `<OutputType>` veya değerini olarak değiştirin `Library` .</span><span class="sxs-lookup"><span data-stu-id="57d42-131">To produce a library, omit the `<OutputType>` property or change its value to `Library`.</span></span> <span data-ttu-id="57d42-132">Bir kitaplığın Il DLL 'SI giriş noktaları içermiyor ve yürütülemiyor.</span><span class="sxs-lookup"><span data-stu-id="57d42-132">The IL DLL for a library doesn't contain entry points and can't be executed.</span></span>

### <a name="msbuild"></a><span data-ttu-id="57d42-133">MSBuild</span><span class="sxs-lookup"><span data-stu-id="57d42-133">MSBuild</span></span>

<span data-ttu-id="57d42-134">`dotnet build`, projeyi derlemek için MSBuild kullanır, bu nedenle hem paralel hem de artımlı yapıları destekler.</span><span class="sxs-lookup"><span data-stu-id="57d42-134">`dotnet build` uses MSBuild to build the project, so it supports both parallel and incremental builds.</span></span> <span data-ttu-id="57d42-135">Daha fazla bilgi için bkz. [Artımlı derlemeler](/visualstudio/msbuild/incremental-builds).</span><span class="sxs-lookup"><span data-stu-id="57d42-135">For more information, see [Incremental Builds](/visualstudio/msbuild/incremental-builds).</span></span>

<span data-ttu-id="57d42-136">Seçeneklerine ek olarak `dotnet build` komut, `-p` özellikleri ayarlama veya bir günlükçü tanımlama gibi MSBuild seçeneklerini kabul eder `-l` .</span><span class="sxs-lookup"><span data-stu-id="57d42-136">In addition to its options, the `dotnet build` command accepts MSBuild options, such as `-p` for setting properties or `-l` to define a logger.</span></span> <span data-ttu-id="57d42-137">Bu seçenekler hakkında daha fazla bilgi için bkz. [MSBuild komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="57d42-137">For more information about these options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="57d42-138">Ayrıca [DotNet MSBuild](dotnet-msbuild.md) komutunu da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="57d42-138">Or you can also use the [dotnet msbuild](dotnet-msbuild.md) command.</span></span>

<span data-ttu-id="57d42-139">Çalışıyor, `dotnet build` çalıştırmaya eşdeğerdir `dotnet msbuild -restore` ; ancak, çıktının varsayılan ayrıntı düzeyi farklıdır.</span><span class="sxs-lookup"><span data-stu-id="57d42-139">Running `dotnet build` is equivalent to running `dotnet msbuild -restore`; however, the default verbosity of the output is different.</span></span>

## <a name="arguments"></a><span data-ttu-id="57d42-140">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="57d42-140">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="57d42-141">Derlenecek proje veya çözüm dosyası.</span><span class="sxs-lookup"><span data-stu-id="57d42-141">The project or solution file to build.</span></span> <span data-ttu-id="57d42-142">Bir proje veya çözüm dosyası belirtilmemişse, MSBuild, *proj* veya *sln* 'de biten bir dosya uzantısına sahip bir dosya için geçerli çalışma dizinini arar ve bu dosyayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="57d42-142">If a project or solution file isn't specified, MSBuild searches the current working directory for a file that has a file extension that ends in either *proj* or *sln* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="57d42-143">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="57d42-143">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="57d42-144">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="57d42-144">Defines the build configuration.</span></span> <span data-ttu-id="57d42-145">Çoğu proje için varsayılandır `Debug` , ancak projenizde derleme yapılandırma ayarlarını geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="57d42-145">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="57d42-146">Belirli bir [çerçeve](../../standard/frameworks.md)için derlenir.</span><span class="sxs-lookup"><span data-stu-id="57d42-146">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="57d42-147">Çerçeve [Proje dosyasında](csproj.md)tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="57d42-147">The framework must be defined in the [project file](csproj.md).</span></span>

- **`--force`**

  <span data-ttu-id="57d42-148">Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar.</span><span class="sxs-lookup"><span data-stu-id="57d42-148">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="57d42-149">Bu bayrağın belirtilmesi, *Project. varlıklar. JSON* dosyasını silme ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="57d42-149">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="57d42-150">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="57d42-150">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="57d42-151">Komutun Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="57d42-151">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="57d42-152">Örneğin, kimlik doğrulamasını tamamlamaya yönelik.</span><span class="sxs-lookup"><span data-stu-id="57d42-152">For example, to complete authentication.</span></span> <span data-ttu-id="57d42-153">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="57d42-153">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="57d42-154">Projeden projeye (P2P) başvurularını yoksayar ve yalnızca belirtilen kök projeyi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="57d42-154">Ignores project-to-project (P2P) references and only builds the specified root project.</span></span>

- **`--no-incremental`**

  <span data-ttu-id="57d42-155">Derlemeyi Artımlı derleme için güvenli değil olarak işaretler.</span><span class="sxs-lookup"><span data-stu-id="57d42-155">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="57d42-156">Bu bayrak, artımlı derlemeyi kapatır ve projenin bağımlılık grafiğinin temiz bir yeniden oluşturulmasına zorlar.</span><span class="sxs-lookup"><span data-stu-id="57d42-156">This flag turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

- **`--no-restore`**

  <span data-ttu-id="57d42-157">Derleme sırasında örtük geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="57d42-157">Doesn't execute an implicit restore during build.</span></span>

- **`--nologo`**

  <span data-ttu-id="57d42-158">Başlangıç başlığını veya telif hakkı iletisini görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="57d42-158">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="57d42-159">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="57d42-159">Available since .NET Core 3.0 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="57d42-160">Oluşturulan ikililerin yerleştirileceği dizin.</span><span class="sxs-lookup"><span data-stu-id="57d42-160">Directory in which to place the built binaries.</span></span> <span data-ttu-id="57d42-161">Belirtilmemişse, varsayılan yol olur `./bin/<configuration>/<framework>/` .</span><span class="sxs-lookup"><span data-stu-id="57d42-161">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="57d42-162">Birden çok hedef çerçevesi olan projeler için ( `TargetFrameworks` özelliği aracılığıyla), `--framework` Bu seçeneği ne zaman belirttiğinizde de tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="57d42-162">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="57d42-163">Hedef çalışma zamanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="57d42-163">Specifies the target runtime.</span></span> <span data-ttu-id="57d42-164">Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="57d42-164">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="57d42-165">Geri yükleme işlemi sırasında kullanılacak NuGet paket kaynağının URI 'SI.</span><span class="sxs-lookup"><span data-stu-id="57d42-165">The URI of the NuGet package source to use during the restore operation.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="57d42-166">MSBuild ayrıntı düzeyi düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="57d42-166">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="57d42-167">İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="57d42-167">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="57d42-168">Varsayılan değer: `minimal`.</span><span class="sxs-lookup"><span data-stu-id="57d42-168">The default is `minimal`.</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="57d42-169">`$(VersionSuffix)`Proje oluşturulurken kullanılacak özelliğin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="57d42-169">Sets the value of the `$(VersionSuffix)` property to use when building the project.</span></span> <span data-ttu-id="57d42-170">Bu yalnızca `$(Version)` özellik ayarlanmamışsa işe yarar.</span><span class="sxs-lookup"><span data-stu-id="57d42-170">This only works if the `$(Version)` property isn't set.</span></span> <span data-ttu-id="57d42-171">Daha sonra, `$(Version)` `$(VersionPrefix)` ile birleştirilmiş olarak ayarlanır `$(VersionSuffix)` , tireyle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="57d42-171">Then, `$(Version)` is set to the `$(VersionPrefix)` combined with the `$(VersionSuffix)`, separated by a dash.</span></span>

## <a name="examples"></a><span data-ttu-id="57d42-172">Örnekler</span><span class="sxs-lookup"><span data-stu-id="57d42-172">Examples</span></span>

- <span data-ttu-id="57d42-173">Bir proje ve bağımlılıklarını oluşturun:</span><span class="sxs-lookup"><span data-stu-id="57d42-173">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet build
  ```

- <span data-ttu-id="57d42-174">Yayın yapılandırması kullanarak bir proje ve bağımlılıklarını oluşturun:</span><span class="sxs-lookup"><span data-stu-id="57d42-174">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet build --configuration Release
  ```

- <span data-ttu-id="57d42-175">Belirli bir çalışma zamanı için bir proje ve bağımlılıklarını oluşturun (Bu örnekte Ubuntu 18,04):</span><span class="sxs-lookup"><span data-stu-id="57d42-175">Build a project and its dependencies for a specific runtime (in this example, Ubuntu 18.04):</span></span>

  ```dotnetcli
  dotnet build --runtime ubuntu.18.04-x64
  ```

- <span data-ttu-id="57d42-176">Projeyi derleyin ve geri yükleme işlemi sırasında belirtilen NuGet paket kaynağını kullanın (.NET Core 2,0 SDK ve sonraki sürümleri):</span><span class="sxs-lookup"><span data-stu-id="57d42-176">Build the project and use the specified NuGet package source during the restore operation (.NET Core 2.0 SDK and later versions):</span></span>

  ```dotnetcli
  dotnet build --source c:\packages\mypackages
  ```

- <span data-ttu-id="57d42-177">`-p` [MSBuild seçeneğini](#msbuild)kullanarak projeyi derleyin ve derleme parametresi olarak 1.2.3.4 olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="57d42-177">Build the project and set version 1.2.3.4 as a build parameter using the `-p` [MSBuild option](#msbuild):</span></span>

  ```dotnetcli
  dotnet build -p:Version=1.2.3.4
  ```
