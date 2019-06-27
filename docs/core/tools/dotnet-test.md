---
title: DotNet testi komutu
description: Dotnet testi komut, belirli bir projede birim testleri yürütmek için kullanılır.
ms.date: 05/29/2018
ms.openlocfilehash: 6b67273f549edd7712237756a5aba13d5cb59a61
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410360"
---
# <a name="dotnet-test"></a><span data-ttu-id="ef607-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="ef607-103">dotnet test</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="ef607-104">Ad</span><span class="sxs-lookup"><span data-stu-id="ef607-104">Name</span></span>

<span data-ttu-id="ef607-105">`dotnet test` -.NET birim testleri yürütmek için kullanılan sürücü test edin.</span><span class="sxs-lookup"><span data-stu-id="ef607-105">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ef607-106">Synopsis</span><span class="sxs-lookup"><span data-stu-id="ef607-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="ef607-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="ef607-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] 
    [-v|--verbosity] [-- <RunSettings arguments>]

dotnet test [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="ef607-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="ef607-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]

dotnet test [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ef607-109">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="ef607-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]

dotnet test [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="ef607-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ef607-110">Description</span></span>

<span data-ttu-id="ef607-111">`dotnet test` Komutu, belirli bir projede birim testleri yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ef607-111">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="ef607-112">`dotnet test` Test Çalıştırıcısı konsol uygulaması projesi için belirtilen komutu çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="ef607-112">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="ef607-113">Test Çalıştırıcısı, birim test çerçevesi (örneğin, MSTest, NUnit veya xUnit) için tanımlanan testleri yürütür ve başarılı veya başarısız her test raporlar.</span><span class="sxs-lookup"><span data-stu-id="ef607-113">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="ef607-114">Tüm testler başarılı olursa, test Çalıştırıcısı 0 bir çıkış kodu döndürür; Aksi takdirde herhangi bir test başarısız olursa, 1 döndürür.</span><span class="sxs-lookup"><span data-stu-id="ef607-114">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="ef607-115">Test Çalıştırıcısı ve birim testi kitaplığı NuGet paketleri olarak paketlenir ve proje için sıradan bağımlılık olarak geri yüklenir.</span><span class="sxs-lookup"><span data-stu-id="ef607-115">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="ef607-116">Test projeleri belirtmek sıradan kullanarak test Çalıştırıcısı `<PackageReference>` aşağıdaki örnek proje dosyasında görülen öğe:</span><span class="sxs-lookup"><span data-stu-id="ef607-116">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="ef607-117">Arguments</span><span class="sxs-lookup"><span data-stu-id="ef607-117">Arguments</span></span>

`PROJECT`

<span data-ttu-id="ef607-118">Test projesinin yolu.</span><span class="sxs-lookup"><span data-stu-id="ef607-118">Path to the test project.</span></span> <span data-ttu-id="ef607-119">Belirtilmezse, geçerli dizin için varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="ef607-119">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="ef607-120">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="ef607-120">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="ef607-121">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="ef607-121">.NET Core 2.1</span></span>](#tab/netcore21)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="ef607-122">Belirtilen yoldan özel test bağdaştırıcılarını test çalıştırmasında kullanın.</span><span class="sxs-lookup"><span data-stu-id="ef607-122">Use the custom test adapters from the specified path in the test run.</span></span>

`--blame`

<span data-ttu-id="ef607-123">Testleri sorumluyu modunda çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="ef607-123">Runs the tests in blame mode.</span></span> <span data-ttu-id="ef607-124">Bu seçenek, sorunlu testleri test ana bilgisayarı kilitlenmesine neden olan sorunları ayırmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="ef607-124">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="ef607-125">Bir çıkış dosyası geçerli dizinde oluşturur *Sequence.xml* , kilitlenme önce testler yürütme sırası yakalar.</span><span class="sxs-lookup"><span data-stu-id="ef607-125">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="ef607-126">Derleme yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ef607-126">Defines the build configuration.</span></span> <span data-ttu-id="ef607-127">Varsayılan değer `Debug`, ancak bu ayarın SDK proje yapılandırmasını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="ef607-127">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="ef607-128">Test çalıştırması için veri toplayıcısını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="ef607-128">Enables data collector for the test run.</span></span> <span data-ttu-id="ef607-129">Daha fazla bilgi için [izleme ve test çalışmasını çözümlemek](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="ef607-129">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="ef607-130">Test platformu ve yazma tanılama iletileri için belirtilen dosyaya tanılama modunu etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="ef607-130">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="ef607-131">Belirli bir test ikililerinin arar [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="ef607-131">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="ef607-132">Testleri kullanarak belirtilen ifade geçerli projede filtreler.</span><span class="sxs-lookup"><span data-stu-id="ef607-132">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="ef607-133">Daha fazla bilgi için [filtre seçeneği ayrıntıları](#filter-option-details) bölümü.</span><span class="sxs-lookup"><span data-stu-id="ef607-133">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="ef607-134">Daha fazla bilgi ve seçmeli birim testi filtreleme kullanma hakkında daha fazla örnek için bkz. [seçmeli birim testleri çalıştırma](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="ef607-134">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="ef607-135">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="ef607-135">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="ef607-136">Test sonuçları için bir Günlükçü belirtir.</span><span class="sxs-lookup"><span data-stu-id="ef607-136">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="ef607-137">Test projesi çalıştırmadan önce derleme değil.</span><span class="sxs-lookup"><span data-stu-id="ef607-137">Doesn't build the test project before running it.</span></span> <span data-ttu-id="ef607-138">Ayrıca örtülü ayarlar `--no-restore` bayrağı.</span><span class="sxs-lookup"><span data-stu-id="ef607-138">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="ef607-139">Örtük bir geri yükleme komutu çalıştırırken yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="ef607-139">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="ef607-140">Çalıştırmak için ikili dosyaları bulmak dizin.</span><span class="sxs-lookup"><span data-stu-id="ef607-140">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="ef607-141">Test sonuçlarını yerleştirilmesi nerede bulunacağını dizin.</span><span class="sxs-lookup"><span data-stu-id="ef607-141">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="ef607-142">Belirtilen dizin yoksa, oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ef607-142">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="ef607-143">`.runsettings` Testleri çalıştırmak için kullanılacak dosya.</span><span class="sxs-lookup"><span data-stu-id="ef607-143">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="ef607-144">Kullanarak birim testlerini yapılandırma bir `.runsettings` dosya.</span><span class="sxs-lookup"><span data-stu-id="ef607-144">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file?view=vs-2019)

`-t|--list-tests`

<span data-ttu-id="ef607-145">Tüm geçerli projede bulunan testleri listeler.</span><span class="sxs-lookup"><span data-stu-id="ef607-145">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="ef607-146">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ef607-146">Sets the verbosity level of the command.</span></span> <span data-ttu-id="ef607-147">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="ef607-147">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`RunSettings arguments`

<span data-ttu-id="ef607-148">Test yapılandırmalarını RunSettings olarak bağımsız değişkenleri geçirildi.</span><span class="sxs-lookup"><span data-stu-id="ef607-148">Arguments passed as RunSettings configurations for the test.</span></span> <span data-ttu-id="ef607-149">Bağımsız değişkenler olarak belirtilen `[name]=[value]` sonra çiftlerini "--" (--sonra boşluk unutmayın).</span><span class="sxs-lookup"><span data-stu-id="ef607-149">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="ef607-150">Birden çok ayırmak için kullanılan bir alanı `[name]=[value]` çiftleri.</span><span class="sxs-lookup"><span data-stu-id="ef607-150">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

<span data-ttu-id="ef607-151">Örnek: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="ef607-151">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

<span data-ttu-id="ef607-152">RunSettings hakkında daha fazla bilgi için bkz: [vstest.console.exe: RunSettings bağımsız değişken geçirme](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="ef607-152">For more information about RunSettings, see [vstest.console.exe: Passing RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="ef607-153">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="ef607-153">.NET Core 2.0</span></span>](#tab/netcore20)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="ef607-154">Belirtilen yoldan özel test bağdaştırıcılarını test çalıştırmasında kullanın.</span><span class="sxs-lookup"><span data-stu-id="ef607-154">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="ef607-155">Derleme yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ef607-155">Defines the build configuration.</span></span> <span data-ttu-id="ef607-156">Varsayılan değer `Debug`, ancak bu ayarın SDK proje yapılandırmasını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="ef607-156">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="ef607-157">Test çalıştırması için veri toplayıcısını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="ef607-157">Enables data collector for the test run.</span></span> <span data-ttu-id="ef607-158">Daha fazla bilgi için [izleme ve test çalışmasını çözümlemek](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="ef607-158">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="ef607-159">Test platformu ve yazma tanılama iletileri için belirtilen dosyaya tanılama modunu etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="ef607-159">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="ef607-160">Belirli bir test ikililerinin arar [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="ef607-160">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="ef607-161">Testleri kullanarak belirtilen ifade geçerli projede filtreler.</span><span class="sxs-lookup"><span data-stu-id="ef607-161">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="ef607-162">Daha fazla bilgi için [filtre seçeneği ayrıntıları](#filter-option-details) bölümü.</span><span class="sxs-lookup"><span data-stu-id="ef607-162">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="ef607-163">Daha fazla bilgi ve seçmeli birim testi filtreleme kullanma hakkında daha fazla örnek için bkz. [seçmeli birim testleri çalıştırma](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="ef607-163">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="ef607-164">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="ef607-164">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="ef607-165">Test sonuçları için bir Günlükçü belirtir.</span><span class="sxs-lookup"><span data-stu-id="ef607-165">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="ef607-166">Test projesi çalıştırmadan önce derleme değil.</span><span class="sxs-lookup"><span data-stu-id="ef607-166">Doesn't build the test project before running it.</span></span> <span data-ttu-id="ef607-167">Ayrıca örtülü ayarlar `--no-restore` bayrağı.</span><span class="sxs-lookup"><span data-stu-id="ef607-167">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="ef607-168">Örtük bir geri yükleme komutu çalıştırırken yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="ef607-168">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="ef607-169">Çalıştırmak için ikili dosyaları bulmak dizin.</span><span class="sxs-lookup"><span data-stu-id="ef607-169">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="ef607-170">Test sonuçlarını yerleştirilmesi nerede bulunacağını dizin.</span><span class="sxs-lookup"><span data-stu-id="ef607-170">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="ef607-171">Belirtilen dizin yoksa, oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ef607-171">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="ef607-172">`.runsettings` Testleri çalıştırmak için kullanılacak dosya.</span><span class="sxs-lookup"><span data-stu-id="ef607-172">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="ef607-173">Kullanarak birim testlerini yapılandırma bir `.runsettings` dosya.</span><span class="sxs-lookup"><span data-stu-id="ef607-173">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file?view=vs-2019)

`-t|--list-tests`

<span data-ttu-id="ef607-174">Tüm geçerli projede bulunan testleri listeler.</span><span class="sxs-lookup"><span data-stu-id="ef607-174">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="ef607-175">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ef607-175">Sets the verbosity level of the command.</span></span> <span data-ttu-id="ef607-176">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="ef607-176">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ef607-177">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="ef607-177">.NET Core 1.x</span></span>](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="ef607-178">Belirtilen yoldan özel test bağdaştırıcılarını test çalıştırmasında kullanın.</span><span class="sxs-lookup"><span data-stu-id="ef607-178">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="ef607-179">Derleme yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ef607-179">Defines the build configuration.</span></span> <span data-ttu-id="ef607-180">Varsayılan değer `Debug`, ancak bu ayarın SDK proje yapılandırmasını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="ef607-180">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="ef607-181">Test platformu ve yazma tanılama iletileri için belirtilen dosyaya tanılama modunu etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="ef607-181">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="ef607-182">Belirli bir test ikililerinin arar [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="ef607-182">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="ef607-183">Testleri kullanarak belirtilen ifade geçerli projede filtreler.</span><span class="sxs-lookup"><span data-stu-id="ef607-183">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="ef607-184">Daha fazla bilgi için [filtre seçeneği ayrıntıları](#filter-option-details) bölümü.</span><span class="sxs-lookup"><span data-stu-id="ef607-184">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="ef607-185">Daha fazla bilgi ve seçmeli birim testi filtreleme kullanma hakkında daha fazla örnek için bkz. [seçmeli birim testleri çalıştırma](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="ef607-185">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="ef607-186">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="ef607-186">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="ef607-187">Test sonuçları için bir Günlükçü belirtir.</span><span class="sxs-lookup"><span data-stu-id="ef607-187">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="ef607-188">Test projesi çalıştırmadan önce derleme değil.</span><span class="sxs-lookup"><span data-stu-id="ef607-188">Doesn't build the test project before running it.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="ef607-189">Çalıştırmak için ikili dosyaları bulmak dizin.</span><span class="sxs-lookup"><span data-stu-id="ef607-189">Directory in which to find the binaries to run.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="ef607-190">`.runsettings` Testleri çalıştırmak için kullanılacak dosya.</span><span class="sxs-lookup"><span data-stu-id="ef607-190">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="ef607-191">Kullanarak birim testlerini yapılandırma bir `.runsettings` dosya.</span><span class="sxs-lookup"><span data-stu-id="ef607-191">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file?view=vs-2019)

`-t|--list-tests`

<span data-ttu-id="ef607-192">Tüm geçerli projede bulunan testleri listeler.</span><span class="sxs-lookup"><span data-stu-id="ef607-192">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="ef607-193">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ef607-193">Sets the verbosity level of the command.</span></span> <span data-ttu-id="ef607-194">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="ef607-194">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="ef607-195">Örnekler</span><span class="sxs-lookup"><span data-stu-id="ef607-195">Examples</span></span>

<span data-ttu-id="ef607-196">Geçerli dizindeki projedeki Testleri Çalıştır:</span><span class="sxs-lookup"><span data-stu-id="ef607-196">Run the tests in the project in the current directory:</span></span>

`dotnet test`

<span data-ttu-id="ef607-197">Testleri çalıştırmak `test1` proje:</span><span class="sxs-lookup"><span data-stu-id="ef607-197">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

<span data-ttu-id="ef607-198">Geçerli dizindeki projedeki testleri çalıştırmak ve trx biçiminde bir test sonuçları dosyası oluşturun:</span><span class="sxs-lookup"><span data-stu-id="ef607-198">Run the tests in the project in the current directory and generate a test results file in the trx format:</span></span>

`dotnet test --logger:trx`

## <a name="filter-option-details"></a><span data-ttu-id="ef607-199">Filtre seçeneği ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="ef607-199">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="ef607-200">`<Expression>` şu biçimdedir `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="ef607-200">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="ef607-201">`<property>` bir özniteliğidir `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="ef607-201">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="ef607-202">Popüler birim testi çerçevelerini tarafından desteklenen özellikler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="ef607-202">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="ef607-203">Test çerçevesi</span><span class="sxs-lookup"><span data-stu-id="ef607-203">Test Framework</span></span> | <span data-ttu-id="ef607-204">Desteklenen özellikler</span><span class="sxs-lookup"><span data-stu-id="ef607-204">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="ef607-205">MSTest</span><span class="sxs-lookup"><span data-stu-id="ef607-205">MSTest</span></span>         | <ul><li><span data-ttu-id="ef607-206">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="ef607-206">FullyQualifiedName</span></span></li><li><span data-ttu-id="ef607-207">Ad</span><span class="sxs-lookup"><span data-stu-id="ef607-207">Name</span></span></li><li><span data-ttu-id="ef607-208">className</span><span class="sxs-lookup"><span data-stu-id="ef607-208">ClassName</span></span></li><li><span data-ttu-id="ef607-209">Öncelik</span><span class="sxs-lookup"><span data-stu-id="ef607-209">Priority</span></span></li><li><span data-ttu-id="ef607-210">TestCategory</span><span class="sxs-lookup"><span data-stu-id="ef607-210">TestCategory</span></span></li></ul> |
| <span data-ttu-id="ef607-211">xUnit</span><span class="sxs-lookup"><span data-stu-id="ef607-211">xUnit</span></span>          | <ul><li><span data-ttu-id="ef607-212">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="ef607-212">FullyQualifiedName</span></span></li><li><span data-ttu-id="ef607-213">displayName</span><span class="sxs-lookup"><span data-stu-id="ef607-213">DisplayName</span></span></li><li><span data-ttu-id="ef607-214">Nitelikler</span><span class="sxs-lookup"><span data-stu-id="ef607-214">Traits</span></span></li></ul>                                   |

<span data-ttu-id="ef607-215">`<operator>` Özellik ve değer arasındaki ilişkiyi açıklar:</span><span class="sxs-lookup"><span data-stu-id="ef607-215">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="ef607-216">İşleç</span><span class="sxs-lookup"><span data-stu-id="ef607-216">Operator</span></span> | <span data-ttu-id="ef607-217">İşlev</span><span class="sxs-lookup"><span data-stu-id="ef607-217">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="ef607-218">Tam eşleşme</span><span class="sxs-lookup"><span data-stu-id="ef607-218">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="ef607-219">Değil tam eşleşme</span><span class="sxs-lookup"><span data-stu-id="ef607-219">Not exact match</span></span> |
| `~`      | <span data-ttu-id="ef607-220">İçerir</span><span class="sxs-lookup"><span data-stu-id="ef607-220">Contains</span></span>        |

<span data-ttu-id="ef607-221">`<value>` bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="ef607-221">`<value>` is a string.</span></span> <span data-ttu-id="ef607-222">Tüm aramalar büyük/küçük harfe duyarsızdır.</span><span class="sxs-lookup"><span data-stu-id="ef607-222">All the lookups are case insensitive.</span></span>

<span data-ttu-id="ef607-223">Bir ifade olmadan bir `<operator>` otomatik olarak kabul edilir bir `contains` üzerinde `FullyQualifiedName` özelliği (örneğin, `dotnet test --filter xyz` aynı `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="ef607-223">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="ef607-224">Koşullu işleçler ile ifadeler katılabilir:</span><span class="sxs-lookup"><span data-stu-id="ef607-224">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="ef607-225">İşleç</span><span class="sxs-lookup"><span data-stu-id="ef607-225">Operator</span></span>            | <span data-ttu-id="ef607-226">İşlev</span><span class="sxs-lookup"><span data-stu-id="ef607-226">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="ef607-227">VEYA</span><span class="sxs-lookup"><span data-stu-id="ef607-227">OR</span></span>       |
| `&`                 | <span data-ttu-id="ef607-228">AND</span><span class="sxs-lookup"><span data-stu-id="ef607-228">AND</span></span>      |

<span data-ttu-id="ef607-229">İfadeleri parantez içinde Koşullu işleçler kullanırken içine aldığınız (örneğin, `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="ef607-229">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="ef607-230">Daha fazla bilgi ve seçmeli birim testi filtreleme kullanma hakkında daha fazla örnek için bkz. [seçmeli birim testleri çalıştırma](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="ef607-230">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ef607-231">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef607-231">See also</span></span>

- [<span data-ttu-id="ef607-232">Çerçeveler ve hedefler</span><span class="sxs-lookup"><span data-stu-id="ef607-232">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="ef607-233">.NET core çalışma zamanı tanımlayıcı (RID) Kataloğu</span><span class="sxs-lookup"><span data-stu-id="ef607-233">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
