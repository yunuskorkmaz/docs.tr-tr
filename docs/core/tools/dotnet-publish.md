---
title: dotnet publish komutu
description: Dotnet publish komutu bir dizine .NET Core projesi veya çözümü yayımlar.
ms.date: 02/24/2020
ms.openlocfilehash: 697746291a8b34a856433049fe7264ad0ea4af7a
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761908"
---
# <a name="dotnet-publish"></a><span data-ttu-id="63dbd-103">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="63dbd-103">dotnet publish</span></span>

<span data-ttu-id="63dbd-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="63dbd-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="63dbd-105">Name</span><span class="sxs-lookup"><span data-stu-id="63dbd-105">Name</span></span>

<span data-ttu-id="63dbd-106">`dotnet publish`-Uygulamayı ve bağımlılıklarını barındırma sistemine dağıtım için bir klasöre yayımlar.</span><span class="sxs-lookup"><span data-stu-id="63dbd-106">`dotnet publish` - Publishes the application and its dependencies to a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="63dbd-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="63dbd-107">Synopsis</span></span>

```dotnetcli
dotnet publish [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [-f|--framework <FRAMEWORK>] [--force] [--interactive]
    [--manifest <PATH_TO_MANIFEST_FILE>] [--no-build] [--no-dependencies]
    [--no-restore] [--nologo] [-o|--output <OUTPUT_DIRECTORY>]
    [-p:PublishReadyToRun=true] [-p:PublishSingleFile=true] [-p:PublishTrimmed=true]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [--self-contained [true|false]]
    [--no-self-contained] [-v|--verbosity <LEVEL>]
    [--version-suffix <VERSION_SUFFIX>]

dotnet publish -h|--help
```

## <a name="description"></a><span data-ttu-id="63dbd-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="63dbd-108">Description</span></span>

<span data-ttu-id="63dbd-109">`dotnet publish`uygulamayı derler, proje dosyasında belirtilen bağımlılıklarını okur ve elde edilen dosya kümesini bir dizine yayınlar.</span><span class="sxs-lookup"><span data-stu-id="63dbd-109">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="63dbd-110">Çıktı aşağıdaki varlıkları içerir:</span><span class="sxs-lookup"><span data-stu-id="63dbd-110">The output includes the following assets:</span></span>

- <span data-ttu-id="63dbd-111">*DLL* uzantılı bir derlemede ara DIL (IL) kodu.</span><span class="sxs-lookup"><span data-stu-id="63dbd-111">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
- <span data-ttu-id="63dbd-112">Projenin tüm bağımlılıklarını içeren bir *. Deps. JSON* dosyası.</span><span class="sxs-lookup"><span data-stu-id="63dbd-112">A *.deps.json* file that includes all of the dependencies of the project.</span></span>
- <span data-ttu-id="63dbd-113">Uygulamanın beklediği paylaşılan çalışma zamanını belirten *. runtimeconfig. JSON* dosyası ve çalışma zamanına yönelik diğer yapılandırma seçenekleri (örneğin, çöp toplama türü).</span><span class="sxs-lookup"><span data-stu-id="63dbd-113">A *.runtimeconfig.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
- <span data-ttu-id="63dbd-114">NuGet önbelleğinden çıkış klasörüne kopyalanmış olan uygulamanın bağımlılıkları.</span><span class="sxs-lookup"><span data-stu-id="63dbd-114">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="63dbd-115">`dotnet publish`Komutun çıktısı, yürütme için bir barındırma sistemine (örneğin, bir sunucu, PC, Mac, dizüstü bilgisayar) dağıtıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="63dbd-115">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="63dbd-116">Uygulamayı dağıtıma hazırlamak için tek resmi olarak desteklenen bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="63dbd-116">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="63dbd-117">Projenin belirttiği dağıtımın türüne bağlı olarak, barındırma sisteminde .NET Core paylaşılan çalışma zamanı yüklü olabilir veya olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="63dbd-117">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="63dbd-118">Daha fazla bilgi için bkz. [.NET Core CLI .NET Core Apps yayımlama](../deploying/deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="63dbd-118">For more information, see [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="63dbd-119">Örtük geri yükleme</span><span class="sxs-lookup"><span data-stu-id="63dbd-119">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

### <a name="msbuild"></a><span data-ttu-id="63dbd-120">MSBuild</span><span class="sxs-lookup"><span data-stu-id="63dbd-120">MSBuild</span></span>

<span data-ttu-id="63dbd-121">`dotnet publish`Komutu, hedefi çağıran MSBuild 'i çağırır `Publish` .</span><span class="sxs-lookup"><span data-stu-id="63dbd-121">The `dotnet publish` command calls MSBuild, which invokes the `Publish` target.</span></span> <span data-ttu-id="63dbd-122">Öğesine geçirilen parametreler `dotnet publish` MSBuild 'e geçirilir.</span><span class="sxs-lookup"><span data-stu-id="63dbd-122">Any parameters passed to `dotnet publish` are passed to MSBuild.</span></span> <span data-ttu-id="63dbd-123">`-c`Ve `-o` parametreleri `Configuration` sırasıyla MSBuild ve özellikler ile eşlenir `OutputPath` .</span><span class="sxs-lookup"><span data-stu-id="63dbd-123">The `-c` and `-o` parameters map to MSBuild's `Configuration` and `OutputPath` properties, respectively.</span></span>

<span data-ttu-id="63dbd-124">`dotnet publish`Komut, `-p` özellikleri ayarlama ve bir günlükçü tanımlama gibi MSBuild seçeneklerini kabul eder `-l` .</span><span class="sxs-lookup"><span data-stu-id="63dbd-124">The `dotnet publish` command accepts MSBuild options, such as `-p` for setting properties and `-l` to define a logger.</span></span> <span data-ttu-id="63dbd-125">Örneğin, şu biçimi kullanarak bir MSBuild özelliği ayarlayabilirsiniz: `-p:<NAME>=<VALUE>` .</span><span class="sxs-lookup"><span data-stu-id="63dbd-125">For example, you can set an MSBuild property by using the format: `-p:<NAME>=<VALUE>`.</span></span> <span data-ttu-id="63dbd-126">Ayrıca, bir *. pubxml* dosyasına başvurarak yayınla ilgili özellikleri ayarlayabilirsiniz, örneğin:</span><span class="sxs-lookup"><span data-stu-id="63dbd-126">You can also set publish-related properties by referring to a *.pubxml* file, for example:</span></span>

```dotnetcli
dotnet publish -p:PublishProfile=Properties\PublishProfiles\FolderProfile.pubxml
```

<span data-ttu-id="63dbd-127">Daha fazla bilgi için aşağıdaki kaynaklara bakın:</span><span class="sxs-lookup"><span data-stu-id="63dbd-127">For more information, see the following resources:</span></span>

- [<span data-ttu-id="63dbd-128">MSBuild komut satırı başvurusu</span><span class="sxs-lookup"><span data-stu-id="63dbd-128">MSBuild command-line reference</span></span>](/visualstudio/msbuild/msbuild-command-line-reference)
- [<span data-ttu-id="63dbd-129">ASP.NET Core uygulama dağıtımı için Visual Studio yayımlama profilleri (. pubxml)</span><span class="sxs-lookup"><span data-stu-id="63dbd-129">Visual Studio publish profiles (.pubxml) for ASP.NET Core app deployment</span></span>](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [<span data-ttu-id="63dbd-130">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="63dbd-130">dotnet msbuild</span></span>](dotnet-msbuild.md)

## <a name="arguments"></a><span data-ttu-id="63dbd-131">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="63dbd-131">Arguments</span></span>

- **`PROJECT|SOLUTION`**

  <span data-ttu-id="63dbd-132">Yayımlanacak proje veya çözüm.</span><span class="sxs-lookup"><span data-stu-id="63dbd-132">The project or solution to publish.</span></span>
  
  * <span data-ttu-id="63dbd-133">`PROJECT`bir [C#](csproj.md), f # veya Visual Basic proje dosyasının yolu ve dosya adı ya da C#, f # veya Visual Basic proje dosyası içeren bir dizinin yoludur.</span><span class="sxs-lookup"><span data-stu-id="63dbd-133">`PROJECT` is the path and filename of a [C#](csproj.md), F#, or Visual Basic project file, or the path to a directory that contains a C#, F#, or Visual Basic project file.</span></span> <span data-ttu-id="63dbd-134">Dizin belirtilmemişse, varsayılan olarak geçerli dizine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="63dbd-134">If the directory is not specified, it defaults to the current directory.</span></span>

  * <span data-ttu-id="63dbd-135">`SOLUTION`, bir çözüm dosyasının (*. sln* uzantısının) yolu ve dosya adı veya çözüm dosyası içeren bir dizinin yoludur.</span><span class="sxs-lookup"><span data-stu-id="63dbd-135">`SOLUTION` is the path and filename of a solution file (*.sln* extension), or the path to a directory that contains a solution file.</span></span> <span data-ttu-id="63dbd-136">Dizin belirtilmemişse, varsayılan olarak geçerli dizine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="63dbd-136">If the directory is not specified, it defaults to the current directory.</span></span> <span data-ttu-id="63dbd-137">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="63dbd-137">Available since .NET Core 3.0 SDK.</span></span>

## <a name="options"></a><span data-ttu-id="63dbd-138">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="63dbd-138">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="63dbd-139">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="63dbd-139">Defines the build configuration.</span></span> <span data-ttu-id="63dbd-140">Çoğu proje için varsayılandır `Debug` , ancak projenizde derleme yapılandırma ayarlarını geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="63dbd-140">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="63dbd-141">Belirtilen [hedef çerçeve](../../standard/frameworks.md)için uygulamayı yayımlar.</span><span class="sxs-lookup"><span data-stu-id="63dbd-141">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="63dbd-142">Hedef çerçeveyi proje dosyasında belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="63dbd-142">You must specify the target framework in the project file.</span></span>

- **`--force`**

  <span data-ttu-id="63dbd-143">Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar.</span><span class="sxs-lookup"><span data-stu-id="63dbd-143">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="63dbd-144">Bu bayrağın belirtilmesi, *Project. varlıklar. JSON* dosyasını silme ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="63dbd-144">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="63dbd-145">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="63dbd-145">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="63dbd-146">Komutun Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="63dbd-146">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="63dbd-147">Örneğin, kimlik doğrulamasını tamamlamaya yönelik.</span><span class="sxs-lookup"><span data-stu-id="63dbd-147">For example, to complete authentication.</span></span> <span data-ttu-id="63dbd-148">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="63dbd-148">Available since .NET Core 3.0 SDK.</span></span>

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  <span data-ttu-id="63dbd-149">Uygulamayla yayımlanmış paket kümesini kırpmak için kullanılacak bir veya birkaç [hedef bildirimi](../deploying/runtime-store.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="63dbd-149">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="63dbd-150">Bildirim dosyası, [ `dotnet store` komutun](dotnet-store.md)çıktısının bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="63dbd-150">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="63dbd-151">Birden çok bildirim belirtmek için `--manifest` her bildirim için bir seçenek ekleyin.</span><span class="sxs-lookup"><span data-stu-id="63dbd-151">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span>

- **`--no-build`**

  <span data-ttu-id="63dbd-152">Yayımlamadan önce projeyi oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="63dbd-152">Doesn't build the project before publishing.</span></span> <span data-ttu-id="63dbd-153">Ayrıca bayrağı örtülü olarak ayarlar `--no-restore` .</span><span class="sxs-lookup"><span data-stu-id="63dbd-153">It also implicitly sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="63dbd-154">Projeden projeye başvuruları yoksayar ve yalnızca kök projeyi geri yükler.</span><span class="sxs-lookup"><span data-stu-id="63dbd-154">Ignores project-to-project references and only restores the root project.</span></span>

- **`--nologo`**

  <span data-ttu-id="63dbd-155">Başlangıç başlığını veya telif hakkı iletisini görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="63dbd-155">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="63dbd-156">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="63dbd-156">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="63dbd-157">Komutu çalıştırılırken örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="63dbd-157">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="63dbd-158">Çıkış dizini için yolu belirtir.</span><span class="sxs-lookup"><span data-stu-id="63dbd-158">Specifies the path for the output directory.</span></span>
  
  <span data-ttu-id="63dbd-159">Belirtilmemişse, çalışma zamanına bağlı bir yürütülebilir dosya ve platformlar arası ikili dosyalar için *[project_file_folder]./bin/[Configuration]/[Framework]/Publish/* varsayılan değeri.</span><span class="sxs-lookup"><span data-stu-id="63dbd-159">If not specified, it defaults to *[project_file_folder]./bin/[configuration]/[framework]/publish/* for a runtime-dependent executable and cross-platform binaries.</span></span> <span data-ttu-id="63dbd-160">Bu, kendi içinde bulunan yürütülebilir dosya için *[project_file_folder]/bin/[yapılandırma]/[Framework]/[Runtime]/Publish/* varsayılan değerini alır.</span><span class="sxs-lookup"><span data-stu-id="63dbd-160">It defaults to *[project_file_folder]/bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained executable.</span></span>

  <span data-ttu-id="63dbd-161">Bir Web projesinde, çıkış klasörü proje klasöründe ise, birbirini izleyen `dotnet publish` Komutlar iç içe geçmiş çıkış klasörlerine neden olur.</span><span class="sxs-lookup"><span data-stu-id="63dbd-161">In a web project, if the output folder is in the project folder, successive `dotnet publish` commands result in nested output folders.</span></span> <span data-ttu-id="63dbd-162">Örneğin, proje klasörü *projem ise*ve yayımlama çıkış klasörü *myprojem/Publish*ise ve `dotnet publish` iki kez çalıştırırsanız ikinci çalıştırma, *MyProject/Publish/Publish*içindeki *. config* ve *. JSON* dosyaları gibi içerik dosyalarını koyar.</span><span class="sxs-lookup"><span data-stu-id="63dbd-162">For example, if the project folder is *myproject*, and the publish output folder is *myproject/publish*, and you run `dotnet publish` twice, the second run puts content files such as *.config* and *.json* files in *myproject/publish/publish*.</span></span> <span data-ttu-id="63dbd-163">Yayımlama klasörlerinin iç içe geçirilmesi önlemek için, proje **klasörünün altında olmayan** bir yayımlama klasörü belirtin veya Yayımla klasörünü projeden dışlayın.</span><span class="sxs-lookup"><span data-stu-id="63dbd-163">To avoid nesting publish folders, specify a publish folder that is not **directly** under the project folder, or exclude the publish folder from the project.</span></span> <span data-ttu-id="63dbd-164">*Publishoutput*adlı bir yayımlama klasörünü dışlamak için, `PropertyGroup` *. csproj* dosyasındaki bir öğeye aşağıdaki öğeyi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="63dbd-164">To exclude a publish folder named *publishoutput*, add the following element to a `PropertyGroup` element in the *.csproj* file:</span></span>

  ```xml
  <DefaultItemExcludes>$(DefaultItemExcludes);publishoutput**</DefaultItemExcludes>
  ```

  - <span data-ttu-id="63dbd-165">.NET Core 3. x SDK ve üzeri</span><span class="sxs-lookup"><span data-stu-id="63dbd-165">.NET Core 3.x SDK and later</span></span>
  
    <span data-ttu-id="63dbd-166">Bir proje yayımlanırken göreli bir yol belirtilmişse, oluşturulan çıkış dizini proje dosyası konumuna değil geçerli çalışma dizinine göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="63dbd-166">If a relative path is specified when publishing a project, the output directory generated is relative to the current working directory, not to the project file location.</span></span>

    <span data-ttu-id="63dbd-167">Bir çözüm yayımlarken göreli bir yol belirtilmişse, tüm projeler için tüm çıktılar geçerli çalışma dizinine göre belirtilen klasöre gider.</span><span class="sxs-lookup"><span data-stu-id="63dbd-167">If a relative path is specified when publishing a solution, all output for all projects goes into the specified folder relative to the current working directory.</span></span> <span data-ttu-id="63dbd-168">Yayımla çıkışını her proje için ayrı klasörlere gitmesini sağlamak için, seçeneği yerine MSBuild özelliğini kullanarak göreli bir yol belirtin `PublishDir` `--output` .</span><span class="sxs-lookup"><span data-stu-id="63dbd-168">To make publish output go to separate folders for each project, specify a relative path by using the msbuild `PublishDir` property instead of the `--output` option.</span></span> <span data-ttu-id="63dbd-169">Örneğin, `dotnet publish -p:PublishDir=.\publish` her proje için yayımlama çıkışını `publish` Proje dosyasını içeren klasörün altındaki bir klasöre gönderir.</span><span class="sxs-lookup"><span data-stu-id="63dbd-169">For example, `dotnet publish -p:PublishDir=.\publish` sends publish output for each project to a `publish` folder under the folder that contains the project file.</span></span>

  - <span data-ttu-id="63dbd-170">.NET Core 2. x SDK</span><span class="sxs-lookup"><span data-stu-id="63dbd-170">.NET Core 2.x SDK</span></span>
  
    <span data-ttu-id="63dbd-171">Bir proje yayımlanırken göreli bir yol belirtilmişse, oluşturulan çıkış dizini geçerli çalışma dizinine değil, proje dosyası konumuna göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="63dbd-171">If a relative path is specified when publishing a project, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

    <span data-ttu-id="63dbd-172">Bir çözüm yayımlarken göreli bir yol belirtilmişse, her projenin çıktısı proje dosyası konumuna göre ayrı bir klasöre gider.</span><span class="sxs-lookup"><span data-stu-id="63dbd-172">If a relative path is specified when publishing a solution, each project's output goes into a separate folder relative to the project file location.</span></span> <span data-ttu-id="63dbd-173">Bir çözüm yayımlarken mutlak bir yol belirtilmişse, tüm projeler için tüm yayımlama çıkışları belirtilen klasöre gider.</span><span class="sxs-lookup"><span data-stu-id="63dbd-173">If an absolute path is specified when publishing a solution, all publish output for all projects goes into the specified folder.</span></span>

- **`-p:PublishReadyToRun=true`**

  <span data-ttu-id="63dbd-174">Uygulama derlemelerini ReadyToRun (R2R) biçimi olarak derler.</span><span class="sxs-lookup"><span data-stu-id="63dbd-174">Compiles application assemblies as ReadyToRun (R2R) format.</span></span> <span data-ttu-id="63dbd-175">R2R, bir süre öncesi (AOT) derleme biçimidir.</span><span class="sxs-lookup"><span data-stu-id="63dbd-175">R2R is a form of ahead-of-time (AOT) compilation.</span></span> <span data-ttu-id="63dbd-176">Daha fazla bilgi için bkz. [Readytorun görüntüleri](../whats-new/dotnet-core-3-0.md#readytorun-images).</span><span class="sxs-lookup"><span data-stu-id="63dbd-176">For more information, see [ReadyToRun images](../whats-new/dotnet-core-3-0.md#readytorun-images).</span></span> <span data-ttu-id="63dbd-177">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="63dbd-177">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="63dbd-178">Bu seçeneği, komut satırı yerine bir yayımlama profilinde belirtmenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="63dbd-178">We recommend that you specify this option in a publish profile rather than on the command line.</span></span> <span data-ttu-id="63dbd-179">Daha fazla bilgi için bkz. [MSBuild](#msbuild).</span><span class="sxs-lookup"><span data-stu-id="63dbd-179">For more information, see [MSBuild](#msbuild).</span></span>

- **`-p:PublishSingleFile=true`**

  <span data-ttu-id="63dbd-180">Uygulamayı platforma özgü bir tek dosya yürütülebilir dosyasına paketler.</span><span class="sxs-lookup"><span data-stu-id="63dbd-180">Packages the app into a platform-specific single-file executable.</span></span> <span data-ttu-id="63dbd-181">Yürütülebilir dosya kendiliğinden ayıklanıyor ve uygulamayı çalıştırmak için gerekli tüm bağımlılıkları (yerel dahil) içerir.</span><span class="sxs-lookup"><span data-stu-id="63dbd-181">The executable is self-extracting and contains all dependencies (including native) that are required to run the app.</span></span> <span data-ttu-id="63dbd-182">Uygulama ilk kez çalıştırıldığında uygulama adı ve derleme tanımlayıcısı temelinde bir dizine çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="63dbd-182">When the app is first run, the application is extracted to a directory based on the app name and build identifier.</span></span> <span data-ttu-id="63dbd-183">Uygulama yeniden çalıştırıldığında başlatma daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="63dbd-183">Startup is faster when the application is run again.</span></span> <span data-ttu-id="63dbd-184">Yeni bir sürüm kullanılmadığı takdirde uygulamanın kendisi ikinci kez ayıklanmasına gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="63dbd-184">The application doesn't need to extract itself a second time unless a new version is used.</span></span> <span data-ttu-id="63dbd-185">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="63dbd-185">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="63dbd-186">Tek dosya yayınlama hakkında daha fazla bilgi için bkz. [tek dosya paketcisi tasarım belgesi](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md).</span><span class="sxs-lookup"><span data-stu-id="63dbd-186">For more information about single-file publishing, see the [single-file bundler design document](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md).</span></span>

  <span data-ttu-id="63dbd-187">Bu seçeneği, komut satırı yerine bir yayımlama profilinde belirtmenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="63dbd-187">We recommend that you specify this option in a publish profile rather than on the command line.</span></span> <span data-ttu-id="63dbd-188">Daha fazla bilgi için bkz. [MSBuild](#msbuild).</span><span class="sxs-lookup"><span data-stu-id="63dbd-188">For more information, see [MSBuild](#msbuild).</span></span>

- **`-p:PublishTrimmed=true`**

  <span data-ttu-id="63dbd-189">Bağımsız bir yürütülebilir dosya yayımlarken uygulamanın dağıtım boyutunu azaltmak için kullanılmayan kitaplıkları kırpar.</span><span class="sxs-lookup"><span data-stu-id="63dbd-189">Trims unused libraries to reduce the deployment size of an app when publishing a self-contained executable.</span></span> <span data-ttu-id="63dbd-190">Daha fazla bilgi için bkz. [kendi kendine kapsanan dağıtımları ve yürütülebilir dosyaları kırpma](../deploying/trim-self-contained.md).</span><span class="sxs-lookup"><span data-stu-id="63dbd-190">For more information, see [Trim self-contained deployments and executables](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="63dbd-191">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="63dbd-191">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="63dbd-192">Bu seçeneği, komut satırı yerine bir yayımlama profilinde belirtmenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="63dbd-192">We recommend that you specify this option in a publish profile rather than on the command line.</span></span> <span data-ttu-id="63dbd-193">Daha fazla bilgi için bkz. [MSBuild](#msbuild).</span><span class="sxs-lookup"><span data-stu-id="63dbd-193">For more information, see [MSBuild](#msbuild).</span></span>

- **`--self-contained [true|false]`**

  <span data-ttu-id="63dbd-194">.NET Core çalışma zamanını uygulamanızla yayımlar, böylece çalışma zamanının hedef makinede yüklü olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="63dbd-194">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="63dbd-195">Varsayılan olarak, `true` bir çalışma zamanı tanımlayıcısı belirtilirse ve proje yürütülebilir bir projem ise (kitaplık projesi değil).</span><span class="sxs-lookup"><span data-stu-id="63dbd-195">Default is `true` if a runtime identifier is specified and the project is an executable project (not a library project).</span></span> <span data-ttu-id="63dbd-196">Daha fazla bilgi için bkz. [.NET Core uygulaması yayımlama](../deploying/index.md) ve [.NET Core CLI .NET Core uygulamaları](../deploying/deploy-with-cli.md)yayımlama.</span><span class="sxs-lookup"><span data-stu-id="63dbd-196">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

  <span data-ttu-id="63dbd-197">Bu seçenek veya belirtilmeden kullanılırsa, `true` `false` varsayılan olur `true` .</span><span class="sxs-lookup"><span data-stu-id="63dbd-197">If this option is used without specifying `true` or `false`, the default is `true`.</span></span> <span data-ttu-id="63dbd-198">Bu durumda, çözüm veya proje bağımsız değişkenini hemen sonra yerleştirmeyin `--self-contained` , çünkü `true` veya `false` Bu konumda beklenmez.</span><span class="sxs-lookup"><span data-stu-id="63dbd-198">In that case, don't put the solution or project argument immediately after `--self-contained`, because `true` or `false` is expected in that position.</span></span>

- **`--no-self-contained`**

  <span data-ttu-id="63dbd-199">İle eşdeğerdir `--self-contained false` .</span><span class="sxs-lookup"><span data-stu-id="63dbd-199">Equivalent to `--self-contained false`.</span></span> <span data-ttu-id="63dbd-200">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="63dbd-200">Available since .NET Core 3.0 SDK.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="63dbd-201">Uygulamayı belirli bir çalışma zamanı için yayımlar.</span><span class="sxs-lookup"><span data-stu-id="63dbd-201">Publishes the application for a given runtime.</span></span> <span data-ttu-id="63dbd-202">Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="63dbd-202">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="63dbd-203">Daha fazla bilgi için bkz. [.NET Core uygulaması yayımlama](../deploying/index.md) ve [.NET Core CLI .NET Core uygulamaları](../deploying/deploy-with-cli.md)yayımlama.</span><span class="sxs-lookup"><span data-stu-id="63dbd-203">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="63dbd-204">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="63dbd-204">Sets the verbosity level of the command.</span></span> <span data-ttu-id="63dbd-205">İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="63dbd-205">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="63dbd-206">Varsayılan değer `minimal` .</span><span class="sxs-lookup"><span data-stu-id="63dbd-206">Default value is `minimal`.</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="63dbd-207">Proje dosyasının sürüm alanındaki yıldız işaretini () değiştirecek olan sürüm sonekini tanımlar `*` .</span><span class="sxs-lookup"><span data-stu-id="63dbd-207">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

## <a name="examples"></a><span data-ttu-id="63dbd-208">Örnekler</span><span class="sxs-lookup"><span data-stu-id="63dbd-208">Examples</span></span>

- <span data-ttu-id="63dbd-209">Geçerli dizindeki proje için [çalışma zamanına bağımlı platformlar arası ikili](../deploying/index.md#produce-a-cross-platform-binary) oluşturun:</span><span class="sxs-lookup"><span data-stu-id="63dbd-209">Create a [runtime-dependent cross-platform binary](../deploying/index.md#produce-a-cross-platform-binary) for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet publish
  ```

  <span data-ttu-id="63dbd-210">.NET Core 3,0 SDK ile başlayarak bu örnek ayrıca geçerli platform için [çalışma zamanına bağlı bir yürütülebilir dosya](../deploying/index.md#publish-runtime-dependent) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="63dbd-210">Starting with .NET Core 3.0 SDK, this example also creates a [runtime-dependent executable](../deploying/index.md#publish-runtime-dependent) for the current platform.</span></span>

- <span data-ttu-id="63dbd-211">Belirli bir çalışma zamanı için geçerli dizindeki proje için [kendi kendine içerilen bir yürütülebilir dosya](../deploying/index.md#publish-self-contained) oluşturun:</span><span class="sxs-lookup"><span data-stu-id="63dbd-211">Create a [self-contained executable](../deploying/index.md#publish-self-contained) for the project in the current directory, for a specific runtime:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64
  ```

  <span data-ttu-id="63dbd-212">RID proje dosyasında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="63dbd-212">The RID must be in the project file.</span></span>

- <span data-ttu-id="63dbd-213">Belirli bir platform için geçerli dizindeki proje için [çalışma zamanına bağımlı bir yürütülebilir dosya](../deploying/index.md#publish-runtime-dependent) oluşturun:</span><span class="sxs-lookup"><span data-stu-id="63dbd-213">Create a [runtime-dependent executable](../deploying/index.md#publish-runtime-dependent) for the project in the current directory, for a specific platform:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64 --self-contained false
  ```

  <span data-ttu-id="63dbd-214">RID proje dosyasında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="63dbd-214">The RID must be in the project file.</span></span> <span data-ttu-id="63dbd-215">Bu örnek .NET Core 3,0 SDK ve sonraki sürümleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="63dbd-215">This example applies to .NET Core 3.0 SDK and later versions.</span></span>

- <span data-ttu-id="63dbd-216">Projeyi, belirli bir çalışma zamanı ve hedef çerçeve için geçerli dizinde yayımlayın:</span><span class="sxs-lookup"><span data-stu-id="63dbd-216">Publish the project in the current directory, for a specific runtime and target framework:</span></span>

  ```dotnetcli
  dotnet publish --framework netcoreapp3.1 --runtime osx.10.11-x64
  ```

- <span data-ttu-id="63dbd-217">Belirtilen proje dosyasını Yayımla:</span><span class="sxs-lookup"><span data-stu-id="63dbd-217">Publish the specified project file:</span></span>

  ```dotnetcli
  dotnet publish ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="63dbd-218">Geçerli uygulamayı yayımlayın ancak projeden projeye (P2P) başvurularını geri yüklemeyin, ancak geri yükleme işlemi sırasında yalnızca kök proje:</span><span class="sxs-lookup"><span data-stu-id="63dbd-218">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation:</span></span>

  ```dotnetcli
  dotnet publish --no-dependencies
  ```

## <a name="see-also"></a><span data-ttu-id="63dbd-219">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="63dbd-219">See also</span></span>

- [<span data-ttu-id="63dbd-220">.NET Core uygulama yayımlamaya genel bakış</span><span class="sxs-lookup"><span data-stu-id="63dbd-220">.NET Core application publishing overview</span></span>](../deploying/index.md)
- [<span data-ttu-id="63dbd-221">.NET Core CLI .NET Core uygulamaları yayımlayın</span><span class="sxs-lookup"><span data-stu-id="63dbd-221">Publish .NET Core apps with the .NET Core CLI</span></span>](../deploying/deploy-with-cli.md)
- [<span data-ttu-id="63dbd-222">Hedef çerçeveler</span><span class="sxs-lookup"><span data-stu-id="63dbd-222">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="63dbd-223">Çalışma zamanı tanımlayıcı (RID) kataloğu</span><span class="sxs-lookup"><span data-stu-id="63dbd-223">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="63dbd-224">MacOS Catalina Notarle çalışma</span><span class="sxs-lookup"><span data-stu-id="63dbd-224">Working with macOS Catalina Notarization</span></span>](../install/macos-notarization-issues.md)
- [<span data-ttu-id="63dbd-225">Yayımlanan bir uygulamanın dizin yapısı</span><span class="sxs-lookup"><span data-stu-id="63dbd-225">Directory structure of a published application</span></span>](/aspnet/core/hosting/directory-structure)
- [<span data-ttu-id="63dbd-226">MSBuild komut satırı başvurusu</span><span class="sxs-lookup"><span data-stu-id="63dbd-226">MSBuild command-line reference</span></span>](/visualstudio/msbuild/msbuild-command-line-reference)
- [<span data-ttu-id="63dbd-227">ASP.NET Core uygulama dağıtımı için Visual Studio yayımlama profilleri (. pubxml)</span><span class="sxs-lookup"><span data-stu-id="63dbd-227">Visual Studio publish profiles (.pubxml) for ASP.NET Core app deployment</span></span>](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [<span data-ttu-id="63dbd-228">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="63dbd-228">dotnet msbuild</span></span>](dotnet-msbuild.md)
- [<span data-ttu-id="63dbd-229">Illınk. Tasks</span><span class="sxs-lookup"><span data-stu-id="63dbd-229">ILLInk.Tasks</span></span>](https://aka.ms/dotnet-illink)
