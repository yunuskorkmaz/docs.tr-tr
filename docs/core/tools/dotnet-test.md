---
title: DotNet test command - .NET Core CLI
description: Dotnet test komutu, belirli bir proje ile birim testleri yürütmek için kullanılır.
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 6102281c4daf149f31e65ef8360831fe9e0ef4f6
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2018
---
# <a name="dotnet-test"></a><span data-ttu-id="c7036-103">DotNet test</span><span class="sxs-lookup"><span data-stu-id="c7036-103">dotnet test</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="c7036-104">Ad</span><span class="sxs-lookup"><span data-stu-id="c7036-104">Name</span></span>

<span data-ttu-id="c7036-105">`dotnet test` -.NET birim testleri çalıştırmak için kullanılan sürücü sınayın.</span><span class="sxs-lookup"><span data-stu-id="c7036-105">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c7036-106">Özet</span><span class="sxs-lookup"><span data-stu-id="c7036-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="c7036-107">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="c7036-107">.NET Core 2.x</span></span>](#tab/netcore2x)


```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c7036-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="c7036-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]
dotnet test [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="c7036-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c7036-109">Description</span></span>

<span data-ttu-id="c7036-110">`dotnet test` Komutu, belirli bir proje ile birim testleri çalıştırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c7036-110">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="c7036-111">`dotnet test` Komutu proje için belirtilen test Çalıştırıcısı konsol uygulaması başlatır.</span><span class="sxs-lookup"><span data-stu-id="c7036-111">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="c7036-112">Sınama Çalıştırıcısı birim test çerçevesi (örneğin, mstest'i, NUnit veya xUnit) için tanımlanan testleri yürütür ve başarı veya başarısızlık her sınamanın raporlar.</span><span class="sxs-lookup"><span data-stu-id="c7036-112">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="c7036-113">Sınama Çalıştırıcısı ve birim testi kitaplığı NuGet paketleri olarak paketlenir ve proje için sıradan bağımlılıklar olarak geri yüklenir.</span><span class="sxs-lookup"><span data-stu-id="c7036-113">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="c7036-114">Test projeleri belirtin sıradan kullanarak test Çalıştırıcısı `<PackageReference>` aşağıdaki örnek proje dosyasında görülen öğe:</span><span class="sxs-lookup"><span data-stu-id="c7036-114">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="c7036-115">Arguments</span><span class="sxs-lookup"><span data-stu-id="c7036-115">Arguments</span></span>

`PROJECT`

<span data-ttu-id="c7036-116">Oluşturduğunuz test projesinin yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="c7036-116">Specifies a path to the test project.</span></span> <span data-ttu-id="c7036-117">Atlanırsa, geçerli dizin için varsayılanları.</span><span class="sxs-lookup"><span data-stu-id="c7036-117">If omitted, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="c7036-118">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="c7036-118">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="c7036-119">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="c7036-119">.NET Core 2.x</span></span>](#tab/netcore2x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="c7036-120">Belirtilen yol özel test bağdaştırıcılarından test çalışması kullanın.</span><span class="sxs-lookup"><span data-stu-id="c7036-120">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="c7036-121">Derleme yapılandırması tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c7036-121">Defines the build configuration.</span></span> <span data-ttu-id="c7036-122">Varsayılan değer `Debug`, ancak bu ayarın SDK projenizin yapılandırmasını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="c7036-122">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="c7036-123">Test çalışması için veri toplayıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c7036-123">Enables data collector for the test run.</span></span> <span data-ttu-id="c7036-124">Daha fazla bilgi için bkz: [İzleyici ve test çalışmasını çözümlemek](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="c7036-124">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="c7036-125">Test platform ve yazma tanılama iletileri belirtilen dosya için tanılama modunu etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="c7036-125">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="c7036-126">Belirli bir test ikili dosyaları arar [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="c7036-126">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="c7036-127">Verilen ifade kullanarak geçerli proje testlerinde kullanıma filtreler.</span><span class="sxs-lookup"><span data-stu-id="c7036-127">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="c7036-128">Daha fazla bilgi için bkz: [filtre seçeneği ayrıntıları](#filter-option-details) bölümü.</span><span class="sxs-lookup"><span data-stu-id="c7036-128">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="c7036-129">Ek bilgi ve seçmeli birim testi filtreleme kullanma hakkında örnekler için bkz: [seçmeli birim testlerini çalıştırma](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="c7036-129">For additional information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="c7036-130">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="c7036-130">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="c7036-131">Test sonuçları için Günlükçü belirtir.</span><span class="sxs-lookup"><span data-stu-id="c7036-131">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="c7036-132">Bunu çalıştırılmadan önce test projesi oluşmuyor.</span><span class="sxs-lookup"><span data-stu-id="c7036-132">Does not build the test project prior to running it.</span></span>

`--no-restore`

<span data-ttu-id="c7036-133">Örtük bir geri yükleme komutu çalıştırırken gerçekleştirmez.</span><span class="sxs-lookup"><span data-stu-id="c7036-133">Doesn't perform an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="c7036-134">Çalıştırmak için ikili dosyaları bulmak dizin.</span><span class="sxs-lookup"><span data-stu-id="c7036-134">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="c7036-135">Test sonuçları yerleştirilmesi nerede bulunacağını dizin.</span><span class="sxs-lookup"><span data-stu-id="c7036-135">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="c7036-136">Belirtilen dizin yoksa oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c7036-136">The specified directory will be created if it doesn't exist.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="c7036-137">Testleri çalıştırırken kullanılacak ayarları.</span><span class="sxs-lookup"><span data-stu-id="c7036-137">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="c7036-138">Tüm geçerli projede bulunan testleri listeler.</span><span class="sxs-lookup"><span data-stu-id="c7036-138">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="c7036-139">Komutun ayrıntı düzeyi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c7036-139">Sets the verbosity level of the command.</span></span> <span data-ttu-id="c7036-140">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="c7036-140">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c7036-141">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="c7036-141">.NET Core 1.x</span></span>](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="c7036-142">Belirtilen yol özel test bağdaştırıcılarından test çalışması kullanın.</span><span class="sxs-lookup"><span data-stu-id="c7036-142">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="c7036-143">Derleme yapılandırması tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c7036-143">Defines the build configuration.</span></span> <span data-ttu-id="c7036-144">Varsayılan değer `Debug`, ancak bu ayarın SDK projenizin yapılandırmasını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="c7036-144">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="c7036-145">Test platform ve yazma tanılama iletileri belirtilen dosya için tanılama modunu etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="c7036-145">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="c7036-146">Belirli bir test ikili dosyaları arar [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="c7036-146">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="c7036-147">Verilen ifade kullanarak geçerli proje testlerinde kullanıma filtreler.</span><span class="sxs-lookup"><span data-stu-id="c7036-147">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="c7036-148">Daha fazla bilgi için bkz: [filtre seçeneği ayrıntıları](#filter-option-details) bölümü.</span><span class="sxs-lookup"><span data-stu-id="c7036-148">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="c7036-149">Ek bilgi ve seçmeli birim testi filtreleme kullanma hakkında örnekler için bkz: [seçmeli birim testlerini çalıştırma](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="c7036-149">For additional information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="c7036-150">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="c7036-150">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="c7036-151">Test sonuçları için Günlükçü belirtir.</span><span class="sxs-lookup"><span data-stu-id="c7036-151">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="c7036-152">Bunu çalıştırılmadan önce test projesi oluşmuyor.</span><span class="sxs-lookup"><span data-stu-id="c7036-152">Does not build the test project prior to running it.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="c7036-153">Çalıştırmak için ikili dosyaları bulmak dizin.</span><span class="sxs-lookup"><span data-stu-id="c7036-153">Directory in which to find the binaries to run.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="c7036-154">Testleri çalıştırırken kullanılacak ayarları.</span><span class="sxs-lookup"><span data-stu-id="c7036-154">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="c7036-155">Tüm geçerli projede bulunan testleri listeler.</span><span class="sxs-lookup"><span data-stu-id="c7036-155">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="c7036-156">Komutun ayrıntı düzeyi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c7036-156">Sets the verbosity level of the command.</span></span> <span data-ttu-id="c7036-157">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="c7036-157">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="c7036-158">Örnekler</span><span class="sxs-lookup"><span data-stu-id="c7036-158">Examples</span></span>

<span data-ttu-id="c7036-159">Geçerli dizin projede Testleri Çalıştır:</span><span class="sxs-lookup"><span data-stu-id="c7036-159">Run the tests in the project in the current directory:</span></span>

`dotnet test`

<span data-ttu-id="c7036-160">Testleri çalıştırmak `test1` proje:</span><span class="sxs-lookup"><span data-stu-id="c7036-160">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

## <a name="filter-option-details"></a><span data-ttu-id="c7036-161">Filtre seçeneği ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="c7036-161">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="c7036-162">`<Expression>` biçimdedir `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="c7036-162">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="c7036-163">`<property>` bir özniteliği olan `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="c7036-163">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="c7036-164">Popüler birim test çerçevelerini tarafından desteklenen özellikler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="c7036-164">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="c7036-165">Test çerçevesi</span><span class="sxs-lookup"><span data-stu-id="c7036-165">Test Framework</span></span> | <span data-ttu-id="c7036-166">Desteklenen özellikler</span><span class="sxs-lookup"><span data-stu-id="c7036-166">Supported properties</span></span>                                                                                      |
| :------------: | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="c7036-167">MSTest</span><span class="sxs-lookup"><span data-stu-id="c7036-167">MSTest</span></span>         | <ul><li><span data-ttu-id="c7036-168">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="c7036-168">FullyQualifiedName</span></span></li><li><span data-ttu-id="c7036-169">Ad</span><span class="sxs-lookup"><span data-stu-id="c7036-169">Name</span></span></li><li><span data-ttu-id="c7036-170">className</span><span class="sxs-lookup"><span data-stu-id="c7036-170">ClassName</span></span></li><li><span data-ttu-id="c7036-171">Öncelik</span><span class="sxs-lookup"><span data-stu-id="c7036-171">Priority</span></span></li><li><span data-ttu-id="c7036-172">TestCategory</span><span class="sxs-lookup"><span data-stu-id="c7036-172">TestCategory</span></span></li></ul> |
| <span data-ttu-id="c7036-173">Xunit</span><span class="sxs-lookup"><span data-stu-id="c7036-173">Xunit</span></span>          | <ul><li><span data-ttu-id="c7036-174">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="c7036-174">FullyQualifiedName</span></span></li><li><span data-ttu-id="c7036-175">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="c7036-175">DisplayName</span></span></li><li><span data-ttu-id="c7036-176">Özellikleri</span><span class="sxs-lookup"><span data-stu-id="c7036-176">Traits</span></span></li></ul>                                   |

<span data-ttu-id="c7036-177">`<operator>` Özellik ve değer arasındaki ilişkiyi açıklar:</span><span class="sxs-lookup"><span data-stu-id="c7036-177">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="c7036-178">İşleç</span><span class="sxs-lookup"><span data-stu-id="c7036-178">Operator</span></span> | <span data-ttu-id="c7036-179">İşlev</span><span class="sxs-lookup"><span data-stu-id="c7036-179">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="c7036-180">Tam eşleşme</span><span class="sxs-lookup"><span data-stu-id="c7036-180">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="c7036-181">Değil tam eşleşme</span><span class="sxs-lookup"><span data-stu-id="c7036-181">Not exact match</span></span> |
| `~`      | <span data-ttu-id="c7036-182">İçerir</span><span class="sxs-lookup"><span data-stu-id="c7036-182">Contains</span></span>        |

<span data-ttu-id="c7036-183">`<value>` bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="c7036-183">`<value>` is a string.</span></span> <span data-ttu-id="c7036-184">Tüm arama büyük/küçük harfe duyarsızdır.</span><span class="sxs-lookup"><span data-stu-id="c7036-184">All the lookups are case insensitive.</span></span>

<span data-ttu-id="c7036-185">Bir ifade olmadan bir `<operator>` otomatik olarak kabul bir `contains` üzerinde `FullyQualifiedName` özelliği (örneğin, `dotnet test --filter xyz` aynı `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="c7036-185">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="c7036-186">İfadeler ile Koşullu işleçler katılabilir:</span><span class="sxs-lookup"><span data-stu-id="c7036-186">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="c7036-187">İşleç</span><span class="sxs-lookup"><span data-stu-id="c7036-187">Operator</span></span> | <span data-ttu-id="c7036-188">İşlev</span><span class="sxs-lookup"><span data-stu-id="c7036-188">Function</span></span> |
| :------: | :------: |
| <code>&#124;</code>      | <span data-ttu-id="c7036-189">VEYA</span><span class="sxs-lookup"><span data-stu-id="c7036-189">OR</span></span>       |
| `&`      | <span data-ttu-id="c7036-190">AND</span><span class="sxs-lookup"><span data-stu-id="c7036-190">AND</span></span>      |

<span data-ttu-id="c7036-191">İfadeler parantez içine Koşullu işleçler kullanırken içine aldığınız (örneğin, `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="c7036-191">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="c7036-192">Ek bilgi ve seçmeli birim testi filtreleme kullanma hakkında örnekler için bkz: [seçmeli birim testlerini çalıştırma](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="c7036-192">For additional information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c7036-193">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7036-193">See also</span></span>

 [<span data-ttu-id="c7036-194">Çerçeveler ve hedefler</span><span class="sxs-lookup"><span data-stu-id="c7036-194">Frameworks and Targets</span></span>](../../standard/frameworks.md)  
 [<span data-ttu-id="c7036-195">.NET çekirdeği çalışma zamanı tanımlayıcı (RID) Kataloğu</span><span class="sxs-lookup"><span data-stu-id="c7036-195">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
