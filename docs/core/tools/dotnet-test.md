---
title: DotNet test komutu
description: DotNet test komutu, belirli bir projedeki birim testlerini yürütmek için kullanılır.
ms.date: 04/29/2020
ms.openlocfilehash: a8218b6596601069b89a60ad018adf89a1f47cf6
ms.sourcegitcommit: e09dbff13f0b21b569a101f3b3c5efa174aec204
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82624897"
---
# <a name="dotnet-test"></a><span data-ttu-id="66c5f-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="66c5f-103">dotnet test</span></span>

<span data-ttu-id="66c5f-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="66c5f-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="66c5f-105">Adı</span><span class="sxs-lookup"><span data-stu-id="66c5f-105">Name</span></span>

<span data-ttu-id="66c5f-106">`dotnet test`-Birim testlerini yürütmek için kullanılan .NET test sürücüsü.</span><span class="sxs-lookup"><span data-stu-id="66c5f-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="66c5f-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="66c5f-107">Synopsis</span></span>

```dotnetcli
dotnet test [<PROJECT> | <SOLUTION>]
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

## <a name="description"></a><span data-ttu-id="66c5f-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="66c5f-108">Description</span></span>

<span data-ttu-id="66c5f-109">Komut `dotnet test` , belirli bir projedeki birim testlerini yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="66c5f-109">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="66c5f-110">Komut `dotnet test` , bir proje için belirtilen Test Çalıştırıcısı konsol uygulamasını başlatır.</span><span class="sxs-lookup"><span data-stu-id="66c5f-110">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="66c5f-111">Test Çalıştırıcısı, bir birim test çerçevesi (örneğin, MSTest, NUnit veya xUnit) için tanımlanan testleri yürütür ve her testin başarısını veya başarısızlığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="66c5f-111">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="66c5f-112">Tüm testler başarılı olursa, Test Çalıştırıcısı çıkış kodu olarak 0 döndürür; Aksi takdirde, herhangi bir test başarısız olursa, 1 döndürür.</span><span class="sxs-lookup"><span data-stu-id="66c5f-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="66c5f-113">Çok hedefli projeler için testler hedeflenen her çerçeve için çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="66c5f-113">For multi-targeted projects, tests are run for each targeted framework.</span></span> <span data-ttu-id="66c5f-114">Test Çalıştırıcısı ve birim testi kitaplığı, NuGet paketleri olarak paketlenir ve proje için sıradan bağımlılıklar olarak geri yüklenir.</span><span class="sxs-lookup"><span data-stu-id="66c5f-114">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="66c5f-115">Test projeleri, aşağıdaki örnek proje dosyasında görüldüğü gibi `<PackageReference>` sıradan bir öğe kullanarak Test Çalıştırıcısı belirtir:</span><span class="sxs-lookup"><span data-stu-id="66c5f-115">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

### <a name="implicit-restore"></a><span data-ttu-id="66c5f-116">Örtük geri yükleme</span><span class="sxs-lookup"><span data-stu-id="66c5f-116">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="66c5f-117">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="66c5f-117">Arguments</span></span>

- **`PROJECT | SOLUTION`**

  <span data-ttu-id="66c5f-118">Test projesinin veya çözümünün yolu.</span><span class="sxs-lookup"><span data-stu-id="66c5f-118">Path to the test project or solution.</span></span> <span data-ttu-id="66c5f-119">Belirtilmezse, varsayılan olarak geçerli dizin olur.</span><span class="sxs-lookup"><span data-stu-id="66c5f-119">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="66c5f-120">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="66c5f-120">Options</span></span>

- **`-a|--test-adapter-path <PATH_TO_ADAPTER>`**

  <span data-ttu-id="66c5f-121">Test çalıştırmasında belirtilen yoldan özel test bağdaştırıcılarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="66c5f-121">Use the custom test adapters from the specified path in the test run.</span></span>

- **`--blame`**

  <span data-ttu-id="66c5f-122">Testleri sorumluyu modunda çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="66c5f-122">Runs the tests in blame mode.</span></span> <span data-ttu-id="66c5f-123">Bu seçenek, test ana bilgisayarının kilitlenmesine neden olan sorunlu testleri yalıtmak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="66c5f-123">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="66c5f-124">Geçerli dizinde, kilitlenmeden önce yürütülen testlerin sırasını yakalayan *Sequence. xml* olarak bir çıktı dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="66c5f-124">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="66c5f-125">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="66c5f-125">Defines the build configuration.</span></span> <span data-ttu-id="66c5f-126">Varsayılan değer `Debug`, ancak projenizin yapılandırması bu varsayılan SDK ayarını geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="66c5f-126">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  <span data-ttu-id="66c5f-127">Test çalıştırması için veri toplayıcıyı etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="66c5f-127">Enables data collector for the test run.</span></span> <span data-ttu-id="66c5f-128">Daha fazla bilgi için bkz. [test çalıştırmasını izleme ve çözümleme](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="66c5f-128">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

- **`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  <span data-ttu-id="66c5f-129">Test platformu için tanılama modunu sağlar ve tanılama iletilerini belirtilen dosyaya yazar.</span><span class="sxs-lookup"><span data-stu-id="66c5f-129">Enables diagnostic mode for the test platform and writes diagnostic messages to the specified file.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="66c5f-130">Belirli bir [çerçeve](../../standard/frameworks.md)için test ikililerini arar.</span><span class="sxs-lookup"><span data-stu-id="66c5f-130">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="66c5f-131">Geçerli projede verilen ifadeyi kullanarak testleri filtreler.</span><span class="sxs-lookup"><span data-stu-id="66c5f-131">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="66c5f-132">Daha fazla bilgi için, [filtre seçeneği ayrıntıları](#filter-option-details) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="66c5f-132">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="66c5f-133">Seçmeli birim testi filtrelemeyi kullanma hakkında daha fazla bilgi ve örnekler için bkz. [Seçmeli birim testlerini çalıştırma](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="66c5f-133">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="66c5f-134">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="66c5f-134">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="66c5f-135">Komutun Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="66c5f-135">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="66c5f-136">Örneğin, kimlik doğrulamasını tamamlamaya yönelik.</span><span class="sxs-lookup"><span data-stu-id="66c5f-136">For example, to complete authentication.</span></span> <span data-ttu-id="66c5f-137">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="66c5f-137">Available since .NET Core 3.0 SDK.</span></span>

- **`-l|--logger <LOGGER_URI/FRIENDLY_NAME>`**

  <span data-ttu-id="66c5f-138">Test sonuçları için bir günlükçü belirtir.</span><span class="sxs-lookup"><span data-stu-id="66c5f-138">Specifies a logger for test results.</span></span> <span data-ttu-id="66c5f-139">MSBuild 'in `-l "console;v=d"` aksine, DotNet testi kısaltmalar kabul etmez: kullanım `-l "console;verbosity=detailed"`yerine.</span><span class="sxs-lookup"><span data-stu-id="66c5f-139">Unlike MSBuild, dotnet test doesn't accept abbreviations: instead of `-l "console;v=d"` use `-l "console;verbosity=detailed"`.</span></span>

- **`--no-build`**

  <span data-ttu-id="66c5f-140">Test projesi çalıştırılmadan önce derlenmez.</span><span class="sxs-lookup"><span data-stu-id="66c5f-140">Doesn't build the test project before running it.</span></span> <span data-ttu-id="66c5f-141">Ayrıca,- `--no-restore` bayrağını örtülü olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="66c5f-141">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--nologo`**

  <span data-ttu-id="66c5f-142">Testleri, Microsoft TestPlatform başlığını görüntülemeden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="66c5f-142">Run tests without displaying the Microsoft TestPlatform banner.</span></span> <span data-ttu-id="66c5f-143">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="66c5f-143">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="66c5f-144">Komutu çalıştırılırken örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="66c5f-144">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="66c5f-145">Çalıştırılacak ikililerin bulunacağı dizin.</span><span class="sxs-lookup"><span data-stu-id="66c5f-145">Directory in which to find the binaries to run.</span></span> <span data-ttu-id="66c5f-146">Belirtilmemişse, varsayılan yol olur `./bin/<configuration>/<framework>/`.</span><span class="sxs-lookup"><span data-stu-id="66c5f-146">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="66c5f-147">Birden çok hedef çerçevesi olan projeler için ( `TargetFrameworks` özelliği aracılığıyla), bu seçeneği ne zaman belirttiğinizde `--framework` de tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="66c5f-147">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span> <span data-ttu-id="66c5f-148">`dotnet test`testleri her zaman çıkış dizininden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="66c5f-148">`dotnet test` always run tests from the output directory.</span></span> <span data-ttu-id="66c5f-149">' I, <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> çıkış dizininde test varlıklarını kullanmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66c5f-149">You can use <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> to consume test assets in the output directory.</span></span>

- **`-r|--results-directory <PATH>`**

  <span data-ttu-id="66c5f-150">Test sonuçlarının yerleştirileceği dizin.</span><span class="sxs-lookup"><span data-stu-id="66c5f-150">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="66c5f-151">Belirtilen dizin yoksa, oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="66c5f-151">If the specified directory doesn't exist, it's created.</span></span> <span data-ttu-id="66c5f-152">Varsayılan değer `TestResults` proje dosyasını içeren dizindir.</span><span class="sxs-lookup"><span data-stu-id="66c5f-152">The default is `TestResults` in the directory that contains the project file.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="66c5f-153">Sınanacak hedef çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="66c5f-153">The target runtime to test for.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="66c5f-154">Testleri `.runsettings` çalıştırmak için kullanılacak dosya.</span><span class="sxs-lookup"><span data-stu-id="66c5f-154">The `.runsettings` file to use for running the tests.</span></span> <span data-ttu-id="66c5f-155">`TargetPlatform` Öğesinin (x86 | x64) için `dotnet test`hiçbir etkisi olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="66c5f-155">Note that the `TargetPlatform` element (x86|x64) has no effect for `dotnet test`.</span></span> <span data-ttu-id="66c5f-156">X86 'yı hedefleyen testleri çalıştırmak için .NET Core 'un x86 sürümünü yükler.</span><span class="sxs-lookup"><span data-stu-id="66c5f-156">To run tests that target x86, install the x86 version of .NET Core.</span></span> <span data-ttu-id="66c5f-157">Yoldaki *DotNet. exe* ' nin bit genişliği, testleri çalıştırmak için kullanılacak şeydir.</span><span class="sxs-lookup"><span data-stu-id="66c5f-157">The bitness of the *dotnet.exe* that is on the path is what will be used for running tests.</span></span> <span data-ttu-id="66c5f-158">daha fazla bilgi için aşağıdaki kaynaklara bakın:</span><span class="sxs-lookup"><span data-stu-id="66c5f-158">for more information, see the following resources:</span></span>

  - [<span data-ttu-id="66c5f-159">Birim testlerini bir `.runsettings` dosya kullanarak yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="66c5f-159">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)
  - [<span data-ttu-id="66c5f-160">Test çalıştırması yapılandırma</span><span class="sxs-lookup"><span data-stu-id="66c5f-160">Configure a test run</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/configure.md)

- **`-t|--list-tests`**

  <span data-ttu-id="66c5f-161">Geçerli projedeki tüm bulunan testlerin listesini listeleyin.</span><span class="sxs-lookup"><span data-stu-id="66c5f-161">List all of the discovered tests in the current project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="66c5f-162">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="66c5f-162">Sets the verbosity level of the command.</span></span> <span data-ttu-id="66c5f-163">İzin verilen değerler `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]`,,, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="66c5f-163">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="66c5f-164">Varsayılan değer: `minimal`.</span><span class="sxs-lookup"><span data-stu-id="66c5f-164">The default is `minimal`.</span></span> <span data-ttu-id="66c5f-165">Daha fazla bilgi için bkz. <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span><span class="sxs-lookup"><span data-stu-id="66c5f-165">For more information, see <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span></span>

- <span data-ttu-id="66c5f-166">**`RunSettings`** değişkenlerinden</span><span class="sxs-lookup"><span data-stu-id="66c5f-166">**`RunSettings`** arguments</span></span>

  <span data-ttu-id="66c5f-167">Bağımsız değişkenler test için `RunSettings` yapılandırma olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="66c5f-167">Arguments are passed as `RunSettings` configurations for the test.</span></span> <span data-ttu-id="66c5f-168">Bağımsız değişkenler "- `[name]=[value]` -" sonra çift olarak belirtilir (--sonra boşluk bırakın).</span><span class="sxs-lookup"><span data-stu-id="66c5f-168">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="66c5f-169">Birden çok `[name]=[value]` çifti ayırmak için bir boşluk kullanılır.</span><span class="sxs-lookup"><span data-stu-id="66c5f-169">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="66c5f-170">Örnek: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="66c5f-170">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="66c5f-171">Daha fazla bilgi için bkz. [komut satırı aracılığıyla RunSettings bağımsız değişkenlerini geçirme](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="66c5f-171">For more information, see [Passing RunSettings arguments through command line](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="66c5f-172">Örnekler</span><span class="sxs-lookup"><span data-stu-id="66c5f-172">Examples</span></span>

- <span data-ttu-id="66c5f-173">Projedeki testleri geçerli dizinde çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="66c5f-173">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="66c5f-174">`test1` Projedeki testleri çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="66c5f-174">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="66c5f-175">Projedeki testleri geçerli dizinde çalıştırın ve TRX biçiminde bir test sonuçları dosyası oluşturun:</span><span class="sxs-lookup"><span data-stu-id="66c5f-175">Run the tests in the project in the current directory, and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

- <span data-ttu-id="66c5f-176">Projedeki testleri geçerli dizinde çalıştırın ve konsolun ayrıntılı ayrıntı düzeyi ile günlüğe kaydedin:</span><span class="sxs-lookup"><span data-stu-id="66c5f-176">Run the tests in the project in the current directory, and log with detailed verbosity to the console:</span></span>

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```

## <a name="filter-option-details"></a><span data-ttu-id="66c5f-177">Filtre seçeneği ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="66c5f-177">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="66c5f-178">`<Expression>`biçimindedir `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="66c5f-178">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="66c5f-179">`<property>`, `Test Case`öğesinin bir özniteliğidir.</span><span class="sxs-lookup"><span data-stu-id="66c5f-179">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="66c5f-180">Popüler birim testi çerçeveleri tarafından desteklenen özellikler aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="66c5f-180">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="66c5f-181">Test çerçevesi</span><span class="sxs-lookup"><span data-stu-id="66c5f-181">Test Framework</span></span> | <span data-ttu-id="66c5f-182">Desteklenen özellikler</span><span class="sxs-lookup"><span data-stu-id="66c5f-182">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="66c5f-183">MSTest</span><span class="sxs-lookup"><span data-stu-id="66c5f-183">MSTest</span></span>         | <ul><li><span data-ttu-id="66c5f-184">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="66c5f-184">FullyQualifiedName</span></span></li><li><span data-ttu-id="66c5f-185">Adı</span><span class="sxs-lookup"><span data-stu-id="66c5f-185">Name</span></span></li><li><span data-ttu-id="66c5f-186">Sınıf</span><span class="sxs-lookup"><span data-stu-id="66c5f-186">ClassName</span></span></li><li><span data-ttu-id="66c5f-187">Öncelik</span><span class="sxs-lookup"><span data-stu-id="66c5f-187">Priority</span></span></li><li><span data-ttu-id="66c5f-188">TestCategory</span><span class="sxs-lookup"><span data-stu-id="66c5f-188">TestCategory</span></span></li></ul> |
| <span data-ttu-id="66c5f-189">xUnit</span><span class="sxs-lookup"><span data-stu-id="66c5f-189">xUnit</span></span>          | <ul><li><span data-ttu-id="66c5f-190">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="66c5f-190">FullyQualifiedName</span></span></li><li><span data-ttu-id="66c5f-191">DisplayName</span><span class="sxs-lookup"><span data-stu-id="66c5f-191">DisplayName</span></span></li><li><span data-ttu-id="66c5f-192">Lerdir</span><span class="sxs-lookup"><span data-stu-id="66c5f-192">Traits</span></span></li></ul>                                   |

<span data-ttu-id="66c5f-193">, `<operator>` Özelliği ve değeri arasındaki ilişkiyi açıklar:</span><span class="sxs-lookup"><span data-stu-id="66c5f-193">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="66c5f-194">İşleç</span><span class="sxs-lookup"><span data-stu-id="66c5f-194">Operator</span></span> | <span data-ttu-id="66c5f-195">İşlev</span><span class="sxs-lookup"><span data-stu-id="66c5f-195">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="66c5f-196">Tam eşleşme</span><span class="sxs-lookup"><span data-stu-id="66c5f-196">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="66c5f-197">Tam eşleşme yok</span><span class="sxs-lookup"><span data-stu-id="66c5f-197">Not exact match</span></span> |
| `~`      | <span data-ttu-id="66c5f-198">Contains</span><span class="sxs-lookup"><span data-stu-id="66c5f-198">Contains</span></span>        |
| `!~`     | <span data-ttu-id="66c5f-199">İçermez</span><span class="sxs-lookup"><span data-stu-id="66c5f-199">Not contains</span></span>    |

<span data-ttu-id="66c5f-200">`<value>`bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="66c5f-200">`<value>` is a string.</span></span> <span data-ttu-id="66c5f-201">Tüm aramalar büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="66c5f-201">All the lookups are case insensitive.</span></span>

<span data-ttu-id="66c5f-202">`<operator>` Bir ifadesi, otomatik olarak `contains` on `FullyQualifiedName` özelliği olarak kabul edilir (örneğin, `dotnet test --filter xyz` ile `dotnet test --filter FullyQualifiedName~xyz`aynıdır).</span><span class="sxs-lookup"><span data-stu-id="66c5f-202">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="66c5f-203">İfadeler koşullu işleçlerle birleştirilebilecek:</span><span class="sxs-lookup"><span data-stu-id="66c5f-203">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="66c5f-204">İşleç</span><span class="sxs-lookup"><span data-stu-id="66c5f-204">Operator</span></span>            | <span data-ttu-id="66c5f-205">İşlev</span><span class="sxs-lookup"><span data-stu-id="66c5f-205">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="66c5f-206">OR</span><span class="sxs-lookup"><span data-stu-id="66c5f-206">OR</span></span>       |
| `&`                 | <span data-ttu-id="66c5f-207">AND</span><span class="sxs-lookup"><span data-stu-id="66c5f-207">AND</span></span>      |

<span data-ttu-id="66c5f-208">Koşullu işleçler kullandığınızda (örneğin, `(Name~TestMethod1) | (Name~TestMethod2)`) ifadeleri parantez içine alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66c5f-208">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="66c5f-209">Seçmeli birim testi filtrelemeyi kullanma hakkında daha fazla bilgi ve örnekler için bkz. [Seçmeli birim testlerini çalıştırma](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="66c5f-209">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="66c5f-210">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66c5f-210">See also</span></span>

- [<span data-ttu-id="66c5f-211">Çerçeveler ve hedefler</span><span class="sxs-lookup"><span data-stu-id="66c5f-211">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="66c5f-212">.NET Core çalışma zamanı tanımlayıcısı (RID) kataloğu</span><span class="sxs-lookup"><span data-stu-id="66c5f-212">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="66c5f-213">Komut satırı aracılığıyla runsettings bağımsız değişkenlerini geçirme</span><span class="sxs-lookup"><span data-stu-id="66c5f-213">Passing runsettings arguments through commandline</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
