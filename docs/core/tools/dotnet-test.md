---
title: dotnet test komutu
description: Dotnet test komutu, belirli bir projede birim testlerini yürütmek için kullanılır.
ms.date: 02/27/2020
ms.openlocfilehash: bac2f0e613c34bc9f657551a5eac4038207a93ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847904"
---
# <a name="dotnet-test"></a><span data-ttu-id="bd46a-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="bd46a-103">dotnet test</span></span>

<span data-ttu-id="bd46a-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 2.1 SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="bd46a-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="bd46a-105">Adı</span><span class="sxs-lookup"><span data-stu-id="bd46a-105">Name</span></span>

<span data-ttu-id="bd46a-106">`dotnet test`- .NET test sürücüsü birim testleri yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bd46a-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="bd46a-107">Özet</span><span class="sxs-lookup"><span data-stu-id="bd46a-107">Synopsis</span></span>

```dotnetcli
dotnet test [<PROJECT> | <SOLUTION>]
    [-a|--test-adapter-path] [--blame] [-c|--configuration]
    [--collect] [-d|--diag] [-f|--framework] [--filter]
    [--interactive] [-l|--logger] [--no-build] [--nologo]
    [--no-restore] [-o|--output] [-r|--results-directory]
    [--runtime] [-s|--settings] [-t|--list-tests]
    [-v|--verbosity] [[--] <RunSettings arguments>]

dotnet test [-h|--help]
```

## <a name="description"></a><span data-ttu-id="bd46a-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bd46a-108">Description</span></span>

<span data-ttu-id="bd46a-109">Komut, `dotnet test` belirli bir projede birim testlerini yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bd46a-109">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="bd46a-110">Komut, `dotnet test` proje için belirtilen test runner konsolu uygulamasını başlatır.</span><span class="sxs-lookup"><span data-stu-id="bd46a-110">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="bd46a-111">Test runner bir birim test çerçevesi (örneğin, MSTest, NUnit veya xUnit) için tanımlanan testleri yürütür ve her testin başarısını veya başarısızlığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="bd46a-111">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="bd46a-112">Tüm testler başarılı olursa, test koşucusu çıkış kodu olarak 0 döndürür; aksi takdirde herhangi bir test başarısız olursa, 1 döndürür.</span><span class="sxs-lookup"><span data-stu-id="bd46a-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="bd46a-113">Test koşucusu ve birim test kitaplığı NuGet paketleri olarak paketlenir ve proje için olağan bağımlılıklar olarak geri yüklenir.</span><span class="sxs-lookup"><span data-stu-id="bd46a-113">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="bd46a-114">Test projeleri, aşağıdaki örnek `<PackageReference>` proje dosyasında görüldüğü gibi, sıradan bir öğe kullanarak test koşucusu belirtir:</span><span class="sxs-lookup"><span data-stu-id="bd46a-114">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="bd46a-115">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="bd46a-115">Arguments</span></span>

- **`PROJECT | SOLUTION`**

  <span data-ttu-id="bd46a-116">Test projesine veya çözüme giden yol.</span><span class="sxs-lookup"><span data-stu-id="bd46a-116">Path to the test project or solution.</span></span> <span data-ttu-id="bd46a-117">Belirtilmemişse, varsayılan olarak geçerli dizini alır.</span><span class="sxs-lookup"><span data-stu-id="bd46a-117">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="bd46a-118">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="bd46a-118">Options</span></span>

- **`a|--test-adapter-path <PATH_TO_ADAPTER>`**

  <span data-ttu-id="bd46a-119">Test çalışmasında belirtilen yoldan özel test bağdaştırıcılarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="bd46a-119">Use the custom test adapters from the specified path in the test run.</span></span>

- **`-blame`**

  <span data-ttu-id="bd46a-120">Testleri suçlama modunda çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="bd46a-120">Runs the tests in blame mode.</span></span> <span data-ttu-id="bd46a-121">Bu seçenek, test ana bilgisayarının çökmesine neden olan sorunlu testleri yalıtmada yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="bd46a-121">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="bd46a-122">Bu, çökmeden önce testlerin yürütülmesi sırasını yakalayan *Sequence.xml* olarak geçerli dizinde bir çıktı dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bd46a-122">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="bd46a-123">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bd46a-123">Defines the build configuration.</span></span> <span data-ttu-id="bd46a-124">Varsayılan değer, `Debug`ancak projenizin yapılandırmabu varsayılan SDK ayarını geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="bd46a-124">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`-collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  <span data-ttu-id="bd46a-125">Test çalışması için veri toplayıcısını sağlar.</span><span class="sxs-lookup"><span data-stu-id="bd46a-125">Enables data collector for the test run.</span></span> <span data-ttu-id="bd46a-126">Daha fazla bilgi için, [bkz.](https://aka.ms/vstest-collect)</span><span class="sxs-lookup"><span data-stu-id="bd46a-126">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

- **`d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  <span data-ttu-id="bd46a-127">Test platformu için tanılama modunu etkinleştirin ve belirtilen dosyaya tanılama iletileri yazar.</span><span class="sxs-lookup"><span data-stu-id="bd46a-127">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

- **`f|--framework <FRAMEWORK>`**

  <span data-ttu-id="bd46a-128">Belirli bir [çerçeve](../../standard/frameworks.md)için test ikilileri arar.</span><span class="sxs-lookup"><span data-stu-id="bd46a-128">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="bd46a-129">Verilen ifadeyi kullanarak geçerli projedeki testleri filtreler.</span><span class="sxs-lookup"><span data-stu-id="bd46a-129">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="bd46a-130">Daha fazla bilgi için [Filtre seçeneği ayrıntıları](#filter-option-details) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="bd46a-130">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="bd46a-131">Seçici birim test filtrelemenin nasıl kullanılacağı hakkında daha fazla bilgi ve örnekler için seçici [birim testlerini çalıştırma'ya](../testing/selective-unit-tests.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="bd46a-131">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`h|--help`**

  <span data-ttu-id="bd46a-132">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="bd46a-132">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="bd46a-133">Komutun durmasını ve kullanıcı girişi veya eylemini beklemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="bd46a-133">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="bd46a-134">Örneğin, kimlik doğrulamasını tamamlamak için.</span><span class="sxs-lookup"><span data-stu-id="bd46a-134">For example, to complete authentication.</span></span> <span data-ttu-id="bd46a-135">.NET Core 3.0 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="bd46a-135">Available since .NET Core 3.0 SDK.</span></span>

- **`l|--logger <LoggerUri/FriendlyName>`**

  <span data-ttu-id="bd46a-136">Test sonuçları için bir logger belirtir.</span><span class="sxs-lookup"><span data-stu-id="bd46a-136">Specifies a logger for test results.</span></span>

- **`--no-build`**

  <span data-ttu-id="bd46a-137">Çalıştırmadan önce test projesini oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="bd46a-137">Doesn't build the test project before running it.</span></span> <span data-ttu-id="bd46a-138">Ayrıca örtülü olarak - `--no-restore` bayrak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bd46a-138">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--nologo`**

  <span data-ttu-id="bd46a-139">Microsoft TestPlatform banner'ını görüntülemeden testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="bd46a-139">Run tests without displaying the Microsoft TestPlatform banner.</span></span> <span data-ttu-id="bd46a-140">.NET Core 3.0 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="bd46a-140">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="bd46a-141">Komutu çalıştırırken örtük bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="bd46a-141">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="bd46a-142">Hangi çalıştırmak için ikili bulmak için dizin.</span><span class="sxs-lookup"><span data-stu-id="bd46a-142">Directory in which to find the binaries to run.</span></span>

- **`-r|--results-directory <PATH>`**

  <span data-ttu-id="bd46a-143">Test sonuçlarının yerleştirilebileceği dizin.</span><span class="sxs-lookup"><span data-stu-id="bd46a-143">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="bd46a-144">Belirtilen dizin yoksa oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="bd46a-144">If the specified directory doesn't exist, it's created.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="bd46a-145">Test etmek için hedef çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="bd46a-145">The target runtime to test for.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="bd46a-146">Testleri `.runsettings` çalıştırmak için kullanılacak dosya.</span><span class="sxs-lookup"><span data-stu-id="bd46a-146">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="bd46a-147">Birim testlerini bir `.runsettings` dosya kullanarak yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="bd46a-147">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)

- **`-t|--list-tests`**

  <span data-ttu-id="bd46a-148">Geçerli projede keşfedilen tüm testleri listele.</span><span class="sxs-lookup"><span data-stu-id="bd46a-148">List all of the discovered tests in the current project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="bd46a-149">Komutun ayrıntılı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bd46a-149">Sets the verbosity level of the command.</span></span> <span data-ttu-id="bd46a-150">İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve .</span><span class="sxs-lookup"><span data-stu-id="bd46a-150">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- <span data-ttu-id="bd46a-151">`RunSettings`Bağımsız değişken</span><span class="sxs-lookup"><span data-stu-id="bd46a-151">`RunSettings` arguments</span></span>

  <span data-ttu-id="bd46a-152">Bağımsız değişkenler `RunSettings` test için yapılandırmaolarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="bd46a-152">Arguments are passed as `RunSettings` configurations for the test.</span></span> <span data-ttu-id="bd46a-153">Bağımsız değişkenler `[name]=[value]` "-- " (sonra daki boşluğa dikkat ......</span><span class="sxs-lookup"><span data-stu-id="bd46a-153">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="bd46a-154">Bir boşluk birden çok `[name]=[value]` çifti ayırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bd46a-154">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="bd46a-155">Örnek: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="bd46a-155">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="bd46a-156">Daha fazla bilgi için [vstest.console.exe: RunSettings args'ı geçmek](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="bd46a-156">For more information, see [vstest.console.exe: Passing RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="bd46a-157">Örnekler</span><span class="sxs-lookup"><span data-stu-id="bd46a-157">Examples</span></span>

- <span data-ttu-id="bd46a-158">Projedeki testleri geçerli dizinde çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="bd46a-158">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="bd46a-159">Projedeki testleri `test1` çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="bd46a-159">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="bd46a-160">Projedeki testleri geçerli dizinde çalıştırın ve trx formatında bir test sonuçları dosyası oluşturun:</span><span class="sxs-lookup"><span data-stu-id="bd46a-160">Run the tests in the project in the current directory and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

## <a name="filter-option-details"></a><span data-ttu-id="bd46a-161">Filtre seçeneği ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="bd46a-161">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="bd46a-162">`<Expression>`biçimi `<property><operator><value>[|&<Expression>]`vardır.</span><span class="sxs-lookup"><span data-stu-id="bd46a-162">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="bd46a-163">`<property>`bir `Test Case`özelliktir.</span><span class="sxs-lookup"><span data-stu-id="bd46a-163">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="bd46a-164">Popüler birim test çerçeveleri tarafından desteklenen özellikler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="bd46a-164">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="bd46a-165">Test Çerçevesi</span><span class="sxs-lookup"><span data-stu-id="bd46a-165">Test Framework</span></span> | <span data-ttu-id="bd46a-166">Desteklenen özellikler</span><span class="sxs-lookup"><span data-stu-id="bd46a-166">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="bd46a-167">MSTest</span><span class="sxs-lookup"><span data-stu-id="bd46a-167">MSTest</span></span>         | <ul><li><span data-ttu-id="bd46a-168">Fullyqualifiedname</span><span class="sxs-lookup"><span data-stu-id="bd46a-168">FullyQualifiedName</span></span></li><li><span data-ttu-id="bd46a-169">Adı</span><span class="sxs-lookup"><span data-stu-id="bd46a-169">Name</span></span></li><li><span data-ttu-id="bd46a-170">Classname</span><span class="sxs-lookup"><span data-stu-id="bd46a-170">ClassName</span></span></li><li><span data-ttu-id="bd46a-171">Öncelik</span><span class="sxs-lookup"><span data-stu-id="bd46a-171">Priority</span></span></li><li><span data-ttu-id="bd46a-172">TestKategorisi</span><span class="sxs-lookup"><span data-stu-id="bd46a-172">TestCategory</span></span></li></ul> |
| <span data-ttu-id="bd46a-173">xBirim</span><span class="sxs-lookup"><span data-stu-id="bd46a-173">xUnit</span></span>          | <ul><li><span data-ttu-id="bd46a-174">Fullyqualifiedname</span><span class="sxs-lookup"><span data-stu-id="bd46a-174">FullyQualifiedName</span></span></li><li><span data-ttu-id="bd46a-175">DisplayName</span><span class="sxs-lookup"><span data-stu-id="bd46a-175">DisplayName</span></span></li><li><span data-ttu-id="bd46a-176">Özellik</span><span class="sxs-lookup"><span data-stu-id="bd46a-176">Traits</span></span></li></ul>                                   |

<span data-ttu-id="bd46a-177">Özellik `<operator>` ve değer arasındaki ilişkiyi açıklar:</span><span class="sxs-lookup"><span data-stu-id="bd46a-177">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="bd46a-178">İşleç</span><span class="sxs-lookup"><span data-stu-id="bd46a-178">Operator</span></span> | <span data-ttu-id="bd46a-179">İşlev</span><span class="sxs-lookup"><span data-stu-id="bd46a-179">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="bd46a-180">Tam eşleşme</span><span class="sxs-lookup"><span data-stu-id="bd46a-180">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="bd46a-181">Tam eşleşme yok</span><span class="sxs-lookup"><span data-stu-id="bd46a-181">Not exact match</span></span> |
| `~`      | <span data-ttu-id="bd46a-182">Contains</span><span class="sxs-lookup"><span data-stu-id="bd46a-182">Contains</span></span>        |
| `!~`     | <span data-ttu-id="bd46a-183">İçermez</span><span class="sxs-lookup"><span data-stu-id="bd46a-183">Not contains</span></span>    |

<span data-ttu-id="bd46a-184">`<value>`bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="bd46a-184">`<value>` is a string.</span></span> <span data-ttu-id="bd46a-185">Tüm aramalar duyarsız.</span><span class="sxs-lookup"><span data-stu-id="bd46a-185">All the lookups are case insensitive.</span></span>

<span data-ttu-id="bd46a-186">Bir ifadesi `<operator>` olmayan bir `contains` ifade otomatik `FullyQualifiedName` olarak açık `dotnet test --filter xyz` özellik olarak `dotnet test --filter FullyQualifiedName~xyz`kabul edilir (örneğin, aynıdır).</span><span class="sxs-lookup"><span data-stu-id="bd46a-186">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="bd46a-187">İfadeler koşullu işleçlerle birleşebilir:</span><span class="sxs-lookup"><span data-stu-id="bd46a-187">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="bd46a-188">İşleç</span><span class="sxs-lookup"><span data-stu-id="bd46a-188">Operator</span></span>            | <span data-ttu-id="bd46a-189">İşlev</span><span class="sxs-lookup"><span data-stu-id="bd46a-189">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="bd46a-190">OR</span><span class="sxs-lookup"><span data-stu-id="bd46a-190">OR</span></span>       |
| `&`                 | <span data-ttu-id="bd46a-191">AND</span><span class="sxs-lookup"><span data-stu-id="bd46a-191">AND</span></span>      |

<span data-ttu-id="bd46a-192">Koşullu işleçleri kullanırken ifadeleri parantez içine alabilirsiniz (örneğin, `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="bd46a-192">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="bd46a-193">Seçici birim test filtrelemenin nasıl kullanılacağı hakkında daha fazla bilgi ve örnekler için seçici [birim testlerini çalıştırma'ya](../testing/selective-unit-tests.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="bd46a-193">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bd46a-194">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd46a-194">See also</span></span>

- [<span data-ttu-id="bd46a-195">Çerçeveler ve Hedefler</span><span class="sxs-lookup"><span data-stu-id="bd46a-195">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="bd46a-196">.NET Core Runtime Tanımlayıcı (RID) kataloğu</span><span class="sxs-lookup"><span data-stu-id="bd46a-196">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
