---
title: NUnit C# ve .NET Core ile birim testi
description: DotNet test ve NUnit C# kullanarak bir örnek çözüm oluşturma adlı etkileşimli bir deneyim aracılığıyla ve .NET Core 'daki birim testi kavramlarını öğrenin.
author: rprouse
ms.date: 08/31/2018
ms.custom: seodec18
ms.openlocfilehash: 4d378e68143192e2f56fb411ae6ee709af753750
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849670"
---
# <a name="unit-testing-c-with-nunit-and-net-core"></a><span data-ttu-id="5eba8-103">NUnit C# ve .NET Core ile birim testi</span><span class="sxs-lookup"><span data-stu-id="5eba8-103">Unit testing C# with NUnit and .NET Core</span></span>

<span data-ttu-id="5eba8-104">Bu öğreticide, birim testi kavramlarını öğrenmek için bir örnek çözüm oluşturma adım adım yönergeler sunarak etkileşimli bir deneyim sağlanır.</span><span class="sxs-lookup"><span data-stu-id="5eba8-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="5eba8-105">Önceden oluşturulmuş bir çözüm kullanarak öğreticiyi izlemeyi tercih ediyorsanız, başlamadan önce [örnek kodu görüntüleyin veya indirin](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/) .</span><span class="sxs-lookup"><span data-stu-id="5eba8-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/) before you begin.</span></span> <span data-ttu-id="5eba8-106">İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="5eba8-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="prerequisites"></a><span data-ttu-id="5eba8-107">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="5eba8-107">Prerequisites</span></span>

- <span data-ttu-id="5eba8-108">[.NET Core 2,1 SDK](https://dotnet.microsoft.com/download) veya sonraki sürümleri.</span><span class="sxs-lookup"><span data-stu-id="5eba8-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later versions.</span></span>
- <span data-ttu-id="5eba8-109">Seçtiğiniz bir metin düzenleyici veya kod Düzenleyicisi.</span><span class="sxs-lookup"><span data-stu-id="5eba8-109">A text editor or code editor of your choice.</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="5eba8-110">Kaynak proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="5eba8-110">Creating the source project</span></span>

<span data-ttu-id="5eba8-111">Bir kabuk penceresi açın.</span><span class="sxs-lookup"><span data-stu-id="5eba8-111">Open a shell window.</span></span> <span data-ttu-id="5eba8-112">Çözümü tutmak için *birim-test-using-NUnit* adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5eba8-112">Create a directory called *unit-testing-using-nunit* to hold the solution.</span></span> <span data-ttu-id="5eba8-113">Bu yeni dizin içinde, sınıf kitaplığı ve test projesi için yeni bir çözüm dosyası oluşturmak üzere aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="5eba8-113">Inside this new directory, run the following command to create a new solution file for the class library and the test project:</span></span>

```console
dotnet new sln
```
 
<span data-ttu-id="5eba8-114">Ardından, bir *Primeservice* dizini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5eba8-114">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="5eba8-115">Aşağıdaki ana hat şu ana kadar dizin ve dosya yapısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="5eba8-115">The following outline shows the directory and file structure so far:</span></span>

```console
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
```

<span data-ttu-id="5eba8-116">Kaynak projeyi oluşturmak için *Primeservice* 'i geçerli dizin yapın ve şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="5eba8-116">Make *PrimeService* the current directory and run the following command to create the source project:</span></span>

```console
dotnet new classlib
```

<span data-ttu-id="5eba8-117">*Class1.cs* *olarak yeniden*adlandırın.</span><span class="sxs-lookup"><span data-stu-id="5eba8-117">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="5eba8-118">`PrimeService` Sınıfın başarısız bir uygulamasını oluşturursunuz:</span><span class="sxs-lookup"><span data-stu-id="5eba8-118">You create a failing implementation of the `PrimeService` class:</span></span>

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

<span data-ttu-id="5eba8-119">Dizini *birim-test-NUnit* dizinine geri doğru değiştirin.</span><span class="sxs-lookup"><span data-stu-id="5eba8-119">Change the directory back to the *unit-testing-using-nunit* directory.</span></span> <span data-ttu-id="5eba8-120">Çözüme Sınıf Kitaplığı projesini eklemek için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="5eba8-120">Run the following command to add the class library project to the solution:</span></span>

```console
dotnet sln add PrimeService/PrimeService.csproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="5eba8-121">Test projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="5eba8-121">Creating the test project</span></span>

<span data-ttu-id="5eba8-122">Ardından, *Primeservice. Tests* dizinini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5eba8-122">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="5eba8-123">Aşağıdaki ana hat dizin yapısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="5eba8-123">The following outline shows the directory structure:</span></span>

```console
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="5eba8-124">*Primeservice. test* dizinini geçerli dizini yapın ve aşağıdaki komutu kullanarak yeni bir proje oluşturun:</span><span class="sxs-lookup"><span data-stu-id="5eba8-124">Make the *PrimeService.Tests* directory the current directory and create a new project using the following command:</span></span>

```console
dotnet new nunit
```

<span data-ttu-id="5eba8-125">[DotNet New](../tools/dotnet-new.md) komutu, test kitaplığı olarak NUnit kullanan bir test projesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5eba8-125">The [dotnet new](../tools/dotnet-new.md) command creates a test project that uses NUnit as the test library.</span></span> <span data-ttu-id="5eba8-126">Oluşturulan şablon, *Primeservice. Tests. csproj* dosyasındaki Test Çalıştırıcısı 'nı yapılandırır:</span><span class="sxs-lookup"><span data-stu-id="5eba8-126">The generated template configures the test runner in the *PrimeService.Tests.csproj* file:</span></span>

[!code-xml[Packages](~/samples/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj#Packages)]

<span data-ttu-id="5eba8-127">Test projesi, birim testlerini oluşturmak ve çalıştırmak için diğer paketlerin kullanılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5eba8-127">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="5eba8-128">`dotnet new`önceki adımda Microsoft Test SDK 'sını, NUnit test çerçevesini ve NUnit test bağdaştırıcısını ekledik.</span><span class="sxs-lookup"><span data-stu-id="5eba8-128">`dotnet new` in the previous step added the Microsoft test SDK, the NUnit test framework, and the NUnit test adapter.</span></span> <span data-ttu-id="5eba8-129">Şimdi, `PrimeService` sınıf kitaplığını projeye başka bir bağımlılık olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5eba8-129">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="5eba8-130">[`dotnet add reference`](../tools/dotnet-add-reference.md) Şu komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="5eba8-130">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```console
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="5eba8-131">GitHub 'daki [örnekler deposunda](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj) dosyanın tamamını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5eba8-131">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="5eba8-132">Aşağıdaki ana hat, son çözüm yerleşimini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="5eba8-132">The following outline shows the final solution layout:</span></span>

```console
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeService.Tests.csproj
```

<span data-ttu-id="5eba8-133">*Birim-test-NUnit* dizininde aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="5eba8-133">Execute the following command in the *unit-testing-using-nunit* directory:</span></span>

```console
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="5eba8-134">İlk test oluşturma</span><span class="sxs-lookup"><span data-stu-id="5eba8-134">Creating the first test</span></span>

<span data-ttu-id="5eba8-135">Başarısız bir test yazdığınızda, geçişi yapıp işlemi tekrarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5eba8-135">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="5eba8-136">*Primeservice. Tests* dizininde, *UnitTest1.cs* dosyasını *PrimeService_IsPrimeShould. cs* olarak yeniden adlandırın ve tüm içeriğini aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="5eba8-136">In the *PrimeService.Tests* directory, rename the *UnitTest1.cs* file to *PrimeService_IsPrimeShould.cs* and replace its entire contents with the following code:</span></span>

```csharp
using NUnit.Framework;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    [TestFixture]
    public class PrimeService_IsPrimeShould
    {
        [Test]
        public void IsPrime_InputIs1_ReturnFalse()
        {
            PrimeService primeService = CreatePrimeService();
            var result = primeService.IsPrime(1);

            Assert.IsFalse(result, "1 should not be prime");
        }
        
        /*
        More tests
        */
        
        private PrimeService CreatePrimeService()
        {
             return new PrimeService();
        }
    }
}
```

<span data-ttu-id="5eba8-137">Öznitelik `[TestFixture]` , birim testlerini içeren bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="5eba8-137">The `[TestFixture]` attribute denotes a class that contains unit tests.</span></span> <span data-ttu-id="5eba8-138">`[Test]` Özniteliği bir yöntemin test yöntemi olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="5eba8-138">The `[Test]` attribute indicates a method is a test method.</span></span>

<span data-ttu-id="5eba8-139">Testleri ve sınıf kitaplığını derlemek [`dotnet test`](../tools/dotnet-test.md) ve ardından testleri çalıştırmak için bu dosyayı kaydedin ve yürütün.</span><span class="sxs-lookup"><span data-stu-id="5eba8-139">Save this file and execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="5eba8-140">NUnit Test Çalıştırıcısı, testlerinizi çalıştırmak için program giriş noktasını içerir.</span><span class="sxs-lookup"><span data-stu-id="5eba8-140">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="5eba8-141">`dotnet test`oluşturduğunuz birim test projesini kullanarak Test Çalıştırıcısı başlatır.</span><span class="sxs-lookup"><span data-stu-id="5eba8-141">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="5eba8-142">Testiniz başarısız oluyor.</span><span class="sxs-lookup"><span data-stu-id="5eba8-142">Your test fails.</span></span> <span data-ttu-id="5eba8-143">Uygulamayı henüz oluşturmadınız.</span><span class="sxs-lookup"><span data-stu-id="5eba8-143">You haven't created the implementation yet.</span></span> <span data-ttu-id="5eba8-144">Bu test geçişini, çalıştıran `PrimeService` sınıfa en basit kodu yazarak yapın:</span><span class="sxs-lookup"><span data-stu-id="5eba8-144">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

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

<span data-ttu-id="5eba8-145">*Birim-test-using-NUnit* dizininde yeniden çalıştırın `dotnet test` .</span><span class="sxs-lookup"><span data-stu-id="5eba8-145">In the *unit-testing-using-nunit* directory, run `dotnet test` again.</span></span> <span data-ttu-id="5eba8-146">Komutu, `PrimeService` proje için bir yapı ve ardından projeiçinçalışır.`PrimeService.Tests` `dotnet test`</span><span class="sxs-lookup"><span data-stu-id="5eba8-146">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="5eba8-147">Her iki proje de oluşturulduktan sonra bu tek testi çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="5eba8-147">After building both projects, it runs this single test.</span></span> <span data-ttu-id="5eba8-148">Geçirir.</span><span class="sxs-lookup"><span data-stu-id="5eba8-148">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="5eba8-149">Daha fazla özellik ekleme</span><span class="sxs-lookup"><span data-stu-id="5eba8-149">Adding more features</span></span>

<span data-ttu-id="5eba8-150">Artık bir test geçişi yapmış olduğunuza göre daha fazla yazma zamanı vardır.</span><span class="sxs-lookup"><span data-stu-id="5eba8-150">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="5eba8-151">Asal sayıların diğer birkaç basit durumu vardır: 0,-1.</span><span class="sxs-lookup"><span data-stu-id="5eba8-151">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="5eba8-152">`[Test]` Özniteliğiyle yeni testler ekleyebilirsiniz, ancak bu hızlı bir şekilde sıkıcı olur.</span><span class="sxs-lookup"><span data-stu-id="5eba8-152">You could add new tests with the `[Test]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="5eba8-153">Benzer testlerin bir paketini yazmanızı sağlayan başka NUnit öznitelikleri vardır.</span><span class="sxs-lookup"><span data-stu-id="5eba8-153">There are other NUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="5eba8-154">`[TestCase]` Özniteliği, aynı kodu çalıştıran ancak farklı giriş bağımsız değişkenlerine sahip olan testlerin bir paketini oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5eba8-154">A `[TestCase]` attribute is used to create a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="5eba8-155">Bu girişlerin değerlerini belirtmek `[TestCase]` için özniteliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5eba8-155">You can use the `[TestCase]` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="5eba8-156">Yeni test oluşturmak yerine, tek bir veri temelli test oluşturmak için bu özniteliği uygulayın.</span><span class="sxs-lookup"><span data-stu-id="5eba8-156">Instead of creating new tests, apply this attribute to create a single data driven test.</span></span> <span data-ttu-id="5eba8-157">Veri temelli test, en düşük asal sayı olan iki değerden küçük birkaç değeri sınayan bir yöntemdir:</span><span class="sxs-lookup"><span data-stu-id="5eba8-157">The data driven test is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="5eba8-158">Çalıştır `dotnet test`ve bu testlerin ikisi de başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="5eba8-158">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="5eba8-159">Tüm testlerin geçişini yapmak için `if` *PrimeService.cs* dosyasındaki `Main` yönteminin başındaki yan tümceyi değiştirin:</span><span class="sxs-lookup"><span data-stu-id="5eba8-159">To make all of the tests pass, change the `if` clause at the beginning of the `Main` method in the *PrimeService.cs* file:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="5eba8-160">Ana kitaplıkta daha fazla test, daha fazla yer ve daha fazla kod ekleyerek yinelemek için devam edin.</span><span class="sxs-lookup"><span data-stu-id="5eba8-160">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="5eba8-161">[Testlerin tamamlanmış sürümüne](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs) ve [kitaplığın tüm uygulamasına](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs)sahipsiniz.</span><span class="sxs-lookup"><span data-stu-id="5eba8-161">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="5eba8-162">Bu kitaplık için küçük bir kitaplık ve birim testleri kümesi oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="5eba8-162">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="5eba8-163">Çözümü, yeni paket ve test eklemek normal iş akışının bir parçası olacak şekilde öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="5eba8-163">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="5eba8-164">Uygulamanın hedeflerini çözme konusunda zaman ve çaba harcamanızı en iyi şekilde gördünüz.</span><span class="sxs-lookup"><span data-stu-id="5eba8-164">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
