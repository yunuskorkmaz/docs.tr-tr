---
title: DotNet test komutu
description: DotNet test komutu, belirli bir projedeki birim testlerini yürütmek için kullanılır.
ms.date: 04/29/2020
ms.openlocfilehash: 911d10917c2262c0bd32ef30d48da0f85ac39a39
ms.sourcegitcommit: 1eae045421d9ea2bfc82aaccfa5b1ff1b8c9e0e4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/16/2020
ms.locfileid: "84803162"
---
# <a name="dotnet-test"></a><span data-ttu-id="e9e87-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="e9e87-103">dotnet test</span></span>

<span data-ttu-id="e9e87-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="e9e87-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="e9e87-105">Name</span><span class="sxs-lookup"><span data-stu-id="e9e87-105">Name</span></span>

<span data-ttu-id="e9e87-106">`dotnet test`-Birim testlerini yürütmek için kullanılan .NET test sürücüsü.</span><span class="sxs-lookup"><span data-stu-id="e9e87-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e9e87-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="e9e87-107">Synopsis</span></span>

```dotnetcli
dotnet test [<PROJECT> | <SOLUTION> | <DIRECTORY> | <DLL>]
    [-a|--test-adapter-path <PATH_TO_ADAPTER>] [--blame]
    [-c|--configuration <CONFIGURATION>]
    [--collect <DATA_COLLECTOR_FRIENDLY_NAME>]
    [-d|--diag <PATH_TO_DIAGNOSTICS_FILE>] [-f|--framework <FRAMEWORK>]
    [--filter <EXPRESSION>] [--interactive]
    [-l|--logger <LOGGER_URI/FRIENDLY_NAME>] [--no-build]
    [--nologo] [--no-restore] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--results-directory <PATH>] [--runtime <RUNTIME_IDENTIFIER>]
    [-s|--settings <SETTINGS_FILE>] [-t|--list-tests]
    [-v|--verbosity <LEVEL>] [[--] <RunSettings arguments>]

dotnet test -h|--help
```

## <a name="description"></a><span data-ttu-id="e9e87-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e9e87-108">Description</span></span>

<span data-ttu-id="e9e87-109">`dotnet test`Komut, belirli bir çözümde birim testlerini yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e9e87-109">The `dotnet test` command is used to execute unit tests in a given solution.</span></span> <span data-ttu-id="e9e87-110">`dotnet test`Komut çözümü oluşturur ve çözümdeki her test projesi için bir test ana bilgisayarı uygulaması çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="e9e87-110">The `dotnet test` command builds the solution and runs a test host application for each test project in the solution.</span></span> <span data-ttu-id="e9e87-111">Test ana bilgisayarı, test çerçevesini (örneğin, MSTest, NUnit veya xUnit) kullanarak belirtilen projedeki testleri yürütür ve her testin başarısını veya başarısızlığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="e9e87-111">The test host executes tests in the given project using a test framework, for example: MSTest, NUnit, or xUnit, and reports the success or failure of each test.</span></span> <span data-ttu-id="e9e87-112">Tüm testler başarılı olursa, Test Çalıştırıcısı çıkış kodu olarak 0 döndürür; Aksi takdirde, herhangi bir test başarısız olursa, 1 döndürür.</span><span class="sxs-lookup"><span data-stu-id="e9e87-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span>

<span data-ttu-id="e9e87-113">Çok hedefli projeler için testler hedeflenen her çerçeve için çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="e9e87-113">For multi-targeted projects, tests are run for each targeted framework.</span></span> <span data-ttu-id="e9e87-114">Test Konağı ve birim testi çerçevesi, NuGet paketleri olarak paketlenir ve proje için sıradan bağımlılıklar olarak geri yüklenir.</span><span class="sxs-lookup"><span data-stu-id="e9e87-114">The test host and the unit test framework are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="e9e87-115">Test projeleri, `<PackageReference>` Aşağıdaki örnek proje dosyasında görüldüğü gibi sıradan bir öğe kullanarak Test Çalıştırıcısı belirtir:</span><span class="sxs-lookup"><span data-stu-id="e9e87-115">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

<span data-ttu-id="e9e87-116">`Microsoft.NET.Test.Sdk`Test Konağı nerede, `xunit` Test çerçevesidir.</span><span class="sxs-lookup"><span data-stu-id="e9e87-116">Where `Microsoft.NET.Test.Sdk` is the test host, `xunit` is the test framework.</span></span> <span data-ttu-id="e9e87-117">Ve `xunit.runner.visualstudio` , xUnit Framework 'ün test ana bilgisayarı ile çalışmasına izin veren bir test bağdaştırıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="e9e87-117">And `xunit.runner.visualstudio` is a test adapter, which allows the xUnit framework to work with the test host.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="e9e87-118">Örtük geri yükleme</span><span class="sxs-lookup"><span data-stu-id="e9e87-118">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="e9e87-119">Arguments</span><span class="sxs-lookup"><span data-stu-id="e9e87-119">Arguments</span></span>

- **`PROJECT | SOLUTION | DIRECTORY | DLL`**

  - <span data-ttu-id="e9e87-120">Test projesinin yolu.</span><span class="sxs-lookup"><span data-stu-id="e9e87-120">Path to the test project.</span></span>
  - <span data-ttu-id="e9e87-121">Çözümün yolu.</span><span class="sxs-lookup"><span data-stu-id="e9e87-121">Path to the solution.</span></span>
  - <span data-ttu-id="e9e87-122">Proje veya çözüm içeren bir dizinin yolu.</span><span class="sxs-lookup"><span data-stu-id="e9e87-122">Path to a directory that contains a project or a solution.</span></span>
  - <span data-ttu-id="e9e87-123">Test projesi *. dll* dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="e9e87-123">Path to a test project *.dll* file.</span></span>

  <span data-ttu-id="e9e87-124">Belirtilmemişse, geçerli dizinde bir proje veya çözüm arar.</span><span class="sxs-lookup"><span data-stu-id="e9e87-124">If not specified, it searches for a project or a solution in the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="e9e87-125">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="e9e87-125">Options</span></span>

- **`-a|--test-adapter-path <PATH_TO_ADAPTER>`**

  <span data-ttu-id="e9e87-126">Ek test bağdaştırıcıları için aranacak bir dizin yolu.</span><span class="sxs-lookup"><span data-stu-id="e9e87-126">Path to a directory to be searched for additional test adapters.</span></span> <span data-ttu-id="e9e87-127">Yalnızca soneki olan *. dll* dosyaları `.TestAdapter.dll` denetlenir.</span><span class="sxs-lookup"><span data-stu-id="e9e87-127">Only *.dll* files with suffix `.TestAdapter.dll` are inspected.</span></span> <span data-ttu-id="e9e87-128">Belirtilmemişse, test *. dll* dizininde arama yapılır.</span><span class="sxs-lookup"><span data-stu-id="e9e87-128">If not specified, the directory of the test *.dll* is searched.</span></span>

- **`--blame`**

  <span data-ttu-id="e9e87-129">Testleri sorumluyu modunda çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="e9e87-129">Runs the tests in blame mode.</span></span> <span data-ttu-id="e9e87-130">Bu seçenek, test ana bilgisayarının kilitlenmesine neden olan sorunlu testleri yalıtmak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="e9e87-130">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="e9e87-131">Kilitlenme algılandığında, `TestResults/<Guid>/<Guid>_Sequence.xml` çökmeden önce çalıştırılan testlerin sırasını yakalayan bir sıra dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e9e87-131">When a crash is detected, it creates a sequence file in `TestResults/<Guid>/<Guid>_Sequence.xml` that captures the order of tests that were run before the crash.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="e9e87-132">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e9e87-132">Defines the build configuration.</span></span> <span data-ttu-id="e9e87-133">Varsayılan değer `Debug` , ancak projenizin yapılandırması bu varsayılan SDK ayarını geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="e9e87-133">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  <span data-ttu-id="e9e87-134">Test çalıştırması için veri toplayıcıyı etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e9e87-134">Enables data collector for the test run.</span></span> <span data-ttu-id="e9e87-135">Daha fazla bilgi için bkz. [test çalıştırmasını izleme ve çözümleme](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="e9e87-135">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>
  
  <span data-ttu-id="e9e87-136">.NET Core tarafından desteklenen herhangi bir platformda kod kapsamı toplamak için, [Kapak](https://github.com/coverlet-coverage/coverlet/blob/master/README.md) ' i yükleyip `--collect:"XPlat Code Coverage"` seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e9e87-136">To collect code coverage on any platform that is supported by .NET Core, install [Coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/README.md) and use the `--collect:"XPlat Code Coverage"` option.</span></span>

  <span data-ttu-id="e9e87-137">Windows üzerinde, seçeneğini kullanarak kod kapsamını toplayabilirsiniz `--collect "Code Coverage"` .</span><span class="sxs-lookup"><span data-stu-id="e9e87-137">On Windows, you can collect code coverage by using the `--collect "Code Coverage"` option.</span></span> <span data-ttu-id="e9e87-138">Bu seçenek, Visual Studio 2019 Enterprise 'ta açılabilen bir *. Coverage* dosyası üretir.</span><span class="sxs-lookup"><span data-stu-id="e9e87-138">This option generates a *.coverage* file, which can be opened in Visual Studio 2019 Enterprise.</span></span> <span data-ttu-id="e9e87-139">Daha fazla bilgi için bkz. [kod kapsamını kullanma](/visualstudio/test/using-code-coverage-to-determine-how-much-code-is-being-tested) ve [kod kapsamı analizini özelleştirme](/visualstudio/test/customizing-code-coverage-analysis).</span><span class="sxs-lookup"><span data-stu-id="e9e87-139">For more information, see [Use code coverage](/visualstudio/test/using-code-coverage-to-determine-how-much-code-is-being-tested) and [Customize code coverage analysis](/visualstudio/test/customizing-code-coverage-analysis).</span></span>

- **`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  <span data-ttu-id="e9e87-140">Test platformu için tanılama modunu sağlar ve belirtilen dosyaya ve bunun yanındaki dosyalara tanılama iletileri yazar.</span><span class="sxs-lookup"><span data-stu-id="e9e87-140">Enables diagnostic mode for the test platform and writes diagnostic messages to the specified file and to files next to it.</span></span> <span data-ttu-id="e9e87-141">İletileri günlüğe kaydeden işlem, `*.host_<date>.txt` Test ana bilgisayar günlüğü için ve veri toplayıcı günlüğü için oluşturulan dosyaları belirler `*.datacollector_<date>.txt` .</span><span class="sxs-lookup"><span data-stu-id="e9e87-141">The process that is logging the messages determines which files are created, such as `*.host_<date>.txt` for test host log, and `*.datacollector_<date>.txt` for data collector log.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="e9e87-142">`dotnet`Test ikilileri için veya .NET Framework test ana bilgisayarının kullanımını zorlar.</span><span class="sxs-lookup"><span data-stu-id="e9e87-142">Forces the use of `dotnet` or .NET Framework test host for the test binaries.</span></span> <span data-ttu-id="e9e87-143">Bu seçenek yalnızca kullanılacak ana bilgisayar türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="e9e87-143">This option only determines which type of host to use.</span></span> <span data-ttu-id="e9e87-144">Kullanılacak gerçek Framework sürümü, Test projesindeki *runtimeconfig.js* tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="e9e87-144">The actual framework version to be used is determined by the *runtimeconfig.json* of the test project.</span></span> <span data-ttu-id="e9e87-145">Belirtilmediğinde, [TargetFramework derleme özniteliği](/dotnet/api/system.runtime.versioning.targetframeworkattribute) konak türünü belirlemekte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e9e87-145">When not specified, the [TargetFramework assembly attribute](/dotnet/api/system.runtime.versioning.targetframeworkattribute) is used to determine the type of host.</span></span> <span data-ttu-id="e9e87-146">Bu öznitelik *. dll*' den çıkarılır .NET Framework ana bilgisayar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e9e87-146">When that attribute is stripped from the *.dll*, the .NET Framework host is used.</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="e9e87-147">Geçerli projede verilen ifadeyi kullanarak testleri filtreler.</span><span class="sxs-lookup"><span data-stu-id="e9e87-147">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="e9e87-148">Daha fazla bilgi için, [filtre seçeneği ayrıntıları](#filter-option-details) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e9e87-148">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="e9e87-149">Seçmeli birim testi filtrelemeyi kullanma hakkında daha fazla bilgi ve örnekler için bkz. [Seçmeli birim testlerini çalıştırma](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="e9e87-149">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="e9e87-150">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="e9e87-150">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="e9e87-151">Komutun Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="e9e87-151">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="e9e87-152">Örneğin, kimlik doğrulamasını tamamlamaya yönelik.</span><span class="sxs-lookup"><span data-stu-id="e9e87-152">For example, to complete authentication.</span></span> <span data-ttu-id="e9e87-153">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e9e87-153">Available since .NET Core 3.0 SDK.</span></span>

- **`-l|--logger <LOGGER_URI/FRIENDLY_NAME>`**

  <span data-ttu-id="e9e87-154">Test sonuçları için bir günlükçü belirtir.</span><span class="sxs-lookup"><span data-stu-id="e9e87-154">Specifies a logger for test results.</span></span> <span data-ttu-id="e9e87-155">MSBuild 'in aksine, DotNet testi kısaltmalar kabul etmez: `-l "console;v=d"` kullanım yerine `-l "console;verbosity=detailed"` .</span><span class="sxs-lookup"><span data-stu-id="e9e87-155">Unlike MSBuild, dotnet test doesn't accept abbreviations: instead of `-l "console;v=d"` use `-l "console;verbosity=detailed"`.</span></span>

- **`--no-build`**

  <span data-ttu-id="e9e87-156">Test projesi çalıştırılmadan önce derlenmez.</span><span class="sxs-lookup"><span data-stu-id="e9e87-156">Doesn't build the test project before running it.</span></span> <span data-ttu-id="e9e87-157">Ayrıca,-bayrağını örtülü olarak ayarlar `--no-restore` .</span><span class="sxs-lookup"><span data-stu-id="e9e87-157">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--nologo`**

  <span data-ttu-id="e9e87-158">Testleri, Microsoft TestPlatform başlığını görüntülemeden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e9e87-158">Run tests without displaying the Microsoft TestPlatform banner.</span></span> <span data-ttu-id="e9e87-159">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e9e87-159">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="e9e87-160">Komutu çalıştırılırken örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="e9e87-160">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="e9e87-161">Çalıştırılacak ikililerin bulunacağı dizin.</span><span class="sxs-lookup"><span data-stu-id="e9e87-161">Directory in which to find the binaries to run.</span></span> <span data-ttu-id="e9e87-162">Belirtilmemişse, varsayılan yol olur `./bin/<configuration>/<framework>/` .</span><span class="sxs-lookup"><span data-stu-id="e9e87-162">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="e9e87-163">Birden çok hedef çerçevesi olan projeler için ( `TargetFrameworks` özelliği aracılığıyla), `--framework` Bu seçeneği ne zaman belirttiğinizde de tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e9e87-163">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span> <span data-ttu-id="e9e87-164">`dotnet test`her zaman çıkış dizininden testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="e9e87-164">`dotnet test` always runs tests from the output directory.</span></span> <span data-ttu-id="e9e87-165"><xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType>' I, çıkış dizininde test varlıklarını kullanmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9e87-165">You can use <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> to consume test assets in the output directory.</span></span>

- **`-r|--results-directory <PATH>`**

  <span data-ttu-id="e9e87-166">Test sonuçlarının yerleştirileceği dizin.</span><span class="sxs-lookup"><span data-stu-id="e9e87-166">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="e9e87-167">Belirtilen dizin yoksa, oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e9e87-167">If the specified directory doesn't exist, it's created.</span></span> <span data-ttu-id="e9e87-168">Varsayılan değer `TestResults` Proje dosyasını içeren dizindir.</span><span class="sxs-lookup"><span data-stu-id="e9e87-168">The default is `TestResults` in the directory that contains the project file.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="e9e87-169">Sınanacak hedef çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="e9e87-169">The target runtime to test for.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="e9e87-170">`.runsettings`Testleri çalıştırmak için kullanılacak dosya.</span><span class="sxs-lookup"><span data-stu-id="e9e87-170">The `.runsettings` file to use for running the tests.</span></span> <span data-ttu-id="e9e87-171">`TargetPlatform`Öğesinin (x86 | x64) için bir etkisi yoktur `dotnet test` .</span><span class="sxs-lookup"><span data-stu-id="e9e87-171">The `TargetPlatform` element (x86|x64) has no effect for `dotnet test`.</span></span> <span data-ttu-id="e9e87-172">X86 'yı hedefleyen testleri çalıştırmak için .NET Core 'un x86 sürümünü yükler.</span><span class="sxs-lookup"><span data-stu-id="e9e87-172">To run tests that target x86, install the x86 version of .NET Core.</span></span> <span data-ttu-id="e9e87-173">Yoldaki *dotnet.exe* bit genişliği, testleri çalıştırmak için kullanılacak şeydir.</span><span class="sxs-lookup"><span data-stu-id="e9e87-173">The bitness of the *dotnet.exe* that is on the path is what will be used for running tests.</span></span> <span data-ttu-id="e9e87-174">Daha fazla bilgi için aşağıdaki kaynaklara bakın:</span><span class="sxs-lookup"><span data-stu-id="e9e87-174">For more information, see the following resources:</span></span>

  - [<span data-ttu-id="e9e87-175">Birim testlerini bir dosya kullanarak yapılandırın `.runsettings` .</span><span class="sxs-lookup"><span data-stu-id="e9e87-175">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)
  - [<span data-ttu-id="e9e87-176">Test çalıştırması yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e9e87-176">Configure a test run</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/configure.md)

- **`-t|--list-tests`**

  <span data-ttu-id="e9e87-177">Geçerli projedeki tüm bulunan testlerin listesini listeleyin.</span><span class="sxs-lookup"><span data-stu-id="e9e87-177">List all of the discovered tests in the current project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="e9e87-178">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e9e87-178">Sets the verbosity level of the command.</span></span> <span data-ttu-id="e9e87-179">İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="e9e87-179">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="e9e87-180">Varsayılan değer: `minimal`.</span><span class="sxs-lookup"><span data-stu-id="e9e87-180">The default is `minimal`.</span></span> <span data-ttu-id="e9e87-181">Daha fazla bilgi için bkz. <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span><span class="sxs-lookup"><span data-stu-id="e9e87-181">For more information, see <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span></span>

- <span data-ttu-id="e9e87-182">**`RunSettings`** değişkenlerinden</span><span class="sxs-lookup"><span data-stu-id="e9e87-182">**`RunSettings`** arguments</span></span>

 <span data-ttu-id="e9e87-183">Satır içi, `RunSettings` "--" sonra komut satırındaki son bağımsız değişkenler olarak geçirilir (--sonra boşluğu aklınızda bırakın).</span><span class="sxs-lookup"><span data-stu-id="e9e87-183">Inline `RunSettings` are passed as the last arguments on the command line after "-- " (note the space after --).</span></span> <span data-ttu-id="e9e87-184">Satır içi `RunSettings` çiftler olarak belirtilir `[name]=[value]` .</span><span class="sxs-lookup"><span data-stu-id="e9e87-184">Inline `RunSettings` are specified as `[name]=[value]` pairs.</span></span> <span data-ttu-id="e9e87-185">Birden çok çifti ayırmak için bir boşluk kullanılır `[name]=[value]` .</span><span class="sxs-lookup"><span data-stu-id="e9e87-185">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="e9e87-186">Örnek: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="e9e87-186">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="e9e87-187">Daha fazla bilgi için bkz. [komut satırı aracılığıyla RunSettings bağımsız değişkenlerini geçirme](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="e9e87-187">For more information, see [Passing RunSettings arguments through command line](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="e9e87-188">Örnekler</span><span class="sxs-lookup"><span data-stu-id="e9e87-188">Examples</span></span>

- <span data-ttu-id="e9e87-189">Projedeki testleri geçerli dizinde çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="e9e87-189">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="e9e87-190">Projedeki testleri çalıştırın `test1` :</span><span class="sxs-lookup"><span data-stu-id="e9e87-190">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="e9e87-191">Projedeki testleri geçerli dizinde çalıştırın ve TRX biçiminde bir test sonuçları dosyası oluşturun:</span><span class="sxs-lookup"><span data-stu-id="e9e87-191">Run the tests in the project in the current directory, and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

- <span data-ttu-id="e9e87-192">Projedeki testleri geçerli dizinde çalıştırın ve bir kod kapsamı dosyası oluşturun ( [Kapak Let](https://github.com/coverlet-coverage/coverlet/blob/master/Documentation/VSTestIntegration.md) toplayıcılarını yükledikten sonra):</span><span class="sxs-lookup"><span data-stu-id="e9e87-192">Run the tests in the project in the current directory, and generate a code coverage file (after installing [Coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/Documentation/VSTestIntegration.md) collectors integration):</span></span>

  ```dotnetcli
  dotnet test --collect:"XPlat Code Coverage"
  ```

- <span data-ttu-id="e9e87-193">Projedeki testleri geçerli dizinde çalıştırın ve bir kod kapsamı dosyası oluşturun (yalnızca Windows):</span><span class="sxs-lookup"><span data-stu-id="e9e87-193">Run the tests in the project in the current directory, and generate a code coverage file (Windows only):</span></span>

  ```dotnetcli
  dotnet test --collect "Code Coverage"
  ```

- <span data-ttu-id="e9e87-194">Projedeki testleri geçerli dizinde çalıştırın ve konsolun ayrıntılı ayrıntı düzeyi ile günlüğe kaydedin:</span><span class="sxs-lookup"><span data-stu-id="e9e87-194">Run the tests in the project in the current directory, and log with detailed verbosity to the console:</span></span>

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```

- <span data-ttu-id="e9e87-195">Projedeki testleri geçerli dizinde çalıştırın ve test ana bilgisayarı kilitlenirse sürmekte olan testleri rapor edin:</span><span class="sxs-lookup"><span data-stu-id="e9e87-195">Run the tests in the project in the current directory, and report tests that were in progress when the test host crashed:</span></span>

  ```dotnetcli
  dotnet test --blame
  ```

## <a name="filter-option-details"></a><span data-ttu-id="e9e87-196">Filtre seçeneği ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="e9e87-196">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="e9e87-197">`<Expression>`biçimindedir `<property><operator><value>[|&<Expression>]` .</span><span class="sxs-lookup"><span data-stu-id="e9e87-197">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="e9e87-198">`<property>`, öğesinin bir özniteliğidir `Test Case` .</span><span class="sxs-lookup"><span data-stu-id="e9e87-198">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="e9e87-199">Popüler birim testi çerçeveleri tarafından desteklenen özellikler aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="e9e87-199">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="e9e87-200">Test çerçevesi</span><span class="sxs-lookup"><span data-stu-id="e9e87-200">Test Framework</span></span> | <span data-ttu-id="e9e87-201">Desteklenen özellikler</span><span class="sxs-lookup"><span data-stu-id="e9e87-201">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="e9e87-202">MSTest</span><span class="sxs-lookup"><span data-stu-id="e9e87-202">MSTest</span></span>         | <ul><li><span data-ttu-id="e9e87-203">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="e9e87-203">FullyQualifiedName</span></span></li><li><span data-ttu-id="e9e87-204">Name</span><span class="sxs-lookup"><span data-stu-id="e9e87-204">Name</span></span></li><li><span data-ttu-id="e9e87-205">Sınıf</span><span class="sxs-lookup"><span data-stu-id="e9e87-205">ClassName</span></span></li><li><span data-ttu-id="e9e87-206">Öncelik</span><span class="sxs-lookup"><span data-stu-id="e9e87-206">Priority</span></span></li><li><span data-ttu-id="e9e87-207">TestCategory</span><span class="sxs-lookup"><span data-stu-id="e9e87-207">TestCategory</span></span></li></ul> |
| <span data-ttu-id="e9e87-208">xUnit</span><span class="sxs-lookup"><span data-stu-id="e9e87-208">xUnit</span></span>          | <ul><li><span data-ttu-id="e9e87-209">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="e9e87-209">FullyQualifiedName</span></span></li><li><span data-ttu-id="e9e87-210">DisplayName</span><span class="sxs-lookup"><span data-stu-id="e9e87-210">DisplayName</span></span></li><li><span data-ttu-id="e9e87-211">Lerdir</span><span class="sxs-lookup"><span data-stu-id="e9e87-211">Traits</span></span></li></ul>                                   |
| <span data-ttu-id="e9e87-212">NUnit</span><span class="sxs-lookup"><span data-stu-id="e9e87-212">NUnit</span></span>          | <ul><li><span data-ttu-id="e9e87-213">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="e9e87-213">FullyQualifiedName</span></span></li><li><span data-ttu-id="e9e87-214">Name</span><span class="sxs-lookup"><span data-stu-id="e9e87-214">Name</span></span></li><li><span data-ttu-id="e9e87-215">TestCategory</span><span class="sxs-lookup"><span data-stu-id="e9e87-215">TestCategory</span></span></li><li><span data-ttu-id="e9e87-216">Öncelik</span><span class="sxs-lookup"><span data-stu-id="e9e87-216">Priority</span></span></li></ul>                                   |

<span data-ttu-id="e9e87-217">, `<operator>` Özelliği ve değeri arasındaki ilişkiyi açıklar:</span><span class="sxs-lookup"><span data-stu-id="e9e87-217">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="e9e87-218">Operatör</span><span class="sxs-lookup"><span data-stu-id="e9e87-218">Operator</span></span> | <span data-ttu-id="e9e87-219">İşlev</span><span class="sxs-lookup"><span data-stu-id="e9e87-219">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="e9e87-220">Tam eşleşme</span><span class="sxs-lookup"><span data-stu-id="e9e87-220">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="e9e87-221">Tam eşleşme yok</span><span class="sxs-lookup"><span data-stu-id="e9e87-221">Not exact match</span></span> |
| `~`      | <span data-ttu-id="e9e87-222">Contains</span><span class="sxs-lookup"><span data-stu-id="e9e87-222">Contains</span></span>        |
| `!~`     | <span data-ttu-id="e9e87-223">İçermez</span><span class="sxs-lookup"><span data-stu-id="e9e87-223">Not contains</span></span>    |

<span data-ttu-id="e9e87-224">`<value>`bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="e9e87-224">`<value>` is a string.</span></span> <span data-ttu-id="e9e87-225">Tüm aramalar büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="e9e87-225">All the lookups are case insensitive.</span></span>

<span data-ttu-id="e9e87-226">Bir ifadesi `<operator>` , otomatik olarak on özelliği olarak kabul `contains` edilir `FullyQualifiedName` (örneğin, `dotnet test --filter xyz` ile aynıdır `dotnet test --filter FullyQualifiedName~xyz` ).</span><span class="sxs-lookup"><span data-stu-id="e9e87-226">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="e9e87-227">İfadeler koşullu işleçlerle birleştirilebilecek:</span><span class="sxs-lookup"><span data-stu-id="e9e87-227">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="e9e87-228">Operatör</span><span class="sxs-lookup"><span data-stu-id="e9e87-228">Operator</span></span>            | <span data-ttu-id="e9e87-229">İşlev</span><span class="sxs-lookup"><span data-stu-id="e9e87-229">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="e9e87-230">OR</span><span class="sxs-lookup"><span data-stu-id="e9e87-230">OR</span></span>       |
| `&`                 | <span data-ttu-id="e9e87-231">AND</span><span class="sxs-lookup"><span data-stu-id="e9e87-231">AND</span></span>      |

<span data-ttu-id="e9e87-232">Koşullu işleçler kullandığınızda (örneğin,) ifadeleri parantez içine alabilirsiniz `(Name~TestMethod1) | (Name~TestMethod2)` .</span><span class="sxs-lookup"><span data-stu-id="e9e87-232">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="e9e87-233">Seçmeli birim testi filtrelemeyi kullanma hakkında daha fazla bilgi ve örnekler için bkz. [Seçmeli birim testlerini çalıştırma](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="e9e87-233">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e9e87-234">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9e87-234">See also</span></span>

- [<span data-ttu-id="e9e87-235">Çerçeveler ve hedefler</span><span class="sxs-lookup"><span data-stu-id="e9e87-235">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="e9e87-236">.NET Core çalışma zamanı tanımlayıcısı (RID) kataloğu</span><span class="sxs-lookup"><span data-stu-id="e9e87-236">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="e9e87-237">Komut satırı aracılığıyla runsettings bağımsız değişkenlerini geçirme</span><span class="sxs-lookup"><span data-stu-id="e9e87-237">Passing runsettings arguments through commandline</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
