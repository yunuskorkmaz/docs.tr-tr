---
title: Dotnet testi ve xUnit kullanarak .NET Core'da C# kodunu test etme birimi
description: Noktanet testi ve xUnit kullanarak adım adım örnek bir çözüm oluşturma etkileşimli bir deneyim le C# ve .NET Core'daki birim test kavramlarını öğrenin.
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: c9e3d63a2cf4f560591459833340b729ffec1b95
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240902"
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a><span data-ttu-id="5d635-103">Dotnet testi ve xUnit kullanarak .NET Core'da C# testi</span><span class="sxs-lookup"><span data-stu-id="5d635-103">Unit testing C# in .NET Core using dotnet test and xUnit</span></span>

<span data-ttu-id="5d635-104">Bu öğretici, birim test projesi ve kaynak kodu projesi içeren bir çözümün nasıl oluşturulabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5d635-104">This tutorial shows how to build a solution containing a unit test project and source code project.</span></span> <span data-ttu-id="5d635-105">Önceden oluşturulmuş bir çözümü kullanarak öğreticiyi takip etmek için [örnek kodu görüntüleyin veya indirin.](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/)</span><span class="sxs-lookup"><span data-stu-id="5d635-105">To follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/).</span></span> <span data-ttu-id="5d635-106">İndirme talimatları için [Örnekler ve Öğreticiler'e](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)bakın.</span><span class="sxs-lookup"><span data-stu-id="5d635-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="create-the-solution"></a><span data-ttu-id="5d635-107">Çözümü oluşturun</span><span class="sxs-lookup"><span data-stu-id="5d635-107">Create the solution</span></span>

<span data-ttu-id="5d635-108">Bu bölümde, kaynak ve test projelerini içeren bir çözüm oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5d635-108">In this section, a solution is created that contains the source and test projects.</span></span> <span data-ttu-id="5d635-109">Tamamlanan çözüm aşağıdaki dizin yapısına sahiptir:</span><span class="sxs-lookup"><span data-stu-id="5d635-109">The completed solution has the following directory structure:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        PrimeService.cs
        PrimeService.csproj
    /PrimeService.Tests
        PrimeService_IsPrimeShould.cs
        PrimeServiceTests.csproj
```

<span data-ttu-id="5d635-110">Aşağıdaki yönergeler, test çözümlerini oluşturmak için adımları sağlar.</span><span class="sxs-lookup"><span data-stu-id="5d635-110">The following instructions provide the steps to create the test solution.</span></span> <span data-ttu-id="5d635-111">Test çözümlerini tek adımda oluşturmak için talimatlar için test çözümü oluşturmak için [Komutlar'a](#create-test-cmd) bakın.</span><span class="sxs-lookup"><span data-stu-id="5d635-111">See [Commands to create test solution](#create-test-cmd) for instructions to create the test solution in one step.</span></span>

* <span data-ttu-id="5d635-112">Bir kabuk penceresi açın.</span><span class="sxs-lookup"><span data-stu-id="5d635-112">Open a shell window.</span></span>
* <span data-ttu-id="5d635-113">Şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="5d635-113">Run the following command:</span></span>

  ```dotnetcli
  dotnet new sln -o unit-testing-using-dotnet-test
  ```

  <span data-ttu-id="5d635-114">Komut, [`dotnet new sln`](../tools/dotnet-new.md) *birim-test-using-dotnet-test* dizininde yeni bir çözüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5d635-114">The [`dotnet new sln`](../tools/dotnet-new.md) command creates a new solution in the *unit-testing-using-dotnet-test* directory.</span></span>
* <span data-ttu-id="5d635-115">*Dizin,birim-test-kullanarak-dotnet-test* klasörüne değiştirin.</span><span class="sxs-lookup"><span data-stu-id="5d635-115">Change directory to the *unit-testing-using-dotnet-test* folder.</span></span>
* <span data-ttu-id="5d635-116">Şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="5d635-116">Run the following command:</span></span>

  ```dotnetcli
  dotnet new classlib -o PrimeService
  ```

   <span data-ttu-id="5d635-117">Komut, [`dotnet new classlib`](../tools/dotnet-new.md) *PrimeService* klasöründe yeni bir sınıf kitaplığı projesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5d635-117">The [`dotnet new classlib`](../tools/dotnet-new.md) command creates a new class library project  in the *PrimeService* folder.</span></span> <span data-ttu-id="5d635-118">Yeni sınıf kitaplığı sınanacak kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="5d635-118">The new class library will contain the code to be tested.</span></span>
* <span data-ttu-id="5d635-119">*Class1.cs* *PrimeService.cs*yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="5d635-119">Rename *Class1.cs* to *PrimeService.cs*.</span></span>
* <span data-ttu-id="5d635-120">*PrimeService.cs* kodu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="5d635-120">Replace the code in *PrimeService.cs* with the following code:</span></span>
  
  ```csharp
    using System;

    namespace Prime.Services
    {
        public class PrimeService
        {
            public bool IsPrime(int candidate)
            {
                throw new NotImplementedException("Not implemented.");
            }
        }
    }
  ```

* <span data-ttu-id="5d635-121">Yukarıdaki kod:</span><span class="sxs-lookup"><span data-stu-id="5d635-121">The preceding code:</span></span>
  * <span data-ttu-id="5d635-122">Uygulanmadığını <xref:System.NotImplementedException> belirten bir ileti atar.</span><span class="sxs-lookup"><span data-stu-id="5d635-122">Throws a <xref:System.NotImplementedException> with a message indicating it's not implemented.</span></span>
  * <span data-ttu-id="5d635-123">Öğreticinin daha sonra güncellenir.</span><span class="sxs-lookup"><span data-stu-id="5d635-123">Is updated later in the tutorial.</span></span>

<!-- preceding code shows an english bias. Message makes no sense outside english -->

* <span data-ttu-id="5d635-124">*Birim-test-using-dotnet-test* dizininde, sınıf kitaplığı projesini çözüme eklemek için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="5d635-124">In the *unit-testing-using-dotnet-test* directory, run the following command to add the class library project to the solution:</span></span>

  ```dotnetcli
  dotnet sln add ./PrimeService/PrimeService.csproj
  ```

* <span data-ttu-id="5d635-125">Aşağıdaki komutu çalıştırarak *PrimeService.Tests* projesini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="5d635-125">Create the *PrimeService.Tests* project by running the following command:</span></span>

  ```dotnetcli
  dotnet new xunit -o PrimeService.Tests
  ```

* <span data-ttu-id="5d635-126">Yukarıdaki komut:</span><span class="sxs-lookup"><span data-stu-id="5d635-126">The preceding command:</span></span>
  * <span data-ttu-id="5d635-127">*PrimeService.Tests* dizininde *PrimeService.Tests* projesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5d635-127">Creates the *PrimeService.Tests* project in the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="5d635-128">Test projesi, test kitaplığı olarak [xUnit](https://xunit.github.io/) kullanır.</span><span class="sxs-lookup"><span data-stu-id="5d635-128">The test project uses [xUnit](https://xunit.github.io/) as the test library.</span></span>
  * <span data-ttu-id="5d635-129">Proje dosyasına aşağıdaki `<PackageReference />`öğeleri ekleyerek test runnerını yapılandırır:</span><span class="sxs-lookup"><span data-stu-id="5d635-129">Configures the test runner by adding the following `<PackageReference />`elements to the project file:</span></span>
    * <span data-ttu-id="5d635-130">"Microsoft.NET.Test.Sdk"</span><span class="sxs-lookup"><span data-stu-id="5d635-130">"Microsoft.NET.Test.Sdk"</span></span>
    * <span data-ttu-id="5d635-131">"xunit"</span><span class="sxs-lookup"><span data-stu-id="5d635-131">"xunit"</span></span>
    * <span data-ttu-id="5d635-132">"xunit.runner.visualstudio"</span><span class="sxs-lookup"><span data-stu-id="5d635-132">"xunit.runner.visualstudio"</span></span>

* <span data-ttu-id="5d635-133">Aşağıdaki komutu çalıştırarak çözüm dosyasına test projesini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="5d635-133">Add the test project to the solution file by running the following command:</span></span>

  ```dotnetcli
  dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
  ```

* <span data-ttu-id="5d635-134">`PrimeService` Sınıf kitaplığını *PrimeService.Tests* projesine bağımlılık olarak ekleyin:</span><span class="sxs-lookup"><span data-stu-id="5d635-134">Add the `PrimeService` class library as a dependency to the *PrimeService.Tests* project:</span></span>

  ```dotnetcli
  dotnet add ./PrimeService.Tests/PrimeService.Tests.csproj reference ./PrimeService/PrimeService.csproj  
  ```

<a name="create-test-cmd"></a>

### <a name="commands-to-create-the-solution"></a><span data-ttu-id="5d635-135">Çözümü oluşturmak için komutlar</span><span class="sxs-lookup"><span data-stu-id="5d635-135">Commands to create the solution</span></span>

<span data-ttu-id="5d635-136">Bu bölümde önceki bölümdeki tüm komutlar özetlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="5d635-136">This section summarizes all the commands in the previous section.</span></span> <span data-ttu-id="5d635-137">Önceki bölümdeki adımları tamamladıysanız bu bölümü atlayın.</span><span class="sxs-lookup"><span data-stu-id="5d635-137">Skip this section if you've completed the steps in the previous section.</span></span>

<span data-ttu-id="5d635-138">Aşağıdaki komutlar bir windows makinesinde test çözümcürse oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5d635-138">The following commands create the test solution on a windows machine.</span></span> <span data-ttu-id="5d635-139">macOS ve Unix için, dosyayı `ren` yeniden `ren` adlandırmak için işletim sistemi sürümüne komutu güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="5d635-139">For macOS and Unix, update the `ren` command to the OS version of `ren` to rename a file:</span></span>

```dotnetcli
dotnet new sln -o unit-testing-using-dotnet-test
cd unit-testing-using-dotnet-test
dotnet new classlib -o PrimeService
ren .\PrimeService\Class1.cs PrimeService.cs
dotnet sln add ./PrimeService/PrimeService.csproj
dotnet new xunit -o PrimeService.Tests
dotnet add ./PrimeService.Tests/PrimeService.Tests.csproj reference ./PrimeService/PrimeService.csproj
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
```

<span data-ttu-id="5d635-140">Önceki bölümdeki *"Kodu PrimeService.cs* aşağıdaki kodla değiştirin" yönergelerini izleyin.</span><span class="sxs-lookup"><span data-stu-id="5d635-140">Follow the instructions for "Replace the code in *PrimeService.cs* with the following code" in the previous section.</span></span>

## <a name="create-a-test"></a><span data-ttu-id="5d635-141">Test oluşturma</span><span class="sxs-lookup"><span data-stu-id="5d635-141">Create a test</span></span>

<span data-ttu-id="5d635-142">Test odaklı geliştirmede (TDD) popüler bir yaklaşım, hedef kodu uygulamadan önce bir test yazmaktır.</span><span class="sxs-lookup"><span data-stu-id="5d635-142">A popular approach in test driven development (TDD) is to write a test before implementing the target code.</span></span> <span data-ttu-id="5d635-143">Bu öğretici TDD yaklaşımını kullanır.</span><span class="sxs-lookup"><span data-stu-id="5d635-143">This tutorial uses the TDD approach.</span></span> <span data-ttu-id="5d635-144">Yöntem `IsPrime` çağrılabilir, ancak uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="5d635-144">The `IsPrime` method is callable, but not implemented.</span></span> <span data-ttu-id="5d635-145">Başarısız olmak `IsPrime` için bir test çağrısı.</span><span class="sxs-lookup"><span data-stu-id="5d635-145">A test call to `IsPrime` fails.</span></span> <span data-ttu-id="5d635-146">TDD ile başarısız olduğu bilinen bir test yazılır.</span><span class="sxs-lookup"><span data-stu-id="5d635-146">With TDD, a test is written that is known to fail.</span></span> <span data-ttu-id="5d635-147">Hedef kod, test sınavını geçmek için güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="5d635-147">The target code is updated to make the test pass.</span></span> <span data-ttu-id="5d635-148">Bu yaklaşımı yinelemeye, başarısız bir test yazmaya ve ardından geçmek için hedef kodu güncelleştirmeye devam edin.</span><span class="sxs-lookup"><span data-stu-id="5d635-148">You keep repeating this approach, writing a failing test and then updating the target code to pass.</span></span>

<span data-ttu-id="5d635-149">Güncelleştirme *PrimeService.Tests* proje:</span><span class="sxs-lookup"><span data-stu-id="5d635-149">Update the *PrimeService.Tests* project:</span></span>

* <span data-ttu-id="5d635-150">*Delete PrimeService.Tests/UnitTest1.cs*.</span><span class="sxs-lookup"><span data-stu-id="5d635-150">Delete *PrimeService.Tests/UnitTest1.cs*.</span></span>
* <span data-ttu-id="5d635-151">*PrimeService.Tests/PrimeService_IsPrimeShould.cs* dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5d635-151">Create a *PrimeService.Tests/PrimeService_IsPrimeShould.cs*  file.</span></span>
* <span data-ttu-id="5d635-152">*PrimeService_IsPrimeShould.cs'deki* kodu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="5d635-152">Replace the code in *PrimeService_IsPrimeShould.cs* with the following code:</span></span>

```csharp
using Xunit;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;

        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [Fact]
        public void IsPrime_InputIs1_ReturnFalse()
        {
            var result = _primeService.IsPrime(1);

            Assert.False(result, "1 should not be prime");
        }
    }
}
```

<span data-ttu-id="5d635-153">Öznitelik, `[Fact]` test koşucusu tarafından çalıştırılabilen bir test yöntemini bildirir.</span><span class="sxs-lookup"><span data-stu-id="5d635-153">The `[Fact]` attribute declares a test method that's run by the test runner.</span></span> <span data-ttu-id="5d635-154">*PrimeService.Tests* klasöründen `dotnet test`çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5d635-154">From the *PrimeService.Tests* folder, run `dotnet test`.</span></span> <span data-ttu-id="5d635-155">[dotnet test](../tools/dotnet-test.md) komutu her iki projeyi oluşturur ve testleri çalıştırar.</span><span class="sxs-lookup"><span data-stu-id="5d635-155">The [dotnet test](../tools/dotnet-test.md) command builds both projects and runs the tests.</span></span> <span data-ttu-id="5d635-156">xUnit test koşucusu testleri çalıştırmak için program giriş noktasını içerir.</span><span class="sxs-lookup"><span data-stu-id="5d635-156">The xUnit test runner contains the program entry point to run the tests.</span></span> <span data-ttu-id="5d635-157">`dotnet test`ünite test projesini kullanarak test koşucusu başlatın.</span><span class="sxs-lookup"><span data-stu-id="5d635-157">`dotnet test` starts the test runner using the unit test project.</span></span>

<span data-ttu-id="5d635-158">Test başarısız `IsPrime` oldu çünkü uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="5d635-158">The test fails because `IsPrime` hasn't been implemented.</span></span> <span data-ttu-id="5d635-159">TDD yaklaşımını kullanarak, bu testin geçmesi için yalnızca yeterli kodu yazın.</span><span class="sxs-lookup"><span data-stu-id="5d635-159">Using the TDD approach, write only enough code so this test passes.</span></span> <span data-ttu-id="5d635-160">Aşağıdaki `IsPrime` kodla güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="5d635-160">Update `IsPrime` with the following code:</span></span>

```csharp
public bool IsPrime(int candidate)
{
    if (candidate == 1)
    {
        return false;
    }
    throw new NotImplementedException("Not fully implemented.");
}
```

<span data-ttu-id="5d635-161">`dotnet test` öğesini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5d635-161">Run `dotnet test`.</span></span> <span data-ttu-id="5d635-162">Test geçer.</span><span class="sxs-lookup"><span data-stu-id="5d635-162">The test passes.</span></span>

### <a name="add-more-tests"></a><span data-ttu-id="5d635-163">Daha fazla test ekleme</span><span class="sxs-lookup"><span data-stu-id="5d635-163">Add more tests</span></span>

<span data-ttu-id="5d635-164">0 ve -1 için asal sayı testleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5d635-164">Add prime number tests for 0 and -1.</span></span> <span data-ttu-id="5d635-165">Önceki testi kopyalayabilir ve aşağıdaki kodu 0 ve -1'i kullanmak üzere değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5d635-165">You could copy the preceding test and change the following code to use 0 and -1:</span></span>

```csharp
var result = _primeService.IsPrime(1);

Assert.False(result, "1 should not be prime");
```

<span data-ttu-id="5d635-166">Yalnızca bir parametre değiştiğinde test kodunun kopyalanması kod çoğaltma ve test şişkinliğiyle sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="5d635-166">Copying test code when only a parameter changes results in code duplication and test bloat.</span></span> <span data-ttu-id="5d635-167">Aşağıdaki xUnit öznitelikleri benzer testlerin bir paketi yazmayı sağlar:</span><span class="sxs-lookup"><span data-stu-id="5d635-167">The following xUnit attributes enable writing a suite of similar tests:</span></span>

- <span data-ttu-id="5d635-168">`[Theory]`aynı kodu çalıştıran ancak farklı giriş bağımsız değişkenleri olan bir test paketini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5d635-168">`[Theory]` represents a suite of tests that execute the same code but have different input arguments.</span></span>

- <span data-ttu-id="5d635-169">`[InlineData]`öznitelik bu girişler için değerleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="5d635-169">`[InlineData]` attribute specifies values for those inputs.</span></span>

<span data-ttu-id="5d635-170">Yeni testler oluşturmak yerine, tek bir teori oluşturmak için önceki xUnit özniteliklerini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="5d635-170">Rather than creating new tests, apply the preceding xUnit attributes to create a single theory.</span></span> <span data-ttu-id="5d635-171">Aşağıdaki kodu değiştirin:</span><span class="sxs-lookup"><span data-stu-id="5d635-171">Replace the following code:</span></span>

```csharp
[Fact]
public void IsPrime_InputIs1_ReturnFalse()
{
    var result = _primeService.IsPrime(1);

    Assert.False(result, "1 should not be prime");
}
```

<span data-ttu-id="5d635-172">aşağıdaki kod ile:</span><span class="sxs-lookup"><span data-stu-id="5d635-172">with the following code:</span></span>

[!code-csharp[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-using-dotnet-test/csharp/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="5d635-173">Önceki kodda `[Theory]` ve `[InlineData]` ikiden küçük birkaç değerin test edilmesini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="5d635-173">In the preceding code, `[Theory]` and `[InlineData]` enable testing several values less than two.</span></span> <span data-ttu-id="5d635-174">İki, en küçük asal sayıdır.</span><span class="sxs-lookup"><span data-stu-id="5d635-174">Two is the smallest prime number.</span></span>

<span data-ttu-id="5d635-175">Çalıştır `dotnet test`, iki test başarısız.</span><span class="sxs-lookup"><span data-stu-id="5d635-175">Run `dotnet test`, two of the tests fail.</span></span> <span data-ttu-id="5d635-176">Tüm testlerin geçmesi için yöntemi `IsPrime` aşağıdaki kodla güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="5d635-176">To make all of the tests pass, update the `IsPrime` method with the following code:</span></span>

```csharp
public bool IsPrime(int candidate)
{
    if (candidate < 2)
    {
        return false;
    }
    throw new NotImplementedException("Not fully implemented.");
}
```

<span data-ttu-id="5d635-177">TDD yaklaşımını izleyerek, daha fazla başarısız test ekleyin ve ardından hedef kodu güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="5d635-177">Following the TDD approach, add more failing tests, then update the target code.</span></span> <span data-ttu-id="5d635-178">[Testlerin tamamlanmış sürümüne](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) ve [kitaplığın tam uygulamasına](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs)bakın.</span><span class="sxs-lookup"><span data-stu-id="5d635-178">See the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="5d635-179">Tamamlanan `IsPrime` yöntem ilkelliği sınamak için etkili bir algoritma değildir.</span><span class="sxs-lookup"><span data-stu-id="5d635-179">The completed `IsPrime` method is not an efficient algorithm for testing primality.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="5d635-180">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="5d635-180">Additional resources</span></span>

- [<span data-ttu-id="5d635-181">resmi site xUnit.net</span><span class="sxs-lookup"><span data-stu-id="5d635-181">xUnit.net official site</span></span>](https://xunit.github.io)
- [<span data-ttu-id="5d635-182">ASP.NET Core'da test denetleyicisi mantığı</span><span class="sxs-lookup"><span data-stu-id="5d635-182">Testing controller logic in ASP.NET Core</span></span>](/aspnet/core/mvc/controllers/testing)
- [`dotnet add reference`](../tools/dotnet-add-reference.md)
