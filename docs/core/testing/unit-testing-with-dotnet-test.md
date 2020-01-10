---
title: DotNet test C# ve xUnit kullanarak .NET Core 'da birim testi kodu
description: Ve .NET Core 'daki C# birim testi kavramlarını, DotNet test ve xUnit kullanarak örnek bir çözüm oluşturma adlı etkileşimli bir deneyim aracılığıyla öğrenin.
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: 226db54047747fbd065c64f5e4812094921c7f62
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714232"
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a><span data-ttu-id="412e8-103">DotNet test C# ve xUnit kullanarak .NET Core 'da birim testi</span><span class="sxs-lookup"><span data-stu-id="412e8-103">Unit testing C# in .NET Core using dotnet test and xUnit</span></span>

<span data-ttu-id="412e8-104">Bu öğreticide, birim testi projesi ve kaynak kodu projesi içeren bir çözüm oluşturma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="412e8-104">This tutorial shows how to build a solution containing a unit test project and source code project.</span></span> <span data-ttu-id="412e8-105">Önceden oluşturulmuş bir çözümü kullanarak öğreticiyi izlemek için [örnek kodu görüntüleyin veya indirin](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/).</span><span class="sxs-lookup"><span data-stu-id="412e8-105">To follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/).</span></span> <span data-ttu-id="412e8-106">İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="412e8-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="create-the-solution"></a><span data-ttu-id="412e8-107">Çözümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="412e8-107">Create the solution</span></span>

<span data-ttu-id="412e8-108">Bu bölümde, kaynak ve test projelerini içeren bir çözüm oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="412e8-108">In this section, a solution is created that contains the source and test projects.</span></span> <span data-ttu-id="412e8-109">Tamamlanmış çözüm aşağıdaki dizin yapısına sahiptir:</span><span class="sxs-lookup"><span data-stu-id="412e8-109">The completed solution has the following directory structure:</span></span>

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

<span data-ttu-id="412e8-110">Aşağıdaki yönergeler, test çözümünü oluşturmak için gereken adımları sağlar.</span><span class="sxs-lookup"><span data-stu-id="412e8-110">The following instructions provide the steps to create the test solution.</span></span> <span data-ttu-id="412e8-111">Test çözümünü tek bir adımda oluşturmaya yönelik yönergeler için bkz. [Test çözümü oluşturma komutları](#create-test-cmd) .</span><span class="sxs-lookup"><span data-stu-id="412e8-111">See [Commands to create test solution](#create-test-cmd) for instructions to create the test solution in one step.</span></span>

* <span data-ttu-id="412e8-112">Bir kabuk penceresi açın.</span><span class="sxs-lookup"><span data-stu-id="412e8-112">Open a shell window.</span></span>
* <span data-ttu-id="412e8-113">Şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="412e8-113">Run the following command:</span></span>

  ```dotnetcli
  dotnet new sln -o unit-testing-using-dotnet-test
  ```

  <span data-ttu-id="412e8-114">[`dotnet new sln`](../tools/dotnet-new.md) komutu, *birim-test-using-DotNet-test* dizininde yeni bir çözüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="412e8-114">The [`dotnet new sln`](../tools/dotnet-new.md) command creates a new solution in the *unit-testing-using-dotnet-test* directory.</span></span>
* <span data-ttu-id="412e8-115">Dizini *birim-test-using-DotNet-test* klasörü ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="412e8-115">Change directory to the *unit-testing-using-dotnet-test* folder.</span></span>
* <span data-ttu-id="412e8-116">Şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="412e8-116">Run the following command:</span></span>

  ```dotnetcli
  dotnet new classlib -o PrimeService
  ```

   <span data-ttu-id="412e8-117">[`dotnet new classlib`](../tools/dotnet-new.md) komutu, *primeservice* klasöründe yeni bir sınıf kitaplığı projesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="412e8-117">The [`dotnet new classlib`](../tools/dotnet-new.md) command creates a new class library project  in the *PrimeService* folder.</span></span> <span data-ttu-id="412e8-118">Yeni sınıf kitaplığı sınanacak kodu içerecektir.</span><span class="sxs-lookup"><span data-stu-id="412e8-118">The new class library will contain the code to be tested.</span></span>
* <span data-ttu-id="412e8-119">*Class1.cs* *olarak yeniden*adlandırın.</span><span class="sxs-lookup"><span data-stu-id="412e8-119">Rename *Class1.cs* to *PrimeService.cs*.</span></span>
* <span data-ttu-id="412e8-120">*PrimeService.cs* içindeki kodu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="412e8-120">Replace the code in *PrimeService.cs* with the following code:</span></span>
  
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

* <span data-ttu-id="412e8-121">Yukarıdaki kod:</span><span class="sxs-lookup"><span data-stu-id="412e8-121">The preceding code:</span></span>
  * <span data-ttu-id="412e8-122">Uygulanmadığını belirten bir ileti içeren bir <xref:System.NotImplementedException> oluşturur.</span><span class="sxs-lookup"><span data-stu-id="412e8-122">Throws a <xref:System.NotImplementedException> with a message indicating it's not implemented.</span></span>
  * <span data-ttu-id="412e8-123">, Öğreticide daha sonra güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="412e8-123">Is updated later in the tutorial.</span></span>

<!-- preceding code shows an english bias. Message makes no sense outside english -->

* <span data-ttu-id="412e8-124">*Birim-test-using-DotNet-test* dizini ' nde, sınıf kitaplığı projesini çözüme eklemek için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="412e8-124">In the *unit-testing-using-dotnet-test* directory, run the following command to add the class library project to the solution:</span></span>

  ```dotnetcli
  dotnet sln add ./PrimeService/PrimeService.csproj
  ```

* <span data-ttu-id="412e8-125">Aşağıdaki komutu çalıştırarak *Primeservice. Tests* projesini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="412e8-125">Create the *PrimeService.Tests* project by running the following command:</span></span>

  ```dotnetcli
  dotnet new xunit -o PrimeService.Tests
  ```

* <span data-ttu-id="412e8-126">Yukarıdaki komut:</span><span class="sxs-lookup"><span data-stu-id="412e8-126">The preceding command:</span></span>
  * <span data-ttu-id="412e8-127">*Primeservice* . *Tests projesindeki primeservice. Tests* projesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="412e8-127">Creates the *PrimeService.Tests* project in the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="412e8-128">Test projesi, test kitaplığı olarak [xUnit](https://xunit.github.io/) kullanır.</span><span class="sxs-lookup"><span data-stu-id="412e8-128">The test project uses [xUnit](https://xunit.github.io/) as the test library.</span></span>
  * <span data-ttu-id="412e8-129">, Aşağıdaki `<PackageReference />`öğelerini proje dosyasına ekleyerek Test Çalıştırıcısı 'nı yapılandırır:</span><span class="sxs-lookup"><span data-stu-id="412e8-129">Configures the test runner by adding the following `<PackageReference />`elements to the project file:</span></span>
    * <span data-ttu-id="412e8-130">"Microsoft. NET. test. SDK"</span><span class="sxs-lookup"><span data-stu-id="412e8-130">"Microsoft.NET.Test.Sdk"</span></span>
    * <span data-ttu-id="412e8-131">xUnit</span><span class="sxs-lookup"><span data-stu-id="412e8-131">"xunit"</span></span>
    * <span data-ttu-id="412e8-132">"xUnit. Runner. VisualStudio"</span><span class="sxs-lookup"><span data-stu-id="412e8-132">"xunit.runner.visualstudio"</span></span>

* <span data-ttu-id="412e8-133">Aşağıdaki komutu çalıştırarak test projesini çözüm dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="412e8-133">Add the test project to the solution file by running the following command:</span></span>

  ```dotnetcli
  dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
  ```

* <span data-ttu-id="412e8-134">`PrimeService` sınıf kitaplığını, *Primeservice. Tests* projesine bağımlılık olarak ekleyin:</span><span class="sxs-lookup"><span data-stu-id="412e8-134">Add the `PrimeService` class library as a dependency to the *PrimeService.Tests* project:</span></span>

  ```dotnetcli
  dotnet add ./PrimeService.Tests/PrimeService.Tests.csproj reference ./PrimeService/PrimeService.csproj  
  ```

<a name="create-test-cmd"></a>

### <a name="commands-to-create-the-solution"></a><span data-ttu-id="412e8-135">Çözüm oluşturma komutları</span><span class="sxs-lookup"><span data-stu-id="412e8-135">Commands to create the solution</span></span>

<span data-ttu-id="412e8-136">Bu bölüm, önceki bölümdeki tüm komutları özetler.</span><span class="sxs-lookup"><span data-stu-id="412e8-136">This section summarizes all the commands in the previous section.</span></span> <span data-ttu-id="412e8-137">Önceki bölümdeki adımları tamamladığınız takdirde bu bölümü atlayın.</span><span class="sxs-lookup"><span data-stu-id="412e8-137">Skip this section if you've completed the steps in the previous section.</span></span>

<span data-ttu-id="412e8-138">Aşağıdaki komutlar, bir Windows makinesinde test çözümünü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="412e8-138">The following commands create the test solution on a windows machine.</span></span> <span data-ttu-id="412e8-139">MacOS ve UNIX için, bir dosyayı yeniden adlandırmak üzere `ren` komutunu `ren` işletim sistemi sürümüne güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="412e8-139">For macOS and Unix, update the `ren` command to the OS version of `ren` to rename a file:</span></span>

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

<span data-ttu-id="412e8-140">Önceki bölümde " *PrimeService.cs* içindeki kodu aşağıdaki kodla değiştirin" yönergelerini izleyin.</span><span class="sxs-lookup"><span data-stu-id="412e8-140">Follow the instructions for "Replace the code in *PrimeService.cs* with the following code" in the previous section.</span></span>

## <a name="create-a-test"></a><span data-ttu-id="412e8-141">Test oluşturma</span><span class="sxs-lookup"><span data-stu-id="412e8-141">Create a test</span></span>

<span data-ttu-id="412e8-142">Test odaklı geliştirme (TDD) içinde popüler bir yaklaşım, hedef kodu uygulamadan önce bir test yazmaktır.</span><span class="sxs-lookup"><span data-stu-id="412e8-142">A popular approach in test driven development (TDD) is to write a test before implementing the target code.</span></span> <span data-ttu-id="412e8-143">Bu öğretici, TDD yaklaşımını kullanır.</span><span class="sxs-lookup"><span data-stu-id="412e8-143">This tutorial uses the TDD approach.</span></span> <span data-ttu-id="412e8-144">`IsPrime` yöntemi çağrılabilir, ancak uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="412e8-144">The `IsPrime` method is callable, but not implemented.</span></span> <span data-ttu-id="412e8-145">`IsPrime` için test çağrısı başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="412e8-145">A test call to `IsPrime` fails.</span></span> <span data-ttu-id="412e8-146">TDD ile başarısız olarak bilinen bir test yazılır.</span><span class="sxs-lookup"><span data-stu-id="412e8-146">With TDD, a test is written that is known to fail.</span></span> <span data-ttu-id="412e8-147">Hedef kodu test geçişini yapmak için güncellenir.</span><span class="sxs-lookup"><span data-stu-id="412e8-147">The target code is updated to make the test pass.</span></span> <span data-ttu-id="412e8-148">Bu yaklaşımı tekrarlayarak, başarısız bir test yazarak ve ardından hedef kodu geçirilecek şekilde güncelleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="412e8-148">You keep repeating this approach, writing a failing test and then updating the target code to pass.</span></span>

<span data-ttu-id="412e8-149">*Primeservice. Tests* projesini güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="412e8-149">Update the *PrimeService.Tests* project:</span></span>

* <span data-ttu-id="412e8-150">*Primeservice. Tests/UnitTest1. cs*öğesini silin.</span><span class="sxs-lookup"><span data-stu-id="412e8-150">Delete *PrimeService.Tests/UnitTest1.cs*.</span></span>
* <span data-ttu-id="412e8-151">Bir *Primeservice. Tests/PrimeService_IsPrimeShould. cs* dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="412e8-151">Create a *PrimeService.Tests/PrimeService_IsPrimeShould.cs*  file.</span></span>
* <span data-ttu-id="412e8-152">*PrimeService_IsPrimeShould. cs* içindeki kodu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="412e8-152">Replace the code in *PrimeService_IsPrimeShould.cs* with the following code:</span></span>

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

<span data-ttu-id="412e8-153">`[Fact]` özniteliği, Test Çalıştırıcısı tarafından çalıştırılan bir test yöntemi bildirir.</span><span class="sxs-lookup"><span data-stu-id="412e8-153">The `[Fact]` attribute declares a test method that's run by the test runner.</span></span> <span data-ttu-id="412e8-154">*Primeservice. Tests* klasöründen `dotnet test`çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="412e8-154">From the *PrimeService.Tests* folder, run `dotnet test`.</span></span> <span data-ttu-id="412e8-155">[DotNet test](../tools/dotnet-test.md) komutu her iki projeyi de oluşturur ve testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="412e8-155">The [dotnet test](../tools/dotnet-test.md) command builds both projects and runs the tests.</span></span> <span data-ttu-id="412e8-156">XUnit Test Çalıştırıcısı, testleri çalıştırmak için program giriş noktasını içerir.</span><span class="sxs-lookup"><span data-stu-id="412e8-156">The xUnit test runner contains the program entry point to run the tests.</span></span> <span data-ttu-id="412e8-157">`dotnet test`, Test Çalıştırıcısı birimini birim testi projesi kullanarak başlatır.</span><span class="sxs-lookup"><span data-stu-id="412e8-157">`dotnet test` starts the test runner using the unit test project.</span></span>

<span data-ttu-id="412e8-158">`IsPrime` uygulanmadığı için test başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="412e8-158">The test fails because `IsPrime` hasn't been implemented.</span></span> <span data-ttu-id="412e8-159">TDD yaklaşımını kullanarak, bu testin başarılı olması için yalnızca yeterli kodu yazın.</span><span class="sxs-lookup"><span data-stu-id="412e8-159">Using the TDD approach, write only enough code so this test passes.</span></span> <span data-ttu-id="412e8-160">`IsPrime` aşağıdaki kodla güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="412e8-160">Update `IsPrime` with the following code:</span></span>

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

<span data-ttu-id="412e8-161">`dotnet test`'i çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="412e8-161">Run `dotnet test`.</span></span> <span data-ttu-id="412e8-162">Test başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="412e8-162">The test passes.</span></span>

### <a name="add-more-tests"></a><span data-ttu-id="412e8-163">Daha fazla test ekleyin</span><span class="sxs-lookup"><span data-stu-id="412e8-163">Add more tests</span></span>

<span data-ttu-id="412e8-164">0 ve-1 için asal sayı testleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="412e8-164">Add prime number tests for 0 and -1.</span></span> <span data-ttu-id="412e8-165">Önceki testi kopyalayabilir ve aşağıdaki kodu 0 ve-1 kullanacak şekilde değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="412e8-165">You could copy the preceding test and change the following code to use 0 and -1:</span></span>

```csharp
var result = _primeService.IsPrime(1);

Assert.False(result, "1 should not be prime");
```

<span data-ttu-id="412e8-166">Yalnızca bir parametre değiştiğinde test kodu kopyalama, kod yineleme ve test blobunun sonuçlarını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="412e8-166">Copying test code when only a parameter changes results in code duplication and test bloat.</span></span> <span data-ttu-id="412e8-167">Aşağıdaki xUnit öznitelikleri benzer testlerin bir paketini yazmayı etkinleştirir:</span><span class="sxs-lookup"><span data-stu-id="412e8-167">The following xUnit attributes enable writing a suite of similar tests:</span></span>

- <span data-ttu-id="412e8-168">`[Theory]`, aynı kodu çalıştıran ancak farklı giriş bağımsız değişkenlerine sahip olan bir test paketini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="412e8-168">`[Theory]` represents a suite of tests that execute the same code but have different input arguments.</span></span>

- <span data-ttu-id="412e8-169">`[InlineData]` öznitelik, bu girişlerin değerlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="412e8-169">`[InlineData]` attribute specifies values for those inputs.</span></span>

<span data-ttu-id="412e8-170">Yeni test oluşturmak yerine, tek bir teorisi oluşturmak için önceki xUnit özniteliklerini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="412e8-170">Rather than creating new tests, apply the preceding xUnit attributes to create a single theory.</span></span> <span data-ttu-id="412e8-171">Aşağıdaki kodu değiştirin:</span><span class="sxs-lookup"><span data-stu-id="412e8-171">Replace the following code:</span></span>

```csharp
[Fact]
public void IsPrime_InputIs1_ReturnFalse()
{
    var result = _primeService.IsPrime(1);

    Assert.False(result, "1 should not be prime");
}
```

<span data-ttu-id="412e8-172">aşağıdaki kodla:</span><span class="sxs-lookup"><span data-stu-id="412e8-172">with the following code:</span></span>

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="412e8-173">Yukarıdaki kodda, `[Theory]` ve `[InlineData]` iki değerden küçük bir testi etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="412e8-173">In the preceding code, `[Theory]` and `[InlineData]` enable testing several values less than two.</span></span> <span data-ttu-id="412e8-174">İki, en küçük asal sayıdır.</span><span class="sxs-lookup"><span data-stu-id="412e8-174">Two is the smallest prime number.</span></span>

<span data-ttu-id="412e8-175">`dotnet test`çalıştırın, testlerin ikisi başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="412e8-175">Run `dotnet test`, two of the tests fail.</span></span> <span data-ttu-id="412e8-176">Tüm testlerin geçişini yapmak için `IsPrime` yöntemini aşağıdaki kodla güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="412e8-176">To make all of the tests pass, update the `IsPrime` method with the following code:</span></span>

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

<span data-ttu-id="412e8-177">TDD yaklaşımını izleyerek, daha fazla başarısız test ekleyin ve ardından hedef kodu güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="412e8-177">Following the TDD approach, add more failing tests, then update the target code.</span></span> <span data-ttu-id="412e8-178">[Testlerin tamamlanmış sürümüne](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) ve [kitaplığın tüm uygulamasına](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs)bakın.</span><span class="sxs-lookup"><span data-stu-id="412e8-178">See the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="412e8-179">Tamamlanan `IsPrime` yöntemi, test pridiklerine yönelik etkili bir algoritma değildir.</span><span class="sxs-lookup"><span data-stu-id="412e8-179">The completed `IsPrime` method is not an efficient algorithm for testing primality.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="412e8-180">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="412e8-180">Additional resources</span></span>

- [<span data-ttu-id="412e8-181">xUnit.net resmi site</span><span class="sxs-lookup"><span data-stu-id="412e8-181">xUnit.net official site</span></span>](https://xunit.github.io)
- [<span data-ttu-id="412e8-182">ASP.NET Core 'de test denetleyicisi mantığı</span><span class="sxs-lookup"><span data-stu-id="412e8-182">Testing controller logic in ASP.NET Core</span></span>](/aspnet/core/mvc/controllers/testing)
- [`dotnet add reference`](../tools/dotnet-add-reference.md)
