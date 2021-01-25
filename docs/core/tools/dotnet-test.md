---
title: DotNet test komutu
description: DotNet test komutu, belirli bir projedeki birim testlerini yürütmek için kullanılır.
ms.date: 04/29/2020
ms.openlocfilehash: 2671cbe6f610cfa8aa98e63e67f3240a1650cd6b
ms.sourcegitcommit: 2b878d7011306b215dbf3d5dc9c1e78355a6dcd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/25/2021
ms.locfileid: "98757882"
---
# <a name="dotnet-test"></a><span data-ttu-id="df6a5-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="df6a5-103">dotnet test</span></span>

<span data-ttu-id="df6a5-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="df6a5-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="df6a5-105">Name</span><span class="sxs-lookup"><span data-stu-id="df6a5-105">Name</span></span>

<span data-ttu-id="df6a5-106">`dotnet test` -Birim testlerini yürütmek için kullanılan .NET test sürücüsü.</span><span class="sxs-lookup"><span data-stu-id="df6a5-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="df6a5-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="df6a5-107">Synopsis</span></span>

```dotnetcli
dotnet test [<PROJECT> | <SOLUTION> | <DIRECTORY> | <DLL>]
    [-a|--test-adapter-path <ADAPTER_PATH>] [--blame] [--blame-crash]
    [--blame-crash-dump-type <DUMP_TYPE>] [--blame-crash-collect-always]
    [--blame-hang] [--blame-hang-dump-type <DUMP_TYPE>]
    [--blame-hang-timeout <TIMESPAN>]
    [-c|--configuration <CONFIGURATION>]
    [--collect <DATA_COLLECTOR_NAME>]
    [-d|--diag <LOG_FILE>] [-f|--framework <FRAMEWORK>]
    [--filter <EXPRESSION>] [--interactive]
    [-l|--logger <LOGGER>] [--no-build]
    [--nologo] [--no-restore] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--results-directory <RESULTS_DIR>] [--runtime <RUNTIME_IDENTIFIER>]
    [-s|--settings <SETTINGS_FILE>] [-t|--list-tests]
    [-v|--verbosity <LEVEL>] [[--] <RunSettings arguments>]

dotnet test -h|--help
```

## <a name="description"></a><span data-ttu-id="df6a5-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="df6a5-108">Description</span></span>

<span data-ttu-id="df6a5-109">`dotnet test`Komut, belirli bir çözümde birim testlerini yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="df6a5-109">The `dotnet test` command is used to execute unit tests in a given solution.</span></span> <span data-ttu-id="df6a5-110">`dotnet test`Komut çözümü oluşturur ve çözümdeki her test projesi için bir test ana bilgisayarı uygulaması çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="df6a5-110">The `dotnet test` command builds the solution and runs a test host application for each test project in the solution.</span></span> <span data-ttu-id="df6a5-111">Test ana bilgisayarı, test çerçevesini (örneğin, MSTest, NUnit veya xUnit) kullanarak belirtilen projedeki testleri yürütür ve her testin başarısını veya başarısızlığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="df6a5-111">The test host executes tests in the given project using a test framework, for example: MSTest, NUnit, or xUnit, and reports the success or failure of each test.</span></span> <span data-ttu-id="df6a5-112">Tüm testler başarılı olursa, Test Çalıştırıcısı çıkış kodu olarak 0 döndürür; Aksi takdirde, herhangi bir test başarısız olursa, 1 döndürür.</span><span class="sxs-lookup"><span data-stu-id="df6a5-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span>

<span data-ttu-id="df6a5-113">Çok hedefli projeler için testler hedeflenen her çerçeve için çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="df6a5-113">For multi-targeted projects, tests are run for each targeted framework.</span></span> <span data-ttu-id="df6a5-114">Test Konağı ve birim testi çerçevesi, NuGet paketleri olarak paketlenir ve proje için sıradan bağımlılıklar olarak geri yüklenir.</span><span class="sxs-lookup"><span data-stu-id="df6a5-114">The test host and the unit test framework are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="df6a5-115">Test projeleri, `<PackageReference>` Aşağıdaki örnek proje dosyasında görüldüğü gibi sıradan bir öğe kullanarak Test Çalıştırıcısı belirtir:</span><span class="sxs-lookup"><span data-stu-id="df6a5-115">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

<span data-ttu-id="df6a5-116">`Microsoft.NET.Test.Sdk`Test Konağı nerede, `xunit` Test çerçevesidir.</span><span class="sxs-lookup"><span data-stu-id="df6a5-116">Where `Microsoft.NET.Test.Sdk` is the test host, `xunit` is the test framework.</span></span> <span data-ttu-id="df6a5-117">Ve `xunit.runner.visualstudio` , xUnit Framework 'ün test ana bilgisayarı ile çalışmasına izin veren bir test bağdaştırıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="df6a5-117">And `xunit.runner.visualstudio` is a test adapter, which allows the xUnit framework to work with the test host.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="df6a5-118">Örtük geri yükleme</span><span class="sxs-lookup"><span data-stu-id="df6a5-118">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="df6a5-119">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="df6a5-119">Arguments</span></span>

- **`PROJECT | SOLUTION | DIRECTORY | DLL`**

  - <span data-ttu-id="df6a5-120">Test projesinin yolu.</span><span class="sxs-lookup"><span data-stu-id="df6a5-120">Path to the test project.</span></span>
  - <span data-ttu-id="df6a5-121">Çözümün yolu.</span><span class="sxs-lookup"><span data-stu-id="df6a5-121">Path to the solution.</span></span>
  - <span data-ttu-id="df6a5-122">Proje veya çözüm içeren bir dizinin yolu.</span><span class="sxs-lookup"><span data-stu-id="df6a5-122">Path to a directory that contains a project or a solution.</span></span>
  - <span data-ttu-id="df6a5-123">Test projesi *. dll* dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="df6a5-123">Path to a test project *.dll* file.</span></span>

  <span data-ttu-id="df6a5-124">Belirtilmemişse, geçerli dizinde bir proje veya çözüm arar.</span><span class="sxs-lookup"><span data-stu-id="df6a5-124">If not specified, it searches for a project or a solution in the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="df6a5-125">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="df6a5-125">Options</span></span>

- **`-a|--test-adapter-path <ADAPTER_PATH>`**

  <span data-ttu-id="df6a5-126">Ek test bağdaştırıcıları için aranacak bir dizin yolu.</span><span class="sxs-lookup"><span data-stu-id="df6a5-126">Path to a directory to be searched for additional test adapters.</span></span> <span data-ttu-id="df6a5-127">Yalnızca soneki olan *. dll* dosyaları `.TestAdapter.dll` denetlenir.</span><span class="sxs-lookup"><span data-stu-id="df6a5-127">Only *.dll* files with suffix `.TestAdapter.dll` are inspected.</span></span> <span data-ttu-id="df6a5-128">Belirtilmemişse, test *. dll* dizininde arama yapılır.</span><span class="sxs-lookup"><span data-stu-id="df6a5-128">If not specified, the directory of the test *.dll* is searched.</span></span>

- **`--blame`**

  <span data-ttu-id="df6a5-129">Testleri sorumluyu modunda çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="df6a5-129">Runs the tests in blame mode.</span></span> <span data-ttu-id="df6a5-130">Bu seçenek, test ana bilgisayarının kilitlenmesine neden olan sorunlu testleri yalıtmak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="df6a5-130">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="df6a5-131">Kilitlenme algılandığında, `TestResults/<Guid>/<Guid>_Sequence.xml` çökmeden önce çalıştırılan testlerin sırasını yakalayan bir sıra dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="df6a5-131">When a crash is detected, it creates a sequence file in `TestResults/<Guid>/<Guid>_Sequence.xml` that captures the order of tests that were run before the crash.</span></span>

- <span data-ttu-id="df6a5-132">**`--blame-crash`** (.NET 5,0 Preview SDK sürümünden itibaren kullanılabilir)</span><span class="sxs-lookup"><span data-stu-id="df6a5-132">**`--blame-crash`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="df6a5-133">Testleri sorumluyu modunda çalıştırır ve test ana bilgisayarı beklenmedik bir şekilde çıktığında kilitlenme dökümünü toplar.</span><span class="sxs-lookup"><span data-stu-id="df6a5-133">Runs the tests in blame mode and collects a crash dump when the test host exits unexpectedly.</span></span> <span data-ttu-id="df6a5-134">Bu seçenek, kullanılan .NET sürümüne, hata türüne ve işletim sistemine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="df6a5-134">This option depends on the version of .NET used, the type of error, and the operating system.</span></span>
  
  <span data-ttu-id="df6a5-135">Yönetilen koddaki özel durumlar için, .NET 5,0 ve sonraki sürümlerinde otomatik olarak bir döküm alınacaktır.</span><span class="sxs-lookup"><span data-stu-id="df6a5-135">For exceptions in managed code, a dump will be automatically collected on .NET 5.0 and later versions.</span></span> <span data-ttu-id="df6a5-136">Testhost veya .NET 5,0 ' de çalıştırılan ve kilitlenen herhangi bir alt işlem için bir döküm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="df6a5-136">It will generate a dump for testhost or any child process that also ran on .NET 5.0 and crashed.</span></span> <span data-ttu-id="df6a5-137">Yerel koddaki kilitlenmeler, döküm oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="df6a5-137">Crashes in native code will not generate a dump.</span></span> <span data-ttu-id="df6a5-138">Bu seçenek Windows, macOS ve Linux 'ta kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="df6a5-138">This option works on Windows, macOS, and Linux.</span></span>
  
  <span data-ttu-id="df6a5-139">Yerel koddaki kilitlenme dökümleri veya .NET Core 3,1 veya önceki sürümleri kullanıldığında, yalnızca Windows üzerinde ProcDump kullanılarak toplanabilir.</span><span class="sxs-lookup"><span data-stu-id="df6a5-139">Crash dumps in native code, or when using .NET Core 3.1 or earlier versions, can only be collected on Windows, by using Procdump.</span></span> <span data-ttu-id="df6a5-140">*procdump.exe* ve *procdump64.exe* IÇEREN bir dizin, yol veya PROCDUMP_PATH ortam değişkeninde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="df6a5-140">A directory that contains *procdump.exe* and *procdump64.exe* must be in the PATH or PROCDUMP_PATH environment variable.</span></span> <span data-ttu-id="df6a5-141">[Araçları indirin](/sysinternals/downloads/procdump).</span><span class="sxs-lookup"><span data-stu-id="df6a5-141">[Download the tools](/sysinternals/downloads/procdump).</span></span> <span data-ttu-id="df6a5-142">Şunu gösterir `--blame` .</span><span class="sxs-lookup"><span data-stu-id="df6a5-142">Implies `--blame`.</span></span>
  
  <span data-ttu-id="df6a5-143">.NET 5,0 veya üzeri sürümlerde çalışan bir yerel uygulamadan kilitlenme dökümü toplamak için, ortam değişkeni olarak ayarlanarak ProcDump kullanımı zorunlu olabilir `VSTEST_DUMP_FORCEPROCDUMP` `1` .</span><span class="sxs-lookup"><span data-stu-id="df6a5-143">To collect a crash dump from a native application running on .NET 5.0 or later, the usage of Procdump can be forced by setting the `VSTEST_DUMP_FORCEPROCDUMP` environment variable to `1`.</span></span>

- <span data-ttu-id="df6a5-144">**`--blame-crash-dump-type <DUMP_TYPE>`** (.NET 5,0 Preview SDK sürümünden itibaren kullanılabilir)</span><span class="sxs-lookup"><span data-stu-id="df6a5-144">**`--blame-crash-dump-type <DUMP_TYPE>`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="df6a5-145">Toplanacak kilitlenme bilgi dökümü türü.</span><span class="sxs-lookup"><span data-stu-id="df6a5-145">The type of crash dump to be collected.</span></span> <span data-ttu-id="df6a5-146">Şunu gösterir `--blame-crash` .</span><span class="sxs-lookup"><span data-stu-id="df6a5-146">Implies `--blame-crash`.</span></span>

- <span data-ttu-id="df6a5-147">**`--blame-crash-collect-always`** (.NET 5,0 Preview SDK sürümünden itibaren kullanılabilir)</span><span class="sxs-lookup"><span data-stu-id="df6a5-147">**`--blame-crash-collect-always`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="df6a5-148">Beklenen ve beklenmeyen test ana bilgisayarı çıkışında oluşan kilitlenme dökümünü toplar.</span><span class="sxs-lookup"><span data-stu-id="df6a5-148">Collects a crash dump on expected as well as unexpected test host exit.</span></span>

- <span data-ttu-id="df6a5-149">**`--blame-hang`** (.NET 5,0 Preview SDK sürümünden itibaren kullanılabilir)</span><span class="sxs-lookup"><span data-stu-id="df6a5-149">**`--blame-hang`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="df6a5-150">Testleri sorumluyu modunda çalıştırın ve bir test verilen zaman aşımını aştığında bir askıda kalma dökümü toplar.</span><span class="sxs-lookup"><span data-stu-id="df6a5-150">Run the tests in blame mode and collects a hang dump when a test exceeds the given timeout.</span></span>

- <span data-ttu-id="df6a5-151">**`--blame-hang-dump-type <DUMP_TYPE>`** (.NET 5,0 Preview SDK sürümünden itibaren kullanılabilir)</span><span class="sxs-lookup"><span data-stu-id="df6a5-151">**`--blame-hang-dump-type <DUMP_TYPE>`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="df6a5-152">Toplanacak kilitlenme bilgi dökümü türü.</span><span class="sxs-lookup"><span data-stu-id="df6a5-152">The type of crash dump to be collected.</span></span> <span data-ttu-id="df6a5-153">`full`, `mini` Veya olmalıdır `none` .</span><span class="sxs-lookup"><span data-stu-id="df6a5-153">It should be `full`, `mini`, or `none`.</span></span> <span data-ttu-id="df6a5-154">`none`Belirtildiğinde, test ana bilgisayarı zaman aşımında sonlandırılır, ancak hiçbir döküm toplanmaz.</span><span class="sxs-lookup"><span data-stu-id="df6a5-154">When `none` is specified, test host is terminated on timeout, but no dump is collected.</span></span> <span data-ttu-id="df6a5-155">Şunu gösterir `--blame-hang` .</span><span class="sxs-lookup"><span data-stu-id="df6a5-155">Implies `--blame-hang`.</span></span>

- <span data-ttu-id="df6a5-156">**`--blame-hang-timeout <TIMESPAN>`** (.NET 5,0 Preview SDK sürümünden itibaren kullanılabilir)</span><span class="sxs-lookup"><span data-stu-id="df6a5-156">**`--blame-hang-timeout <TIMESPAN>`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="df6a5-157">Test başına zaman aşımı, bir askıda kalma dökümü tetiklendikten sonra test ana bilgisayarı işlemi ve tüm alt işlemleri dökülür ve sonlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="df6a5-157">Per-test timeout, after which a hang dump is triggered and the test host process and all of its child processes are dumped and terminated.</span></span> <span data-ttu-id="df6a5-158">Zaman aşımı değeri aşağıdaki biçimlerden birinde belirtilir:</span><span class="sxs-lookup"><span data-stu-id="df6a5-158">The timeout value is specified in one of the following formats:</span></span>
  
  - <span data-ttu-id="df6a5-159">1.5 h, 1,5 saat, 1,5 saat</span><span class="sxs-lookup"><span data-stu-id="df6a5-159">1.5h, 1.5hour, 1.5hours</span></span>
  - <span data-ttu-id="df6a5-160">90 milyon, 90min, 90 dakika, 90 dakika</span><span class="sxs-lookup"><span data-stu-id="df6a5-160">90m, 90min, 90minute, 90minutes</span></span>
  - <span data-ttu-id="df6a5-161">5400s, 5400sn, 5400second, 5400saniye</span><span class="sxs-lookup"><span data-stu-id="df6a5-161">5400s, 5400sec, 5400second, 5400seconds</span></span>
  - <span data-ttu-id="df6a5-162">5400000ms, 5400000mil, 5400000milisaniyelik, 5400000milliseconds</span><span class="sxs-lookup"><span data-stu-id="df6a5-162">5400000ms, 5400000mil, 5400000millisecond, 5400000milliseconds</span></span>

  <span data-ttu-id="df6a5-163">Hiçbir birim kullanılmazsa (örneğin, 5400000), değerin milisaniye cinsinden olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="df6a5-163">When no unit is used (for example, 5400000), the value is assumed to be in milliseconds.</span></span> <span data-ttu-id="df6a5-164">Veri odaklı testlerle birlikte kullanıldığında, zaman aşımı davranışı kullanılan test bağdaştırıcısına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="df6a5-164">When used together with data driven tests, the timeout behavior depends on the test adapter used.</span></span> <span data-ttu-id="df6a5-165">XUnit ve NUnit için zaman aşımı her test çalışmasının ardından yenilenir.</span><span class="sxs-lookup"><span data-stu-id="df6a5-165">For xUnit and NUnit the timeout is renewed after every test case.</span></span> <span data-ttu-id="df6a5-166">MSTest için zaman aşımı tüm test çalışmaları için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="df6a5-166">For MSTest, the timeout is used for all test cases.</span></span> <span data-ttu-id="df6a5-167">Bu seçenek netcoreapp 2.1 ve üzeri sürümlerde, netcoreapp 3.1 ve üzeri ile Linux 'ta ve net 5.0 veya üzeri ile macOS 'ta desteklenir.</span><span class="sxs-lookup"><span data-stu-id="df6a5-167">This option is supported on Windows with netcoreapp2.1 and later, on Linux with netcoreapp3.1 and later, and on macOS with net5.0 or later.</span></span> <span data-ttu-id="df6a5-168">Ve anlamına gelir `--blame` `--blame-hang` .</span><span class="sxs-lookup"><span data-stu-id="df6a5-168">Implies `--blame` and `--blame-hang`.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="df6a5-169">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="df6a5-169">Defines the build configuration.</span></span> <span data-ttu-id="df6a5-170">Varsayılan değer `Debug` , ancak projenizin yapılandırması bu varsayılan SDK ayarını geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="df6a5-170">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`--collect <DATA_COLLECTOR_NAME>`**

  <span data-ttu-id="df6a5-171">Test çalıştırması için veri toplayıcıyı etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="df6a5-171">Enables data collector for the test run.</span></span> <span data-ttu-id="df6a5-172">Daha fazla bilgi için bkz. [test çalıştırmasını izleme ve çözümleme](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="df6a5-172">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>
  
  <span data-ttu-id="df6a5-173">.NET Core tarafından desteklenen herhangi bir platformda kod kapsamı toplamak için, [Kapak](https://github.com/coverlet-coverage/coverlet/blob/master/README.md) ' i yükleyip `--collect:"XPlat Code Coverage"` seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="df6a5-173">To collect code coverage on any platform that is supported by .NET Core, install [Coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/README.md) and use the `--collect:"XPlat Code Coverage"` option.</span></span>

  <span data-ttu-id="df6a5-174">Windows üzerinde, seçeneğini kullanarak kod kapsamını toplayabilirsiniz `--collect "Code Coverage"` .</span><span class="sxs-lookup"><span data-stu-id="df6a5-174">On Windows, you can collect code coverage by using the `--collect "Code Coverage"` option.</span></span> <span data-ttu-id="df6a5-175">Bu seçenek, Visual Studio 2019 Enterprise 'ta açılabilen bir *. Coverage* dosyası üretir.</span><span class="sxs-lookup"><span data-stu-id="df6a5-175">This option generates a *.coverage* file, which can be opened in Visual Studio 2019 Enterprise.</span></span> <span data-ttu-id="df6a5-176">Daha fazla bilgi için bkz. [kod kapsamını kullanma](/visualstudio/test/using-code-coverage-to-determine-how-much-code-is-being-tested) ve [kod kapsamı analizini özelleştirme](/visualstudio/test/customizing-code-coverage-analysis).</span><span class="sxs-lookup"><span data-stu-id="df6a5-176">For more information, see [Use code coverage](/visualstudio/test/using-code-coverage-to-determine-how-much-code-is-being-tested) and [Customize code coverage analysis](/visualstudio/test/customizing-code-coverage-analysis).</span></span>

- **`-d|--diag <LOG_FILE>`**

  <span data-ttu-id="df6a5-177">Test platformu için tanılama modunu sağlar ve belirtilen dosyaya ve bunun yanındaki dosyalara tanılama iletileri yazar.</span><span class="sxs-lookup"><span data-stu-id="df6a5-177">Enables diagnostic mode for the test platform and writes diagnostic messages to the specified file and to files next to it.</span></span> <span data-ttu-id="df6a5-178">İletileri günlüğe kaydeden işlem, `*.host_<date>.txt` Test ana bilgisayar günlüğü için ve veri toplayıcı günlüğü için oluşturulan dosyaları belirler `*.datacollector_<date>.txt` .</span><span class="sxs-lookup"><span data-stu-id="df6a5-178">The process that is logging the messages determines which files are created, such as `*.host_<date>.txt` for test host log, and `*.datacollector_<date>.txt` for data collector log.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="df6a5-179">`dotnet`Test ikilileri için veya .NET Framework test ana bilgisayarının kullanımını zorlar.</span><span class="sxs-lookup"><span data-stu-id="df6a5-179">Forces the use of `dotnet` or .NET Framework test host for the test binaries.</span></span> <span data-ttu-id="df6a5-180">Bu seçenek yalnızca kullanılacak ana bilgisayar türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="df6a5-180">This option only determines which type of host to use.</span></span> <span data-ttu-id="df6a5-181">Kullanılacak gerçek Framework sürümü, Test projesindeki *runtimeconfig.js* tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="df6a5-181">The actual framework version to be used is determined by the *runtimeconfig.json* of the test project.</span></span> <span data-ttu-id="df6a5-182">Belirtilmediğinde, [TargetFramework derleme özniteliği](/dotnet/api/system.runtime.versioning.targetframeworkattribute) konak türünü belirlemekte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="df6a5-182">When not specified, the [TargetFramework assembly attribute](/dotnet/api/system.runtime.versioning.targetframeworkattribute) is used to determine the type of host.</span></span> <span data-ttu-id="df6a5-183">Bu öznitelik *. dll*' den çıkarılır .NET Framework ana bilgisayar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="df6a5-183">When that attribute is stripped from the *.dll*, the .NET Framework host is used.</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="df6a5-184">Geçerli projede verilen ifadeyi kullanarak testleri filtreler.</span><span class="sxs-lookup"><span data-stu-id="df6a5-184">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="df6a5-185">Daha fazla bilgi için, [filtre seçeneği ayrıntıları](#filter-option-details) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="df6a5-185">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="df6a5-186">Seçmeli birim testi filtrelemeyi kullanma hakkında daha fazla bilgi ve örnekler için bkz. [Seçmeli birim testlerini çalıştırma](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="df6a5-186">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="df6a5-187">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="df6a5-187">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="df6a5-188">Komutun Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="df6a5-188">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="df6a5-189">Örneğin, kimlik doğrulamasını tamamlamaya yönelik.</span><span class="sxs-lookup"><span data-stu-id="df6a5-189">For example, to complete authentication.</span></span> <span data-ttu-id="df6a5-190">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="df6a5-190">Available since .NET Core 3.0 SDK.</span></span>

- **`-l|--logger <LOGGER>`**

  <span data-ttu-id="df6a5-191">Test sonuçları için bir günlükçü belirtir.</span><span class="sxs-lookup"><span data-stu-id="df6a5-191">Specifies a logger for test results.</span></span> <span data-ttu-id="df6a5-192">MSBuild 'in aksine, DotNet testi kısaltmalar kabul etmez: `-l "console;v=d"` kullanım yerine `-l "console;verbosity=detailed"` .</span><span class="sxs-lookup"><span data-stu-id="df6a5-192">Unlike MSBuild, dotnet test doesn't accept abbreviations: instead of `-l "console;v=d"` use `-l "console;verbosity=detailed"`.</span></span> <span data-ttu-id="df6a5-193">Birden çok günlüğü etkinleştirmek için parametreyi birden çok kez belirtin.</span><span class="sxs-lookup"><span data-stu-id="df6a5-193">Specify the parameter multiple times to enable multiple loggers.</span></span>

- **`--no-build`**

  <span data-ttu-id="df6a5-194">Test projesi çalıştırılmadan önce derlenmez.</span><span class="sxs-lookup"><span data-stu-id="df6a5-194">Doesn't build the test project before running it.</span></span> <span data-ttu-id="df6a5-195">Ayrıca,-bayrağını örtülü olarak ayarlar `--no-restore` .</span><span class="sxs-lookup"><span data-stu-id="df6a5-195">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--nologo`**

  <span data-ttu-id="df6a5-196">Testleri, Microsoft TestPlatform başlığını görüntülemeden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="df6a5-196">Run tests without displaying the Microsoft TestPlatform banner.</span></span> <span data-ttu-id="df6a5-197">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="df6a5-197">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="df6a5-198">Komutu çalıştırılırken örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="df6a5-198">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="df6a5-199">Çalıştırılacak ikililerin bulunacağı dizin.</span><span class="sxs-lookup"><span data-stu-id="df6a5-199">Directory in which to find the binaries to run.</span></span> <span data-ttu-id="df6a5-200">Belirtilmemişse, varsayılan yol olur `./bin/<configuration>/<framework>/` .</span><span class="sxs-lookup"><span data-stu-id="df6a5-200">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="df6a5-201">Birden çok hedef çerçevesi olan projeler için ( `TargetFrameworks` özelliği aracılığıyla), `--framework` Bu seçeneği ne zaman belirttiğinizde de tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="df6a5-201">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span> <span data-ttu-id="df6a5-202">`dotnet test` her zaman çıkış dizininden testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="df6a5-202">`dotnet test` always runs tests from the output directory.</span></span> <span data-ttu-id="df6a5-203"><xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType>' I, çıkış dizininde test varlıklarını kullanmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df6a5-203">You can use <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> to consume test assets in the output directory.</span></span>

- **`-r|--results-directory <RESULTS_DIR>`**

  <span data-ttu-id="df6a5-204">Test sonuçlarının yerleştirileceği dizin.</span><span class="sxs-lookup"><span data-stu-id="df6a5-204">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="df6a5-205">Belirtilen dizin yoksa, oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="df6a5-205">If the specified directory doesn't exist, it's created.</span></span> <span data-ttu-id="df6a5-206">Varsayılan değer `TestResults` Proje dosyasını içeren dizindir.</span><span class="sxs-lookup"><span data-stu-id="df6a5-206">The default is `TestResults` in the directory that contains the project file.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="df6a5-207">Sınanacak hedef çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="df6a5-207">The target runtime to test for.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="df6a5-208">`.runsettings`Testleri çalıştırmak için kullanılacak dosya.</span><span class="sxs-lookup"><span data-stu-id="df6a5-208">The `.runsettings` file to use for running the tests.</span></span> <span data-ttu-id="df6a5-209">`TargetPlatform`Öğesinin (x86 | x64) için bir etkisi yoktur `dotnet test` .</span><span class="sxs-lookup"><span data-stu-id="df6a5-209">The `TargetPlatform` element (x86|x64) has no effect for `dotnet test`.</span></span> <span data-ttu-id="df6a5-210">X86 'yı hedefleyen testleri çalıştırmak için .NET Core 'un x86 sürümünü yükler.</span><span class="sxs-lookup"><span data-stu-id="df6a5-210">To run tests that target x86, install the x86 version of .NET Core.</span></span> <span data-ttu-id="df6a5-211">Yoldaki *dotnet.exe* bit genişliği, testleri çalıştırmak için kullanılacak şeydir.</span><span class="sxs-lookup"><span data-stu-id="df6a5-211">The bitness of the *dotnet.exe* that is on the path is what will be used for running tests.</span></span> <span data-ttu-id="df6a5-212">Daha fazla bilgi için aşağıdaki kaynaklara bakın:</span><span class="sxs-lookup"><span data-stu-id="df6a5-212">For more information, see the following resources:</span></span>

  - [<span data-ttu-id="df6a5-213">Birim testlerini bir dosya kullanarak yapılandırın `.runsettings` .</span><span class="sxs-lookup"><span data-stu-id="df6a5-213">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)
  - [<span data-ttu-id="df6a5-214">Test çalıştırması yapılandırma</span><span class="sxs-lookup"><span data-stu-id="df6a5-214">Configure a test run</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/configure.md)

- **`-t|--list-tests`**

  <span data-ttu-id="df6a5-215">Testleri çalıştırmak yerine bulunan testleri listeleyin.</span><span class="sxs-lookup"><span data-stu-id="df6a5-215">List the discovered tests instead of running the tests.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="df6a5-216">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="df6a5-216">Sets the verbosity level of the command.</span></span> <span data-ttu-id="df6a5-217">İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="df6a5-217">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="df6a5-218">Varsayılan değer: `minimal`.</span><span class="sxs-lookup"><span data-stu-id="df6a5-218">The default is `minimal`.</span></span> <span data-ttu-id="df6a5-219">Daha fazla bilgi için bkz. <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span><span class="sxs-lookup"><span data-stu-id="df6a5-219">For more information, see <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span></span>

- <span data-ttu-id="df6a5-220">**`RunSettings`** değişkenlerinden</span><span class="sxs-lookup"><span data-stu-id="df6a5-220">**`RunSettings`** arguments</span></span>

 <span data-ttu-id="df6a5-221">Satır içi, `RunSettings` "--" sonra komut satırındaki son bağımsız değişkenler olarak geçirilir (--sonra boşluğu aklınızda bırakın).</span><span class="sxs-lookup"><span data-stu-id="df6a5-221">Inline `RunSettings` are passed as the last arguments on the command line after "-- " (note the space after --).</span></span> <span data-ttu-id="df6a5-222">Satır içi `RunSettings` çiftler olarak belirtilir `[name]=[value]` .</span><span class="sxs-lookup"><span data-stu-id="df6a5-222">Inline `RunSettings` are specified as `[name]=[value]` pairs.</span></span> <span data-ttu-id="df6a5-223">Birden çok çifti ayırmak için bir boşluk kullanılır `[name]=[value]` .</span><span class="sxs-lookup"><span data-stu-id="df6a5-223">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="df6a5-224">Örnek: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="df6a5-224">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="df6a5-225">Daha fazla bilgi için bkz. [komut satırı aracılığıyla RunSettings bağımsız değişkenlerini geçirme](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="df6a5-225">For more information, see [Passing RunSettings arguments through command line](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="df6a5-226">Örnekler</span><span class="sxs-lookup"><span data-stu-id="df6a5-226">Examples</span></span>

- <span data-ttu-id="df6a5-227">Projedeki testleri geçerli dizinde çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="df6a5-227">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="df6a5-228">Projedeki testleri çalıştırın `test1` :</span><span class="sxs-lookup"><span data-stu-id="df6a5-228">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="df6a5-229">Projedeki testleri geçerli dizinde çalıştırın ve TRX biçiminde bir test sonuçları dosyası oluşturun:</span><span class="sxs-lookup"><span data-stu-id="df6a5-229">Run the tests in the project in the current directory, and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

- <span data-ttu-id="df6a5-230">Projedeki testleri geçerli dizinde çalıştırın ve bir kod kapsamı dosyası oluşturun ( [Kapak Let](https://github.com/coverlet-coverage/coverlet/blob/master/Documentation/VSTestIntegration.md) toplayıcılarını yükledikten sonra):</span><span class="sxs-lookup"><span data-stu-id="df6a5-230">Run the tests in the project in the current directory, and generate a code coverage file (after installing [Coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/Documentation/VSTestIntegration.md) collectors integration):</span></span>

  ```dotnetcli
  dotnet test --collect:"XPlat Code Coverage"
  ```

- <span data-ttu-id="df6a5-231">Projedeki testleri geçerli dizinde çalıştırın ve bir kod kapsamı dosyası oluşturun (yalnızca Windows):</span><span class="sxs-lookup"><span data-stu-id="df6a5-231">Run the tests in the project in the current directory, and generate a code coverage file (Windows only):</span></span>

  ```dotnetcli
  dotnet test --collect "Code Coverage"
  ```

- <span data-ttu-id="df6a5-232">Projedeki testleri geçerli dizinde çalıştırın ve konsolun ayrıntılı ayrıntı düzeyi ile günlüğe kaydedin:</span><span class="sxs-lookup"><span data-stu-id="df6a5-232">Run the tests in the project in the current directory, and log with detailed verbosity to the console:</span></span>

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```

- <span data-ttu-id="df6a5-233">Projedeki testleri geçerli dizinde çalıştırın ve test ana bilgisayarı kilitlenirse sürmekte olan testleri rapor edin:</span><span class="sxs-lookup"><span data-stu-id="df6a5-233">Run the tests in the project in the current directory, and report tests that were in progress when the test host crashed:</span></span>

  ```dotnetcli
  dotnet test --blame
  ```

## <a name="filter-option-details"></a><span data-ttu-id="df6a5-234">Filtre seçeneği ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="df6a5-234">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="df6a5-235">`<Expression>` biçimindedir `<property><operator><value>[|&<Expression>]` .</span><span class="sxs-lookup"><span data-stu-id="df6a5-235">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="df6a5-236">`<property>` , öğesinin bir özniteliğidir `Test Case` .</span><span class="sxs-lookup"><span data-stu-id="df6a5-236">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="df6a5-237">Popüler birim testi çerçeveleri tarafından desteklenen özellikler aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="df6a5-237">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="df6a5-238">Test çerçevesi</span><span class="sxs-lookup"><span data-stu-id="df6a5-238">Test Framework</span></span> | <span data-ttu-id="df6a5-239">Desteklenen özellikler</span><span class="sxs-lookup"><span data-stu-id="df6a5-239">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="df6a5-240">MSTest</span><span class="sxs-lookup"><span data-stu-id="df6a5-240">MSTest</span></span>         | <ul><li><span data-ttu-id="df6a5-241">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="df6a5-241">FullyQualifiedName</span></span></li><li><span data-ttu-id="df6a5-242">Name</span><span class="sxs-lookup"><span data-stu-id="df6a5-242">Name</span></span></li><li><span data-ttu-id="df6a5-243">Sınıf</span><span class="sxs-lookup"><span data-stu-id="df6a5-243">ClassName</span></span></li><li><span data-ttu-id="df6a5-244">Öncelik</span><span class="sxs-lookup"><span data-stu-id="df6a5-244">Priority</span></span></li><li><span data-ttu-id="df6a5-245">TestCategory</span><span class="sxs-lookup"><span data-stu-id="df6a5-245">TestCategory</span></span></li></ul> |
| <span data-ttu-id="df6a5-246">xUnit</span><span class="sxs-lookup"><span data-stu-id="df6a5-246">xUnit</span></span>          | <ul><li><span data-ttu-id="df6a5-247">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="df6a5-247">FullyQualifiedName</span></span></li><li><span data-ttu-id="df6a5-248">DisplayName</span><span class="sxs-lookup"><span data-stu-id="df6a5-248">DisplayName</span></span></li><li><span data-ttu-id="df6a5-249">Kategori</span><span class="sxs-lookup"><span data-stu-id="df6a5-249">Category</span></span></li></ul>                                 |
| <span data-ttu-id="df6a5-250">NUnit</span><span class="sxs-lookup"><span data-stu-id="df6a5-250">NUnit</span></span>          | <ul><li><span data-ttu-id="df6a5-251">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="df6a5-251">FullyQualifiedName</span></span></li><li><span data-ttu-id="df6a5-252">Name</span><span class="sxs-lookup"><span data-stu-id="df6a5-252">Name</span></span></li><li><span data-ttu-id="df6a5-253">TestCategory</span><span class="sxs-lookup"><span data-stu-id="df6a5-253">TestCategory</span></span></li><li><span data-ttu-id="df6a5-254">Öncelik</span><span class="sxs-lookup"><span data-stu-id="df6a5-254">Priority</span></span></li></ul>                                   |

<span data-ttu-id="df6a5-255">, `<operator>` Özelliği ve değeri arasındaki ilişkiyi açıklar:</span><span class="sxs-lookup"><span data-stu-id="df6a5-255">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="df6a5-256">Operatör</span><span class="sxs-lookup"><span data-stu-id="df6a5-256">Operator</span></span> | <span data-ttu-id="df6a5-257">İşlev</span><span class="sxs-lookup"><span data-stu-id="df6a5-257">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="df6a5-258">Tam eşleşme</span><span class="sxs-lookup"><span data-stu-id="df6a5-258">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="df6a5-259">Tam eşleşme yok</span><span class="sxs-lookup"><span data-stu-id="df6a5-259">Not exact match</span></span> |
| `~`      | <span data-ttu-id="df6a5-260">Contains</span><span class="sxs-lookup"><span data-stu-id="df6a5-260">Contains</span></span>        |
| `!~`     | <span data-ttu-id="df6a5-261">İçermez</span><span class="sxs-lookup"><span data-stu-id="df6a5-261">Not contains</span></span>    |

<span data-ttu-id="df6a5-262">`<value>` bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="df6a5-262">`<value>` is a string.</span></span> <span data-ttu-id="df6a5-263">Tüm aramalar büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="df6a5-263">All the lookups are case insensitive.</span></span>

<span data-ttu-id="df6a5-264">Bir ifadesi `<operator>` , otomatik olarak on özelliği olarak kabul `contains` edilir `FullyQualifiedName` (örneğin, `dotnet test --filter xyz` ile aynıdır `dotnet test --filter FullyQualifiedName~xyz` ).</span><span class="sxs-lookup"><span data-stu-id="df6a5-264">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="df6a5-265">İfadeler koşullu işleçlerle birleştirilebilecek:</span><span class="sxs-lookup"><span data-stu-id="df6a5-265">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="df6a5-266">Operatör</span><span class="sxs-lookup"><span data-stu-id="df6a5-266">Operator</span></span>            | <span data-ttu-id="df6a5-267">İşlev</span><span class="sxs-lookup"><span data-stu-id="df6a5-267">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="df6a5-268">VEYA</span><span class="sxs-lookup"><span data-stu-id="df6a5-268">OR</span></span>       |
| `&`                 | <span data-ttu-id="df6a5-269">AND</span><span class="sxs-lookup"><span data-stu-id="df6a5-269">AND</span></span>      |

<span data-ttu-id="df6a5-270">Koşullu işleçler kullandığınızda (örneğin,) ifadeleri parantez içine alabilirsiniz `(Name~TestMethod1) | (Name~TestMethod2)` .</span><span class="sxs-lookup"><span data-stu-id="df6a5-270">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="df6a5-271">Seçmeli birim testi filtrelemeyi kullanma hakkında daha fazla bilgi ve örnekler için bkz. [Seçmeli birim testlerini çalıştırma](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="df6a5-271">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="df6a5-272">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="df6a5-272">See also</span></span>

- [<span data-ttu-id="df6a5-273">Çerçeveler ve hedefler</span><span class="sxs-lookup"><span data-stu-id="df6a5-273">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="df6a5-274">.NET çalışma zamanı tanımlayıcısı (RID) kataloğu</span><span class="sxs-lookup"><span data-stu-id="df6a5-274">.NET Runtime Identifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="df6a5-275">Komut satırı aracılığıyla runsettings bağımsız değişkenlerini geçirme</span><span class="sxs-lookup"><span data-stu-id="df6a5-275">Passing runsettings arguments through commandline</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
