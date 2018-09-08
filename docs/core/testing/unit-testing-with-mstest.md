---
title: Birim testi MSTest ve .NET Core ile C#
description: Adım adım örnek bir çözüm oluşturmak bir etkileşimli deneyim C# ve .NET Core birim testi kavramları hakkında bilgi dotnet testi ve MSTest kullanarak.
author: ncarandini
ms.author: wiwagn
ms.date: 09/08/2017
ms.openlocfilehash: efeb12eb43539b0a85168b1162e0f8b94ad67e90
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44213838"
---
# <a name="unit-testing-c-with-mstest-and-net-core"></a><span data-ttu-id="a04b9-103">Birim testi MSTest ve .NET Core ile C#</span><span class="sxs-lookup"><span data-stu-id="a04b9-103">Unit testing C# with MSTest and .NET Core</span></span>

<span data-ttu-id="a04b9-104">Bu öğretici örnek bir çözüm birim testi kavramlarını öğrenmek için adım adım oluşturmaya etkileşimli deneyim gösterir.</span><span class="sxs-lookup"><span data-stu-id="a04b9-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="a04b9-105">Önceden oluşturulmuş bir çözümü kullanarak öğreticiyi uygulamak isterseniz [görüntülemek veya örnek kodu indirdikten](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/) başlamadan önce.</span><span class="sxs-lookup"><span data-stu-id="a04b9-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/) before you begin.</span></span> <span data-ttu-id="a04b9-106">Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="a04b9-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

### <a name="creating-the-source-project"></a><span data-ttu-id="a04b9-107">Kaynak proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="a04b9-107">Creating the source project</span></span>

<span data-ttu-id="a04b9-108">Shell penceresini açın.</span><span class="sxs-lookup"><span data-stu-id="a04b9-108">Open a shell window.</span></span> <span data-ttu-id="a04b9-109">Adlı bir dizin oluşturun *birim-test-kullanarak-mstest* çözüm tutacak.</span><span class="sxs-lookup"><span data-stu-id="a04b9-109">Create a directory called *unit-testing-using-mstest* to hold the solution.</span></span> <span data-ttu-id="a04b9-110">Bu yeni dizin içinde çalıştırma [ `dotnet new sln` ](../tools/dotnet-new.md) sınıf kitaplığı ve test projesi için yeni bir çözüm dosyası oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="a04b9-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution file for the class library and the test project.</span></span> <span data-ttu-id="a04b9-111">Ardından, oluşturun bir *PrimeService* dizin.</span><span class="sxs-lookup"><span data-stu-id="a04b9-111">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="a04b9-112">Aşağıdaki ana hat şimdiye kadarki dizin ve dosya yapısı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="a04b9-112">The following outline shows the directory and file structure thus far:</span></span>

```
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
```

<span data-ttu-id="a04b9-113">Olun *PrimeService* geçerli dizin ve çalışma [ `dotnet new classlib` ](../tools/dotnet-new.md) kaynak proje oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="a04b9-113">Make *PrimeService* the current directory and run [`dotnet new classlib`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="a04b9-114">Yeniden adlandırma *Class1.cs* için *PrimeService.cs*.</span><span class="sxs-lookup"><span data-stu-id="a04b9-114">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="a04b9-115">Teste dayalı geliştirme (TDD) kullanmak için bir başarısız uygulaması oluşturun. `PrimeService` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="a04b9-115">To use test-driven development (TDD), you create a failing implementation of the `PrimeService` class:</span></span>

```csharp
using System;

namespace Prime.Services
{
    public class PrimeService
    {
        public bool IsPrime(int candidate) 
        {
            throw new NotImplementedException("Please create a test first");
        } 
    }
}
```

<span data-ttu-id="a04b9-116">Dizine dön değişiklik *birim-test-kullanarak-mstest* dizin.</span><span class="sxs-lookup"><span data-stu-id="a04b9-116">Change the directory back to the *unit-testing-using-mstest* directory.</span></span> <span data-ttu-id="a04b9-117">Çalıştırma [ `dotnet sln add PrimeService/PrimeService.csproj` ](../tools/dotnet-sln.md) sınıf kitaplığı projesi çözüme eklemek için.</span><span class="sxs-lookup"><span data-stu-id="a04b9-117">Run [`dotnet sln add PrimeService/PrimeService.csproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span> 

### <a name="creating-the-test-project"></a><span data-ttu-id="a04b9-118">Test projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="a04b9-118">Creating the test project</span></span>

<span data-ttu-id="a04b9-119">Ardından, oluşturma *PrimeService.Tests* dizin.</span><span class="sxs-lookup"><span data-stu-id="a04b9-119">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="a04b9-120">Ana hat aşağıdaki dizin yapısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="a04b9-120">The following outline shows the directory structure:</span></span>

```
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="a04b9-121">Olun *PrimeService.Tests* dizini geçerli dizin ve kullanarak yeni bir proje oluşturma [ `dotnet new mstest` ](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="a04b9-121">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new mstest`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="a04b9-122">Dotnet yeni komut MStest test kitaplık olarak kullanan bir test projesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a04b9-122">The dotnet new command creates a test project that uses MStest as the test library.</span></span> <span data-ttu-id="a04b9-123">Test Çalıştırıcısı'nda oluşturulan şablon yapılandırır *PrimeServiceTests.csproj* dosyası:</span><span class="sxs-lookup"><span data-stu-id="a04b9-123">The generated template configures the test runner in the *PrimeServiceTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

<span data-ttu-id="a04b9-124">Test projesi oluşturma ve birim testlerini çalıştırmak için diğer paketleri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a04b9-124">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="a04b9-125">`dotnet new` Önceki adımda eklenen MSTest SDK'sı, MSTest framework ve MSTest Çalıştırıcısı sınayın.</span><span class="sxs-lookup"><span data-stu-id="a04b9-125">`dotnet new` in the previous step added the MSTest SDK, the MSTest test framework, and the MSTest runner.</span></span> <span data-ttu-id="a04b9-126">Şimdi ekleyin `PrimeService` sınıf kitaplığı projesine başka bir bağımlılık olarak.</span><span class="sxs-lookup"><span data-stu-id="a04b9-126">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="a04b9-127">Kullanım [ `dotnet add reference` ](../tools/dotnet-add-reference.md) komutu:</span><span class="sxs-lookup"><span data-stu-id="a04b9-127">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="a04b9-128">Dosyanın tamamını görebilirsiniz [örnekleri depomuzdan](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) GitHub üzerinde.</span><span class="sxs-lookup"><span data-stu-id="a04b9-128">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="a04b9-129">Aşağıdaki ana hat nihai çözüm düzeni gösterilir:</span><span class="sxs-lookup"><span data-stu-id="a04b9-129">The following outline shows the final solution layout:</span></span>

```
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

<span data-ttu-id="a04b9-130">Yürütme [ `dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj` ](../tools/dotnet-sln.md) içinde *birim testi-kullanarak-dotnet-test* dizin.</span><span class="sxs-lookup"><span data-stu-id="a04b9-130">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) in the *unit-testing-using-dotnet-test* directory.</span></span> 

## <a name="creating-the-first-test"></a><span data-ttu-id="a04b9-131">İlk testi oluşturma</span><span class="sxs-lookup"><span data-stu-id="a04b9-131">Creating the first test</span></span>

<span data-ttu-id="a04b9-132">TDD yaklaşım geçer hale getirme ve süreci tekrarlayarak yazma bir başarısız test için çağırır.</span><span class="sxs-lookup"><span data-stu-id="a04b9-132">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="a04b9-133">Kaldırma *UnitTest1.cs* gelen *PrimeService.Tests* dizin adlı yeni bir C# dosyası oluşturup *PrimeService_IsPrimeShould.cs* aşağıdaki içeriğe sahip:</span><span class="sxs-lookup"><span data-stu-id="a04b9-133">Remove *UnitTest1.cs* from the *PrimeService.Tests* directory and create a new C# file named *PrimeService_IsPrimeShould.cs* with the following content:</span></span>

```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    [TestClass]
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;

        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [TestMethod]
        public void ReturnFalseGivenValueOf1()
        {
            var result = _primeService.IsPrime(1);

            Assert.IsFalse(result, "1 should not be prime");
        }
    }
}
```

<span data-ttu-id="a04b9-134">`[TestClass]` Özniteliği birim testleri içeren bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="a04b9-134">The `[TestClass]` attribute denotes a class that contains unit tests.</span></span> <span data-ttu-id="a04b9-135">`[TestMethod]` Öznitelik, bir yöntemi olan bir test yöntemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="a04b9-135">The `[TestMethod]` attribute indicates a method is a test method.</span></span> 

<span data-ttu-id="a04b9-136">Bu dosyayı kaydedin ve yürütme [ `dotnet test` ](../tools/dotnet-test.md) testler ve sınıf kitaplığı oluşturun ve ardından testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a04b9-136">Save this file and execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="a04b9-137">Programın giriş noktası, testlerinizi çalıştırmak için MSTest test Çalıştırıcısı içerir.</span><span class="sxs-lookup"><span data-stu-id="a04b9-137">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="a04b9-138">`dotnet test` oluşturduğunuz birim test projesi kullanarak test Çalıştırıcısı'nı başlatır.</span><span class="sxs-lookup"><span data-stu-id="a04b9-138">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="a04b9-139">Test başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="a04b9-139">Your test fails.</span></span> <span data-ttu-id="a04b9-140">Uygulama henüz oluşturmadınız.</span><span class="sxs-lookup"><span data-stu-id="a04b9-140">You haven't created the implementation yet.</span></span> <span data-ttu-id="a04b9-141">En basit kod yazarak geçirmek bu testin geçmesini `PrimeService` çalışır sınıfı:</span><span class="sxs-lookup"><span data-stu-id="a04b9-141">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

```csharp
public bool IsPrime(int candidate)
{
    if (candidate == 1)
    {
        return false;
    }
    throw new NotImplementedException("Please create a test first");
}
```

<span data-ttu-id="a04b9-142">İçinde *birim-test-kullanarak-mstest* çalışması dizini `dotnet test` yeniden.</span><span class="sxs-lookup"><span data-stu-id="a04b9-142">In the *unit-testing-using-mstest* directory, run `dotnet test` again.</span></span> <span data-ttu-id="a04b9-143">`dotnet test` Komut çalıştıran bir derleme için `PrimeService` proje ve ardından `PrimeService.Tests` proje.</span><span class="sxs-lookup"><span data-stu-id="a04b9-143">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="a04b9-144">Her iki proje oluşturduktan sonra bu tek bir test çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="a04b9-144">After building both projects, it runs this single test.</span></span> <span data-ttu-id="a04b9-145">Bu geçirir.</span><span class="sxs-lookup"><span data-stu-id="a04b9-145">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="a04b9-146">Daha fazla özellik ekleme</span><span class="sxs-lookup"><span data-stu-id="a04b9-146">Adding more features</span></span>

<span data-ttu-id="a04b9-147">Bir test geçirmek yaptığınız, daha fazla yazmak için zaman var.</span><span class="sxs-lookup"><span data-stu-id="a04b9-147">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="a04b9-148">Diğer basit bazı durumlar için asal sayıları: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="a04b9-148">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="a04b9-149">Yeni testleriyle ekleyebilirsiniz `[TestMethod]` özniteliği ancak hızla olur yorucu bir süreç.</span><span class="sxs-lookup"><span data-stu-id="a04b9-149">You could add new tests with the `[TestMethod]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="a04b9-150">Benzer testleri paketi yazmanızı sağlayan diğer MSTest öznitelikleri vardır.</span><span class="sxs-lookup"><span data-stu-id="a04b9-150">There are other MSTest attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="a04b9-151">A `[DataTestMethod]`öznitelik aynı kod yürütün, ancak farklı giriş bağımsız değişkenleri olan testleri paketi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a04b9-151">A `[DataTestMethod]`attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="a04b9-152">Kullanabileceğiniz `[DataRow]` bu girişleri değerlerini belirtmek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a04b9-152">You can use the `[DataRow]` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="a04b9-153">Yeni testler oluşturmak yerine, bir tek veri tabanlı test oluşturmak için bu iki öznitelikler uygulanır.</span><span class="sxs-lookup"><span data-stu-id="a04b9-153">Instead of creating new tests, apply these two attributes to create a single data driven test.</span></span> <span data-ttu-id="a04b9-154">Test odaklı veri asal numarası en düşük olan değerlerden küçüktür iki test yöntemi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="a04b9-154">The data driven test is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="a04b9-155">Çalıştırma `dotnet test`, ve bunlardan ikisi başarısız test eder.</span><span class="sxs-lookup"><span data-stu-id="a04b9-155">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="a04b9-156">Tüm testler başarılı hale getirmek için değiştirme `if` yöntemin başında yan tümcesi:</span><span class="sxs-lookup"><span data-stu-id="a04b9-156">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="a04b9-157">Ana Kitaplığı'nda daha fazla test, daha fazla Teoriler ve daha fazla kod ekleyerek yinelemek devam edin.</span><span class="sxs-lookup"><span data-stu-id="a04b9-157">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="a04b9-158">Sahip olduğunuz [testlerinin tamamlanmış bir sürümünü](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) ve [Kitaplığı'nın tam bir uygulamaya](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs).</span><span class="sxs-lookup"><span data-stu-id="a04b9-158">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="a04b9-159">Küçük bir kitaplık ve bu kitaplık için birim testleri bir dizi oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="a04b9-159">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="a04b9-160">Böylece yeni paketler ekleme çözüm yapılandırılmış ve testleri normal iş akışı bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="a04b9-160">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="a04b9-161">Zaman ve çaba çözme hedeflerinden biri, uygulama üzerinde en yoğun.</span><span class="sxs-lookup"><span data-stu-id="a04b9-161">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
