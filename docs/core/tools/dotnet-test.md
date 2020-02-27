---
title: DotNet test komutu
description: DotNet test komutu, belirli bir projedeki birim testlerini yürütmek için kullanılır.
ms.date: 05/29/2018
ms.openlocfilehash: 890d1fc3fd9d47f2bdcd63f2a25248c3edd705e4
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626053"
---
# <a name="dotnet-test"></a><span data-ttu-id="62688-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="62688-103">dotnet test</span></span>

<span data-ttu-id="62688-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="62688-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="62688-105">Adı</span><span class="sxs-lookup"><span data-stu-id="62688-105">Name</span></span>

<span data-ttu-id="62688-106">birim testlerini yürütmek için kullanılan `dotnet test` .NET test sürücüsü.</span><span class="sxs-lookup"><span data-stu-id="62688-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="62688-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="62688-107">Synopsis</span></span>

```dotnetcli
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame]
    [-c|--configuration] [--collect] [-d|--diag] [-f|--framework]
    [--filter] [-l|--logger] [--no-build] [--no-restore]
    [-o|--output] [-r|--results-directory] [-s|--settings]
    [-t|--list-tests] [-v|--verbosity] [-- <RunSettings arguments>]

dotnet test [-h|--help]
```

## <a name="description"></a><span data-ttu-id="62688-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="62688-108">Description</span></span>

<span data-ttu-id="62688-109">`dotnet test` komutu, belirli bir projedeki birim testlerini yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="62688-109">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="62688-110">`dotnet test` komutu, bir proje için belirtilen Test Çalıştırıcısı konsol uygulamasını başlatır.</span><span class="sxs-lookup"><span data-stu-id="62688-110">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="62688-111">Test Çalıştırıcısı, bir birim test çerçevesi (örneğin, MSTest, NUnit veya xUnit) için tanımlanan testleri yürütür ve her testin başarısını veya başarısızlığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="62688-111">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="62688-112">Tüm testler başarılı olursa, Test Çalıştırıcısı çıkış kodu olarak 0 döndürür; Aksi takdirde, herhangi bir test başarısız olursa, 1 döndürür.</span><span class="sxs-lookup"><span data-stu-id="62688-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="62688-113">Test Çalıştırıcısı ve birim testi kitaplığı, NuGet paketleri olarak paketlenir ve proje için sıradan bağımlılıklar olarak geri yüklenir.</span><span class="sxs-lookup"><span data-stu-id="62688-113">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="62688-114">Test projeleri, aşağıdaki örnek proje dosyasında görüldüğü gibi sıradan bir `<PackageReference>` öğesi kullanarak Test Çalıştırıcısı belirtir:</span><span class="sxs-lookup"><span data-stu-id="62688-114">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="62688-115">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="62688-115">Arguments</span></span>

- **`PROJECT`**

  <span data-ttu-id="62688-116">Test projesinin yolu.</span><span class="sxs-lookup"><span data-stu-id="62688-116">Path to the test project.</span></span> <span data-ttu-id="62688-117">Belirtilmezse, varsayılan olarak geçerli dizin olur.</span><span class="sxs-lookup"><span data-stu-id="62688-117">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="62688-118">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="62688-118">Options</span></span>

- **`a|--test-adapter-path <PATH_TO_ADAPTER>`**

  <span data-ttu-id="62688-119">Test çalıştırmasında belirtilen yoldan özel test bağdaştırıcılarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="62688-119">Use the custom test adapters from the specified path in the test run.</span></span>

- **`-blame`**

  <span data-ttu-id="62688-120">Testleri sorumluyu modunda çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="62688-120">Runs the tests in blame mode.</span></span> <span data-ttu-id="62688-121">Bu seçenek, test ana bilgisayarının kilitlenmesine neden olan sorunlu testleri yalıtmak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="62688-121">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="62688-122">Geçerli dizinde, kilitlenmeden önce yürütülen testlerin sırasını yakalayan *Sequence. xml* olarak bir çıktı dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="62688-122">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`c|--configuration {Debug|Release}`**

  <span data-ttu-id="62688-123">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="62688-123">Defines the build configuration.</span></span> <span data-ttu-id="62688-124">Varsayılan değer `Debug`, ancak projenizin yapılandırması bu varsayılan SDK ayarını geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="62688-124">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`-collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  <span data-ttu-id="62688-125">Test çalıştırması için veri toplayıcıyı etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="62688-125">Enables data collector for the test run.</span></span> <span data-ttu-id="62688-126">Daha fazla bilgi için bkz. [test çalıştırmasını izleme ve çözümleme](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="62688-126">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

- **`d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  <span data-ttu-id="62688-127">Test platformu için tanılama modunu sağlar ve belirtilen dosyaya tanılama iletileri yazar.</span><span class="sxs-lookup"><span data-stu-id="62688-127">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

- **`f|--framework <FRAMEWORK>`**

  <span data-ttu-id="62688-128">Belirli bir [çerçeve](../../standard/frameworks.md)için test ikililerini arar.</span><span class="sxs-lookup"><span data-stu-id="62688-128">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="62688-129">Geçerli projede verilen ifadeyi kullanarak testleri filtreler.</span><span class="sxs-lookup"><span data-stu-id="62688-129">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="62688-130">Daha fazla bilgi için, [filtre seçeneği ayrıntıları](#filter-option-details) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="62688-130">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="62688-131">Seçmeli birim testi filtrelemeyi kullanma hakkında daha fazla bilgi ve örnekler için bkz. [Seçmeli birim testlerini çalıştırma](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="62688-131">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`h|--help`**

  <span data-ttu-id="62688-132">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="62688-132">Prints out a short help for the command.</span></span>

- **`l|--logger <LoggerUri/FriendlyName>`**

  <span data-ttu-id="62688-133">Test sonuçları için bir günlükçü belirtir.</span><span class="sxs-lookup"><span data-stu-id="62688-133">Specifies a logger for test results.</span></span>

- **`--no-build`**

  <span data-ttu-id="62688-134">Test projesi çalıştırılmadan önce derlenmez.</span><span class="sxs-lookup"><span data-stu-id="62688-134">Doesn't build the test project before running it.</span></span> <span data-ttu-id="62688-135">Ayrıca,-`--no-restore` bayrağını örtülü olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="62688-135">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--no-restore`**

  <span data-ttu-id="62688-136">Komutu çalıştırılırken örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="62688-136">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="62688-137">Çalıştırılacak ikililerin bulunacağı dizin.</span><span class="sxs-lookup"><span data-stu-id="62688-137">Directory in which to find the binaries to run.</span></span>

- **`-r|--results-directory <PATH>`**

  <span data-ttu-id="62688-138">Test sonuçlarının yerleştirileceği dizin.</span><span class="sxs-lookup"><span data-stu-id="62688-138">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="62688-139">Belirtilen dizin yoksa, oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="62688-139">If the specified directory doesn't exist, it's created.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="62688-140">Testleri çalıştırmak için kullanılacak `.runsettings` dosyası.</span><span class="sxs-lookup"><span data-stu-id="62688-140">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="62688-141">`.runsettings` bir dosya kullanarak birim testlerini yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="62688-141">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)

- **`-t|--list-tests`**

  <span data-ttu-id="62688-142">Geçerli projedeki tüm bulunan testlerin listesini listeleyin.</span><span class="sxs-lookup"><span data-stu-id="62688-142">List all of the discovered tests in the current project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="62688-143">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="62688-143">Sets the verbosity level of the command.</span></span> <span data-ttu-id="62688-144">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="62688-144">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- <span data-ttu-id="62688-145">`RunSettings` bağımsız değişkenleri</span><span class="sxs-lookup"><span data-stu-id="62688-145">`RunSettings` arguments</span></span>

  <span data-ttu-id="62688-146">Bağımsız değişkenler test için `RunSettings` yapılandırma olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="62688-146">Arguments are passed as `RunSettings` configurations for the test.</span></span> <span data-ttu-id="62688-147">Bağımsız değişkenler "--" sonra `[name]=[value]` çiftleri olarak belirtilir (--After---------</span><span class="sxs-lookup"><span data-stu-id="62688-147">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="62688-148">Birden çok `[name]=[value]` çiftini ayırmak için bir boşluk kullanılır.</span><span class="sxs-lookup"><span data-stu-id="62688-148">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="62688-149">Örnek: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="62688-149">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="62688-150">Daha fazla bilgi için bkz. [VSTest. Console. exe: RunSettings args geçirme](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="62688-150">For more information, see [vstest.console.exe: Passing RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="62688-151">Örnekler</span><span class="sxs-lookup"><span data-stu-id="62688-151">Examples</span></span>

- <span data-ttu-id="62688-152">Projedeki testleri geçerli dizinde çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="62688-152">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="62688-153">`test1` projesindeki testleri çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="62688-153">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="62688-154">Projedeki testleri geçerli dizinde çalıştırın ve TRX biçiminde bir test sonuçları dosyası oluşturun:</span><span class="sxs-lookup"><span data-stu-id="62688-154">Run the tests in the project in the current directory and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

## <a name="filter-option-details"></a><span data-ttu-id="62688-155">Filtre seçeneği ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="62688-155">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="62688-156">`<Expression>` `<property><operator><value>[|&<Expression>]`biçimine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="62688-156">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="62688-157">`<property>`, `Test Case`özniteliğidir.</span><span class="sxs-lookup"><span data-stu-id="62688-157">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="62688-158">Popüler birim testi çerçeveleri tarafından desteklenen özellikler aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="62688-158">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="62688-159">Test çerçevesi</span><span class="sxs-lookup"><span data-stu-id="62688-159">Test Framework</span></span> | <span data-ttu-id="62688-160">Desteklenen özellikler</span><span class="sxs-lookup"><span data-stu-id="62688-160">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="62688-161">MSTest</span><span class="sxs-lookup"><span data-stu-id="62688-161">MSTest</span></span>         | <ul><li><span data-ttu-id="62688-162">TamAdı</span><span class="sxs-lookup"><span data-stu-id="62688-162">FullyQualifiedName</span></span></li><li><span data-ttu-id="62688-163">Adı</span><span class="sxs-lookup"><span data-stu-id="62688-163">Name</span></span></li><li><span data-ttu-id="62688-164">Sınıf</span><span class="sxs-lookup"><span data-stu-id="62688-164">ClassName</span></span></li><li><span data-ttu-id="62688-165">Öncelik</span><span class="sxs-lookup"><span data-stu-id="62688-165">Priority</span></span></li><li><span data-ttu-id="62688-166">TestCategory</span><span class="sxs-lookup"><span data-stu-id="62688-166">TestCategory</span></span></li></ul> |
| <span data-ttu-id="62688-167">xUnit</span><span class="sxs-lookup"><span data-stu-id="62688-167">xUnit</span></span>          | <ul><li><span data-ttu-id="62688-168">TamAdı</span><span class="sxs-lookup"><span data-stu-id="62688-168">FullyQualifiedName</span></span></li><li><span data-ttu-id="62688-169">DisplayName</span><span class="sxs-lookup"><span data-stu-id="62688-169">DisplayName</span></span></li><li><span data-ttu-id="62688-170">Lerdir</span><span class="sxs-lookup"><span data-stu-id="62688-170">Traits</span></span></li></ul>                                   |

<span data-ttu-id="62688-171">`<operator>`, özelliği ve değeri arasındaki ilişkiyi açıklar:</span><span class="sxs-lookup"><span data-stu-id="62688-171">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="62688-172">İşleç</span><span class="sxs-lookup"><span data-stu-id="62688-172">Operator</span></span> | <span data-ttu-id="62688-173">İşlev</span><span class="sxs-lookup"><span data-stu-id="62688-173">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="62688-174">Tam eşleşme</span><span class="sxs-lookup"><span data-stu-id="62688-174">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="62688-175">Tam eşleşme yok</span><span class="sxs-lookup"><span data-stu-id="62688-175">Not exact match</span></span> |
| `~`      | <span data-ttu-id="62688-176">Contains</span><span class="sxs-lookup"><span data-stu-id="62688-176">Contains</span></span>        |
| `!~`     | <span data-ttu-id="62688-177">İçermez</span><span class="sxs-lookup"><span data-stu-id="62688-177">Not contains</span></span>    |

<span data-ttu-id="62688-178">`<value>` bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="62688-178">`<value>` is a string.</span></span> <span data-ttu-id="62688-179">Tüm aramalar büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="62688-179">All the lookups are case insensitive.</span></span>

<span data-ttu-id="62688-180">`<operator>` olmayan bir ifade `FullyQualifiedName` özelliğinde `contains` olarak kabul edilir (örneğin, `dotnet test --filter xyz` `dotnet test --filter FullyQualifiedName~xyz`aynıdır).</span><span class="sxs-lookup"><span data-stu-id="62688-180">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="62688-181">İfadeler koşullu işleçlerle birleştirilebilecek:</span><span class="sxs-lookup"><span data-stu-id="62688-181">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="62688-182">İşleç</span><span class="sxs-lookup"><span data-stu-id="62688-182">Operator</span></span>            | <span data-ttu-id="62688-183">İşlev</span><span class="sxs-lookup"><span data-stu-id="62688-183">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="62688-184">OR</span><span class="sxs-lookup"><span data-stu-id="62688-184">OR</span></span>       |
| `&`                 | <span data-ttu-id="62688-185">AND</span><span class="sxs-lookup"><span data-stu-id="62688-185">AND</span></span>      |

<span data-ttu-id="62688-186">Koşullu işleçler kullandığınızda (örneğin, `(Name~TestMethod1) | (Name~TestMethod2)`) ifadeleri parantez içine alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62688-186">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="62688-187">Seçmeli birim testi filtrelemeyi kullanma hakkında daha fazla bilgi ve örnekler için bkz. [Seçmeli birim testlerini çalıştırma](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="62688-187">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="62688-188">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62688-188">See also</span></span>

- [<span data-ttu-id="62688-189">Çerçeveler ve hedefler</span><span class="sxs-lookup"><span data-stu-id="62688-189">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="62688-190">.NET Core çalışma zamanı tanımlayıcısı (RID) kataloğu</span><span class="sxs-lookup"><span data-stu-id="62688-190">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
