---
title: DotNet VSTest komutu
description: DotNet VSTest komutu bir proje ve tüm bağımlılıklarını oluşturur.
ms.date: 02/27/2020
ms.openlocfilehash: 88e5b6a8966d78d0746f9ea5ccbccab142a2e0f6
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156939"
---
# <a name="dotnet-vstest"></a><span data-ttu-id="4c69f-103">dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="4c69f-103">dotnet vstest</span></span>

<span data-ttu-id="4c69f-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="4c69f-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="4c69f-105">Adı</span><span class="sxs-lookup"><span data-stu-id="4c69f-105">Name</span></span>

<span data-ttu-id="4c69f-106">`dotnet-vstest`, belirtilen dosyalardan testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="4c69f-106">`dotnet-vstest` - Runs tests from the specified files.</span></span>

## <a name="synopsis"></a><span data-ttu-id="4c69f-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="4c69f-107">Synopsis</span></span>

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings] [--Tests]
    [--TestAdapterPath] [--Platform] [--Framework] [--Parallel]
    [--TestCaseFilter] [--logger] [-lt|--ListTests]
    [--ParentProcessId] [--Port] [--Diag] [--Blame]
    [--InIsolation] [[--] <args>...]] [-?|--Help]
```

## <a name="description"></a><span data-ttu-id="4c69f-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4c69f-108">Description</span></span>

<span data-ttu-id="4c69f-109">`dotnet-vstest` komutu, otomatik birim testlerini çalıştırmak için `VSTest.Console` komut satırı uygulamasını çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="4c69f-109">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="4c69f-110">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="4c69f-110">Arguments</span></span>

- **`TEST_FILE_NAMES`**

  <span data-ttu-id="4c69f-111">Belirtilen derlemelerdeki testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4c69f-111">Run tests from the specified assemblies.</span></span> <span data-ttu-id="4c69f-112">Birden çok test derleme adını boşluklarla ayırın.</span><span class="sxs-lookup"><span data-stu-id="4c69f-112">Separate multiple test assembly names with spaces.</span></span> <span data-ttu-id="4c69f-113">Joker karakterler desteklenir.</span><span class="sxs-lookup"><span data-stu-id="4c69f-113">Wildcards are supported.</span></span>

## <a name="options"></a><span data-ttu-id="4c69f-114">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="4c69f-114">Options</span></span>

- **`--Settings <Settings File>`**

  <span data-ttu-id="4c69f-115">Testler çalıştırılırken kullanılacak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4c69f-115">Settings to use when running tests.</span></span>

- **`--Tests <Test Names>`**

  <span data-ttu-id="4c69f-116">Testleri, belirtilen değerlerle eşleşen adlarla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4c69f-116">Run tests with names that match the provided values.</span></span> <span data-ttu-id="4c69f-117">Birden çok değeri virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="4c69f-117">Separate multiple values with commas.</span></span>

- **`--TestAdapterPath`**

  <span data-ttu-id="4c69f-118">Test çalıştırmasında belirli bir yoldan (varsa) özel test bağdaştırıcıları kullanın.</span><span class="sxs-lookup"><span data-stu-id="4c69f-118">Use custom test adapters from a given path (if any) in the test run.</span></span>

- **`--Platform <Platform type>`**

  <span data-ttu-id="4c69f-119">Test yürütmesi için kullanılan hedef platform mimarisi.</span><span class="sxs-lookup"><span data-stu-id="4c69f-119">Target platform architecture used for test execution.</span></span> <span data-ttu-id="4c69f-120">Geçerli değerler `x86`, `x64`ve `ARM`.</span><span class="sxs-lookup"><span data-stu-id="4c69f-120">Valid values are `x86`, `x64`, and `ARM`.</span></span>

- **`--Framework <Framework Version>`**

  <span data-ttu-id="4c69f-121">Test yürütmesi için kullanılan hedef .NET Framework sürümü.</span><span class="sxs-lookup"><span data-stu-id="4c69f-121">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="4c69f-122">Geçerli değer örnekleri `.NETFramework,Version=v4.6` veya `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="4c69f-122">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="4c69f-123">Desteklenen diğer değerler `Framework40`, `Framework45`, `FrameworkCore10`ve `FrameworkUap10`.</span><span class="sxs-lookup"><span data-stu-id="4c69f-123">Other supported values are `Framework40`, `Framework45`, `FrameworkCore10`, and `FrameworkUap10`.</span></span>

- **`--Parallel`**

  <span data-ttu-id="4c69f-124">Testleri paralel olarak çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4c69f-124">Run tests in parallel.</span></span> <span data-ttu-id="4c69f-125">Varsayılan olarak, makinedeki tüm kullanılabilir çekirdekler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4c69f-125">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="4c69f-126">*Runsettings* dosyasındaki `RunConfiguration` düğümü altında `MaxCpuCount` özelliğini ayarlayarak, açık sayıda çekirdek belirtin.</span><span class="sxs-lookup"><span data-stu-id="4c69f-126">Specify an explicit number of cores by setting the `MaxCpuCount` property under the `RunConfiguration` node in the *runsettings* file.</span></span>

- **`--TestCaseFilter <Expression>`**

  <span data-ttu-id="4c69f-127">Verilen ifadeyle eşleşen testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4c69f-127">Run tests that match the given expression.</span></span> <span data-ttu-id="4c69f-128">`<Expression>` biçim `<property>Operator<value>[|&<Expression>]`, burada Işleç `=`, `!=`veya `~`biridir.</span><span class="sxs-lookup"><span data-stu-id="4c69f-128">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="4c69f-129">İşleç `~` ' Contains ' semantiğine sahiptir ve `DisplayName`gibi dize özellikleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4c69f-129">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="4c69f-130">Parantez `()` alt ifadeleri gruplandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4c69f-130">Parenthesis `()` are used to group subexpressions.</span></span>

- **`-?|--Help`**

  <span data-ttu-id="4c69f-131">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="4c69f-131">Prints out a short help for the command.</span></span>

- **`--logger <Logger Uri/FriendlyName>`**

  <span data-ttu-id="4c69f-132">Test sonuçları için bir günlükçü belirtin.</span><span class="sxs-lookup"><span data-stu-id="4c69f-132">Specify a logger for test results.</span></span>

  - <span data-ttu-id="4c69f-133">Test sonuçlarını Team Foundation Server yayımlamak için `TfsPublisher` günlükçü sağlayıcısını kullanın:</span><span class="sxs-lookup"><span data-stu-id="4c69f-133">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

    ```console
    /logger:TfsPublisher;
        Collection=<team project collection url>;
        BuildName=<build name>;
        TeamProject=<team project name>
        [;Platform=<Defaults to "Any CPU">]
        [;Flavor=<Defaults to "Debug">]
        [;RunTitle=<title>]
    ```

  - <span data-ttu-id="4c69f-134">Sonuçları bir Visual Studio Test Sonuçları dosyasına (TRX) kaydetmek için `trx` günlükçü sağlayıcısını kullanın.</span><span class="sxs-lookup"><span data-stu-id="4c69f-134">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="4c69f-135">Bu anahtar, test sonuçları dizininde verilen günlük dosyası adına sahip bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4c69f-135">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="4c69f-136">`LogFileName` sağlanmazsa, test sonuçlarını tutmak için benzersiz bir dosya adı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4c69f-136">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

    ```console
    /logger:trx [;LogFileName=<Defaults to unique file name>]
    ```

- **`-lt|--ListTests <File Name>`**

  <span data-ttu-id="4c69f-137">Verilen test kapsayıcısından tüm bulunan testleri listeler.</span><span class="sxs-lookup"><span data-stu-id="4c69f-137">Lists all discovered tests from the given test container.</span></span>

- **`--ParentProcessId <ParentProcessId>`**

  <span data-ttu-id="4c69f-138">Geçerli işlemin başlatmasından sorumlu olan üst işlemin işlem KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="4c69f-138">Process ID of the parent process responsible for launching the current process.</span></span>

- **`--Port <Port>`**

  <span data-ttu-id="4c69f-139">Yuva bağlantısı ve olay iletilerini alma bağlantı noktasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4c69f-139">Specifies the port for the socket connection and receiving the event messages.</span></span>

- **`--Diag <Path to log file>`**

  <span data-ttu-id="4c69f-140">Test platformu için ayrıntılı günlükleri etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="4c69f-140">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="4c69f-141">Günlükler, belirtilen dosyaya yazılır.</span><span class="sxs-lookup"><span data-stu-id="4c69f-141">Logs are written to the provided file.</span></span>

- **`--Blame`**

  <span data-ttu-id="4c69f-142">Testleri sorumluyu modunda çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="4c69f-142">Runs the tests in blame mode.</span></span> <span data-ttu-id="4c69f-143">Bu seçenek, test ana bilgisayarının kilitlenmesine neden olan sorunlu testleri yalıtmak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="4c69f-143">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="4c69f-144">Geçerli dizinde, kilitlenmeden önce yürütülen testlerin sırasını yakalayan *Sequence. xml* olarak bir çıktı dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4c69f-144">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`--InIsolation`**

  <span data-ttu-id="4c69f-145">Testleri yalıtılmış bir işlemde çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="4c69f-145">Runs the tests in an isolated process.</span></span> <span data-ttu-id="4c69f-146">Bu, *VSTest. Console. exe* işleminin testlerin bir hata üzerinde durdurulması olasılığını azaltır, ancak testler daha yavaş çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="4c69f-146">This makes *vstest.console.exe* process less likely to be stopped on an error in the tests, but tests may run slower.</span></span>

- **`@<file>`**

  <span data-ttu-id="4c69f-147">Daha fazla seçenek için yanıt dosyasını okur.</span><span class="sxs-lookup"><span data-stu-id="4c69f-147">Reads response file for more options.</span></span>

- **`args`**

  <span data-ttu-id="4c69f-148">Bağdaştırıcıya geçirilecek ek bağımsız değişkenleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="4c69f-148">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="4c69f-149">Bağımsız değişkenler `<n>=<v>`biçim-değer çiftleri olarak belirtilir; burada `<n>` bağımsız değişken adıdır ve `<v>` bağımsız değişken değeridir.</span><span class="sxs-lookup"><span data-stu-id="4c69f-149">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="4c69f-150">Birden çok bağımsız değişkeni ayırmak için boşluk kullanın.</span><span class="sxs-lookup"><span data-stu-id="4c69f-150">Use a space to separate multiple arguments.</span></span>

## <a name="examples"></a><span data-ttu-id="4c69f-151">Örnekler</span><span class="sxs-lookup"><span data-stu-id="4c69f-151">Examples</span></span>

<span data-ttu-id="4c69f-152">Testleri *MyTestProject. dll*içinde Çalıştır:</span><span class="sxs-lookup"><span data-stu-id="4c69f-152">Run tests in *mytestproject.dll*:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll
```

<span data-ttu-id="4c69f-153">Testleri *MyTestProject. dll*içinde çalıştırın, özel adla özel klasöre dışarı aktarma:</span><span class="sxs-lookup"><span data-stu-id="4c69f-153">Run tests in *mytestproject.dll*, exporting to custom folder with custom name:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path
```

<span data-ttu-id="4c69f-154">*Testprojem. dll* ve *myothertestproject. exe*' de testleri çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="4c69f-154">Run tests in *mytestproject.dll* and *myothertestproject.exe*:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll myothertestproject.exe
```

<span data-ttu-id="4c69f-155">`TestMethod1` testlerini Çalıştır:</span><span class="sxs-lookup"><span data-stu-id="4c69f-155">Run `TestMethod1` tests:</span></span>

```dotnetcli
dotnet vstest /Tests:TestMethod1
```

<span data-ttu-id="4c69f-156">`TestMethod1` Çalıştır ve Testleri `TestMethod2`:</span><span class="sxs-lookup"><span data-stu-id="4c69f-156">Run `TestMethod1` and `TestMethod2` tests:</span></span>

```dotnetcli
dotnet vstest /Tests:TestMethod1,TestMethod2
```
