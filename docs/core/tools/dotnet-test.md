---
title: DotNet testi komutu
description: Dotnet testi komut, belirli bir projede birim testleri yürütmek için kullanılır.
ms.date: 05/29/2018
ms.openlocfilehash: 1b2a3917a930db0c0a49ebea41f568aaf4a58ee3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665539"
---
# <a name="dotnet-test"></a><span data-ttu-id="5f30f-103">DotNet testi</span><span class="sxs-lookup"><span data-stu-id="5f30f-103">dotnet test</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="5f30f-104">Ad</span><span class="sxs-lookup"><span data-stu-id="5f30f-104">Name</span></span>

<span data-ttu-id="5f30f-105">`dotnet test` -.NET birim testleri yürütmek için kullanılan sürücü test edin.</span><span class="sxs-lookup"><span data-stu-id="5f30f-105">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5f30f-106">Synopsis</span><span class="sxs-lookup"><span data-stu-id="5f30f-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="5f30f-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="5f30f-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] 
    [-v|--verbosity] [-- <RunSettings arguments>]

dotnet test [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="5f30f-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="5f30f-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]

dotnet test [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5f30f-109">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="5f30f-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]

dotnet test [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="5f30f-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5f30f-110">Description</span></span>

<span data-ttu-id="5f30f-111">`dotnet test` Komutu, belirli bir projede birim testleri yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5f30f-111">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="5f30f-112">`dotnet test` Test Çalıştırıcısı konsol uygulaması projesi için belirtilen komutu çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="5f30f-112">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="5f30f-113">Test Çalıştırıcısı, birim test çerçevesi (örneğin, MSTest, NUnit veya xUnit) için tanımlanan testleri yürütür ve başarılı veya başarısız her test raporlar.</span><span class="sxs-lookup"><span data-stu-id="5f30f-113">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="5f30f-114">Tüm testler başarılı olursa, test Çalıştırıcısı 0 bir çıkış kodu döndürür; Aksi takdirde herhangi bir test başarısız olursa, 1 döndürür.</span><span class="sxs-lookup"><span data-stu-id="5f30f-114">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="5f30f-115">Test Çalıştırıcısı ve birim testi kitaplığı NuGet paketleri olarak paketlenir ve proje için sıradan bağımlılık olarak geri yüklenir.</span><span class="sxs-lookup"><span data-stu-id="5f30f-115">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="5f30f-116">Test projeleri belirtmek sıradan kullanarak test Çalıştırıcısı `<PackageReference>` aşağıdaki örnek proje dosyasında görülen öğe:</span><span class="sxs-lookup"><span data-stu-id="5f30f-116">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="5f30f-117">Arguments</span><span class="sxs-lookup"><span data-stu-id="5f30f-117">Arguments</span></span>

`PROJECT`

<span data-ttu-id="5f30f-118">Test projesinin yolu.</span><span class="sxs-lookup"><span data-stu-id="5f30f-118">Path to the test project.</span></span> <span data-ttu-id="5f30f-119">Belirtilmezse, geçerli dizin için varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="5f30f-119">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="5f30f-120">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="5f30f-120">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="5f30f-121">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="5f30f-121">.NET Core 2.1</span></span>](#tab/netcore21)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="5f30f-122">Belirtilen yoldan özel test bağdaştırıcılarını test çalıştırmasında kullanın.</span><span class="sxs-lookup"><span data-stu-id="5f30f-122">Use the custom test adapters from the specified path in the test run.</span></span>

`--blame`

<span data-ttu-id="5f30f-123">Testleri sorumluyu modunda çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="5f30f-123">Runs the tests in blame mode.</span></span> <span data-ttu-id="5f30f-124">Bu seçenek, sorunlu testleri test ana bilgisayarı kilitlenmesine neden olan sorunları ayırmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="5f30f-124">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="5f30f-125">Bir çıkış dosyası geçerli dizinde oluşturur *Sequence.xml* , kilitlenme önce testler yürütme sırası yakalar.</span><span class="sxs-lookup"><span data-stu-id="5f30f-125">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="5f30f-126">Derleme yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5f30f-126">Defines the build configuration.</span></span> <span data-ttu-id="5f30f-127">Varsayılan değer `Debug`, ancak bu ayarın SDK proje yapılandırmasını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="5f30f-127">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="5f30f-128">Test çalıştırması için veri toplayıcısını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="5f30f-128">Enables data collector for the test run.</span></span> <span data-ttu-id="5f30f-129">Daha fazla bilgi için [izleme ve test çalışmasını çözümlemek](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="5f30f-129">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="5f30f-130">Test platformu ve yazma tanılama iletileri için belirtilen dosyaya tanılama modunu etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="5f30f-130">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="5f30f-131">Belirli bir test ikililerinin arar [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="5f30f-131">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="5f30f-132">Testleri kullanarak belirtilen ifade geçerli projede filtreler.</span><span class="sxs-lookup"><span data-stu-id="5f30f-132">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="5f30f-133">Daha fazla bilgi için [filtre seçeneği ayrıntıları](#filter-option-details) bölümü.</span><span class="sxs-lookup"><span data-stu-id="5f30f-133">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="5f30f-134">Daha fazla bilgi ve seçmeli birim testi filtreleme kullanma hakkında daha fazla örnek için bkz. [seçmeli birim testleri çalıştırma](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="5f30f-134">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="5f30f-135">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="5f30f-135">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="5f30f-136">Test sonuçları için bir Günlükçü belirtir.</span><span class="sxs-lookup"><span data-stu-id="5f30f-136">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="5f30f-137">Test projesi çalıştırmadan önce derleme değil.</span><span class="sxs-lookup"><span data-stu-id="5f30f-137">Doesn't build the test project before running it.</span></span> <span data-ttu-id="5f30f-138">Ayrıca örtülü ayarlar `--no-restore` bayrağı.</span><span class="sxs-lookup"><span data-stu-id="5f30f-138">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="5f30f-139">Örtük bir geri yükleme komutu çalıştırırken yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="5f30f-139">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="5f30f-140">Çalıştırmak için ikili dosyaları bulmak dizin.</span><span class="sxs-lookup"><span data-stu-id="5f30f-140">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="5f30f-141">Test sonuçlarını yerleştirilmesi nerede bulunacağını dizin.</span><span class="sxs-lookup"><span data-stu-id="5f30f-141">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="5f30f-142">Belirtilen dizin yoksa, oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5f30f-142">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="5f30f-143">Testleri çalıştırırken kullanılacak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5f30f-143">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="5f30f-144">Tüm geçerli projede bulunan testleri listeler.</span><span class="sxs-lookup"><span data-stu-id="5f30f-144">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="5f30f-145">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5f30f-145">Sets the verbosity level of the command.</span></span> <span data-ttu-id="5f30f-146">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="5f30f-146">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`RunSettings arguments`

<span data-ttu-id="5f30f-147">Test yapılandırmalarını RunSettings olarak bağımsız değişkenleri geçirildi.</span><span class="sxs-lookup"><span data-stu-id="5f30f-147">Arguments passed as RunSettings configurations for the test.</span></span> <span data-ttu-id="5f30f-148">Bağımsız değişkenler olarak belirtilen `[name]=[value]` sonra çiftlerini "--" (--sonra boşluk unutmayın).</span><span class="sxs-lookup"><span data-stu-id="5f30f-148">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="5f30f-149">Birden çok ayırmak için kullanılan bir alanı `[name]=[value]` çiftleri.</span><span class="sxs-lookup"><span data-stu-id="5f30f-149">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

<span data-ttu-id="5f30f-150">Örnek: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="5f30f-150">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

<span data-ttu-id="5f30f-151">RunSettings hakkında daha fazla bilgi için bkz: [vstest.console.exe: RunSettings bağımsız değişken geçirme](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="5f30f-151">For more information about RunSettings, see [vstest.console.exe: Passing RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="5f30f-152">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="5f30f-152">.NET Core 2.0</span></span>](#tab/netcore20)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="5f30f-153">Belirtilen yoldan özel test bağdaştırıcılarını test çalıştırmasında kullanın.</span><span class="sxs-lookup"><span data-stu-id="5f30f-153">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="5f30f-154">Derleme yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5f30f-154">Defines the build configuration.</span></span> <span data-ttu-id="5f30f-155">Varsayılan değer `Debug`, ancak bu ayarın SDK proje yapılandırmasını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="5f30f-155">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="5f30f-156">Test çalıştırması için veri toplayıcısını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="5f30f-156">Enables data collector for the test run.</span></span> <span data-ttu-id="5f30f-157">Daha fazla bilgi için [izleme ve test çalışmasını çözümlemek](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="5f30f-157">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="5f30f-158">Test platformu ve yazma tanılama iletileri için belirtilen dosyaya tanılama modunu etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="5f30f-158">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="5f30f-159">Belirli bir test ikililerinin arar [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="5f30f-159">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="5f30f-160">Testleri kullanarak belirtilen ifade geçerli projede filtreler.</span><span class="sxs-lookup"><span data-stu-id="5f30f-160">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="5f30f-161">Daha fazla bilgi için [filtre seçeneği ayrıntıları](#filter-option-details) bölümü.</span><span class="sxs-lookup"><span data-stu-id="5f30f-161">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="5f30f-162">Daha fazla bilgi ve seçmeli birim testi filtreleme kullanma hakkında daha fazla örnek için bkz. [seçmeli birim testleri çalıştırma](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="5f30f-162">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="5f30f-163">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="5f30f-163">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="5f30f-164">Test sonuçları için bir Günlükçü belirtir.</span><span class="sxs-lookup"><span data-stu-id="5f30f-164">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="5f30f-165">Test projesi çalıştırmadan önce derleme değil.</span><span class="sxs-lookup"><span data-stu-id="5f30f-165">Doesn't build the test project before running it.</span></span> <span data-ttu-id="5f30f-166">Ayrıca örtülü ayarlar `--no-restore` bayrağı.</span><span class="sxs-lookup"><span data-stu-id="5f30f-166">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="5f30f-167">Örtük bir geri yükleme komutu çalıştırırken yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="5f30f-167">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="5f30f-168">Çalıştırmak için ikili dosyaları bulmak dizin.</span><span class="sxs-lookup"><span data-stu-id="5f30f-168">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="5f30f-169">Test sonuçlarını yerleştirilmesi nerede bulunacağını dizin.</span><span class="sxs-lookup"><span data-stu-id="5f30f-169">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="5f30f-170">Belirtilen dizin yoksa, oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5f30f-170">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="5f30f-171">Testleri çalıştırırken kullanılacak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5f30f-171">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="5f30f-172">Tüm geçerli projede bulunan testleri listeler.</span><span class="sxs-lookup"><span data-stu-id="5f30f-172">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="5f30f-173">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5f30f-173">Sets the verbosity level of the command.</span></span> <span data-ttu-id="5f30f-174">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="5f30f-174">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5f30f-175">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="5f30f-175">.NET Core 1.x</span></span>](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="5f30f-176">Belirtilen yoldan özel test bağdaştırıcılarını test çalıştırmasında kullanın.</span><span class="sxs-lookup"><span data-stu-id="5f30f-176">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="5f30f-177">Derleme yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5f30f-177">Defines the build configuration.</span></span> <span data-ttu-id="5f30f-178">Varsayılan değer `Debug`, ancak bu ayarın SDK proje yapılandırmasını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="5f30f-178">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="5f30f-179">Test platformu ve yazma tanılama iletileri için belirtilen dosyaya tanılama modunu etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="5f30f-179">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="5f30f-180">Belirli bir test ikililerinin arar [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="5f30f-180">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="5f30f-181">Testleri kullanarak belirtilen ifade geçerli projede filtreler.</span><span class="sxs-lookup"><span data-stu-id="5f30f-181">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="5f30f-182">Daha fazla bilgi için [filtre seçeneği ayrıntıları](#filter-option-details) bölümü.</span><span class="sxs-lookup"><span data-stu-id="5f30f-182">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="5f30f-183">Daha fazla bilgi ve seçmeli birim testi filtreleme kullanma hakkında daha fazla örnek için bkz. [seçmeli birim testleri çalıştırma](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="5f30f-183">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="5f30f-184">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="5f30f-184">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="5f30f-185">Test sonuçları için bir Günlükçü belirtir.</span><span class="sxs-lookup"><span data-stu-id="5f30f-185">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="5f30f-186">Test projesi çalıştırmadan önce derleme değil.</span><span class="sxs-lookup"><span data-stu-id="5f30f-186">Doesn't build the test project before running it.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="5f30f-187">Çalıştırmak için ikili dosyaları bulmak dizin.</span><span class="sxs-lookup"><span data-stu-id="5f30f-187">Directory in which to find the binaries to run.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="5f30f-188">Testleri çalıştırırken kullanılacak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5f30f-188">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="5f30f-189">Tüm geçerli projede bulunan testleri listeler.</span><span class="sxs-lookup"><span data-stu-id="5f30f-189">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="5f30f-190">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5f30f-190">Sets the verbosity level of the command.</span></span> <span data-ttu-id="5f30f-191">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="5f30f-191">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="5f30f-192">Örnekler</span><span class="sxs-lookup"><span data-stu-id="5f30f-192">Examples</span></span>

<span data-ttu-id="5f30f-193">Geçerli dizindeki projedeki Testleri Çalıştır:</span><span class="sxs-lookup"><span data-stu-id="5f30f-193">Run the tests in the project in the current directory:</span></span>

`dotnet test`

<span data-ttu-id="5f30f-194">Testleri çalıştırmak `test1` proje:</span><span class="sxs-lookup"><span data-stu-id="5f30f-194">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

<span data-ttu-id="5f30f-195">Geçerli dizindeki projedeki testleri çalıştırmak ve trx biçiminde bir test sonuçları dosyası oluşturun:</span><span class="sxs-lookup"><span data-stu-id="5f30f-195">Run the tests in the project in the current directory and generate a test results file in the trx format:</span></span>

`dotnet test --logger:trx`

## <a name="filter-option-details"></a><span data-ttu-id="5f30f-196">Filtre seçeneği ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="5f30f-196">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="5f30f-197">`<Expression>` şu biçimdedir `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="5f30f-197">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="5f30f-198">`<property>` bir özniteliğidir `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="5f30f-198">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="5f30f-199">Popüler birim testi çerçevelerini tarafından desteklenen özellikler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="5f30f-199">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="5f30f-200">Test çerçevesi</span><span class="sxs-lookup"><span data-stu-id="5f30f-200">Test Framework</span></span> | <span data-ttu-id="5f30f-201">Desteklenen özellikler</span><span class="sxs-lookup"><span data-stu-id="5f30f-201">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="5f30f-202">MSTest</span><span class="sxs-lookup"><span data-stu-id="5f30f-202">MSTest</span></span>         | <ul><li><span data-ttu-id="5f30f-203">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="5f30f-203">FullyQualifiedName</span></span></li><li><span data-ttu-id="5f30f-204">Ad</span><span class="sxs-lookup"><span data-stu-id="5f30f-204">Name</span></span></li><li><span data-ttu-id="5f30f-205">className</span><span class="sxs-lookup"><span data-stu-id="5f30f-205">ClassName</span></span></li><li><span data-ttu-id="5f30f-206">Öncelik</span><span class="sxs-lookup"><span data-stu-id="5f30f-206">Priority</span></span></li><li><span data-ttu-id="5f30f-207">TestCategory</span><span class="sxs-lookup"><span data-stu-id="5f30f-207">TestCategory</span></span></li></ul> |
| <span data-ttu-id="5f30f-208">xUnit</span><span class="sxs-lookup"><span data-stu-id="5f30f-208">xUnit</span></span>          | <ul><li><span data-ttu-id="5f30f-209">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="5f30f-209">FullyQualifiedName</span></span></li><li><span data-ttu-id="5f30f-210">displayName</span><span class="sxs-lookup"><span data-stu-id="5f30f-210">DisplayName</span></span></li><li><span data-ttu-id="5f30f-211">Nitelikler</span><span class="sxs-lookup"><span data-stu-id="5f30f-211">Traits</span></span></li></ul>                                   |

<span data-ttu-id="5f30f-212">`<operator>` Özellik ve değer arasındaki ilişkiyi açıklar:</span><span class="sxs-lookup"><span data-stu-id="5f30f-212">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="5f30f-213">İşleç</span><span class="sxs-lookup"><span data-stu-id="5f30f-213">Operator</span></span> | <span data-ttu-id="5f30f-214">İşlev</span><span class="sxs-lookup"><span data-stu-id="5f30f-214">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="5f30f-215">Tam eşleşme</span><span class="sxs-lookup"><span data-stu-id="5f30f-215">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="5f30f-216">Değil tam eşleşme</span><span class="sxs-lookup"><span data-stu-id="5f30f-216">Not exact match</span></span> |
| `~`      | <span data-ttu-id="5f30f-217">İçerir</span><span class="sxs-lookup"><span data-stu-id="5f30f-217">Contains</span></span>        |

<span data-ttu-id="5f30f-218">`<value>` bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="5f30f-218">`<value>` is a string.</span></span> <span data-ttu-id="5f30f-219">Tüm aramalar büyük/küçük harfe duyarsızdır.</span><span class="sxs-lookup"><span data-stu-id="5f30f-219">All the lookups are case insensitive.</span></span>

<span data-ttu-id="5f30f-220">Bir ifade olmadan bir `<operator>` otomatik olarak kabul edilir bir `contains` üzerinde `FullyQualifiedName` özelliği (örneğin, `dotnet test --filter xyz` aynı `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="5f30f-220">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="5f30f-221">Koşullu işleçler ile ifadeler katılabilir:</span><span class="sxs-lookup"><span data-stu-id="5f30f-221">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="5f30f-222">İşleç</span><span class="sxs-lookup"><span data-stu-id="5f30f-222">Operator</span></span>            | <span data-ttu-id="5f30f-223">İşlev</span><span class="sxs-lookup"><span data-stu-id="5f30f-223">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="5f30f-224">VEYA</span><span class="sxs-lookup"><span data-stu-id="5f30f-224">OR</span></span>       |
| `&`                 | <span data-ttu-id="5f30f-225">AND</span><span class="sxs-lookup"><span data-stu-id="5f30f-225">AND</span></span>      |

<span data-ttu-id="5f30f-226">İfadeleri parantez içinde Koşullu işleçler kullanırken içine aldığınız (örneğin, `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="5f30f-226">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="5f30f-227">Daha fazla bilgi ve seçmeli birim testi filtreleme kullanma hakkında daha fazla örnek için bkz. [seçmeli birim testleri çalıştırma](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="5f30f-227">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5f30f-228">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5f30f-228">See also</span></span>

- [<span data-ttu-id="5f30f-229">Çerçeveler ve hedefler</span><span class="sxs-lookup"><span data-stu-id="5f30f-229">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="5f30f-230">.NET core çalışma zamanı tanımlayıcı (RID) Kataloğu</span><span class="sxs-lookup"><span data-stu-id="5f30f-230">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
