---
title: C# kod dotnet testi ve xUnit kullanarak .NET Core birim testi
description: Adım adım örnek bir çözüm oluşturmak bir etkileşimli deneyim C# ve .NET Core birim testi kavramları hakkında bilgi dotnet testi ve xUnit kullanma.
author: ardalis
ms.author: wiwagn
ms.date: 11/29/2017
ms.custom: seodec18
ms.openlocfilehash: 97cf42c78154375ce06639d4a3029ed87b993ced
ms.sourcegitcommit: 8258515adc6c37ab6278e5a3d102d593246f8672
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58504359"
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a><span data-ttu-id="9f833-103">Birim testi C# .NET Core dotnet testi ve xUnit kullanma</span><span class="sxs-lookup"><span data-stu-id="9f833-103">Unit testing C# in .NET Core using dotnet test and xUnit</span></span>

<span data-ttu-id="9f833-104">Bu öğretici örnek bir çözüm birim testi kavramlarını öğrenmek için adım adım oluşturmaya etkileşimli deneyim gösterir.</span><span class="sxs-lookup"><span data-stu-id="9f833-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="9f833-105">Önceden oluşturulmuş bir çözümü kullanarak öğreticiyi uygulamak isterseniz [görüntülemek veya örnek kodu indirdikten](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/) başlamadan önce.</span><span class="sxs-lookup"><span data-stu-id="9f833-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/) before you begin.</span></span> <span data-ttu-id="9f833-106">Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="9f833-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="9f833-107">Kaynak proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="9f833-107">Creating the source project</span></span>

<span data-ttu-id="9f833-108">Shell penceresini açın.</span><span class="sxs-lookup"><span data-stu-id="9f833-108">Open a shell window.</span></span> <span data-ttu-id="9f833-109">Adlı bir dizin oluşturun *birim testi-kullanarak-dotnet-test* çözüm tutacak.</span><span class="sxs-lookup"><span data-stu-id="9f833-109">Create a directory called *unit-testing-using-dotnet-test* to hold the solution.</span></span>
<span data-ttu-id="9f833-110">Bu yeni dizin içinde çalıştırma [ `dotnet new sln` ](../tools/dotnet-new.md) yeni bir çözüm oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="9f833-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="9f833-111">Bir çözüm olan sınıf kitaplığı hem birim test projesi yönetmenizi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="9f833-111">Having a solution makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="9f833-112">Çözüm dizini içinde bir *PrimeService* dizin.</span><span class="sxs-lookup"><span data-stu-id="9f833-112">Inside the solution directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="9f833-113">Şimdiye kadar dizin ve dosya yapısı şu şekilde olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="9f833-113">The directory and file structure thus far should be as follows:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

<span data-ttu-id="9f833-114">Olun *PrimeService* geçerli dizin ve çalışma [ `dotnet new classlib` ](../tools/dotnet-new.md) kaynak proje oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="9f833-114">Make *PrimeService* the current directory and run [`dotnet new classlib`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="9f833-115">Yeniden adlandırma *Class1.cs* için *PrimeService.cs*.</span><span class="sxs-lookup"><span data-stu-id="9f833-115">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="9f833-116">Öncelikle bir başarısız uygulaması oluşturmanız `PrimeService` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="9f833-116">You first create a failing implementation of the `PrimeService` class:</span></span>

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

<span data-ttu-id="9f833-117">Dizine dön değişiklik *birim testi-kullanarak-dotnet-test* dizin.</span><span class="sxs-lookup"><span data-stu-id="9f833-117">Change the directory back to the *unit-testing-using-dotnet-test* directory.</span></span>

<span data-ttu-id="9f833-118">Çalıştırma [dotnet sln](../tools/dotnet-sln.md) sınıf kitaplığı projesi çözüme eklenecek komut:</span><span class="sxs-lookup"><span data-stu-id="9f833-118">Run the [dotnet sln](../tools/dotnet-sln.md) command to add the class library project to the solution:</span></span>

```
dotnet sln add ./PrimeService/PrimeService.csproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="9f833-119">Test projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="9f833-119">Creating the test project</span></span>

<span data-ttu-id="9f833-120">Ardından, oluşturma *PrimeService.Tests* dizin.</span><span class="sxs-lookup"><span data-stu-id="9f833-120">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="9f833-121">Ana hat aşağıdaki dizin yapısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="9f833-121">The following outline shows the directory structure:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="9f833-122">Olun *PrimeService.Tests* dizini geçerli dizin ve kullanarak yeni bir proje oluşturma [ `dotnet new xunit` ](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="9f833-122">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new xunit`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="9f833-123">Bu komut, kullanan bir test projesi oluşturur. [xUnit](https://xunit.github.io/) test kitaplığı olarak.</span><span class="sxs-lookup"><span data-stu-id="9f833-123">This command creates a test project that uses [xUnit](https://xunit.github.io/) as the test library.</span></span> <span data-ttu-id="9f833-124">Test Çalıştırıcısı'nda oluşturulan şablon yapılandırır *PrimeServiceTests.csproj* aşağıdaki koda benzer dosya:</span><span class="sxs-lookup"><span data-stu-id="9f833-124">The generated template configures the test runner in the *PrimeServiceTests.csproj* file similar to the following code:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

<span data-ttu-id="9f833-125">Test projesi oluşturma ve birim testlerini çalıştırmak için diğer paketleri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9f833-125">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="9f833-126">`dotnet new` Önceki adımda, xUnit ve xUnit Çalıştırıcısı eklendi.</span><span class="sxs-lookup"><span data-stu-id="9f833-126">`dotnet new` in the previous step added xUnit and the xUnit runner.</span></span> <span data-ttu-id="9f833-127">Şimdi ekleyin `PrimeService` sınıf kitaplığı projesine başka bir bağımlılık olarak.</span><span class="sxs-lookup"><span data-stu-id="9f833-127">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="9f833-128">Kullanım [ `dotnet add reference` ](../tools/dotnet-add-reference.md) komutu:</span><span class="sxs-lookup"><span data-stu-id="9f833-128">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="9f833-129">Dosyanın tamamını görebilirsiniz [örnekleri depomuzdan](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj) GitHub üzerinde.</span><span class="sxs-lookup"><span data-stu-id="9f833-129">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="9f833-130">Aşağıda, nihai çözüm Düzen gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="9f833-130">The following shows the final solution layout:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

<span data-ttu-id="9f833-131">Test projesi çözüme eklemek için çalıştırın [dotnet sln](../tools/dotnet-sln.md) komutunu *birim testi-kullanarak-dotnet-test* dizini:</span><span class="sxs-lookup"><span data-stu-id="9f833-131">To add the test project to the solution, run the [dotnet sln](../tools/dotnet-sln.md) command in the *unit-testing-using-dotnet-test* directory:</span></span>

```
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="9f833-132">İlk testi oluşturma</span><span class="sxs-lookup"><span data-stu-id="9f833-132">Creating the first test</span></span>

<span data-ttu-id="9f833-133">Bir yazma, test başarısız kolaylaştırır geçişi, sonra işlemi yineleyin.</span><span class="sxs-lookup"><span data-stu-id="9f833-133">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="9f833-134">Kaldırma *UnitTest1.cs* gelen *PrimeService.Tests* dizin ve yeni bir C# adlı dosya *PrimeService_IsPrimeShould.cs*.</span><span class="sxs-lookup"><span data-stu-id="9f833-134">Remove *UnitTest1.cs* from the *PrimeService.Tests* directory and create a new C# file named *PrimeService_IsPrimeShould.cs*.</span></span> <span data-ttu-id="9f833-135">Aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="9f833-135">Add the following code:</span></span>

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
        public void ReturnFalseGivenValueOf1()
        {
            var result = _primeService.IsPrime(1);

            Assert.False(result, "1 should not be prime");
        }
    }
}
```

<span data-ttu-id="9f833-136">`[Fact]` Test Çalıştırıcısı tarafından yürütülen bir test metodu özniteliği gösterir.</span><span class="sxs-lookup"><span data-stu-id="9f833-136">The `[Fact]` attribute indicates a test method that is run by the test runner.</span></span> <span data-ttu-id="9f833-137">Gelen *PrimeService.Tests* klasöründe yürütme [ `dotnet test` ](../tools/dotnet-test.md) testler ve sınıf kitaplığı oluşturun ve ardından testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9f833-137">From the *PrimeService.Tests* folder, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="9f833-138">XUnit test Çalıştırıcısı, testlerinizi çalıştırmak için programın giriş noktası içerir.</span><span class="sxs-lookup"><span data-stu-id="9f833-138">The xUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="9f833-139">`dotnet test` oluşturduğunuz birim test projesi kullanarak test Çalıştırıcısı'nı başlatır.</span><span class="sxs-lookup"><span data-stu-id="9f833-139">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="9f833-140">Test başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="9f833-140">Your test fails.</span></span> <span data-ttu-id="9f833-141">Uygulama henüz oluşturmadınız.</span><span class="sxs-lookup"><span data-stu-id="9f833-141">You haven't created the implementation yet.</span></span> <span data-ttu-id="9f833-142">En basit kod yazarak geçirmek bu testin geçmesini `PrimeService` çalışır sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9f833-142">Make this test pass by writing the simplest code in the `PrimeService` class that works.</span></span> <span data-ttu-id="9f833-143">Varolan `IsPrime` yöntemi uygulamasını aşağıdaki kod ile:</span><span class="sxs-lookup"><span data-stu-id="9f833-143">Replace the existing `IsPrime` method implementation with the following code:</span></span>

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

<span data-ttu-id="9f833-144">İçinde *PrimeService.Tests* çalışması dizini `dotnet test` yeniden.</span><span class="sxs-lookup"><span data-stu-id="9f833-144">In the *PrimeService.Tests* directory, run `dotnet test` again.</span></span> <span data-ttu-id="9f833-145">`dotnet test` Komut çalıştıran bir derleme için `PrimeService` proje ve ardından `PrimeService.Tests` proje.</span><span class="sxs-lookup"><span data-stu-id="9f833-145">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="9f833-146">Her iki proje oluşturduktan sonra bu tek bir test çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="9f833-146">After building both projects, it runs this single test.</span></span> <span data-ttu-id="9f833-147">Bu geçirir.</span><span class="sxs-lookup"><span data-stu-id="9f833-147">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="9f833-148">Daha fazla özellik ekleme</span><span class="sxs-lookup"><span data-stu-id="9f833-148">Adding more features</span></span>

<span data-ttu-id="9f833-149">Bir test geçirmek yaptığınız, daha fazla yazmak için zaman var.</span><span class="sxs-lookup"><span data-stu-id="9f833-149">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="9f833-150">Birkaç basit durumlardaysa asal sayıları için vardır: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="9f833-150">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="9f833-151">Bu gibi durumlarda, yeni testleriyle olarak ekleyebilirsiniz `[Fact]` özniteliği ancak hızla olur yorucu bir süreç.</span><span class="sxs-lookup"><span data-stu-id="9f833-151">You could add those cases as new tests with the `[Fact]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="9f833-152">Benzer testleri paketi yazmanızı sağlayan diğer xUnit öznitelikleri vardır:</span><span class="sxs-lookup"><span data-stu-id="9f833-152">There are other xUnit attributes that enable you to write a suite of similar tests:</span></span>

- <span data-ttu-id="9f833-153">`[Theory]` aynı kod yürütün, ancak farklı giriş bağımsız değişkenleri olan testleri paketi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9f833-153">`[Theory]` represents a suite of tests that execute the same code but have different input arguments.</span></span>

- <span data-ttu-id="9f833-154">`[InlineData]` özniteliği, bu girişleri için değerleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="9f833-154">`[InlineData]` attribute specifies values for those inputs.</span></span>

<span data-ttu-id="9f833-155">Yeni testler oluşturmak yerine, bu iki öznitelik geçerli `[Theory]` ve `[InlineData]`tek bir teorik olarak oluşturmak için *PrimeService_IsPrimeShould.cs* dosya.</span><span class="sxs-lookup"><span data-stu-id="9f833-155">Instead of creating new tests, apply these two attributes, `[Theory]` and `[InlineData]`, to create a single theory in the *PrimeService_IsPrimeShould.cs* file.</span></span> <span data-ttu-id="9f833-156">Teorik asal numarası en düşük olan değerlerden küçüktür iki test yöntemi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="9f833-156">The theory is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="9f833-157">Çalıştırma `dotnet test` yeniden ve iki bu testler başarısız olması.</span><span class="sxs-lookup"><span data-stu-id="9f833-157">Run `dotnet test` again, and two of these tests should fail.</span></span> <span data-ttu-id="9f833-158">Tüm testleri geçer hale getirmek için değiştirme `if` başındaki yan tümcesi `IsPrime` yönteminde *PrimeService.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="9f833-158">To make all of the tests pass, change the `if` clause at the beginning of the `IsPrime` method in the *PrimeService.cs* file:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="9f833-159">Ana Kitaplığı'nda daha fazla test, daha fazla Teoriler ve daha fazla kod ekleyerek yinelemek devam edin.</span><span class="sxs-lookup"><span data-stu-id="9f833-159">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="9f833-160">Sahip olduğunuz [testlerinin tamamlanmış bir sürümünü](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) ve [Kitaplığı'nın tam bir uygulamaya](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).</span><span class="sxs-lookup"><span data-stu-id="9f833-160">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="9f833-161">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="9f833-161">Additional resources</span></span>

- [<span data-ttu-id="9f833-162">xUnit.net resmi sitesi</span><span class="sxs-lookup"><span data-stu-id="9f833-162">xUnit.net official site</span></span>](https://xunit.github.io)
- [<span data-ttu-id="9f833-163">ASP.NET Core test denetleyici mantığında</span><span class="sxs-lookup"><span data-stu-id="9f833-163">Testing controller logic in ASP.NET Core</span></span>](/aspnet/core/mvc/controllers/testing)
