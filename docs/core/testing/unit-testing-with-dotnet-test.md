---
title: DotNet test C# ve xUnit kullanarak .NET Core 'da birim testi kodu
description: Ve .NET Core 'daki C# birim testi kavramlarını, DotNet test ve xUnit kullanarak örnek bir çözüm oluşturma adlı etkileşimli bir deneyim aracılığıyla öğrenin.
author: ardalis
ms.author: wiwagn
ms.date: 11/29/2017
ms.custom: seodec18
ms.openlocfilehash: 1a6c8ed515e62bed921290a54e3d9687bb889a4d
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2019
ms.locfileid: "70374147"
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a><span data-ttu-id="3ced9-103">DotNet test C# ve xUnit kullanarak .NET Core 'da birim testi</span><span class="sxs-lookup"><span data-stu-id="3ced9-103">Unit testing C# in .NET Core using dotnet test and xUnit</span></span>

<span data-ttu-id="3ced9-104">Bu öğreticide, birim testi kavramlarını öğrenmek için bir örnek çözüm oluşturma adım adım yönergeler sunarak etkileşimli bir deneyim sağlanır.</span><span class="sxs-lookup"><span data-stu-id="3ced9-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="3ced9-105">Önceden oluşturulmuş bir çözüm kullanarak öğreticiyi izlemeyi tercih ediyorsanız, başlamadan önce [örnek kodu görüntüleyin veya indirin](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/) .</span><span class="sxs-lookup"><span data-stu-id="3ced9-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/) before you begin.</span></span> <span data-ttu-id="3ced9-106">İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="3ced9-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="creating-the-source-project"></a><span data-ttu-id="3ced9-107">Kaynak proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="3ced9-107">Creating the source project</span></span>

<span data-ttu-id="3ced9-108">Bir kabuk penceresi açın.</span><span class="sxs-lookup"><span data-stu-id="3ced9-108">Open a shell window.</span></span> <span data-ttu-id="3ced9-109">Çözümü tutmak için *birim-test-using-DotNet-test* adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3ced9-109">Create a directory called *unit-testing-using-dotnet-test* to hold the solution.</span></span>
<span data-ttu-id="3ced9-110">Yeni bir çözüm oluşturmak için bu [`dotnet new sln`](../tools/dotnet-new.md) yeni dizinin içinde öğesini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3ced9-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="3ced9-111">Bir çözüme sahip olmak, hem sınıf kitaplığını hem de birim testi projesini yönetmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="3ced9-111">Having a solution makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="3ced9-112">Çözüm dizini içinde bir *Primeservice* dizini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3ced9-112">Inside the solution directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="3ced9-113">Bu nedenle, dizin ve dosya yapısı şu şekilde olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="3ced9-113">The directory and file structure thus far should be as follows:</span></span>

```console
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

<span data-ttu-id="3ced9-114">Kaynak projeyi oluşturmak için *primeservice* 'i geçerli [`dotnet new classlib`](../tools/dotnet-new.md) Dizin yapın ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3ced9-114">Make *PrimeService* the current directory and run [`dotnet new classlib`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="3ced9-115">*Class1.cs* *olarak yeniden*adlandırın.</span><span class="sxs-lookup"><span data-stu-id="3ced9-115">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="3ced9-116">Önce `PrimeService` sınıfın başarısız bir uygulamasını oluşturursunuz:</span><span class="sxs-lookup"><span data-stu-id="3ced9-116">You first create a failing implementation of the `PrimeService` class:</span></span>

```csharp
using System;

namespace Prime.Services
{
    public class PrimeService
    {
        public bool IsPrime(int candidate)
        {
            throw new NotImplementedException("Please create a test first.");
        }
    }
}
```

<span data-ttu-id="3ced9-117">Dizini *birim-test-using-DotNet-test* dizinine geri çevirin.</span><span class="sxs-lookup"><span data-stu-id="3ced9-117">Change the directory back to the *unit-testing-using-dotnet-test* directory.</span></span>

<span data-ttu-id="3ced9-118">Sınıf Kitaplığı projesini çözüme eklemek için [DotNet sln](../tools/dotnet-sln.md) komutunu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="3ced9-118">Run the [dotnet sln](../tools/dotnet-sln.md) command to add the class library project to the solution:</span></span>

```console
dotnet sln add ./PrimeService/PrimeService.csproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="3ced9-119">Test projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="3ced9-119">Creating the test project</span></span>

<span data-ttu-id="3ced9-120">Ardından, *Primeservice. Tests* dizinini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3ced9-120">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="3ced9-121">Aşağıdaki ana hat dizin yapısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="3ced9-121">The following outline shows the directory structure:</span></span>

```console
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="3ced9-122">*Primeservice. test* dizinini geçerli dizini yapın ve kullanarak [`dotnet new xunit`](../tools/dotnet-new.md)yeni bir proje oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3ced9-122">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new xunit`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="3ced9-123">Bu komut, test kitaplığı olarak [xUnit](https://xunit.github.io/) kullanan bir test projesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3ced9-123">This command creates a test project that uses [xUnit](https://xunit.github.io/) as the test library.</span></span> <span data-ttu-id="3ced9-124">Oluşturulan şablon, *Primeservicetests. csproj* dosyasında aşağıdaki koda benzer Test Çalıştırıcısı 'nı yapılandırır:</span><span class="sxs-lookup"><span data-stu-id="3ced9-124">The generated template configures the test runner in the *PrimeServiceTests.csproj* file similar to the following code:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

<span data-ttu-id="3ced9-125">Test projesi, birim testlerini oluşturmak ve çalıştırmak için diğer paketlerin kullanılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3ced9-125">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="3ced9-126">`dotnet new`önceki adımda xUnit ve xUnit Çalıştırıcısı eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="3ced9-126">`dotnet new` in the previous step added xUnit and the xUnit runner.</span></span> <span data-ttu-id="3ced9-127">Şimdi, `PrimeService` sınıf kitaplığını projeye başka bir bağımlılık olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3ced9-127">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="3ced9-128">[`dotnet add reference`](../tools/dotnet-add-reference.md) Şu komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="3ced9-128">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```console
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="3ced9-129">GitHub 'daki [örnekler deposunda](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj) dosyanın tamamını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3ced9-129">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="3ced9-130">Son çözüm düzeni aşağıda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="3ced9-130">The following shows the final solution layout:</span></span>

```console
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

<span data-ttu-id="3ced9-131">Çözüme test projesi eklemek için, *birim-test-using-DotNet-test* dizininde [DotNet sln](../tools/dotnet-sln.md) komutunu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="3ced9-131">To add the test project to the solution, run the [dotnet sln](../tools/dotnet-sln.md) command in the *unit-testing-using-dotnet-test* directory:</span></span>

```console
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="3ced9-132">İlk test oluşturma</span><span class="sxs-lookup"><span data-stu-id="3ced9-132">Creating the first test</span></span>

<span data-ttu-id="3ced9-133">Başarısız bir test yazdığınızda, geçişi yapıp işlemi tekrarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3ced9-133">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="3ced9-134">*UnitTest1.cs* öğesini *primeservice. Tests* dizininden kaldırın ve *PrimeService_IsPrimeShould. cs*adlı C# yeni bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3ced9-134">Remove *UnitTest1.cs* from the *PrimeService.Tests* directory and create a new C# file named *PrimeService_IsPrimeShould.cs*.</span></span> <span data-ttu-id="3ced9-135">Aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="3ced9-135">Add the following code:</span></span>

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

<span data-ttu-id="3ced9-136">`[Fact]` Özniteliği, Test Çalıştırıcısı tarafından çalıştırılan bir test yöntemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3ced9-136">The `[Fact]` attribute indicates a test method that is run by the test runner.</span></span> <span data-ttu-id="3ced9-137">*Primeservice. Tests* klasöründen, testleri ve sınıf [`dotnet test`](../tools/dotnet-test.md) kitaplığını oluşturmak için yürütün ve ardından testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3ced9-137">From the *PrimeService.Tests* folder, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="3ced9-138">XUnit Test Çalıştırıcısı, testlerinizi çalıştırmak için program giriş noktasını içerir.</span><span class="sxs-lookup"><span data-stu-id="3ced9-138">The xUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="3ced9-139">`dotnet test`oluşturduğunuz birim test projesini kullanarak Test Çalıştırıcısı başlatır.</span><span class="sxs-lookup"><span data-stu-id="3ced9-139">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="3ced9-140">Testiniz başarısız oluyor.</span><span class="sxs-lookup"><span data-stu-id="3ced9-140">Your test fails.</span></span> <span data-ttu-id="3ced9-141">Uygulamayı henüz oluşturmadınız.</span><span class="sxs-lookup"><span data-stu-id="3ced9-141">You haven't created the implementation yet.</span></span> <span data-ttu-id="3ced9-142">Bu test geçişini, en basit kodu `PrimeService` çalıştıran sınıfa yazarak yapın.</span><span class="sxs-lookup"><span data-stu-id="3ced9-142">Make this test pass by writing the simplest code in the `PrimeService` class that works.</span></span> <span data-ttu-id="3ced9-143">Mevcut `IsPrime` Yöntem uygulamasını şu kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="3ced9-143">Replace the existing `IsPrime` method implementation with the following code:</span></span>

```csharp
public bool IsPrime(int candidate)
{
    if (candidate == 1)
    {
        return false;
    }
    throw new NotImplementedException("Please create a test first.");
}
```

<span data-ttu-id="3ced9-144">*Primeservice. Tests* dizininde yeniden çalıştırın `dotnet test` .</span><span class="sxs-lookup"><span data-stu-id="3ced9-144">In the *PrimeService.Tests* directory, run `dotnet test` again.</span></span> <span data-ttu-id="3ced9-145">Komutu, `PrimeService` proje için bir yapı ve ardından projeiçinçalışır.`PrimeService.Tests` `dotnet test`</span><span class="sxs-lookup"><span data-stu-id="3ced9-145">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="3ced9-146">Her iki proje de oluşturulduktan sonra bu tek testi çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="3ced9-146">After building both projects, it runs this single test.</span></span> <span data-ttu-id="3ced9-147">Geçirir.</span><span class="sxs-lookup"><span data-stu-id="3ced9-147">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="3ced9-148">Daha fazla özellik ekleme</span><span class="sxs-lookup"><span data-stu-id="3ced9-148">Adding more features</span></span>

<span data-ttu-id="3ced9-149">Artık bir test geçişi yapmış olduğunuza göre daha fazla yazma zamanı vardır.</span><span class="sxs-lookup"><span data-stu-id="3ced9-149">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="3ced9-150">Asal sayıların diğer birkaç basit durumu vardır: 0,-1.</span><span class="sxs-lookup"><span data-stu-id="3ced9-150">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="3ced9-151">Bu servis taleplerini `[Fact]` özniteliğiyle yeni testler olarak ekleyebilirsiniz, ancak bu, hızlı bir şekilde sıkıcı hale gelir.</span><span class="sxs-lookup"><span data-stu-id="3ced9-151">You could add those cases as new tests with the `[Fact]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="3ced9-152">Benzer testlerin bir paketini yazmanızı sağlayan başka xUnit öznitelikleri vardır:</span><span class="sxs-lookup"><span data-stu-id="3ced9-152">There are other xUnit attributes that enable you to write a suite of similar tests:</span></span>

- <span data-ttu-id="3ced9-153">`[Theory]`aynı kodu çalıştıran, ancak farklı giriş bağımsız değişkenlerine sahip olan testlerin paketini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3ced9-153">`[Theory]` represents a suite of tests that execute the same code but have different input arguments.</span></span>

- <span data-ttu-id="3ced9-154">`[InlineData]`öznitelik, bu girişlerin değerlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3ced9-154">`[InlineData]` attribute specifies values for those inputs.</span></span>

<span data-ttu-id="3ced9-155">Yeni testler oluşturmak yerine, bu iki özniteliği `[Theory]` uygulayın ve `[InlineData]`PrimeService_IsPrimeShould. cs dosyasında tek bir teorisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3ced9-155">Instead of creating new tests, apply these two attributes, `[Theory]` and `[InlineData]`, to create a single theory in the *PrimeService_IsPrimeShould.cs* file.</span></span> <span data-ttu-id="3ced9-156">Teorisi, en düşük asal sayı olan iki değerden küçük birkaç değeri sınayan bir yöntemdir:</span><span class="sxs-lookup"><span data-stu-id="3ced9-156">The theory is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="3ced9-157">Yeniden `dotnet test` çalıştırın, bu testlerin ikisi de başarısız olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3ced9-157">Run `dotnet test` again, and two of these tests should fail.</span></span> <span data-ttu-id="3ced9-158">Tüm testlerin geçişini yapmak için `if` *PrimeService.cs* dosyasındaki `IsPrime` yönteminin başındaki yan tümceyi değiştirin:</span><span class="sxs-lookup"><span data-stu-id="3ced9-158">To make all of the tests pass, change the `if` clause at the beginning of the `IsPrime` method in the *PrimeService.cs* file:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="3ced9-159">Ana kitaplıkta daha fazla test, daha fazla yer ve daha fazla kod ekleyerek yinelemek için devam edin.</span><span class="sxs-lookup"><span data-stu-id="3ced9-159">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="3ced9-160">[Testlerin tamamlanmış sürümüne](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) ve [kitaplığın tüm uygulamasına](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs)sahipsiniz.</span><span class="sxs-lookup"><span data-stu-id="3ced9-160">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="3ced9-161">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="3ced9-161">Additional resources</span></span>

- [<span data-ttu-id="3ced9-162">xUnit.net resmi site</span><span class="sxs-lookup"><span data-stu-id="3ced9-162">xUnit.net official site</span></span>](https://xunit.github.io)
- [<span data-ttu-id="3ced9-163">ASP.NET Core 'de test denetleyicisi mantığı</span><span class="sxs-lookup"><span data-stu-id="3ced9-163">Testing controller logic in ASP.NET Core</span></span>](/aspnet/core/mvc/controllers/testing)
