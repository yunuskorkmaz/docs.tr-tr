---
title: DotNet VSTest komutu
description: DotNet VSTest komutu bir proje ve tüm bağımlılıklarını oluşturur.
ms.date: 02/27/2020
ms.openlocfilehash: f7db58f4aab59354b8c69ce0371324c23482dafe
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975400"
---
# <a name="dotnet-vstest"></a><span data-ttu-id="59001-103">dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="59001-103">dotnet vstest</span></span>

<span data-ttu-id="59001-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="59001-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

> [!IMPORTANT]
> <span data-ttu-id="59001-105">Bu `dotnet vstest` komut, artık derlemeleri `dotnet test`çalıştırmak için kullanılabilecek tarafından değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="59001-105">The `dotnet vstest` command is superseded by `dotnet test`, which can now be used to run assemblies.</span></span> <span data-ttu-id="59001-106">Bkz [`dotnet test`](dotnet-test.md)..</span><span class="sxs-lookup"><span data-stu-id="59001-106">See [`dotnet test`](dotnet-test.md).</span></span>

## <a name="name"></a><span data-ttu-id="59001-107">Name</span><span class="sxs-lookup"><span data-stu-id="59001-107">Name</span></span>

<span data-ttu-id="59001-108">`dotnet-vstest`-Belirtilen derlemelerdeki testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="59001-108">`dotnet-vstest` - Runs tests from the specified assemblies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="59001-109">Özeti</span><span class="sxs-lookup"><span data-stu-id="59001-109">Synopsis</span></span>

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Blame] [--Diag <PATH_TO_LOG_FILE>]
    [--Framework <FRAMEWORK>] [--InIsolation] [-lt|--ListTests <FILE_NAME>]
    [--logger <LOGGER_URI/FRIENDLY_NAME>] [--Parallel]
    [--ParentProcessId <PROCESS_ID>] [--Platform] <PLATFORM_TYPE>
    [--Port <PORT>] [--ResultsDirectory<PATH>] [--Settings <SETTINGS_FILE>]
    [--TestAdapterPath <PATH>] [--TestCaseFilter <EXPRESSION>]
    [--Tests <TEST_NAMES>] [[--] <args>...]]

dotnet vstest -?|--Help
```

## <a name="description"></a><span data-ttu-id="59001-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="59001-110">Description</span></span>

<span data-ttu-id="59001-111">Komut `dotnet-vstest` , otomatik birim `VSTest.Console` testlerini çalıştırmak için komut satırı uygulamasını çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="59001-111">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="59001-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="59001-112">Arguments</span></span>

- **`TEST_FILE_NAMES`**

  <span data-ttu-id="59001-113">Belirtilen derlemelerdeki testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="59001-113">Run tests from the specified assemblies.</span></span> <span data-ttu-id="59001-114">Birden çok test derleme adını boşluklarla ayırın.</span><span class="sxs-lookup"><span data-stu-id="59001-114">Separate multiple test assembly names with spaces.</span></span> <span data-ttu-id="59001-115">Joker karakterler desteklenir.</span><span class="sxs-lookup"><span data-stu-id="59001-115">Wildcards are supported.</span></span>

## <a name="options"></a><span data-ttu-id="59001-116">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="59001-116">Options</span></span>

- **`--Blame`**

  <span data-ttu-id="59001-117">Testleri sorumluyu modunda çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="59001-117">Runs the tests in blame mode.</span></span> <span data-ttu-id="59001-118">Bu seçenek, test ana bilgisayarının kilitlenmesine neden olan sorunlu testleri yalıtmak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="59001-118">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="59001-119">Geçerli dizinde, kilitlenmeden önce yürütülen testlerin sırasını yakalayan *Sequence. xml* olarak bir çıktı dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="59001-119">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`--Diag <PATH_TO_LOG_FILE>`**

  <span data-ttu-id="59001-120">Test platformu için ayrıntılı günlükleri etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="59001-120">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="59001-121">Günlükler, belirtilen dosyaya yazılır.</span><span class="sxs-lookup"><span data-stu-id="59001-121">Logs are written to the provided file.</span></span>

- **`--Framework <FRAMEWORK>`**

  <span data-ttu-id="59001-122">Test yürütmesi için kullanılan hedef .NET Framework sürümü.</span><span class="sxs-lookup"><span data-stu-id="59001-122">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="59001-123">Geçerli değer örnekleri `.NETFramework,Version=v4.6` veya `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="59001-123">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="59001-124">Desteklenen diğer değerler, `Framework40` `Framework45` `FrameworkCore10`, ve `FrameworkUap10`' dir.</span><span class="sxs-lookup"><span data-stu-id="59001-124">Other supported values are `Framework40`, `Framework45`, `FrameworkCore10`, and `FrameworkUap10`.</span></span>

- **`--InIsolation`**

  <span data-ttu-id="59001-125">Testleri yalıtılmış bir işlemde çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="59001-125">Runs the tests in an isolated process.</span></span> <span data-ttu-id="59001-126">Bu, *VSTest. Console. exe* işleminin testlerin bir hata üzerinde durdurulması olasılığını azaltır, ancak testler daha yavaş çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="59001-126">This makes *vstest.console.exe* process less likely to be stopped on an error in the tests, but tests may run slower.</span></span>

- **`-lt|--ListTests <FILE_NAME>`**

  <span data-ttu-id="59001-127">Verilen test kapsayıcısından tüm bulunan testleri listeler.</span><span class="sxs-lookup"><span data-stu-id="59001-127">Lists all discovered tests from the given test container.</span></span>

- **`--logger <LOGGER_URI/FRIENDLY_NAME>`**

  <span data-ttu-id="59001-128">Test sonuçları için bir günlükçü belirtin.</span><span class="sxs-lookup"><span data-stu-id="59001-128">Specify a logger for test results.</span></span>

  - <span data-ttu-id="59001-129">Team Foundation Server için test sonuçlarını yayınlamak için `TfsPublisher` günlükçü sağlayıcısını kullanın:</span><span class="sxs-lookup"><span data-stu-id="59001-129">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

    ```console
    /logger:TfsPublisher;
        Collection=<team project collection url>;
        BuildName=<build name>;
        TeamProject=<team project name>
        [;Platform=<Defaults to "Any CPU">]
        [;Flavor=<Defaults to "Debug">]
        [;RunTitle=<title>]
    ```

  - <span data-ttu-id="59001-130">Sonuçları bir Visual Studio Test Sonuçları dosyasına (TRX) kaydetmek için `trx` günlükçü sağlayıcısını kullanın.</span><span class="sxs-lookup"><span data-stu-id="59001-130">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="59001-131">Bu anahtar, test sonuçları dizininde verilen günlük dosyası adına sahip bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="59001-131">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="59001-132">`LogFileName` Sağlanmazsa, test sonuçlarını tutmak için benzersiz bir dosya adı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="59001-132">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

    ```console
    /logger:trx [;LogFileName=<Defaults to unique file name>]
    ```

- **`--Parallel`**

  <span data-ttu-id="59001-133">Testleri paralel olarak çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="59001-133">Run tests in parallel.</span></span> <span data-ttu-id="59001-134">Varsayılan olarak, makinedeki tüm kullanılabilir çekirdekler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="59001-134">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="59001-135">`MaxCpuCount` *Runsettings* dosyasındaki `RunConfiguration` düğümü altında özelliğini ayarlayarak açık sayıda çekirdek belirtin.</span><span class="sxs-lookup"><span data-stu-id="59001-135">Specify an explicit number of cores by setting the `MaxCpuCount` property under the `RunConfiguration` node in the *runsettings* file.</span></span>

- **`--ParentProcessId <PROCESS_ID>`**

  <span data-ttu-id="59001-136">Geçerli işlemin başlatmasından sorumlu olan üst işlemin işlem KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="59001-136">Process ID of the parent process responsible for launching the current process.</span></span>

- **`--Platform <PLATFORM_TYPE>`**

  <span data-ttu-id="59001-137">Test yürütmesi için kullanılan hedef platform mimarisi.</span><span class="sxs-lookup"><span data-stu-id="59001-137">Target platform architecture used for test execution.</span></span> <span data-ttu-id="59001-138">Geçerli değerler `x86`, `x64`, ve. `ARM`</span><span class="sxs-lookup"><span data-stu-id="59001-138">Valid values are `x86`, `x64`, and `ARM`.</span></span>

- **`--Port <PORT>`**

  <span data-ttu-id="59001-139">Yuva bağlantısı ve olay iletilerini alma bağlantı noktasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="59001-139">Specifies the port for the socket connection and receiving the event messages.</span></span>

- **`--ResultsDirectory:<PATH>`**

  <span data-ttu-id="59001-140">Mevcut değilse, belirtilen yolda test sonuçları dizini oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="59001-140">Test results directory will be created in specified path if not exists.</span></span>

- **`--Settings <SETTINGS_FILE>`**

  <span data-ttu-id="59001-141">Testler çalıştırılırken kullanılacak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="59001-141">Settings to use when running tests.</span></span>

- **`--TestAdapterPath <PATH>`**

  <span data-ttu-id="59001-142">Test çalıştırmasında belirli bir yoldan (varsa) özel test bağdaştırıcıları kullanın.</span><span class="sxs-lookup"><span data-stu-id="59001-142">Use custom test adapters from a given path (if any) in the test run.</span></span>

- **`--TestCaseFilter <EXPRESSION>`**

  <span data-ttu-id="59001-143">Verilen ifadeyle eşleşen testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="59001-143">Run tests that match the given expression.</span></span> <span data-ttu-id="59001-144">`<EXPRESSION>`biçimindedir `<property>Operator<value>[|&<EXPRESSION>]`, burada işleci `=`, `!=`veya `~`' den biridir.</span><span class="sxs-lookup"><span data-stu-id="59001-144">`<EXPRESSION>` is of the format `<property>Operator<value>[|&<EXPRESSION>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="59001-145">İşlecinde `~` ' Contains ' semantiği var ve gibi `DisplayName`dize özellikleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="59001-145">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="59001-146">Parantezler `()` , alt ifadeleri gruplandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="59001-146">Parentheses `()` are used to group subexpressions.</span></span> <span data-ttu-id="59001-147">Daha fazla bilgi için bkz. [TestCase filtresi](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span><span class="sxs-lookup"><span data-stu-id="59001-147">For more information, see [TestCase filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span></span>

- **`--Tests <TEST_NAMES>`**

  <span data-ttu-id="59001-148">Testleri, belirtilen değerlerle eşleşen adlarla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="59001-148">Run tests with names that match the provided values.</span></span> <span data-ttu-id="59001-149">Birden çok değeri virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="59001-149">Separate multiple values with commas.</span></span>

- **`-?|--Help`**

  <span data-ttu-id="59001-150">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="59001-150">Prints out a short help for the command.</span></span>

- **`@<file>`**

  <span data-ttu-id="59001-151">Daha fazla seçenek için yanıt dosyasını okur.</span><span class="sxs-lookup"><span data-stu-id="59001-151">Reads response file for more options.</span></span>

- **`args`**

  <span data-ttu-id="59001-152">Bağdaştırıcıya geçirilecek ek bağımsız değişkenleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="59001-152">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="59001-153">Bağımsız değişkenler, formun `<n>=<v>`ad-değer çiftleri olarak belirtilir, burada `<n>` bağımsız değişken adıdır ve `<v>` bağımsız değişken değeridir.</span><span class="sxs-lookup"><span data-stu-id="59001-153">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="59001-154">Birden çok bağımsız değişkeni ayırmak için boşluk kullanın.</span><span class="sxs-lookup"><span data-stu-id="59001-154">Use a space to separate multiple arguments.</span></span>

## <a name="examples"></a><span data-ttu-id="59001-155">Örnekler</span><span class="sxs-lookup"><span data-stu-id="59001-155">Examples</span></span>

<span data-ttu-id="59001-156">Testleri *MyTestProject. dll*içinde Çalıştır:</span><span class="sxs-lookup"><span data-stu-id="59001-156">Run tests in *mytestproject.dll*:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll
```

<span data-ttu-id="59001-157">Testleri *MyTestProject. dll*içinde çalıştırın, özel adla özel klasöre dışarı aktarma:</span><span class="sxs-lookup"><span data-stu-id="59001-157">Run tests in *mytestproject.dll*, exporting to custom folder with custom name:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path
```

<span data-ttu-id="59001-158">*Testprojem. dll* ve *myothertestproject. exe*' de testleri çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="59001-158">Run tests in *mytestproject.dll* and *myothertestproject.exe*:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll myothertestproject.exe
```

<span data-ttu-id="59001-159">Testleri `TestMethod1` Çalıştır:</span><span class="sxs-lookup"><span data-stu-id="59001-159">Run `TestMethod1` tests:</span></span>

```dotnetcli
dotnet vstest /Tests:TestMethod1
```

<span data-ttu-id="59001-160">Çalıştır `TestMethod1` ve `TestMethod2` testler:</span><span class="sxs-lookup"><span data-stu-id="59001-160">Run `TestMethod1` and `TestMethod2` tests:</span></span>

```dotnetcli
dotnet vstest /Tests:TestMethod1,TestMethod2
```

## <a name="see-also"></a><span data-ttu-id="59001-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59001-161">See also</span></span>

- [<span data-ttu-id="59001-162">VSTest.Console.exe komut satırı seçenekleri</span><span class="sxs-lookup"><span data-stu-id="59001-162">VSTest.Console.exe command-line options</span></span>](/visualstudio/test/vstest-console-options)
