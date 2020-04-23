---
title: dotnet test komutu
description: Dotnet test komutu, belirli bir projede birim testlerini yürütmek için kullanılır.
ms.date: 02/27/2020
ms.openlocfilehash: 69b8101f9b1052f4726dce8a86234da99f5dc89c
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102755"
---
# <a name="dotnet-test"></a><span data-ttu-id="29b76-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="29b76-103">dotnet test</span></span>

<span data-ttu-id="29b76-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 2.1 SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="29b76-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="29b76-105">Adı</span><span class="sxs-lookup"><span data-stu-id="29b76-105">Name</span></span>

<span data-ttu-id="29b76-106">`dotnet test`- .NET test sürücüsü birim testleri yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="29b76-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="29b76-107">Özet</span><span class="sxs-lookup"><span data-stu-id="29b76-107">Synopsis</span></span>

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

## <a name="description"></a><span data-ttu-id="29b76-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="29b76-108">Description</span></span>

<span data-ttu-id="29b76-109">Komut, `dotnet test` belirli bir projede birim testlerini yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="29b76-109">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="29b76-110">Komut, `dotnet test` proje için belirtilen test runner konsolu uygulamasını başlatır.</span><span class="sxs-lookup"><span data-stu-id="29b76-110">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="29b76-111">Test runner bir birim test çerçevesi (örneğin, MSTest, NUnit veya xUnit) için tanımlanan testleri yürütür ve her testin başarısını veya başarısızlığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="29b76-111">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="29b76-112">Tüm testler başarılı olursa, test koşucusu çıkış kodu olarak 0 döndürür; aksi takdirde herhangi bir test başarısız olursa, 1 döndürür.</span><span class="sxs-lookup"><span data-stu-id="29b76-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="29b76-113">Test koşucusu ve birim test kitaplığı NuGet paketleri olarak paketlenir ve proje için olağan bağımlılıklar olarak geri yüklenir.</span><span class="sxs-lookup"><span data-stu-id="29b76-113">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="29b76-114">Test projeleri, aşağıdaki örnek `<PackageReference>` proje dosyasında görüldüğü gibi, sıradan bir öğe kullanarak test koşucusu belirtir:</span><span class="sxs-lookup"><span data-stu-id="29b76-114">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

### <a name="implicit-restore"></a><span data-ttu-id="29b76-115">Örtük geri yükleme</span><span class="sxs-lookup"><span data-stu-id="29b76-115">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="29b76-116">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="29b76-116">Arguments</span></span>

- **`PROJECT | SOLUTION`**

  <span data-ttu-id="29b76-117">Test projesine veya çözüme giden yol.</span><span class="sxs-lookup"><span data-stu-id="29b76-117">Path to the test project or solution.</span></span> <span data-ttu-id="29b76-118">Belirtilmemişse, varsayılan olarak geçerli dizini alır.</span><span class="sxs-lookup"><span data-stu-id="29b76-118">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="29b76-119">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="29b76-119">Options</span></span>

- **`-a|--test-adapter-path <PATH_TO_ADAPTER>`**

  <span data-ttu-id="29b76-120">Test çalışmasında belirtilen yoldan özel test bağdaştırıcılarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="29b76-120">Use the custom test adapters from the specified path in the test run.</span></span>

- **`--blame`**

  <span data-ttu-id="29b76-121">Testleri suçlama modunda çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="29b76-121">Runs the tests in blame mode.</span></span> <span data-ttu-id="29b76-122">Bu seçenek, test ana bilgisayarının çökmesine neden olan sorunlu testleri yalıtmada yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="29b76-122">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="29b76-123">Bu, çökmeden önce testlerin yürütülmesi sırasını yakalayan *Sequence.xml* olarak geçerli dizinde bir çıktı dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="29b76-123">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="29b76-124">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="29b76-124">Defines the build configuration.</span></span> <span data-ttu-id="29b76-125">Varsayılan değer, `Debug`ancak projenizin yapılandırmabu varsayılan SDK ayarını geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="29b76-125">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  <span data-ttu-id="29b76-126">Test çalışması için veri toplayıcısını sağlar.</span><span class="sxs-lookup"><span data-stu-id="29b76-126">Enables data collector for the test run.</span></span> <span data-ttu-id="29b76-127">Daha fazla bilgi için, [bkz.](https://aka.ms/vstest-collect)</span><span class="sxs-lookup"><span data-stu-id="29b76-127">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

- **`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  <span data-ttu-id="29b76-128">Test platformu için tanılama modunu etkinleştirir ve belirtilen dosyaya tanılama iletileri yazar.</span><span class="sxs-lookup"><span data-stu-id="29b76-128">Enables diagnostic mode for the test platform and writes diagnostic messages to the specified file.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="29b76-129">Belirli bir [çerçeve](../../standard/frameworks.md)için test ikilileri arar.</span><span class="sxs-lookup"><span data-stu-id="29b76-129">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="29b76-130">Verilen ifadeyi kullanarak geçerli projedeki testleri filtreler.</span><span class="sxs-lookup"><span data-stu-id="29b76-130">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="29b76-131">Daha fazla bilgi için [Filtre seçeneği ayrıntıları](#filter-option-details) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="29b76-131">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="29b76-132">Seçici birim test filtrelemenin nasıl kullanılacağı hakkında daha fazla bilgi ve örnekler için seçici [birim testlerini çalıştırma'ya](../testing/selective-unit-tests.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="29b76-132">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="29b76-133">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="29b76-133">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="29b76-134">Komutun durmasını ve kullanıcı girişi veya eylemini beklemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="29b76-134">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="29b76-135">Örneğin, kimlik doğrulamasını tamamlamak için.</span><span class="sxs-lookup"><span data-stu-id="29b76-135">For example, to complete authentication.</span></span> <span data-ttu-id="29b76-136">.NET Core 3.0 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="29b76-136">Available since .NET Core 3.0 SDK.</span></span>

- **`-l|--logger <LOGGER_URI/FRIENDLY_NAME>`**

  <span data-ttu-id="29b76-137">Test sonuçları için bir logger belirtir.</span><span class="sxs-lookup"><span data-stu-id="29b76-137">Specifies a logger for test results.</span></span> <span data-ttu-id="29b76-138">MSBuild aksine, dotnet testi kısaltmalar kabul `-l "console;v=d"` etmez: yerine kullanım `-l "console;verbosity=detailed"`.</span><span class="sxs-lookup"><span data-stu-id="29b76-138">Unlike MSBuild, dotnet test doesn't accept abbreviations: instead of `-l "console;v=d"` use `-l "console;verbosity=detailed"`.</span></span>

- **`--no-build`**

  <span data-ttu-id="29b76-139">Çalıştırmadan önce test projesini oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="29b76-139">Doesn't build the test project before running it.</span></span> <span data-ttu-id="29b76-140">Ayrıca örtülü olarak - `--no-restore` bayrak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="29b76-140">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--nologo`**

  <span data-ttu-id="29b76-141">Microsoft TestPlatform banner'ını görüntülemeden testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="29b76-141">Run tests without displaying the Microsoft TestPlatform banner.</span></span> <span data-ttu-id="29b76-142">.NET Core 3.0 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="29b76-142">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="29b76-143">Komutu çalıştırırken örtük bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="29b76-143">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="29b76-144">Hangi çalıştırmak için ikili bulmak için dizin.</span><span class="sxs-lookup"><span data-stu-id="29b76-144">Directory in which to find the binaries to run.</span></span> <span data-ttu-id="29b76-145">Belirtilmemişse, varsayılan `./bin/<configuration>/<framework>/`yol .</span><span class="sxs-lookup"><span data-stu-id="29b76-145">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="29b76-146">Birden çok hedef çerçevesi olan `TargetFrameworks` projelerde (özellik üzerinden), bu seçeneği belirttiğinizi de tanımlamanız `--framework` gerekir.</span><span class="sxs-lookup"><span data-stu-id="29b76-146">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span>

- **`-r|--results-directory <PATH>`**

  <span data-ttu-id="29b76-147">Test sonuçlarının yerleştirilebileceği dizin.</span><span class="sxs-lookup"><span data-stu-id="29b76-147">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="29b76-148">Belirtilen dizin yoksa oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="29b76-148">If the specified directory doesn't exist, it's created.</span></span> <span data-ttu-id="29b76-149">Varsayılan değer, proje dosyasını içeren dizindedir. `TestResults`</span><span class="sxs-lookup"><span data-stu-id="29b76-149">The default is `TestResults` in the directory that contains the project file.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="29b76-150">Test etmek için hedef çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="29b76-150">The target runtime to test for.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="29b76-151">Testleri `.runsettings` çalıştırmak için kullanılacak dosya.</span><span class="sxs-lookup"><span data-stu-id="29b76-151">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="29b76-152">Birim testlerini bir `.runsettings` dosya kullanarak yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="29b76-152">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)

- **`-t|--list-tests`**

  <span data-ttu-id="29b76-153">Geçerli projede keşfedilen tüm testleri listele.</span><span class="sxs-lookup"><span data-stu-id="29b76-153">List all of the discovered tests in the current project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="29b76-154">Komutun ayrıntılı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="29b76-154">Sets the verbosity level of the command.</span></span> <span data-ttu-id="29b76-155">İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve .</span><span class="sxs-lookup"><span data-stu-id="29b76-155">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="29b76-156">Varsayılan değer: `minimal`.</span><span class="sxs-lookup"><span data-stu-id="29b76-156">The default is `minimal`.</span></span> <span data-ttu-id="29b76-157">Daha fazla bilgi için bkz. <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span><span class="sxs-lookup"><span data-stu-id="29b76-157">For more information, see <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span></span>

- <span data-ttu-id="29b76-158">**`RunSettings`** Bağımsız değişken</span><span class="sxs-lookup"><span data-stu-id="29b76-158">**`RunSettings`** arguments</span></span>

  <span data-ttu-id="29b76-159">Bağımsız değişkenler `RunSettings` test için yapılandırmaolarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="29b76-159">Arguments are passed as `RunSettings` configurations for the test.</span></span> <span data-ttu-id="29b76-160">Bağımsız değişkenler `[name]=[value]` "-- " (sonra daki boşluğa dikkat ......</span><span class="sxs-lookup"><span data-stu-id="29b76-160">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="29b76-161">Bir boşluk birden çok `[name]=[value]` çifti ayırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="29b76-161">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="29b76-162">Örnek: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="29b76-162">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="29b76-163">Daha fazla bilgi için [bkz.](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)</span><span class="sxs-lookup"><span data-stu-id="29b76-163">For more information, see [Passing RunSettings arguments through command line](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="29b76-164">Örnekler</span><span class="sxs-lookup"><span data-stu-id="29b76-164">Examples</span></span>

- <span data-ttu-id="29b76-165">Projedeki testleri geçerli dizinde çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="29b76-165">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="29b76-166">Projedeki testleri `test1` çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="29b76-166">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="29b76-167">Projedeki testleri geçerli dizinde çalıştırın ve trx formatında bir test sonuçları dosyası oluşturun:</span><span class="sxs-lookup"><span data-stu-id="29b76-167">Run the tests in the project in the current directory, and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

- <span data-ttu-id="29b76-168">Projedeki testleri geçerli dizinde çalıştırın ve konsola ayrıntılı ayrıntılı bilgi yle günlüğe kaydedin:</span><span class="sxs-lookup"><span data-stu-id="29b76-168">Run the tests in the project in the current directory, and log with detailed verbosity to the console:</span></span>

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```

## <a name="filter-option-details"></a><span data-ttu-id="29b76-169">Filtre seçeneği ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="29b76-169">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="29b76-170">`<Expression>`biçimi `<property><operator><value>[|&<Expression>]`vardır.</span><span class="sxs-lookup"><span data-stu-id="29b76-170">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="29b76-171">`<property>`bir `Test Case`özelliktir.</span><span class="sxs-lookup"><span data-stu-id="29b76-171">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="29b76-172">Popüler birim test çerçeveleri tarafından desteklenen özellikler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="29b76-172">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="29b76-173">Test Çerçevesi</span><span class="sxs-lookup"><span data-stu-id="29b76-173">Test Framework</span></span> | <span data-ttu-id="29b76-174">Desteklenen özellikler</span><span class="sxs-lookup"><span data-stu-id="29b76-174">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="29b76-175">MSTest</span><span class="sxs-lookup"><span data-stu-id="29b76-175">MSTest</span></span>         | <ul><li><span data-ttu-id="29b76-176">Fullyqualifiedname</span><span class="sxs-lookup"><span data-stu-id="29b76-176">FullyQualifiedName</span></span></li><li><span data-ttu-id="29b76-177">Adı</span><span class="sxs-lookup"><span data-stu-id="29b76-177">Name</span></span></li><li><span data-ttu-id="29b76-178">Classname</span><span class="sxs-lookup"><span data-stu-id="29b76-178">ClassName</span></span></li><li><span data-ttu-id="29b76-179">Öncelik</span><span class="sxs-lookup"><span data-stu-id="29b76-179">Priority</span></span></li><li><span data-ttu-id="29b76-180">TestKategorisi</span><span class="sxs-lookup"><span data-stu-id="29b76-180">TestCategory</span></span></li></ul> |
| <span data-ttu-id="29b76-181">xBirim</span><span class="sxs-lookup"><span data-stu-id="29b76-181">xUnit</span></span>          | <ul><li><span data-ttu-id="29b76-182">Fullyqualifiedname</span><span class="sxs-lookup"><span data-stu-id="29b76-182">FullyQualifiedName</span></span></li><li><span data-ttu-id="29b76-183">DisplayName</span><span class="sxs-lookup"><span data-stu-id="29b76-183">DisplayName</span></span></li><li><span data-ttu-id="29b76-184">Özellik</span><span class="sxs-lookup"><span data-stu-id="29b76-184">Traits</span></span></li></ul>                                   |

<span data-ttu-id="29b76-185">Özellik `<operator>` ve değer arasındaki ilişkiyi açıklar:</span><span class="sxs-lookup"><span data-stu-id="29b76-185">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="29b76-186">İşleç</span><span class="sxs-lookup"><span data-stu-id="29b76-186">Operator</span></span> | <span data-ttu-id="29b76-187">İşlev</span><span class="sxs-lookup"><span data-stu-id="29b76-187">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="29b76-188">Tam eşleşme</span><span class="sxs-lookup"><span data-stu-id="29b76-188">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="29b76-189">Tam eşleşme yok</span><span class="sxs-lookup"><span data-stu-id="29b76-189">Not exact match</span></span> |
| `~`      | <span data-ttu-id="29b76-190">Contains</span><span class="sxs-lookup"><span data-stu-id="29b76-190">Contains</span></span>        |
| `!~`     | <span data-ttu-id="29b76-191">İçermez</span><span class="sxs-lookup"><span data-stu-id="29b76-191">Not contains</span></span>    |

<span data-ttu-id="29b76-192">`<value>`bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="29b76-192">`<value>` is a string.</span></span> <span data-ttu-id="29b76-193">Tüm aramalar duyarsız.</span><span class="sxs-lookup"><span data-stu-id="29b76-193">All the lookups are case insensitive.</span></span>

<span data-ttu-id="29b76-194">Bir ifadesi `<operator>` olmayan bir `contains` ifade otomatik `FullyQualifiedName` olarak açık `dotnet test --filter xyz` özellik olarak `dotnet test --filter FullyQualifiedName~xyz`kabul edilir (örneğin, aynıdır).</span><span class="sxs-lookup"><span data-stu-id="29b76-194">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="29b76-195">İfadeler koşullu işleçlerle birleşebilir:</span><span class="sxs-lookup"><span data-stu-id="29b76-195">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="29b76-196">İşleç</span><span class="sxs-lookup"><span data-stu-id="29b76-196">Operator</span></span>            | <span data-ttu-id="29b76-197">İşlev</span><span class="sxs-lookup"><span data-stu-id="29b76-197">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="29b76-198">OR</span><span class="sxs-lookup"><span data-stu-id="29b76-198">OR</span></span>       |
| `&`                 | <span data-ttu-id="29b76-199">AND</span><span class="sxs-lookup"><span data-stu-id="29b76-199">AND</span></span>      |

<span data-ttu-id="29b76-200">Koşullu işleçleri kullanırken ifadeleri parantez içine alabilirsiniz (örneğin, `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="29b76-200">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="29b76-201">Seçici birim test filtrelemenin nasıl kullanılacağı hakkında daha fazla bilgi ve örnekler için seçici [birim testlerini çalıştırma'ya](../testing/selective-unit-tests.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="29b76-201">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="29b76-202">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29b76-202">See also</span></span>

- [<span data-ttu-id="29b76-203">Çerçeveler ve Hedefler</span><span class="sxs-lookup"><span data-stu-id="29b76-203">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="29b76-204">.NET Core Runtime Tanımlayıcı (RID) kataloğu</span><span class="sxs-lookup"><span data-stu-id="29b76-204">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="29b76-205">Çalışma ayarlarını komut satırından geçirme</span><span class="sxs-lookup"><span data-stu-id="29b76-205">Passing runsettings arguments through commandline</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
