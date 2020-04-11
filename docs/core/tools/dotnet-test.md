---
title: dotnet test komutu
description: Dotnet test komutu, belirli bir projede birim testlerini yürütmek için kullanılır.
ms.date: 02/27/2020
ms.openlocfilehash: 359e4522b26e2b59092d55eea3fca575d2afaf1f
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121036"
---
# <a name="dotnet-test"></a><span data-ttu-id="a7cbe-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="a7cbe-103">dotnet test</span></span>

<span data-ttu-id="a7cbe-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 2.1 SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="a7cbe-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="a7cbe-105">Adı</span><span class="sxs-lookup"><span data-stu-id="a7cbe-105">Name</span></span>

<span data-ttu-id="a7cbe-106">`dotnet test`- .NET test sürücüsü birim testleri yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a7cbe-107">Özet</span><span class="sxs-lookup"><span data-stu-id="a7cbe-107">Synopsis</span></span>

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

## <a name="description"></a><span data-ttu-id="a7cbe-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7cbe-108">Description</span></span>

<span data-ttu-id="a7cbe-109">Komut, `dotnet test` belirli bir projede birim testlerini yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-109">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="a7cbe-110">Komut, `dotnet test` proje için belirtilen test runner konsolu uygulamasını başlatır.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-110">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="a7cbe-111">Test runner bir birim test çerçevesi (örneğin, MSTest, NUnit veya xUnit) için tanımlanan testleri yürütür ve her testin başarısını veya başarısızlığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-111">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="a7cbe-112">Tüm testler başarılı olursa, test koşucusu çıkış kodu olarak 0 döndürür; aksi takdirde herhangi bir test başarısız olursa, 1 döndürür.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="a7cbe-113">Test koşucusu ve birim test kitaplığı NuGet paketleri olarak paketlenir ve proje için olağan bağımlılıklar olarak geri yüklenir.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-113">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="a7cbe-114">Test projeleri, aşağıdaki örnek `<PackageReference>` proje dosyasında görüldüğü gibi, sıradan bir öğe kullanarak test koşucusu belirtir:</span><span class="sxs-lookup"><span data-stu-id="a7cbe-114">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="a7cbe-115">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="a7cbe-115">Arguments</span></span>

- **`PROJECT | SOLUTION`**

  <span data-ttu-id="a7cbe-116">Test projesine veya çözüme giden yol.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-116">Path to the test project or solution.</span></span> <span data-ttu-id="a7cbe-117">Belirtilmemişse, varsayılan olarak geçerli dizini alır.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-117">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="a7cbe-118">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="a7cbe-118">Options</span></span>

- **`a|--test-adapter-path <PATH_TO_ADAPTER>`**

  <span data-ttu-id="a7cbe-119">Test çalışmasında belirtilen yoldan özel test bağdaştırıcılarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-119">Use the custom test adapters from the specified path in the test run.</span></span>

- **`--blame`**

  <span data-ttu-id="a7cbe-120">Testleri suçlama modunda çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-120">Runs the tests in blame mode.</span></span> <span data-ttu-id="a7cbe-121">Bu seçenek, test ana bilgisayarının çökmesine neden olan sorunlu testleri yalıtmada yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-121">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="a7cbe-122">Bu, çökmeden önce testlerin yürütülmesi sırasını yakalayan *Sequence.xml* olarak geçerli dizinde bir çıktı dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-122">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="a7cbe-123">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-123">Defines the build configuration.</span></span> <span data-ttu-id="a7cbe-124">Varsayılan değer, `Debug`ancak projenizin yapılandırmabu varsayılan SDK ayarını geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-124">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`-collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  <span data-ttu-id="a7cbe-125">Test çalışması için veri toplayıcısını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-125">Enables data collector for the test run.</span></span> <span data-ttu-id="a7cbe-126">Daha fazla bilgi için, [bkz.](https://aka.ms/vstest-collect)</span><span class="sxs-lookup"><span data-stu-id="a7cbe-126">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

- **`d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  <span data-ttu-id="a7cbe-127">Test platformu için tanılama modunu etkinleştirin ve belirtilen dosyaya tanılama iletileri yazar.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-127">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

- **`f|--framework <FRAMEWORK>`**

  <span data-ttu-id="a7cbe-128">Belirli bir [çerçeve](../../standard/frameworks.md)için test ikilileri arar.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-128">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="a7cbe-129">Verilen ifadeyi kullanarak geçerli projedeki testleri filtreler.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-129">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="a7cbe-130">Daha fazla bilgi için [Filtre seçeneği ayrıntıları](#filter-option-details) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-130">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="a7cbe-131">Seçici birim test filtrelemenin nasıl kullanılacağı hakkında daha fazla bilgi ve örnekler için seçici [birim testlerini çalıştırma'ya](../testing/selective-unit-tests.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-131">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`h|--help`**

  <span data-ttu-id="a7cbe-132">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-132">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="a7cbe-133">Komutun durmasını ve kullanıcı girişi veya eylemini beklemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-133">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="a7cbe-134">Örneğin, kimlik doğrulamasını tamamlamak için.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-134">For example, to complete authentication.</span></span> <span data-ttu-id="a7cbe-135">.NET Core 3.0 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-135">Available since .NET Core 3.0 SDK.</span></span>

- **`l|--logger <LoggerUri/FriendlyName>`**

  <span data-ttu-id="a7cbe-136">Test sonuçları için bir logger belirtir.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-136">Specifies a logger for test results.</span></span> <span data-ttu-id="a7cbe-137">MSBuild aksine, dotnet testi kısaltmalar kabul `-l "console;v=d"` etmez: yerine kullanım `-l "console;verbosity=detailed"`.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-137">Unlike MSBuild, dotnet test doesn't accept abbreviations: instead of `-l "console;v=d"` use `-l "console;verbosity=detailed"`.</span></span>

- **`--no-build`**

  <span data-ttu-id="a7cbe-138">Çalıştırmadan önce test projesini oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-138">Doesn't build the test project before running it.</span></span> <span data-ttu-id="a7cbe-139">Ayrıca örtülü olarak - `--no-restore` bayrak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-139">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--nologo`**

  <span data-ttu-id="a7cbe-140">Microsoft TestPlatform banner'ını görüntülemeden testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-140">Run tests without displaying the Microsoft TestPlatform banner.</span></span> <span data-ttu-id="a7cbe-141">.NET Core 3.0 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-141">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="a7cbe-142">Komutu çalıştırırken örtük bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-142">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="a7cbe-143">Hangi çalıştırmak için ikili bulmak için dizin.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-143">Directory in which to find the binaries to run.</span></span>

- **`-r|--results-directory <PATH>`**

  <span data-ttu-id="a7cbe-144">Test sonuçlarının yerleştirilebileceği dizin.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-144">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="a7cbe-145">Belirtilen dizin yoksa oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-145">If the specified directory doesn't exist, it's created.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="a7cbe-146">Test etmek için hedef çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-146">The target runtime to test for.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="a7cbe-147">Testleri `.runsettings` çalıştırmak için kullanılacak dosya.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-147">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="a7cbe-148">Birim testlerini bir `.runsettings` dosya kullanarak yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-148">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)

- **`-t|--list-tests`**

  <span data-ttu-id="a7cbe-149">Geçerli projede keşfedilen tüm testleri listele.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-149">List all of the discovered tests in the current project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="a7cbe-150">Komutun ayrıntılı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-150">Sets the verbosity level of the command.</span></span> <span data-ttu-id="a7cbe-151">İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve .</span><span class="sxs-lookup"><span data-stu-id="a7cbe-151">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="a7cbe-152">Varsayılan değer: `minimal`.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-152">The default is `minimal`.</span></span> <span data-ttu-id="a7cbe-153">Daha fazla bilgi için bkz. <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-153">For more information, see <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span></span>

- <span data-ttu-id="a7cbe-154">`RunSettings`Bağımsız değişken</span><span class="sxs-lookup"><span data-stu-id="a7cbe-154">`RunSettings` arguments</span></span>

  <span data-ttu-id="a7cbe-155">Bağımsız değişkenler `RunSettings` test için yapılandırmaolarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-155">Arguments are passed as `RunSettings` configurations for the test.</span></span> <span data-ttu-id="a7cbe-156">Bağımsız değişkenler `[name]=[value]` "-- " (sonra daki boşluğa dikkat ......</span><span class="sxs-lookup"><span data-stu-id="a7cbe-156">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="a7cbe-157">Bir boşluk birden çok `[name]=[value]` çifti ayırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-157">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="a7cbe-158">Örnek: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="a7cbe-158">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="a7cbe-159">Daha fazla bilgi için [vstest.console.exe: RunSettings args'ı geçmek](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="a7cbe-159">For more information, see [vstest.console.exe: Passing RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="a7cbe-160">Örnekler</span><span class="sxs-lookup"><span data-stu-id="a7cbe-160">Examples</span></span>

- <span data-ttu-id="a7cbe-161">Projedeki testleri geçerli dizinde çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="a7cbe-161">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="a7cbe-162">Projedeki testleri `test1` çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="a7cbe-162">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="a7cbe-163">Projedeki testleri geçerli dizinde çalıştırın ve trx formatında bir test sonuçları dosyası oluşturun:</span><span class="sxs-lookup"><span data-stu-id="a7cbe-163">Run the tests in the project in the current directory, and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

- <span data-ttu-id="a7cbe-164">Projedeki testleri geçerli dizinde çalıştırın ve konsola ayrıntılı ayrıntılı bilgi yle günlüğe kaydedin:</span><span class="sxs-lookup"><span data-stu-id="a7cbe-164">Run the tests in the project in the current directory, and log with detailed verbosity to the console:</span></span>

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```

## <a name="filter-option-details"></a><span data-ttu-id="a7cbe-165">Filtre seçeneği ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="a7cbe-165">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="a7cbe-166">`<Expression>`biçimi `<property><operator><value>[|&<Expression>]`vardır.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-166">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="a7cbe-167">`<property>`bir `Test Case`özelliktir.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-167">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="a7cbe-168">Popüler birim test çerçeveleri tarafından desteklenen özellikler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="a7cbe-168">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="a7cbe-169">Test Çerçevesi</span><span class="sxs-lookup"><span data-stu-id="a7cbe-169">Test Framework</span></span> | <span data-ttu-id="a7cbe-170">Desteklenen özellikler</span><span class="sxs-lookup"><span data-stu-id="a7cbe-170">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="a7cbe-171">MSTest</span><span class="sxs-lookup"><span data-stu-id="a7cbe-171">MSTest</span></span>         | <ul><li><span data-ttu-id="a7cbe-172">Fullyqualifiedname</span><span class="sxs-lookup"><span data-stu-id="a7cbe-172">FullyQualifiedName</span></span></li><li><span data-ttu-id="a7cbe-173">Adı</span><span class="sxs-lookup"><span data-stu-id="a7cbe-173">Name</span></span></li><li><span data-ttu-id="a7cbe-174">Classname</span><span class="sxs-lookup"><span data-stu-id="a7cbe-174">ClassName</span></span></li><li><span data-ttu-id="a7cbe-175">Öncelik</span><span class="sxs-lookup"><span data-stu-id="a7cbe-175">Priority</span></span></li><li><span data-ttu-id="a7cbe-176">TestKategorisi</span><span class="sxs-lookup"><span data-stu-id="a7cbe-176">TestCategory</span></span></li></ul> |
| <span data-ttu-id="a7cbe-177">xBirim</span><span class="sxs-lookup"><span data-stu-id="a7cbe-177">xUnit</span></span>          | <ul><li><span data-ttu-id="a7cbe-178">Fullyqualifiedname</span><span class="sxs-lookup"><span data-stu-id="a7cbe-178">FullyQualifiedName</span></span></li><li><span data-ttu-id="a7cbe-179">DisplayName</span><span class="sxs-lookup"><span data-stu-id="a7cbe-179">DisplayName</span></span></li><li><span data-ttu-id="a7cbe-180">Özellik</span><span class="sxs-lookup"><span data-stu-id="a7cbe-180">Traits</span></span></li></ul>                                   |

<span data-ttu-id="a7cbe-181">Özellik `<operator>` ve değer arasındaki ilişkiyi açıklar:</span><span class="sxs-lookup"><span data-stu-id="a7cbe-181">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="a7cbe-182">İşleç</span><span class="sxs-lookup"><span data-stu-id="a7cbe-182">Operator</span></span> | <span data-ttu-id="a7cbe-183">İşlev</span><span class="sxs-lookup"><span data-stu-id="a7cbe-183">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="a7cbe-184">Tam eşleşme</span><span class="sxs-lookup"><span data-stu-id="a7cbe-184">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="a7cbe-185">Tam eşleşme yok</span><span class="sxs-lookup"><span data-stu-id="a7cbe-185">Not exact match</span></span> |
| `~`      | <span data-ttu-id="a7cbe-186">Contains</span><span class="sxs-lookup"><span data-stu-id="a7cbe-186">Contains</span></span>        |
| `!~`     | <span data-ttu-id="a7cbe-187">İçermez</span><span class="sxs-lookup"><span data-stu-id="a7cbe-187">Not contains</span></span>    |

<span data-ttu-id="a7cbe-188">`<value>`bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-188">`<value>` is a string.</span></span> <span data-ttu-id="a7cbe-189">Tüm aramalar duyarsız.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-189">All the lookups are case insensitive.</span></span>

<span data-ttu-id="a7cbe-190">Bir ifadesi `<operator>` olmayan bir `contains` ifade otomatik `FullyQualifiedName` olarak açık `dotnet test --filter xyz` özellik olarak `dotnet test --filter FullyQualifiedName~xyz`kabul edilir (örneğin, aynıdır).</span><span class="sxs-lookup"><span data-stu-id="a7cbe-190">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="a7cbe-191">İfadeler koşullu işleçlerle birleşebilir:</span><span class="sxs-lookup"><span data-stu-id="a7cbe-191">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="a7cbe-192">İşleç</span><span class="sxs-lookup"><span data-stu-id="a7cbe-192">Operator</span></span>            | <span data-ttu-id="a7cbe-193">İşlev</span><span class="sxs-lookup"><span data-stu-id="a7cbe-193">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="a7cbe-194">OR</span><span class="sxs-lookup"><span data-stu-id="a7cbe-194">OR</span></span>       |
| `&`                 | <span data-ttu-id="a7cbe-195">AND</span><span class="sxs-lookup"><span data-stu-id="a7cbe-195">AND</span></span>      |

<span data-ttu-id="a7cbe-196">Koşullu işleçleri kullanırken ifadeleri parantez içine alabilirsiniz (örneğin, `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="a7cbe-196">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="a7cbe-197">Seçici birim test filtrelemenin nasıl kullanılacağı hakkında daha fazla bilgi ve örnekler için seçici [birim testlerini çalıştırma'ya](../testing/selective-unit-tests.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-197">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a7cbe-198">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7cbe-198">See also</span></span>

- [<span data-ttu-id="a7cbe-199">Çerçeveler ve Hedefler</span><span class="sxs-lookup"><span data-stu-id="a7cbe-199">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="a7cbe-200">.NET Core Runtime Tanımlayıcı (RID) kataloğu</span><span class="sxs-lookup"><span data-stu-id="a7cbe-200">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="a7cbe-201">Çalışma ayarlarını komut satırından geçirme</span><span class="sxs-lookup"><span data-stu-id="a7cbe-201">Passing runsettings arguments through commandline</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
