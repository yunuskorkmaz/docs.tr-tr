---
title: DotNet test komutu
description: DotNet test komutu, belirli bir projedeki birim testlerini yürütmek için kullanılır.
ms.date: 02/27/2020
ms.openlocfilehash: 6e906ab396a788905c99f50e73390b765b240efc
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157017"
---
# <a name="dotnet-test"></a><span data-ttu-id="368ae-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="368ae-103">dotnet test</span></span>

<span data-ttu-id="368ae-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="368ae-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="368ae-105">Adı</span><span class="sxs-lookup"><span data-stu-id="368ae-105">Name</span></span>

<span data-ttu-id="368ae-106">birim testlerini yürütmek için kullanılan `dotnet test` .NET test sürücüsü.</span><span class="sxs-lookup"><span data-stu-id="368ae-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="368ae-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="368ae-107">Synopsis</span></span>

```dotnetcli
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame]
    [-c|--configuration] [--collect] [-d|--diag] [-f|--framework]
    [--filter] [-l|--logger] [--no-build] [--no-restore]
    [-o|--output] [-r|--results-directory] [-s|--settings]
    [-t|--list-tests] [-v|--verbosity] [-- <RunSettings arguments>]

dotnet test [-h|--help]
```

## <a name="description"></a><span data-ttu-id="368ae-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="368ae-108">Description</span></span>

<span data-ttu-id="368ae-109">`dotnet test` komutu, belirli bir projedeki birim testlerini yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="368ae-109">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="368ae-110">`dotnet test` komutu, bir proje için belirtilen Test Çalıştırıcısı konsol uygulamasını başlatır.</span><span class="sxs-lookup"><span data-stu-id="368ae-110">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="368ae-111">Test Çalıştırıcısı, bir birim test çerçevesi (örneğin, MSTest, NUnit veya xUnit) için tanımlanan testleri yürütür ve her testin başarısını veya başarısızlığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="368ae-111">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="368ae-112">Tüm testler başarılı olursa, Test Çalıştırıcısı çıkış kodu olarak 0 döndürür; Aksi takdirde, herhangi bir test başarısız olursa, 1 döndürür.</span><span class="sxs-lookup"><span data-stu-id="368ae-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="368ae-113">Test Çalıştırıcısı ve birim testi kitaplığı, NuGet paketleri olarak paketlenir ve proje için sıradan bağımlılıklar olarak geri yüklenir.</span><span class="sxs-lookup"><span data-stu-id="368ae-113">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="368ae-114">Test projeleri, aşağıdaki örnek proje dosyasında görüldüğü gibi sıradan bir `<PackageReference>` öğesi kullanarak Test Çalıştırıcısı belirtir:</span><span class="sxs-lookup"><span data-stu-id="368ae-114">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="368ae-115">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="368ae-115">Arguments</span></span>

- **`PROJECT`**

  <span data-ttu-id="368ae-116">Test projesinin yolu.</span><span class="sxs-lookup"><span data-stu-id="368ae-116">Path to the test project.</span></span> <span data-ttu-id="368ae-117">Belirtilmezse, varsayılan olarak geçerli dizin olur.</span><span class="sxs-lookup"><span data-stu-id="368ae-117">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="368ae-118">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="368ae-118">Options</span></span>

- **`a|--test-adapter-path <PATH_TO_ADAPTER>`**

  <span data-ttu-id="368ae-119">Test çalıştırmasında belirtilen yoldan özel test bağdaştırıcılarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="368ae-119">Use the custom test adapters from the specified path in the test run.</span></span>

- **`-blame`**

  <span data-ttu-id="368ae-120">Testleri sorumluyu modunda çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="368ae-120">Runs the tests in blame mode.</span></span> <span data-ttu-id="368ae-121">Bu seçenek, test ana bilgisayarının kilitlenmesine neden olan sorunlu testleri yalıtmak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="368ae-121">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="368ae-122">Geçerli dizinde, kilitlenmeden önce yürütülen testlerin sırasını yakalayan *Sequence. xml* olarak bir çıktı dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="368ae-122">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`c|--configuration {Debug|Release}`**

  <span data-ttu-id="368ae-123">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="368ae-123">Defines the build configuration.</span></span> <span data-ttu-id="368ae-124">Varsayılan değer `Debug`, ancak projenizin yapılandırması bu varsayılan SDK ayarını geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="368ae-124">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`-collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  <span data-ttu-id="368ae-125">Test çalıştırması için veri toplayıcıyı etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="368ae-125">Enables data collector for the test run.</span></span> <span data-ttu-id="368ae-126">Daha fazla bilgi için bkz. [test çalıştırmasını izleme ve çözümleme](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="368ae-126">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

- **`d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  <span data-ttu-id="368ae-127">Test platformu için tanılama modunu sağlar ve belirtilen dosyaya tanılama iletileri yazar.</span><span class="sxs-lookup"><span data-stu-id="368ae-127">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

- **`f|--framework <FRAMEWORK>`**

  <span data-ttu-id="368ae-128">Belirli bir [çerçeve](../../standard/frameworks.md)için test ikililerini arar.</span><span class="sxs-lookup"><span data-stu-id="368ae-128">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="368ae-129">Geçerli projede verilen ifadeyi kullanarak testleri filtreler.</span><span class="sxs-lookup"><span data-stu-id="368ae-129">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="368ae-130">Daha fazla bilgi için, [filtre seçeneği ayrıntıları](#filter-option-details) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="368ae-130">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="368ae-131">Seçmeli birim testi filtrelemeyi kullanma hakkında daha fazla bilgi ve örnekler için bkz. [Seçmeli birim testlerini çalıştırma](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="368ae-131">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`h|--help`**

  <span data-ttu-id="368ae-132">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="368ae-132">Prints out a short help for the command.</span></span>

- **`l|--logger <LoggerUri/FriendlyName>`**

  <span data-ttu-id="368ae-133">Test sonuçları için bir günlükçü belirtir.</span><span class="sxs-lookup"><span data-stu-id="368ae-133">Specifies a logger for test results.</span></span>

- **`--no-build`**

  <span data-ttu-id="368ae-134">Test projesi çalıştırılmadan önce derlenmez.</span><span class="sxs-lookup"><span data-stu-id="368ae-134">Doesn't build the test project before running it.</span></span> <span data-ttu-id="368ae-135">Ayrıca,-`--no-restore` bayrağını örtülü olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="368ae-135">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--no-restore`**

  <span data-ttu-id="368ae-136">Komutu çalıştırılırken örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="368ae-136">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="368ae-137">Çalıştırılacak ikililerin bulunacağı dizin.</span><span class="sxs-lookup"><span data-stu-id="368ae-137">Directory in which to find the binaries to run.</span></span>

- **`-r|--results-directory <PATH>`**

  <span data-ttu-id="368ae-138">Test sonuçlarının yerleştirileceği dizin.</span><span class="sxs-lookup"><span data-stu-id="368ae-138">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="368ae-139">Belirtilen dizin yoksa, oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="368ae-139">If the specified directory doesn't exist, it's created.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="368ae-140">Testleri çalıştırmak için kullanılacak `.runsettings` dosyası.</span><span class="sxs-lookup"><span data-stu-id="368ae-140">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="368ae-141">`.runsettings` bir dosya kullanarak birim testlerini yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="368ae-141">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)

- **`-t|--list-tests`**

  <span data-ttu-id="368ae-142">Geçerli projedeki tüm bulunan testlerin listesini listeleyin.</span><span class="sxs-lookup"><span data-stu-id="368ae-142">List all of the discovered tests in the current project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="368ae-143">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="368ae-143">Sets the verbosity level of the command.</span></span> <span data-ttu-id="368ae-144">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="368ae-144">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- <span data-ttu-id="368ae-145">`RunSettings` bağımsız değişkenleri</span><span class="sxs-lookup"><span data-stu-id="368ae-145">`RunSettings` arguments</span></span>

  <span data-ttu-id="368ae-146">Bağımsız değişkenler test için `RunSettings` yapılandırma olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="368ae-146">Arguments are passed as `RunSettings` configurations for the test.</span></span> <span data-ttu-id="368ae-147">Bağımsız değişkenler "--" sonra `[name]=[value]` çiftleri olarak belirtilir (--After---------</span><span class="sxs-lookup"><span data-stu-id="368ae-147">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="368ae-148">Birden çok `[name]=[value]` çiftini ayırmak için bir boşluk kullanılır.</span><span class="sxs-lookup"><span data-stu-id="368ae-148">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="368ae-149">Örnek: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="368ae-149">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="368ae-150">Daha fazla bilgi için bkz. [VSTest. Console. exe: RunSettings args geçirme](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="368ae-150">For more information, see [vstest.console.exe: Passing RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="368ae-151">Örnekler</span><span class="sxs-lookup"><span data-stu-id="368ae-151">Examples</span></span>

- <span data-ttu-id="368ae-152">Projedeki testleri geçerli dizinde çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="368ae-152">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="368ae-153">`test1` projesindeki testleri çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="368ae-153">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="368ae-154">Projedeki testleri geçerli dizinde çalıştırın ve TRX biçiminde bir test sonuçları dosyası oluşturun:</span><span class="sxs-lookup"><span data-stu-id="368ae-154">Run the tests in the project in the current directory and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

## <a name="filter-option-details"></a><span data-ttu-id="368ae-155">Filtre seçeneği ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="368ae-155">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="368ae-156">`<Expression>` `<property><operator><value>[|&<Expression>]`biçimine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="368ae-156">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="368ae-157">`<property>`, `Test Case`özniteliğidir.</span><span class="sxs-lookup"><span data-stu-id="368ae-157">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="368ae-158">Popüler birim testi çerçeveleri tarafından desteklenen özellikler aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="368ae-158">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="368ae-159">Test çerçevesi</span><span class="sxs-lookup"><span data-stu-id="368ae-159">Test Framework</span></span> | <span data-ttu-id="368ae-160">Desteklenen özellikler</span><span class="sxs-lookup"><span data-stu-id="368ae-160">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="368ae-161">MSTest</span><span class="sxs-lookup"><span data-stu-id="368ae-161">MSTest</span></span>         | <ul><li><span data-ttu-id="368ae-162">TamAdı</span><span class="sxs-lookup"><span data-stu-id="368ae-162">FullyQualifiedName</span></span></li><li><span data-ttu-id="368ae-163">Adı</span><span class="sxs-lookup"><span data-stu-id="368ae-163">Name</span></span></li><li><span data-ttu-id="368ae-164">Sınıf</span><span class="sxs-lookup"><span data-stu-id="368ae-164">ClassName</span></span></li><li><span data-ttu-id="368ae-165">Öncelik</span><span class="sxs-lookup"><span data-stu-id="368ae-165">Priority</span></span></li><li><span data-ttu-id="368ae-166">TestCategory</span><span class="sxs-lookup"><span data-stu-id="368ae-166">TestCategory</span></span></li></ul> |
| <span data-ttu-id="368ae-167">xUnit</span><span class="sxs-lookup"><span data-stu-id="368ae-167">xUnit</span></span>          | <ul><li><span data-ttu-id="368ae-168">TamAdı</span><span class="sxs-lookup"><span data-stu-id="368ae-168">FullyQualifiedName</span></span></li><li><span data-ttu-id="368ae-169">DisplayName</span><span class="sxs-lookup"><span data-stu-id="368ae-169">DisplayName</span></span></li><li><span data-ttu-id="368ae-170">Lerdir</span><span class="sxs-lookup"><span data-stu-id="368ae-170">Traits</span></span></li></ul>                                   |

<span data-ttu-id="368ae-171">`<operator>`, özelliği ve değeri arasındaki ilişkiyi açıklar:</span><span class="sxs-lookup"><span data-stu-id="368ae-171">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="368ae-172">İşleç</span><span class="sxs-lookup"><span data-stu-id="368ae-172">Operator</span></span> | <span data-ttu-id="368ae-173">İşlev</span><span class="sxs-lookup"><span data-stu-id="368ae-173">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="368ae-174">Tam eşleşme</span><span class="sxs-lookup"><span data-stu-id="368ae-174">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="368ae-175">Tam eşleşme yok</span><span class="sxs-lookup"><span data-stu-id="368ae-175">Not exact match</span></span> |
| `~`      | <span data-ttu-id="368ae-176">Contains</span><span class="sxs-lookup"><span data-stu-id="368ae-176">Contains</span></span>        |
| `!~`     | <span data-ttu-id="368ae-177">İçermez</span><span class="sxs-lookup"><span data-stu-id="368ae-177">Not contains</span></span>    |

<span data-ttu-id="368ae-178">`<value>` bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="368ae-178">`<value>` is a string.</span></span> <span data-ttu-id="368ae-179">Tüm aramalar büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="368ae-179">All the lookups are case insensitive.</span></span>

<span data-ttu-id="368ae-180">`<operator>` olmayan bir ifade `FullyQualifiedName` özelliğinde `contains` olarak kabul edilir (örneğin, `dotnet test --filter xyz` `dotnet test --filter FullyQualifiedName~xyz`aynıdır).</span><span class="sxs-lookup"><span data-stu-id="368ae-180">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="368ae-181">İfadeler koşullu işleçlerle birleştirilebilecek:</span><span class="sxs-lookup"><span data-stu-id="368ae-181">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="368ae-182">İşleç</span><span class="sxs-lookup"><span data-stu-id="368ae-182">Operator</span></span>            | <span data-ttu-id="368ae-183">İşlev</span><span class="sxs-lookup"><span data-stu-id="368ae-183">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="368ae-184">OR</span><span class="sxs-lookup"><span data-stu-id="368ae-184">OR</span></span>       |
| `&`                 | <span data-ttu-id="368ae-185">AND</span><span class="sxs-lookup"><span data-stu-id="368ae-185">AND</span></span>      |

<span data-ttu-id="368ae-186">Koşullu işleçler kullandığınızda (örneğin, `(Name~TestMethod1) | (Name~TestMethod2)`) ifadeleri parantez içine alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="368ae-186">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="368ae-187">Seçmeli birim testi filtrelemeyi kullanma hakkında daha fazla bilgi ve örnekler için bkz. [Seçmeli birim testlerini çalıştırma](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="368ae-187">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="368ae-188">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="368ae-188">See also</span></span>

- [<span data-ttu-id="368ae-189">Çerçeveler ve hedefler</span><span class="sxs-lookup"><span data-stu-id="368ae-189">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="368ae-190">.NET Core çalışma zamanı tanımlayıcısı (RID) kataloğu</span><span class="sxs-lookup"><span data-stu-id="368ae-190">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
