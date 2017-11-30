---
title: DotNet vstest command - .NET Core CLI
description: "Dotnet vstest komutu bir proje ve tüm bağımlılıkları oluşturur."
author: guardrex
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: c5a7ee0ba306cea641b0ff34f0b521c92bd03719
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-vstest"></a><span data-ttu-id="2623f-103">DotNet vstest</span><span class="sxs-lookup"><span data-stu-id="2623f-103">dotnet vstest</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="2623f-104">Ad</span><span class="sxs-lookup"><span data-stu-id="2623f-104">Name</span></span>

<span data-ttu-id="2623f-105">`dotnet-vstest`-Belirtilen dosyalarından testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="2623f-105">`dotnet-vstest` - Runs tests from the specified files.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2623f-106">Özet</span><span class="sxs-lookup"><span data-stu-id="2623f-106">Synopsis</span></span>

`dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath] [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger] [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]`

## <a name="description"></a><span data-ttu-id="2623f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2623f-107">Description</span></span>

<span data-ttu-id="2623f-108">`dotnet-vstest` Komutu çalıştırır `VSTest.Console` çalıştırmak için komut satırı uygulaması birim otomatik ve kodlanmış UI uygulama testleri.</span><span class="sxs-lookup"><span data-stu-id="2623f-108">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit and coded UI application tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="2623f-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="2623f-109">Arguments</span></span>

`TEST_FILE_NAMES`

<span data-ttu-id="2623f-110">Belirtilen derlemelerden testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="2623f-110">Run tests from the specified assemblies.</span></span> <span data-ttu-id="2623f-111">Birden çok test derleme adlarının boşlukla ayırın.</span><span class="sxs-lookup"><span data-stu-id="2623f-111">Separate multiple test assembly names with spaces.</span></span>

## <a name="options"></a><span data-ttu-id="2623f-112">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="2623f-112">Options</span></span>

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="2623f-113">Testleri çalıştırırken kullanılacak ayarları.</span><span class="sxs-lookup"><span data-stu-id="2623f-113">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="2623f-114">Sağlanan değerlerle eşleşen adlarıyla testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="2623f-114">Run tests with names that match the provided values.</span></span> <span data-ttu-id="2623f-115">Birden çok değeri virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="2623f-115">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="2623f-116">Belirli bir yol özel test bağdaştırıcılarından test çalışması (varsa) kullanın.</span><span class="sxs-lookup"><span data-stu-id="2623f-116">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="2623f-117">Hedef platform mimarisi test yürütmesi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2623f-117">Target platform architecture used for test execution.</span></span> <span data-ttu-id="2623f-118">Geçerli değerler `x86`, `x64`, ve `ARM`.</span><span class="sxs-lookup"><span data-stu-id="2623f-118">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="2623f-119">Hedef .NET Framework sürümü test yürütmesi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2623f-119">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="2623f-120">Geçerli değerler örnekleri `.NETFramework,Version=v4.6`, `.NETCoreApp,Version=v1.0`vb. Desteklenen diğer değerler `Framework35`, `Framework40`, `Framework45`, ve `FrameworkCore10`.</span><span class="sxs-lookup"><span data-stu-id="2623f-120">Examples of valid values are `.NETFramework,Version=v4.6`, `.NETCoreApp,Version=v1.0`, etc. Other supported values are `Framework35`, `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="2623f-121">Testler paralel olarak yürütün.</span><span class="sxs-lookup"><span data-stu-id="2623f-121">Execute tests in parallel.</span></span> <span data-ttu-id="2623f-122">Varsayılan olarak, tüm kullanılabilir çekirdekler makinede kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2623f-122">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="2623f-123">Açık bir çekirdek sayısı ayarlar dosyasıyla ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2623f-123">Set an explicit number of cores with a settings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="2623f-124">Verilen ifade eşleşen testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="2623f-124">Run tests that match the given expression.</span></span> <span data-ttu-id="2623f-125">`<Expression>`biçimi `<property>Operator<value>[|&<Expression>]`, işleci biri burada `=`, `!=`, veya `~`.</span><span class="sxs-lookup"><span data-stu-id="2623f-125">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span>  <span data-ttu-id="2623f-126">İşleç `~` 'içeren' anlamsallarını sahiptir ve gibi dize özellikleri için geçerlidir `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="2623f-126">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="2623f-127">Parantez `()` alt ifadeleri gruplamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2623f-127">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="2623f-128">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="2623f-128">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="2623f-129">Test sonuçları için Günlükçü belirtin.</span><span class="sxs-lookup"><span data-stu-id="2623f-129">Specify a logger for test results.</span></span>  

* <span data-ttu-id="2623f-130">Team Foundation Server için test sonuçlarını yayımlamak için kullanmak `TfsPublisher` Günlükçü sağlayıcısı:</span><span class="sxs-lookup"><span data-stu-id="2623f-130">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="2623f-131">Sonuçları bir Visual Studio Test sonuçları dosyası (TRX) için oturum açmak için kullandığınız `trx` Günlükçü sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="2623f-131">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="2623f-132">Bu anahtarı bir dosya olarak test sonuçlarını oluşturur. günlük dosyası adı verilen ile dizin.</span><span class="sxs-lookup"><span data-stu-id="2623f-132">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="2623f-133">Varsa `LogFileName` test sonuçlarını tutmak için benzersiz bir dosya adı oluşturulan sağlanan değil.</span><span class="sxs-lookup"><span data-stu-id="2623f-133">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="2623f-134">Listeleri verilen test kapsayıcısı testlerden buldu.</span><span class="sxs-lookup"><span data-stu-id="2623f-134">Lists discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="2623f-135">Geçerli işlem başlatmaktan sorumlu üst işlemin işlem kimliği.</span><span class="sxs-lookup"><span data-stu-id="2623f-135">Process Id of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="2623f-136">Yuva bağlantısı ve olay iletileri almak için bağlantı noktasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2623f-136">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="2623f-137">Ayrıntılı günlükleri test Platform sağlar.</span><span class="sxs-lookup"><span data-stu-id="2623f-137">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="2623f-138">Günlükleri sağlanan dosyasına yazılır.</span><span class="sxs-lookup"><span data-stu-id="2623f-138">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="2623f-139">Bağdaştırıcıya geçirmek için ek bağımsız değişkenlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2623f-139">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="2623f-140">Bağımsız değişkenler formun ad-değer çiftleri olarak belirtilen `<n>=<v>`, burada `<n>` bağımsız değişkeni adı ve `<v>` bağımsız değişken değeri.</span><span class="sxs-lookup"><span data-stu-id="2623f-140">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="2623f-141">Birden çok bağımsız değişkenleri ayırmak için boşluk kullanın.</span><span class="sxs-lookup"><span data-stu-id="2623f-141">Use a space to separate multiple arguments.</span></span>

## <a name="examples"></a><span data-ttu-id="2623f-142">Örnekler</span><span class="sxs-lookup"><span data-stu-id="2623f-142">Examples</span></span>

<span data-ttu-id="2623f-143">Testleri çalıştırmak `mytestproject.dll`:</span><span class="sxs-lookup"><span data-stu-id="2623f-143">Run tests in `mytestproject.dll`:</span></span>

`dotnet vstest mytestproject.dll`

<span data-ttu-id="2623f-144">Testleri çalıştırmak `mytestproject.dll` ve `myothertestproject.exe`:</span><span class="sxs-lookup"><span data-stu-id="2623f-144">Run tests in `mytestproject.dll` and `myothertestproject.exe`:</span></span>

`dotnet vstest mytestproject.dll myothertestproject.exe`

<span data-ttu-id="2623f-145">Çalıştırma `TestMethod1` testler:</span><span class="sxs-lookup"><span data-stu-id="2623f-145">Run `TestMethod1` tests:</span></span>

`dotnet vstest /Tests:TestMethod1`

<span data-ttu-id="2623f-146">Çalıştırma `TestMethod1` ve `TestMethod2` testleri:</span><span class="sxs-lookup"><span data-stu-id="2623f-146">Run `TestMethod1` and `TestMethod2` tests:</span></span>

`dotnet vstest /Tests:TestMethod1,TestMethod2`
