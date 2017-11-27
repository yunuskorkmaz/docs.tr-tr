---
title: "Birim .NET çekirdek dotnet test ve xUnit kullanarak C# kodu testi"
description: "Adım adım örnek çözüm oluşturma etkileşimli bir deneyim aracılığıyla C# ve .NET Core birim testi kavramları hakkında bilgi dotnet test ve xUnit kullanarak."
author: ardalis
ms.author: wiwagn
ms.date: 09/08/2017
ms.topic: article
ms.prod: .net-core
ms.openlocfilehash: 6e986e89d47ba4de9b8563f1a95cb1ae89accc89
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a><span data-ttu-id="8d0c8-103">Birim testi C# .NET çekirdek dotnet test ve xUnit kullanma</span><span class="sxs-lookup"><span data-stu-id="8d0c8-103">Unit testing C# in .NET Core using dotnet test and xUnit</span></span>

<span data-ttu-id="8d0c8-104">Bu öğretici birim testi kavramlarını öğrenmek için adım adım örnek çözüm oluşturma etkileşimli bir deneyim gösterir.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="8d0c8-105">Önceden oluşturulmuş bir çözümü kullanarak öğreticiyi izleyin tercih ediyorsanız [görüntülemek veya karşıdan örnek kod](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-using-dotnet-test/) başlamadan önce.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-using-dotnet-test/) before you begin.</span></span> <span data-ttu-id="8d0c8-106">Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="8d0c8-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="8d0c8-107">Kaynak projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="8d0c8-107">Creating the source project</span></span>

<span data-ttu-id="8d0c8-108">Kabuk penceresini açın.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-108">Open a shell window.</span></span> <span data-ttu-id="8d0c8-109">Adlı bir dizin oluşturun *birim testi-kullanma-dotnet-sınama* çözümü tutmak için.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-109">Create a directory called *unit-testing-using-dotnet-test* to hold the solution.</span></span>
<span data-ttu-id="8d0c8-110">Bu yeni dizin içinde çalıştırmak [ `dotnet new sln` ](../tools/dotnet-new.md) yeni bir çözüm oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="8d0c8-111">Bu sınıf kitaplığı ve birim testi projesi yönetmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-111">This makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="8d0c8-112">Çözüm dizini içinde oluşturmak bir *PrimeService* dizini.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-112">Inside the solution directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="8d0c8-113">Dizin ve dosya yapısı bugüne kadarki aşağıda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="8d0c8-113">The directory and file structure thus far is shown below:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

<span data-ttu-id="8d0c8-114">Olun *PrimeService* geçerli dizin ve çalışma [ `dotnet new classlib` ](../tools/dotnet-new.md) kaynak projesi oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-114">Make *PrimeService* the current directory and run [`dotnet new classlib`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="8d0c8-115">Yeniden Adlandır *Class1.cs* için *PrimeService.cs*.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-115">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="8d0c8-116">Teste dayalı geliştirme (TDD) kullanmak için başarısız olan uyarlamasını oluşturacaksınız `PrimeService` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="8d0c8-116">To use test-driven development (TDD), you'll create a failing implementation of the `PrimeService` class:</span></span>

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

<span data-ttu-id="8d0c8-117">Dizin geri değişiklik *birim testi-kullanma-dotnet-sınama* dizin.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-117">Change the directory back to the *unit-testing-using-dotnet-test* directory.</span></span> <span data-ttu-id="8d0c8-118">Çalıştırma [ `dotnet sln add .\PrimeService\PrimeService.csproj` ](../tools/dotnet-sln.md) sınıf kitaplığı proje çözüme eklemek için.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-118">Run [`dotnet sln add .\PrimeService\PrimeService.csproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="8d0c8-119">Test projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="8d0c8-119">Creating the test project</span></span>

<span data-ttu-id="8d0c8-120">Ardından, oluşturun *PrimeService.Tests* dizini.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-120">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="8d0c8-121">Aşağıdaki anahat dizin yapısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="8d0c8-121">The following outline shows the directory structure:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="8d0c8-122">Olun *PrimeService.Tests* dizine geçerli ve kullanarak yeni bir proje oluşturun [ `dotnet new xunit` ](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="8d0c8-122">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new xunit`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="8d0c8-123">Bu test kitaplık olarak xUnit kullanan bir test projesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-123">This creates a test project that uses xUnit as the test library.</span></span> <span data-ttu-id="8d0c8-124">Test Çalıştırıcısı'nda oluşturulan şablon yapılandırır *PrimeServiceTests.csproj*:</span><span class="sxs-lookup"><span data-stu-id="8d0c8-124">The generated template configures the test runner in the *PrimeServiceTests.csproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

<span data-ttu-id="8d0c8-125">Test projesi oluşturmak ve birim testleri çalıştırmak için diğer paketleri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-125">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="8d0c8-126">`dotnet new`Önceki adımda xUnit ve xUnit Çalıştırıcısı eklendi.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-126">`dotnet new` in the previous step added xUnit and the xUnit runner.</span></span> <span data-ttu-id="8d0c8-127">Şimdi, ekleyin `PrimeService` sınıf kitaplığı proje için başka bir bağımlılık olarak.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-127">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="8d0c8-128">Kullanım [ `dotnet add reference` ](../tools/dotnet-add-reference.md) komutu:</span><span class="sxs-lookup"><span data-stu-id="8d0c8-128">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="8d0c8-129">Tüm dosyasında görebilirsiniz [örnekleri deposu](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj) github'da.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-129">You can see the entire file in the [samples repository](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="8d0c8-130">Aşağıdakiler, nihai çözüm düzeni gösterilir:</span><span class="sxs-lookup"><span data-stu-id="8d0c8-130">The following shows the final solution layout:</span></span>

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

<span data-ttu-id="8d0c8-131">Yürütme [ `dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj` ](../tools/dotnet-sln.md) içinde *birim testi-kullanma-dotnet-sınama* dizin.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-131">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) in the *unit-testing-using-dotnet-test* directory.</span></span> 

## <a name="creating-the-first-test"></a><span data-ttu-id="8d0c8-132">İlk testi oluşturma</span><span class="sxs-lookup"><span data-stu-id="8d0c8-132">Creating the first test</span></span>

<span data-ttu-id="8d0c8-133">TDD yaklaşım geçirmek kolaylaştırarak ve süreci tekrarlayarak yazma bir başarısız test için çağırır.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-133">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="8d0c8-134">Kaldırma *UnitTest1.cs* gelen *PrimeService.Tests* dizin ve adlı yeni bir C# dosya oluşturma *PrimeService_IsPrimeShould.cs*.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-134">Remove *UnitTest1.cs* from the *PrimeService.Tests* directory and create a new C# file named *PrimeService_IsPrimeShould.cs*.</span></span> <span data-ttu-id="8d0c8-135">Aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8d0c8-135">Add the following code:</span></span>

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

<span data-ttu-id="8d0c8-136">`[Fact]` Özniteliği test Çalıştırıcısı tarafından çalıştırılan bir test yöntemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-136">The `[Fact]` attribute indicates a test method that is run by the test runner.</span></span> <span data-ttu-id="8d0c8-137">Gelen *birim testi-kullanma-dotnet-sınama*, yürütme [ `dotnet test` ](../tools/dotnet-test.md) testleri ve sınıf kitaplığı oluşturmak ve ardından testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-137">From the *unit-testing-using-dotnet-test*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="8d0c8-138">XUnit test Çalıştırıcısı testleri çalıştırmak için program giriş noktası içerir.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-138">The xUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="8d0c8-139">`dotnet test`oluşturduğunuz birim testi projesi kullanarak test Çalıştırıcısı başlatır.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-139">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="8d0c8-140">Testiniz başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-140">Your test fails.</span></span> <span data-ttu-id="8d0c8-141">Uygulama henüz oluşturmadınız.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-141">You haven't created the implementation yet.</span></span> <span data-ttu-id="8d0c8-142">Bu test basit kod yazarken yapmasına `PrimeService` çalışır sınıfı:</span><span class="sxs-lookup"><span data-stu-id="8d0c8-142">Make this test by writing the simplest code in the `PrimeService` class that works:</span></span>

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

<span data-ttu-id="8d0c8-143">İçinde *birim testi-kullanma-dotnet-sınama* çalışması dizini `dotnet test` yeniden.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-143">In the *unit-testing-using-dotnet-test* directory, run `dotnet test` again.</span></span> <span data-ttu-id="8d0c8-144">`dotnet test` Komutu çalıştıran bir yapı `PrimeService` proje ve ardından `PrimeService.Tests` projesi.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-144">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="8d0c8-145">Her iki proje oluşturduktan sonra bu tek bir test çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-145">After building both projects, it runs this single test.</span></span> <span data-ttu-id="8d0c8-146">Bunu geçirir.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-146">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="8d0c8-147">Daha fazla özellik ekleme</span><span class="sxs-lookup"><span data-stu-id="8d0c8-147">Adding more features</span></span>

<span data-ttu-id="8d0c8-148">Bir test geçirmek yapmış olduğunuz, daha fazla yazma zamanı geldi.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-148">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="8d0c8-149">Diğer basit bazı durumlar asal sayılar için vardır: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-149">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="8d0c8-150">Bu gibi durumlarda yeni testleriyle olarak ekleyebilirsiniz `[Fact]` özniteliği, ancak, hızlı hale can sıkıcı.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-150">You could add those cases as new tests with the `[Fact]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="8d0c8-151">Benzer testleri dizisi yazmak için etkinleştirmek diğer xUnit özniteliği vardır.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-151">There are other xUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="8d0c8-152">A `[Theory]` özniteliği, aynı kod yürütmek ancak farklı giriş bağımsız değişkeni olan testleri bir paketi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-152">A `[Theory]` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="8d0c8-153">Kullanabileceğiniz `[InlineData]` özniteliği bu girişleri için değerleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-153">You can use the `[InlineData]` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="8d0c8-154">Yeni testler oluşturmak yerine, tek bir kuramsal oluşturmak için bu iki öznitelikler uygulanır.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-154">Instead of creating new tests, apply these two attributes to create a single theory.</span></span> <span data-ttu-id="8d0c8-155">Teorik asal numarası en düşük olduğu birden fazla değer ikiden az, testleri bir yöntemi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="8d0c8-155">The theory is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="8d0c8-156">Çalıştırma `dotnet test`, ve bunların ikisini sınamaları başarısız.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-156">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="8d0c8-157">Tüm testleri geçişini yapmak için değiştirme `if` yöntemi başındaki yan tümcesi:</span><span class="sxs-lookup"><span data-stu-id="8d0c8-157">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="8d0c8-158">Daha fazla testleri, daha fazla kuramlarý ve daha fazla kod ana kitaplıkta ekleyerek yinelemek devam edin.</span><span class="sxs-lookup"><span data-stu-id="8d0c8-158">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="8d0c8-159">Sahip olduğunuz [testleri tamamlanmış sürümü](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) ve [kitaplığının tam uygulama](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).</span><span class="sxs-lookup"><span data-stu-id="8d0c8-159">You have the [finished version of the tests](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="8d0c8-160">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="8d0c8-160">Additional resources</span></span>

[<span data-ttu-id="8d0c8-161">ASP.NET Core test denetleyicisi mantığı</span><span class="sxs-lookup"><span data-stu-id="8d0c8-161">Testing controller logic in ASP.NET Core</span></span>](https://docs.microsoft.com/aspnet/core/mvc/controllers/testing)
