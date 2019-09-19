---
title: DotNet test komutu
description: DotNet test komutu, belirli bir projedeki birim testlerini yürütmek için kullanılır.
ms.date: 05/29/2018
ms.openlocfilehash: 306b6f8d890e567afc419b0408d7e683baaa814d
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117570"
---
# <a name="dotnet-test"></a><span data-ttu-id="d459f-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="d459f-103">dotnet test</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="d459f-104">Ad</span><span class="sxs-lookup"><span data-stu-id="d459f-104">Name</span></span>

<span data-ttu-id="d459f-105">`dotnet test`-Birim testlerini yürütmek için kullanılan .NET test sürücüsü.</span><span class="sxs-lookup"><span data-stu-id="d459f-105">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d459f-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="d459f-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="d459f-107">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="d459f-107">.NET Core 2.1</span></span>](#tab/netcore21)

```dotnetcli
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] 
    [-v|--verbosity] [-- <RunSettings arguments>]

dotnet test [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="d459f-108">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="d459f-108">.NET Core 2.0</span></span>](#tab/netcore20)

```dotnetcli
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]

dotnet test [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d459f-109">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="d459f-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]

dotnet test [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="d459f-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d459f-110">Description</span></span>

<span data-ttu-id="d459f-111">Komut `dotnet test` , belirli bir projedeki birim testlerini yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d459f-111">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="d459f-112">Komut `dotnet test` , bir proje için belirtilen Test Çalıştırıcısı konsol uygulamasını başlatır.</span><span class="sxs-lookup"><span data-stu-id="d459f-112">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="d459f-113">Test Çalıştırıcısı, bir birim test çerçevesi (örneğin, MSTest, NUnit veya xUnit) için tanımlanan testleri yürütür ve her testin başarısını veya başarısızlığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="d459f-113">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="d459f-114">Tüm testler başarılı olursa, Test Çalıştırıcısı çıkış kodu olarak 0 döndürür; Aksi takdirde, herhangi bir test başarısız olursa, 1 döndürür.</span><span class="sxs-lookup"><span data-stu-id="d459f-114">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="d459f-115">Test Çalıştırıcısı ve birim testi kitaplığı, NuGet paketleri olarak paketlenir ve proje için sıradan bağımlılıklar olarak geri yüklenir.</span><span class="sxs-lookup"><span data-stu-id="d459f-115">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="d459f-116">Test projeleri, aşağıdaki örnek proje dosyasında görüldüğü gibi `<PackageReference>` sıradan bir öğe kullanarak Test Çalıştırıcısı belirtir:</span><span class="sxs-lookup"><span data-stu-id="d459f-116">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="d459f-117">Arguments</span><span class="sxs-lookup"><span data-stu-id="d459f-117">Arguments</span></span>

`PROJECT`

<span data-ttu-id="d459f-118">Test projesinin yolu.</span><span class="sxs-lookup"><span data-stu-id="d459f-118">Path to the test project.</span></span> <span data-ttu-id="d459f-119">Belirtilmezse, varsayılan olarak geçerli dizin olur.</span><span class="sxs-lookup"><span data-stu-id="d459f-119">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="d459f-120">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="d459f-120">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="d459f-121">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="d459f-121">.NET Core 2.1</span></span>](#tab/netcore21)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="d459f-122">Test çalıştırmasında belirtilen yoldan özel test bağdaştırıcılarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="d459f-122">Use the custom test adapters from the specified path in the test run.</span></span>

`--blame`

<span data-ttu-id="d459f-123">Testleri sorumluyu modunda çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="d459f-123">Runs the tests in blame mode.</span></span> <span data-ttu-id="d459f-124">Bu seçenek, test ana bilgisayarının kilitlenmesine neden olan sorunlu testleri yalıtmak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="d459f-124">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="d459f-125">Geçerli dizinde, kilitlenmeden önce yürütülen testlerin sırasını yakalayan *Sequence. xml* olarak bir çıktı dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d459f-125">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="d459f-126">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d459f-126">Defines the build configuration.</span></span> <span data-ttu-id="d459f-127">Varsayılan değer `Debug`, ancak projenizin yapılandırması bu varsayılan SDK ayarını geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="d459f-127">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="d459f-128">Test çalıştırması için veri toplayıcıyı etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="d459f-128">Enables data collector for the test run.</span></span> <span data-ttu-id="d459f-129">Daha fazla bilgi için bkz. [test çalıştırmasını izleme ve çözümleme](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="d459f-129">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="d459f-130">Test platformu için tanılama modunu sağlar ve belirtilen dosyaya tanılama iletileri yazar.</span><span class="sxs-lookup"><span data-stu-id="d459f-130">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="d459f-131">Belirli bir [çerçeve](../../standard/frameworks.md)için test ikililerini arar.</span><span class="sxs-lookup"><span data-stu-id="d459f-131">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="d459f-132">Geçerli projede verilen ifadeyi kullanarak testleri filtreler.</span><span class="sxs-lookup"><span data-stu-id="d459f-132">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="d459f-133">Daha fazla bilgi için, [filtre seçeneği ayrıntıları](#filter-option-details) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="d459f-133">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="d459f-134">Seçmeli birim testi filtrelemeyi kullanma hakkında daha fazla bilgi ve örnekler için bkz. [Seçmeli birim testlerini çalıştırma](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="d459f-134">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="d459f-135">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="d459f-135">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="d459f-136">Test sonuçları için bir günlükçü belirtir.</span><span class="sxs-lookup"><span data-stu-id="d459f-136">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="d459f-137">Test projesi çalıştırılmadan önce derlenmez.</span><span class="sxs-lookup"><span data-stu-id="d459f-137">Doesn't build the test project before running it.</span></span> <span data-ttu-id="d459f-138">`--no-restore` Bayrak de örtülü olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="d459f-138">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="d459f-139">Komutu çalıştırılırken örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="d459f-139">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="d459f-140">Çalıştırılacak ikililerin bulunacağı dizin.</span><span class="sxs-lookup"><span data-stu-id="d459f-140">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="d459f-141">Test sonuçlarının yerleştirileceği dizin.</span><span class="sxs-lookup"><span data-stu-id="d459f-141">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="d459f-142">Belirtilen dizin yoksa, oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d459f-142">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="d459f-143">Testleri çalıştırmak için kullanılacak dosya.`.runsettings`</span><span class="sxs-lookup"><span data-stu-id="d459f-143">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="d459f-144">Birim testlerini bir `.runsettings` dosya kullanarak yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="d459f-144">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file?view=vs-2019)

`-t|--list-tests`

<span data-ttu-id="d459f-145">Geçerli projedeki tüm bulunan testlerin listesini listeleyin.</span><span class="sxs-lookup"><span data-stu-id="d459f-145">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="d459f-146">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d459f-146">Sets the verbosity level of the command.</span></span> <span data-ttu-id="d459f-147">İzin verilen değerler `q[uiet]` `m[inimal]` ,`n[ormal]`,, ve .`diag[nostic]` `d[etailed]`</span><span class="sxs-lookup"><span data-stu-id="d459f-147">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`RunSettings arguments`

<span data-ttu-id="d459f-148">Test için RunSettings yapılandırması olarak geçirilen bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="d459f-148">Arguments passed as RunSettings configurations for the test.</span></span> <span data-ttu-id="d459f-149">Bağımsız değişkenler "- `[name]=[value]` -" sonra çift olarak belirtilir (--sonra boşluk bırakın).</span><span class="sxs-lookup"><span data-stu-id="d459f-149">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="d459f-150">Birden çok `[name]=[value]` çifti ayırmak için bir boşluk kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d459f-150">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

<span data-ttu-id="d459f-151">Örnek: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="d459f-151">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

<span data-ttu-id="d459f-152">Runsettings hakkında daha fazla bilgi için bkz [. VSTest. Console. exe: RunSettings bağımsız değişkenleri](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)geçiliyor.</span><span class="sxs-lookup"><span data-stu-id="d459f-152">For more information about RunSettings, see [vstest.console.exe: Passing RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="d459f-153">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="d459f-153">.NET Core 2.0</span></span>](#tab/netcore20)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="d459f-154">Test çalıştırmasında belirtilen yoldan özel test bağdaştırıcılarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="d459f-154">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="d459f-155">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d459f-155">Defines the build configuration.</span></span> <span data-ttu-id="d459f-156">Varsayılan değer `Debug`, ancak projenizin yapılandırması bu varsayılan SDK ayarını geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="d459f-156">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="d459f-157">Test çalıştırması için veri toplayıcıyı etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="d459f-157">Enables data collector for the test run.</span></span> <span data-ttu-id="d459f-158">Daha fazla bilgi için bkz. [test çalıştırmasını izleme ve çözümleme](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="d459f-158">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="d459f-159">Test platformu için tanılama modunu sağlar ve belirtilen dosyaya tanılama iletileri yazar.</span><span class="sxs-lookup"><span data-stu-id="d459f-159">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="d459f-160">Belirli bir [çerçeve](../../standard/frameworks.md)için test ikililerini arar.</span><span class="sxs-lookup"><span data-stu-id="d459f-160">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="d459f-161">Geçerli projede verilen ifadeyi kullanarak testleri filtreler.</span><span class="sxs-lookup"><span data-stu-id="d459f-161">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="d459f-162">Daha fazla bilgi için, [filtre seçeneği ayrıntıları](#filter-option-details) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="d459f-162">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="d459f-163">Seçmeli birim testi filtrelemeyi kullanma hakkında daha fazla bilgi ve örnekler için bkz. [Seçmeli birim testlerini çalıştırma](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="d459f-163">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="d459f-164">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="d459f-164">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="d459f-165">Test sonuçları için bir günlükçü belirtir.</span><span class="sxs-lookup"><span data-stu-id="d459f-165">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="d459f-166">Test projesi çalıştırılmadan önce derlenmez.</span><span class="sxs-lookup"><span data-stu-id="d459f-166">Doesn't build the test project before running it.</span></span> <span data-ttu-id="d459f-167">`--no-restore` Bayrak de örtülü olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="d459f-167">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="d459f-168">Komutu çalıştırılırken örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="d459f-168">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="d459f-169">Çalıştırılacak ikililerin bulunacağı dizin.</span><span class="sxs-lookup"><span data-stu-id="d459f-169">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="d459f-170">Test sonuçlarının yerleştirileceği dizin.</span><span class="sxs-lookup"><span data-stu-id="d459f-170">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="d459f-171">Belirtilen dizin yoksa, oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d459f-171">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="d459f-172">Testleri çalıştırmak için kullanılacak dosya.`.runsettings`</span><span class="sxs-lookup"><span data-stu-id="d459f-172">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="d459f-173">Birim testlerini bir `.runsettings` dosya kullanarak yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="d459f-173">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file?view=vs-2019)

`-t|--list-tests`

<span data-ttu-id="d459f-174">Geçerli projedeki tüm bulunan testlerin listesini listeleyin.</span><span class="sxs-lookup"><span data-stu-id="d459f-174">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="d459f-175">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d459f-175">Sets the verbosity level of the command.</span></span> <span data-ttu-id="d459f-176">İzin verilen değerler `q[uiet]` `m[inimal]` ,`n[ormal]`,, ve .`diag[nostic]` `d[etailed]`</span><span class="sxs-lookup"><span data-stu-id="d459f-176">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d459f-177">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="d459f-177">.NET Core 1.x</span></span>](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="d459f-178">Test çalıştırmasında belirtilen yoldan özel test bağdaştırıcılarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="d459f-178">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="d459f-179">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d459f-179">Defines the build configuration.</span></span> <span data-ttu-id="d459f-180">Varsayılan değer `Debug`, ancak projenizin yapılandırması bu varsayılan SDK ayarını geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="d459f-180">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="d459f-181">Test platformu için tanılama modunu sağlar ve belirtilen dosyaya tanılama iletileri yazar.</span><span class="sxs-lookup"><span data-stu-id="d459f-181">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="d459f-182">Belirli bir [çerçeve](../../standard/frameworks.md)için test ikililerini arar.</span><span class="sxs-lookup"><span data-stu-id="d459f-182">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="d459f-183">Geçerli projede verilen ifadeyi kullanarak testleri filtreler.</span><span class="sxs-lookup"><span data-stu-id="d459f-183">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="d459f-184">Daha fazla bilgi için, [filtre seçeneği ayrıntıları](#filter-option-details) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="d459f-184">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="d459f-185">Seçmeli birim testi filtrelemeyi kullanma hakkında daha fazla bilgi ve örnekler için bkz. [Seçmeli birim testlerini çalıştırma](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="d459f-185">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="d459f-186">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="d459f-186">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="d459f-187">Test sonuçları için bir günlükçü belirtir.</span><span class="sxs-lookup"><span data-stu-id="d459f-187">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="d459f-188">Test projesi çalıştırılmadan önce derlenmez.</span><span class="sxs-lookup"><span data-stu-id="d459f-188">Doesn't build the test project before running it.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="d459f-189">Çalıştırılacak ikililerin bulunacağı dizin.</span><span class="sxs-lookup"><span data-stu-id="d459f-189">Directory in which to find the binaries to run.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="d459f-190">Testleri çalıştırmak için kullanılacak dosya.`.runsettings`</span><span class="sxs-lookup"><span data-stu-id="d459f-190">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="d459f-191">Birim testlerini bir `.runsettings` dosya kullanarak yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="d459f-191">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file?view=vs-2019)

`-t|--list-tests`

<span data-ttu-id="d459f-192">Geçerli projedeki tüm bulunan testlerin listesini listeleyin.</span><span class="sxs-lookup"><span data-stu-id="d459f-192">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="d459f-193">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d459f-193">Sets the verbosity level of the command.</span></span> <span data-ttu-id="d459f-194">İzin verilen değerler `q[uiet]` `m[inimal]` ,`n[ormal]`,, ve .`diag[nostic]` `d[etailed]`</span><span class="sxs-lookup"><span data-stu-id="d459f-194">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="d459f-195">Örnekler</span><span class="sxs-lookup"><span data-stu-id="d459f-195">Examples</span></span>

<span data-ttu-id="d459f-196">Projedeki testleri geçerli dizinde çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="d459f-196">Run the tests in the project in the current directory:</span></span>

`dotnet test`

<span data-ttu-id="d459f-197">`test1` Projedeki testleri çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="d459f-197">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

<span data-ttu-id="d459f-198">Projedeki testleri geçerli dizinde çalıştırın ve TRX biçiminde bir test sonuçları dosyası oluşturun:</span><span class="sxs-lookup"><span data-stu-id="d459f-198">Run the tests in the project in the current directory and generate a test results file in the trx format:</span></span>

`dotnet test --logger trx`

## <a name="filter-option-details"></a><span data-ttu-id="d459f-199">Filtre seçeneği ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="d459f-199">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="d459f-200">`<Expression>`biçimindedir `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="d459f-200">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="d459f-201">`<property>`, `Test Case`öğesinin bir özniteliğidir.</span><span class="sxs-lookup"><span data-stu-id="d459f-201">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="d459f-202">Popüler birim testi çerçeveleri tarafından desteklenen özellikler aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="d459f-202">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="d459f-203">Test çerçevesi</span><span class="sxs-lookup"><span data-stu-id="d459f-203">Test Framework</span></span> | <span data-ttu-id="d459f-204">Desteklenen özellikler</span><span class="sxs-lookup"><span data-stu-id="d459f-204">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="d459f-205">MSTest</span><span class="sxs-lookup"><span data-stu-id="d459f-205">MSTest</span></span>         | <ul><li><span data-ttu-id="d459f-206">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="d459f-206">FullyQualifiedName</span></span></li><li><span data-ttu-id="d459f-207">Ad</span><span class="sxs-lookup"><span data-stu-id="d459f-207">Name</span></span></li><li><span data-ttu-id="d459f-208">Sınıf</span><span class="sxs-lookup"><span data-stu-id="d459f-208">ClassName</span></span></li><li><span data-ttu-id="d459f-209">Öncelik</span><span class="sxs-lookup"><span data-stu-id="d459f-209">Priority</span></span></li><li><span data-ttu-id="d459f-210">TestCategory</span><span class="sxs-lookup"><span data-stu-id="d459f-210">TestCategory</span></span></li></ul> |
| <span data-ttu-id="d459f-211">xUnit</span><span class="sxs-lookup"><span data-stu-id="d459f-211">xUnit</span></span>          | <ul><li><span data-ttu-id="d459f-212">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="d459f-212">FullyQualifiedName</span></span></li><li><span data-ttu-id="d459f-213">DisplayName</span><span class="sxs-lookup"><span data-stu-id="d459f-213">DisplayName</span></span></li><li><span data-ttu-id="d459f-214">Lerdir</span><span class="sxs-lookup"><span data-stu-id="d459f-214">Traits</span></span></li></ul>                                   |

<span data-ttu-id="d459f-215">, `<operator>` Özelliği ve değeri arasındaki ilişkiyi açıklar:</span><span class="sxs-lookup"><span data-stu-id="d459f-215">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="d459f-216">İşleç</span><span class="sxs-lookup"><span data-stu-id="d459f-216">Operator</span></span> | <span data-ttu-id="d459f-217">İşlev</span><span class="sxs-lookup"><span data-stu-id="d459f-217">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="d459f-218">Tam eşleşme</span><span class="sxs-lookup"><span data-stu-id="d459f-218">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="d459f-219">Tam eşleşme yok</span><span class="sxs-lookup"><span data-stu-id="d459f-219">Not exact match</span></span> |
| `~`      | <span data-ttu-id="d459f-220">İçerir</span><span class="sxs-lookup"><span data-stu-id="d459f-220">Contains</span></span>        |

<span data-ttu-id="d459f-221">`<value>`bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="d459f-221">`<value>` is a string.</span></span> <span data-ttu-id="d459f-222">Tüm aramalar büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="d459f-222">All the lookups are case insensitive.</span></span>

<span data-ttu-id="d459f-223">Bir `<operator>` ifadesi, otomatik olarak `contains` on `FullyQualifiedName` özelliği olarak kabul edilir (örneğin, `dotnet test --filter xyz` ile `dotnet test --filter FullyQualifiedName~xyz`aynıdır).</span><span class="sxs-lookup"><span data-stu-id="d459f-223">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="d459f-224">İfadeler koşullu işleçlerle birleştirilebilecek:</span><span class="sxs-lookup"><span data-stu-id="d459f-224">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="d459f-225">İşleç</span><span class="sxs-lookup"><span data-stu-id="d459f-225">Operator</span></span>            | <span data-ttu-id="d459f-226">İşlev</span><span class="sxs-lookup"><span data-stu-id="d459f-226">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="d459f-227">VEYA</span><span class="sxs-lookup"><span data-stu-id="d459f-227">OR</span></span>       |
| `&`                 | <span data-ttu-id="d459f-228">AND</span><span class="sxs-lookup"><span data-stu-id="d459f-228">AND</span></span>      |

<span data-ttu-id="d459f-229">Koşullu işleçler kullandığınızda (örneğin, `(Name~TestMethod1) | (Name~TestMethod2)`) ifadeleri parantez içine alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d459f-229">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="d459f-230">Seçmeli birim testi filtrelemeyi kullanma hakkında daha fazla bilgi ve örnekler için bkz. [Seçmeli birim testlerini çalıştırma](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="d459f-230">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d459f-231">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d459f-231">See also</span></span>

- [<span data-ttu-id="d459f-232">Çerçeveler ve hedefler</span><span class="sxs-lookup"><span data-stu-id="d459f-232">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="d459f-233">.NET Core çalışma zamanı tanımlayıcısı (RID) kataloğu</span><span class="sxs-lookup"><span data-stu-id="d459f-233">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
