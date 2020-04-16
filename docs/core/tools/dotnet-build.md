---
title: dotnet yapı komutu
description: Dotnet build komutu bir proje ve tüm bağımlılıklarını oluşturur.
ms.date: 02/14/2020
ms.openlocfilehash: 27deca4ab1c12314db5214c73660862a8a57a398
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463716"
---
# <a name="dotnet-build"></a><span data-ttu-id="3f3e7-103">dotnet build</span><span class="sxs-lookup"><span data-stu-id="3f3e7-103">dotnet build</span></span>

<span data-ttu-id="3f3e7-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 2.x SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="3f3e7-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="3f3e7-105">Adı</span><span class="sxs-lookup"><span data-stu-id="3f3e7-105">Name</span></span>

<span data-ttu-id="3f3e7-106">`dotnet build`- Bir proje ve tüm bağımlılıkları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-106">`dotnet build` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="3f3e7-107">Özet</span><span class="sxs-lookup"><span data-stu-id="3f3e7-107">Synopsis</span></span>

```dotnetcli
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [-f|--framework <FRAMEWORK>] [--force] [--interactive] [--no-dependencies]
    [--no-incremental] [--no-restore] [--nologo] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [-v|--verbosity <LEVEL>]
    [--version-suffix <VERSION_SUFFIX>]

dotnet build -h|--help
```

## <a name="description"></a><span data-ttu-id="3f3e7-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3f3e7-108">Description</span></span>

<span data-ttu-id="3f3e7-109">Komut, `dotnet build` projeyi ve bağımlılıklarını bir dizi ikili ye dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-109">The `dotnet build` command builds the project and its dependencies into a set of binaries.</span></span> <span data-ttu-id="3f3e7-110">İkili dosyalar, projenin kodlarını *.dll* uzantılı Orta Dil (IL) dosyalarında içerir.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-110">The binaries include the project's code in Intermediate Language (IL) files with a *.dll* extension.</span></span>  <span data-ttu-id="3f3e7-111">Proje türüne ve ayarlarına bağlı olarak, aşağıdakiler gibi başka dosyalar da eklenebilir:</span><span class="sxs-lookup"><span data-stu-id="3f3e7-111">Depending on the project type and settings, other files may be included, such as:</span></span>

- <span data-ttu-id="3f3e7-112">Proje türü yürütülebilir bir hedefleme .NET Core 3.0 veya daha sonra ise, uygulamayı çalıştırmak için kullanılabilecek bir yürütülebilir.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-112">An executable that can be used to run the application, if the project type is an executable targeting .NET Core 3.0 or later.</span></span>
- <span data-ttu-id="3f3e7-113">*.pdb* uzantılı hata ayıklama için kullanılan simge dosyaları.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-113">Symbol files used for debugging with a *.pdb* extension.</span></span>
- <span data-ttu-id="3f3e7-114">Uygulamanın veya kitaplığın bağımlılıklarını listeleyen bir *.deps.json* dosyası.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-114">A *.deps.json* file, which lists the dependencies of the application or library.</span></span>
- <span data-ttu-id="3f3e7-115">Bir uygulama için paylaşılan çalışma süresini ve sürümünü belirten bir *.runtimeconfig.json* dosyası.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-115">A *.runtimeconfig.json* file, which specifies the shared runtime and its version for an application.</span></span>
- <span data-ttu-id="3f3e7-116">Projenin bağlı olduğu diğer kitaplıklar (proje referansları veya NuGet paket başvuruları yoluyla).</span><span class="sxs-lookup"><span data-stu-id="3f3e7-116">Other libraries that the project depends on (via project references or NuGet package references).</span></span>

<span data-ttu-id="3f3e7-117">.NET Core 3.0'dan önceki sürümleri hedefleyen çalıştırılabilir projeler için, NuGet'in kitaplık bağımlılıkları genellikle çıktı klasörüne kopyalanmaz.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-117">For executable projects targeting versions earlier than .NET Core 3.0, library dependencies from NuGet are typically NOT copied to the output folder.</span></span>  <span data-ttu-id="3f3e7-118">Bunlar, çalışma zamanında NuGet global paketler klasöründen çözülür.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-118">They're resolved from the NuGet global packages folder at run time.</span></span> <span data-ttu-id="3f3e7-119">Bunu göz önünde bulundurarak, ürün `dotnet build` çalıştırmak için başka bir makineye transfer için hazır değildir.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-119">With that in mind, the product of `dotnet build` isn't ready to be transferred to another machine to run.</span></span> <span data-ttu-id="3f3e7-120">Uygulamanın dağıtılabilen bir sürümünü oluşturmak için, uygulamayı yayımlamanız gerekir (örneğin, [dotnet yayımlama](dotnet-publish.md) komutuyla).</span><span class="sxs-lookup"><span data-stu-id="3f3e7-120">To create a version of the application that can be deployed, you need to publish it (for example, with the [dotnet publish](dotnet-publish.md) command).</span></span> <span data-ttu-id="3f3e7-121">Daha fazla bilgi için [bkz.](../deploying/index.md)</span><span class="sxs-lookup"><span data-stu-id="3f3e7-121">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span>

<span data-ttu-id="3f3e7-122">.NET Core 3.0 ve sonrası hedeflemesi yapılan yürütülebilir projeler için kitaplık bağımlılıkları çıktı klasörüne kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-122">For executable projects targeting .NET Core 3.0 and later, library dependencies are copied to the output folder.</span></span> <span data-ttu-id="3f3e7-123">Bu, yayımlamaya özgü başka bir mantık yoksa (Web projeleri gibi), yapı çıktısının dağıtılabilir olması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-123">This means that if there isn't any other publish-specific logic (such as Web projects have), the build output should be deployable.</span></span>

<span data-ttu-id="3f3e7-124">Bina, uygulamanızın bağımlılıklarını listeleyen *project.assets.json* dosyasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-124">Building requires the *project.assets.json* file, which lists the dependencies of your application.</span></span> <span data-ttu-id="3f3e7-125">Dosya yürütüldüğünde [`dotnet restore`](dotnet-restore.md) oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-125">The file is created when [`dotnet restore`](dotnet-restore.md) is executed.</span></span> <span data-ttu-id="3f3e7-126">Varlıklar dosyası yerinde olmadan, takım başvuru derlemelerini çözemez ve bu da hatalara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-126">Without the assets file in place, the tooling can't resolve reference assemblies, which results in errors.</span></span> <span data-ttu-id="3f3e7-127">.NET Core 1.x SDK ile çalıştırmadan `dotnet restore` `dotnet build`önce açıkça çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-127">With .NET Core 1.x SDK, you needed to explicitly run `dotnet restore` before running `dotnet build`.</span></span> <span data-ttu-id="3f3e7-128">.NET Core 2.0 SDK `dotnet restore` ile başlayarak, `dotnet build`çalıştırdığınızda örtülü olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-128">Starting with .NET Core 2.0 SDK, `dotnet restore` runs implicitly when you run `dotnet build`.</span></span> <span data-ttu-id="3f3e7-129">Yapı komutunu çalıştırırken örtülü geri yüklemeyi devre dışı `--no-restore` kalmak istiyorsanız, seçeneği geçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-129">If you want to disable implicit restore when running the build command, you can pass the `--no-restore` option.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

<span data-ttu-id="3f3e7-130">Projenin yürütülüp yürütülemeyeceği proje `<OutputType>` dosyasındaki özellik tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-130">Whether the project is executable or not is determined by the `<OutputType>` property in the project file.</span></span> <span data-ttu-id="3f3e7-131">Aşağıdaki örnek, yürütülebilir kod üreten bir projeyi gösterir:</span><span class="sxs-lookup"><span data-stu-id="3f3e7-131">The following example shows a project that produces executable code:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="3f3e7-132">Kitaplık oluşturmak için, özelliği `<OutputType>` atlaveya değerini `Library`' ye değdirin.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-132">To produce a library, omit the `<OutputType>` property or change its value to `Library`.</span></span> <span data-ttu-id="3f3e7-133">Kitaplık için IL DLL giriş noktaları içermez ve yürütülemez.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-133">The IL DLL for a library doesn't contain entry points and can't be executed.</span></span>

### <a name="msbuild"></a><span data-ttu-id="3f3e7-134">MSBuild</span><span class="sxs-lookup"><span data-stu-id="3f3e7-134">MSBuild</span></span>

<span data-ttu-id="3f3e7-135">`dotnet build`projeyi oluşturmak için MSBuild'i kullanır, böylece hem paralel hem de artımlı yapıyı destekler.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-135">`dotnet build` uses MSBuild to build the project, so it supports both parallel and incremental builds.</span></span> <span data-ttu-id="3f3e7-136">Daha fazla bilgi için [Bkz. Artımlı Yapılar.](/visualstudio/msbuild/incremental-builds)</span><span class="sxs-lookup"><span data-stu-id="3f3e7-136">For more information, see [Incremental Builds](/visualstudio/msbuild/incremental-builds).</span></span>

<span data-ttu-id="3f3e7-137">Komut, seçeneklerine ek `dotnet build` olarak, özellikleri ayarlama veya `-p` `-l` logger tanımlama gibi MSBuild seçeneklerini de kabul eder.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-137">In addition to its options, the `dotnet build` command accepts MSBuild options, such as `-p` for setting properties or `-l` to define a logger.</span></span> <span data-ttu-id="3f3e7-138">Bu seçenekler hakkında daha fazla bilgi için [MSBuild Komut Satırı Başvurusu'na](/visualstudio/msbuild/msbuild-command-line-reference)bakın.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-138">For more information about these options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="3f3e7-139">Veya [dotnet msbuild](dotnet-msbuild.md) komutunu da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-139">Or you can also use the [dotnet msbuild](dotnet-msbuild.md) command.</span></span>

<span data-ttu-id="3f3e7-140">Koşmak `dotnet build` koşmaya `dotnet msbuild -restore`eşdeğerdir; ancak, çıktının varsayılan ayrıntılılığı farklıdır.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-140">Running `dotnet build` is equivalent to running `dotnet msbuild -restore`; however, the default verbosity of the output is different.</span></span>

## <a name="arguments"></a><span data-ttu-id="3f3e7-141">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="3f3e7-141">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="3f3e7-142">Oluşturmak için proje veya çözüm dosyası.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-142">The project or solution file to build.</span></span> <span data-ttu-id="3f3e7-143">Bir proje veya çözüm dosyası belirtilmemişse, MSBuild *proj* veya *sln* ile biten ve bu dosyayı kullanan bir dosya uzantısı olan bir dosya için geçerli çalışma dizinini arar.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-143">If a project or solution file isn't specified, MSBuild searches the current working directory for a file that has a file extension that ends in either *proj* or *sln* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="3f3e7-144">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="3f3e7-144">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="3f3e7-145">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-145">Defines the build configuration.</span></span> <span data-ttu-id="3f3e7-146">Çoğu proje için `Debug`varsayılan değer, ancak projenizdeki yapı yapılandırma ayarlarını geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-146">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="3f3e7-147">Belirli bir [çerçeve](../../standard/frameworks.md)için derler.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-147">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="3f3e7-148">Çerçeve [proje dosyasında](csproj.md)tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-148">The framework must be defined in the [project file](csproj.md).</span></span>

- **`--force`**

  <span data-ttu-id="3f3e7-149">Son geri yükleme başarılı olsa bile tüm bağımlılıkları çözüme kavuşturmaya zorlar.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-149">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="3f3e7-150">Bu bayrağı *belirtmek, project.assets.json* dosyasını silmekle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-150">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="3f3e7-151">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-151">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="3f3e7-152">Komutun durmasını ve kullanıcı girişi veya eylemini beklemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-152">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="3f3e7-153">Örneğin, kimlik doğrulamasını tamamlamak için.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-153">For example, to complete authentication.</span></span> <span data-ttu-id="3f3e7-154">.NET Core 3.0 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-154">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="3f3e7-155">Projeden projeye (P2P) başvurularını yoksa ve yalnızca belirtilen kök projeyi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-155">Ignores project-to-project (P2P) references and only builds the specified root project.</span></span>

- **`--no-incremental`**

  <span data-ttu-id="3f3e7-156">Artımlı yapı için yapıyı güvenli olmayan olarak işaretler.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-156">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="3f3e7-157">Bu bayrak artımlı derlemeyi kapatır ve projenin bağımlılık grafiğini temiz bir yeniden oluşturmaya zorlar.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-157">This flag turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

- **`--no-restore`**

  <span data-ttu-id="3f3e7-158">Yapı sırasında örtük bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-158">Doesn't execute an implicit restore during build.</span></span>

- **`--nologo`**

  <span data-ttu-id="3f3e7-159">Başlangıç bayrağını veya telif hakkı iletisini görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-159">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="3f3e7-160">.NET Core 3.0 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-160">Available since .NET Core 3.0 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="3f3e7-161">Yapılı ikililerin yerleştirilen dizin.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-161">Directory in which to place the built binaries.</span></span> <span data-ttu-id="3f3e7-162">Belirtilmemişse, varsayılan `./bin/<configuration>/<framework>/`yol .</span><span class="sxs-lookup"><span data-stu-id="3f3e7-162">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="3f3e7-163">Birden çok hedef çerçevesi olan `TargetFrameworks` projelerde (özellik üzerinden), bu seçeneği belirttiğinizi de tanımlamanız `--framework` gerekir.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-163">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="3f3e7-164">Hedef çalışma süresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-164">Specifies the target runtime.</span></span> <span data-ttu-id="3f3e7-165">Runtime Tanımlayıcıları (RID'ler) listesi için RID [kataloğuna](../rid-catalog.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-165">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="3f3e7-166">MSBuild ayrıntılı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-166">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="3f3e7-167">İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve .</span><span class="sxs-lookup"><span data-stu-id="3f3e7-167">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="3f3e7-168">Varsayılan değer: `minimal`.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-168">The default is `minimal`.</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="3f3e7-169">Projeyi `$(VersionSuffix)` yaparken kullanılacak özelliğin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-169">Sets the value of the `$(VersionSuffix)` property to use when building the project.</span></span> <span data-ttu-id="3f3e7-170">Bu yalnızca `$(Version)` özellik ayarlı değilse çalışır.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-170">This only works if the `$(Version)` property isn't set.</span></span> <span data-ttu-id="3f3e7-171">Daha `$(Version)` sonra, bir `$(VersionPrefix)` çizgi `$(VersionSuffix)`ile ayrılmış ile birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-171">Then, `$(Version)` is set to the `$(VersionPrefix)` combined with the `$(VersionSuffix)`, separated by a dash.</span></span>

## <a name="examples"></a><span data-ttu-id="3f3e7-172">Örnekler</span><span class="sxs-lookup"><span data-stu-id="3f3e7-172">Examples</span></span>

- <span data-ttu-id="3f3e7-173">Bir proje ve bağımlılıkları oluşturun:</span><span class="sxs-lookup"><span data-stu-id="3f3e7-173">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet build
  ```

- <span data-ttu-id="3f3e7-174">Sürüm yapılandırmasını kullanarak bir proje ve bağımlılıkları oluşturun:</span><span class="sxs-lookup"><span data-stu-id="3f3e7-174">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet build --configuration Release
  ```

- <span data-ttu-id="3f3e7-175">Belirli bir çalışma zamanı için proje ve bağımlılıkları oluşturun (bu örnekte, Ubuntu 18.04):</span><span class="sxs-lookup"><span data-stu-id="3f3e7-175">Build a project and its dependencies for a specific runtime (in this example, Ubuntu 18.04):</span></span>

  ```dotnetcli
  dotnet build --runtime ubuntu.18.04-x64
  ```

- <span data-ttu-id="3f3e7-176">Projeyi oluşturun ve geri yükleme işlemi sırasında belirtilen NuGet paket kaynağını kullanın (.NET Core 2.0 SDK ve sonraki sürümler):</span><span class="sxs-lookup"><span data-stu-id="3f3e7-176">Build the project and use the specified NuGet package source during the restore operation (.NET Core 2.0 SDK and later versions):</span></span>

  ```dotnetcli
  dotnet build --source c:\packages\mypackages
  ```

- <span data-ttu-id="3f3e7-177">PROJEYI oluşturun ve `-p` [MSBuild seçeneğini](#msbuild)kullanarak sürüm 1.2.3.4'u yapı parametresi olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="3f3e7-177">Build the project and set version 1.2.3.4 as a build parameter using the `-p` [MSBuild option](#msbuild):</span></span>

  ```dotnetcli
  dotnet build -p:Version=1.2.3.4
  ```
