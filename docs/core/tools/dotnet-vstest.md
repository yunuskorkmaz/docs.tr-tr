---
title: DotNet VSTest komutu
description: DotNet VSTest komutu bir proje ve tüm bağımlılıklarını oluşturur.
ms.date: 05/30/2018
ms.openlocfilehash: c3838617ed539cf56f2840b826e9de58833820fd
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215306"
---
# <a name="dotnet-vstest"></a><span data-ttu-id="efe3c-103">dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="efe3c-103">dotnet vstest</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="efe3c-104">Ad</span><span class="sxs-lookup"><span data-stu-id="efe3c-104">Name</span></span>

<span data-ttu-id="efe3c-105">`dotnet-vstest`, belirtilen dosyalardan testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="efe3c-105">`dotnet-vstest` - Runs tests from the specified files.</span></span>

## <a name="synopsis"></a><span data-ttu-id="efe3c-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="efe3c-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="efe3c-107">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="efe3c-107">.NET Core 2.1</span></span>](#tab/netcore21)

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [--Blame|/Blame] [--InIsolation|/InIsolation]
    [[--] <args>...]] [-?|--Help|/?|/Help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="efe3c-108">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="efe3c-108">.NET Core 2.0</span></span>](#tab/netcore20)

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath] 
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="efe3c-109">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="efe3c-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger] 
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```

---

## <a name="description"></a><span data-ttu-id="efe3c-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="efe3c-110">Description</span></span>

<span data-ttu-id="efe3c-111">`dotnet-vstest` komutu, otomatik birim testlerini çalıştırmak için `VSTest.Console` komut satırı uygulamasını çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="efe3c-111">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="efe3c-112">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="efe3c-112">Arguments</span></span>

`TEST_FILE_NAMES`

<span data-ttu-id="efe3c-113">Belirtilen derlemelerdeki testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="efe3c-113">Run tests from the specified assemblies.</span></span> <span data-ttu-id="efe3c-114">Birden çok test derleme adını boşluklarla ayırın.</span><span class="sxs-lookup"><span data-stu-id="efe3c-114">Separate multiple test assembly names with spaces.</span></span>

## <a name="options"></a><span data-ttu-id="efe3c-115">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="efe3c-115">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="efe3c-116">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="efe3c-116">.NET Core 2.1</span></span>](#tab/netcore21)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="efe3c-117">Testler çalıştırılırken kullanılacak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="efe3c-117">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="efe3c-118">Testleri, belirtilen değerlerle eşleşen adlarla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="efe3c-118">Run tests with names that match the provided values.</span></span> <span data-ttu-id="efe3c-119">Birden çok değeri virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="efe3c-119">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="efe3c-120">Test çalıştırmasında belirli bir yoldan (varsa) özel test bağdaştırıcıları kullanın.</span><span class="sxs-lookup"><span data-stu-id="efe3c-120">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="efe3c-121">Test yürütmesi için kullanılan hedef platform mimarisi.</span><span class="sxs-lookup"><span data-stu-id="efe3c-121">Target platform architecture used for test execution.</span></span> <span data-ttu-id="efe3c-122">Geçerli değerler `x86`, `x64`ve `ARM`.</span><span class="sxs-lookup"><span data-stu-id="efe3c-122">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="efe3c-123">Test yürütmesi için kullanılan hedef .NET Framework sürümü.</span><span class="sxs-lookup"><span data-stu-id="efe3c-123">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="efe3c-124">Geçerli değer örnekleri `.NETFramework,Version=v4.6` veya `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="efe3c-124">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="efe3c-125">Desteklenen diğer değerler `Framework40`, `Framework45`, `FrameworkCore10`ve `FrameworkUap10`.</span><span class="sxs-lookup"><span data-stu-id="efe3c-125">Other supported values are `Framework40`, `Framework45`, `FrameworkCore10`, and `FrameworkUap10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="efe3c-126">Testleri paralel olarak yürütün.</span><span class="sxs-lookup"><span data-stu-id="efe3c-126">Execute tests in parallel.</span></span> <span data-ttu-id="efe3c-127">Varsayılan olarak, makinedeki tüm kullanılabilir çekirdekler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="efe3c-127">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="efe3c-128">Runsettings dosyasındaki RunConfiguration düğümü altında MaxCpuCount özelliğini ayarlayarak açık sayıda çekirdek belirtin.</span><span class="sxs-lookup"><span data-stu-id="efe3c-128">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="efe3c-129">Verilen ifadeyle eşleşen testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="efe3c-129">Run tests that match the given expression.</span></span> <span data-ttu-id="efe3c-130">`<Expression>` biçim `<property>Operator<value>[|&<Expression>]`, burada Işleç `=`, `!=`veya `~`biridir.</span><span class="sxs-lookup"><span data-stu-id="efe3c-130">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="efe3c-131">İşleç `~` ' Contains ' semantiğine sahiptir ve `DisplayName`gibi dize özellikleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="efe3c-131">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="efe3c-132">Parantez `()` alt ifadeleri gruplandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="efe3c-132">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="efe3c-133">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="efe3c-133">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="efe3c-134">Test sonuçları için bir günlükçü belirtin.</span><span class="sxs-lookup"><span data-stu-id="efe3c-134">Specify a logger for test results.</span></span>

* <span data-ttu-id="efe3c-135">Test sonuçlarını Team Foundation Server yayımlamak için `TfsPublisher` günlükçü sağlayıcısını kullanın:</span><span class="sxs-lookup"><span data-stu-id="efe3c-135">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```console
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="efe3c-136">Sonuçları bir Visual Studio Test Sonuçları dosyasına (TRX) kaydetmek için `trx` günlükçü sağlayıcısını kullanın.</span><span class="sxs-lookup"><span data-stu-id="efe3c-136">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="efe3c-137">Bu anahtar, test sonuçları dizininde verilen günlük dosyası adına sahip bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="efe3c-137">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="efe3c-138">`LogFileName` sağlanmazsa, test sonuçlarını tutmak için benzersiz bir dosya adı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="efe3c-138">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```console
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="efe3c-139">Verilen test kapsayıcısından tüm bulunan testleri listeler.</span><span class="sxs-lookup"><span data-stu-id="efe3c-139">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="efe3c-140">Geçerli işlemin başlatmasından sorumlu olan üst işlemin işlem KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="efe3c-140">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="efe3c-141">Yuva bağlantısı ve olay iletilerini alma bağlantı noktasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="efe3c-141">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="efe3c-142">Test platformu için ayrıntılı günlükleri etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="efe3c-142">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="efe3c-143">Günlükler, belirtilen dosyaya yazılır.</span><span class="sxs-lookup"><span data-stu-id="efe3c-143">Logs are written to the provided file.</span></span>

`--Blame|/Blame`

<span data-ttu-id="efe3c-144">Testleri sorumluyu modunda çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="efe3c-144">Runs the tests in blame mode.</span></span> <span data-ttu-id="efe3c-145">Bu seçenek, test ana bilgisayarının kilitlenmesine neden olan sorunlu testleri yalıtmak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="efe3c-145">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="efe3c-146">Geçerli dizinde, kilitlenmeden önce yürütülen testlerin sırasını yakalayan *Sequence. xml* olarak bir çıktı dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="efe3c-146">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`--InIsolation|/InIsolation`

<span data-ttu-id="efe3c-147">Testleri yalıtılmış bir işlemde çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="efe3c-147">Runs the tests in an isolated process.</span></span> <span data-ttu-id="efe3c-148">Bu, *VSTest. Console. exe* işleminin testlerin bir hata üzerinde durdurulması olasılığını azaltır, ancak testler daha yavaş çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="efe3c-148">This makes *vstest.console.exe* process less likely to be stopped on an error in the tests, but tests may run slower.</span></span>

`@<file>`

<span data-ttu-id="efe3c-149">Daha fazla seçenek için yanıt dosyasını okur.</span><span class="sxs-lookup"><span data-stu-id="efe3c-149">Reads response file for more options.</span></span>

`args`

<span data-ttu-id="efe3c-150">Bağdaştırıcıya geçirilecek ek bağımsız değişkenleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="efe3c-150">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="efe3c-151">Bağımsız değişkenler `<n>=<v>`biçim-değer çiftleri olarak belirtilir; burada `<n>` bağımsız değişken adıdır ve `<v>` bağımsız değişken değeridir.</span><span class="sxs-lookup"><span data-stu-id="efe3c-151">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="efe3c-152">Birden çok bağımsız değişkeni ayırmak için boşluk kullanın.</span><span class="sxs-lookup"><span data-stu-id="efe3c-152">Use a space to separate multiple arguments.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="efe3c-153">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="efe3c-153">.NET Core 2.0</span></span>](#tab/netcore20)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="efe3c-154">Testler çalıştırılırken kullanılacak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="efe3c-154">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="efe3c-155">Testleri, belirtilen değerlerle eşleşen adlarla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="efe3c-155">Run tests with names that match the provided values.</span></span> <span data-ttu-id="efe3c-156">Birden çok değeri virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="efe3c-156">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="efe3c-157">Test çalıştırmasında belirli bir yoldan (varsa) özel test bağdaştırıcıları kullanın.</span><span class="sxs-lookup"><span data-stu-id="efe3c-157">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="efe3c-158">Test yürütmesi için kullanılan hedef platform mimarisi.</span><span class="sxs-lookup"><span data-stu-id="efe3c-158">Target platform architecture used for test execution.</span></span> <span data-ttu-id="efe3c-159">Geçerli değerler `x86`, `x64`ve `ARM`.</span><span class="sxs-lookup"><span data-stu-id="efe3c-159">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="efe3c-160">Test yürütmesi için kullanılan hedef .NET Framework sürümü.</span><span class="sxs-lookup"><span data-stu-id="efe3c-160">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="efe3c-161">Geçerli değer örnekleri `.NETFramework,Version=v4.6` veya `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="efe3c-161">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="efe3c-162">Desteklenen diğer değerler `Framework40`, `Framework45`ve `FrameworkCore10`.</span><span class="sxs-lookup"><span data-stu-id="efe3c-162">Other supported values are `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="efe3c-163">Testleri paralel olarak yürütün.</span><span class="sxs-lookup"><span data-stu-id="efe3c-163">Execute tests in parallel.</span></span> <span data-ttu-id="efe3c-164">Varsayılan olarak, makinedeki tüm kullanılabilir çekirdekler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="efe3c-164">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="efe3c-165">Runsettings dosyasındaki RunConfiguration düğümü altında MaxCpuCount özelliğini ayarlayarak açık sayıda çekirdek belirtin.</span><span class="sxs-lookup"><span data-stu-id="efe3c-165">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="efe3c-166">Verilen ifadeyle eşleşen testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="efe3c-166">Run tests that match the given expression.</span></span> <span data-ttu-id="efe3c-167">`<Expression>` biçim `<property>Operator<value>[|&<Expression>]`, burada Işleç `=`, `!=`veya `~`biridir.</span><span class="sxs-lookup"><span data-stu-id="efe3c-167">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="efe3c-168">İşleç `~` ' Contains ' semantiğine sahiptir ve `DisplayName`gibi dize özellikleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="efe3c-168">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="efe3c-169">Parantez `()` alt ifadeleri gruplandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="efe3c-169">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="efe3c-170">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="efe3c-170">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="efe3c-171">Test sonuçları için bir günlükçü belirtin.</span><span class="sxs-lookup"><span data-stu-id="efe3c-171">Specify a logger for test results.</span></span>

* <span data-ttu-id="efe3c-172">Test sonuçlarını Team Foundation Server yayımlamak için `TfsPublisher` günlükçü sağlayıcısını kullanın:</span><span class="sxs-lookup"><span data-stu-id="efe3c-172">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```console
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="efe3c-173">Sonuçları bir Visual Studio Test Sonuçları dosyasına (TRX) kaydetmek için `trx` günlükçü sağlayıcısını kullanın.</span><span class="sxs-lookup"><span data-stu-id="efe3c-173">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="efe3c-174">Bu anahtar, test sonuçları dizininde verilen günlük dosyası adına sahip bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="efe3c-174">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="efe3c-175">`LogFileName` sağlanmazsa, test sonuçlarını tutmak için benzersiz bir dosya adı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="efe3c-175">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```console
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="efe3c-176">Verilen test kapsayıcısından tüm bulunan testleri listeler.</span><span class="sxs-lookup"><span data-stu-id="efe3c-176">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="efe3c-177">Geçerli işlemin başlatmasından sorumlu olan üst işlemin işlem KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="efe3c-177">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="efe3c-178">Yuva bağlantısı ve olay iletilerini alma bağlantı noktasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="efe3c-178">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="efe3c-179">Test platformu için ayrıntılı günlükleri etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="efe3c-179">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="efe3c-180">Günlükler, belirtilen dosyaya yazılır.</span><span class="sxs-lookup"><span data-stu-id="efe3c-180">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="efe3c-181">Bağdaştırıcıya geçirilecek ek bağımsız değişkenleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="efe3c-181">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="efe3c-182">Bağımsız değişkenler `<n>=<v>`biçim-değer çiftleri olarak belirtilir; burada `<n>` bağımsız değişken adıdır ve `<v>` bağımsız değişken değeridir.</span><span class="sxs-lookup"><span data-stu-id="efe3c-182">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="efe3c-183">Birden çok bağımsız değişkeni ayırmak için boşluk kullanın.</span><span class="sxs-lookup"><span data-stu-id="efe3c-183">Use a space to separate multiple arguments.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="efe3c-184">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="efe3c-184">.NET Core 1.x</span></span>](#tab/netcore1x)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="efe3c-185">Testler çalıştırılırken kullanılacak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="efe3c-185">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="efe3c-186">Testleri, belirtilen değerlerle eşleşen adlarla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="efe3c-186">Run tests with names that match the provided values.</span></span> <span data-ttu-id="efe3c-187">Birden çok değeri virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="efe3c-187">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="efe3c-188">Test çalıştırmasında belirli bir yoldan (varsa) özel test bağdaştırıcıları kullanın.</span><span class="sxs-lookup"><span data-stu-id="efe3c-188">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="efe3c-189">Test yürütmesi için kullanılan hedef platform mimarisi.</span><span class="sxs-lookup"><span data-stu-id="efe3c-189">Target platform architecture used for test execution.</span></span> <span data-ttu-id="efe3c-190">Geçerli değerler `x86`, `x64`ve `ARM`.</span><span class="sxs-lookup"><span data-stu-id="efe3c-190">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="efe3c-191">Test yürütmesi için kullanılan hedef .NET Framework sürümü.</span><span class="sxs-lookup"><span data-stu-id="efe3c-191">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="efe3c-192">Geçerli değer örnekleri `.NETFramework,Version=v4.6` veya `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="efe3c-192">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="efe3c-193">Desteklenen diğer değerler `Framework40`, `Framework45`ve `FrameworkCore10`.</span><span class="sxs-lookup"><span data-stu-id="efe3c-193">Other supported values are `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="efe3c-194">Testleri paralel olarak yürütün.</span><span class="sxs-lookup"><span data-stu-id="efe3c-194">Execute tests in parallel.</span></span> <span data-ttu-id="efe3c-195">Varsayılan olarak, makinedeki tüm kullanılabilir çekirdekler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="efe3c-195">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="efe3c-196">Runsettings dosyasındaki RunConfiguration düğümü altında MaxCpuCount özelliğini ayarlayarak açık sayıda çekirdek belirtin.</span><span class="sxs-lookup"><span data-stu-id="efe3c-196">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="efe3c-197">Verilen ifadeyle eşleşen testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="efe3c-197">Run tests that match the given expression.</span></span> <span data-ttu-id="efe3c-198">`<Expression>` biçim `<property>Operator<value>[|&<Expression>]`, burada Işleç `=`, `!=`veya `~`biridir.</span><span class="sxs-lookup"><span data-stu-id="efe3c-198">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="efe3c-199">İşleç `~` ' Contains ' semantiğine sahiptir ve `DisplayName`gibi dize özellikleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="efe3c-199">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="efe3c-200">Parantez `()` alt ifadeleri gruplandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="efe3c-200">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="efe3c-201">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="efe3c-201">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="efe3c-202">Test sonuçları için bir günlükçü belirtin.</span><span class="sxs-lookup"><span data-stu-id="efe3c-202">Specify a logger for test results.</span></span>

* <span data-ttu-id="efe3c-203">Test sonuçlarını Team Foundation Server yayımlamak için `TfsPublisher` günlükçü sağlayıcısını kullanın:</span><span class="sxs-lookup"><span data-stu-id="efe3c-203">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```console
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="efe3c-204">Sonuçları bir Visual Studio Test Sonuçları dosyasına (TRX) kaydetmek için `trx` günlükçü sağlayıcısını kullanın.</span><span class="sxs-lookup"><span data-stu-id="efe3c-204">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="efe3c-205">Bu anahtar, test sonuçları dizininde verilen günlük dosyası adına sahip bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="efe3c-205">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="efe3c-206">`LogFileName` sağlanmazsa, test sonuçlarını tutmak için benzersiz bir dosya adı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="efe3c-206">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```console
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="efe3c-207">Verilen test kapsayıcısından tüm bulunan testleri listeler.</span><span class="sxs-lookup"><span data-stu-id="efe3c-207">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="efe3c-208">Geçerli işlemin başlatmasından sorumlu olan üst işlemin işlem KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="efe3c-208">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="efe3c-209">Yuva bağlantısı ve olay iletilerini alma bağlantı noktasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="efe3c-209">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="efe3c-210">Test platformu için ayrıntılı günlükleri etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="efe3c-210">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="efe3c-211">Günlükler, belirtilen dosyaya yazılır.</span><span class="sxs-lookup"><span data-stu-id="efe3c-211">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="efe3c-212">Bağdaştırıcıya geçirilecek ek bağımsız değişkenleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="efe3c-212">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="efe3c-213">Bağımsız değişkenler `<n>=<v>`biçim-değer çiftleri olarak belirtilir; burada `<n>` bağımsız değişken adıdır ve `<v>` bağımsız değişken değeridir.</span><span class="sxs-lookup"><span data-stu-id="efe3c-213">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="efe3c-214">Birden çok bağımsız değişkeni ayırmak için boşluk kullanın.</span><span class="sxs-lookup"><span data-stu-id="efe3c-214">Use a space to separate multiple arguments.</span></span>

---

## <a name="examples"></a><span data-ttu-id="efe3c-215">Örnekler</span><span class="sxs-lookup"><span data-stu-id="efe3c-215">Examples</span></span>

<span data-ttu-id="efe3c-216">`mytestproject.dll`Testleri Çalıştır:</span><span class="sxs-lookup"><span data-stu-id="efe3c-216">Run tests in `mytestproject.dll`:</span></span>

`dotnet vstest mytestproject.dll`

<span data-ttu-id="efe3c-217">Testleri `mytestproject.dll`' de Çalıştır, özel bir klasöre dışarı aktarma özel adı:</span><span class="sxs-lookup"><span data-stu-id="efe3c-217">Run tests in `mytestproject.dll`, exporting to custom folder with custom name:</span></span>

`dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path`

<span data-ttu-id="efe3c-218">`mytestproject.dll` ve `myothertestproject.exe`testleri çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="efe3c-218">Run tests in `mytestproject.dll` and `myothertestproject.exe`:</span></span>

`dotnet vstest mytestproject.dll myothertestproject.exe`

<span data-ttu-id="efe3c-219">`TestMethod1` testlerini Çalıştır:</span><span class="sxs-lookup"><span data-stu-id="efe3c-219">Run `TestMethod1` tests:</span></span>

`dotnet vstest /Tests:TestMethod1`

<span data-ttu-id="efe3c-220">`TestMethod1` Çalıştır ve Testleri `TestMethod2`:</span><span class="sxs-lookup"><span data-stu-id="efe3c-220">Run `TestMethod1` and `TestMethod2` tests:</span></span>

`dotnet vstest /Tests:TestMethod1,TestMethod2`
