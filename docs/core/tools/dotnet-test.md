---
title: DotNet test komutu
description: DotNet test komutu, belirli bir projedeki birim testlerini yürütmek için kullanılır.
ms.date: 05/29/2018
ms.openlocfilehash: 909815151265117395c6d8d13b4443a245c05f9e
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451200"
---
# <a name="dotnet-test"></a><span data-ttu-id="e534c-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="e534c-103">dotnet test</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="e534c-104">Name</span><span class="sxs-lookup"><span data-stu-id="e534c-104">Name</span></span>

<span data-ttu-id="e534c-105">birim testlerini yürütmek için kullanılan `dotnet test` .NET test sürücüsü.</span><span class="sxs-lookup"><span data-stu-id="e534c-105">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e534c-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="e534c-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21"></a>[<span data-ttu-id="e534c-107">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="e534c-107">.NET Core 2.1</span></span>](#tab/netcore21)

```dotnetcli
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] 
    [-v|--verbosity] [-- <RunSettings arguments>]

dotnet test [-h|--help]
```

# <a name="net-core-20"></a>[<span data-ttu-id="e534c-108">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="e534c-108">.NET Core 2.0</span></span>](#tab/netcore20)

```dotnetcli
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]

dotnet test [-h|--help]
```

# <a name="net-core-1x"></a>[<span data-ttu-id="e534c-109">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="e534c-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]

dotnet test [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="e534c-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e534c-110">Description</span></span>

<span data-ttu-id="e534c-111">`dotnet test` komutu, belirli bir projedeki birim testlerini yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e534c-111">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="e534c-112">`dotnet test` komutu, bir proje için belirtilen Test Çalıştırıcısı konsol uygulamasını başlatır.</span><span class="sxs-lookup"><span data-stu-id="e534c-112">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="e534c-113">Test Çalıştırıcısı, bir birim test çerçevesi (örneğin, MSTest, NUnit veya xUnit) için tanımlanan testleri yürütür ve her testin başarısını veya başarısızlığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="e534c-113">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="e534c-114">Tüm testler başarılı olursa, Test Çalıştırıcısı çıkış kodu olarak 0 döndürür; Aksi takdirde, herhangi bir test başarısız olursa, 1 döndürür.</span><span class="sxs-lookup"><span data-stu-id="e534c-114">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="e534c-115">Test Çalıştırıcısı ve birim testi kitaplığı, NuGet paketleri olarak paketlenir ve proje için sıradan bağımlılıklar olarak geri yüklenir.</span><span class="sxs-lookup"><span data-stu-id="e534c-115">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="e534c-116">Test projeleri, aşağıdaki örnek proje dosyasında görüldüğü gibi sıradan bir `<PackageReference>` öğesi kullanarak Test Çalıştırıcısı belirtir:</span><span class="sxs-lookup"><span data-stu-id="e534c-116">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="e534c-117">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="e534c-117">Arguments</span></span>

`PROJECT`

<span data-ttu-id="e534c-118">Test projesinin yolu.</span><span class="sxs-lookup"><span data-stu-id="e534c-118">Path to the test project.</span></span> <span data-ttu-id="e534c-119">Belirtilmezse, varsayılan olarak geçerli dizin olur.</span><span class="sxs-lookup"><span data-stu-id="e534c-119">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="e534c-120">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="e534c-120">Options</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="e534c-121">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="e534c-121">.NET Core 2.1</span></span>](#tab/netcore21)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="e534c-122">Test çalıştırmasında belirtilen yoldan özel test bağdaştırıcılarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="e534c-122">Use the custom test adapters from the specified path in the test run.</span></span>

`--blame`

<span data-ttu-id="e534c-123">Testleri sorumluyu modunda çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="e534c-123">Runs the tests in blame mode.</span></span> <span data-ttu-id="e534c-124">Bu seçenek, test ana bilgisayarının kilitlenmesine neden olan sorunlu testleri yalıtmak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="e534c-124">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="e534c-125">Geçerli dizinde, kilitlenmeden önce yürütülen testlerin sırasını yakalayan *Sequence. xml* olarak bir çıktı dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e534c-125">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="e534c-126">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e534c-126">Defines the build configuration.</span></span> <span data-ttu-id="e534c-127">Varsayılan değer `Debug`, ancak projenizin yapılandırması bu varsayılan SDK ayarını geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="e534c-127">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="e534c-128">Test çalıştırması için veri toplayıcıyı etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e534c-128">Enables data collector for the test run.</span></span> <span data-ttu-id="e534c-129">Daha fazla bilgi için bkz. [test çalıştırmasını izleme ve çözümleme](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="e534c-129">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="e534c-130">Test platformu için tanılama modunu sağlar ve belirtilen dosyaya tanılama iletileri yazar.</span><span class="sxs-lookup"><span data-stu-id="e534c-130">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="e534c-131">Belirli bir [çerçeve](../../standard/frameworks.md)için test ikililerini arar.</span><span class="sxs-lookup"><span data-stu-id="e534c-131">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="e534c-132">Geçerli projede verilen ifadeyi kullanarak testleri filtreler.</span><span class="sxs-lookup"><span data-stu-id="e534c-132">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="e534c-133">Daha fazla bilgi için, [filtre seçeneği ayrıntıları](#filter-option-details) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e534c-133">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="e534c-134">Seçmeli birim testi filtrelemeyi kullanma hakkında daha fazla bilgi ve örnekler için bkz. [Seçmeli birim testlerini çalıştırma](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="e534c-134">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="e534c-135">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="e534c-135">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="e534c-136">Test sonuçları için bir günlükçü belirtir.</span><span class="sxs-lookup"><span data-stu-id="e534c-136">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="e534c-137">Test projesi çalıştırılmadan önce derlenmez.</span><span class="sxs-lookup"><span data-stu-id="e534c-137">Doesn't build the test project before running it.</span></span> <span data-ttu-id="e534c-138">Ayrıca `--no-restore` bayrağını örtülü olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e534c-138">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="e534c-139">Komutu çalıştırılırken örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="e534c-139">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="e534c-140">Çalıştırılacak ikililerin bulunacağı dizin.</span><span class="sxs-lookup"><span data-stu-id="e534c-140">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="e534c-141">Test sonuçlarının yerleştirileceği dizin.</span><span class="sxs-lookup"><span data-stu-id="e534c-141">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="e534c-142">Belirtilen dizin yoksa, oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e534c-142">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="e534c-143">Testleri çalıştırmak için kullanılacak `.runsettings` dosyası.</span><span class="sxs-lookup"><span data-stu-id="e534c-143">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="e534c-144">`.runsettings` bir dosya kullanarak birim testlerini yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="e534c-144">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)

`-t|--list-tests`

<span data-ttu-id="e534c-145">Geçerli projedeki tüm bulunan testlerin listesini listeleyin.</span><span class="sxs-lookup"><span data-stu-id="e534c-145">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="e534c-146">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e534c-146">Sets the verbosity level of the command.</span></span> <span data-ttu-id="e534c-147">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="e534c-147">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`RunSettings arguments`

<span data-ttu-id="e534c-148">Test için RunSettings yapılandırması olarak geçirilen bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="e534c-148">Arguments passed as RunSettings configurations for the test.</span></span> <span data-ttu-id="e534c-149">Bağımsız değişkenler "--" sonra `[name]=[value]` çiftleri olarak belirtilir (--After---------</span><span class="sxs-lookup"><span data-stu-id="e534c-149">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="e534c-150">Birden çok `[name]=[value]` çiftini ayırmak için bir boşluk kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e534c-150">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

<span data-ttu-id="e534c-151">Örnek: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="e534c-151">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

<span data-ttu-id="e534c-152">RunSettings hakkında daha fazla bilgi için bkz. [VSTest. Console. exe: runsettings args geçirme](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="e534c-152">For more information about RunSettings, see [vstest.console.exe: Passing RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

# <a name="net-core-20"></a>[<span data-ttu-id="e534c-153">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="e534c-153">.NET Core 2.0</span></span>](#tab/netcore20)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="e534c-154">Test çalıştırmasında belirtilen yoldan özel test bağdaştırıcılarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="e534c-154">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="e534c-155">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e534c-155">Defines the build configuration.</span></span> <span data-ttu-id="e534c-156">Varsayılan değer `Debug`, ancak projenizin yapılandırması bu varsayılan SDK ayarını geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="e534c-156">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="e534c-157">Test çalıştırması için veri toplayıcıyı etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e534c-157">Enables data collector for the test run.</span></span> <span data-ttu-id="e534c-158">Daha fazla bilgi için bkz. [test çalıştırmasını izleme ve çözümleme](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="e534c-158">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="e534c-159">Test platformu için tanılama modunu sağlar ve belirtilen dosyaya tanılama iletileri yazar.</span><span class="sxs-lookup"><span data-stu-id="e534c-159">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="e534c-160">Belirli bir [çerçeve](../../standard/frameworks.md)için test ikililerini arar.</span><span class="sxs-lookup"><span data-stu-id="e534c-160">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="e534c-161">Geçerli projede verilen ifadeyi kullanarak testleri filtreler.</span><span class="sxs-lookup"><span data-stu-id="e534c-161">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="e534c-162">Daha fazla bilgi için, [filtre seçeneği ayrıntıları](#filter-option-details) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e534c-162">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="e534c-163">Seçmeli birim testi filtrelemeyi kullanma hakkında daha fazla bilgi ve örnekler için bkz. [Seçmeli birim testlerini çalıştırma](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="e534c-163">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="e534c-164">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="e534c-164">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="e534c-165">Test sonuçları için bir günlükçü belirtir.</span><span class="sxs-lookup"><span data-stu-id="e534c-165">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="e534c-166">Test projesi çalıştırılmadan önce derlenmez.</span><span class="sxs-lookup"><span data-stu-id="e534c-166">Doesn't build the test project before running it.</span></span> <span data-ttu-id="e534c-167">Ayrıca `--no-restore` bayrağını örtülü olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e534c-167">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="e534c-168">Komutu çalıştırılırken örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="e534c-168">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="e534c-169">Çalıştırılacak ikililerin bulunacağı dizin.</span><span class="sxs-lookup"><span data-stu-id="e534c-169">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="e534c-170">Test sonuçlarının yerleştirileceği dizin.</span><span class="sxs-lookup"><span data-stu-id="e534c-170">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="e534c-171">Belirtilen dizin yoksa, oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e534c-171">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="e534c-172">Testleri çalıştırmak için kullanılacak `.runsettings` dosyası.</span><span class="sxs-lookup"><span data-stu-id="e534c-172">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="e534c-173">`.runsettings` bir dosya kullanarak birim testlerini yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="e534c-173">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)

`-t|--list-tests`

<span data-ttu-id="e534c-174">Geçerli projedeki tüm bulunan testlerin listesini listeleyin.</span><span class="sxs-lookup"><span data-stu-id="e534c-174">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="e534c-175">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e534c-175">Sets the verbosity level of the command.</span></span> <span data-ttu-id="e534c-176">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="e534c-176">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1x"></a>[<span data-ttu-id="e534c-177">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="e534c-177">.NET Core 1.x</span></span>](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="e534c-178">Test çalıştırmasında belirtilen yoldan özel test bağdaştırıcılarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="e534c-178">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="e534c-179">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e534c-179">Defines the build configuration.</span></span> <span data-ttu-id="e534c-180">Varsayılan değer `Debug`, ancak projenizin yapılandırması bu varsayılan SDK ayarını geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="e534c-180">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="e534c-181">Test platformu için tanılama modunu sağlar ve belirtilen dosyaya tanılama iletileri yazar.</span><span class="sxs-lookup"><span data-stu-id="e534c-181">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="e534c-182">Belirli bir [çerçeve](../../standard/frameworks.md)için test ikililerini arar.</span><span class="sxs-lookup"><span data-stu-id="e534c-182">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="e534c-183">Geçerli projede verilen ifadeyi kullanarak testleri filtreler.</span><span class="sxs-lookup"><span data-stu-id="e534c-183">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="e534c-184">Daha fazla bilgi için, [filtre seçeneği ayrıntıları](#filter-option-details) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e534c-184">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="e534c-185">Seçmeli birim testi filtrelemeyi kullanma hakkında daha fazla bilgi ve örnekler için bkz. [Seçmeli birim testlerini çalıştırma](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="e534c-185">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="e534c-186">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="e534c-186">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="e534c-187">Test sonuçları için bir günlükçü belirtir.</span><span class="sxs-lookup"><span data-stu-id="e534c-187">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="e534c-188">Test projesi çalıştırılmadan önce derlenmez.</span><span class="sxs-lookup"><span data-stu-id="e534c-188">Doesn't build the test project before running it.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="e534c-189">Çalıştırılacak ikililerin bulunacağı dizin.</span><span class="sxs-lookup"><span data-stu-id="e534c-189">Directory in which to find the binaries to run.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="e534c-190">Testleri çalıştırmak için kullanılacak `.runsettings` dosyası.</span><span class="sxs-lookup"><span data-stu-id="e534c-190">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="e534c-191">`.runsettings` bir dosya kullanarak birim testlerini yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="e534c-191">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)

`-t|--list-tests`

<span data-ttu-id="e534c-192">Geçerli projedeki tüm bulunan testlerin listesini listeleyin.</span><span class="sxs-lookup"><span data-stu-id="e534c-192">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="e534c-193">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e534c-193">Sets the verbosity level of the command.</span></span> <span data-ttu-id="e534c-194">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="e534c-194">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="e534c-195">Örnekler</span><span class="sxs-lookup"><span data-stu-id="e534c-195">Examples</span></span>

<span data-ttu-id="e534c-196">Projedeki testleri geçerli dizinde çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="e534c-196">Run the tests in the project in the current directory:</span></span>

`dotnet test`

<span data-ttu-id="e534c-197">`test1` projesindeki testleri çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="e534c-197">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

<span data-ttu-id="e534c-198">Projedeki testleri geçerli dizinde çalıştırın ve TRX biçiminde bir test sonuçları dosyası oluşturun:</span><span class="sxs-lookup"><span data-stu-id="e534c-198">Run the tests in the project in the current directory and generate a test results file in the trx format:</span></span>

`dotnet test --logger trx`

## <a name="filter-option-details"></a><span data-ttu-id="e534c-199">Filtre seçeneği ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="e534c-199">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="e534c-200">`<Expression>` `<property><operator><value>[|&<Expression>]`biçimine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e534c-200">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="e534c-201">`<property>`, `Test Case`özniteliğidir.</span><span class="sxs-lookup"><span data-stu-id="e534c-201">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="e534c-202">Popüler birim testi çerçeveleri tarafından desteklenen özellikler aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="e534c-202">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="e534c-203">Test çerçevesi</span><span class="sxs-lookup"><span data-stu-id="e534c-203">Test Framework</span></span> | <span data-ttu-id="e534c-204">Desteklenen özellikler</span><span class="sxs-lookup"><span data-stu-id="e534c-204">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="e534c-205">MSTest</span><span class="sxs-lookup"><span data-stu-id="e534c-205">MSTest</span></span>         | <ul><li><span data-ttu-id="e534c-206">TamAdı</span><span class="sxs-lookup"><span data-stu-id="e534c-206">FullyQualifiedName</span></span></li><li><span data-ttu-id="e534c-207">Name</span><span class="sxs-lookup"><span data-stu-id="e534c-207">Name</span></span></li><li><span data-ttu-id="e534c-208">Sınıf</span><span class="sxs-lookup"><span data-stu-id="e534c-208">ClassName</span></span></li><li><span data-ttu-id="e534c-209">Öncelik</span><span class="sxs-lookup"><span data-stu-id="e534c-209">Priority</span></span></li><li><span data-ttu-id="e534c-210">TestCategory</span><span class="sxs-lookup"><span data-stu-id="e534c-210">TestCategory</span></span></li></ul> |
| <span data-ttu-id="e534c-211">xUnit</span><span class="sxs-lookup"><span data-stu-id="e534c-211">xUnit</span></span>          | <ul><li><span data-ttu-id="e534c-212">TamAdı</span><span class="sxs-lookup"><span data-stu-id="e534c-212">FullyQualifiedName</span></span></li><li><span data-ttu-id="e534c-213">DisplayName</span><span class="sxs-lookup"><span data-stu-id="e534c-213">DisplayName</span></span></li><li><span data-ttu-id="e534c-214">Lerdir</span><span class="sxs-lookup"><span data-stu-id="e534c-214">Traits</span></span></li></ul>                                   |

<span data-ttu-id="e534c-215">`<operator>`, özelliği ve değeri arasındaki ilişkiyi açıklar:</span><span class="sxs-lookup"><span data-stu-id="e534c-215">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="e534c-216">İşleç</span><span class="sxs-lookup"><span data-stu-id="e534c-216">Operator</span></span> | <span data-ttu-id="e534c-217">İşlev</span><span class="sxs-lookup"><span data-stu-id="e534c-217">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="e534c-218">Tam eşleşme</span><span class="sxs-lookup"><span data-stu-id="e534c-218">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="e534c-219">Tam eşleşme yok</span><span class="sxs-lookup"><span data-stu-id="e534c-219">Not exact match</span></span> |
| `~`      | <span data-ttu-id="e534c-220">İçerir</span><span class="sxs-lookup"><span data-stu-id="e534c-220">Contains</span></span>        |
| `!~`     | <span data-ttu-id="e534c-221">İçermez</span><span class="sxs-lookup"><span data-stu-id="e534c-221">Not contains</span></span>    |

<span data-ttu-id="e534c-222">`<value>` bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="e534c-222">`<value>` is a string.</span></span> <span data-ttu-id="e534c-223">Tüm aramalar büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="e534c-223">All the lookups are case insensitive.</span></span>

<span data-ttu-id="e534c-224">`<operator>` olmayan bir ifade `FullyQualifiedName` özelliğinde `contains` olarak kabul edilir (örneğin, `dotnet test --filter xyz` `dotnet test --filter FullyQualifiedName~xyz`aynıdır).</span><span class="sxs-lookup"><span data-stu-id="e534c-224">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="e534c-225">İfadeler koşullu işleçlerle birleştirilebilecek:</span><span class="sxs-lookup"><span data-stu-id="e534c-225">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="e534c-226">İşleç</span><span class="sxs-lookup"><span data-stu-id="e534c-226">Operator</span></span>            | <span data-ttu-id="e534c-227">İşlev</span><span class="sxs-lookup"><span data-stu-id="e534c-227">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="e534c-228">VEYA</span><span class="sxs-lookup"><span data-stu-id="e534c-228">OR</span></span>       |
| `&`                 | <span data-ttu-id="e534c-229">AND</span><span class="sxs-lookup"><span data-stu-id="e534c-229">AND</span></span>      |

<span data-ttu-id="e534c-230">Koşullu işleçler kullandığınızda (örneğin, `(Name~TestMethod1) | (Name~TestMethod2)`) ifadeleri parantez içine alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e534c-230">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="e534c-231">Seçmeli birim testi filtrelemeyi kullanma hakkında daha fazla bilgi ve örnekler için bkz. [Seçmeli birim testlerini çalıştırma](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="e534c-231">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e534c-232">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e534c-232">See also</span></span>

- [<span data-ttu-id="e534c-233">Çerçeveler ve hedefler</span><span class="sxs-lookup"><span data-stu-id="e534c-233">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="e534c-234">.NET Core çalışma zamanı tanımlayıcısı (RID) kataloğu</span><span class="sxs-lookup"><span data-stu-id="e534c-234">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
