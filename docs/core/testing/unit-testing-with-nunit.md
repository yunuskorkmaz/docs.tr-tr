---
title: Birim testi NUnit ve .NET Core ile C#
description: Adım adım örnek bir çözüm oluşturmak bir etkileşimli deneyim C# ve .NET Core birim testi kavramları hakkında bilgi dotnet testi ve NUnit kullanarak.
author: rprouse
ms.date: 08/31/2018
ms.openlocfilehash: 253e07c16740a39566cf37ee5742a32342c78c49
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44699692"
---
# <a name="unit-testing-c-with-nunit-and-net-core"></a><span data-ttu-id="02f48-103">Birim testi NUnit ve .NET Core ile C#</span><span class="sxs-lookup"><span data-stu-id="02f48-103">Unit testing C# with NUnit and .NET Core</span></span>

<span data-ttu-id="02f48-104">Bu öğretici örnek bir çözüm birim testi kavramlarını öğrenmek için adım adım oluşturmaya etkileşimli deneyim gösterir.</span><span class="sxs-lookup"><span data-stu-id="02f48-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="02f48-105">Önceden oluşturulmuş bir çözümü kullanarak öğreticiyi uygulamak isterseniz [görüntülemek veya örnek kodu indirdikten](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/) başlamadan önce.</span><span class="sxs-lookup"><span data-stu-id="02f48-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/) before you begin.</span></span> <span data-ttu-id="02f48-106">Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="02f48-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="02f48-107">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="02f48-107">Prerequisites</span></span>

- <span data-ttu-id="02f48-108">[.NET core SDK 2.1 (v. 2.1.400)](https://www.microsoft.com/net/download) veya sonraki sürümler.</span><span class="sxs-lookup"><span data-stu-id="02f48-108">[.NET Core SDK 2.1 (v. 2.1.400)](https://www.microsoft.com/net/download) or later versions.</span></span>
- <span data-ttu-id="02f48-109">Bir metin düzenleyicisi veya tercih ettiğiniz Kod Düzenleyicisi.</span><span class="sxs-lookup"><span data-stu-id="02f48-109">A text editor or code editor of your choice.</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="02f48-110">Kaynak proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="02f48-110">Creating the source project</span></span>

<span data-ttu-id="02f48-111">Shell penceresini açın.</span><span class="sxs-lookup"><span data-stu-id="02f48-111">Open a shell window.</span></span> <span data-ttu-id="02f48-112">Adlı bir dizin oluşturun *birim-test-kullanarak-nunit* çözüm tutacak.</span><span class="sxs-lookup"><span data-stu-id="02f48-112">Create a directory called *unit-testing-using-nunit* to hold the solution.</span></span> <span data-ttu-id="02f48-113">Bu yeni dizin içinde sınıf kitaplığı ve test projesi için yeni bir çözüm dosyası oluşturmak için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="02f48-113">Inside this new directory, run the following command to create a new solution file for the class library and the test project:</span></span>

```console
dotnet new sln
```
 
<span data-ttu-id="02f48-114">Ardından, oluşturun bir *PrimeService* dizin.</span><span class="sxs-lookup"><span data-stu-id="02f48-114">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="02f48-115">Aşağıdaki ana hat dizin ve dosya yapısı şu ana kadar gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="02f48-115">The following outline shows the directory and file structure so far:</span></span>

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
```

<span data-ttu-id="02f48-116">Olun *PrimeService* aşağıdaki komut kaynak projesi oluşturmak için geçerli dizin ve çalıştırma:</span><span class="sxs-lookup"><span data-stu-id="02f48-116">Make *PrimeService* the current directory and run the following command to create the source project:</span></span>

```console
dotnet new classlib
```

<span data-ttu-id="02f48-117">Yeniden adlandırma *Class1.cs* için *PrimeService.cs*.</span><span class="sxs-lookup"><span data-stu-id="02f48-117">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="02f48-118">Teste dayalı geliştirme (TDD) kullanmak için bir başarısız uygulaması oluşturun. `PrimeService` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="02f48-118">To use test-driven development (TDD), you create a failing implementation of the `PrimeService` class:</span></span>

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

<span data-ttu-id="02f48-119">Dizine dön değişiklik *birim-test-kullanarak-nunit* dizin.</span><span class="sxs-lookup"><span data-stu-id="02f48-119">Change the directory back to the *unit-testing-using-nunit* directory.</span></span> <span data-ttu-id="02f48-120">Sınıf kitaplığı projesi çözüme eklemek için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="02f48-120">Run the following command to add the class library project to the solution:</span></span>

```console
dotnet sln add PrimeService/PrimeService.csproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="02f48-121">Test projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="02f48-121">Creating the test project</span></span>

<span data-ttu-id="02f48-122">Ardından, oluşturma *PrimeService.Tests* dizin.</span><span class="sxs-lookup"><span data-stu-id="02f48-122">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="02f48-123">Ana hat aşağıdaki dizin yapısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="02f48-123">The following outline shows the directory structure:</span></span>

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="02f48-124">Olun *PrimeService.Tests* dizini geçerli dizin ve aşağıdaki komutu kullanarak yeni bir proje oluşturun:</span><span class="sxs-lookup"><span data-stu-id="02f48-124">Make the *PrimeService.Tests* directory the current directory and create a new project using the following command:</span></span>

```console
dotnet new nunit
```

<span data-ttu-id="02f48-125">[Yeni dotnet](../tools/dotnet-new.md) komut NUnit test kitaplık olarak kullanan bir test projesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="02f48-125">The [dotnet new](../tools/dotnet-new.md) command creates a test project that uses NUnit as the test library.</span></span> <span data-ttu-id="02f48-126">Test Çalıştırıcısı'nda oluşturulan şablon yapılandırır *PrimeService.Tests.csproj* dosyası:</span><span class="sxs-lookup"><span data-stu-id="02f48-126">The generated template configures the test runner in the *PrimeService.Tests.csproj* file:</span></span>

[!code-xml[Packages](~/samples/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj#Packages)]

<span data-ttu-id="02f48-127">Test projesi oluşturma ve birim testlerini çalıştırmak için diğer paketleri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="02f48-127">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="02f48-128">`dotnet new` Önceki adımda, Microsoft test SDK'sı, NUnit test çerçevesi ve NUnit test bağdaştırıcısı eklendi.</span><span class="sxs-lookup"><span data-stu-id="02f48-128">`dotnet new` in the previous step added the Microsoft test SDK, the NUnit test framework, and the NUnit test adapter.</span></span> <span data-ttu-id="02f48-129">Şimdi ekleyin `PrimeService` sınıf kitaplığı projesine başka bir bağımlılık olarak.</span><span class="sxs-lookup"><span data-stu-id="02f48-129">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="02f48-130">Kullanım [ `dotnet add reference` ](../tools/dotnet-add-reference.md) komutu:</span><span class="sxs-lookup"><span data-stu-id="02f48-130">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```console
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="02f48-131">Dosyanın tamamını görebilirsiniz [örnekleri depomuzdan](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj) GitHub üzerinde.</span><span class="sxs-lookup"><span data-stu-id="02f48-131">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="02f48-132">Aşağıdaki ana hat nihai çözüm düzeni gösterilir:</span><span class="sxs-lookup"><span data-stu-id="02f48-132">The following outline shows the final solution layout:</span></span>

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeService.Tests.csproj
```

<span data-ttu-id="02f48-133">Aşağıdaki komutu yürütün *birim testi-kullanarak-dotnet-test* dizini:</span><span class="sxs-lookup"><span data-stu-id="02f48-133">Execute the following command in the *unit-testing-using-dotnet-test* directory:</span></span>

```console
dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="02f48-134">İlk testi oluşturma</span><span class="sxs-lookup"><span data-stu-id="02f48-134">Creating the first test</span></span>

<span data-ttu-id="02f48-135">TDD yaklaşım geçer hale getirme ve süreci tekrarlayarak yazma bir başarısız test için çağırır.</span><span class="sxs-lookup"><span data-stu-id="02f48-135">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="02f48-136">İçinde *PrimeService.Tests* dizini yeniden adlandırma *UnitTest1.cs* dosyasını *PrimeService_IsPrimeShould.cs* ve tüm içeriğini aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="02f48-136">In the *PrimeService.Tests* directory, rename the *UnitTest1.cs* file to *PrimeService_IsPrimeShould.cs* and replace its entire contents with the following code:</span></span>

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

<span data-ttu-id="02f48-137">`[TestFixture]` Özniteliği birim testleri içeren bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="02f48-137">The `[TestFixture]` attribute denotes a class that contains unit tests.</span></span> <span data-ttu-id="02f48-138">`[Test]` Öznitelik, bir yöntemi olan bir test yöntemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="02f48-138">The `[Test]` attribute indicates a method is a test method.</span></span>

<span data-ttu-id="02f48-139">Bu dosyayı kaydedin ve yürütme [ `dotnet test` ](../tools/dotnet-test.md) testler ve sınıf kitaplığı oluşturun ve ardından testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="02f48-139">Save this file and execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="02f48-140">NUnit test Çalıştırıcısı, testlerinizi çalıştırmak için programın giriş noktası içerir.</span><span class="sxs-lookup"><span data-stu-id="02f48-140">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="02f48-141">`dotnet test` oluşturduğunuz birim test projesi kullanarak test Çalıştırıcısı'nı başlatır.</span><span class="sxs-lookup"><span data-stu-id="02f48-141">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="02f48-142">Test başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="02f48-142">Your test fails.</span></span> <span data-ttu-id="02f48-143">Uygulama henüz oluşturmadınız.</span><span class="sxs-lookup"><span data-stu-id="02f48-143">You haven't created the implementation yet.</span></span> <span data-ttu-id="02f48-144">En basit kod yazarak geçirmek bu testin geçmesini `PrimeService` çalışır sınıfı:</span><span class="sxs-lookup"><span data-stu-id="02f48-144">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

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

<span data-ttu-id="02f48-145">İçinde *birim-test-kullanarak-nunit* çalışması dizini `dotnet test` yeniden.</span><span class="sxs-lookup"><span data-stu-id="02f48-145">In the *unit-testing-using-nunit* directory, run `dotnet test` again.</span></span> <span data-ttu-id="02f48-146">`dotnet test` Komut çalıştıran bir derleme için `PrimeService` proje ve ardından `PrimeService.Tests` proje.</span><span class="sxs-lookup"><span data-stu-id="02f48-146">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="02f48-147">Her iki proje oluşturduktan sonra bu tek bir test çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="02f48-147">After building both projects, it runs this single test.</span></span> <span data-ttu-id="02f48-148">Bu geçirir.</span><span class="sxs-lookup"><span data-stu-id="02f48-148">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="02f48-149">Daha fazla özellik ekleme</span><span class="sxs-lookup"><span data-stu-id="02f48-149">Adding more features</span></span>

<span data-ttu-id="02f48-150">Bir test geçirmek yaptığınız, daha fazla yazmak için zaman var.</span><span class="sxs-lookup"><span data-stu-id="02f48-150">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="02f48-151">Diğer basit bazı durumlar için asal sayıları: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="02f48-151">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="02f48-152">Yeni testleriyle ekleyebilirsiniz `[Test]` özniteliği ancak hızla olur yorucu bir süreç.</span><span class="sxs-lookup"><span data-stu-id="02f48-152">You could add new tests with the `[Test]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="02f48-153">Benzer testleri paketi yazmanızı sağlayan diğer NUnit öznitelikleri vardır.</span><span class="sxs-lookup"><span data-stu-id="02f48-153">There are other NUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="02f48-154">A `[TestCase]` özniteliği, aynı kod yürütün, ancak farklı giriş bağımsız değişkenleri olan testleri paketi oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="02f48-154">A `[TestCase]` attribute is used to create a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="02f48-155">Kullanabileceğiniz `[TestCase]` bu girişleri değerlerini belirtmek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="02f48-155">You can use the `[TestCase]` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="02f48-156">Yeni testler oluşturmak yerine, bu öznitelik, bir tek veri tabanlı test oluşturmak için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="02f48-156">Instead of creating new tests, apply this attribute to create a single data driven test.</span></span> <span data-ttu-id="02f48-157">Test odaklı veri asal numarası en düşük olan değerlerden küçüktür iki test yöntemi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="02f48-157">The data driven test is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="02f48-158">Çalıştırma `dotnet test`, ve bunlardan ikisi başarısız test eder.</span><span class="sxs-lookup"><span data-stu-id="02f48-158">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="02f48-159">Tüm testleri geçer hale getirmek için değiştirme `if` başındaki yan tümcesi `Main` yönteminde *PrimeService.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="02f48-159">To make all of the tests pass, change the `if` clause at the beginning of the `Main` method in the *PrimeService.cs* file:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="02f48-160">Ana Kitaplığı'nda daha fazla test, daha fazla Teoriler ve daha fazla kod ekleyerek yinelemek devam edin.</span><span class="sxs-lookup"><span data-stu-id="02f48-160">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="02f48-161">Sahip olduğunuz [testlerinin tamamlanmış bir sürümünü](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs) ve [Kitaplığı'nın tam bir uygulamaya](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs).</span><span class="sxs-lookup"><span data-stu-id="02f48-161">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="02f48-162">Küçük bir kitaplık ve bu kitaplık için birim testleri bir dizi oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="02f48-162">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="02f48-163">Böylece yeni paketler ekleme çözüm yapılandırılmış ve testleri normal iş akışı bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="02f48-163">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="02f48-164">Zaman ve çaba çözme hedeflerinden biri, uygulama üzerinde en yoğun.</span><span class="sxs-lookup"><span data-stu-id="02f48-164">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
