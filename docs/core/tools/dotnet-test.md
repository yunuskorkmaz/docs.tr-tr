---
title: DotNet test komutu
description: DotNet test komutu, belirli bir projedeki birim testlerini yürütmek için kullanılır.
ms.date: 04/29/2020
ms.openlocfilehash: ef71e48daa7c4a6f33961d05a2f3def122087b0e
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975439"
---
# <a name="dotnet-test"></a><span data-ttu-id="e0492-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="e0492-103">dotnet test</span></span>

<span data-ttu-id="e0492-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="e0492-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="e0492-105">Name</span><span class="sxs-lookup"><span data-stu-id="e0492-105">Name</span></span>

<span data-ttu-id="e0492-106">`dotnet test`-Birim testlerini yürütmek için kullanılan .NET test sürücüsü.</span><span class="sxs-lookup"><span data-stu-id="e0492-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e0492-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="e0492-107">Synopsis</span></span>

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

## <a name="description"></a><span data-ttu-id="e0492-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e0492-108">Description</span></span>

<span data-ttu-id="e0492-109">Komut `dotnet test` , belirli bir çözümde birim testlerini yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e0492-109">The `dotnet test` command is used to execute unit tests in a given solution.</span></span> <span data-ttu-id="e0492-110">`dotnet test` Komut çözümü oluşturur ve çözümdeki her test projesi için bir test ana bilgisayarı uygulaması çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="e0492-110">The `dotnet test` command builds the solution and runs a test host application for each test project in the solution.</span></span> <span data-ttu-id="e0492-111">Test ana bilgisayarı, test çerçevesini (örneğin, MSTest, NUnit veya xUnit) kullanarak belirtilen projedeki testleri yürütür ve her testin başarısını veya başarısızlığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="e0492-111">The test host executes tests in the given project using a test framework, for example: MSTest, NUnit, or xUnit, and reports the success or failure of each test.</span></span> <span data-ttu-id="e0492-112">Tüm testler başarılı olursa, Test Çalıştırıcısı çıkış kodu olarak 0 döndürür; Aksi takdirde, herhangi bir test başarısız olursa, 1 döndürür.</span><span class="sxs-lookup"><span data-stu-id="e0492-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span>

<span data-ttu-id="e0492-113">Çok hedefli projeler için testler hedeflenen her çerçeve için çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="e0492-113">For multi-targeted projects, tests are run for each targeted framework.</span></span> <span data-ttu-id="e0492-114">Test Konağı ve birim testi çerçevesi, NuGet paketleri olarak paketlenir ve proje için sıradan bağımlılıklar olarak geri yüklenir.</span><span class="sxs-lookup"><span data-stu-id="e0492-114">The test host and the unit test framework are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="e0492-115">Test projeleri, aşağıdaki örnek proje dosyasında görüldüğü gibi `<PackageReference>` sıradan bir öğe kullanarak Test Çalıştırıcısı belirtir:</span><span class="sxs-lookup"><span data-stu-id="e0492-115">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

<span data-ttu-id="e0492-116">Test `Microsoft.NET.Test.Sdk` Konağı `xunit` nerede, test çerçevesidir.</span><span class="sxs-lookup"><span data-stu-id="e0492-116">Where `Microsoft.NET.Test.Sdk` is the test host, `xunit` is the test framework.</span></span> <span data-ttu-id="e0492-117">Ve `xunit.runner.visualstudio` , xUnit Framework 'ün test ana bilgisayarı ile çalışmasına izin veren bir test bağdaştırıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="e0492-117">And `xunit.runner.visualstudio` is a test adapter, which allows the xUnit framework to work with the test host.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="e0492-118">Örtük geri yükleme</span><span class="sxs-lookup"><span data-stu-id="e0492-118">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="e0492-119">Arguments</span><span class="sxs-lookup"><span data-stu-id="e0492-119">Arguments</span></span>

- **`PROJECT | SOLUTION | DIRECTORY | DLL`**

  - <span data-ttu-id="e0492-120">Test projesinin yolu.</span><span class="sxs-lookup"><span data-stu-id="e0492-120">Path to the test project.</span></span>
  - <span data-ttu-id="e0492-121">Çözümün yolu.</span><span class="sxs-lookup"><span data-stu-id="e0492-121">Path to the solution.</span></span>
  - <span data-ttu-id="e0492-122">Proje veya çözüm içeren bir dizinin yolu.</span><span class="sxs-lookup"><span data-stu-id="e0492-122">Path to a directory that contains a project or a solution.</span></span>
  - <span data-ttu-id="e0492-123">Test projesi *. dll* dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="e0492-123">Path to a test project *.dll* file.</span></span>

  <span data-ttu-id="e0492-124">Belirtilmemişse, geçerli dizinde bir proje veya çözüm arar.</span><span class="sxs-lookup"><span data-stu-id="e0492-124">If not specified, it searches for a project or a solution in the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="e0492-125">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="e0492-125">Options</span></span>

- **`-a|--test-adapter-path <PATH_TO_ADAPTER>`**

  <span data-ttu-id="e0492-126">Ek test bağdaştırıcıları için aranacak bir dizin yolu.</span><span class="sxs-lookup"><span data-stu-id="e0492-126">Path to a directory to be searched for additional test adapters.</span></span> <span data-ttu-id="e0492-127">Yalnızca soneki `.TestAdapter.dll` olan *. dll* dosyaları denetlenir.</span><span class="sxs-lookup"><span data-stu-id="e0492-127">Only *.dll* files with suffix `.TestAdapter.dll` are inspected.</span></span> <span data-ttu-id="e0492-128">Belirtilmemişse, test *. dll* dizininde arama yapılır.</span><span class="sxs-lookup"><span data-stu-id="e0492-128">If not specified, the directory of the test *.dll* is searched.</span></span>

- **`--blame`**

  <span data-ttu-id="e0492-129">Testleri sorumluyu modunda çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="e0492-129">Runs the tests in blame mode.</span></span> <span data-ttu-id="e0492-130">Bu seçenek, test ana bilgisayarının kilitlenmesine neden olan sorunlu testleri yalıtmak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="e0492-130">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="e0492-131">Kilitlenme algılandığında, çökmeden önce çalıştırılan testlerin sırasını yakalayan bir sıra `TestResults/<Guid>/<Guid>_Sequence.xml` dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e0492-131">When a crash is detected, it creates an sequence file in `TestResults/<Guid>/<Guid>_Sequence.xml` that captures the order of tests that were run before the crash.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="e0492-132">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e0492-132">Defines the build configuration.</span></span> <span data-ttu-id="e0492-133">Varsayılan değer `Debug`, ancak projenizin yapılandırması bu varsayılan SDK ayarını geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="e0492-133">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  <span data-ttu-id="e0492-134">Test çalıştırması için veri toplayıcıyı etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e0492-134">Enables data collector for the test run.</span></span> <span data-ttu-id="e0492-135">Daha fazla bilgi için bkz. [test çalıştırmasını izleme ve çözümleme](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="e0492-135">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

- **`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  <span data-ttu-id="e0492-136">Test platformu için tanılama modunu sağlar ve belirtilen dosyaya ve bunun yanındaki dosyalara tanılama iletileri yazar.</span><span class="sxs-lookup"><span data-stu-id="e0492-136">Enables diagnostic mode for the test platform and writes diagnostic messages to the specified file and to files next to it.</span></span> <span data-ttu-id="e0492-137">İletileri günlüğe kaydeden işlem, test ana bilgisayar günlüğü `*.host_<date>.txt` için ve `*.datacollector_<date>.txt` veri toplayıcı günlüğü için oluşturulan dosyaları belirler.</span><span class="sxs-lookup"><span data-stu-id="e0492-137">The process that is logging the messages determines which files are created, such as `*.host_<date>.txt` for test host log, and `*.datacollector_<date>.txt` for data collector log.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="e0492-138">Test ikilileri için `dotnet` veya .NET Framework test ana bilgisayarının kullanımını zorlar.</span><span class="sxs-lookup"><span data-stu-id="e0492-138">Forces the use of `dotnet` or .NET Framework test host for the test binaries.</span></span> <span data-ttu-id="e0492-139">Bu seçenek yalnızca kullanılacak ana bilgisayar türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="e0492-139">This option only determines which type of host to use.</span></span> <span data-ttu-id="e0492-140">Kullanılacak gerçek çerçeve sürümü test projesinin *runtimeconfig. JSON* tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="e0492-140">The actual framework version to be used is determined by the *runtimeconfig.json* of the test project.</span></span> <span data-ttu-id="e0492-141">Belirtilmediğinde, [TargetFramework derleme özniteliği](/dotnet/api/system.runtime.versioning.targetframeworkattribute) konak türünü belirlemekte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e0492-141">When not specified, the [TargetFramework assembly attribute](/dotnet/api/system.runtime.versioning.targetframeworkattribute) is used to determine the type of host.</span></span> <span data-ttu-id="e0492-142">Bu öznitelik *. dll*' den çıkarılır .NET Framework ana bilgisayar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e0492-142">When that attribute is stripped from the *.dll*, the .NET Framework host is used.</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="e0492-143">Geçerli projede verilen ifadeyi kullanarak testleri filtreler.</span><span class="sxs-lookup"><span data-stu-id="e0492-143">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="e0492-144">Daha fazla bilgi için, [filtre seçeneği ayrıntıları](#filter-option-details) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e0492-144">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="e0492-145">Seçmeli birim testi filtrelemeyi kullanma hakkında daha fazla bilgi ve örnekler için bkz. [Seçmeli birim testlerini çalıştırma](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="e0492-145">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="e0492-146">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="e0492-146">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="e0492-147">Komutun Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="e0492-147">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="e0492-148">Örneğin, kimlik doğrulamasını tamamlamaya yönelik.</span><span class="sxs-lookup"><span data-stu-id="e0492-148">For example, to complete authentication.</span></span> <span data-ttu-id="e0492-149">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e0492-149">Available since .NET Core 3.0 SDK.</span></span>

- **`-l|--logger <LOGGER_URI/FRIENDLY_NAME>`**

  <span data-ttu-id="e0492-150">Test sonuçları için bir günlükçü belirtir.</span><span class="sxs-lookup"><span data-stu-id="e0492-150">Specifies a logger for test results.</span></span> <span data-ttu-id="e0492-151">MSBuild 'in `-l "console;v=d"` aksine, DotNet testi kısaltmalar kabul etmez: kullanım `-l "console;verbosity=detailed"`yerine.</span><span class="sxs-lookup"><span data-stu-id="e0492-151">Unlike MSBuild, dotnet test doesn't accept abbreviations: instead of `-l "console;v=d"` use `-l "console;verbosity=detailed"`.</span></span>

- **`--no-build`**

  <span data-ttu-id="e0492-152">Test projesi çalıştırılmadan önce derlenmez.</span><span class="sxs-lookup"><span data-stu-id="e0492-152">Doesn't build the test project before running it.</span></span> <span data-ttu-id="e0492-153">Ayrıca,- `--no-restore` bayrağını örtülü olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e0492-153">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--nologo`**

  <span data-ttu-id="e0492-154">Testleri, Microsoft TestPlatform başlığını görüntülemeden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e0492-154">Run tests without displaying the Microsoft TestPlatform banner.</span></span> <span data-ttu-id="e0492-155">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e0492-155">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="e0492-156">Komutu çalıştırılırken örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="e0492-156">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="e0492-157">Çalıştırılacak ikililerin bulunacağı dizin.</span><span class="sxs-lookup"><span data-stu-id="e0492-157">Directory in which to find the binaries to run.</span></span> <span data-ttu-id="e0492-158">Belirtilmemişse, varsayılan yol olur `./bin/<configuration>/<framework>/`.</span><span class="sxs-lookup"><span data-stu-id="e0492-158">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="e0492-159">Birden çok hedef çerçevesi olan projeler için ( `TargetFrameworks` özelliği aracılığıyla), bu seçeneği ne zaman belirttiğinizde `--framework` de tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0492-159">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span> <span data-ttu-id="e0492-160">`dotnet test`testleri her zaman çıkış dizininden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e0492-160">`dotnet test` always run tests from the output directory.</span></span> <span data-ttu-id="e0492-161">' I, <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> çıkış dizininde test varlıklarını kullanmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0492-161">You can use <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> to consume test assets in the output directory.</span></span>

- **`-r|--results-directory <PATH>`**

  <span data-ttu-id="e0492-162">Test sonuçlarının yerleştirileceği dizin.</span><span class="sxs-lookup"><span data-stu-id="e0492-162">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="e0492-163">Belirtilen dizin yoksa, oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e0492-163">If the specified directory doesn't exist, it's created.</span></span> <span data-ttu-id="e0492-164">Varsayılan değer `TestResults` proje dosyasını içeren dizindir.</span><span class="sxs-lookup"><span data-stu-id="e0492-164">The default is `TestResults` in the directory that contains the project file.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="e0492-165">Sınanacak hedef çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="e0492-165">The target runtime to test for.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="e0492-166">Testleri `.runsettings` çalıştırmak için kullanılacak dosya.</span><span class="sxs-lookup"><span data-stu-id="e0492-166">The `.runsettings` file to use for running the tests.</span></span> <span data-ttu-id="e0492-167">`TargetPlatform` Öğesinin (x86 | x64) için `dotnet test`hiçbir etkisi olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e0492-167">Note that the `TargetPlatform` element (x86|x64) has no effect for `dotnet test`.</span></span> <span data-ttu-id="e0492-168">X86 'yı hedefleyen testleri çalıştırmak için .NET Core 'un x86 sürümünü yükler.</span><span class="sxs-lookup"><span data-stu-id="e0492-168">To run tests that target x86, install the x86 version of .NET Core.</span></span> <span data-ttu-id="e0492-169">Yoldaki *DotNet. exe* ' nin bit genişliği, testleri çalıştırmak için kullanılacak şeydir.</span><span class="sxs-lookup"><span data-stu-id="e0492-169">The bitness of the *dotnet.exe* that is on the path is what will be used for running tests.</span></span> <span data-ttu-id="e0492-170">Daha fazla bilgi için aşağıdaki kaynaklara bakın:</span><span class="sxs-lookup"><span data-stu-id="e0492-170">For more information, see the following resources:</span></span>

  - [<span data-ttu-id="e0492-171">Birim testlerini bir `.runsettings` dosya kullanarak yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="e0492-171">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)
  - [<span data-ttu-id="e0492-172">Test çalıştırması yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e0492-172">Configure a test run</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/configure.md)

- **`-t|--list-tests`**

  <span data-ttu-id="e0492-173">Geçerli projedeki tüm bulunan testlerin listesini listeleyin.</span><span class="sxs-lookup"><span data-stu-id="e0492-173">List all of the discovered tests in the current project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="e0492-174">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e0492-174">Sets the verbosity level of the command.</span></span> <span data-ttu-id="e0492-175">İzin verilen değerler `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]`,,, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="e0492-175">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="e0492-176">Varsayılan değer: `minimal`.</span><span class="sxs-lookup"><span data-stu-id="e0492-176">The default is `minimal`.</span></span> <span data-ttu-id="e0492-177">Daha fazla bilgi için bkz. <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span><span class="sxs-lookup"><span data-stu-id="e0492-177">For more information, see <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span></span>

- <span data-ttu-id="e0492-178">**`RunSettings`** değişkenlerinden</span><span class="sxs-lookup"><span data-stu-id="e0492-178">**`RunSettings`** arguments</span></span>

 <span data-ttu-id="e0492-179">Satır `RunSettings` içi, "--" sonra komut satırındaki son bağımsız değişkenler olarak geçirilir (--sonra boşluğu aklınızda bırakın).</span><span class="sxs-lookup"><span data-stu-id="e0492-179">Inline `RunSettings` are passed as the last arguments on the command line after "-- " (note the space after --).</span></span> <span data-ttu-id="e0492-180">Satır `RunSettings` içi çiftler olarak `[name]=[value]` belirtilir.</span><span class="sxs-lookup"><span data-stu-id="e0492-180">Inline `RunSettings` are specified as `[name]=[value]` pairs.</span></span> <span data-ttu-id="e0492-181">Birden çok `[name]=[value]` çifti ayırmak için bir boşluk kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e0492-181">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="e0492-182">Örnek: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="e0492-182">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="e0492-183">Daha fazla bilgi için bkz. [komut satırı aracılığıyla RunSettings bağımsız değişkenlerini geçirme](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="e0492-183">For more information, see [Passing RunSettings arguments through command line](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="e0492-184">Örnekler</span><span class="sxs-lookup"><span data-stu-id="e0492-184">Examples</span></span>

- <span data-ttu-id="e0492-185">Projedeki testleri geçerli dizinde çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="e0492-185">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="e0492-186">`test1` Projedeki testleri çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="e0492-186">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="e0492-187">Projedeki testleri geçerli dizinde çalıştırın ve TRX biçiminde bir test sonuçları dosyası oluşturun:</span><span class="sxs-lookup"><span data-stu-id="e0492-187">Run the tests in the project in the current directory, and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

- <span data-ttu-id="e0492-188">Projedeki testleri geçerli dizinde çalıştırın ve konsolun ayrıntılı ayrıntı düzeyi ile günlüğe kaydedin:</span><span class="sxs-lookup"><span data-stu-id="e0492-188">Run the tests in the project in the current directory, and log with detailed verbosity to the console:</span></span>

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```
  
  - <span data-ttu-id="e0492-189">Projedeki testleri geçerli dizinde çalıştırın ve test ana bilgisayarı kilitlenirse sürmekte olan testleri rapor edin:</span><span class="sxs-lookup"><span data-stu-id="e0492-189">Run the tests in the project in the current directory, and report tests that were in progress when the test host crashed:</span></span>

  ```dotnetcli
  dotnet test --blame
  ```

## <a name="filter-option-details"></a><span data-ttu-id="e0492-190">Filtre seçeneği ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="e0492-190">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="e0492-191">`<Expression>`biçimindedir `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="e0492-191">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="e0492-192">`<property>`, `Test Case`öğesinin bir özniteliğidir.</span><span class="sxs-lookup"><span data-stu-id="e0492-192">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="e0492-193">Popüler birim testi çerçeveleri tarafından desteklenen özellikler aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="e0492-193">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="e0492-194">Test çerçevesi</span><span class="sxs-lookup"><span data-stu-id="e0492-194">Test Framework</span></span> | <span data-ttu-id="e0492-195">Desteklenen özellikler</span><span class="sxs-lookup"><span data-stu-id="e0492-195">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="e0492-196">MSTest</span><span class="sxs-lookup"><span data-stu-id="e0492-196">MSTest</span></span>         | <ul><li><span data-ttu-id="e0492-197">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="e0492-197">FullyQualifiedName</span></span></li><li><span data-ttu-id="e0492-198">Name</span><span class="sxs-lookup"><span data-stu-id="e0492-198">Name</span></span></li><li><span data-ttu-id="e0492-199">Sınıf</span><span class="sxs-lookup"><span data-stu-id="e0492-199">ClassName</span></span></li><li><span data-ttu-id="e0492-200">Öncelik</span><span class="sxs-lookup"><span data-stu-id="e0492-200">Priority</span></span></li><li><span data-ttu-id="e0492-201">TestCategory</span><span class="sxs-lookup"><span data-stu-id="e0492-201">TestCategory</span></span></li></ul> |
| <span data-ttu-id="e0492-202">xUnit</span><span class="sxs-lookup"><span data-stu-id="e0492-202">xUnit</span></span>          | <ul><li><span data-ttu-id="e0492-203">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="e0492-203">FullyQualifiedName</span></span></li><li><span data-ttu-id="e0492-204">DisplayName</span><span class="sxs-lookup"><span data-stu-id="e0492-204">DisplayName</span></span></li><li><span data-ttu-id="e0492-205">Lerdir</span><span class="sxs-lookup"><span data-stu-id="e0492-205">Traits</span></span></li></ul>                                   |

<span data-ttu-id="e0492-206">, `<operator>` Özelliği ve değeri arasındaki ilişkiyi açıklar:</span><span class="sxs-lookup"><span data-stu-id="e0492-206">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="e0492-207">İşleç</span><span class="sxs-lookup"><span data-stu-id="e0492-207">Operator</span></span> | <span data-ttu-id="e0492-208">İşlev</span><span class="sxs-lookup"><span data-stu-id="e0492-208">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="e0492-209">Tam eşleşme</span><span class="sxs-lookup"><span data-stu-id="e0492-209">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="e0492-210">Tam eşleşme yok</span><span class="sxs-lookup"><span data-stu-id="e0492-210">Not exact match</span></span> |
| `~`      | <span data-ttu-id="e0492-211">Contains</span><span class="sxs-lookup"><span data-stu-id="e0492-211">Contains</span></span>        |
| `!~`     | <span data-ttu-id="e0492-212">İçermez</span><span class="sxs-lookup"><span data-stu-id="e0492-212">Not contains</span></span>    |

<span data-ttu-id="e0492-213">`<value>`bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="e0492-213">`<value>` is a string.</span></span> <span data-ttu-id="e0492-214">Tüm aramalar büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="e0492-214">All the lookups are case insensitive.</span></span>

<span data-ttu-id="e0492-215">`<operator>` Bir ifadesi, otomatik olarak `contains` on `FullyQualifiedName` özelliği olarak kabul edilir (örneğin, `dotnet test --filter xyz` ile `dotnet test --filter FullyQualifiedName~xyz`aynıdır).</span><span class="sxs-lookup"><span data-stu-id="e0492-215">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="e0492-216">İfadeler koşullu işleçlerle birleştirilebilecek:</span><span class="sxs-lookup"><span data-stu-id="e0492-216">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="e0492-217">İşleç</span><span class="sxs-lookup"><span data-stu-id="e0492-217">Operator</span></span>            | <span data-ttu-id="e0492-218">İşlev</span><span class="sxs-lookup"><span data-stu-id="e0492-218">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="e0492-219">OR</span><span class="sxs-lookup"><span data-stu-id="e0492-219">OR</span></span>       |
| `&`                 | <span data-ttu-id="e0492-220">AND</span><span class="sxs-lookup"><span data-stu-id="e0492-220">AND</span></span>      |

<span data-ttu-id="e0492-221">Koşullu işleçler kullandığınızda (örneğin, `(Name~TestMethod1) | (Name~TestMethod2)`) ifadeleri parantez içine alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0492-221">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="e0492-222">Seçmeli birim testi filtrelemeyi kullanma hakkında daha fazla bilgi ve örnekler için bkz. [Seçmeli birim testlerini çalıştırma](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="e0492-222">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e0492-223">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0492-223">See also</span></span>

- [<span data-ttu-id="e0492-224">Çerçeveler ve hedefler</span><span class="sxs-lookup"><span data-stu-id="e0492-224">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="e0492-225">.NET Core çalışma zamanı tanımlayıcısı (RID) kataloğu</span><span class="sxs-lookup"><span data-stu-id="e0492-225">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="e0492-226">Komut satırı aracılığıyla runsettings bağımsız değişkenlerini geçirme</span><span class="sxs-lookup"><span data-stu-id="e0492-226">Passing runsettings arguments through commandline</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
