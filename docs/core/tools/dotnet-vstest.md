---
title: dotnet vstest komutu
description: Dotnet vstest komutu bir proje ve tüm bağımlılıklarını oluşturur.
ms.date: 02/27/2020
ms.openlocfilehash: 88e5b6a8966d78d0746f9ea5ccbccab142a2e0f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156939"
---
# <a name="dotnet-vstest"></a><span data-ttu-id="59dae-103">dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="59dae-103">dotnet vstest</span></span>

<span data-ttu-id="59dae-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 2.1 SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="59dae-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="59dae-105">Adı</span><span class="sxs-lookup"><span data-stu-id="59dae-105">Name</span></span>

<span data-ttu-id="59dae-106">`dotnet-vstest`- Belirtilen dosyalardan testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="59dae-106">`dotnet-vstest` - Runs tests from the specified files.</span></span>

## <a name="synopsis"></a><span data-ttu-id="59dae-107">Özet</span><span class="sxs-lookup"><span data-stu-id="59dae-107">Synopsis</span></span>

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings] [--Tests]
    [--TestAdapterPath] [--Platform] [--Framework] [--Parallel]
    [--TestCaseFilter] [--logger] [-lt|--ListTests]
    [--ParentProcessId] [--Port] [--Diag] [--Blame]
    [--InIsolation] [[--] <args>...]] [-?|--Help]
```

## <a name="description"></a><span data-ttu-id="59dae-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="59dae-108">Description</span></span>

<span data-ttu-id="59dae-109">Komut, `dotnet-vstest` otomatik `VSTest.Console` birim testlerini çalıştırmak için komut satırı uygulamasını çalıştırAr.</span><span class="sxs-lookup"><span data-stu-id="59dae-109">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="59dae-110">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="59dae-110">Arguments</span></span>

- **`TEST_FILE_NAMES`**

  <span data-ttu-id="59dae-111">Belirtilen derlemelerden testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="59dae-111">Run tests from the specified assemblies.</span></span> <span data-ttu-id="59dae-112">Birden çok test derleme adını boşluklarla ayırın.</span><span class="sxs-lookup"><span data-stu-id="59dae-112">Separate multiple test assembly names with spaces.</span></span> <span data-ttu-id="59dae-113">Joker karakterler desteklenir.</span><span class="sxs-lookup"><span data-stu-id="59dae-113">Wildcards are supported.</span></span>

## <a name="options"></a><span data-ttu-id="59dae-114">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="59dae-114">Options</span></span>

- **`--Settings <Settings File>`**

  <span data-ttu-id="59dae-115">Testleri çalıştırırken kullanılacak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="59dae-115">Settings to use when running tests.</span></span>

- **`--Tests <Test Names>`**

  <span data-ttu-id="59dae-116">Sağlanan değerlerle eşleşen adlarla testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="59dae-116">Run tests with names that match the provided values.</span></span> <span data-ttu-id="59dae-117">Birden çok değeri virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="59dae-117">Separate multiple values with commas.</span></span>

- **`--TestAdapterPath`**

  <span data-ttu-id="59dae-118">Test çalışmasında belirli bir yoldan (varsa) özel test bağdaştırıcıları kullanın.</span><span class="sxs-lookup"><span data-stu-id="59dae-118">Use custom test adapters from a given path (if any) in the test run.</span></span>

- **`--Platform <Platform type>`**

  <span data-ttu-id="59dae-119">Test yürütme için kullanılan hedef platform mimarisi.</span><span class="sxs-lookup"><span data-stu-id="59dae-119">Target platform architecture used for test execution.</span></span> <span data-ttu-id="59dae-120">Geçerli değerler `x86` `x64`, `ARM`ve .</span><span class="sxs-lookup"><span data-stu-id="59dae-120">Valid values are `x86`, `x64`, and `ARM`.</span></span>

- **`--Framework <Framework Version>`**

  <span data-ttu-id="59dae-121">Test yürütmesi için kullanılan Hedef .NET Framework sürümü.</span><span class="sxs-lookup"><span data-stu-id="59dae-121">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="59dae-122">Geçerli değerlere `.NETFramework,Version=v4.6` örnek `.NETCoreApp,Version=v1.0`olarak .</span><span class="sxs-lookup"><span data-stu-id="59dae-122">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="59dae-123">Desteklenen diğer değerler `Framework40` `Framework45`, `FrameworkCore10`, `FrameworkUap10`, ve .</span><span class="sxs-lookup"><span data-stu-id="59dae-123">Other supported values are `Framework40`, `Framework45`, `FrameworkCore10`, and `FrameworkUap10`.</span></span>

- **`--Parallel`**

  <span data-ttu-id="59dae-124">Testleri paralel olarak çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="59dae-124">Run tests in parallel.</span></span> <span data-ttu-id="59dae-125">Varsayılan olarak, makinedeki tüm kullanılabilir çekirdekler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="59dae-125">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="59dae-126">Runsettings dosyasındaki `MaxCpuCount` `RunConfiguration` düğümün altındaki özelliği ayarlayarak açık *runsettings* sayıda çekirdek belirtin.</span><span class="sxs-lookup"><span data-stu-id="59dae-126">Specify an explicit number of cores by setting the `MaxCpuCount` property under the `RunConfiguration` node in the *runsettings* file.</span></span>

- **`--TestCaseFilter <Expression>`**

  <span data-ttu-id="59dae-127">Verilen ifadeyle eşleşen testler çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="59dae-127">Run tests that match the given expression.</span></span> <span data-ttu-id="59dae-128">`<Expression>`biçimindedir `<property>Operator<value>[|&<Expression>]`, Operatör biri olduğu `=` `!=`, `~`, veya .</span><span class="sxs-lookup"><span data-stu-id="59dae-128">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="59dae-129">İşleç `~` 'içerir' semantik ve gibi `DisplayName`dize özellikleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="59dae-129">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="59dae-130">`()` Alt ifadeleri gruplandırmak için parantez kullanılır.</span><span class="sxs-lookup"><span data-stu-id="59dae-130">Parenthesis `()` are used to group subexpressions.</span></span>

- **`-?|--Help`**

  <span data-ttu-id="59dae-131">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="59dae-131">Prints out a short help for the command.</span></span>

- **`--logger <Logger Uri/FriendlyName>`**

  <span data-ttu-id="59dae-132">Test sonuçları için bir logger belirtin.</span><span class="sxs-lookup"><span data-stu-id="59dae-132">Specify a logger for test results.</span></span>

  - <span data-ttu-id="59dae-133">Test sonuçlarını Team Foundation Server'da `TfsPublisher` yayımlamak için kaydedici sağlayıcıyı kullanın:</span><span class="sxs-lookup"><span data-stu-id="59dae-133">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

    ```console
    /logger:TfsPublisher;
        Collection=<team project collection url>;
        BuildName=<build name>;
        TeamProject=<team project name>
        [;Platform=<Defaults to "Any CPU">]
        [;Flavor=<Defaults to "Debug">]
        [;RunTitle=<title>]
    ```

  - <span data-ttu-id="59dae-134">Sonuçları Visual Studio Test Sonuçları Dosyasına (TRX) kaydetmek için logger sağlayıcısını `trx` kullanın.</span><span class="sxs-lookup"><span data-stu-id="59dae-134">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="59dae-135">Bu anahtar, test sonuçları dizininde verilen günlük dosyası adı içeren bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="59dae-135">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="59dae-136">Sağlanmadıysa, `LogFileName` test sonuçlarını tutmak için benzersiz bir dosya adı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="59dae-136">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

    ```console
    /logger:trx [;LogFileName=<Defaults to unique file name>]
    ```

- **`-lt|--ListTests <File Name>`**

  <span data-ttu-id="59dae-137">Verilen test kabından keşfedilen tüm testleri listeler.</span><span class="sxs-lookup"><span data-stu-id="59dae-137">Lists all discovered tests from the given test container.</span></span>

- **`--ParentProcessId <ParentProcessId>`**

  <span data-ttu-id="59dae-138">Geçerli işlemin başlatılmasından sorumlu ana işlemin işlem kimliği.</span><span class="sxs-lookup"><span data-stu-id="59dae-138">Process ID of the parent process responsible for launching the current process.</span></span>

- **`--Port <Port>`**

  <span data-ttu-id="59dae-139">Soket bağlantısı ve olay iletileri almak için bağlantı noktasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="59dae-139">Specifies the port for the socket connection and receiving the event messages.</span></span>

- **`--Diag <Path to log file>`**

  <span data-ttu-id="59dae-140">Test platformu için ayrıntılı günlükleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="59dae-140">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="59dae-141">Günlükler sağlanan dosyaya yazılır.</span><span class="sxs-lookup"><span data-stu-id="59dae-141">Logs are written to the provided file.</span></span>

- **`--Blame`**

  <span data-ttu-id="59dae-142">Testleri suçlama modunda çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="59dae-142">Runs the tests in blame mode.</span></span> <span data-ttu-id="59dae-143">Bu seçenek, test ana bilgisayar çökmesine neden sorunlu testleri yalıtmak yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="59dae-143">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="59dae-144">Bu, çökmeden önce testlerin yürütülmesi sırasını yakalayan *Sequence.xml* olarak geçerli dizinde bir çıktı dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="59dae-144">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`--InIsolation`**

  <span data-ttu-id="59dae-145">Testleri yalıtılmış bir işlemle çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="59dae-145">Runs the tests in an isolated process.</span></span> <span data-ttu-id="59dae-146">Bu, *vstest.console.exe* işleminin testlerdeki bir hata da durdurulmasını daha az sağlar, ancak testler daha yavaş çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="59dae-146">This makes *vstest.console.exe* process less likely to be stopped on an error in the tests, but tests may run slower.</span></span>

- **`@<file>`**

  <span data-ttu-id="59dae-147">Daha fazla seçenek için yanıt dosyalarını okur.</span><span class="sxs-lookup"><span data-stu-id="59dae-147">Reads response file for more options.</span></span>

- **`args`**

  <span data-ttu-id="59dae-148">Bağdaştırıcıya geçmek için fazladan bağımsız değişkenler belirtir.</span><span class="sxs-lookup"><span data-stu-id="59dae-148">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="59dae-149">Bağımsız değişkenler formun `<n>=<v>`ad değeri çiftleri `<n>` olarak belirtilir, `<v>` bağımsız değişken adı ve bağımsız değişken değeridir.</span><span class="sxs-lookup"><span data-stu-id="59dae-149">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="59dae-150">Birden çok bağımsız değişkeni ayırmak için bir boşluk kullanın.</span><span class="sxs-lookup"><span data-stu-id="59dae-150">Use a space to separate multiple arguments.</span></span>

## <a name="examples"></a><span data-ttu-id="59dae-151">Örnekler</span><span class="sxs-lookup"><span data-stu-id="59dae-151">Examples</span></span>

<span data-ttu-id="59dae-152">*mytestproject.dll*testleri çalıştırın :</span><span class="sxs-lookup"><span data-stu-id="59dae-152">Run tests in *mytestproject.dll*:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll
```

<span data-ttu-id="59dae-153">*Mytestproject.dll'de*testleri çalıştırın, özel adla özel klasöre dışa aktarın:</span><span class="sxs-lookup"><span data-stu-id="59dae-153">Run tests in *mytestproject.dll*, exporting to custom folder with custom name:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path
```

<span data-ttu-id="59dae-154">*mytestproject.dll* ve *myothertestproject.exe*testleri çalıştırın :</span><span class="sxs-lookup"><span data-stu-id="59dae-154">Run tests in *mytestproject.dll* and *myothertestproject.exe*:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll myothertestproject.exe
```

<span data-ttu-id="59dae-155">Testleri `TestMethod1` çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="59dae-155">Run `TestMethod1` tests:</span></span>

```dotnetcli
dotnet vstest /Tests:TestMethod1
```

<span data-ttu-id="59dae-156">Çalıştır `TestMethod1` `TestMethod2` ve testler:</span><span class="sxs-lookup"><span data-stu-id="59dae-156">Run `TestMethod1` and `TestMethod2` tests:</span></span>

```dotnetcli
dotnet vstest /Tests:TestMethod1,TestMethod2
```
