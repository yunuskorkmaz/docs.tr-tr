---
title: DotNet test command - .NET Core CLI
description: Dotnet test komutu, belirli bir proje ile birim testleri yürütmek için kullanılır.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 8a10ac9175ee5fcf8649efbb07d8d382ac3afdc7
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696276"
---
# <a name="dotnet-test"></a><span data-ttu-id="dde56-103">DotNet test</span><span class="sxs-lookup"><span data-stu-id="dde56-103">dotnet test</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="dde56-104">Ad</span><span class="sxs-lookup"><span data-stu-id="dde56-104">Name</span></span>

<span data-ttu-id="dde56-105">`dotnet test` -.NET birim testleri çalıştırmak için kullanılan sürücü sınayın.</span><span class="sxs-lookup"><span data-stu-id="dde56-105">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="dde56-106">Özet</span><span class="sxs-lookup"><span data-stu-id="dde56-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="dde56-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="dde56-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="dde56-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="dde56-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="dde56-109">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="dde56-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]
dotnet test [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="dde56-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dde56-110">Description</span></span>

<span data-ttu-id="dde56-111">`dotnet test` Komutu, belirli bir proje ile birim testleri çalıştırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dde56-111">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="dde56-112">`dotnet test` Komutu proje için belirtilen test Çalıştırıcısı konsol uygulaması başlatır.</span><span class="sxs-lookup"><span data-stu-id="dde56-112">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="dde56-113">Sınama Çalıştırıcısı birim test çerçevesi (örneğin, mstest'i, NUnit veya xUnit) için tanımlanan testleri yürütür ve başarı veya başarısızlık her sınamanın raporlar.</span><span class="sxs-lookup"><span data-stu-id="dde56-113">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="dde56-114">Sınama Çalıştırıcısı ve birim testi kitaplığı NuGet paketleri olarak paketlenir ve proje için sıradan bağımlılıklar olarak geri yüklenir.</span><span class="sxs-lookup"><span data-stu-id="dde56-114">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="dde56-115">Test projeleri belirtin sıradan kullanarak test Çalıştırıcısı `<PackageReference>` aşağıdaki örnek proje dosyasında görülen öğe:</span><span class="sxs-lookup"><span data-stu-id="dde56-115">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="dde56-116">Arguments</span><span class="sxs-lookup"><span data-stu-id="dde56-116">Arguments</span></span>

`PROJECT`

<span data-ttu-id="dde56-117">Oluşturduğunuz test projesinin yolu.</span><span class="sxs-lookup"><span data-stu-id="dde56-117">Path to the test project.</span></span> <span data-ttu-id="dde56-118">Belirtilmezse, geçerli dizine varsayılan olur.</span><span class="sxs-lookup"><span data-stu-id="dde56-118">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="dde56-119">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="dde56-119">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="dde56-120">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="dde56-120">.NET Core 2.1</span></span>](#tab/netcore21)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="dde56-121">Belirtilen yol özel test bağdaştırıcılarından test çalışması kullanın.</span><span class="sxs-lookup"><span data-stu-id="dde56-121">Use the custom test adapters from the specified path in the test run.</span></span>

`--blame`

<span data-ttu-id="dde56-122">Testleri nedenlerle modunda çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="dde56-122">Runs the tests in blame mode.</span></span> <span data-ttu-id="dde56-123">Bu seçenek test ana çökmesine neden sorunlu testleri yalıtmaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="dde56-123">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="dde56-124">Bir çıktı dosyası geçerli dizinde oluşturur *Sequence.xml* kilitlenme önce testleri yürütme sırasını yakalar.</span><span class="sxs-lookup"><span data-stu-id="dde56-124">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="dde56-125">Derleme yapılandırması tanımlar.</span><span class="sxs-lookup"><span data-stu-id="dde56-125">Defines the build configuration.</span></span> <span data-ttu-id="dde56-126">Varsayılan değer `Debug`, ancak bu ayarın SDK projenizin yapılandırmasını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="dde56-126">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="dde56-127">Test çalışması için veri toplayıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="dde56-127">Enables data collector for the test run.</span></span> <span data-ttu-id="dde56-128">Daha fazla bilgi için bkz: [İzleyici ve test çalışmasını çözümlemek](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="dde56-128">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="dde56-129">Test platform ve yazma tanılama iletileri belirtilen dosya için tanılama modunu etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="dde56-129">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="dde56-130">Belirli bir test ikili dosyaları arar [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="dde56-130">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="dde56-131">Verilen ifade kullanarak geçerli proje testlerinde kullanıma filtreler.</span><span class="sxs-lookup"><span data-stu-id="dde56-131">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="dde56-132">Daha fazla bilgi için bkz: [filtre seçeneği ayrıntıları](#filter-option-details) bölümü.</span><span class="sxs-lookup"><span data-stu-id="dde56-132">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="dde56-133">Daha fazla bilgi ve seçmeli birim testi filtreleme kullanma hakkında örnekler için bkz: [seçmeli birim testlerini çalıştırma](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="dde56-133">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="dde56-134">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="dde56-134">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="dde56-135">Test sonuçları için Günlükçü belirtir.</span><span class="sxs-lookup"><span data-stu-id="dde56-135">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="dde56-136">Oluşturduğunuz test projesinin çalıştırmadan önce derleme değil.</span><span class="sxs-lookup"><span data-stu-id="dde56-136">Doesn't build the test project before running it.</span></span> <span data-ttu-id="dde56-137">Ayrıca örtük ayarlar `--no-restore` bayrağı.</span><span class="sxs-lookup"><span data-stu-id="dde56-137">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="dde56-138">Örtük bir geri yükleme komutu çalıştırırken yürütmez.</span><span class="sxs-lookup"><span data-stu-id="dde56-138">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="dde56-139">Çalıştırmak için ikili dosyaları bulmak dizin.</span><span class="sxs-lookup"><span data-stu-id="dde56-139">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="dde56-140">Test sonuçları yerleştirilmesi nerede bulunacağını dizin.</span><span class="sxs-lookup"><span data-stu-id="dde56-140">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="dde56-141">Belirtilen dizin yoksa, oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="dde56-141">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="dde56-142">Testleri çalıştırırken kullanılacak ayarları.</span><span class="sxs-lookup"><span data-stu-id="dde56-142">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="dde56-143">Tüm geçerli projede bulunan testleri listeler.</span><span class="sxs-lookup"><span data-stu-id="dde56-143">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="dde56-144">Komutun ayrıntı düzeyi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="dde56-144">Sets the verbosity level of the command.</span></span> <span data-ttu-id="dde56-145">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="dde56-145">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="dde56-146">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="dde56-146">.NET Core 2.0</span></span>](#tab/netcore20)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="dde56-147">Belirtilen yol özel test bağdaştırıcılarından test çalışması kullanın.</span><span class="sxs-lookup"><span data-stu-id="dde56-147">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="dde56-148">Derleme yapılandırması tanımlar.</span><span class="sxs-lookup"><span data-stu-id="dde56-148">Defines the build configuration.</span></span> <span data-ttu-id="dde56-149">Varsayılan değer `Debug`, ancak bu ayarın SDK projenizin yapılandırmasını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="dde56-149">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="dde56-150">Test çalışması için veri toplayıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="dde56-150">Enables data collector for the test run.</span></span> <span data-ttu-id="dde56-151">Daha fazla bilgi için bkz: [İzleyici ve test çalışmasını çözümlemek](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="dde56-151">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="dde56-152">Test platform ve yazma tanılama iletileri belirtilen dosya için tanılama modunu etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="dde56-152">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="dde56-153">Belirli bir test ikili dosyaları arar [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="dde56-153">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="dde56-154">Verilen ifade kullanarak geçerli proje testlerinde kullanıma filtreler.</span><span class="sxs-lookup"><span data-stu-id="dde56-154">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="dde56-155">Daha fazla bilgi için bkz: [filtre seçeneği ayrıntıları](#filter-option-details) bölümü.</span><span class="sxs-lookup"><span data-stu-id="dde56-155">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="dde56-156">Daha fazla bilgi ve seçmeli birim testi filtreleme kullanma hakkında örnekler için bkz: [seçmeli birim testlerini çalıştırma](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="dde56-156">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="dde56-157">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="dde56-157">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="dde56-158">Test sonuçları için Günlükçü belirtir.</span><span class="sxs-lookup"><span data-stu-id="dde56-158">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="dde56-159">Oluşturduğunuz test projesinin çalıştırmadan önce derleme değil.</span><span class="sxs-lookup"><span data-stu-id="dde56-159">Doesn't build the test project before running it.</span></span> <span data-ttu-id="dde56-160">Ayrıca örtük ayarlar `--no-restore` bayrağı.</span><span class="sxs-lookup"><span data-stu-id="dde56-160">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="dde56-161">Örtük bir geri yükleme komutu çalıştırırken yürütmez.</span><span class="sxs-lookup"><span data-stu-id="dde56-161">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="dde56-162">Çalıştırmak için ikili dosyaları bulmak dizin.</span><span class="sxs-lookup"><span data-stu-id="dde56-162">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="dde56-163">Test sonuçları yerleştirilmesi nerede bulunacağını dizin.</span><span class="sxs-lookup"><span data-stu-id="dde56-163">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="dde56-164">Belirtilen dizin yoksa, oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="dde56-164">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="dde56-165">Testleri çalıştırırken kullanılacak ayarları.</span><span class="sxs-lookup"><span data-stu-id="dde56-165">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="dde56-166">Tüm geçerli projede bulunan testleri listeler.</span><span class="sxs-lookup"><span data-stu-id="dde56-166">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="dde56-167">Komutun ayrıntı düzeyi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="dde56-167">Sets the verbosity level of the command.</span></span> <span data-ttu-id="dde56-168">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="dde56-168">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="dde56-169">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="dde56-169">.NET Core 1.x</span></span>](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="dde56-170">Belirtilen yol özel test bağdaştırıcılarından test çalışması kullanın.</span><span class="sxs-lookup"><span data-stu-id="dde56-170">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="dde56-171">Derleme yapılandırması tanımlar.</span><span class="sxs-lookup"><span data-stu-id="dde56-171">Defines the build configuration.</span></span> <span data-ttu-id="dde56-172">Varsayılan değer `Debug`, ancak bu ayarın SDK projenizin yapılandırmasını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="dde56-172">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="dde56-173">Test platform ve yazma tanılama iletileri belirtilen dosya için tanılama modunu etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="dde56-173">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="dde56-174">Belirli bir test ikili dosyaları arar [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="dde56-174">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="dde56-175">Verilen ifade kullanarak geçerli proje testlerinde kullanıma filtreler.</span><span class="sxs-lookup"><span data-stu-id="dde56-175">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="dde56-176">Daha fazla bilgi için bkz: [filtre seçeneği ayrıntıları](#filter-option-details) bölümü.</span><span class="sxs-lookup"><span data-stu-id="dde56-176">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="dde56-177">Daha fazla bilgi ve seçmeli birim testi filtreleme kullanma hakkında örnekler için bkz: [seçmeli birim testlerini çalıştırma](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="dde56-177">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="dde56-178">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="dde56-178">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="dde56-179">Test sonuçları için Günlükçü belirtir.</span><span class="sxs-lookup"><span data-stu-id="dde56-179">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="dde56-180">Oluşturduğunuz test projesinin çalıştırmadan önce derleme değil.</span><span class="sxs-lookup"><span data-stu-id="dde56-180">Doesn't build the test project before running it.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="dde56-181">Çalıştırmak için ikili dosyaları bulmak dizin.</span><span class="sxs-lookup"><span data-stu-id="dde56-181">Directory in which to find the binaries to run.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="dde56-182">Testleri çalıştırırken kullanılacak ayarları.</span><span class="sxs-lookup"><span data-stu-id="dde56-182">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="dde56-183">Tüm geçerli projede bulunan testleri listeler.</span><span class="sxs-lookup"><span data-stu-id="dde56-183">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="dde56-184">Komutun ayrıntı düzeyi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="dde56-184">Sets the verbosity level of the command.</span></span> <span data-ttu-id="dde56-185">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="dde56-185">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="dde56-186">Örnekler</span><span class="sxs-lookup"><span data-stu-id="dde56-186">Examples</span></span>

<span data-ttu-id="dde56-187">Geçerli dizin projede Testleri Çalıştır:</span><span class="sxs-lookup"><span data-stu-id="dde56-187">Run the tests in the project in the current directory:</span></span>

`dotnet test`

<span data-ttu-id="dde56-188">Testleri çalıştırmak `test1` proje:</span><span class="sxs-lookup"><span data-stu-id="dde56-188">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

## <a name="filter-option-details"></a><span data-ttu-id="dde56-189">Filtre seçeneği ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="dde56-189">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="dde56-190">`<Expression>` biçimdedir `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="dde56-190">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="dde56-191">`<property>` bir özniteliği olan `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="dde56-191">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="dde56-192">Popüler birim test çerçevelerini tarafından desteklenen özellikler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="dde56-192">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="dde56-193">Test çerçevesi</span><span class="sxs-lookup"><span data-stu-id="dde56-193">Test Framework</span></span> | <span data-ttu-id="dde56-194">Desteklenen özellikler</span><span class="sxs-lookup"><span data-stu-id="dde56-194">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="dde56-195">MSTest</span><span class="sxs-lookup"><span data-stu-id="dde56-195">MSTest</span></span>         | <ul><li><span data-ttu-id="dde56-196">Karşılık gelen fullyqualifiedname öğesi</span><span class="sxs-lookup"><span data-stu-id="dde56-196">FullyQualifiedName</span></span></li><li><span data-ttu-id="dde56-197">Ad</span><span class="sxs-lookup"><span data-stu-id="dde56-197">Name</span></span></li><li><span data-ttu-id="dde56-198">className</span><span class="sxs-lookup"><span data-stu-id="dde56-198">ClassName</span></span></li><li><span data-ttu-id="dde56-199">Öncelik</span><span class="sxs-lookup"><span data-stu-id="dde56-199">Priority</span></span></li><li><span data-ttu-id="dde56-200">TestCategory</span><span class="sxs-lookup"><span data-stu-id="dde56-200">TestCategory</span></span></li></ul> |
| <span data-ttu-id="dde56-201">xUnit</span><span class="sxs-lookup"><span data-stu-id="dde56-201">xUnit</span></span>          | <ul><li><span data-ttu-id="dde56-202">Karşılık gelen fullyqualifiedname öğesi</span><span class="sxs-lookup"><span data-stu-id="dde56-202">FullyQualifiedName</span></span></li><li><span data-ttu-id="dde56-203">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="dde56-203">DisplayName</span></span></li><li><span data-ttu-id="dde56-204">Özellikleri</span><span class="sxs-lookup"><span data-stu-id="dde56-204">Traits</span></span></li></ul>                                   |

<span data-ttu-id="dde56-205">`<operator>` Özellik ve değer arasındaki ilişkiyi açıklar:</span><span class="sxs-lookup"><span data-stu-id="dde56-205">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="dde56-206">İşleç</span><span class="sxs-lookup"><span data-stu-id="dde56-206">Operator</span></span> | <span data-ttu-id="dde56-207">İşlev</span><span class="sxs-lookup"><span data-stu-id="dde56-207">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="dde56-208">Tam eşleşme</span><span class="sxs-lookup"><span data-stu-id="dde56-208">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="dde56-209">Değil tam eşleşme</span><span class="sxs-lookup"><span data-stu-id="dde56-209">Not exact match</span></span> |
| `~`      | <span data-ttu-id="dde56-210">İçerir</span><span class="sxs-lookup"><span data-stu-id="dde56-210">Contains</span></span>        |

<span data-ttu-id="dde56-211">`<value>` bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="dde56-211">`<value>` is a string.</span></span> <span data-ttu-id="dde56-212">Tüm arama büyük/küçük harfe duyarsızdır.</span><span class="sxs-lookup"><span data-stu-id="dde56-212">All the lookups are case insensitive.</span></span>

<span data-ttu-id="dde56-213">Bir ifade olmadan bir `<operator>` otomatik olarak kabul bir `contains` üzerinde `FullyQualifiedName` özelliği (örneğin, `dotnet test --filter xyz` aynı `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="dde56-213">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="dde56-214">İfadeler ile Koşullu işleçler katılabilir:</span><span class="sxs-lookup"><span data-stu-id="dde56-214">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="dde56-215">İşleç</span><span class="sxs-lookup"><span data-stu-id="dde56-215">Operator</span></span>            | <span data-ttu-id="dde56-216">İşlev</span><span class="sxs-lookup"><span data-stu-id="dde56-216">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="dde56-217">VEYA</span><span class="sxs-lookup"><span data-stu-id="dde56-217">OR</span></span>       |
| `&`                 | <span data-ttu-id="dde56-218">AND</span><span class="sxs-lookup"><span data-stu-id="dde56-218">AND</span></span>      |

<span data-ttu-id="dde56-219">İfadeler parantez içine Koşullu işleçler kullanırken içine aldığınız (örneğin, `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="dde56-219">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="dde56-220">Daha fazla bilgi ve seçmeli birim testi filtreleme kullanma hakkında örnekler için bkz: [seçmeli birim testlerini çalıştırma](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="dde56-220">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dde56-221">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dde56-221">See also</span></span>

[<span data-ttu-id="dde56-222">Çerçeveler ve hedefler</span><span class="sxs-lookup"><span data-stu-id="dde56-222">Frameworks and Targets</span></span>](../../standard/frameworks.md)  
[<span data-ttu-id="dde56-223">.NET çekirdeği çalışma zamanı tanımlayıcı (RID) Kataloğu</span><span class="sxs-lookup"><span data-stu-id="dde56-223">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
