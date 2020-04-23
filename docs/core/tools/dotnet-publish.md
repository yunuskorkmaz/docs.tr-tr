---
title: dotnet yayımlama komutu
description: Dotnet yayımlama komutu bir .NET Core projesi veya çözüm bir dizine yayımlar.
ms.date: 02/24/2020
ms.openlocfilehash: 78ed8098be1b6887fc6a2a647fd169e2bf7f7fd1
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102807"
---
# <a name="dotnet-publish"></a><span data-ttu-id="83990-103">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="83990-103">dotnet publish</span></span>

<span data-ttu-id="83990-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 2.1 SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="83990-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="83990-105">Adı</span><span class="sxs-lookup"><span data-stu-id="83990-105">Name</span></span>

<span data-ttu-id="83990-106">`dotnet publish`- Uygulama ve bağımlılıklarını barındırma sistemine dağıtım için bir klasöre yayımlar.</span><span class="sxs-lookup"><span data-stu-id="83990-106">`dotnet publish` - Publishes the application and its dependencies to a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="83990-107">Özet</span><span class="sxs-lookup"><span data-stu-id="83990-107">Synopsis</span></span>

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

## <a name="description"></a><span data-ttu-id="83990-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="83990-108">Description</span></span>

<span data-ttu-id="83990-109">`dotnet publish`uygulamayı derler, proje dosyasında belirtilen bağımlılıkları okur ve ortaya çıkan dosya kümesini bir dizine yayınlar.</span><span class="sxs-lookup"><span data-stu-id="83990-109">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="83990-110">Çıktı aşağıdaki varlıkları içerir:</span><span class="sxs-lookup"><span data-stu-id="83990-110">The output includes the following assets:</span></span>

- <span data-ttu-id="83990-111">*Dll* uzantılı bir derlemede Ara Dil (IL) kodu.</span><span class="sxs-lookup"><span data-stu-id="83990-111">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
- <span data-ttu-id="83990-112">Projenin tüm bağımlılıklarını içeren bir *.deps.json* dosyası.</span><span class="sxs-lookup"><span data-stu-id="83990-112">A *.deps.json* file that includes all of the dependencies of the project.</span></span>
- <span data-ttu-id="83990-113">Uygulamanın beklediği paylaşılan çalışma süresini ve çalışma zamanı için diğer yapılandırma seçeneklerini (örneğin, çöp toplama türü) belirten bir *.runtimeconfig.json* dosyası.</span><span class="sxs-lookup"><span data-stu-id="83990-113">A *.runtimeconfig.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
- <span data-ttu-id="83990-114">NuGet önbelleğinden çıktı klasörüne kopyalanan uygulamabağımlılıkları.</span><span class="sxs-lookup"><span data-stu-id="83990-114">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="83990-115">Komutun `dotnet publish` çıktısı yürütme için bir barındırma sistemine (örneğin, bir sunucu, PC, Mac, dizüstü bilgisayar) dağıtım için hazırdır.</span><span class="sxs-lookup"><span data-stu-id="83990-115">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="83990-116">Uygulamayı dağıtıma hazırlamak için resmi olarak desteklenen tek yol bu.</span><span class="sxs-lookup"><span data-stu-id="83990-116">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="83990-117">Projenin belirttiği dağıtım türüne bağlı olarak, barındırma sistemi .NET Core paylaşılan çalışma zamanı yüklü olabilir veya olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="83990-117">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="83990-118">Daha fazla bilgi için [bkz.](../deploying/deploy-with-cli.md)</span><span class="sxs-lookup"><span data-stu-id="83990-118">For more information, see [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="83990-119">Örtük geri yükleme</span><span class="sxs-lookup"><span data-stu-id="83990-119">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

### <a name="msbuild"></a><span data-ttu-id="83990-120">MSBuild</span><span class="sxs-lookup"><span data-stu-id="83990-120">MSBuild</span></span>

<span data-ttu-id="83990-121">Komut, `dotnet publish` hedefi çağıran MSBuild'i `Publish` çağırır.</span><span class="sxs-lookup"><span data-stu-id="83990-121">The `dotnet publish` command calls MSBuild, which invokes the `Publish` target.</span></span> <span data-ttu-id="83990-122">Geçirilen parametreler `dotnet publish` MSBuild'e geçirilir.</span><span class="sxs-lookup"><span data-stu-id="83990-122">Any parameters passed to `dotnet publish` are passed to MSBuild.</span></span> <span data-ttu-id="83990-123">Ve `-c` `-o` parametreler, sırasıyla MSBuild'in `Configuration` ve `OutputPath` özelliklerinin eşlenir.</span><span class="sxs-lookup"><span data-stu-id="83990-123">The `-c` and `-o` parameters map to MSBuild's `Configuration` and `OutputPath` properties, respectively.</span></span>

<span data-ttu-id="83990-124">Komut, `dotnet publish` özellikleri ayarlama ve `-p` `-l` logger tanımlama gibi MSBuild seçeneklerini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="83990-124">The `dotnet publish` command accepts MSBuild options, such as `-p` for setting properties and `-l` to define a logger.</span></span> <span data-ttu-id="83990-125">Örneğin, biçimi kullanarak bir MSBuild özelliği ayarlayabilirsiniz: `-p:<NAME>=<VALUE>`.</span><span class="sxs-lookup"><span data-stu-id="83990-125">For example, you can set an MSBuild property by using the format: `-p:<NAME>=<VALUE>`.</span></span> <span data-ttu-id="83990-126">Yayımlamayla ilgili özellikleri, örneğin bir *.pubxml* dosyasına atıfta bulunarak da ayarlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="83990-126">You can also set publish-related properties by referring to a *.pubxml* file, for example:</span></span>

```dotnetcli
dotnet publish -p:PublishProfile=Properties\PublishProfiles\FolderProfile.pubxml
```

<span data-ttu-id="83990-127">Daha fazla bilgi için aşağıdaki kaynaklara bakın:</span><span class="sxs-lookup"><span data-stu-id="83990-127">For more information, see the following resources:</span></span>

- [<span data-ttu-id="83990-128">MSBuild komut satırı başvurusu</span><span class="sxs-lookup"><span data-stu-id="83990-128">MSBuild command-line reference</span></span>](/visualstudio/msbuild/msbuild-command-line-reference)
- [<span data-ttu-id="83990-129">Visual Studio ASP.NET Core uygulama dağıtımı için profilleri (.pubxml) yayınlamak</span><span class="sxs-lookup"><span data-stu-id="83990-129">Visual Studio publish profiles (.pubxml) for ASP.NET Core app deployment</span></span>](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [<span data-ttu-id="83990-130">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="83990-130">dotnet msbuild</span></span>](dotnet-msbuild.md)

## <a name="arguments"></a><span data-ttu-id="83990-131">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="83990-131">Arguments</span></span>

- **`PROJECT|SOLUTION`**

  <span data-ttu-id="83990-132">Yayımlanmak için proje veya çözüm.</span><span class="sxs-lookup"><span data-stu-id="83990-132">The project or solution to publish.</span></span>
  
  * <span data-ttu-id="83990-133">`PROJECT`[C#](csproj.md), F#veya Visual Basic proje dosyasının yolu ve dosya adı veya C#, F#veya Visual Basic proje dosyası içeren bir dizine giden yoldur.</span><span class="sxs-lookup"><span data-stu-id="83990-133">`PROJECT` is the path and filename of a [C#](csproj.md), F#, or Visual Basic project file, or the path to a directory that contains a C#, F#, or Visual Basic project file.</span></span> <span data-ttu-id="83990-134">Dizin belirtilmemişse, geçerli dizine varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="83990-134">If the directory is not specified, it defaults to the current directory.</span></span>

  * <span data-ttu-id="83990-135">`SOLUTION`çözüm dosyasının *(.sln* uzantısı) veya çözüm dosyası içeren bir dizine giden yol ve dosya adıdır.</span><span class="sxs-lookup"><span data-stu-id="83990-135">`SOLUTION` is the path and filename of a solution file (*.sln* extension), or the path to a directory that contains a solution file.</span></span> <span data-ttu-id="83990-136">Dizin belirtilmemişse, geçerli dizine varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="83990-136">If the directory is not specified, it defaults to the current directory.</span></span> <span data-ttu-id="83990-137">.NET Core 3.0 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="83990-137">Available since .NET Core 3.0 SDK.</span></span>

## <a name="options"></a><span data-ttu-id="83990-138">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="83990-138">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="83990-139">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="83990-139">Defines the build configuration.</span></span> <span data-ttu-id="83990-140">Çoğu proje için `Debug`varsayılan değer, ancak projenizdeki yapı yapılandırma ayarlarını geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83990-140">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="83990-141">Belirtilen [hedef çerçeve](../../standard/frameworks.md)için uygulama yayımlar.</span><span class="sxs-lookup"><span data-stu-id="83990-141">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="83990-142">Proje dosyasındaki hedef çerçeveyi belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="83990-142">You must specify the target framework in the project file.</span></span>

- **`--force`**

  <span data-ttu-id="83990-143">Son geri yükleme başarılı olsa bile tüm bağımlılıkları çözüme kavuşturmaya zorlar.</span><span class="sxs-lookup"><span data-stu-id="83990-143">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="83990-144">Bu bayrağı *belirtmek, project.assets.json* dosyasını silmekle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="83990-144">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="83990-145">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="83990-145">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="83990-146">Komutun durmasını ve kullanıcı girişi veya eylemini beklemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="83990-146">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="83990-147">Örneğin, kimlik doğrulamasını tamamlamak için.</span><span class="sxs-lookup"><span data-stu-id="83990-147">For example, to complete authentication.</span></span> <span data-ttu-id="83990-148">.NET Core 3.0 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="83990-148">Available since .NET Core 3.0 SDK.</span></span>

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  <span data-ttu-id="83990-149">Uygulamayla birlikte yayınlanan paket kümesini kırpmak için kullanılacak bir veya birkaç [hedef bildirimi](../deploying/runtime-store.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="83990-149">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="83990-150">Bildirim dosyası [ `dotnet store` komutun](dotnet-store.md)çıktısının bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="83990-150">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="83990-151">Birden çok bildirim belirtmek `--manifest` için, her bildirim için bir seçenek ekleyin.</span><span class="sxs-lookup"><span data-stu-id="83990-151">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span>

- **`--no-build`**

  <span data-ttu-id="83990-152">Yayımlamadan önce projeyi oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="83990-152">Doesn't build the project before publishing.</span></span> <span data-ttu-id="83990-153">Ayrıca bayrağı da `--no-restore` örtülü olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="83990-153">It also implicitly sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="83990-154">Projeden projeye başvuruları yoksa ve yalnızca kök projeyi geri yükler.</span><span class="sxs-lookup"><span data-stu-id="83990-154">Ignores project-to-project references and only restores the root project.</span></span>

- **`--nologo`**

  <span data-ttu-id="83990-155">Başlangıç bayrağını veya telif hakkı iletisini görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="83990-155">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="83990-156">.NET Core 3.0 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="83990-156">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="83990-157">Komutu çalıştırırken örtük bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="83990-157">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="83990-158">Çıktı dizininin yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="83990-158">Specifies the path for the output directory.</span></span>
  
  <span data-ttu-id="83990-159">Belirtilmemişse, çalışma süresine bağlı yürütülebilir ve platform lar arası ikili ler için *[project_file_folder]./bin/[configuration]/[framework]/publish/* olarak varsayılan olarak geçer.</span><span class="sxs-lookup"><span data-stu-id="83990-159">If not specified, it defaults to *[project_file_folder]./bin/[configuration]/[framework]/publish/* for a runtime-dependent executable and cross-platform binaries.</span></span> <span data-ttu-id="83990-160">Kendi kendine yeten bir yürütülebilir için *[project_file_folder]/bin/[configuration]/[framework]/[runtime]/publish/* olarak varsayılan olarak</span><span class="sxs-lookup"><span data-stu-id="83990-160">It defaults to *[project_file_folder]/bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained executable.</span></span>

  <span data-ttu-id="83990-161">Bir web projesinde, çıktı klasörü proje klasöründeyse, ardışık `dotnet publish` komutlar iç içe olan çıktı klasörlerine neden olur.</span><span class="sxs-lookup"><span data-stu-id="83990-161">In a web project, if the output folder is in the project folder, successive `dotnet publish` commands result in nested output folders.</span></span> <span data-ttu-id="83990-162">Örneğin, proje klasörü *myproject*ise ve yayımlama çıktısı klasörü *myproject/publish*ise ve iki kez `dotnet publish` çalıştırın, ikinci çalıştırma *myproject/publish/publish* *'e .config* ve *.json* dosyaları gibi içerik dosyalarını koyar.</span><span class="sxs-lookup"><span data-stu-id="83990-162">For example, if the project folder is *myproject*, and the publish output folder is *myproject/publish*, and you run `dotnet publish` twice, the second run puts content files such as *.config* and *.json* files in *myproject/publish/publish*.</span></span> <span data-ttu-id="83990-163">Yayımlama klasörlerini iç içe geçmemek için, doğrudan proje klasörü altında olmayan bir yayımlama klasörü belirtin veya yayımlama klasörünü projeden hariç tarayın.</span><span class="sxs-lookup"><span data-stu-id="83990-163">To avoid nesting publish folders, specify a publish folder that is not directly under the project folder, or exclude the publish folder from the project.</span></span> <span data-ttu-id="83990-164">Publishoutput adlı bir *yayımlama*klasörünü dışlamak `PropertyGroup` için *.csproj* dosyasındaki bir öğeye aşağıdaki öğeyi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="83990-164">To exclude a publish folder named *publishoutput*, add the following element to a `PropertyGroup` element in the *.csproj* file:</span></span>

  ```xml
  <DefaultItemExcludes>$(DefaultItemExcludes);publishoutput**</DefaultItemExcludes>
  ```

  - <span data-ttu-id="83990-165">.NET Core 3.x SDK ve sonrası</span><span class="sxs-lookup"><span data-stu-id="83990-165">.NET Core 3.x SDK and later</span></span>
  
    <span data-ttu-id="83990-166">Proje yayımlanırken göreceli bir yol belirtilirse, oluşturulan çıktı dizini proje dosyası konumuna değil, geçerli çalışma dizinine göredir.</span><span class="sxs-lookup"><span data-stu-id="83990-166">If a relative path is specified when publishing a project, the output directory generated is relative to the current working directory, not to the project file location.</span></span>

    <span data-ttu-id="83990-167">Çözüm yayımlanırken göreceli bir yol belirtilirse, tüm projelerin tüm çıktıları geçerli çalışma dizinine göre belirtilen klasöre gider.</span><span class="sxs-lookup"><span data-stu-id="83990-167">If a relative path is specified when publishing a solution, all output for all projects goes into the specified folder relative to the current working directory.</span></span> <span data-ttu-id="83990-168">Yayımlama çıktısının her proje için ayrı klasörlere gitmesini sağlamak için, seçenek yerine msbuild `PublishDir` özelliğini kullanarak göreli bir yol belirtin. `--output`</span><span class="sxs-lookup"><span data-stu-id="83990-168">To make publish output go to separate folders for each project, specify a relative path by using the msbuild `PublishDir` property instead of the `--output` option.</span></span> <span data-ttu-id="83990-169">Örneğin, `dotnet publish -p:PublishDir=.\publish` her proje için yayımçıktısını proje dosyasını içeren klasörün altındaki klasöre `publish` gönderir.</span><span class="sxs-lookup"><span data-stu-id="83990-169">For example, `dotnet publish -p:PublishDir=.\publish` sends publish output for each project to a `publish` folder under the folder that contains the project file.</span></span>

  - <span data-ttu-id="83990-170">.NET Çekirdek 2.x SDK</span><span class="sxs-lookup"><span data-stu-id="83990-170">.NET Core 2.x SDK</span></span>
  
    <span data-ttu-id="83990-171">Proje yayımlanırken göreceli bir yol belirtilirse, oluşturulan çıktı dizini geçerli çalışma dizinine değil, proje dosyası konumuna göredir.</span><span class="sxs-lookup"><span data-stu-id="83990-171">If a relative path is specified when publishing a project, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

    <span data-ttu-id="83990-172">Çözüm yayımlanırken göreli bir yol belirtilirse, her projenin çıktısı proje dosyası konumuna göre ayrı bir klasöre gider.</span><span class="sxs-lookup"><span data-stu-id="83990-172">If a relative path is specified when publishing a solution, each project's output goes into a separate folder relative to the project file location.</span></span> <span data-ttu-id="83990-173">Bir çözüm yayımlanırken mutlak bir yol belirtilirse, tüm projeler için çıktı yayımlamak belirtilen klasöre gider.</span><span class="sxs-lookup"><span data-stu-id="83990-173">If an absolute path is specified when publishing a solution, all publish output for all projects goes into the specified folder.</span></span>

- **`-p:PublishReadyToRun=true`**

  <span data-ttu-id="83990-174">Uygulama derlemelerini ReadyToRun (R2R) biçiminde derler.</span><span class="sxs-lookup"><span data-stu-id="83990-174">Compiles application assemblies as ReadyToRun (R2R) format.</span></span> <span data-ttu-id="83990-175">R2R, ileri zaman (AOT) derlemesinin bir şeklidir.</span><span class="sxs-lookup"><span data-stu-id="83990-175">R2R is a form of ahead-of-time (AOT) compilation.</span></span> <span data-ttu-id="83990-176">Daha fazla bilgi için [ReadyToRun resimlerine](../whats-new/dotnet-core-3-0.md#readytorun-images)bakın.</span><span class="sxs-lookup"><span data-stu-id="83990-176">For more information, see [ReadyToRun images](../whats-new/dotnet-core-3-0.md#readytorun-images).</span></span> <span data-ttu-id="83990-177">.NET Core 3.0 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="83990-177">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="83990-178">Bu seçeneği komut satırında değil, bir yayımlama profilinde belirtmenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="83990-178">We recommend that you specify this option in a publish profile rather than on the command line.</span></span> <span data-ttu-id="83990-179">Daha fazla bilgi için [MSBuild'e](#msbuild)bakın.</span><span class="sxs-lookup"><span data-stu-id="83990-179">For more information, see [MSBuild](#msbuild).</span></span>

- **`-p:PublishSingleFile=true`**

  <span data-ttu-id="83990-180">Uygulamayı platforma özgü tek dosyalı çalıştırılabilir olarak paketler.</span><span class="sxs-lookup"><span data-stu-id="83990-180">Packages the app into a platform-specific single-file executable.</span></span> <span data-ttu-id="83990-181">Yürütülebilir kendi kendini ayıklama ve uygulamayı çalıştırmak için gerekli olan tüm bağımlılıkları (yerel dahil) içerir.</span><span class="sxs-lookup"><span data-stu-id="83990-181">The executable is self-extracting and contains all dependencies (including native) that are required to run the app.</span></span> <span data-ttu-id="83990-182">Uygulama ilk çalıştırıldığında, uygulama uygulama adına ve yapı tanımlayıcısına göre bir dizine ayıklanır.</span><span class="sxs-lookup"><span data-stu-id="83990-182">When the app is first run, the application is extracted to a directory based on the app name and build identifier.</span></span> <span data-ttu-id="83990-183">Uygulama yeniden çalıştırıldığında başlatma daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="83990-183">Startup is faster when the application is run again.</span></span> <span data-ttu-id="83990-184">Yeni bir sürüm kullanılmadığı sürece uygulamanın kendisini ikinci kez ayıklaması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="83990-184">The application doesn't need to extract itself a second time unless a new version is used.</span></span> <span data-ttu-id="83990-185">.NET Core 3.0 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="83990-185">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="83990-186">Tek dosyalı yayımlama hakkında daha fazla bilgi için [tek dosyalı paketleyici tasarım belgesine](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="83990-186">For more information about single-file publishing, see the [single-file bundler design document](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md).</span></span>

  <span data-ttu-id="83990-187">Bu seçeneği komut satırında değil, bir yayımlama profilinde belirtmenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="83990-187">We recommend that you specify this option in a publish profile rather than on the command line.</span></span> <span data-ttu-id="83990-188">Daha fazla bilgi için [MSBuild'e](#msbuild)bakın.</span><span class="sxs-lookup"><span data-stu-id="83990-188">For more information, see [MSBuild](#msbuild).</span></span>

- **`-p:PublishTrimmed=true`**

  <span data-ttu-id="83990-189">Kendi kendine yeten bir yürütücü yayımlarken uygulamanın dağıtım boyutunu azaltmak için kullanılmayan kitaplıkları kırpıyor.</span><span class="sxs-lookup"><span data-stu-id="83990-189">Trims unused libraries to reduce the deployment size of an app when publishing a self-contained executable.</span></span> <span data-ttu-id="83990-190">Daha fazla bilgi için, trim [bağımsız dağıtımlar ve yürütülebilir bakın.](../deploying/trim-self-contained.md)</span><span class="sxs-lookup"><span data-stu-id="83990-190">For more information, see [Trim self-contained deployments and executables](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="83990-191">.NET Core 3.0 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="83990-191">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="83990-192">Bu seçeneği komut satırında değil, bir yayımlama profilinde belirtmenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="83990-192">We recommend that you specify this option in a publish profile rather than on the command line.</span></span> <span data-ttu-id="83990-193">Daha fazla bilgi için [MSBuild'e](#msbuild)bakın.</span><span class="sxs-lookup"><span data-stu-id="83990-193">For more information, see [MSBuild](#msbuild).</span></span>

- **`--self-contained [true|false]`**

  <span data-ttu-id="83990-194">.NET Core çalışma zamanını uygulamanızla birlikte yayınlar, böylece çalışma süresinin hedef makineye yüklenmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="83990-194">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="83990-195">Varsayılan `true` değer, çalışma zamanı tanımlayıcısı belirtilmişse ve proje yürütülebilir bir projeyse (kitaplık projesi değil).</span><span class="sxs-lookup"><span data-stu-id="83990-195">Default is `true` if a runtime identifier is specified and the project is an executable project (not a library project).</span></span> <span data-ttu-id="83990-196">Daha fazla bilgi için [.NET Core uygulama yayımlama](../deploying/index.md) ve [.NET Core CLI ile .NET Core uygulamaları yayımlama](../deploying/deploy-with-cli.md)'ya bakın.</span><span class="sxs-lookup"><span data-stu-id="83990-196">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

  <span data-ttu-id="83990-197">Bu seçenek belirtilmeden `true` kullanılırsa veya `false` `true`varsayılan .</span><span class="sxs-lookup"><span data-stu-id="83990-197">If this option is used without specifying `true` or `false`, the default is `true`.</span></span> <span data-ttu-id="83990-198">Bu durumda, çözüm veya proje bağımsız değişkenini hemen sonra `--self-contained`koymayın, çünkü `true` bu `false` konumda bekleniyor.</span><span class="sxs-lookup"><span data-stu-id="83990-198">In that case, don't put the solution or project argument immediately after `--self-contained`, because `true` or `false` is expected in that position.</span></span>

- **`--no-self-contained`**

  <span data-ttu-id="83990-199">`--self-contained false`Eşdeğeri .</span><span class="sxs-lookup"><span data-stu-id="83990-199">Equivalent to `--self-contained false`.</span></span> <span data-ttu-id="83990-200">.NET Core 3.0 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="83990-200">Available since .NET Core 3.0 SDK.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="83990-201">Belirli bir çalışma zamanı için uygulamayı yayımlar.</span><span class="sxs-lookup"><span data-stu-id="83990-201">Publishes the application for a given runtime.</span></span> <span data-ttu-id="83990-202">Runtime Tanımlayıcıları (RID'ler) listesi için RID [kataloğuna](../rid-catalog.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="83990-202">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="83990-203">Daha fazla bilgi için [.NET Core uygulama yayımlama](../deploying/index.md) ve [.NET Core CLI ile .NET Core uygulamaları yayımlama](../deploying/deploy-with-cli.md)'ya bakın.</span><span class="sxs-lookup"><span data-stu-id="83990-203">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="83990-204">Komutun ayrıntılı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="83990-204">Sets the verbosity level of the command.</span></span> <span data-ttu-id="83990-205">İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve .</span><span class="sxs-lookup"><span data-stu-id="83990-205">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="83990-206">Varsayılan değer. `minimal`</span><span class="sxs-lookup"><span data-stu-id="83990-206">Default value is `minimal`.</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="83990-207">Proje dosyasının sürüm alanında yıldız işaretini`*`( ) değiştirmek için sürüm soneki tanımlar.</span><span class="sxs-lookup"><span data-stu-id="83990-207">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

## <a name="examples"></a><span data-ttu-id="83990-208">Örnekler</span><span class="sxs-lookup"><span data-stu-id="83990-208">Examples</span></span>

- <span data-ttu-id="83990-209">Geçerli dizinde proje için [çalışma süresine bağımlı çapraz platform ikilisi](../deploying/index.md#produce-a-cross-platform-binary) oluşturun:</span><span class="sxs-lookup"><span data-stu-id="83990-209">Create a [runtime-dependent cross-platform binary](../deploying/index.md#produce-a-cross-platform-binary) for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet publish
  ```

  <span data-ttu-id="83990-210">.NET Core 3.0 SDK ile başlayarak, bu örnek aynı zamanda geçerli platform için [çalıştırılabilir bir çalışma zamanı bağımlı](../deploying/index.md#publish-runtime-dependent) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="83990-210">Starting with .NET Core 3.0 SDK, this example also creates a [runtime-dependent executable](../deploying/index.md#publish-runtime-dependent) for the current platform.</span></span>

- <span data-ttu-id="83990-211">Belirli bir çalışma süresi için geçerli dizindeki proje için bağımsız bir [yürütülebilir](../deploying/index.md#publish-self-contained) oluşturun:</span><span class="sxs-lookup"><span data-stu-id="83990-211">Create a [self-contained executable](../deploying/index.md#publish-self-contained) for the project in the current directory, for a specific runtime:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64
  ```

  <span data-ttu-id="83990-212">RID proje dosyasında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="83990-212">The RID must be in the project file.</span></span>

- <span data-ttu-id="83990-213">Belirli bir platform için geçerli dizindeki proje için [çalışma süresine bağlı yürütülebilir bir çalıştırılmaz](../deploying/index.md#publish-runtime-dependent) oluşturun:</span><span class="sxs-lookup"><span data-stu-id="83990-213">Create a [runtime-dependent executable](../deploying/index.md#publish-runtime-dependent) for the project in the current directory, for a specific platform:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64 --self-contained false
  ```

  <span data-ttu-id="83990-214">RID proje dosyasında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="83990-214">The RID must be in the project file.</span></span> <span data-ttu-id="83990-215">Bu örnek .NET Core 3.0 SDK ve sonraki sürümler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="83990-215">This example applies to .NET Core 3.0 SDK and later versions.</span></span>

- <span data-ttu-id="83990-216">Belirli bir çalışma zamanı ve hedef çerçeve için projeyi geçerli dizinde yayımlayın:</span><span class="sxs-lookup"><span data-stu-id="83990-216">Publish the project in the current directory, for a specific runtime and target framework:</span></span>

  ```dotnetcli
  dotnet publish --framework netcoreapp3.1 --runtime osx.10.11-x64
  ```

- <span data-ttu-id="83990-217">Belirtilen proje dosyasını yayımlayın:</span><span class="sxs-lookup"><span data-stu-id="83990-217">Publish the specified project file:</span></span>

  ```dotnetcli
  dotnet publish ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="83990-218">Geçerli uygulamayı yayımlayın, ancak projeden projeye (P2P) başvurularını, yalnızca geri yükleme işlemi sırasındaki kök projeyi geri yüklemeyin:</span><span class="sxs-lookup"><span data-stu-id="83990-218">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation:</span></span>

  ```dotnetcli
  dotnet publish --no-dependencies
  ```

## <a name="see-also"></a><span data-ttu-id="83990-219">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="83990-219">See also</span></span>

- [<span data-ttu-id="83990-220">.NET Core uygulama yayıncılığı genel bakış</span><span class="sxs-lookup"><span data-stu-id="83990-220">.NET Core application publishing overview</span></span>](../deploying/index.md)
- [<span data-ttu-id="83990-221">.NET Core CLI ile .NET Core uygulamalarını yayımla</span><span class="sxs-lookup"><span data-stu-id="83990-221">Publish .NET Core apps with the .NET Core CLI</span></span>](../deploying/deploy-with-cli.md)
- [<span data-ttu-id="83990-222">Hedef çerçeveler</span><span class="sxs-lookup"><span data-stu-id="83990-222">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="83990-223">Çalışma Zamanı Tanımlayıcı (RID) kataloğu</span><span class="sxs-lookup"><span data-stu-id="83990-223">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="83990-224">macOS Catalina Noterizasyonu ile çalışma</span><span class="sxs-lookup"><span data-stu-id="83990-224">Working with macOS Catalina Notarization</span></span>](../install/macos-notarization-issues.md)
- [<span data-ttu-id="83990-225">Yayınlanan bir uygulamanın dizin yapısı</span><span class="sxs-lookup"><span data-stu-id="83990-225">Directory structure of a published application</span></span>](/aspnet/core/hosting/directory-structure)
- [<span data-ttu-id="83990-226">MSBuild komut satırı başvurusu</span><span class="sxs-lookup"><span data-stu-id="83990-226">MSBuild command-line reference</span></span>](/visualstudio/msbuild/msbuild-command-line-reference)
- [<span data-ttu-id="83990-227">Visual Studio ASP.NET Core uygulama dağıtımı için profilleri (.pubxml) yayınlamak</span><span class="sxs-lookup"><span data-stu-id="83990-227">Visual Studio publish profiles (.pubxml) for ASP.NET Core app deployment</span></span>](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [<span data-ttu-id="83990-228">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="83990-228">dotnet msbuild</span></span>](dotnet-msbuild.md)
- [<span data-ttu-id="83990-229">ILLInk.Görevleri</span><span class="sxs-lookup"><span data-stu-id="83990-229">ILLInk.Tasks</span></span>](https://aka.ms/dotnet-illink)
