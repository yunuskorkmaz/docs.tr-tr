---
title: dotnet vstest komutu
description: Dotnet vstest komutu bir proje ve tüm bağımlılıklarını oluşturur.
ms.date: 02/27/2020
ms.openlocfilehash: e8fa94cf12ca2fe5fb99c6e3c1dcdb52185798c0
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463279"
---
# <a name="dotnet-vstest"></a><span data-ttu-id="33baa-103">dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="33baa-103">dotnet vstest</span></span>

<span data-ttu-id="33baa-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 2.1 SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="33baa-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="33baa-105">Adı</span><span class="sxs-lookup"><span data-stu-id="33baa-105">Name</span></span>

<span data-ttu-id="33baa-106">`dotnet-vstest`- Belirtilen dosyalardan testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="33baa-106">`dotnet-vstest` - Runs tests from the specified files.</span></span>

## <a name="synopsis"></a><span data-ttu-id="33baa-107">Özet</span><span class="sxs-lookup"><span data-stu-id="33baa-107">Synopsis</span></span>

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

## <a name="description"></a><span data-ttu-id="33baa-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="33baa-108">Description</span></span>

<span data-ttu-id="33baa-109">Komut, `dotnet-vstest` otomatik `VSTest.Console` birim testlerini çalıştırmak için komut satırı uygulamasını çalıştırAr.</span><span class="sxs-lookup"><span data-stu-id="33baa-109">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="33baa-110">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="33baa-110">Arguments</span></span>

- **`TEST_FILE_NAMES`**

  <span data-ttu-id="33baa-111">Belirtilen derlemelerden testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="33baa-111">Run tests from the specified assemblies.</span></span> <span data-ttu-id="33baa-112">Birden çok test derleme adını boşluklarla ayırın.</span><span class="sxs-lookup"><span data-stu-id="33baa-112">Separate multiple test assembly names with spaces.</span></span> <span data-ttu-id="33baa-113">Joker karakterler desteklenir.</span><span class="sxs-lookup"><span data-stu-id="33baa-113">Wildcards are supported.</span></span>

## <a name="options"></a><span data-ttu-id="33baa-114">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="33baa-114">Options</span></span>

- **`--Blame`**

  <span data-ttu-id="33baa-115">Testleri suçlama modunda çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="33baa-115">Runs the tests in blame mode.</span></span> <span data-ttu-id="33baa-116">Bu seçenek, test ana bilgisayar çökmesine neden sorunlu testleri yalıtmak yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="33baa-116">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="33baa-117">Bu, çökmeden önce testlerin yürütülmesi sırasını yakalayan *Sequence.xml* olarak geçerli dizinde bir çıktı dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="33baa-117">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`--Diag <PATH_TO_LOG_FILE>`**

  <span data-ttu-id="33baa-118">Test platformu için ayrıntılı günlükleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="33baa-118">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="33baa-119">Günlükler sağlanan dosyaya yazılır.</span><span class="sxs-lookup"><span data-stu-id="33baa-119">Logs are written to the provided file.</span></span>

- **`--Framework <FRAMEWORK>`**

  <span data-ttu-id="33baa-120">Test yürütmesi için kullanılan Hedef .NET Framework sürümü.</span><span class="sxs-lookup"><span data-stu-id="33baa-120">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="33baa-121">Geçerli değerlere `.NETFramework,Version=v4.6` örnek `.NETCoreApp,Version=v1.0`olarak .</span><span class="sxs-lookup"><span data-stu-id="33baa-121">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="33baa-122">Desteklenen diğer değerler `Framework40` `Framework45`, `FrameworkCore10`, `FrameworkUap10`, ve .</span><span class="sxs-lookup"><span data-stu-id="33baa-122">Other supported values are `Framework40`, `Framework45`, `FrameworkCore10`, and `FrameworkUap10`.</span></span>

- **`--InIsolation`**

  <span data-ttu-id="33baa-123">Testleri yalıtılmış bir işlemle çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="33baa-123">Runs the tests in an isolated process.</span></span> <span data-ttu-id="33baa-124">Bu, *vstest.console.exe* işleminin testlerdeki bir hata da durdurulmasını daha az sağlar, ancak testler daha yavaş çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="33baa-124">This makes *vstest.console.exe* process less likely to be stopped on an error in the tests, but tests may run slower.</span></span>

- **`-lt|--ListTests <FILE_NAME>`**

  <span data-ttu-id="33baa-125">Verilen test kabından keşfedilen tüm testleri listeler.</span><span class="sxs-lookup"><span data-stu-id="33baa-125">Lists all discovered tests from the given test container.</span></span>

- **`--logger <LOGGER_URI/FRIENDLY_NAME>`**

  <span data-ttu-id="33baa-126">Test sonuçları için bir logger belirtin.</span><span class="sxs-lookup"><span data-stu-id="33baa-126">Specify a logger for test results.</span></span>

  - <span data-ttu-id="33baa-127">Test sonuçlarını Team Foundation Server'da `TfsPublisher` yayımlamak için kaydedici sağlayıcıyı kullanın:</span><span class="sxs-lookup"><span data-stu-id="33baa-127">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

    ```console
    /logger:TfsPublisher;
        Collection=<team project collection url>;
        BuildName=<build name>;
        TeamProject=<team project name>
        [;Platform=<Defaults to "Any CPU">]
        [;Flavor=<Defaults to "Debug">]
        [;RunTitle=<title>]
    ```

  - <span data-ttu-id="33baa-128">Sonuçları Visual Studio Test Sonuçları Dosyasına (TRX) kaydetmek için logger sağlayıcısını `trx` kullanın.</span><span class="sxs-lookup"><span data-stu-id="33baa-128">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="33baa-129">Bu anahtar, test sonuçları dizininde verilen günlük dosyası adı içeren bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="33baa-129">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="33baa-130">Sağlanmadıysa, `LogFileName` test sonuçlarını tutmak için benzersiz bir dosya adı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="33baa-130">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

    ```console
    /logger:trx [;LogFileName=<Defaults to unique file name>]
    ```

- **`--Parallel`**

  <span data-ttu-id="33baa-131">Testleri paralel olarak çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="33baa-131">Run tests in parallel.</span></span> <span data-ttu-id="33baa-132">Varsayılan olarak, makinedeki tüm kullanılabilir çekirdekler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="33baa-132">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="33baa-133">Runsettings dosyasındaki `MaxCpuCount` `RunConfiguration` düğümün altındaki özelliği ayarlayarak açık *runsettings* sayıda çekirdek belirtin.</span><span class="sxs-lookup"><span data-stu-id="33baa-133">Specify an explicit number of cores by setting the `MaxCpuCount` property under the `RunConfiguration` node in the *runsettings* file.</span></span>

- **`--ParentProcessId <PROCESS_ID>`**

  <span data-ttu-id="33baa-134">Geçerli işlemin başlatılmasından sorumlu ana işlemin işlem kimliği.</span><span class="sxs-lookup"><span data-stu-id="33baa-134">Process ID of the parent process responsible for launching the current process.</span></span>

- **`--Platform <PLATFORM_TYPE>`**

  <span data-ttu-id="33baa-135">Test yürütme için kullanılan hedef platform mimarisi.</span><span class="sxs-lookup"><span data-stu-id="33baa-135">Target platform architecture used for test execution.</span></span> <span data-ttu-id="33baa-136">Geçerli değerler `x86` `x64`, `ARM`ve .</span><span class="sxs-lookup"><span data-stu-id="33baa-136">Valid values are `x86`, `x64`, and `ARM`.</span></span>

- **`--Port <PORT>`**

  <span data-ttu-id="33baa-137">Soket bağlantısı ve olay iletileri almak için bağlantı noktasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="33baa-137">Specifies the port for the socket connection and receiving the event messages.</span></span>

- **`--ResultsDirectory:<PATH>`**

  <span data-ttu-id="33baa-138">Test sonuçları dizini yoksa belirtilen yolda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="33baa-138">Test results directory will be created in specified path if not exists.</span></span>

- **`--Settings <SETTINGS_FILE>`**

  <span data-ttu-id="33baa-139">Testleri çalıştırırken kullanılacak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="33baa-139">Settings to use when running tests.</span></span>

- **`--TestAdapterPath <PATH>`**

  <span data-ttu-id="33baa-140">Test çalışmasında belirli bir yoldan (varsa) özel test bağdaştırıcıları kullanın.</span><span class="sxs-lookup"><span data-stu-id="33baa-140">Use custom test adapters from a given path (if any) in the test run.</span></span>

- **`--TestCaseFilter <EXPRESSION>`**

  <span data-ttu-id="33baa-141">Verilen ifadeyle eşleşen testler çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="33baa-141">Run tests that match the given expression.</span></span> <span data-ttu-id="33baa-142">`<EXPRESSION>`biçimindedir `<property>Operator<value>[|&<EXPRESSION>]`, Operatör biri olduğu `=` `!=`, `~`, veya .</span><span class="sxs-lookup"><span data-stu-id="33baa-142">`<EXPRESSION>` is of the format `<property>Operator<value>[|&<EXPRESSION>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="33baa-143">İşleç `~` 'içerir' semantik ve gibi `DisplayName`dize özellikleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="33baa-143">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="33baa-144">Alt ifadeleri `()` gruplandırmak için parantezler kullanılır.</span><span class="sxs-lookup"><span data-stu-id="33baa-144">Parentheses `()` are used to group subexpressions.</span></span> <span data-ttu-id="33baa-145">Daha fazla bilgi için [TestCase filtresine](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="33baa-145">For more information, see [TestCase filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span></span>

- **`--Tests <TEST_NAMES>`**

  <span data-ttu-id="33baa-146">Sağlanan değerlerle eşleşen adlarla testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="33baa-146">Run tests with names that match the provided values.</span></span> <span data-ttu-id="33baa-147">Birden çok değeri virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="33baa-147">Separate multiple values with commas.</span></span>

- **`-?|--Help`**

  <span data-ttu-id="33baa-148">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="33baa-148">Prints out a short help for the command.</span></span>

- **`@<file>`**

  <span data-ttu-id="33baa-149">Daha fazla seçenek için yanıt dosyalarını okur.</span><span class="sxs-lookup"><span data-stu-id="33baa-149">Reads response file for more options.</span></span>

- **`args`**

  <span data-ttu-id="33baa-150">Bağdaştırıcıya geçmek için fazladan bağımsız değişkenler belirtir.</span><span class="sxs-lookup"><span data-stu-id="33baa-150">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="33baa-151">Bağımsız değişkenler formun `<n>=<v>`ad değeri çiftleri `<n>` olarak belirtilir, `<v>` bağımsız değişken adı ve bağımsız değişken değeridir.</span><span class="sxs-lookup"><span data-stu-id="33baa-151">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="33baa-152">Birden çok bağımsız değişkeni ayırmak için bir boşluk kullanın.</span><span class="sxs-lookup"><span data-stu-id="33baa-152">Use a space to separate multiple arguments.</span></span>

## <a name="examples"></a><span data-ttu-id="33baa-153">Örnekler</span><span class="sxs-lookup"><span data-stu-id="33baa-153">Examples</span></span>

<span data-ttu-id="33baa-154">*mytestproject.dll*testleri çalıştırın :</span><span class="sxs-lookup"><span data-stu-id="33baa-154">Run tests in *mytestproject.dll*:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll
```

<span data-ttu-id="33baa-155">*Mytestproject.dll'de*testleri çalıştırın, özel adla özel klasöre dışa aktarın:</span><span class="sxs-lookup"><span data-stu-id="33baa-155">Run tests in *mytestproject.dll*, exporting to custom folder with custom name:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path
```

<span data-ttu-id="33baa-156">*mytestproject.dll* ve *myothertestproject.exe*testleri çalıştırın :</span><span class="sxs-lookup"><span data-stu-id="33baa-156">Run tests in *mytestproject.dll* and *myothertestproject.exe*:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll myothertestproject.exe
```

<span data-ttu-id="33baa-157">Testleri `TestMethod1` çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="33baa-157">Run `TestMethod1` tests:</span></span>

```dotnetcli
dotnet vstest /Tests:TestMethod1
```

<span data-ttu-id="33baa-158">Çalıştır `TestMethod1` `TestMethod2` ve testler:</span><span class="sxs-lookup"><span data-stu-id="33baa-158">Run `TestMethod1` and `TestMethod2` tests:</span></span>

```dotnetcli
dotnet vstest /Tests:TestMethod1,TestMethod2
```

## <a name="see-also"></a><span data-ttu-id="33baa-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="33baa-159">See also</span></span>

- [<span data-ttu-id="33baa-160">VSTest.Console.exe komut satırı seçenekleri</span><span class="sxs-lookup"><span data-stu-id="33baa-160">VSTest.Console.exe command-line options</span></span>](/visualstudio/test/vstest-console-options)
