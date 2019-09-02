---
title: DotNet VSTest komutu
description: DotNet VSTest komutu bir proje ve tüm bağımlılıklarını oluşturur.
author: mairaw
ms.date: 05/30/2018
ms.openlocfilehash: 4630982ba21ab37b051895faf3dc0fcd8784cb18
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202784"
---
# <a name="dotnet-vstest"></a><span data-ttu-id="7d077-103">dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="7d077-103">dotnet vstest</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="7d077-104">Ad</span><span class="sxs-lookup"><span data-stu-id="7d077-104">Name</span></span>

<span data-ttu-id="7d077-105">`dotnet-vstest`-Belirtilen dosyalardan testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="7d077-105">`dotnet-vstest` - Runs tests from the specified files.</span></span>

## <a name="synopsis"></a><span data-ttu-id="7d077-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="7d077-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="7d077-107">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="7d077-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [--Blame|/Blame] [--InIsolation|/InIsolation]
    [[--] <args>...]] [-?|--Help|/?|/Help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="7d077-108">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="7d077-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath] 
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="7d077-109">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="7d077-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger] 
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```

---

## <a name="description"></a><span data-ttu-id="7d077-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7d077-110">Description</span></span>

<span data-ttu-id="7d077-111">Komut `dotnet-vstest` , otomatik birim `VSTest.Console` testlerini çalıştırmak için komut satırı uygulamasını çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="7d077-111">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="7d077-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="7d077-112">Arguments</span></span>

`TEST_FILE_NAMES`

<span data-ttu-id="7d077-113">Belirtilen derlemelerdeki testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7d077-113">Run tests from the specified assemblies.</span></span> <span data-ttu-id="7d077-114">Birden çok test derleme adını boşluklarla ayırın.</span><span class="sxs-lookup"><span data-stu-id="7d077-114">Separate multiple test assembly names with spaces.</span></span>

## <a name="options"></a><span data-ttu-id="7d077-115">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="7d077-115">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="7d077-116">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="7d077-116">.NET Core 2.1</span></span>](#tab/netcore21)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="7d077-117">Testler çalıştırılırken kullanılacak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7d077-117">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="7d077-118">Testleri, belirtilen değerlerle eşleşen adlarla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7d077-118">Run tests with names that match the provided values.</span></span> <span data-ttu-id="7d077-119">Birden çok değeri virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="7d077-119">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="7d077-120">Test çalıştırmasında belirli bir yoldan (varsa) özel test bağdaştırıcıları kullanın.</span><span class="sxs-lookup"><span data-stu-id="7d077-120">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="7d077-121">Test yürütmesi için kullanılan hedef platform mimarisi.</span><span class="sxs-lookup"><span data-stu-id="7d077-121">Target platform architecture used for test execution.</span></span> <span data-ttu-id="7d077-122">Geçerli değerler `x86`, `x64`, ve `ARM`.</span><span class="sxs-lookup"><span data-stu-id="7d077-122">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="7d077-123">Test yürütmesi için kullanılan hedef .NET Framework sürümü.</span><span class="sxs-lookup"><span data-stu-id="7d077-123">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="7d077-124">Geçerli değer `.NETFramework,Version=v4.6` örnekleri veya `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="7d077-124">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="7d077-125">Desteklenen `Framework40`diğer değerler `Framework45` ,`FrameworkCore10`, ve`FrameworkUap10`' dir.</span><span class="sxs-lookup"><span data-stu-id="7d077-125">Other supported values are `Framework40`, `Framework45`, `FrameworkCore10`, and `FrameworkUap10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="7d077-126">Testleri paralel olarak yürütün.</span><span class="sxs-lookup"><span data-stu-id="7d077-126">Execute tests in parallel.</span></span> <span data-ttu-id="7d077-127">Varsayılan olarak, makinedeki tüm kullanılabilir çekirdekler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7d077-127">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="7d077-128">Runsettings dosyasındaki RunConfiguration düğümü altında MaxCpuCount özelliğini ayarlayarak açık sayıda çekirdek belirtin.</span><span class="sxs-lookup"><span data-stu-id="7d077-128">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="7d077-129">Verilen ifadeyle eşleşen testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7d077-129">Run tests that match the given expression.</span></span> <span data-ttu-id="7d077-130">`<Expression>`biçimindedir `<property>Operator<value>[|&<Expression>]`, burada işleci `=`, `!=`veya `~`' den biridir.</span><span class="sxs-lookup"><span data-stu-id="7d077-130">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="7d077-131">İşlecinde `~` ' Contains ' semantiği var ve gibi `DisplayName`dize özellikleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="7d077-131">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="7d077-132">Parantez `()` alt ifadeleri gruplandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7d077-132">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="7d077-133">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="7d077-133">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="7d077-134">Test sonuçları için bir günlükçü belirtin.</span><span class="sxs-lookup"><span data-stu-id="7d077-134">Specify a logger for test results.</span></span>

* <span data-ttu-id="7d077-135">Team Foundation Server için test sonuçlarını yayınlamak için `TfsPublisher` günlükçü sağlayıcısını kullanın:</span><span class="sxs-lookup"><span data-stu-id="7d077-135">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```console
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="7d077-136">Sonuçları bir Visual Studio test sonuçları dosyasına (trx) kaydetmek için `trx` günlükçü sağlayıcısını kullanın.</span><span class="sxs-lookup"><span data-stu-id="7d077-136">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="7d077-137">Bu anahtar, test sonuçları dizininde verilen günlük dosyası adına sahip bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7d077-137">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="7d077-138">`LogFileName` Sağlanmazsa, test sonuçlarını tutmak için benzersiz bir dosya adı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7d077-138">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```console
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="7d077-139">Verilen test kapsayıcısından tüm bulunan testleri listeler.</span><span class="sxs-lookup"><span data-stu-id="7d077-139">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="7d077-140">Geçerli işlemin başlatmasından sorumlu olan üst işlemin işlem KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="7d077-140">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="7d077-141">Yuva bağlantısı ve olay iletilerini alma bağlantı noktasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7d077-141">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="7d077-142">Test platformu için ayrıntılı günlükleri etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="7d077-142">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="7d077-143">Günlükler, belirtilen dosyaya yazılır.</span><span class="sxs-lookup"><span data-stu-id="7d077-143">Logs are written to the provided file.</span></span>

`--Blame|/Blame`

<span data-ttu-id="7d077-144">Testleri sorumluyu modunda çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="7d077-144">Runs the tests in blame mode.</span></span> <span data-ttu-id="7d077-145">Bu seçenek, test ana bilgisayarının kilitlenmesine neden olan sorunlu testleri yalıtmak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="7d077-145">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="7d077-146">Geçerli dizinde, kilitlenmeden önce yürütülen testlerin sırasını yakalayan *Sequence. xml* olarak bir çıktı dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7d077-146">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`--InIsolation|/InIsolation`

<span data-ttu-id="7d077-147">Testleri yalıtılmış bir işlemde çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="7d077-147">Runs the tests in an isolated process.</span></span> <span data-ttu-id="7d077-148">Bu, *VSTest. Console. exe* işleminin testlerin bir hata üzerinde durdurulması olasılığını azaltır, ancak testler daha yavaş çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="7d077-148">This makes *vstest.console.exe* process less likely to be stopped on an error in the tests, but tests may run slower.</span></span>

`@<file>`

<span data-ttu-id="7d077-149">Daha fazla seçenek için yanıt dosyasını okur.</span><span class="sxs-lookup"><span data-stu-id="7d077-149">Reads response file for more options.</span></span>

`args`

<span data-ttu-id="7d077-150">Bağdaştırıcıya geçirilecek ek bağımsız değişkenleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="7d077-150">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="7d077-151">Bağımsız değişkenler, formun `<n>=<v>`ad-değer çiftleri olarak belirtilir, burada `<n>` bağımsız değişken adıdır ve `<v>` bağımsız değişken değeridir.</span><span class="sxs-lookup"><span data-stu-id="7d077-151">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="7d077-152">Birden çok bağımsız değişkeni ayırmak için boşluk kullanın.</span><span class="sxs-lookup"><span data-stu-id="7d077-152">Use a space to separate multiple arguments.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="7d077-153">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="7d077-153">.NET Core 2.0</span></span>](#tab/netcore20)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="7d077-154">Testler çalıştırılırken kullanılacak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7d077-154">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="7d077-155">Testleri, belirtilen değerlerle eşleşen adlarla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7d077-155">Run tests with names that match the provided values.</span></span> <span data-ttu-id="7d077-156">Birden çok değeri virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="7d077-156">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="7d077-157">Test çalıştırmasında belirli bir yoldan (varsa) özel test bağdaştırıcıları kullanın.</span><span class="sxs-lookup"><span data-stu-id="7d077-157">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="7d077-158">Test yürütmesi için kullanılan hedef platform mimarisi.</span><span class="sxs-lookup"><span data-stu-id="7d077-158">Target platform architecture used for test execution.</span></span> <span data-ttu-id="7d077-159">Geçerli değerler `x86`, `x64`, ve `ARM`.</span><span class="sxs-lookup"><span data-stu-id="7d077-159">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="7d077-160">Test yürütmesi için kullanılan hedef .NET Framework sürümü.</span><span class="sxs-lookup"><span data-stu-id="7d077-160">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="7d077-161">Geçerli değer `.NETFramework,Version=v4.6` örnekleri veya `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="7d077-161">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="7d077-162">Desteklenen diğer değerler, `Framework40` `Framework45`ve `FrameworkCore10`' dir.</span><span class="sxs-lookup"><span data-stu-id="7d077-162">Other supported values are `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="7d077-163">Testleri paralel olarak yürütün.</span><span class="sxs-lookup"><span data-stu-id="7d077-163">Execute tests in parallel.</span></span> <span data-ttu-id="7d077-164">Varsayılan olarak, makinedeki tüm kullanılabilir çekirdekler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7d077-164">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="7d077-165">Runsettings dosyasındaki RunConfiguration düğümü altında MaxCpuCount özelliğini ayarlayarak açık sayıda çekirdek belirtin.</span><span class="sxs-lookup"><span data-stu-id="7d077-165">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="7d077-166">Verilen ifadeyle eşleşen testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7d077-166">Run tests that match the given expression.</span></span> <span data-ttu-id="7d077-167">`<Expression>`biçimindedir `<property>Operator<value>[|&<Expression>]`, burada işleci `=`, `!=`veya `~`' den biridir.</span><span class="sxs-lookup"><span data-stu-id="7d077-167">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="7d077-168">İşlecinde `~` ' Contains ' semantiği var ve gibi `DisplayName`dize özellikleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="7d077-168">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="7d077-169">Parantez `()` alt ifadeleri gruplandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7d077-169">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="7d077-170">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="7d077-170">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="7d077-171">Test sonuçları için bir günlükçü belirtin.</span><span class="sxs-lookup"><span data-stu-id="7d077-171">Specify a logger for test results.</span></span>

* <span data-ttu-id="7d077-172">Team Foundation Server için test sonuçlarını yayınlamak için `TfsPublisher` günlükçü sağlayıcısını kullanın:</span><span class="sxs-lookup"><span data-stu-id="7d077-172">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```console
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="7d077-173">Sonuçları bir Visual Studio test sonuçları dosyasına (trx) kaydetmek için `trx` günlükçü sağlayıcısını kullanın.</span><span class="sxs-lookup"><span data-stu-id="7d077-173">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="7d077-174">Bu anahtar, test sonuçları dizininde verilen günlük dosyası adına sahip bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7d077-174">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="7d077-175">`LogFileName` Sağlanmazsa, test sonuçlarını tutmak için benzersiz bir dosya adı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7d077-175">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```console
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="7d077-176">Verilen test kapsayıcısından tüm bulunan testleri listeler.</span><span class="sxs-lookup"><span data-stu-id="7d077-176">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="7d077-177">Geçerli işlemin başlatmasından sorumlu olan üst işlemin işlem KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="7d077-177">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="7d077-178">Yuva bağlantısı ve olay iletilerini alma bağlantı noktasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7d077-178">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="7d077-179">Test platformu için ayrıntılı günlükleri etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="7d077-179">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="7d077-180">Günlükler, belirtilen dosyaya yazılır.</span><span class="sxs-lookup"><span data-stu-id="7d077-180">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="7d077-181">Bağdaştırıcıya geçirilecek ek bağımsız değişkenleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="7d077-181">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="7d077-182">Bağımsız değişkenler, formun `<n>=<v>`ad-değer çiftleri olarak belirtilir, burada `<n>` bağımsız değişken adıdır ve `<v>` bağımsız değişken değeridir.</span><span class="sxs-lookup"><span data-stu-id="7d077-182">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="7d077-183">Birden çok bağımsız değişkeni ayırmak için boşluk kullanın.</span><span class="sxs-lookup"><span data-stu-id="7d077-183">Use a space to separate multiple arguments.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="7d077-184">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="7d077-184">.NET Core 1.x</span></span>](#tab/netcore1x)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="7d077-185">Testler çalıştırılırken kullanılacak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7d077-185">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="7d077-186">Testleri, belirtilen değerlerle eşleşen adlarla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7d077-186">Run tests with names that match the provided values.</span></span> <span data-ttu-id="7d077-187">Birden çok değeri virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="7d077-187">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="7d077-188">Test çalıştırmasında belirli bir yoldan (varsa) özel test bağdaştırıcıları kullanın.</span><span class="sxs-lookup"><span data-stu-id="7d077-188">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="7d077-189">Test yürütmesi için kullanılan hedef platform mimarisi.</span><span class="sxs-lookup"><span data-stu-id="7d077-189">Target platform architecture used for test execution.</span></span> <span data-ttu-id="7d077-190">Geçerli değerler `x86`, `x64`, ve `ARM`.</span><span class="sxs-lookup"><span data-stu-id="7d077-190">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="7d077-191">Test yürütmesi için kullanılan hedef .NET Framework sürümü.</span><span class="sxs-lookup"><span data-stu-id="7d077-191">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="7d077-192">Geçerli değer `.NETFramework,Version=v4.6` örnekleri veya `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="7d077-192">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="7d077-193">Desteklenen diğer değerler, `Framework40` `Framework45`ve `FrameworkCore10`' dir.</span><span class="sxs-lookup"><span data-stu-id="7d077-193">Other supported values are `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="7d077-194">Testleri paralel olarak yürütün.</span><span class="sxs-lookup"><span data-stu-id="7d077-194">Execute tests in parallel.</span></span> <span data-ttu-id="7d077-195">Varsayılan olarak, makinedeki tüm kullanılabilir çekirdekler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7d077-195">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="7d077-196">Runsettings dosyasındaki RunConfiguration düğümü altında MaxCpuCount özelliğini ayarlayarak açık sayıda çekirdek belirtin.</span><span class="sxs-lookup"><span data-stu-id="7d077-196">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="7d077-197">Verilen ifadeyle eşleşen testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7d077-197">Run tests that match the given expression.</span></span> <span data-ttu-id="7d077-198">`<Expression>`biçimindedir `<property>Operator<value>[|&<Expression>]`, burada işleci `=`, `!=`veya `~`' den biridir.</span><span class="sxs-lookup"><span data-stu-id="7d077-198">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="7d077-199">İşlecinde `~` ' Contains ' semantiği var ve gibi `DisplayName`dize özellikleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="7d077-199">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="7d077-200">Parantez `()` alt ifadeleri gruplandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7d077-200">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="7d077-201">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="7d077-201">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="7d077-202">Test sonuçları için bir günlükçü belirtin.</span><span class="sxs-lookup"><span data-stu-id="7d077-202">Specify a logger for test results.</span></span>

* <span data-ttu-id="7d077-203">Team Foundation Server için test sonuçlarını yayınlamak için `TfsPublisher` günlükçü sağlayıcısını kullanın:</span><span class="sxs-lookup"><span data-stu-id="7d077-203">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```console
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="7d077-204">Sonuçları bir Visual Studio test sonuçları dosyasına (trx) kaydetmek için `trx` günlükçü sağlayıcısını kullanın.</span><span class="sxs-lookup"><span data-stu-id="7d077-204">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="7d077-205">Bu anahtar, test sonuçları dizininde verilen günlük dosyası adına sahip bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7d077-205">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="7d077-206">`LogFileName` Sağlanmazsa, test sonuçlarını tutmak için benzersiz bir dosya adı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7d077-206">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```console
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="7d077-207">Verilen test kapsayıcısından tüm bulunan testleri listeler.</span><span class="sxs-lookup"><span data-stu-id="7d077-207">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="7d077-208">Geçerli işlemin başlatmasından sorumlu olan üst işlemin işlem KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="7d077-208">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="7d077-209">Yuva bağlantısı ve olay iletilerini alma bağlantı noktasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7d077-209">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="7d077-210">Test platformu için ayrıntılı günlükleri etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="7d077-210">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="7d077-211">Günlükler, belirtilen dosyaya yazılır.</span><span class="sxs-lookup"><span data-stu-id="7d077-211">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="7d077-212">Bağdaştırıcıya geçirilecek ek bağımsız değişkenleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="7d077-212">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="7d077-213">Bağımsız değişkenler, formun `<n>=<v>`ad-değer çiftleri olarak belirtilir, burada `<n>` bağımsız değişken adıdır ve `<v>` bağımsız değişken değeridir.</span><span class="sxs-lookup"><span data-stu-id="7d077-213">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="7d077-214">Birden çok bağımsız değişkeni ayırmak için boşluk kullanın.</span><span class="sxs-lookup"><span data-stu-id="7d077-214">Use a space to separate multiple arguments.</span></span>

---

## <a name="examples"></a><span data-ttu-id="7d077-215">Örnekler</span><span class="sxs-lookup"><span data-stu-id="7d077-215">Examples</span></span>

<span data-ttu-id="7d077-216">Testleri `mytestproject.dll`çalıştırma:</span><span class="sxs-lookup"><span data-stu-id="7d077-216">Run tests in `mytestproject.dll`:</span></span>

`dotnet vstest mytestproject.dll`

<span data-ttu-id="7d077-217">Özel adla özel `mytestproject.dll`klasöre dışarı aktarmak için içindeki testleri çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="7d077-217">Run tests in `mytestproject.dll`, exporting to custom folder with custom name:</span></span>

`dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path`

<span data-ttu-id="7d077-218">Testleri ve `mytestproject.dll` `myothertestproject.exe`içinde çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="7d077-218">Run tests in `mytestproject.dll` and `myothertestproject.exe`:</span></span>

`dotnet vstest mytestproject.dll myothertestproject.exe`

<span data-ttu-id="7d077-219">Testleri `TestMethod1` Çalıştır:</span><span class="sxs-lookup"><span data-stu-id="7d077-219">Run `TestMethod1` tests:</span></span>

`dotnet vstest /Tests:TestMethod1`

<span data-ttu-id="7d077-220">Çalıştır `TestMethod1` ve`TestMethod2` testler:</span><span class="sxs-lookup"><span data-stu-id="7d077-220">Run `TestMethod1` and `TestMethod2` tests:</span></span>

`dotnet vstest /Tests:TestMethod1,TestMethod2`
