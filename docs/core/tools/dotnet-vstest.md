---
title: DotNet VSTest komutu
description: DotNet VSTest komutu bir proje ve tüm bağımlılıklarını oluşturur.
author: mairaw
ms.date: 05/30/2018
ms.openlocfilehash: ffe3807be2c35fb4d6b46b83ed84200433f551d8
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117517"
---
# <a name="dotnet-vstest"></a><span data-ttu-id="0329e-103">dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="0329e-103">dotnet vstest</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="0329e-104">Ad</span><span class="sxs-lookup"><span data-stu-id="0329e-104">Name</span></span>

<span data-ttu-id="0329e-105">`dotnet-vstest`-Belirtilen dosyalardan testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="0329e-105">`dotnet-vstest` - Runs tests from the specified files.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0329e-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="0329e-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="0329e-107">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="0329e-107">.NET Core 2.1</span></span>](#tab/netcore21)

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [--Blame|/Blame] [--InIsolation|/InIsolation]
    [[--] <args>...]] [-?|--Help|/?|/Help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="0329e-108">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="0329e-108">.NET Core 2.0</span></span>](#tab/netcore20)

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath] 
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="0329e-109">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="0329e-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger] 
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```

---

## <a name="description"></a><span data-ttu-id="0329e-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0329e-110">Description</span></span>

<span data-ttu-id="0329e-111">Komut `dotnet-vstest` , otomatik birim `VSTest.Console` testlerini çalıştırmak için komut satırı uygulamasını çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="0329e-111">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="0329e-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="0329e-112">Arguments</span></span>

`TEST_FILE_NAMES`

<span data-ttu-id="0329e-113">Belirtilen derlemelerdeki testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0329e-113">Run tests from the specified assemblies.</span></span> <span data-ttu-id="0329e-114">Birden çok test derleme adını boşluklarla ayırın.</span><span class="sxs-lookup"><span data-stu-id="0329e-114">Separate multiple test assembly names with spaces.</span></span>

## <a name="options"></a><span data-ttu-id="0329e-115">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="0329e-115">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="0329e-116">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="0329e-116">.NET Core 2.1</span></span>](#tab/netcore21)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="0329e-117">Testler çalıştırılırken kullanılacak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0329e-117">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="0329e-118">Testleri, belirtilen değerlerle eşleşen adlarla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0329e-118">Run tests with names that match the provided values.</span></span> <span data-ttu-id="0329e-119">Birden çok değeri virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="0329e-119">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="0329e-120">Test çalıştırmasında belirli bir yoldan (varsa) özel test bağdaştırıcıları kullanın.</span><span class="sxs-lookup"><span data-stu-id="0329e-120">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="0329e-121">Test yürütmesi için kullanılan hedef platform mimarisi.</span><span class="sxs-lookup"><span data-stu-id="0329e-121">Target platform architecture used for test execution.</span></span> <span data-ttu-id="0329e-122">Geçerli değerler `x86`, `x64`, ve `ARM`.</span><span class="sxs-lookup"><span data-stu-id="0329e-122">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="0329e-123">Test yürütmesi için kullanılan hedef .NET Framework sürümü.</span><span class="sxs-lookup"><span data-stu-id="0329e-123">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="0329e-124">Geçerli değer `.NETFramework,Version=v4.6` örnekleri veya `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="0329e-124">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="0329e-125">Desteklenen `Framework40`diğer değerler `Framework45` ,`FrameworkCore10`, ve`FrameworkUap10`' dir.</span><span class="sxs-lookup"><span data-stu-id="0329e-125">Other supported values are `Framework40`, `Framework45`, `FrameworkCore10`, and `FrameworkUap10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="0329e-126">Testleri paralel olarak yürütün.</span><span class="sxs-lookup"><span data-stu-id="0329e-126">Execute tests in parallel.</span></span> <span data-ttu-id="0329e-127">Varsayılan olarak, makinedeki tüm kullanılabilir çekirdekler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0329e-127">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="0329e-128">Runsettings dosyasındaki RunConfiguration düğümü altında MaxCpuCount özelliğini ayarlayarak açık sayıda çekirdek belirtin.</span><span class="sxs-lookup"><span data-stu-id="0329e-128">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="0329e-129">Verilen ifadeyle eşleşen testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0329e-129">Run tests that match the given expression.</span></span> <span data-ttu-id="0329e-130">`<Expression>`biçimindedir `<property>Operator<value>[|&<Expression>]`, burada işleci `=`, `!=`veya `~`' den biridir.</span><span class="sxs-lookup"><span data-stu-id="0329e-130">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="0329e-131">İşlecinde `~` ' Contains ' semantiği var ve gibi `DisplayName`dize özellikleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0329e-131">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="0329e-132">Parantez `()` alt ifadeleri gruplandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0329e-132">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="0329e-133">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="0329e-133">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="0329e-134">Test sonuçları için bir günlükçü belirtin.</span><span class="sxs-lookup"><span data-stu-id="0329e-134">Specify a logger for test results.</span></span>

* <span data-ttu-id="0329e-135">Team Foundation Server için test sonuçlarını yayınlamak için `TfsPublisher` günlükçü sağlayıcısını kullanın:</span><span class="sxs-lookup"><span data-stu-id="0329e-135">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```console
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="0329e-136">Sonuçları bir Visual Studio test sonuçları dosyasına (trx) kaydetmek için `trx` günlükçü sağlayıcısını kullanın.</span><span class="sxs-lookup"><span data-stu-id="0329e-136">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="0329e-137">Bu anahtar, test sonuçları dizininde verilen günlük dosyası adına sahip bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0329e-137">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="0329e-138">`LogFileName` Sağlanmazsa, test sonuçlarını tutmak için benzersiz bir dosya adı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0329e-138">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```console
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="0329e-139">Verilen test kapsayıcısından tüm bulunan testleri listeler.</span><span class="sxs-lookup"><span data-stu-id="0329e-139">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="0329e-140">Geçerli işlemin başlatmasından sorumlu olan üst işlemin işlem KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="0329e-140">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="0329e-141">Yuva bağlantısı ve olay iletilerini alma bağlantı noktasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0329e-141">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="0329e-142">Test platformu için ayrıntılı günlükleri etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="0329e-142">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="0329e-143">Günlükler, belirtilen dosyaya yazılır.</span><span class="sxs-lookup"><span data-stu-id="0329e-143">Logs are written to the provided file.</span></span>

`--Blame|/Blame`

<span data-ttu-id="0329e-144">Testleri sorumluyu modunda çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="0329e-144">Runs the tests in blame mode.</span></span> <span data-ttu-id="0329e-145">Bu seçenek, test ana bilgisayarının kilitlenmesine neden olan sorunlu testleri yalıtmak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="0329e-145">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="0329e-146">Geçerli dizinde, kilitlenmeden önce yürütülen testlerin sırasını yakalayan *Sequence. xml* olarak bir çıktı dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0329e-146">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`--InIsolation|/InIsolation`

<span data-ttu-id="0329e-147">Testleri yalıtılmış bir işlemde çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="0329e-147">Runs the tests in an isolated process.</span></span> <span data-ttu-id="0329e-148">Bu, *VSTest. Console. exe* işleminin testlerin bir hata üzerinde durdurulması olasılığını azaltır, ancak testler daha yavaş çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="0329e-148">This makes *vstest.console.exe* process less likely to be stopped on an error in the tests, but tests may run slower.</span></span>

`@<file>`

<span data-ttu-id="0329e-149">Daha fazla seçenek için yanıt dosyasını okur.</span><span class="sxs-lookup"><span data-stu-id="0329e-149">Reads response file for more options.</span></span>

`args`

<span data-ttu-id="0329e-150">Bağdaştırıcıya geçirilecek ek bağımsız değişkenleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="0329e-150">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="0329e-151">Bağımsız değişkenler, formun `<n>=<v>`ad-değer çiftleri olarak belirtilir, burada `<n>` bağımsız değişken adıdır ve `<v>` bağımsız değişken değeridir.</span><span class="sxs-lookup"><span data-stu-id="0329e-151">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="0329e-152">Birden çok bağımsız değişkeni ayırmak için boşluk kullanın.</span><span class="sxs-lookup"><span data-stu-id="0329e-152">Use a space to separate multiple arguments.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="0329e-153">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="0329e-153">.NET Core 2.0</span></span>](#tab/netcore20)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="0329e-154">Testler çalıştırılırken kullanılacak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0329e-154">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="0329e-155">Testleri, belirtilen değerlerle eşleşen adlarla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0329e-155">Run tests with names that match the provided values.</span></span> <span data-ttu-id="0329e-156">Birden çok değeri virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="0329e-156">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="0329e-157">Test çalıştırmasında belirli bir yoldan (varsa) özel test bağdaştırıcıları kullanın.</span><span class="sxs-lookup"><span data-stu-id="0329e-157">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="0329e-158">Test yürütmesi için kullanılan hedef platform mimarisi.</span><span class="sxs-lookup"><span data-stu-id="0329e-158">Target platform architecture used for test execution.</span></span> <span data-ttu-id="0329e-159">Geçerli değerler `x86`, `x64`, ve `ARM`.</span><span class="sxs-lookup"><span data-stu-id="0329e-159">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="0329e-160">Test yürütmesi için kullanılan hedef .NET Framework sürümü.</span><span class="sxs-lookup"><span data-stu-id="0329e-160">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="0329e-161">Geçerli değer `.NETFramework,Version=v4.6` örnekleri veya `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="0329e-161">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="0329e-162">Desteklenen diğer değerler, `Framework40` `Framework45`ve `FrameworkCore10`' dir.</span><span class="sxs-lookup"><span data-stu-id="0329e-162">Other supported values are `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="0329e-163">Testleri paralel olarak yürütün.</span><span class="sxs-lookup"><span data-stu-id="0329e-163">Execute tests in parallel.</span></span> <span data-ttu-id="0329e-164">Varsayılan olarak, makinedeki tüm kullanılabilir çekirdekler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0329e-164">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="0329e-165">Runsettings dosyasındaki RunConfiguration düğümü altında MaxCpuCount özelliğini ayarlayarak açık sayıda çekirdek belirtin.</span><span class="sxs-lookup"><span data-stu-id="0329e-165">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="0329e-166">Verilen ifadeyle eşleşen testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0329e-166">Run tests that match the given expression.</span></span> <span data-ttu-id="0329e-167">`<Expression>`biçimindedir `<property>Operator<value>[|&<Expression>]`, burada işleci `=`, `!=`veya `~`' den biridir.</span><span class="sxs-lookup"><span data-stu-id="0329e-167">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="0329e-168">İşlecinde `~` ' Contains ' semantiği var ve gibi `DisplayName`dize özellikleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0329e-168">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="0329e-169">Parantez `()` alt ifadeleri gruplandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0329e-169">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="0329e-170">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="0329e-170">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="0329e-171">Test sonuçları için bir günlükçü belirtin.</span><span class="sxs-lookup"><span data-stu-id="0329e-171">Specify a logger for test results.</span></span>

* <span data-ttu-id="0329e-172">Team Foundation Server için test sonuçlarını yayınlamak için `TfsPublisher` günlükçü sağlayıcısını kullanın:</span><span class="sxs-lookup"><span data-stu-id="0329e-172">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```console
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="0329e-173">Sonuçları bir Visual Studio test sonuçları dosyasına (trx) kaydetmek için `trx` günlükçü sağlayıcısını kullanın.</span><span class="sxs-lookup"><span data-stu-id="0329e-173">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="0329e-174">Bu anahtar, test sonuçları dizininde verilen günlük dosyası adına sahip bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0329e-174">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="0329e-175">`LogFileName` Sağlanmazsa, test sonuçlarını tutmak için benzersiz bir dosya adı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0329e-175">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```console
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="0329e-176">Verilen test kapsayıcısından tüm bulunan testleri listeler.</span><span class="sxs-lookup"><span data-stu-id="0329e-176">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="0329e-177">Geçerli işlemin başlatmasından sorumlu olan üst işlemin işlem KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="0329e-177">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="0329e-178">Yuva bağlantısı ve olay iletilerini alma bağlantı noktasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0329e-178">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="0329e-179">Test platformu için ayrıntılı günlükleri etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="0329e-179">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="0329e-180">Günlükler, belirtilen dosyaya yazılır.</span><span class="sxs-lookup"><span data-stu-id="0329e-180">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="0329e-181">Bağdaştırıcıya geçirilecek ek bağımsız değişkenleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="0329e-181">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="0329e-182">Bağımsız değişkenler, formun `<n>=<v>`ad-değer çiftleri olarak belirtilir, burada `<n>` bağımsız değişken adıdır ve `<v>` bağımsız değişken değeridir.</span><span class="sxs-lookup"><span data-stu-id="0329e-182">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="0329e-183">Birden çok bağımsız değişkeni ayırmak için boşluk kullanın.</span><span class="sxs-lookup"><span data-stu-id="0329e-183">Use a space to separate multiple arguments.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="0329e-184">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="0329e-184">.NET Core 1.x</span></span>](#tab/netcore1x)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="0329e-185">Testler çalıştırılırken kullanılacak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0329e-185">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="0329e-186">Testleri, belirtilen değerlerle eşleşen adlarla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0329e-186">Run tests with names that match the provided values.</span></span> <span data-ttu-id="0329e-187">Birden çok değeri virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="0329e-187">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="0329e-188">Test çalıştırmasında belirli bir yoldan (varsa) özel test bağdaştırıcıları kullanın.</span><span class="sxs-lookup"><span data-stu-id="0329e-188">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="0329e-189">Test yürütmesi için kullanılan hedef platform mimarisi.</span><span class="sxs-lookup"><span data-stu-id="0329e-189">Target platform architecture used for test execution.</span></span> <span data-ttu-id="0329e-190">Geçerli değerler `x86`, `x64`, ve `ARM`.</span><span class="sxs-lookup"><span data-stu-id="0329e-190">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="0329e-191">Test yürütmesi için kullanılan hedef .NET Framework sürümü.</span><span class="sxs-lookup"><span data-stu-id="0329e-191">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="0329e-192">Geçerli değer `.NETFramework,Version=v4.6` örnekleri veya `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="0329e-192">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="0329e-193">Desteklenen diğer değerler, `Framework40` `Framework45`ve `FrameworkCore10`' dir.</span><span class="sxs-lookup"><span data-stu-id="0329e-193">Other supported values are `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="0329e-194">Testleri paralel olarak yürütün.</span><span class="sxs-lookup"><span data-stu-id="0329e-194">Execute tests in parallel.</span></span> <span data-ttu-id="0329e-195">Varsayılan olarak, makinedeki tüm kullanılabilir çekirdekler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0329e-195">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="0329e-196">Runsettings dosyasındaki RunConfiguration düğümü altında MaxCpuCount özelliğini ayarlayarak açık sayıda çekirdek belirtin.</span><span class="sxs-lookup"><span data-stu-id="0329e-196">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="0329e-197">Verilen ifadeyle eşleşen testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0329e-197">Run tests that match the given expression.</span></span> <span data-ttu-id="0329e-198">`<Expression>`biçimindedir `<property>Operator<value>[|&<Expression>]`, burada işleci `=`, `!=`veya `~`' den biridir.</span><span class="sxs-lookup"><span data-stu-id="0329e-198">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="0329e-199">İşlecinde `~` ' Contains ' semantiği var ve gibi `DisplayName`dize özellikleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0329e-199">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="0329e-200">Parantez `()` alt ifadeleri gruplandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0329e-200">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="0329e-201">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="0329e-201">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="0329e-202">Test sonuçları için bir günlükçü belirtin.</span><span class="sxs-lookup"><span data-stu-id="0329e-202">Specify a logger for test results.</span></span>

* <span data-ttu-id="0329e-203">Team Foundation Server için test sonuçlarını yayınlamak için `TfsPublisher` günlükçü sağlayıcısını kullanın:</span><span class="sxs-lookup"><span data-stu-id="0329e-203">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```console
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="0329e-204">Sonuçları bir Visual Studio test sonuçları dosyasına (trx) kaydetmek için `trx` günlükçü sağlayıcısını kullanın.</span><span class="sxs-lookup"><span data-stu-id="0329e-204">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="0329e-205">Bu anahtar, test sonuçları dizininde verilen günlük dosyası adına sahip bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0329e-205">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="0329e-206">`LogFileName` Sağlanmazsa, test sonuçlarını tutmak için benzersiz bir dosya adı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0329e-206">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```console
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="0329e-207">Verilen test kapsayıcısından tüm bulunan testleri listeler.</span><span class="sxs-lookup"><span data-stu-id="0329e-207">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="0329e-208">Geçerli işlemin başlatmasından sorumlu olan üst işlemin işlem KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="0329e-208">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="0329e-209">Yuva bağlantısı ve olay iletilerini alma bağlantı noktasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0329e-209">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="0329e-210">Test platformu için ayrıntılı günlükleri etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="0329e-210">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="0329e-211">Günlükler, belirtilen dosyaya yazılır.</span><span class="sxs-lookup"><span data-stu-id="0329e-211">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="0329e-212">Bağdaştırıcıya geçirilecek ek bağımsız değişkenleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="0329e-212">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="0329e-213">Bağımsız değişkenler, formun `<n>=<v>`ad-değer çiftleri olarak belirtilir, burada `<n>` bağımsız değişken adıdır ve `<v>` bağımsız değişken değeridir.</span><span class="sxs-lookup"><span data-stu-id="0329e-213">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="0329e-214">Birden çok bağımsız değişkeni ayırmak için boşluk kullanın.</span><span class="sxs-lookup"><span data-stu-id="0329e-214">Use a space to separate multiple arguments.</span></span>

---

## <a name="examples"></a><span data-ttu-id="0329e-215">Örnekler</span><span class="sxs-lookup"><span data-stu-id="0329e-215">Examples</span></span>

<span data-ttu-id="0329e-216">Testleri `mytestproject.dll`çalıştırma:</span><span class="sxs-lookup"><span data-stu-id="0329e-216">Run tests in `mytestproject.dll`:</span></span>

`dotnet vstest mytestproject.dll`

<span data-ttu-id="0329e-217">Özel adla özel `mytestproject.dll`klasöre dışarı aktarmak için içindeki testleri çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="0329e-217">Run tests in `mytestproject.dll`, exporting to custom folder with custom name:</span></span>

`dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path`

<span data-ttu-id="0329e-218">Testleri ve `mytestproject.dll` `myothertestproject.exe`içinde çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="0329e-218">Run tests in `mytestproject.dll` and `myothertestproject.exe`:</span></span>

`dotnet vstest mytestproject.dll myothertestproject.exe`

<span data-ttu-id="0329e-219">Testleri `TestMethod1` Çalıştır:</span><span class="sxs-lookup"><span data-stu-id="0329e-219">Run `TestMethod1` tests:</span></span>

`dotnet vstest /Tests:TestMethod1`

<span data-ttu-id="0329e-220">Çalıştır `TestMethod1` ve`TestMethod2` testler:</span><span class="sxs-lookup"><span data-stu-id="0329e-220">Run `TestMethod1` and `TestMethod2` tests:</span></span>

`dotnet vstest /Tests:TestMethod1,TestMethod2`
