---
title: DotNet testi command - .NET Core CLI
description: Dotnet testi komut, belirli bir projede birim testleri yürütmek için kullanılır.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: e80ba874ec8d0fbc49858719dc3b9b6e02254c78
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46696462"
---
# <a name="dotnet-test"></a><span data-ttu-id="45b16-103">DotNet testi</span><span class="sxs-lookup"><span data-stu-id="45b16-103">dotnet test</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="45b16-104">Ad</span><span class="sxs-lookup"><span data-stu-id="45b16-104">Name</span></span>

<span data-ttu-id="45b16-105">`dotnet test` -.NET birim testleri yürütmek için kullanılan sürücü test edin.</span><span class="sxs-lookup"><span data-stu-id="45b16-105">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="45b16-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="45b16-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="45b16-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="45b16-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="45b16-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="45b16-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="45b16-109">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="45b16-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]
dotnet test [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="45b16-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="45b16-110">Description</span></span>

<span data-ttu-id="45b16-111">`dotnet test` Komutu, belirli bir projede birim testleri yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="45b16-111">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="45b16-112">`dotnet test` Test Çalıştırıcısı konsol uygulaması projesi için belirtilen komutu çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="45b16-112">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="45b16-113">Test Çalıştırıcısı, birim test çerçevesi (örneğin, MSTest, NUnit veya xUnit) için tanımlanan testleri yürütür ve başarılı veya başarısız her test raporlar.</span><span class="sxs-lookup"><span data-stu-id="45b16-113">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="45b16-114">Tüm testler başarılı olursa, test Çalıştırıcısı 0 bir çıkış kodu döndürür; Aksi takdirde herhangi bir test başarısız olursa, 1 döndürür.</span><span class="sxs-lookup"><span data-stu-id="45b16-114">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="45b16-115">Test Çalıştırıcısı ve birim testi kitaplığı NuGet paketleri olarak paketlenir ve proje için sıradan bağımlılık olarak geri yüklenir.</span><span class="sxs-lookup"><span data-stu-id="45b16-115">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="45b16-116">Test projeleri belirtmek sıradan kullanarak test Çalıştırıcısı `<PackageReference>` aşağıdaki örnek proje dosyasında görülen öğe:</span><span class="sxs-lookup"><span data-stu-id="45b16-116">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="45b16-117">Arguments</span><span class="sxs-lookup"><span data-stu-id="45b16-117">Arguments</span></span>

`PROJECT`

<span data-ttu-id="45b16-118">Test projesinin yolu.</span><span class="sxs-lookup"><span data-stu-id="45b16-118">Path to the test project.</span></span> <span data-ttu-id="45b16-119">Belirtilmezse, geçerli dizin için varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="45b16-119">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="45b16-120">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="45b16-120">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="45b16-121">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="45b16-121">.NET Core 2.1</span></span>](#tab/netcore21)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="45b16-122">Belirtilen yoldan özel test bağdaştırıcılarını test çalıştırmasında kullanın.</span><span class="sxs-lookup"><span data-stu-id="45b16-122">Use the custom test adapters from the specified path in the test run.</span></span>

`--blame`

<span data-ttu-id="45b16-123">Testleri sorumluyu modunda çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="45b16-123">Runs the tests in blame mode.</span></span> <span data-ttu-id="45b16-124">Bu seçenek, sorunlu testleri test ana bilgisayarı kilitlenmesine neden olan sorunları ayırmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="45b16-124">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="45b16-125">Bir çıkış dosyası geçerli dizinde oluşturur *Sequence.xml* , kilitlenme önce testler yürütme sırası yakalar.</span><span class="sxs-lookup"><span data-stu-id="45b16-125">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="45b16-126">Derleme yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="45b16-126">Defines the build configuration.</span></span> <span data-ttu-id="45b16-127">Varsayılan değer `Debug`, ancak bu ayarın SDK proje yapılandırmasını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="45b16-127">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="45b16-128">Test çalıştırması için veri toplayıcısını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="45b16-128">Enables data collector for the test run.</span></span> <span data-ttu-id="45b16-129">Daha fazla bilgi için [izleme ve test çalışmasını çözümlemek](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="45b16-129">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="45b16-130">Test platformu ve yazma tanılama iletileri için belirtilen dosyaya tanılama modunu etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="45b16-130">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="45b16-131">Belirli bir test ikililerinin arar [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="45b16-131">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="45b16-132">Testleri kullanarak belirtilen ifade geçerli projede filtreler.</span><span class="sxs-lookup"><span data-stu-id="45b16-132">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="45b16-133">Daha fazla bilgi için [filtre seçeneği ayrıntıları](#filter-option-details) bölümü.</span><span class="sxs-lookup"><span data-stu-id="45b16-133">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="45b16-134">Daha fazla bilgi ve seçmeli birim testi filtreleme kullanma hakkında daha fazla örnek için bkz. [seçmeli birim testleri çalıştırma](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="45b16-134">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="45b16-135">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="45b16-135">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="45b16-136">Test sonuçları için bir Günlükçü belirtir.</span><span class="sxs-lookup"><span data-stu-id="45b16-136">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="45b16-137">Test projesi çalıştırmadan önce derleme değil.</span><span class="sxs-lookup"><span data-stu-id="45b16-137">Doesn't build the test project before running it.</span></span> <span data-ttu-id="45b16-138">Ayrıca örtülü ayarlar `--no-restore` bayrağı.</span><span class="sxs-lookup"><span data-stu-id="45b16-138">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="45b16-139">Örtük bir geri yükleme komutu çalıştırırken yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="45b16-139">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="45b16-140">Çalıştırmak için ikili dosyaları bulmak dizin.</span><span class="sxs-lookup"><span data-stu-id="45b16-140">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="45b16-141">Test sonuçlarını yerleştirilmesi nerede bulunacağını dizin.</span><span class="sxs-lookup"><span data-stu-id="45b16-141">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="45b16-142">Belirtilen dizin yoksa, oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="45b16-142">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="45b16-143">Testleri çalıştırırken kullanılacak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="45b16-143">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="45b16-144">Tüm geçerli projede bulunan testleri listeler.</span><span class="sxs-lookup"><span data-stu-id="45b16-144">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="45b16-145">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="45b16-145">Sets the verbosity level of the command.</span></span> <span data-ttu-id="45b16-146">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="45b16-146">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="45b16-147">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="45b16-147">.NET Core 2.0</span></span>](#tab/netcore20)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="45b16-148">Belirtilen yoldan özel test bağdaştırıcılarını test çalıştırmasında kullanın.</span><span class="sxs-lookup"><span data-stu-id="45b16-148">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="45b16-149">Derleme yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="45b16-149">Defines the build configuration.</span></span> <span data-ttu-id="45b16-150">Varsayılan değer `Debug`, ancak bu ayarın SDK proje yapılandırmasını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="45b16-150">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="45b16-151">Test çalıştırması için veri toplayıcısını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="45b16-151">Enables data collector for the test run.</span></span> <span data-ttu-id="45b16-152">Daha fazla bilgi için [izleme ve test çalışmasını çözümlemek](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="45b16-152">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="45b16-153">Test platformu ve yazma tanılama iletileri için belirtilen dosyaya tanılama modunu etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="45b16-153">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="45b16-154">Belirli bir test ikililerinin arar [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="45b16-154">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="45b16-155">Testleri kullanarak belirtilen ifade geçerli projede filtreler.</span><span class="sxs-lookup"><span data-stu-id="45b16-155">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="45b16-156">Daha fazla bilgi için [filtre seçeneği ayrıntıları](#filter-option-details) bölümü.</span><span class="sxs-lookup"><span data-stu-id="45b16-156">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="45b16-157">Daha fazla bilgi ve seçmeli birim testi filtreleme kullanma hakkında daha fazla örnek için bkz. [seçmeli birim testleri çalıştırma](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="45b16-157">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="45b16-158">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="45b16-158">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="45b16-159">Test sonuçları için bir Günlükçü belirtir.</span><span class="sxs-lookup"><span data-stu-id="45b16-159">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="45b16-160">Test projesi çalıştırmadan önce derleme değil.</span><span class="sxs-lookup"><span data-stu-id="45b16-160">Doesn't build the test project before running it.</span></span> <span data-ttu-id="45b16-161">Ayrıca örtülü ayarlar `--no-restore` bayrağı.</span><span class="sxs-lookup"><span data-stu-id="45b16-161">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="45b16-162">Örtük bir geri yükleme komutu çalıştırırken yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="45b16-162">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="45b16-163">Çalıştırmak için ikili dosyaları bulmak dizin.</span><span class="sxs-lookup"><span data-stu-id="45b16-163">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="45b16-164">Test sonuçlarını yerleştirilmesi nerede bulunacağını dizin.</span><span class="sxs-lookup"><span data-stu-id="45b16-164">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="45b16-165">Belirtilen dizin yoksa, oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="45b16-165">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="45b16-166">Testleri çalıştırırken kullanılacak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="45b16-166">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="45b16-167">Tüm geçerli projede bulunan testleri listeler.</span><span class="sxs-lookup"><span data-stu-id="45b16-167">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="45b16-168">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="45b16-168">Sets the verbosity level of the command.</span></span> <span data-ttu-id="45b16-169">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="45b16-169">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="45b16-170">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="45b16-170">.NET Core 1.x</span></span>](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="45b16-171">Belirtilen yoldan özel test bağdaştırıcılarını test çalıştırmasında kullanın.</span><span class="sxs-lookup"><span data-stu-id="45b16-171">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="45b16-172">Derleme yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="45b16-172">Defines the build configuration.</span></span> <span data-ttu-id="45b16-173">Varsayılan değer `Debug`, ancak bu ayarın SDK proje yapılandırmasını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="45b16-173">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="45b16-174">Test platformu ve yazma tanılama iletileri için belirtilen dosyaya tanılama modunu etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="45b16-174">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="45b16-175">Belirli bir test ikililerinin arar [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="45b16-175">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="45b16-176">Testleri kullanarak belirtilen ifade geçerli projede filtreler.</span><span class="sxs-lookup"><span data-stu-id="45b16-176">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="45b16-177">Daha fazla bilgi için [filtre seçeneği ayrıntıları](#filter-option-details) bölümü.</span><span class="sxs-lookup"><span data-stu-id="45b16-177">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="45b16-178">Daha fazla bilgi ve seçmeli birim testi filtreleme kullanma hakkında daha fazla örnek için bkz. [seçmeli birim testleri çalıştırma](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="45b16-178">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="45b16-179">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="45b16-179">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="45b16-180">Test sonuçları için bir Günlükçü belirtir.</span><span class="sxs-lookup"><span data-stu-id="45b16-180">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="45b16-181">Test projesi çalıştırmadan önce derleme değil.</span><span class="sxs-lookup"><span data-stu-id="45b16-181">Doesn't build the test project before running it.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="45b16-182">Çalıştırmak için ikili dosyaları bulmak dizin.</span><span class="sxs-lookup"><span data-stu-id="45b16-182">Directory in which to find the binaries to run.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="45b16-183">Testleri çalıştırırken kullanılacak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="45b16-183">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="45b16-184">Tüm geçerli projede bulunan testleri listeler.</span><span class="sxs-lookup"><span data-stu-id="45b16-184">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="45b16-185">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="45b16-185">Sets the verbosity level of the command.</span></span> <span data-ttu-id="45b16-186">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="45b16-186">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="45b16-187">Örnekler</span><span class="sxs-lookup"><span data-stu-id="45b16-187">Examples</span></span>

<span data-ttu-id="45b16-188">Geçerli dizindeki projedeki Testleri Çalıştır:</span><span class="sxs-lookup"><span data-stu-id="45b16-188">Run the tests in the project in the current directory:</span></span>

`dotnet test`

<span data-ttu-id="45b16-189">Testleri çalıştırmak `test1` proje:</span><span class="sxs-lookup"><span data-stu-id="45b16-189">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

<span data-ttu-id="45b16-190">Geçerli dizindeki projedeki testleri çalıştırmak ve trx biçiminde bir test sonuçları dosyası oluşturun:</span><span class="sxs-lookup"><span data-stu-id="45b16-190">Run the tests in the project in the current directory and generate a test results file in the trx format:</span></span>

`dotnet test --logger:trx`

## <a name="filter-option-details"></a><span data-ttu-id="45b16-191">Filtre seçeneği ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="45b16-191">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="45b16-192">`<Expression>` şu biçimdedir `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="45b16-192">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="45b16-193">`<property>` bir özniteliğidir `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="45b16-193">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="45b16-194">Popüler birim testi çerçevelerini tarafından desteklenen özellikler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="45b16-194">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="45b16-195">Test çerçevesi</span><span class="sxs-lookup"><span data-stu-id="45b16-195">Test Framework</span></span> | <span data-ttu-id="45b16-196">Desteklenen özellikler</span><span class="sxs-lookup"><span data-stu-id="45b16-196">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="45b16-197">MSTest</span><span class="sxs-lookup"><span data-stu-id="45b16-197">MSTest</span></span>         | <ul><li><span data-ttu-id="45b16-198">Karşılık gelen fullyqualifiedname öğesi</span><span class="sxs-lookup"><span data-stu-id="45b16-198">FullyQualifiedName</span></span></li><li><span data-ttu-id="45b16-199">Ad</span><span class="sxs-lookup"><span data-stu-id="45b16-199">Name</span></span></li><li><span data-ttu-id="45b16-200">className</span><span class="sxs-lookup"><span data-stu-id="45b16-200">ClassName</span></span></li><li><span data-ttu-id="45b16-201">Öncelik</span><span class="sxs-lookup"><span data-stu-id="45b16-201">Priority</span></span></li><li><span data-ttu-id="45b16-202">TestCategory</span><span class="sxs-lookup"><span data-stu-id="45b16-202">TestCategory</span></span></li></ul> |
| <span data-ttu-id="45b16-203">xUnit</span><span class="sxs-lookup"><span data-stu-id="45b16-203">xUnit</span></span>          | <ul><li><span data-ttu-id="45b16-204">Karşılık gelen fullyqualifiedname öğesi</span><span class="sxs-lookup"><span data-stu-id="45b16-204">FullyQualifiedName</span></span></li><li><span data-ttu-id="45b16-205">displayName</span><span class="sxs-lookup"><span data-stu-id="45b16-205">DisplayName</span></span></li><li><span data-ttu-id="45b16-206">Nitelikler</span><span class="sxs-lookup"><span data-stu-id="45b16-206">Traits</span></span></li></ul>                                   |

<span data-ttu-id="45b16-207">`<operator>` Özellik ve değer arasındaki ilişkiyi açıklar:</span><span class="sxs-lookup"><span data-stu-id="45b16-207">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="45b16-208">İşleç</span><span class="sxs-lookup"><span data-stu-id="45b16-208">Operator</span></span> | <span data-ttu-id="45b16-209">İşlev</span><span class="sxs-lookup"><span data-stu-id="45b16-209">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="45b16-210">Tam eşleşme</span><span class="sxs-lookup"><span data-stu-id="45b16-210">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="45b16-211">Değil tam eşleşme</span><span class="sxs-lookup"><span data-stu-id="45b16-211">Not exact match</span></span> |
| `~`      | <span data-ttu-id="45b16-212">İçerir</span><span class="sxs-lookup"><span data-stu-id="45b16-212">Contains</span></span>        |

<span data-ttu-id="45b16-213">`<value>` bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="45b16-213">`<value>` is a string.</span></span> <span data-ttu-id="45b16-214">Tüm aramalar büyük/küçük harfe duyarsızdır.</span><span class="sxs-lookup"><span data-stu-id="45b16-214">All the lookups are case insensitive.</span></span>

<span data-ttu-id="45b16-215">Bir ifade olmadan bir `<operator>` otomatik olarak kabul edilir bir `contains` üzerinde `FullyQualifiedName` özelliği (örneğin, `dotnet test --filter xyz` aynı `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="45b16-215">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="45b16-216">Koşullu işleçler ile ifadeler katılabilir:</span><span class="sxs-lookup"><span data-stu-id="45b16-216">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="45b16-217">İşleç</span><span class="sxs-lookup"><span data-stu-id="45b16-217">Operator</span></span>            | <span data-ttu-id="45b16-218">İşlev</span><span class="sxs-lookup"><span data-stu-id="45b16-218">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="45b16-219">VEYA</span><span class="sxs-lookup"><span data-stu-id="45b16-219">OR</span></span>       |
| `&`                 | <span data-ttu-id="45b16-220">AND</span><span class="sxs-lookup"><span data-stu-id="45b16-220">AND</span></span>      |

<span data-ttu-id="45b16-221">İfadeleri parantez içinde Koşullu işleçler kullanırken içine aldığınız (örneğin, `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="45b16-221">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="45b16-222">Daha fazla bilgi ve seçmeli birim testi filtreleme kullanma hakkında daha fazla örnek için bkz. [seçmeli birim testleri çalıştırma](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="45b16-222">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="45b16-223">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45b16-223">See also</span></span>

* [<span data-ttu-id="45b16-224">Çerçeveler ve hedefler</span><span class="sxs-lookup"><span data-stu-id="45b16-224">Frameworks and Targets</span></span>](../../standard/frameworks.md)  
* [<span data-ttu-id="45b16-225">.NET core çalışma zamanı tanımlayıcı (RID) Kataloğu</span><span class="sxs-lookup"><span data-stu-id="45b16-225">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
