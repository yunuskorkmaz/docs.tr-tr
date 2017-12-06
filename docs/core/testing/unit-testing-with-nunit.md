---
title: Birim testi C# NUnit ve .NET Core
description: "Adım adım örnek çözüm oluşturma etkileşimli bir deneyim aracılığıyla C# ve .NET Core birim testi kavramları hakkında bilgi dotnet test ve NUnit kullanarak."
keywords: NUnit, .NET, .NET Core
author: rprouse
ms.date: 12/01/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.openlocfilehash: ad410497adc641e89bd9845ed69c063692ad2f73
ms.sourcegitcommit: 401c4427a3ec0d1263543033b3084039278509dc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/06/2017
---
# <a name="unit-testing-c-with-nunit-and-net-core"></a><span data-ttu-id="9a50f-104">Birim testi C# NUnit ve .NET Core</span><span class="sxs-lookup"><span data-stu-id="9a50f-104">Unit testing C# with NUnit and .NET Core</span></span>

<span data-ttu-id="9a50f-105">Bu öğretici birim testi kavramlarını öğrenmek için adım adım örnek çözüm oluşturma etkileşimli bir deneyim gösterir.</span><span class="sxs-lookup"><span data-stu-id="9a50f-105">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="9a50f-106">Önceden oluşturulmuş bir çözümü kullanarak öğreticiyi izleyin tercih ediyorsanız [görüntülemek veya karşıdan örnek kod](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-nunit/) başlamadan önce.</span><span class="sxs-lookup"><span data-stu-id="9a50f-106">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-nunit/) before you begin.</span></span> <span data-ttu-id="9a50f-107">Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="9a50f-107">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="9a50f-108">Kaynak projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="9a50f-108">Creating the source project</span></span>

<span data-ttu-id="9a50f-109">Kabuk penceresini açın.</span><span class="sxs-lookup"><span data-stu-id="9a50f-109">Open a shell window.</span></span> <span data-ttu-id="9a50f-110">Adlı bir dizin oluşturun *birim-test etme-kullanma-nunit* çözümü tutmak için.</span><span class="sxs-lookup"><span data-stu-id="9a50f-110">Create a directory called *unit-testing-using-nunit* to hold the solution.</span></span> <span data-ttu-id="9a50f-111">Bu yeni dizin içinde çalıştırmak [ `dotnet new sln` ](../tools/dotnet-new.md) sınıf kitaplığı ve test projesi için yeni bir çözüm dosyası oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="9a50f-111">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution file for the class library and the test project.</span></span> <span data-ttu-id="9a50f-112">Ardından, oluşturun bir *PrimeService* dizini.</span><span class="sxs-lookup"><span data-stu-id="9a50f-112">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="9a50f-113">Aşağıdaki anahat dizin ve dosya yapısı bugüne kadarki gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="9a50f-113">The following outline shows the directory and file structure thus far:</span></span>

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
```

<span data-ttu-id="9a50f-114">Olun *PrimeService* geçerli dizin ve çalışma [ `dotnet new classlib` ](../tools/dotnet-new.md) kaynak projesi oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="9a50f-114">Make *PrimeService* the current directory and run [`dotnet new classlib`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="9a50f-115">Yeniden Adlandır *Class1.cs* için *PrimeService.cs*.</span><span class="sxs-lookup"><span data-stu-id="9a50f-115">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="9a50f-116">Teste dayalı geliştirme (TDD) kullanmak için bir başarısız uygulaması oluşturun `PrimeService` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="9a50f-116">To use test-driven development (TDD), you create a failing implementation of the `PrimeService` class:</span></span>

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

<span data-ttu-id="9a50f-117">Dizin geri değişiklik *birim-test etme-kullanma-nunit* dizini.</span><span class="sxs-lookup"><span data-stu-id="9a50f-117">Change the directory back to the *unit-testing-using-nunit* directory.</span></span> <span data-ttu-id="9a50f-118">Çalıştırma [ `dotnet sln add PrimeService/PrimeService.csproj` ](../tools/dotnet-sln.md) sınıf kitaplığı proje çözüme eklemek için.</span><span class="sxs-lookup"><span data-stu-id="9a50f-118">Run [`dotnet sln add PrimeService/PrimeService.csproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="install-the-nunit-project-template"></a><span data-ttu-id="9a50f-119">NUnit proje şablonu yükleyin</span><span class="sxs-lookup"><span data-stu-id="9a50f-119">Install the NUnit project template</span></span>

<span data-ttu-id="9a50f-120">NUnit test projesi şablonları bir test projesi oluşturmadan önce yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="9a50f-120">The NUnit test project templates need to be installed before creating a test project.</span></span> <span data-ttu-id="9a50f-121">Bu yalnızca bir kez yeni NUnit projeleri oluşturacağınız her geliştirici makinede yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9a50f-121">This only needs to be done once on each developer machine where you'll create new NUnit projects.</span></span> <span data-ttu-id="9a50f-122">Çalıştırma [ `dotnet new -i NUnit3.DotNetNew.Template` ](../tools/dotnet-new.md) NUnit şablonları yüklemek için.</span><span class="sxs-lookup"><span data-stu-id="9a50f-122">Run [`dotnet new -i NUnit3.DotNetNew.Template`](../tools/dotnet-new.md) to install the NUnit templates.</span></span>

```
dotnet new -i NUnit3.DotNetNew.Template
```

### <a name="creating-the-test-project"></a><span data-ttu-id="9a50f-123">Test projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="9a50f-123">Creating the test project</span></span>

<span data-ttu-id="9a50f-124">Ardından, oluşturun *PrimeService.Tests* dizini.</span><span class="sxs-lookup"><span data-stu-id="9a50f-124">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="9a50f-125">Aşağıdaki anahat dizin yapısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="9a50f-125">The following outline shows the directory structure:</span></span>

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="9a50f-126">Olun *PrimeService.Tests* dizine geçerli ve kullanarak yeni bir proje oluşturun [ `dotnet new nunit` ](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="9a50f-126">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new nunit`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="9a50f-127">Dotnet yeni komutu NUnit test kitaplığını kullanan bir test projesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9a50f-127">The dotnet new command creates a test project that uses NUnit as the test library.</span></span> <span data-ttu-id="9a50f-128">Test Çalıştırıcısı'nda oluşturulan şablon yapılandırır *PrimeServiceTests.csproj* dosyası:</span><span class="sxs-lookup"><span data-stu-id="9a50f-128">The generated template configures the test runner in the *PrimeServiceTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

<span data-ttu-id="9a50f-129">Test projesi oluşturmak ve birim testleri çalıştırmak için diğer paketleri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9a50f-129">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="9a50f-130">`dotnet new`Önceki adımda Microsoft test SDK, NUnit test çerçevesi ve NUnit test bağdaştırıcısı eklendi.</span><span class="sxs-lookup"><span data-stu-id="9a50f-130">`dotnet new` in the previous step added the Microsoft test SDK, the NUnit test framework, and the NUnit test adapter.</span></span> <span data-ttu-id="9a50f-131">Şimdi, ekleyin `PrimeService` sınıf kitaplığı proje için başka bir bağımlılık olarak.</span><span class="sxs-lookup"><span data-stu-id="9a50f-131">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="9a50f-132">Kullanım [ `dotnet add reference` ](../tools/dotnet-add-reference.md) komutu:</span><span class="sxs-lookup"><span data-stu-id="9a50f-132">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="9a50f-133">Tüm dosyasında görebilirsiniz [örnekleri deposu](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj) github'da.</span><span class="sxs-lookup"><span data-stu-id="9a50f-133">You can see the entire file in the [samples repository](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="9a50f-134">Aşağıdaki anahat nihai çözüm düzeni gösterilir:</span><span class="sxs-lookup"><span data-stu-id="9a50f-134">The following outline shows the final solution layout:</span></span>

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

<span data-ttu-id="9a50f-135">Yürütme [ `dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj` ](../tools/dotnet-sln.md) içinde *birim testi-kullanma-dotnet-sınama* dizin.</span><span class="sxs-lookup"><span data-stu-id="9a50f-135">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) in the *unit-testing-using-dotnet-test* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="9a50f-136">İlk testi oluşturma</span><span class="sxs-lookup"><span data-stu-id="9a50f-136">Creating the first test</span></span>

<span data-ttu-id="9a50f-137">TDD yaklaşım geçirmek kolaylaştırarak ve süreci tekrarlayarak yazma bir başarısız test için çağırır.</span><span class="sxs-lookup"><span data-stu-id="9a50f-137">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="9a50f-138">Kaldırma *UnitTest1.cs* gelen *PrimeService.Tests* dizin ve adlı yeni bir C# dosya oluşturma *PrimeService_IsPrimeShould.cs* aşağıdaki içeriğe sahip:</span><span class="sxs-lookup"><span data-stu-id="9a50f-138">Remove *UnitTest1.cs* from the *PrimeService.Tests* directory and create a new C# file named *PrimeService_IsPrimeShould.cs* with the following content:</span></span>

```csharp
using NUnit.Framework;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    [TestFixture]
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;

        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [Test]
        public void ReturnFalseGivenValueOf1()
        {
            var result = _primeService.IsPrime(1);

            Assert.IsFalse(result, "1 should not be prime");
        }
    }
}
```

<span data-ttu-id="9a50f-139">`[TestFixture]` Özniteliği birim testleri içeren bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="9a50f-139">The `[TestFixture]` attribute denotes a class that contains unit tests.</span></span> <span data-ttu-id="9a50f-140">`[Test]` Öznitelik, bir yöntemdir test yöntemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9a50f-140">The `[Test]` attribute indicates a method is a test method.</span></span>

<span data-ttu-id="9a50f-141">Bu dosyayı kaydedin ve yürütme [ `dotnet test` ](../tools/dotnet-test.md) testleri ve sınıf kitaplığı oluşturmak ve ardından testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9a50f-141">Save this file and execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="9a50f-142">NUnit test Çalıştırıcısı testleri çalıştırmak için program giriş noktası içerir.</span><span class="sxs-lookup"><span data-stu-id="9a50f-142">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="9a50f-143">`dotnet test`oluşturduğunuz birim testi projesi kullanarak test Çalıştırıcısı başlatır.</span><span class="sxs-lookup"><span data-stu-id="9a50f-143">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="9a50f-144">Testiniz başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="9a50f-144">Your test fails.</span></span> <span data-ttu-id="9a50f-145">Uygulama henüz oluşturmadınız.</span><span class="sxs-lookup"><span data-stu-id="9a50f-145">You haven't created the implementation yet.</span></span> <span data-ttu-id="9a50f-146">En basit kod yazarak geçirmek bu testi yapmak `PrimeService` çalışır sınıfı:</span><span class="sxs-lookup"><span data-stu-id="9a50f-146">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

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

<span data-ttu-id="9a50f-147">İçinde *birim-test etme-kullanma-nunit* çalışması dizini `dotnet test` yeniden.</span><span class="sxs-lookup"><span data-stu-id="9a50f-147">In the *unit-testing-using-nunit* directory, run `dotnet test` again.</span></span> <span data-ttu-id="9a50f-148">`dotnet test` Komutu çalıştıran bir yapı `PrimeService` proje ve ardından `PrimeService.Tests` projesi.</span><span class="sxs-lookup"><span data-stu-id="9a50f-148">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="9a50f-149">Her iki proje oluşturduktan sonra bu tek bir test çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="9a50f-149">After building both projects, it runs this single test.</span></span> <span data-ttu-id="9a50f-150">Bunu geçirir.</span><span class="sxs-lookup"><span data-stu-id="9a50f-150">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="9a50f-151">Daha fazla özellik ekleme</span><span class="sxs-lookup"><span data-stu-id="9a50f-151">Adding more features</span></span>

<span data-ttu-id="9a50f-152">Bir test geçirmek yapmış olduğunuz, daha fazla yazma zamanı geldi.</span><span class="sxs-lookup"><span data-stu-id="9a50f-152">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="9a50f-153">Diğer basit bazı durumlar asal sayılar için vardır: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="9a50f-153">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="9a50f-154">Yeni testleriyle ekleyebilirsiniz `[Test]` özniteliği, ancak, hızlı hale can sıkıcı.</span><span class="sxs-lookup"><span data-stu-id="9a50f-154">You could add new tests with the `[Test]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="9a50f-155">Benzer testleri dizisi yazmak için etkinleştirmek diğer NUnit özniteliği vardır.</span><span class="sxs-lookup"><span data-stu-id="9a50f-155">There are other NUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="9a50f-156">A `[TestCase]` özniteliği, aynı kod yürütmek ancak farklı giriş bağımsız değişkeni olan testleri dizisi oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9a50f-156">A `[TestCase]` attribute is used to create a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="9a50f-157">Kullanabileceğiniz `[TestCase]` özniteliği bu girişleri için değerleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="9a50f-157">You can use the `[TestCase]` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="9a50f-158">Yeni testler oluşturmak yerine bir tek veri tabanlı testi oluşturmak için bu özniteliğini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="9a50f-158">Instead of creating new tests, apply this attribute to create a single data driven test.</span></span> <span data-ttu-id="9a50f-159">Test güdümlü veri asal numarası en düşük olduğu birden fazla değer ikiden az, testleri bir yöntemi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="9a50f-159">The data driven test is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="9a50f-160">Çalıştırma `dotnet test`, ve bunların ikisini sınamaları başarısız.</span><span class="sxs-lookup"><span data-stu-id="9a50f-160">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="9a50f-161">Tüm testleri geçişini yapmak için değiştirme `if` yöntemi başındaki yan tümcesi:</span><span class="sxs-lookup"><span data-stu-id="9a50f-161">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="9a50f-162">Daha fazla testleri, daha fazla kuramlarý ve daha fazla kod ana kitaplıkta ekleyerek yinelemek devam edin.</span><span class="sxs-lookup"><span data-stu-id="9a50f-162">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="9a50f-163">Sahip olduğunuz [testleri tamamlanmış sürümü](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs) ve [kitaplığının tam uygulama](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs).</span><span class="sxs-lookup"><span data-stu-id="9a50f-163">You have the [finished version of the tests](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="9a50f-164">Küçük bir kitaplığı ve bu kitaplık için birim testleri kümesini temel aldık.</span><span class="sxs-lookup"><span data-stu-id="9a50f-164">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="9a50f-165">Böylece yeni paketleri ekleme çözümü yapılandırılmış ve testleri normal iş akışı bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="9a50f-165">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="9a50f-166">Çoğu zaman ve çaba uygulama amaçlarını çözme üzerinde yoğunlaşmıştır.</span><span class="sxs-lookup"><span data-stu-id="9a50f-166">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
