---
title: Birim testi C# mstest'i ve .NET Core
description: "Adım adım örnek çözüm oluşturma etkileşimli bir deneyim aracılığıyla C# ve .NET Core birim testi kavramları hakkında bilgi dotnet test ve mstest'i kullanarak."
keywords: Mstest'i, .NET, .NET Core
author: ncarandini
ms.author: wiwagn
ms.date: 09/08/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: ed447641-3e85-4e50-b7ed-004630048a3e
ms.workload: dotnetcore
ms.openlocfilehash: 827f17a347a1a6c3830b2e7feb4de7781369a203
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="unit-testing-c-with-mstest-and-net-core"></a><span data-ttu-id="eb236-104">Birim testi C# mstest'i ve .NET Core</span><span class="sxs-lookup"><span data-stu-id="eb236-104">Unit testing C# with MSTest and .NET Core</span></span>

<span data-ttu-id="eb236-105">Bu öğretici birim testi kavramlarını öğrenmek için adım adım örnek çözüm oluşturma etkileşimli bir deneyim gösterir.</span><span class="sxs-lookup"><span data-stu-id="eb236-105">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="eb236-106">Önceden oluşturulmuş bir çözümü kullanarak öğreticiyi izleyin tercih ediyorsanız [görüntülemek veya karşıdan örnek kod](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/) başlamadan önce.</span><span class="sxs-lookup"><span data-stu-id="eb236-106">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/) before you begin.</span></span> <span data-ttu-id="eb236-107">Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="eb236-107">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

### <a name="creating-the-source-project"></a><span data-ttu-id="eb236-108">Kaynak projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="eb236-108">Creating the source project</span></span>

<span data-ttu-id="eb236-109">Kabuk penceresini açın.</span><span class="sxs-lookup"><span data-stu-id="eb236-109">Open a shell window.</span></span> <span data-ttu-id="eb236-110">Adlı bir dizin oluşturun *birim testi-kullanma-dotnet-sınama* çözümü tutmak için.</span><span class="sxs-lookup"><span data-stu-id="eb236-110">Create a directory called *unit-testing-using-dotnet-test* to hold the solution.</span></span> <span data-ttu-id="eb236-111">Bu yeni dizin içinde çalıştırmak [ `dotnet new sln` ](../tools/dotnet-new.md) sınıf kitaplığı ve test projesi için yeni bir çözüm dosyası oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="eb236-111">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution file for the class library and the test project.</span></span> <span data-ttu-id="eb236-112">Ardından, oluşturun bir *PrimeService* dizini.</span><span class="sxs-lookup"><span data-stu-id="eb236-112">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="eb236-113">Aşağıdaki anahat dizin ve dosya yapısı bugüne kadarki gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="eb236-113">The following outline shows the directory and file structure thus far:</span></span>

```
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
```

<span data-ttu-id="eb236-114">Olun *PrimeService* geçerli dizin ve çalışma [ `dotnet new classlib` ](../tools/dotnet-new.md) kaynak projesi oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="eb236-114">Make *PrimeService* the current directory and run [`dotnet new classlib`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="eb236-115">Yeniden Adlandır *Class1.cs* için *PrimeService.cs*.</span><span class="sxs-lookup"><span data-stu-id="eb236-115">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="eb236-116">Teste dayalı geliştirme (TDD) kullanmak için bir başarısız uygulaması oluşturun `PrimeService` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="eb236-116">To use test-driven development (TDD), you create a failing implementation of the `PrimeService` class:</span></span>

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

<span data-ttu-id="eb236-117">Dizin geri değişiklik *birim-test etme-kullanma-mstest'i* dizin.</span><span class="sxs-lookup"><span data-stu-id="eb236-117">Change the directory back to the *unit-testing-using-mstest* directory.</span></span> <span data-ttu-id="eb236-118">Çalıştırma [ `dotnet sln add PrimeService/PrimeService.csproj` ](../tools/dotnet-sln.md) sınıf kitaplığı proje çözüme eklemek için.</span><span class="sxs-lookup"><span data-stu-id="eb236-118">Run [`dotnet sln add PrimeService/PrimeService.csproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span> 

### <a name="creating-the-test-project"></a><span data-ttu-id="eb236-119">Test projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="eb236-119">Creating the test project</span></span>

<span data-ttu-id="eb236-120">Ardından, oluşturun *PrimeService.Tests* dizini.</span><span class="sxs-lookup"><span data-stu-id="eb236-120">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="eb236-121">Aşağıdaki anahat dizin yapısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="eb236-121">The following outline shows the directory structure:</span></span>

```
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="eb236-122">Olun *PrimeService.Tests* dizine geçerli ve kullanarak yeni bir proje oluşturun [ `dotnet new mstest` ](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="eb236-122">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new mstest`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="eb236-123">Dotnet yeni komutu mstest'i test kitaplığını kullanan bir test projesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="eb236-123">The dotnet new command creates a test project that uses MStest as the test library.</span></span> <span data-ttu-id="eb236-124">Test Çalıştırıcısı'nda oluşturulan şablon yapılandırır *PrimeServiceTests.csproj* dosyası:</span><span class="sxs-lookup"><span data-stu-id="eb236-124">The generated template configures the test runner in the *PrimeServiceTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

<span data-ttu-id="eb236-125">Test projesi oluşturmak ve birim testleri çalıştırmak için diğer paketleri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="eb236-125">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="eb236-126">`dotnet new`Önceki adımda eklenen framework ve mstest'i Çalıştırıcısı mstest'i SDK'sı, mstest'i test edin.</span><span class="sxs-lookup"><span data-stu-id="eb236-126">`dotnet new` in the previous step added the MSTest SDK, the MSTest test framework, and the MSTest runner.</span></span> <span data-ttu-id="eb236-127">Şimdi, ekleyin `PrimeService` sınıf kitaplığı proje için başka bir bağımlılık olarak.</span><span class="sxs-lookup"><span data-stu-id="eb236-127">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="eb236-128">Kullanım [ `dotnet add reference` ](../tools/dotnet-add-reference.md) komutu:</span><span class="sxs-lookup"><span data-stu-id="eb236-128">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="eb236-129">Tüm dosyasında görebilirsiniz [örnekleri deposu](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) github'da.</span><span class="sxs-lookup"><span data-stu-id="eb236-129">You can see the entire file in the [samples repository](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="eb236-130">Aşağıdaki anahat nihai çözüm düzeni gösterilir:</span><span class="sxs-lookup"><span data-stu-id="eb236-130">The following outline shows the final solution layout:</span></span>

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

<span data-ttu-id="eb236-131">Yürütme [ `dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj` ](../tools/dotnet-sln.md) içinde *birim testi-kullanma-dotnet-sınama* dizin.</span><span class="sxs-lookup"><span data-stu-id="eb236-131">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) in the *unit-testing-using-dotnet-test* directory.</span></span> 

## <a name="creating-the-first-test"></a><span data-ttu-id="eb236-132">İlk testi oluşturma</span><span class="sxs-lookup"><span data-stu-id="eb236-132">Creating the first test</span></span>

<span data-ttu-id="eb236-133">TDD yaklaşım geçirmek kolaylaştırarak ve süreci tekrarlayarak yazma bir başarısız test için çağırır.</span><span class="sxs-lookup"><span data-stu-id="eb236-133">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="eb236-134">Kaldırma *UnitTest1.cs* gelen *PrimeService.Tests* dizin ve adlı yeni bir C# dosya oluşturma *PrimeService_IsPrimeShould.cs* aşağıdaki içeriğe sahip:</span><span class="sxs-lookup"><span data-stu-id="eb236-134">Remove *UnitTest1.cs* from the *PrimeService.Tests* directory and create a new C# file named *PrimeService_IsPrimeShould.cs* with the following content:</span></span>

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

<span data-ttu-id="eb236-135">`[TestClass]` Özniteliği birim testleri içeren bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="eb236-135">The `[TestClass]` attribute denotes a class that contains unit tests.</span></span> <span data-ttu-id="eb236-136">`[TestMethod]` Öznitelik, bir yöntemdir test yöntemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="eb236-136">The `[TestMethod]` attribute indicates a method is a test method.</span></span> 

<span data-ttu-id="eb236-137">Bu dosyayı kaydedin ve yürütme [ `dotnet test` ](../tools/dotnet-test.md) testleri ve sınıf kitaplığı oluşturmak ve ardından testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="eb236-137">Save this file and execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="eb236-138">Mstest'i test Çalıştırıcısı testleri çalıştırmak için program giriş noktası içerir.</span><span class="sxs-lookup"><span data-stu-id="eb236-138">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="eb236-139">`dotnet test`oluşturduğunuz birim testi projesi kullanarak test Çalıştırıcısı başlatır.</span><span class="sxs-lookup"><span data-stu-id="eb236-139">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="eb236-140">Testiniz başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="eb236-140">Your test fails.</span></span> <span data-ttu-id="eb236-141">Uygulama henüz oluşturmadınız.</span><span class="sxs-lookup"><span data-stu-id="eb236-141">You haven't created the implementation yet.</span></span> <span data-ttu-id="eb236-142">En basit kod yazarak geçirmek bu testi yapmak `PrimeService` çalışır sınıfı:</span><span class="sxs-lookup"><span data-stu-id="eb236-142">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

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

<span data-ttu-id="eb236-143">İçinde *birim-test etme-kullanma-mstest'i* çalışması dizini `dotnet test` yeniden.</span><span class="sxs-lookup"><span data-stu-id="eb236-143">In the *unit-testing-using-mstest* directory, run `dotnet test` again.</span></span> <span data-ttu-id="eb236-144">`dotnet test` Komutu çalıştıran bir yapı `PrimeService` proje ve ardından `PrimeService.Tests` projesi.</span><span class="sxs-lookup"><span data-stu-id="eb236-144">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="eb236-145">Her iki proje oluşturduktan sonra bu tek bir test çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="eb236-145">After building both projects, it runs this single test.</span></span> <span data-ttu-id="eb236-146">Bunu geçirir.</span><span class="sxs-lookup"><span data-stu-id="eb236-146">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="eb236-147">Daha fazla özellik ekleme</span><span class="sxs-lookup"><span data-stu-id="eb236-147">Adding more features</span></span>

<span data-ttu-id="eb236-148">Bir test geçirmek yapmış olduğunuz, daha fazla yazma zamanı geldi.</span><span class="sxs-lookup"><span data-stu-id="eb236-148">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="eb236-149">Diğer basit bazı durumlar asal sayılar için vardır: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="eb236-149">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="eb236-150">Yeni testleriyle ekleyebilirsiniz `[TestMethod]` özniteliği, ancak, hızlı hale can sıkıcı.</span><span class="sxs-lookup"><span data-stu-id="eb236-150">You could add new tests with the `[TestMethod]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="eb236-151">Benzer testleri dizisi yazmak için etkinleştirmek diğer mstest'i özniteliği vardır.</span><span class="sxs-lookup"><span data-stu-id="eb236-151">There are other MSTest attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="eb236-152">A `[DataTestMethod]`özniteliği, aynı kod yürütmek ancak farklı giriş bağımsız değişkeni olan testleri bir paketi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="eb236-152">A `[DataTestMethod]`attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="eb236-153">Kullanabileceğiniz `[DataRow]` özniteliği bu girişleri için değerleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="eb236-153">You can use the `[DataRow]` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="eb236-154">Yeni testler oluşturmak yerine bir tek veri tabanlı testi oluşturmak için bu iki öznitelikler uygulanır.</span><span class="sxs-lookup"><span data-stu-id="eb236-154">Instead of creating new tests, apply these two attributes to create a single data driven test.</span></span> <span data-ttu-id="eb236-155">Veri tabanlı test düşük asal sayı olan çeşitli değerleri değerinden iki sınayan bir yöntemdir::</span><span class="sxs-lookup"><span data-stu-id="eb236-155">The data driven test is a method that tests several values less than two, which is the lowest prime number: :</span></span>

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="eb236-156">Çalıştırma `dotnet test`, ve bunların ikisini sınamaları başarısız.</span><span class="sxs-lookup"><span data-stu-id="eb236-156">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="eb236-157">Tüm testleri geçişini yapmak için değiştirme `if` yöntemi başındaki yan tümcesi:</span><span class="sxs-lookup"><span data-stu-id="eb236-157">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="eb236-158">Daha fazla testleri, daha fazla kuramlarý ve daha fazla kod ana kitaplıkta ekleyerek yinelemek devam edin.</span><span class="sxs-lookup"><span data-stu-id="eb236-158">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="eb236-159">Sahip olduğunuz [testleri tamamlanmış sürümü](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) ve [kitaplığının tam uygulama](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs).</span><span class="sxs-lookup"><span data-stu-id="eb236-159">You have the [finished version of the tests](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="eb236-160">Küçük bir kitaplığı ve bu kitaplık için birim testleri kümesini temel aldık.</span><span class="sxs-lookup"><span data-stu-id="eb236-160">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="eb236-161">Böylece yeni paketleri ekleme çözümü yapılandırılmış ve testleri normal iş akışı bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="eb236-161">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="eb236-162">Çoğu zaman ve çaba uygulama amaçlarını çözme üzerinde yoğunlaşmıştır.</span><span class="sxs-lookup"><span data-stu-id="eb236-162">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
