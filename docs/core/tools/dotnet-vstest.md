---
title: DotNet vstest komutu
description: Dotnet vstest komutu, bir projeyi ve tüm bağımlılıklarını oluşturur.
author: mairaw
ms.date: 05/30/2018
ms.openlocfilehash: 45fda3b34d2649bc6f20cf3f35c65277a9a53cec
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300040"
---
# <a name="dotnet-vstest"></a><span data-ttu-id="70fc5-103">dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="70fc5-103">dotnet vstest</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="70fc5-104">Ad</span><span class="sxs-lookup"><span data-stu-id="70fc5-104">Name</span></span>

<span data-ttu-id="70fc5-105">`dotnet-vstest` -Belirtilen dosyalardan testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="70fc5-105">`dotnet-vstest` - Runs tests from the specified files.</span></span>

## <a name="synopsis"></a><span data-ttu-id="70fc5-106">Synopsis</span><span class="sxs-lookup"><span data-stu-id="70fc5-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="70fc5-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="70fc5-107">.NET Core 2.1</span></span>](#tab/netcore21)

```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [--Blame|/Blame] [--InIsolation|/InIsolation]
    [[--] <args>...]] [-?|--Help|/?|/Help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="70fc5-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="70fc5-108">.NET Core 2.0</span></span>](#tab/netcore20)

```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath] 
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="70fc5-109">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="70fc5-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger] 
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```

---

## <a name="description"></a><span data-ttu-id="70fc5-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="70fc5-110">Description</span></span>

<span data-ttu-id="70fc5-111">`dotnet-vstest` Komutu çalıştırmaları `VSTest.Console` otomatik birim testleri çalıştırmak için komut satırı uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="70fc5-111">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="70fc5-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="70fc5-112">Arguments</span></span>

`TEST_FILE_NAMES`

<span data-ttu-id="70fc5-113">Belirtilen derlemelerden testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="70fc5-113">Run tests from the specified assemblies.</span></span> <span data-ttu-id="70fc5-114">Birden çok test derleme adlarının boşluklarla ayırın.</span><span class="sxs-lookup"><span data-stu-id="70fc5-114">Separate multiple test assembly names with spaces.</span></span>

## <a name="options"></a><span data-ttu-id="70fc5-115">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="70fc5-115">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="70fc5-116">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="70fc5-116">.NET Core 2.1</span></span>](#tab/netcore21)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="70fc5-117">Testleri çalıştırırken kullanılacak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="70fc5-117">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="70fc5-118">Testleri sağlanan değerlerle eşleşen adlarla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="70fc5-118">Run tests with names that match the provided values.</span></span> <span data-ttu-id="70fc5-119">Birden çok değer virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="70fc5-119">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="70fc5-120">Özel test bağdaştırıcılarını verilen yoldan (varsa) test çalıştırmasında kullanın.</span><span class="sxs-lookup"><span data-stu-id="70fc5-120">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="70fc5-121">Hedef platform mimarisi, test yürütmesi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="70fc5-121">Target platform architecture used for test execution.</span></span> <span data-ttu-id="70fc5-122">Geçerli değerler `x86`, `x64`, ve `ARM`.</span><span class="sxs-lookup"><span data-stu-id="70fc5-122">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="70fc5-123">Test çalıştırması için kullanılan hedef .NET Framework sürümü.</span><span class="sxs-lookup"><span data-stu-id="70fc5-123">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="70fc5-124">Geçerli değerler örnekler `.NETFramework,Version=v4.6` veya `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="70fc5-124">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="70fc5-125">Desteklenen diğer değerler `Framework40`, `Framework45`, `FrameworkCore10`, ve `FrameworkUap10`.</span><span class="sxs-lookup"><span data-stu-id="70fc5-125">Other supported values are `Framework40`, `Framework45`, `FrameworkCore10`, and `FrameworkUap10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="70fc5-126">Testleri paralel olarak yürütür.</span><span class="sxs-lookup"><span data-stu-id="70fc5-126">Execute tests in parallel.</span></span> <span data-ttu-id="70fc5-127">Varsayılan olarak, makinedeki tüm mevcut çekirdekler kullanılabilir duruma gelir.</span><span class="sxs-lookup"><span data-stu-id="70fc5-127">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="70fc5-128">Runsettings dosyasında RunConfiguration düğümü altındaki MaxCpuCount özelliği ayarlayarak açık bir çekirdek sayısını belirtin.</span><span class="sxs-lookup"><span data-stu-id="70fc5-128">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="70fc5-129">Verili ifadeyle eşleşen testler çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="70fc5-129">Run tests that match the given expression.</span></span> <span data-ttu-id="70fc5-130">`<Expression>` biçimi `<property>Operator<value>[|&<Expression>]`, burada işleç birini `=`, `!=`, veya `~`.</span><span class="sxs-lookup"><span data-stu-id="70fc5-130">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="70fc5-131">İşleç `~` gibi dize özellikleri için geçerlidir ve 'contains' semantiğe sahip `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="70fc5-131">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="70fc5-132">Parantez `()` alt ifadeleri gruplamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="70fc5-132">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="70fc5-133">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="70fc5-133">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="70fc5-134">Test sonuçları için bir Günlükçü belirtin.</span><span class="sxs-lookup"><span data-stu-id="70fc5-134">Specify a logger for test results.</span></span>

* <span data-ttu-id="70fc5-135">Team Foundation Server test sonuçlarını yayımlamak için kullanmak `TfsPublisher` Günlükçü sağlayıcısı:</span><span class="sxs-lookup"><span data-stu-id="70fc5-135">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="70fc5-136">Bir Visual Studio Test sonuçları dosyası (TRX) için sonuçlar'ı açmak için kullandığınız `trx` Günlükçü sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="70fc5-136">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="70fc5-137">Bu anahtar test sonuçlarında bir dosya oluşturur. günlük dosyası adı verilen ile dizin.</span><span class="sxs-lookup"><span data-stu-id="70fc5-137">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="70fc5-138">Varsa `LogFileName` test sonuçlarını tutmak için benzersiz bir dosya adı oluşturan koşuluyla değil.</span><span class="sxs-lookup"><span data-stu-id="70fc5-138">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="70fc5-139">Tüm, verili test kapsayıcısından bulunan testleri listeler.</span><span class="sxs-lookup"><span data-stu-id="70fc5-139">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="70fc5-140">Geçerli işlem başlatmaktan sorumlu üst işlemin işlem kimliği.</span><span class="sxs-lookup"><span data-stu-id="70fc5-140">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="70fc5-141">Yuva bağlantısı ve olay iletileri almak için bir bağlantı noktasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="70fc5-141">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="70fc5-142">Ayrıntılı günlükler için test platformu sağlar.</span><span class="sxs-lookup"><span data-stu-id="70fc5-142">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="70fc5-143">Günlükleri, belirtilen dosyaya yazılır.</span><span class="sxs-lookup"><span data-stu-id="70fc5-143">Logs are written to the provided file.</span></span>

`--Blame|/Blame`

<span data-ttu-id="70fc5-144">Testleri sorumluyu modunda çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="70fc5-144">Runs the tests in blame mode.</span></span> <span data-ttu-id="70fc5-145">Bu seçenek, sorunlu testleri test ana bilgisayarı kilitlenmesine neden olan sorunları ayırmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="70fc5-145">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="70fc5-146">Bir çıkış dosyası geçerli dizinde oluşturur *Sequence.xml* , kilitlenme önce testler yürütme sırası yakalar.</span><span class="sxs-lookup"><span data-stu-id="70fc5-146">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`--InIsolation|/InIsolation`

<span data-ttu-id="70fc5-147">Testleri yalıtılmış bir işlemde çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="70fc5-147">Runs the tests in an isolated process.</span></span> <span data-ttu-id="70fc5-148">Böylece *vstest.console.exe* büyük olasılıkla daha az bir hata sırasında durdurulması işlemi, ancak testleri daha yavaş çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="70fc5-148">This makes *vstest.console.exe* process less likely to be stopped on an error in the tests, but tests may run slower.</span></span>

`@<file>`

<span data-ttu-id="70fc5-149">Daha fazla seçenek için yanıt dosyasını okur.</span><span class="sxs-lookup"><span data-stu-id="70fc5-149">Reads response file for more options.</span></span>

`args`

<span data-ttu-id="70fc5-150">Bağdaştırıcıya geçirilecek ek bağımsız değişkenleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="70fc5-150">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="70fc5-151">Bağımsız değişkenler formun ad-değer çiftleri olarak belirtilen `<n>=<v>`burada `<n>` bağımsız değişken adıdır ve `<v>` bağımsız değişken değeri.</span><span class="sxs-lookup"><span data-stu-id="70fc5-151">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="70fc5-152">Birden çok bağımsız değişkeni ayırmak için boşluk kullanın.</span><span class="sxs-lookup"><span data-stu-id="70fc5-152">Use a space to separate multiple arguments.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="70fc5-153">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="70fc5-153">.NET Core 2.0</span></span>](#tab/netcore20)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="70fc5-154">Testleri çalıştırırken kullanılacak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="70fc5-154">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="70fc5-155">Testleri sağlanan değerlerle eşleşen adlarla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="70fc5-155">Run tests with names that match the provided values.</span></span> <span data-ttu-id="70fc5-156">Birden çok değer virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="70fc5-156">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="70fc5-157">Özel test bağdaştırıcılarını verilen yoldan (varsa) test çalıştırmasında kullanın.</span><span class="sxs-lookup"><span data-stu-id="70fc5-157">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="70fc5-158">Hedef platform mimarisi, test yürütmesi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="70fc5-158">Target platform architecture used for test execution.</span></span> <span data-ttu-id="70fc5-159">Geçerli değerler `x86`, `x64`, ve `ARM`.</span><span class="sxs-lookup"><span data-stu-id="70fc5-159">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="70fc5-160">Test çalıştırması için kullanılan hedef .NET Framework sürümü.</span><span class="sxs-lookup"><span data-stu-id="70fc5-160">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="70fc5-161">Geçerli değerler örnekler `.NETFramework,Version=v4.6` veya `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="70fc5-161">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="70fc5-162">Desteklenen diğer değerler `Framework40`, `Framework45`, ve `FrameworkCore10`.</span><span class="sxs-lookup"><span data-stu-id="70fc5-162">Other supported values are `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="70fc5-163">Testleri paralel olarak yürütür.</span><span class="sxs-lookup"><span data-stu-id="70fc5-163">Execute tests in parallel.</span></span> <span data-ttu-id="70fc5-164">Varsayılan olarak, makinedeki tüm mevcut çekirdekler kullanılabilir duruma gelir.</span><span class="sxs-lookup"><span data-stu-id="70fc5-164">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="70fc5-165">Runsettings dosyasında RunConfiguration düğümü altındaki MaxCpuCount özelliği ayarlayarak açık bir çekirdek sayısını belirtin.</span><span class="sxs-lookup"><span data-stu-id="70fc5-165">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="70fc5-166">Verili ifadeyle eşleşen testler çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="70fc5-166">Run tests that match the given expression.</span></span> <span data-ttu-id="70fc5-167">`<Expression>` biçimi `<property>Operator<value>[|&<Expression>]`, burada işleç birini `=`, `!=`, veya `~`.</span><span class="sxs-lookup"><span data-stu-id="70fc5-167">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="70fc5-168">İşleç `~` gibi dize özellikleri için geçerlidir ve 'contains' semantiğe sahip `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="70fc5-168">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="70fc5-169">Parantez `()` alt ifadeleri gruplamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="70fc5-169">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="70fc5-170">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="70fc5-170">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="70fc5-171">Test sonuçları için bir Günlükçü belirtin.</span><span class="sxs-lookup"><span data-stu-id="70fc5-171">Specify a logger for test results.</span></span>

* <span data-ttu-id="70fc5-172">Team Foundation Server test sonuçlarını yayımlamak için kullanmak `TfsPublisher` Günlükçü sağlayıcısı:</span><span class="sxs-lookup"><span data-stu-id="70fc5-172">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="70fc5-173">Bir Visual Studio Test sonuçları dosyası (TRX) için sonuçlar'ı açmak için kullandığınız `trx` Günlükçü sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="70fc5-173">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="70fc5-174">Bu anahtar test sonuçlarında bir dosya oluşturur. günlük dosyası adı verilen ile dizin.</span><span class="sxs-lookup"><span data-stu-id="70fc5-174">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="70fc5-175">Varsa `LogFileName` test sonuçlarını tutmak için benzersiz bir dosya adı oluşturan koşuluyla değil.</span><span class="sxs-lookup"><span data-stu-id="70fc5-175">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="70fc5-176">Tüm, verili test kapsayıcısından bulunan testleri listeler.</span><span class="sxs-lookup"><span data-stu-id="70fc5-176">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="70fc5-177">Geçerli işlem başlatmaktan sorumlu üst işlemin işlem kimliği.</span><span class="sxs-lookup"><span data-stu-id="70fc5-177">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="70fc5-178">Yuva bağlantısı ve olay iletileri almak için bir bağlantı noktasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="70fc5-178">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="70fc5-179">Ayrıntılı günlükler için test platformu sağlar.</span><span class="sxs-lookup"><span data-stu-id="70fc5-179">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="70fc5-180">Günlükleri, belirtilen dosyaya yazılır.</span><span class="sxs-lookup"><span data-stu-id="70fc5-180">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="70fc5-181">Bağdaştırıcıya geçirilecek ek bağımsız değişkenleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="70fc5-181">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="70fc5-182">Bağımsız değişkenler formun ad-değer çiftleri olarak belirtilen `<n>=<v>`burada `<n>` bağımsız değişken adıdır ve `<v>` bağımsız değişken değeri.</span><span class="sxs-lookup"><span data-stu-id="70fc5-182">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="70fc5-183">Birden çok bağımsız değişkeni ayırmak için boşluk kullanın.</span><span class="sxs-lookup"><span data-stu-id="70fc5-183">Use a space to separate multiple arguments.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="70fc5-184">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="70fc5-184">.NET Core 1.x</span></span>](#tab/netcore1x)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="70fc5-185">Testleri çalıştırırken kullanılacak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="70fc5-185">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="70fc5-186">Testleri sağlanan değerlerle eşleşen adlarla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="70fc5-186">Run tests with names that match the provided values.</span></span> <span data-ttu-id="70fc5-187">Birden çok değer virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="70fc5-187">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="70fc5-188">Özel test bağdaştırıcılarını verilen yoldan (varsa) test çalıştırmasında kullanın.</span><span class="sxs-lookup"><span data-stu-id="70fc5-188">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="70fc5-189">Hedef platform mimarisi, test yürütmesi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="70fc5-189">Target platform architecture used for test execution.</span></span> <span data-ttu-id="70fc5-190">Geçerli değerler `x86`, `x64`, ve `ARM`.</span><span class="sxs-lookup"><span data-stu-id="70fc5-190">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="70fc5-191">Test çalıştırması için kullanılan hedef .NET Framework sürümü.</span><span class="sxs-lookup"><span data-stu-id="70fc5-191">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="70fc5-192">Geçerli değerler örnekler `.NETFramework,Version=v4.6` veya `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="70fc5-192">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="70fc5-193">Desteklenen diğer değerler `Framework40`, `Framework45`, ve `FrameworkCore10`.</span><span class="sxs-lookup"><span data-stu-id="70fc5-193">Other supported values are `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="70fc5-194">Testleri paralel olarak yürütür.</span><span class="sxs-lookup"><span data-stu-id="70fc5-194">Execute tests in parallel.</span></span> <span data-ttu-id="70fc5-195">Varsayılan olarak, makinedeki tüm mevcut çekirdekler kullanılabilir duruma gelir.</span><span class="sxs-lookup"><span data-stu-id="70fc5-195">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="70fc5-196">Runsettings dosyasında RunConfiguration düğümü altındaki MaxCpuCount özelliği ayarlayarak açık bir çekirdek sayısını belirtin.</span><span class="sxs-lookup"><span data-stu-id="70fc5-196">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="70fc5-197">Verili ifadeyle eşleşen testler çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="70fc5-197">Run tests that match the given expression.</span></span> <span data-ttu-id="70fc5-198">`<Expression>` biçimi `<property>Operator<value>[|&<Expression>]`, burada işleç birini `=`, `!=`, veya `~`.</span><span class="sxs-lookup"><span data-stu-id="70fc5-198">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="70fc5-199">İşleç `~` gibi dize özellikleri için geçerlidir ve 'contains' semantiğe sahip `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="70fc5-199">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="70fc5-200">Parantez `()` alt ifadeleri gruplamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="70fc5-200">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="70fc5-201">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="70fc5-201">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="70fc5-202">Test sonuçları için bir Günlükçü belirtin.</span><span class="sxs-lookup"><span data-stu-id="70fc5-202">Specify a logger for test results.</span></span>

* <span data-ttu-id="70fc5-203">Team Foundation Server test sonuçlarını yayımlamak için kullanmak `TfsPublisher` Günlükçü sağlayıcısı:</span><span class="sxs-lookup"><span data-stu-id="70fc5-203">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="70fc5-204">Bir Visual Studio Test sonuçları dosyası (TRX) için sonuçlar'ı açmak için kullandığınız `trx` Günlükçü sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="70fc5-204">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="70fc5-205">Bu anahtar test sonuçlarında bir dosya oluşturur. günlük dosyası adı verilen ile dizin.</span><span class="sxs-lookup"><span data-stu-id="70fc5-205">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="70fc5-206">Varsa `LogFileName` test sonuçlarını tutmak için benzersiz bir dosya adı oluşturan koşuluyla değil.</span><span class="sxs-lookup"><span data-stu-id="70fc5-206">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="70fc5-207">Tüm, verili test kapsayıcısından bulunan testleri listeler.</span><span class="sxs-lookup"><span data-stu-id="70fc5-207">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="70fc5-208">Geçerli işlem başlatmaktan sorumlu üst işlemin işlem kimliği.</span><span class="sxs-lookup"><span data-stu-id="70fc5-208">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="70fc5-209">Yuva bağlantısı ve olay iletileri almak için bir bağlantı noktasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="70fc5-209">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="70fc5-210">Ayrıntılı günlükler için test platformu sağlar.</span><span class="sxs-lookup"><span data-stu-id="70fc5-210">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="70fc5-211">Günlükleri, belirtilen dosyaya yazılır.</span><span class="sxs-lookup"><span data-stu-id="70fc5-211">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="70fc5-212">Bağdaştırıcıya geçirilecek ek bağımsız değişkenleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="70fc5-212">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="70fc5-213">Bağımsız değişkenler formun ad-değer çiftleri olarak belirtilen `<n>=<v>`burada `<n>` bağımsız değişken adıdır ve `<v>` bağımsız değişken değeri.</span><span class="sxs-lookup"><span data-stu-id="70fc5-213">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="70fc5-214">Birden çok bağımsız değişkeni ayırmak için boşluk kullanın.</span><span class="sxs-lookup"><span data-stu-id="70fc5-214">Use a space to separate multiple arguments.</span></span>

---

## <a name="examples"></a><span data-ttu-id="70fc5-215">Örnekler</span><span class="sxs-lookup"><span data-stu-id="70fc5-215">Examples</span></span>

<span data-ttu-id="70fc5-216">Testleri Çalıştır `mytestproject.dll`:</span><span class="sxs-lookup"><span data-stu-id="70fc5-216">Run tests in `mytestproject.dll`:</span></span>

`dotnet vstest mytestproject.dll`

<span data-ttu-id="70fc5-217">Testleri Çalıştır `mytestproject.dll`, dışa aktarma için özel bir ada sahip özel klasör:</span><span class="sxs-lookup"><span data-stu-id="70fc5-217">Run tests in `mytestproject.dll`, exporting to custom folder with custom name:</span></span>

`dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path`

<span data-ttu-id="70fc5-218">Testleri Çalıştır `mytestproject.dll` ve `myothertestproject.exe`:</span><span class="sxs-lookup"><span data-stu-id="70fc5-218">Run tests in `mytestproject.dll` and `myothertestproject.exe`:</span></span>

`dotnet vstest mytestproject.dll myothertestproject.exe`

<span data-ttu-id="70fc5-219">Çalıştırma `TestMethod1` testler:</span><span class="sxs-lookup"><span data-stu-id="70fc5-219">Run `TestMethod1` tests:</span></span>

`dotnet vstest /Tests:TestMethod1`

<span data-ttu-id="70fc5-220">Çalıştırma `TestMethod1` ve `TestMethod2` testler:</span><span class="sxs-lookup"><span data-stu-id="70fc5-220">Run `TestMethod1` and `TestMethod2` tests:</span></span>

`dotnet vstest /Tests:TestMethod1,TestMethod2`
