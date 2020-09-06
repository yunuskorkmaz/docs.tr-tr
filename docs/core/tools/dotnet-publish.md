---
title: dotnet publish komutu
description: Dotnet publish komutu bir dizine .NET Core projesi veya çözümü yayımlar.
ms.date: 02/24/2020
ms.openlocfilehash: f171baaa0dbc070b6389ec0fa9895b2c5dcfafff
ms.sourcegitcommit: f279a4488c48236793c04bf825ae6f9128790849
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2020
ms.locfileid: "89501915"
---
# <a name="dotnet-publish"></a><span data-ttu-id="57dcc-103">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="57dcc-103">dotnet publish</span></span>

<span data-ttu-id="57dcc-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="57dcc-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="57dcc-105">Name</span><span class="sxs-lookup"><span data-stu-id="57dcc-105">Name</span></span>

<span data-ttu-id="57dcc-106">`dotnet publish` -Uygulamayı ve bağımlılıklarını barındırma sistemine dağıtım için bir klasöre yayımlar.</span><span class="sxs-lookup"><span data-stu-id="57dcc-106">`dotnet publish` - Publishes the application and its dependencies to a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="57dcc-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="57dcc-107">Synopsis</span></span>

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

## <a name="description"></a><span data-ttu-id="57dcc-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57dcc-108">Description</span></span>

<span data-ttu-id="57dcc-109">`dotnet publish` uygulamayı derler, proje dosyasında belirtilen bağımlılıklarını okur ve elde edilen dosya kümesini bir dizine yayınlar.</span><span class="sxs-lookup"><span data-stu-id="57dcc-109">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="57dcc-110">Çıktı aşağıdaki varlıkları içerir:</span><span class="sxs-lookup"><span data-stu-id="57dcc-110">The output includes the following assets:</span></span>

- <span data-ttu-id="57dcc-111">*DLL* uzantılı bir derlemede ara DIL (IL) kodu.</span><span class="sxs-lookup"><span data-stu-id="57dcc-111">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
- <span data-ttu-id="57dcc-112">Projenin tüm bağımlılıklarını içeren bir *.deps.js* dosyası.</span><span class="sxs-lookup"><span data-stu-id="57dcc-112">A *.deps.json* file that includes all of the dependencies of the project.</span></span>
- <span data-ttu-id="57dcc-113">Bir dosyada, uygulamanın beklediği paylaşılan çalışma zamanını belirten bir *.runtimeconfig.js* ve çalışma zamanına yönelik diğer yapılandırma seçenekleri (örneğin, çöp toplama türü).</span><span class="sxs-lookup"><span data-stu-id="57dcc-113">A *.runtimeconfig.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
- <span data-ttu-id="57dcc-114">NuGet önbelleğinden çıkış klasörüne kopyalanmış olan uygulamanın bağımlılıkları.</span><span class="sxs-lookup"><span data-stu-id="57dcc-114">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="57dcc-115">`dotnet publish`Komutun çıktısı, yürütme için bir barındırma sistemine (örneğin, bir sunucu, PC, Mac, dizüstü bilgisayar) dağıtıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="57dcc-115">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="57dcc-116">Uygulamayı dağıtıma hazırlamak için tek resmi olarak desteklenen bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="57dcc-116">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="57dcc-117">Projenin belirttiği dağıtımın türüne bağlı olarak, barındırma sisteminde .NET Core paylaşılan çalışma zamanı yüklü olabilir veya olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="57dcc-117">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="57dcc-118">Daha fazla bilgi için bkz. [.NET Core CLI .NET Core Apps yayımlama](../deploying/deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="57dcc-118">For more information, see [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="57dcc-119">Örtük geri yükleme</span><span class="sxs-lookup"><span data-stu-id="57dcc-119">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

### <a name="msbuild"></a><span data-ttu-id="57dcc-120">MSBuild</span><span class="sxs-lookup"><span data-stu-id="57dcc-120">MSBuild</span></span>

<span data-ttu-id="57dcc-121">`dotnet publish`Komutu, hedefi çağıran MSBuild 'i çağırır `Publish` .</span><span class="sxs-lookup"><span data-stu-id="57dcc-121">The `dotnet publish` command calls MSBuild, which invokes the `Publish` target.</span></span> <span data-ttu-id="57dcc-122">Öğesine geçirilen parametreler `dotnet publish` MSBuild 'e geçirilir.</span><span class="sxs-lookup"><span data-stu-id="57dcc-122">Any parameters passed to `dotnet publish` are passed to MSBuild.</span></span> <span data-ttu-id="57dcc-123">`-c`Ve `-o` parametreleri `Configuration` sırasıyla MSBuild ve özellikler ile eşlenir `PublishDir` .</span><span class="sxs-lookup"><span data-stu-id="57dcc-123">The `-c` and `-o` parameters map to MSBuild's `Configuration` and `PublishDir` properties, respectively.</span></span>

<span data-ttu-id="57dcc-124">`dotnet publish`Komut, `-p` özellikleri ayarlama ve bir günlükçü tanımlama gibi MSBuild seçeneklerini kabul eder `-l` .</span><span class="sxs-lookup"><span data-stu-id="57dcc-124">The `dotnet publish` command accepts MSBuild options, such as `-p` for setting properties and `-l` to define a logger.</span></span> <span data-ttu-id="57dcc-125">Örneğin, şu biçimi kullanarak bir MSBuild özelliği ayarlayabilirsiniz: `-p:<NAME>=<VALUE>` .</span><span class="sxs-lookup"><span data-stu-id="57dcc-125">For example, you can set an MSBuild property by using the format: `-p:<NAME>=<VALUE>`.</span></span>

<span data-ttu-id="57dcc-126">Ayrıca, bir *. pubxml* dosyasına (.net Core 3,1 SDK sürümünden itibaren kullanılabilir) başvurarak, yayınla ilgili özellikleri de ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="57dcc-126">You can also set publish-related properties by referring to a *.pubxml* file (available since .NET Core 3.1 SDK).</span></span> <span data-ttu-id="57dcc-127">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="57dcc-127">For example:</span></span>

```dotnetcli
dotnet publish -p:PublishProfile=FolderProfile
```

<span data-ttu-id="57dcc-128">Önceki örnekte, \* \<project_folder> /Properties/publishprofiles\* klasöründe bulunan *folderprofile. pubxml* dosyası kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="57dcc-128">The preceding example uses the *FolderProfile.pubxml* file that is found in the *\<project_folder>/Properties/PublishProfiles* folder.</span></span> <span data-ttu-id="57dcc-129">Özelliği ayarlarken bir yol ve dosya uzantısı belirtirseniz `PublishProfile` , bunlar yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="57dcc-129">If you specify a path and file extension when setting the `PublishProfile` property, they are ignored.</span></span> <span data-ttu-id="57dcc-130">MSBuild varsayılan olarak *Properties/PublishProfiles* klasörüne bakar ve *pubxml* dosya uzantısını varsayar.</span><span class="sxs-lookup"><span data-stu-id="57dcc-130">MSBuild by default looks in the *Properties/PublishProfiles* folder and assumes the *pubxml* file extension.</span></span> <span data-ttu-id="57dcc-131">Uzantısı dahil yolunu ve dosya adını belirtmek için özelliği `PublishProfileFullPath` yerine özelliği ayarlayın `PublishProfile` .</span><span class="sxs-lookup"><span data-stu-id="57dcc-131">To specify the path and filename including extension, set the `PublishProfileFullPath` property instead of the `PublishProfile` property.</span></span>

<span data-ttu-id="57dcc-132">Daha fazla bilgi için aşağıdaki kaynaklara bakın:</span><span class="sxs-lookup"><span data-stu-id="57dcc-132">For more information, see the following resources:</span></span>

- [<span data-ttu-id="57dcc-133">MSBuild komut satırı başvurusu</span><span class="sxs-lookup"><span data-stu-id="57dcc-133">MSBuild command-line reference</span></span>](/visualstudio/msbuild/msbuild-command-line-reference)
- [<span data-ttu-id="57dcc-134">ASP.NET Core uygulama dağıtımı için Visual Studio yayımlama profilleri (. pubxml)</span><span class="sxs-lookup"><span data-stu-id="57dcc-134">Visual Studio publish profiles (.pubxml) for ASP.NET Core app deployment</span></span>](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [<span data-ttu-id="57dcc-135">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="57dcc-135">dotnet msbuild</span></span>](dotnet-msbuild.md)

## <a name="arguments"></a><span data-ttu-id="57dcc-136">Arguments</span><span class="sxs-lookup"><span data-stu-id="57dcc-136">Arguments</span></span>

- **`PROJECT|SOLUTION`**

  <span data-ttu-id="57dcc-137">Yayımlanacak proje veya çözüm.</span><span class="sxs-lookup"><span data-stu-id="57dcc-137">The project or solution to publish.</span></span>
  
  * <span data-ttu-id="57dcc-138">`PROJECT` bir [C#](csproj.md), f # veya Visual Basic proje dosyasının yolu ve dosya adı ya da C#, f # veya Visual Basic proje dosyası içeren bir dizinin yoludur.</span><span class="sxs-lookup"><span data-stu-id="57dcc-138">`PROJECT` is the path and filename of a [C#](csproj.md), F#, or Visual Basic project file, or the path to a directory that contains a C#, F#, or Visual Basic project file.</span></span> <span data-ttu-id="57dcc-139">Dizin belirtilmemişse, varsayılan olarak geçerli dizine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="57dcc-139">If the directory is not specified, it defaults to the current directory.</span></span>

  * <span data-ttu-id="57dcc-140">`SOLUTION` , bir çözüm dosyasının (*. sln* uzantısının) yolu ve dosya adı veya çözüm dosyası içeren bir dizinin yoludur.</span><span class="sxs-lookup"><span data-stu-id="57dcc-140">`SOLUTION` is the path and filename of a solution file (*.sln* extension), or the path to a directory that contains a solution file.</span></span> <span data-ttu-id="57dcc-141">Dizin belirtilmemişse, varsayılan olarak geçerli dizine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="57dcc-141">If the directory is not specified, it defaults to the current directory.</span></span> <span data-ttu-id="57dcc-142">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="57dcc-142">Available since .NET Core 3.0 SDK.</span></span>

## <a name="options"></a><span data-ttu-id="57dcc-143">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="57dcc-143">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="57dcc-144">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="57dcc-144">Defines the build configuration.</span></span> <span data-ttu-id="57dcc-145">Çoğu proje için varsayılandır `Debug` , ancak projenizde derleme yapılandırma ayarlarını geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="57dcc-145">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="57dcc-146">Belirtilen [hedef çerçeve](../../standard/frameworks.md)için uygulamayı yayımlar.</span><span class="sxs-lookup"><span data-stu-id="57dcc-146">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="57dcc-147">Hedef çerçeveyi proje dosyasında belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="57dcc-147">You must specify the target framework in the project file.</span></span>

- **`--force`**

  <span data-ttu-id="57dcc-148">Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar.</span><span class="sxs-lookup"><span data-stu-id="57dcc-148">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="57dcc-149">Bu bayrağın belirtilmesi, dosyadaki *project.assets.js* silme ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="57dcc-149">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="57dcc-150">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="57dcc-150">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="57dcc-151">Komutun Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="57dcc-151">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="57dcc-152">Örneğin, kimlik doğrulamasını tamamlamaya yönelik.</span><span class="sxs-lookup"><span data-stu-id="57dcc-152">For example, to complete authentication.</span></span> <span data-ttu-id="57dcc-153">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="57dcc-153">Available since .NET Core 3.0 SDK.</span></span>

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  <span data-ttu-id="57dcc-154">Uygulamayla yayımlanmış paket kümesini kırpmak için kullanılacak bir veya birkaç [hedef bildirimi](../deploying/runtime-store.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="57dcc-154">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="57dcc-155">Bildirim dosyası, [ `dotnet store` komutun](dotnet-store.md)çıktısının bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="57dcc-155">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="57dcc-156">Birden çok bildirim belirtmek için `--manifest` her bildirim için bir seçenek ekleyin.</span><span class="sxs-lookup"><span data-stu-id="57dcc-156">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span>

- **`--no-build`**

  <span data-ttu-id="57dcc-157">Yayımlamadan önce projeyi oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="57dcc-157">Doesn't build the project before publishing.</span></span> <span data-ttu-id="57dcc-158">Ayrıca bayrağı örtülü olarak ayarlar `--no-restore` .</span><span class="sxs-lookup"><span data-stu-id="57dcc-158">It also implicitly sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="57dcc-159">Projeden projeye başvuruları yoksayar ve yalnızca kök projeyi geri yükler.</span><span class="sxs-lookup"><span data-stu-id="57dcc-159">Ignores project-to-project references and only restores the root project.</span></span>

- **`--nologo`**

  <span data-ttu-id="57dcc-160">Başlangıç başlığını veya telif hakkı iletisini görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="57dcc-160">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="57dcc-161">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="57dcc-161">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="57dcc-162">Komutu çalıştırılırken örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="57dcc-162">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="57dcc-163">Çıkış dizini için yolu belirtir.</span><span class="sxs-lookup"><span data-stu-id="57dcc-163">Specifies the path for the output directory.</span></span>
  
  <span data-ttu-id="57dcc-164">Belirtilmemişse, çerçeveye bağlı bir yürütülebilir dosya ve platformlar arası ikili dosyalar için *[project_file_folder]/bin/[Configuration]/[Framework]/Publish/* varsayılan değeri.</span><span class="sxs-lookup"><span data-stu-id="57dcc-164">If not specified, it defaults to *[project_file_folder]/bin/[configuration]/[framework]/publish/* for a framework-dependent executable and cross-platform binaries.</span></span> <span data-ttu-id="57dcc-165">Bu, kendi içinde bulunan yürütülebilir dosya için *[project_file_folder]/bin/[yapılandırma]/[Framework]/[Runtime]/Publish/* varsayılan değerini alır.</span><span class="sxs-lookup"><span data-stu-id="57dcc-165">It defaults to *[project_file_folder]/bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained executable.</span></span>

  <span data-ttu-id="57dcc-166">Bir Web projesinde, çıkış klasörü proje klasöründe ise, birbirini izleyen `dotnet publish` Komutlar iç içe geçmiş çıkış klasörlerine neden olur.</span><span class="sxs-lookup"><span data-stu-id="57dcc-166">In a web project, if the output folder is in the project folder, successive `dotnet publish` commands result in nested output folders.</span></span> <span data-ttu-id="57dcc-167">Örneğin, proje klasörü *projem ise*ve yayımlama çıkış klasörü *myprojem/Publish*ise ve `dotnet publish` iki kez çalıştırırsanız ikinci çalıştırma, *MyProject/Publish/Publish*içindeki *. config* ve *. JSON* dosyaları gibi içerik dosyalarını koyar.</span><span class="sxs-lookup"><span data-stu-id="57dcc-167">For example, if the project folder is *myproject*, and the publish output folder is *myproject/publish*, and you run `dotnet publish` twice, the second run puts content files such as *.config* and *.json* files in *myproject/publish/publish*.</span></span> <span data-ttu-id="57dcc-168">Yayımlama klasörlerinin iç içe geçirilmesi önlemek için, proje **klasörünün altında olmayan** bir yayımlama klasörü belirtin veya Yayımla klasörünü projeden dışlayın.</span><span class="sxs-lookup"><span data-stu-id="57dcc-168">To avoid nesting publish folders, specify a publish folder that is not **directly** under the project folder, or exclude the publish folder from the project.</span></span> <span data-ttu-id="57dcc-169">*Publishoutput*adlı bir yayımlama klasörünü dışlamak için, `PropertyGroup` *. csproj* dosyasındaki bir öğeye aşağıdaki öğeyi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="57dcc-169">To exclude a publish folder named *publishoutput*, add the following element to a `PropertyGroup` element in the *.csproj* file:</span></span>

  ```xml
  <DefaultItemExcludes>$(DefaultItemExcludes);publishoutput**</DefaultItemExcludes>
  ```

  - <span data-ttu-id="57dcc-170">.NET Core 3. x SDK ve üzeri</span><span class="sxs-lookup"><span data-stu-id="57dcc-170">.NET Core 3.x SDK and later</span></span>
  
    <span data-ttu-id="57dcc-171">Bir proje yayımlanırken göreli bir yol belirtilmişse, oluşturulan çıkış dizini proje dosyası konumuna değil geçerli çalışma dizinine göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="57dcc-171">If a relative path is specified when publishing a project, the output directory generated is relative to the current working directory, not to the project file location.</span></span>

    <span data-ttu-id="57dcc-172">Bir çözüm yayımlarken göreli bir yol belirtilmişse, tüm projeler için tüm çıktılar geçerli çalışma dizinine göre belirtilen klasöre gider.</span><span class="sxs-lookup"><span data-stu-id="57dcc-172">If a relative path is specified when publishing a solution, all output for all projects goes into the specified folder relative to the current working directory.</span></span> <span data-ttu-id="57dcc-173">Yayımla çıkışını her proje için ayrı klasörlere gitmesini sağlamak için, seçeneği yerine MSBuild özelliğini kullanarak göreli bir yol belirtin `PublishDir` `--output` .</span><span class="sxs-lookup"><span data-stu-id="57dcc-173">To make publish output go to separate folders for each project, specify a relative path by using the msbuild `PublishDir` property instead of the `--output` option.</span></span> <span data-ttu-id="57dcc-174">Örneğin, `dotnet publish -p:PublishDir=.\publish` her proje için yayımlama çıkışını `publish` Proje dosyasını içeren klasörün altındaki bir klasöre gönderir.</span><span class="sxs-lookup"><span data-stu-id="57dcc-174">For example, `dotnet publish -p:PublishDir=.\publish` sends publish output for each project to a `publish` folder under the folder that contains the project file.</span></span>

  - <span data-ttu-id="57dcc-175">.NET Core 2. x SDK</span><span class="sxs-lookup"><span data-stu-id="57dcc-175">.NET Core 2.x SDK</span></span>
  
    <span data-ttu-id="57dcc-176">Bir proje yayımlanırken göreli bir yol belirtilmişse, oluşturulan çıkış dizini geçerli çalışma dizinine değil, proje dosyası konumuna göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="57dcc-176">If a relative path is specified when publishing a project, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

    <span data-ttu-id="57dcc-177">Bir çözüm yayımlarken göreli bir yol belirtilmişse, her projenin çıktısı proje dosyası konumuna göre ayrı bir klasöre gider.</span><span class="sxs-lookup"><span data-stu-id="57dcc-177">If a relative path is specified when publishing a solution, each project's output goes into a separate folder relative to the project file location.</span></span> <span data-ttu-id="57dcc-178">Bir çözüm yayımlarken mutlak bir yol belirtilmişse, tüm projeler için tüm yayımlama çıkışları belirtilen klasöre gider.</span><span class="sxs-lookup"><span data-stu-id="57dcc-178">If an absolute path is specified when publishing a solution, all publish output for all projects goes into the specified folder.</span></span>

- **`-p:PublishReadyToRun=true`**

  <span data-ttu-id="57dcc-179">Uygulama derlemelerini ReadyToRun (R2R) biçimi olarak derler.</span><span class="sxs-lookup"><span data-stu-id="57dcc-179">Compiles application assemblies as ReadyToRun (R2R) format.</span></span> <span data-ttu-id="57dcc-180">R2R, bir süre öncesi (AOT) derleme biçimidir.</span><span class="sxs-lookup"><span data-stu-id="57dcc-180">R2R is a form of ahead-of-time (AOT) compilation.</span></span> <span data-ttu-id="57dcc-181">Daha fazla bilgi için bkz. [Readytorun görüntüleri](../whats-new/dotnet-core-3-0.md#readytorun-images).</span><span class="sxs-lookup"><span data-stu-id="57dcc-181">For more information, see [ReadyToRun images](../whats-new/dotnet-core-3-0.md#readytorun-images).</span></span> <span data-ttu-id="57dcc-182">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="57dcc-182">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="57dcc-183">Bu seçeneği, komut satırı yerine bir yayımlama profilinde belirtmenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="57dcc-183">We recommend that you specify this option in a publish profile rather than on the command line.</span></span> <span data-ttu-id="57dcc-184">Daha fazla bilgi için bkz. [MSBuild](#msbuild).</span><span class="sxs-lookup"><span data-stu-id="57dcc-184">For more information, see [MSBuild](#msbuild).</span></span>

- **`-p:PublishSingleFile=true`**

  <span data-ttu-id="57dcc-185">Uygulamayı platforma özgü bir tek dosya yürütülebilir dosyasına paketler.</span><span class="sxs-lookup"><span data-stu-id="57dcc-185">Packages the app into a platform-specific single-file executable.</span></span> <span data-ttu-id="57dcc-186">Yürütülebilir dosya kendiliğinden ayıklanıyor ve uygulamayı çalıştırmak için gerekli tüm bağımlılıkları (yerel dahil) içerir.</span><span class="sxs-lookup"><span data-stu-id="57dcc-186">The executable is self-extracting and contains all dependencies (including native) that are required to run the app.</span></span> <span data-ttu-id="57dcc-187">Uygulama ilk kez çalıştırıldığında uygulama adı ve derleme tanımlayıcısı temelinde bir dizine çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="57dcc-187">When the app is first run, the application is extracted to a directory based on the app name and build identifier.</span></span> <span data-ttu-id="57dcc-188">Uygulama yeniden çalıştırıldığında başlatma daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="57dcc-188">Startup is faster when the application is run again.</span></span> <span data-ttu-id="57dcc-189">Yeni bir sürüm kullanılmadığı takdirde uygulamanın kendisi ikinci kez ayıklanmasına gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="57dcc-189">The application doesn't need to extract itself a second time unless a new version is used.</span></span> <span data-ttu-id="57dcc-190">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="57dcc-190">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="57dcc-191">Tek dosya yayınlama hakkında daha fazla bilgi için bkz. [tek dosya paketcisi tasarım belgesi](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md).</span><span class="sxs-lookup"><span data-stu-id="57dcc-191">For more information about single-file publishing, see the [single-file bundler design document](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md).</span></span>

  <span data-ttu-id="57dcc-192">Bu seçeneği, komut satırı yerine bir yayımlama profilinde belirtmenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="57dcc-192">We recommend that you specify this option in a publish profile rather than on the command line.</span></span> <span data-ttu-id="57dcc-193">Daha fazla bilgi için bkz. [MSBuild](#msbuild).</span><span class="sxs-lookup"><span data-stu-id="57dcc-193">For more information, see [MSBuild](#msbuild).</span></span>

- **`-p:PublishTrimmed=true`**

  <span data-ttu-id="57dcc-194">Bağımsız bir yürütülebilir dosya yayımlarken uygulamanın dağıtım boyutunu azaltmak için kullanılmayan kitaplıkları kırpar.</span><span class="sxs-lookup"><span data-stu-id="57dcc-194">Trims unused libraries to reduce the deployment size of an app when publishing a self-contained executable.</span></span> <span data-ttu-id="57dcc-195">Daha fazla bilgi için bkz. [kendi kendine kapsanan dağıtımları ve yürütülebilir dosyaları kırpma](../deploying/trim-self-contained.md).</span><span class="sxs-lookup"><span data-stu-id="57dcc-195">For more information, see [Trim self-contained deployments and executables](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="57dcc-196">Bir önizleme özelliği olarak .NET Core 3,0 SDK sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="57dcc-196">Available since .NET Core 3.0 SDK as a preview feature.</span></span>

  <span data-ttu-id="57dcc-197">Bu seçeneği, komut satırı yerine bir yayımlama profilinde belirtmenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="57dcc-197">We recommend that you specify this option in a publish profile rather than on the command line.</span></span> <span data-ttu-id="57dcc-198">Daha fazla bilgi için bkz. [MSBuild](#msbuild).</span><span class="sxs-lookup"><span data-stu-id="57dcc-198">For more information, see [MSBuild](#msbuild).</span></span>

- **`--self-contained [true|false]`**

  <span data-ttu-id="57dcc-199">.NET Core çalışma zamanını uygulamanızla yayımlar, böylece çalışma zamanının hedef makinede yüklü olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="57dcc-199">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="57dcc-200">Varsayılan olarak, `true` bir çalışma zamanı tanımlayıcısı belirtilirse ve proje yürütülebilir bir projem ise (kitaplık projesi değil).</span><span class="sxs-lookup"><span data-stu-id="57dcc-200">Default is `true` if a runtime identifier is specified and the project is an executable project (not a library project).</span></span> <span data-ttu-id="57dcc-201">Daha fazla bilgi için bkz. [.NET Core uygulaması yayımlama](../deploying/index.md) ve [.NET Core CLI .NET Core uygulamaları](../deploying/deploy-with-cli.md)yayımlama.</span><span class="sxs-lookup"><span data-stu-id="57dcc-201">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

  <span data-ttu-id="57dcc-202">Bu seçenek veya belirtilmeden kullanılırsa, `true` `false` varsayılan olur `true` .</span><span class="sxs-lookup"><span data-stu-id="57dcc-202">If this option is used without specifying `true` or `false`, the default is `true`.</span></span> <span data-ttu-id="57dcc-203">Bu durumda, çözüm veya proje bağımsız değişkenini hemen sonra yerleştirmeyin `--self-contained` , çünkü `true` veya `false` Bu konumda beklenmez.</span><span class="sxs-lookup"><span data-stu-id="57dcc-203">In that case, don't put the solution or project argument immediately after `--self-contained`, because `true` or `false` is expected in that position.</span></span>

- **`--no-self-contained`**

  <span data-ttu-id="57dcc-204">İle eşdeğerdir `--self-contained false` .</span><span class="sxs-lookup"><span data-stu-id="57dcc-204">Equivalent to `--self-contained false`.</span></span> <span data-ttu-id="57dcc-205">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="57dcc-205">Available since .NET Core 3.0 SDK.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="57dcc-206">Uygulamayı belirli bir çalışma zamanı için yayımlar.</span><span class="sxs-lookup"><span data-stu-id="57dcc-206">Publishes the application for a given runtime.</span></span> <span data-ttu-id="57dcc-207">Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="57dcc-207">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="57dcc-208">Daha fazla bilgi için bkz. [.NET Core uygulaması yayımlama](../deploying/index.md) ve [.NET Core CLI .NET Core uygulamaları](../deploying/deploy-with-cli.md)yayımlama.</span><span class="sxs-lookup"><span data-stu-id="57dcc-208">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="57dcc-209">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="57dcc-209">Sets the verbosity level of the command.</span></span> <span data-ttu-id="57dcc-210">İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="57dcc-210">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="57dcc-211">Varsayılan değer `minimal` .</span><span class="sxs-lookup"><span data-stu-id="57dcc-211">Default value is `minimal`.</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="57dcc-212">Proje dosyasının sürüm alanındaki yıldız işaretini () değiştirecek olan sürüm sonekini tanımlar `*` .</span><span class="sxs-lookup"><span data-stu-id="57dcc-212">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

## <a name="examples"></a><span data-ttu-id="57dcc-213">Örnekler</span><span class="sxs-lookup"><span data-stu-id="57dcc-213">Examples</span></span>

- <span data-ttu-id="57dcc-214">Geçerli dizinde proje için [çerçeveye bağımlı platformlar arası ikili](../deploying/index.md#produce-a-cross-platform-binary) oluşturun:</span><span class="sxs-lookup"><span data-stu-id="57dcc-214">Create a [framework-dependent cross-platform binary](../deploying/index.md#produce-a-cross-platform-binary) for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet publish
  ```

  <span data-ttu-id="57dcc-215">.NET Core 3,0 SDK ile başlayarak bu örnek ayrıca geçerli platform için [çerçeveye bağlı bir yürütülebilir dosya](../deploying/index.md#publish-framework-dependent) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="57dcc-215">Starting with .NET Core 3.0 SDK, this example also creates a [framework-dependent executable](../deploying/index.md#publish-framework-dependent) for the current platform.</span></span>

- <span data-ttu-id="57dcc-216">Belirli bir çalışma zamanı için geçerli dizindeki proje için [kendi kendine içerilen bir yürütülebilir dosya](../deploying/index.md#publish-self-contained) oluşturun:</span><span class="sxs-lookup"><span data-stu-id="57dcc-216">Create a [self-contained executable](../deploying/index.md#publish-self-contained) for the project in the current directory, for a specific runtime:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64
  ```

  <span data-ttu-id="57dcc-217">RID proje dosyasında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="57dcc-217">The RID must be in the project file.</span></span>

- <span data-ttu-id="57dcc-218">Belirli bir platform için geçerli dizindeki proje için [çerçeveye bağlı bir yürütülebilir dosya](../deploying/index.md#publish-framework-dependent) oluşturun:</span><span class="sxs-lookup"><span data-stu-id="57dcc-218">Create a [framework-dependent executable](../deploying/index.md#publish-framework-dependent) for the project in the current directory, for a specific platform:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64 --self-contained false
  ```

  <span data-ttu-id="57dcc-219">RID proje dosyasında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="57dcc-219">The RID must be in the project file.</span></span> <span data-ttu-id="57dcc-220">Bu örnek .NET Core 3,0 SDK ve sonraki sürümleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="57dcc-220">This example applies to .NET Core 3.0 SDK and later versions.</span></span>

- <span data-ttu-id="57dcc-221">Projeyi, belirli bir çalışma zamanı ve hedef çerçeve için geçerli dizinde yayımlayın:</span><span class="sxs-lookup"><span data-stu-id="57dcc-221">Publish the project in the current directory, for a specific runtime and target framework:</span></span>

  ```dotnetcli
  dotnet publish --framework netcoreapp3.1 --runtime osx.10.11-x64
  ```

- <span data-ttu-id="57dcc-222">Belirtilen proje dosyasını Yayımla:</span><span class="sxs-lookup"><span data-stu-id="57dcc-222">Publish the specified project file:</span></span>

  ```dotnetcli
  dotnet publish ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="57dcc-223">Geçerli uygulamayı yayımlayın ancak projeden projeye (P2P) başvurularını geri yüklemeyin, ancak geri yükleme işlemi sırasında yalnızca kök proje:</span><span class="sxs-lookup"><span data-stu-id="57dcc-223">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation:</span></span>

  ```dotnetcli
  dotnet publish --no-dependencies
  ```

## <a name="see-also"></a><span data-ttu-id="57dcc-224">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="57dcc-224">See also</span></span>

- [<span data-ttu-id="57dcc-225">.NET Core uygulama yayımlamaya genel bakış</span><span class="sxs-lookup"><span data-stu-id="57dcc-225">.NET Core application publishing overview</span></span>](../deploying/index.md)
- [<span data-ttu-id="57dcc-226">.NET Core CLI .NET Core uygulamaları yayımlayın</span><span class="sxs-lookup"><span data-stu-id="57dcc-226">Publish .NET Core apps with the .NET Core CLI</span></span>](../deploying/deploy-with-cli.md)
- [<span data-ttu-id="57dcc-227">Hedef çerçeveler</span><span class="sxs-lookup"><span data-stu-id="57dcc-227">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="57dcc-228">Çalışma Zamanı Tanımlayıcısı (RID) kataloğu</span><span class="sxs-lookup"><span data-stu-id="57dcc-228">Runtime Identifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="57dcc-229">MacOS Catalina Notarle çalışma</span><span class="sxs-lookup"><span data-stu-id="57dcc-229">Working with macOS Catalina Notarization</span></span>](../install/macos-notarization-issues.md)
- [<span data-ttu-id="57dcc-230">Yayımlanan bir uygulamanın dizin yapısı</span><span class="sxs-lookup"><span data-stu-id="57dcc-230">Directory structure of a published application</span></span>](/aspnet/core/hosting/directory-structure)
- [<span data-ttu-id="57dcc-231">MSBuild komut satırı başvurusu</span><span class="sxs-lookup"><span data-stu-id="57dcc-231">MSBuild command-line reference</span></span>](/visualstudio/msbuild/msbuild-command-line-reference)
- [<span data-ttu-id="57dcc-232">ASP.NET Core uygulama dağıtımı için Visual Studio yayımlama profilleri (. pubxml)</span><span class="sxs-lookup"><span data-stu-id="57dcc-232">Visual Studio publish profiles (.pubxml) for ASP.NET Core app deployment</span></span>](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [<span data-ttu-id="57dcc-233">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="57dcc-233">dotnet msbuild</span></span>](dotnet-msbuild.md)
- [<span data-ttu-id="57dcc-234">Illınk. Tasks</span><span class="sxs-lookup"><span data-stu-id="57dcc-234">ILLInk.Tasks</span></span>](https://aka.ms/dotnet-illink)
