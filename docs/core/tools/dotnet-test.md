---
title: DotNet testi command - .NET Core CLI
description: Dotnet testi komut, belirli bir projede birim testleri yürütmek için kullanılır.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 7946196b27489870da1c16b15cbf5f078ae89c61
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44361241"
---
# <a name="dotnet-test"></a><span data-ttu-id="245e8-103">DotNet testi</span><span class="sxs-lookup"><span data-stu-id="245e8-103">dotnet test</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="245e8-104">Ad</span><span class="sxs-lookup"><span data-stu-id="245e8-104">Name</span></span>

<span data-ttu-id="245e8-105">`dotnet test` -.NET birim testleri yürütmek için kullanılan sürücü test edin.</span><span class="sxs-lookup"><span data-stu-id="245e8-105">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="245e8-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="245e8-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="245e8-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="245e8-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="245e8-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="245e8-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="245e8-109">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="245e8-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]
dotnet test [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="245e8-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="245e8-110">Description</span></span>

<span data-ttu-id="245e8-111">`dotnet test` Komutu, belirli bir projede birim testleri yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="245e8-111">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="245e8-112">`dotnet test` Test Çalıştırıcısı konsol uygulaması projesi için belirtilen komutu çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="245e8-112">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="245e8-113">Test Çalıştırıcısı, birim test çerçevesi (örneğin, MSTest, NUnit veya xUnit) için tanımlanan testleri yürütür ve başarılı veya başarısız her test raporlar.</span><span class="sxs-lookup"><span data-stu-id="245e8-113">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="245e8-114">Test Çalıştırıcısı ve birim testi kitaplığı NuGet paketleri olarak paketlenir ve proje için sıradan bağımlılık olarak geri yüklenir.</span><span class="sxs-lookup"><span data-stu-id="245e8-114">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="245e8-115">Test projeleri belirtmek sıradan kullanarak test Çalıştırıcısı `<PackageReference>` aşağıdaki örnek proje dosyasında görülen öğe:</span><span class="sxs-lookup"><span data-stu-id="245e8-115">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="245e8-116">Arguments</span><span class="sxs-lookup"><span data-stu-id="245e8-116">Arguments</span></span>

`PROJECT`

<span data-ttu-id="245e8-117">Test projesinin yolu.</span><span class="sxs-lookup"><span data-stu-id="245e8-117">Path to the test project.</span></span> <span data-ttu-id="245e8-118">Belirtilmezse, geçerli dizin için varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="245e8-118">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="245e8-119">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="245e8-119">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="245e8-120">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="245e8-120">.NET Core 2.1</span></span>](#tab/netcore21)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="245e8-121">Belirtilen yoldan özel test bağdaştırıcılarını test çalıştırmasında kullanın.</span><span class="sxs-lookup"><span data-stu-id="245e8-121">Use the custom test adapters from the specified path in the test run.</span></span>

`--blame`

<span data-ttu-id="245e8-122">Testleri sorumluyu modunda çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="245e8-122">Runs the tests in blame mode.</span></span> <span data-ttu-id="245e8-123">Bu seçenek, sorunlu testleri test ana bilgisayarı kilitlenmesine neden olan sorunları ayırmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="245e8-123">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="245e8-124">Bir çıkış dosyası geçerli dizinde oluşturur *Sequence.xml* , kilitlenme önce testler yürütme sırası yakalar.</span><span class="sxs-lookup"><span data-stu-id="245e8-124">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="245e8-125">Derleme yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="245e8-125">Defines the build configuration.</span></span> <span data-ttu-id="245e8-126">Varsayılan değer `Debug`, ancak bu ayarın SDK proje yapılandırmasını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="245e8-126">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="245e8-127">Test çalıştırması için veri toplayıcısını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="245e8-127">Enables data collector for the test run.</span></span> <span data-ttu-id="245e8-128">Daha fazla bilgi için [izleme ve test çalışmasını çözümlemek](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="245e8-128">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="245e8-129">Test platformu ve yazma tanılama iletileri için belirtilen dosyaya tanılama modunu etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="245e8-129">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="245e8-130">Belirli bir test ikililerinin arar [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="245e8-130">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="245e8-131">Testleri kullanarak belirtilen ifade geçerli projede filtreler.</span><span class="sxs-lookup"><span data-stu-id="245e8-131">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="245e8-132">Daha fazla bilgi için [filtre seçeneği ayrıntıları](#filter-option-details) bölümü.</span><span class="sxs-lookup"><span data-stu-id="245e8-132">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="245e8-133">Daha fazla bilgi ve seçmeli birim testi filtreleme kullanma hakkında daha fazla örnek için bkz. [seçmeli birim testleri çalıştırma](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="245e8-133">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="245e8-134">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="245e8-134">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="245e8-135">Test sonuçları için bir Günlükçü belirtir.</span><span class="sxs-lookup"><span data-stu-id="245e8-135">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="245e8-136">Test projesi çalıştırmadan önce derleme değil.</span><span class="sxs-lookup"><span data-stu-id="245e8-136">Doesn't build the test project before running it.</span></span> <span data-ttu-id="245e8-137">Ayrıca örtülü ayarlar `--no-restore` bayrağı.</span><span class="sxs-lookup"><span data-stu-id="245e8-137">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="245e8-138">Örtük bir geri yükleme komutu çalıştırırken yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="245e8-138">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="245e8-139">Çalıştırmak için ikili dosyaları bulmak dizin.</span><span class="sxs-lookup"><span data-stu-id="245e8-139">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="245e8-140">Test sonuçlarını yerleştirilmesi nerede bulunacağını dizin.</span><span class="sxs-lookup"><span data-stu-id="245e8-140">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="245e8-141">Belirtilen dizin yoksa, oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="245e8-141">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="245e8-142">Testleri çalıştırırken kullanılacak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="245e8-142">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="245e8-143">Tüm geçerli projede bulunan testleri listeler.</span><span class="sxs-lookup"><span data-stu-id="245e8-143">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="245e8-144">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="245e8-144">Sets the verbosity level of the command.</span></span> <span data-ttu-id="245e8-145">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="245e8-145">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="245e8-146">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="245e8-146">.NET Core 2.0</span></span>](#tab/netcore20)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="245e8-147">Belirtilen yoldan özel test bağdaştırıcılarını test çalıştırmasında kullanın.</span><span class="sxs-lookup"><span data-stu-id="245e8-147">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="245e8-148">Derleme yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="245e8-148">Defines the build configuration.</span></span> <span data-ttu-id="245e8-149">Varsayılan değer `Debug`, ancak bu ayarın SDK proje yapılandırmasını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="245e8-149">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="245e8-150">Test çalıştırması için veri toplayıcısını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="245e8-150">Enables data collector for the test run.</span></span> <span data-ttu-id="245e8-151">Daha fazla bilgi için [izleme ve test çalışmasını çözümlemek](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="245e8-151">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="245e8-152">Test platformu ve yazma tanılama iletileri için belirtilen dosyaya tanılama modunu etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="245e8-152">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="245e8-153">Belirli bir test ikililerinin arar [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="245e8-153">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="245e8-154">Testleri kullanarak belirtilen ifade geçerli projede filtreler.</span><span class="sxs-lookup"><span data-stu-id="245e8-154">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="245e8-155">Daha fazla bilgi için [filtre seçeneği ayrıntıları](#filter-option-details) bölümü.</span><span class="sxs-lookup"><span data-stu-id="245e8-155">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="245e8-156">Daha fazla bilgi ve seçmeli birim testi filtreleme kullanma hakkında daha fazla örnek için bkz. [seçmeli birim testleri çalıştırma](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="245e8-156">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="245e8-157">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="245e8-157">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="245e8-158">Test sonuçları için bir Günlükçü belirtir.</span><span class="sxs-lookup"><span data-stu-id="245e8-158">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="245e8-159">Test projesi çalıştırmadan önce derleme değil.</span><span class="sxs-lookup"><span data-stu-id="245e8-159">Doesn't build the test project before running it.</span></span> <span data-ttu-id="245e8-160">Ayrıca örtülü ayarlar `--no-restore` bayrağı.</span><span class="sxs-lookup"><span data-stu-id="245e8-160">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="245e8-161">Örtük bir geri yükleme komutu çalıştırırken yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="245e8-161">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="245e8-162">Çalıştırmak için ikili dosyaları bulmak dizin.</span><span class="sxs-lookup"><span data-stu-id="245e8-162">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="245e8-163">Test sonuçlarını yerleştirilmesi nerede bulunacağını dizin.</span><span class="sxs-lookup"><span data-stu-id="245e8-163">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="245e8-164">Belirtilen dizin yoksa, oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="245e8-164">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="245e8-165">Testleri çalıştırırken kullanılacak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="245e8-165">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="245e8-166">Tüm geçerli projede bulunan testleri listeler.</span><span class="sxs-lookup"><span data-stu-id="245e8-166">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="245e8-167">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="245e8-167">Sets the verbosity level of the command.</span></span> <span data-ttu-id="245e8-168">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="245e8-168">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="245e8-169">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="245e8-169">.NET Core 1.x</span></span>](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="245e8-170">Belirtilen yoldan özel test bağdaştırıcılarını test çalıştırmasında kullanın.</span><span class="sxs-lookup"><span data-stu-id="245e8-170">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="245e8-171">Derleme yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="245e8-171">Defines the build configuration.</span></span> <span data-ttu-id="245e8-172">Varsayılan değer `Debug`, ancak bu ayarın SDK proje yapılandırmasını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="245e8-172">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="245e8-173">Test platformu ve yazma tanılama iletileri için belirtilen dosyaya tanılama modunu etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="245e8-173">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="245e8-174">Belirli bir test ikililerinin arar [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="245e8-174">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="245e8-175">Testleri kullanarak belirtilen ifade geçerli projede filtreler.</span><span class="sxs-lookup"><span data-stu-id="245e8-175">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="245e8-176">Daha fazla bilgi için [filtre seçeneği ayrıntıları](#filter-option-details) bölümü.</span><span class="sxs-lookup"><span data-stu-id="245e8-176">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="245e8-177">Daha fazla bilgi ve seçmeli birim testi filtreleme kullanma hakkında daha fazla örnek için bkz. [seçmeli birim testleri çalıştırma](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="245e8-177">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="245e8-178">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="245e8-178">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="245e8-179">Test sonuçları için bir Günlükçü belirtir.</span><span class="sxs-lookup"><span data-stu-id="245e8-179">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="245e8-180">Test projesi çalıştırmadan önce derleme değil.</span><span class="sxs-lookup"><span data-stu-id="245e8-180">Doesn't build the test project before running it.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="245e8-181">Çalıştırmak için ikili dosyaları bulmak dizin.</span><span class="sxs-lookup"><span data-stu-id="245e8-181">Directory in which to find the binaries to run.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="245e8-182">Testleri çalıştırırken kullanılacak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="245e8-182">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="245e8-183">Tüm geçerli projede bulunan testleri listeler.</span><span class="sxs-lookup"><span data-stu-id="245e8-183">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="245e8-184">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="245e8-184">Sets the verbosity level of the command.</span></span> <span data-ttu-id="245e8-185">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="245e8-185">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="245e8-186">Örnekler</span><span class="sxs-lookup"><span data-stu-id="245e8-186">Examples</span></span>

<span data-ttu-id="245e8-187">Geçerli dizindeki projedeki Testleri Çalıştır:</span><span class="sxs-lookup"><span data-stu-id="245e8-187">Run the tests in the project in the current directory:</span></span>

`dotnet test`

<span data-ttu-id="245e8-188">Testleri çalıştırmak `test1` proje:</span><span class="sxs-lookup"><span data-stu-id="245e8-188">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

<span data-ttu-id="245e8-189">Geçerli dizindeki projedeki testleri çalıştırmak ve trx biçiminde bir test sonuçları dosyası oluşturun:</span><span class="sxs-lookup"><span data-stu-id="245e8-189">Run the tests in the project in the current directory and generate a test results file in the trx format:</span></span>

`dotnet test --logger:trx`

## <a name="filter-option-details"></a><span data-ttu-id="245e8-190">Filtre seçeneği ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="245e8-190">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="245e8-191">`<Expression>` şu biçimdedir `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="245e8-191">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="245e8-192">`<property>` bir özniteliğidir `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="245e8-192">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="245e8-193">Popüler birim testi çerçevelerini tarafından desteklenen özellikler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="245e8-193">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="245e8-194">Test çerçevesi</span><span class="sxs-lookup"><span data-stu-id="245e8-194">Test Framework</span></span> | <span data-ttu-id="245e8-195">Desteklenen özellikler</span><span class="sxs-lookup"><span data-stu-id="245e8-195">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="245e8-196">MSTest</span><span class="sxs-lookup"><span data-stu-id="245e8-196">MSTest</span></span>         | <ul><li><span data-ttu-id="245e8-197">Karşılık gelen fullyqualifiedname öğesi</span><span class="sxs-lookup"><span data-stu-id="245e8-197">FullyQualifiedName</span></span></li><li><span data-ttu-id="245e8-198">Ad</span><span class="sxs-lookup"><span data-stu-id="245e8-198">Name</span></span></li><li><span data-ttu-id="245e8-199">className</span><span class="sxs-lookup"><span data-stu-id="245e8-199">ClassName</span></span></li><li><span data-ttu-id="245e8-200">Öncelik</span><span class="sxs-lookup"><span data-stu-id="245e8-200">Priority</span></span></li><li><span data-ttu-id="245e8-201">TestCategory</span><span class="sxs-lookup"><span data-stu-id="245e8-201">TestCategory</span></span></li></ul> |
| <span data-ttu-id="245e8-202">xUnit</span><span class="sxs-lookup"><span data-stu-id="245e8-202">xUnit</span></span>          | <ul><li><span data-ttu-id="245e8-203">Karşılık gelen fullyqualifiedname öğesi</span><span class="sxs-lookup"><span data-stu-id="245e8-203">FullyQualifiedName</span></span></li><li><span data-ttu-id="245e8-204">displayName</span><span class="sxs-lookup"><span data-stu-id="245e8-204">DisplayName</span></span></li><li><span data-ttu-id="245e8-205">Nitelikler</span><span class="sxs-lookup"><span data-stu-id="245e8-205">Traits</span></span></li></ul>                                   |

<span data-ttu-id="245e8-206">`<operator>` Özellik ve değer arasındaki ilişkiyi açıklar:</span><span class="sxs-lookup"><span data-stu-id="245e8-206">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="245e8-207">İşleç</span><span class="sxs-lookup"><span data-stu-id="245e8-207">Operator</span></span> | <span data-ttu-id="245e8-208">İşlev</span><span class="sxs-lookup"><span data-stu-id="245e8-208">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="245e8-209">Tam eşleşme</span><span class="sxs-lookup"><span data-stu-id="245e8-209">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="245e8-210">Değil tam eşleşme</span><span class="sxs-lookup"><span data-stu-id="245e8-210">Not exact match</span></span> |
| `~`      | <span data-ttu-id="245e8-211">İçerir</span><span class="sxs-lookup"><span data-stu-id="245e8-211">Contains</span></span>        |

<span data-ttu-id="245e8-212">`<value>` bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="245e8-212">`<value>` is a string.</span></span> <span data-ttu-id="245e8-213">Tüm aramalar büyük/küçük harfe duyarsızdır.</span><span class="sxs-lookup"><span data-stu-id="245e8-213">All the lookups are case insensitive.</span></span>

<span data-ttu-id="245e8-214">Bir ifade olmadan bir `<operator>` otomatik olarak kabul edilir bir `contains` üzerinde `FullyQualifiedName` özelliği (örneğin, `dotnet test --filter xyz` aynı `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="245e8-214">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="245e8-215">Koşullu işleçler ile ifadeler katılabilir:</span><span class="sxs-lookup"><span data-stu-id="245e8-215">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="245e8-216">İşleç</span><span class="sxs-lookup"><span data-stu-id="245e8-216">Operator</span></span>            | <span data-ttu-id="245e8-217">İşlev</span><span class="sxs-lookup"><span data-stu-id="245e8-217">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="245e8-218">VEYA</span><span class="sxs-lookup"><span data-stu-id="245e8-218">OR</span></span>       |
| `&`                 | <span data-ttu-id="245e8-219">AND</span><span class="sxs-lookup"><span data-stu-id="245e8-219">AND</span></span>      |

<span data-ttu-id="245e8-220">İfadeleri parantez içinde Koşullu işleçler kullanırken içine aldığınız (örneğin, `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="245e8-220">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="245e8-221">Daha fazla bilgi ve seçmeli birim testi filtreleme kullanma hakkında daha fazla örnek için bkz. [seçmeli birim testleri çalıştırma](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="245e8-221">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="245e8-222">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="245e8-222">See also</span></span>

* [<span data-ttu-id="245e8-223">Çerçeveler ve hedefler</span><span class="sxs-lookup"><span data-stu-id="245e8-223">Frameworks and Targets</span></span>](../../standard/frameworks.md)  
* [<span data-ttu-id="245e8-224">.NET core çalışma zamanı tanımlayıcı (RID) Kataloğu</span><span class="sxs-lookup"><span data-stu-id="245e8-224">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
