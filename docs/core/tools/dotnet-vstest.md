---
title: DotNet VSTest komutu
description: DotNet VSTest komutu bir proje ve tüm bağımlılıklarını oluşturur.
ms.date: 05/30/2018
ms.openlocfilehash: 3fdb5443d6d0cfbe1e7e88bc824cbb930f211260
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451187"
---
# <a name="dotnet-vstest"></a><span data-ttu-id="94d88-103">dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="94d88-103">dotnet vstest</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="94d88-104">Name</span><span class="sxs-lookup"><span data-stu-id="94d88-104">Name</span></span>

<span data-ttu-id="94d88-105">`dotnet-vstest`, belirtilen dosyalardan testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="94d88-105">`dotnet-vstest` - Runs tests from the specified files.</span></span>

## <a name="synopsis"></a><span data-ttu-id="94d88-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="94d88-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21"></a>[<span data-ttu-id="94d88-107">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="94d88-107">.NET Core 2.1</span></span>](#tab/netcore21)

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [--Blame|/Blame] [--InIsolation|/InIsolation]
    [[--] <args>...]] [-?|--Help|/?|/Help]
```

# <a name="net-core-20"></a>[<span data-ttu-id="94d88-108">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="94d88-108">.NET Core 2.0</span></span>](#tab/netcore20)

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath] 
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```

# <a name="net-core-1x"></a>[<span data-ttu-id="94d88-109">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="94d88-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger] 
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```

---

## <a name="description"></a><span data-ttu-id="94d88-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="94d88-110">Description</span></span>

<span data-ttu-id="94d88-111">`dotnet-vstest` komutu, otomatik birim testlerini çalıştırmak için `VSTest.Console` komut satırı uygulamasını çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="94d88-111">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="94d88-112">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="94d88-112">Arguments</span></span>

`TEST_FILE_NAMES`

<span data-ttu-id="94d88-113">Belirtilen derlemelerdeki testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="94d88-113">Run tests from the specified assemblies.</span></span> <span data-ttu-id="94d88-114">Birden çok test derleme adını boşluklarla ayırın.</span><span class="sxs-lookup"><span data-stu-id="94d88-114">Separate multiple test assembly names with spaces.</span></span>

## <a name="options"></a><span data-ttu-id="94d88-115">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="94d88-115">Options</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="94d88-116">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="94d88-116">.NET Core 2.1</span></span>](#tab/netcore21)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="94d88-117">Testler çalıştırılırken kullanılacak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="94d88-117">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="94d88-118">Testleri, belirtilen değerlerle eşleşen adlarla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="94d88-118">Run tests with names that match the provided values.</span></span> <span data-ttu-id="94d88-119">Birden çok değeri virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="94d88-119">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="94d88-120">Test çalıştırmasında belirli bir yoldan (varsa) özel test bağdaştırıcıları kullanın.</span><span class="sxs-lookup"><span data-stu-id="94d88-120">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="94d88-121">Test yürütmesi için kullanılan hedef platform mimarisi.</span><span class="sxs-lookup"><span data-stu-id="94d88-121">Target platform architecture used for test execution.</span></span> <span data-ttu-id="94d88-122">Geçerli değerler `x86`, `x64`ve `ARM`.</span><span class="sxs-lookup"><span data-stu-id="94d88-122">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="94d88-123">Test yürütmesi için kullanılan hedef .NET Framework sürümü.</span><span class="sxs-lookup"><span data-stu-id="94d88-123">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="94d88-124">Geçerli değer örnekleri `.NETFramework,Version=v4.6` veya `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="94d88-124">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="94d88-125">Desteklenen diğer değerler `Framework40`, `Framework45`, `FrameworkCore10`ve `FrameworkUap10`.</span><span class="sxs-lookup"><span data-stu-id="94d88-125">Other supported values are `Framework40`, `Framework45`, `FrameworkCore10`, and `FrameworkUap10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="94d88-126">Testleri paralel olarak yürütün.</span><span class="sxs-lookup"><span data-stu-id="94d88-126">Execute tests in parallel.</span></span> <span data-ttu-id="94d88-127">Varsayılan olarak, makinedeki tüm kullanılabilir çekirdekler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="94d88-127">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="94d88-128">Runsettings dosyasındaki RunConfiguration düğümü altında MaxCpuCount özelliğini ayarlayarak açık sayıda çekirdek belirtin.</span><span class="sxs-lookup"><span data-stu-id="94d88-128">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="94d88-129">Verilen ifadeyle eşleşen testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="94d88-129">Run tests that match the given expression.</span></span> <span data-ttu-id="94d88-130">`<Expression>` biçim `<property>Operator<value>[|&<Expression>]`, burada Işleç `=`, `!=`veya `~`biridir.</span><span class="sxs-lookup"><span data-stu-id="94d88-130">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="94d88-131">İşleç `~` ' Contains ' semantiğine sahiptir ve `DisplayName`gibi dize özellikleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="94d88-131">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="94d88-132">Parantez `()` alt ifadeleri gruplandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="94d88-132">Parenthesis `()` are used to group subexpressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="94d88-133">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="94d88-133">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="94d88-134">Test sonuçları için bir günlükçü belirtin.</span><span class="sxs-lookup"><span data-stu-id="94d88-134">Specify a logger for test results.</span></span>

* <span data-ttu-id="94d88-135">Test sonuçlarını Team Foundation Server yayımlamak için `TfsPublisher` günlükçü sağlayıcısını kullanın:</span><span class="sxs-lookup"><span data-stu-id="94d88-135">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```console
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="94d88-136">Sonuçları bir Visual Studio Test Sonuçları dosyasına (TRX) kaydetmek için `trx` günlükçü sağlayıcısını kullanın.</span><span class="sxs-lookup"><span data-stu-id="94d88-136">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="94d88-137">Bu anahtar, test sonuçları dizininde verilen günlük dosyası adına sahip bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="94d88-137">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="94d88-138">`LogFileName` sağlanmazsa, test sonuçlarını tutmak için benzersiz bir dosya adı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="94d88-138">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```console
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="94d88-139">Verilen test kapsayıcısından tüm bulunan testleri listeler.</span><span class="sxs-lookup"><span data-stu-id="94d88-139">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="94d88-140">Geçerli işlemin başlatmasından sorumlu olan üst işlemin işlem KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="94d88-140">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="94d88-141">Yuva bağlantısı ve olay iletilerini alma bağlantı noktasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="94d88-141">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="94d88-142">Test platformu için ayrıntılı günlükleri etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="94d88-142">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="94d88-143">Günlükler, belirtilen dosyaya yazılır.</span><span class="sxs-lookup"><span data-stu-id="94d88-143">Logs are written to the provided file.</span></span>

`--Blame|/Blame`

<span data-ttu-id="94d88-144">Testleri sorumluyu modunda çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="94d88-144">Runs the tests in blame mode.</span></span> <span data-ttu-id="94d88-145">Bu seçenek, test ana bilgisayarının kilitlenmesine neden olan sorunlu testleri yalıtmak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="94d88-145">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="94d88-146">Geçerli dizinde, kilitlenmeden önce yürütülen testlerin sırasını yakalayan *Sequence. xml* olarak bir çıktı dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="94d88-146">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`--InIsolation|/InIsolation`

<span data-ttu-id="94d88-147">Testleri yalıtılmış bir işlemde çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="94d88-147">Runs the tests in an isolated process.</span></span> <span data-ttu-id="94d88-148">Bu, *VSTest. Console. exe* işleminin testlerin bir hata üzerinde durdurulması olasılığını azaltır, ancak testler daha yavaş çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="94d88-148">This makes *vstest.console.exe* process less likely to be stopped on an error in the tests, but tests may run slower.</span></span>

`@<file>`

<span data-ttu-id="94d88-149">Daha fazla seçenek için yanıt dosyasını okur.</span><span class="sxs-lookup"><span data-stu-id="94d88-149">Reads response file for more options.</span></span>

`args`

<span data-ttu-id="94d88-150">Bağdaştırıcıya geçirilecek ek bağımsız değişkenleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="94d88-150">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="94d88-151">Bağımsız değişkenler `<n>=<v>`biçim-değer çiftleri olarak belirtilir; burada `<n>` bağımsız değişken adıdır ve `<v>` bağımsız değişken değeridir.</span><span class="sxs-lookup"><span data-stu-id="94d88-151">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="94d88-152">Birden çok bağımsız değişkeni ayırmak için boşluk kullanın.</span><span class="sxs-lookup"><span data-stu-id="94d88-152">Use a space to separate multiple arguments.</span></span>

# <a name="net-core-20"></a>[<span data-ttu-id="94d88-153">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="94d88-153">.NET Core 2.0</span></span>](#tab/netcore20)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="94d88-154">Testler çalıştırılırken kullanılacak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="94d88-154">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="94d88-155">Testleri, belirtilen değerlerle eşleşen adlarla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="94d88-155">Run tests with names that match the provided values.</span></span> <span data-ttu-id="94d88-156">Birden çok değeri virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="94d88-156">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="94d88-157">Test çalıştırmasında belirli bir yoldan (varsa) özel test bağdaştırıcıları kullanın.</span><span class="sxs-lookup"><span data-stu-id="94d88-157">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="94d88-158">Test yürütmesi için kullanılan hedef platform mimarisi.</span><span class="sxs-lookup"><span data-stu-id="94d88-158">Target platform architecture used for test execution.</span></span> <span data-ttu-id="94d88-159">Geçerli değerler `x86`, `x64`ve `ARM`.</span><span class="sxs-lookup"><span data-stu-id="94d88-159">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="94d88-160">Test yürütmesi için kullanılan hedef .NET Framework sürümü.</span><span class="sxs-lookup"><span data-stu-id="94d88-160">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="94d88-161">Geçerli değer örnekleri `.NETFramework,Version=v4.6` veya `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="94d88-161">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="94d88-162">Desteklenen diğer değerler `Framework40`, `Framework45`ve `FrameworkCore10`.</span><span class="sxs-lookup"><span data-stu-id="94d88-162">Other supported values are `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="94d88-163">Testleri paralel olarak yürütün.</span><span class="sxs-lookup"><span data-stu-id="94d88-163">Execute tests in parallel.</span></span> <span data-ttu-id="94d88-164">Varsayılan olarak, makinedeki tüm kullanılabilir çekirdekler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="94d88-164">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="94d88-165">Runsettings dosyasındaki RunConfiguration düğümü altında MaxCpuCount özelliğini ayarlayarak açık sayıda çekirdek belirtin.</span><span class="sxs-lookup"><span data-stu-id="94d88-165">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="94d88-166">Verilen ifadeyle eşleşen testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="94d88-166">Run tests that match the given expression.</span></span> <span data-ttu-id="94d88-167">`<Expression>` biçim `<property>Operator<value>[|&<Expression>]`, burada Işleç `=`, `!=`veya `~`biridir.</span><span class="sxs-lookup"><span data-stu-id="94d88-167">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="94d88-168">İşleç `~` ' Contains ' semantiğine sahiptir ve `DisplayName`gibi dize özellikleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="94d88-168">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="94d88-169">Parantez `()` alt ifadeleri gruplandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="94d88-169">Parenthesis `()` are used to group subexpressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="94d88-170">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="94d88-170">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="94d88-171">Test sonuçları için bir günlükçü belirtin.</span><span class="sxs-lookup"><span data-stu-id="94d88-171">Specify a logger for test results.</span></span>

* <span data-ttu-id="94d88-172">Test sonuçlarını Team Foundation Server yayımlamak için `TfsPublisher` günlükçü sağlayıcısını kullanın:</span><span class="sxs-lookup"><span data-stu-id="94d88-172">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```console
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="94d88-173">Sonuçları bir Visual Studio Test Sonuçları dosyasına (TRX) kaydetmek için `trx` günlükçü sağlayıcısını kullanın.</span><span class="sxs-lookup"><span data-stu-id="94d88-173">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="94d88-174">Bu anahtar, test sonuçları dizininde verilen günlük dosyası adına sahip bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="94d88-174">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="94d88-175">`LogFileName` sağlanmazsa, test sonuçlarını tutmak için benzersiz bir dosya adı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="94d88-175">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```console
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="94d88-176">Verilen test kapsayıcısından tüm bulunan testleri listeler.</span><span class="sxs-lookup"><span data-stu-id="94d88-176">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="94d88-177">Geçerli işlemin başlatmasından sorumlu olan üst işlemin işlem KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="94d88-177">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="94d88-178">Yuva bağlantısı ve olay iletilerini alma bağlantı noktasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="94d88-178">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="94d88-179">Test platformu için ayrıntılı günlükleri etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="94d88-179">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="94d88-180">Günlükler, belirtilen dosyaya yazılır.</span><span class="sxs-lookup"><span data-stu-id="94d88-180">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="94d88-181">Bağdaştırıcıya geçirilecek ek bağımsız değişkenleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="94d88-181">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="94d88-182">Bağımsız değişkenler `<n>=<v>`biçim-değer çiftleri olarak belirtilir; burada `<n>` bağımsız değişken adıdır ve `<v>` bağımsız değişken değeridir.</span><span class="sxs-lookup"><span data-stu-id="94d88-182">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="94d88-183">Birden çok bağımsız değişkeni ayırmak için boşluk kullanın.</span><span class="sxs-lookup"><span data-stu-id="94d88-183">Use a space to separate multiple arguments.</span></span>

# <a name="net-core-1x"></a>[<span data-ttu-id="94d88-184">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="94d88-184">.NET Core 1.x</span></span>](#tab/netcore1x)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="94d88-185">Testler çalıştırılırken kullanılacak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="94d88-185">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="94d88-186">Testleri, belirtilen değerlerle eşleşen adlarla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="94d88-186">Run tests with names that match the provided values.</span></span> <span data-ttu-id="94d88-187">Birden çok değeri virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="94d88-187">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="94d88-188">Test çalıştırmasında belirli bir yoldan (varsa) özel test bağdaştırıcıları kullanın.</span><span class="sxs-lookup"><span data-stu-id="94d88-188">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="94d88-189">Test yürütmesi için kullanılan hedef platform mimarisi.</span><span class="sxs-lookup"><span data-stu-id="94d88-189">Target platform architecture used for test execution.</span></span> <span data-ttu-id="94d88-190">Geçerli değerler `x86`, `x64`ve `ARM`.</span><span class="sxs-lookup"><span data-stu-id="94d88-190">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="94d88-191">Test yürütmesi için kullanılan hedef .NET Framework sürümü.</span><span class="sxs-lookup"><span data-stu-id="94d88-191">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="94d88-192">Geçerli değer örnekleri `.NETFramework,Version=v4.6` veya `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="94d88-192">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="94d88-193">Desteklenen diğer değerler `Framework40`, `Framework45`ve `FrameworkCore10`.</span><span class="sxs-lookup"><span data-stu-id="94d88-193">Other supported values are `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="94d88-194">Testleri paralel olarak yürütün.</span><span class="sxs-lookup"><span data-stu-id="94d88-194">Execute tests in parallel.</span></span> <span data-ttu-id="94d88-195">Varsayılan olarak, makinedeki tüm kullanılabilir çekirdekler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="94d88-195">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="94d88-196">Runsettings dosyasındaki RunConfiguration düğümü altında MaxCpuCount özelliğini ayarlayarak açık sayıda çekirdek belirtin.</span><span class="sxs-lookup"><span data-stu-id="94d88-196">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="94d88-197">Verilen ifadeyle eşleşen testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="94d88-197">Run tests that match the given expression.</span></span> <span data-ttu-id="94d88-198">`<Expression>` biçim `<property>Operator<value>[|&<Expression>]`, burada Işleç `=`, `!=`veya `~`biridir.</span><span class="sxs-lookup"><span data-stu-id="94d88-198">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="94d88-199">İşleç `~` ' Contains ' semantiğine sahiptir ve `DisplayName`gibi dize özellikleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="94d88-199">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="94d88-200">Parantez `()` alt ifadeleri gruplandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="94d88-200">Parenthesis `()` are used to group subexpressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="94d88-201">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="94d88-201">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="94d88-202">Test sonuçları için bir günlükçü belirtin.</span><span class="sxs-lookup"><span data-stu-id="94d88-202">Specify a logger for test results.</span></span>

* <span data-ttu-id="94d88-203">Test sonuçlarını Team Foundation Server yayımlamak için `TfsPublisher` günlükçü sağlayıcısını kullanın:</span><span class="sxs-lookup"><span data-stu-id="94d88-203">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```console
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="94d88-204">Sonuçları bir Visual Studio Test Sonuçları dosyasına (TRX) kaydetmek için `trx` günlükçü sağlayıcısını kullanın.</span><span class="sxs-lookup"><span data-stu-id="94d88-204">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="94d88-205">Bu anahtar, test sonuçları dizininde verilen günlük dosyası adına sahip bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="94d88-205">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="94d88-206">`LogFileName` sağlanmazsa, test sonuçlarını tutmak için benzersiz bir dosya adı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="94d88-206">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```console
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="94d88-207">Verilen test kapsayıcısından tüm bulunan testleri listeler.</span><span class="sxs-lookup"><span data-stu-id="94d88-207">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="94d88-208">Geçerli işlemin başlatmasından sorumlu olan üst işlemin işlem KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="94d88-208">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="94d88-209">Yuva bağlantısı ve olay iletilerini alma bağlantı noktasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="94d88-209">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="94d88-210">Test platformu için ayrıntılı günlükleri etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="94d88-210">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="94d88-211">Günlükler, belirtilen dosyaya yazılır.</span><span class="sxs-lookup"><span data-stu-id="94d88-211">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="94d88-212">Bağdaştırıcıya geçirilecek ek bağımsız değişkenleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="94d88-212">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="94d88-213">Bağımsız değişkenler `<n>=<v>`biçim-değer çiftleri olarak belirtilir; burada `<n>` bağımsız değişken adıdır ve `<v>` bağımsız değişken değeridir.</span><span class="sxs-lookup"><span data-stu-id="94d88-213">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="94d88-214">Birden çok bağımsız değişkeni ayırmak için boşluk kullanın.</span><span class="sxs-lookup"><span data-stu-id="94d88-214">Use a space to separate multiple arguments.</span></span>

---

## <a name="examples"></a><span data-ttu-id="94d88-215">Örnekler</span><span class="sxs-lookup"><span data-stu-id="94d88-215">Examples</span></span>

<span data-ttu-id="94d88-216">`mytestproject.dll`Testleri Çalıştır:</span><span class="sxs-lookup"><span data-stu-id="94d88-216">Run tests in `mytestproject.dll`:</span></span>

`dotnet vstest mytestproject.dll`

<span data-ttu-id="94d88-217">Testleri `mytestproject.dll`' de Çalıştır, özel bir klasöre dışarı aktarma özel adı:</span><span class="sxs-lookup"><span data-stu-id="94d88-217">Run tests in `mytestproject.dll`, exporting to custom folder with custom name:</span></span>

`dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path`

<span data-ttu-id="94d88-218">`mytestproject.dll` ve `myothertestproject.exe`testleri çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="94d88-218">Run tests in `mytestproject.dll` and `myothertestproject.exe`:</span></span>

`dotnet vstest mytestproject.dll myothertestproject.exe`

<span data-ttu-id="94d88-219">`TestMethod1` testlerini Çalıştır:</span><span class="sxs-lookup"><span data-stu-id="94d88-219">Run `TestMethod1` tests:</span></span>

`dotnet vstest /Tests:TestMethod1`

<span data-ttu-id="94d88-220">`TestMethod1` Çalıştır ve Testleri `TestMethod2`:</span><span class="sxs-lookup"><span data-stu-id="94d88-220">Run `TestMethod1` and `TestMethod2` tests:</span></span>

`dotnet vstest /Tests:TestMethod1,TestMethod2`
