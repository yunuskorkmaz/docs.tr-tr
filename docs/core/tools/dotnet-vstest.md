---
title: DotNet vstest command - .NET Core CLI
description: Dotnet vstest komutu bir proje ve tüm bağımlılıkları oluşturur.
author: guardrex
ms.author: mairaw
ms.date: 05/30/2018
ms.openlocfilehash: 84b9d9eebfbf20fefe8153dd3ae9bec0f34986c8
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696344"
---
# <a name="dotnet-vstest"></a><span data-ttu-id="9d622-103">DotNet vstest</span><span class="sxs-lookup"><span data-stu-id="9d622-103">dotnet vstest</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="9d622-104">Ad</span><span class="sxs-lookup"><span data-stu-id="9d622-104">Name</span></span>

<span data-ttu-id="9d622-105">`dotnet-vstest` -Belirtilen dosyalarından testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="9d622-105">`dotnet-vstest` - Runs tests from the specified files.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9d622-106">Özet</span><span class="sxs-lookup"><span data-stu-id="9d622-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="9d622-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="9d622-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [--Blame|/Blame] [--InIsolation|/InIsolation]
    [[--] <args>...]] [-?|--Help|/?|/Help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="9d622-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="9d622-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath] 
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="9d622-109">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="9d622-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger] 
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```
---

## <a name="description"></a><span data-ttu-id="9d622-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9d622-110">Description</span></span>

<span data-ttu-id="9d622-111">`dotnet-vstest` Komutu çalıştırır `VSTest.Console` çalıştırmak için komut satırı uygulaması birim otomatik ve kodlanmış UI uygulama testleri.</span><span class="sxs-lookup"><span data-stu-id="9d622-111">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit and coded UI application tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="9d622-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="9d622-112">Arguments</span></span>

`TEST_FILE_NAMES`

<span data-ttu-id="9d622-113">Belirtilen derlemelerden testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9d622-113">Run tests from the specified assemblies.</span></span> <span data-ttu-id="9d622-114">Birden çok test derleme adlarının boşlukla ayırın.</span><span class="sxs-lookup"><span data-stu-id="9d622-114">Separate multiple test assembly names with spaces.</span></span>

## <a name="options"></a><span data-ttu-id="9d622-115">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="9d622-115">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="9d622-116">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="9d622-116">.NET Core 2.1</span></span>](#tab/netcore21)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="9d622-117">Testleri çalıştırırken kullanılacak ayarları.</span><span class="sxs-lookup"><span data-stu-id="9d622-117">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="9d622-118">Sağlanan değerlerle eşleşen adlarıyla testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9d622-118">Run tests with names that match the provided values.</span></span> <span data-ttu-id="9d622-119">Birden çok değeri virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="9d622-119">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="9d622-120">Belirli bir yol özel test bağdaştırıcılarından test çalışması (varsa) kullanın.</span><span class="sxs-lookup"><span data-stu-id="9d622-120">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="9d622-121">Hedef platform mimarisi test yürütmesi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9d622-121">Target platform architecture used for test execution.</span></span> <span data-ttu-id="9d622-122">Geçerli değerler `x86`, `x64`, ve `ARM`.</span><span class="sxs-lookup"><span data-stu-id="9d622-122">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="9d622-123">Hedef .NET Framework sürümü test yürütmesi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9d622-123">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="9d622-124">Geçerli değerler örnekleri `.NETFramework,Version=v4.6` veya `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="9d622-124">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="9d622-125">Desteklenen diğer değerler `Framework35`, `Framework40`, `Framework45`, `FrameworkCore10`, ve `FrameworkUap10`.</span><span class="sxs-lookup"><span data-stu-id="9d622-125">Other supported values are `Framework35`, `Framework40`, `Framework45`, `FrameworkCore10`, and `FrameworkUap10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="9d622-126">Testler paralel olarak yürütün.</span><span class="sxs-lookup"><span data-stu-id="9d622-126">Execute tests in parallel.</span></span> <span data-ttu-id="9d622-127">Varsayılan olarak, tüm kullanılabilir çekirdekler makinede kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9d622-127">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="9d622-128">Açık bir çekirdek sayısı ayarlar dosyasıyla ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9d622-128">Set an explicit number of cores with a settings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="9d622-129">Verilen ifade eşleşen testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9d622-129">Run tests that match the given expression.</span></span> <span data-ttu-id="9d622-130">`<Expression>` biçimi `<property>Operator<value>[|&<Expression>]`, işleci biri burada `=`, `!=`, veya `~`.</span><span class="sxs-lookup"><span data-stu-id="9d622-130">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="9d622-131">İşleç `~` 'içeren' anlamsallarını sahiptir ve gibi dize özellikleri için geçerlidir `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="9d622-131">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="9d622-132">Parantez `()` alt ifadeleri gruplamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9d622-132">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="9d622-133">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="9d622-133">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="9d622-134">Test sonuçları için Günlükçü belirtin.</span><span class="sxs-lookup"><span data-stu-id="9d622-134">Specify a logger for test results.</span></span>

* <span data-ttu-id="9d622-135">Team Foundation Server için test sonuçlarını yayımlamak için kullanmak `TfsPublisher` Günlükçü sağlayıcısı:</span><span class="sxs-lookup"><span data-stu-id="9d622-135">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="9d622-136">Sonuçları bir Visual Studio Test sonuçları dosyası (TRX) için oturum açmak için kullandığınız `trx` Günlükçü sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="9d622-136">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="9d622-137">Bu anahtarı bir dosya olarak test sonuçlarını oluşturur. günlük dosyası adı verilen ile dizin.</span><span class="sxs-lookup"><span data-stu-id="9d622-137">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="9d622-138">Varsa `LogFileName` test sonuçlarını tutmak için benzersiz bir dosya adı oluşturulan sağlanan değil.</span><span class="sxs-lookup"><span data-stu-id="9d622-138">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="9d622-139">Belirli test kapsayıcısı bulunan tüm testleri listeler.</span><span class="sxs-lookup"><span data-stu-id="9d622-139">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="9d622-140">Geçerli işlem başlatmaktan sorumlu üst işlemin işlem kimliği.</span><span class="sxs-lookup"><span data-stu-id="9d622-140">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="9d622-141">Yuva bağlantısı ve olay iletileri almak için bağlantı noktasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9d622-141">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="9d622-142">Ayrıntılı günlükleri test Platform sağlar.</span><span class="sxs-lookup"><span data-stu-id="9d622-142">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="9d622-143">Günlükleri sağlanan dosyasına yazılır.</span><span class="sxs-lookup"><span data-stu-id="9d622-143">Logs are written to the provided file.</span></span>

`--Blame|/Blame`

<span data-ttu-id="9d622-144">Testleri nedenlerle modunda çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="9d622-144">Runs the tests in blame mode.</span></span> <span data-ttu-id="9d622-145">Bu seçenek test ana çökmesine neden sorunlu testleri yalıtmaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="9d622-145">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="9d622-146">Bir çıktı dosyası geçerli dizinde oluşturur *Sequence.xml* kilitlenme önce testleri yürütme sırasını yakalar.</span><span class="sxs-lookup"><span data-stu-id="9d622-146">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`--InIsolation|/InIsolation`

<span data-ttu-id="9d622-147">Testleri yalıtılmış bir işlem içinde çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="9d622-147">Runs the tests in an isolated process.</span></span> <span data-ttu-id="9d622-148">Böylece *vstest.console.exe* bir hata testlerinde durdurulacak büyük olasılıkla daha az işlem ancak testleri daha yavaş çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="9d622-148">This makes *vstest.console.exe* process less likely to be stopped on an error in the tests, but tests may run slower.</span></span>

`@<file>`

<span data-ttu-id="9d622-149">Daha fazla seçenek için yanıt dosyasını okur.</span><span class="sxs-lookup"><span data-stu-id="9d622-149">Reads response file for more options.</span></span>


`args`

<span data-ttu-id="9d622-150">Bağdaştırıcıya geçirmek için ek bağımsız değişkenlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9d622-150">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="9d622-151">Bağımsız değişkenler formun ad-değer çiftleri olarak belirtilen `<n>=<v>`, burada `<n>` bağımsız değişkeni adı ve `<v>` bağımsız değişken değeri.</span><span class="sxs-lookup"><span data-stu-id="9d622-151">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="9d622-152">Birden çok bağımsız değişkenleri ayırmak için boşluk kullanın.</span><span class="sxs-lookup"><span data-stu-id="9d622-152">Use a space to separate multiple arguments.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="9d622-153">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="9d622-153">.NET Core 2.0</span></span>](#tab/netcore20)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="9d622-154">Testleri çalıştırırken kullanılacak ayarları.</span><span class="sxs-lookup"><span data-stu-id="9d622-154">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="9d622-155">Sağlanan değerlerle eşleşen adlarıyla testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9d622-155">Run tests with names that match the provided values.</span></span> <span data-ttu-id="9d622-156">Birden çok değeri virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="9d622-156">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="9d622-157">Belirli bir yol özel test bağdaştırıcılarından test çalışması (varsa) kullanın.</span><span class="sxs-lookup"><span data-stu-id="9d622-157">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="9d622-158">Hedef platform mimarisi test yürütmesi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9d622-158">Target platform architecture used for test execution.</span></span> <span data-ttu-id="9d622-159">Geçerli değerler `x86`, `x64`, ve `ARM`.</span><span class="sxs-lookup"><span data-stu-id="9d622-159">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="9d622-160">Hedef .NET Framework sürümü test yürütmesi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9d622-160">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="9d622-161">Geçerli değerler örnekleri `.NETFramework,Version=v4.6` veya `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="9d622-161">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="9d622-162">Desteklenen diğer değerler `Framework35`, `Framework40`, `Framework45`, ve `FrameworkCore10`.</span><span class="sxs-lookup"><span data-stu-id="9d622-162">Other supported values are `Framework35`, `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="9d622-163">Testler paralel olarak yürütün.</span><span class="sxs-lookup"><span data-stu-id="9d622-163">Execute tests in parallel.</span></span> <span data-ttu-id="9d622-164">Varsayılan olarak, tüm kullanılabilir çekirdekler makinede kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9d622-164">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="9d622-165">Açık bir çekirdek sayısı ayarlar dosyasıyla ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9d622-165">Set an explicit number of cores with a settings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="9d622-166">Verilen ifade eşleşen testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9d622-166">Run tests that match the given expression.</span></span> <span data-ttu-id="9d622-167">`<Expression>` biçimi `<property>Operator<value>[|&<Expression>]`, işleci biri burada `=`, `!=`, veya `~`.</span><span class="sxs-lookup"><span data-stu-id="9d622-167">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="9d622-168">İşleç `~` 'içeren' anlamsallarını sahiptir ve gibi dize özellikleri için geçerlidir `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="9d622-168">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="9d622-169">Parantez `()` alt ifadeleri gruplamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9d622-169">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="9d622-170">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="9d622-170">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="9d622-171">Test sonuçları için Günlükçü belirtin.</span><span class="sxs-lookup"><span data-stu-id="9d622-171">Specify a logger for test results.</span></span>

* <span data-ttu-id="9d622-172">Team Foundation Server için test sonuçlarını yayımlamak için kullanmak `TfsPublisher` Günlükçü sağlayıcısı:</span><span class="sxs-lookup"><span data-stu-id="9d622-172">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="9d622-173">Sonuçları bir Visual Studio Test sonuçları dosyası (TRX) için oturum açmak için kullandığınız `trx` Günlükçü sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="9d622-173">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="9d622-174">Bu anahtarı bir dosya olarak test sonuçlarını oluşturur. günlük dosyası adı verilen ile dizin.</span><span class="sxs-lookup"><span data-stu-id="9d622-174">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="9d622-175">Varsa `LogFileName` test sonuçlarını tutmak için benzersiz bir dosya adı oluşturulan sağlanan değil.</span><span class="sxs-lookup"><span data-stu-id="9d622-175">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="9d622-176">Belirli test kapsayıcısı bulunan tüm testleri listeler.</span><span class="sxs-lookup"><span data-stu-id="9d622-176">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="9d622-177">Geçerli işlem başlatmaktan sorumlu üst işlemin işlem kimliği.</span><span class="sxs-lookup"><span data-stu-id="9d622-177">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="9d622-178">Yuva bağlantısı ve olay iletileri almak için bağlantı noktasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9d622-178">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="9d622-179">Ayrıntılı günlükleri test Platform sağlar.</span><span class="sxs-lookup"><span data-stu-id="9d622-179">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="9d622-180">Günlükleri sağlanan dosyasına yazılır.</span><span class="sxs-lookup"><span data-stu-id="9d622-180">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="9d622-181">Bağdaştırıcıya geçirmek için ek bağımsız değişkenlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9d622-181">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="9d622-182">Bağımsız değişkenler formun ad-değer çiftleri olarak belirtilen `<n>=<v>`, burada `<n>` bağımsız değişkeni adı ve `<v>` bağımsız değişken değeri.</span><span class="sxs-lookup"><span data-stu-id="9d622-182">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="9d622-183">Birden çok bağımsız değişkenleri ayırmak için boşluk kullanın.</span><span class="sxs-lookup"><span data-stu-id="9d622-183">Use a space to separate multiple arguments.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="9d622-184">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="9d622-184">.NET Core 1.x</span></span>](#tab/netcore1x)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="9d622-185">Testleri çalıştırırken kullanılacak ayarları.</span><span class="sxs-lookup"><span data-stu-id="9d622-185">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="9d622-186">Sağlanan değerlerle eşleşen adlarıyla testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9d622-186">Run tests with names that match the provided values.</span></span> <span data-ttu-id="9d622-187">Birden çok değeri virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="9d622-187">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="9d622-188">Belirli bir yol özel test bağdaştırıcılarından test çalışması (varsa) kullanın.</span><span class="sxs-lookup"><span data-stu-id="9d622-188">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="9d622-189">Hedef platform mimarisi test yürütmesi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9d622-189">Target platform architecture used for test execution.</span></span> <span data-ttu-id="9d622-190">Geçerli değerler `x86`, `x64`, ve `ARM`.</span><span class="sxs-lookup"><span data-stu-id="9d622-190">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="9d622-191">Hedef .NET Framework sürümü test yürütmesi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9d622-191">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="9d622-192">Geçerli değerler örnekleri `.NETFramework,Version=v4.6` veya `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="9d622-192">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="9d622-193">Desteklenen diğer değerler `Framework35`, `Framework40`, `Framework45`, ve `FrameworkCore10`.</span><span class="sxs-lookup"><span data-stu-id="9d622-193">Other supported values are `Framework35`, `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="9d622-194">Testler paralel olarak yürütün.</span><span class="sxs-lookup"><span data-stu-id="9d622-194">Execute tests in parallel.</span></span> <span data-ttu-id="9d622-195">Varsayılan olarak, tüm kullanılabilir çekirdekler makinede kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9d622-195">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="9d622-196">Açık bir çekirdek sayısı ayarlar dosyasıyla ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9d622-196">Set an explicit number of cores with a settings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="9d622-197">Verilen ifade eşleşen testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9d622-197">Run tests that match the given expression.</span></span> <span data-ttu-id="9d622-198">`<Expression>` biçimi `<property>Operator<value>[|&<Expression>]`, işleci biri burada `=`, `!=`, veya `~`.</span><span class="sxs-lookup"><span data-stu-id="9d622-198">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="9d622-199">İşleç `~` 'içeren' anlamsallarını sahiptir ve gibi dize özellikleri için geçerlidir `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="9d622-199">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="9d622-200">Parantez `()` alt ifadeleri gruplamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9d622-200">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="9d622-201">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="9d622-201">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="9d622-202">Test sonuçları için Günlükçü belirtin.</span><span class="sxs-lookup"><span data-stu-id="9d622-202">Specify a logger for test results.</span></span>

* <span data-ttu-id="9d622-203">Team Foundation Server için test sonuçlarını yayımlamak için kullanmak `TfsPublisher` Günlükçü sağlayıcısı:</span><span class="sxs-lookup"><span data-stu-id="9d622-203">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="9d622-204">Sonuçları bir Visual Studio Test sonuçları dosyası (TRX) için oturum açmak için kullandığınız `trx` Günlükçü sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="9d622-204">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="9d622-205">Bu anahtarı bir dosya olarak test sonuçlarını oluşturur. günlük dosyası adı verilen ile dizin.</span><span class="sxs-lookup"><span data-stu-id="9d622-205">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="9d622-206">Varsa `LogFileName` test sonuçlarını tutmak için benzersiz bir dosya adı oluşturulan sağlanan değil.</span><span class="sxs-lookup"><span data-stu-id="9d622-206">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="9d622-207">Belirli test kapsayıcısı bulunan tüm testleri listeler.</span><span class="sxs-lookup"><span data-stu-id="9d622-207">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="9d622-208">Geçerli işlem başlatmaktan sorumlu üst işlemin işlem kimliği.</span><span class="sxs-lookup"><span data-stu-id="9d622-208">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="9d622-209">Yuva bağlantısı ve olay iletileri almak için bağlantı noktasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9d622-209">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="9d622-210">Ayrıntılı günlükleri test Platform sağlar.</span><span class="sxs-lookup"><span data-stu-id="9d622-210">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="9d622-211">Günlükleri sağlanan dosyasına yazılır.</span><span class="sxs-lookup"><span data-stu-id="9d622-211">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="9d622-212">Bağdaştırıcıya geçirmek için ek bağımsız değişkenlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9d622-212">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="9d622-213">Bağımsız değişkenler formun ad-değer çiftleri olarak belirtilen `<n>=<v>`, burada `<n>` bağımsız değişkeni adı ve `<v>` bağımsız değişken değeri.</span><span class="sxs-lookup"><span data-stu-id="9d622-213">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="9d622-214">Birden çok bağımsız değişkenleri ayırmak için boşluk kullanın.</span><span class="sxs-lookup"><span data-stu-id="9d622-214">Use a space to separate multiple arguments.</span></span>

---

## <a name="examples"></a><span data-ttu-id="9d622-215">Örnekler</span><span class="sxs-lookup"><span data-stu-id="9d622-215">Examples</span></span>

<span data-ttu-id="9d622-216">Testleri çalıştırmak `mytestproject.dll`:</span><span class="sxs-lookup"><span data-stu-id="9d622-216">Run tests in `mytestproject.dll`:</span></span>

`dotnet vstest mytestproject.dll`

<span data-ttu-id="9d622-217">Testleri çalıştırmak `mytestproject.dll`, özel adda özel klasör verme:</span><span class="sxs-lookup"><span data-stu-id="9d622-217">Run tests in `mytestproject.dll`, exporting to custom folder with custom name:</span></span>

`dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path`

<span data-ttu-id="9d622-218">Testleri çalıştırmak `mytestproject.dll` ve `myothertestproject.exe`:</span><span class="sxs-lookup"><span data-stu-id="9d622-218">Run tests in `mytestproject.dll` and `myothertestproject.exe`:</span></span>

`dotnet vstest mytestproject.dll myothertestproject.exe`

<span data-ttu-id="9d622-219">Çalıştırma `TestMethod1` testler:</span><span class="sxs-lookup"><span data-stu-id="9d622-219">Run `TestMethod1` tests:</span></span>

`dotnet vstest /Tests:TestMethod1`

<span data-ttu-id="9d622-220">Çalıştırma `TestMethod1` ve `TestMethod2` testleri:</span><span class="sxs-lookup"><span data-stu-id="9d622-220">Run `TestMethod1` and `TestMethod2` tests:</span></span>

`dotnet vstest /Tests:TestMethod1,TestMethod2`