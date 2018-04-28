---
title: Birim .NET Core dotnet test ve xUnit kullanarak bir Visual Basic ile testi
description: Adım adım örnek Visual Basic çözüm oluşturma etkileşimli bir deneyim aracılığıyla .NET Core olarak birim testi kavramları hakkında bilgi dotnet test ve xUnit kullanarak.
author: billwagner
ms.author: wiwagn
ms.date: 09/01/2017
ms.topic: conceptual
dev_langs:
- vb
ms.prod: dotnet-core
ms.workload:
- dotnetcore
ms.openlocfilehash: 3402ac1f159dd6764dfd72da9d5ae09e946a4c88
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-xunit"></a><span data-ttu-id="68a58-103">Birim testi dotnet test ve xUnit kullanarak Visual Basic .NET Core kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="68a58-103">Unit testing Visual Basic .NET Core libraries using dotnet test and xUnit</span></span>

<span data-ttu-id="68a58-104">Bu öğretici birim testi kavramlarını öğrenmek için adım adım örnek çözüm oluşturma etkileşimli bir deneyim gösterir.</span><span class="sxs-lookup"><span data-stu-id="68a58-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="68a58-105">Önceden oluşturulmuş bir çözümü kullanarak öğreticiyi izleyin tercih ediyorsanız [görüntülemek veya karşıdan örnek kod](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-dotnet-test) başlamadan önce.</span><span class="sxs-lookup"><span data-stu-id="68a58-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-dotnet-test) before you begin.</span></span> <span data-ttu-id="68a58-106">Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="68a58-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="68a58-107">Kaynak projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="68a58-107">Creating the source project</span></span>

<span data-ttu-id="68a58-108">Kabuk penceresini açın.</span><span class="sxs-lookup"><span data-stu-id="68a58-108">Open a shell window.</span></span> <span data-ttu-id="68a58-109">Adlı bir dizin oluşturun *unit-testing-vb-using-dotnet-test* çözümü tutmak için.</span><span class="sxs-lookup"><span data-stu-id="68a58-109">Create a directory called *unit-testing-vb-using-dotnet-test* to hold the solution.</span></span>
<span data-ttu-id="68a58-110">Bu yeni dizin içinde çalıştırmak [ `dotnet new sln` ](../tools/dotnet-new.md) yeni bir çözüm oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="68a58-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="68a58-111">Bu yöntem, sınıf kitaplığı ve birim testi projesi yönetmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="68a58-111">This practice makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="68a58-112">Çözüm dizini içinde oluşturmak bir *PrimeService* dizini.</span><span class="sxs-lookup"><span data-stu-id="68a58-112">Inside the solution directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="68a58-113">Aşağıdaki dizin ve dosya yapısı bugüne kadarki vardır:</span><span class="sxs-lookup"><span data-stu-id="68a58-113">You have the following directory and file structure thus far:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

<span data-ttu-id="68a58-114">Olun *PrimeService* geçerli dizin ve çalışma [ `dotnet new classlib -lang VB` ](../tools/dotnet-new.md) kaynak projesi oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="68a58-114">Make *PrimeService* the current directory and run [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="68a58-115">Yeniden Adlandır *Class1.vb'ye* için *PrimeService.VB*.</span><span class="sxs-lookup"><span data-stu-id="68a58-115">Rename *Class1.VB* to *PrimeService.VB*.</span></span> <span data-ttu-id="68a58-116">Teste dayalı geliştirme (TDD) kullanmak için bir başarısız uygulaması oluşturun `PrimeService` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="68a58-116">To use test-driven development (TDD), you create a failing implementation of the `PrimeService` class:</span></span>

```vb
Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first")
        End Function
    End Class
End Namespace
```

<span data-ttu-id="68a58-117">Dizin geri değişiklik *unit-testing-vb-using-dotnet-test* dizini.</span><span class="sxs-lookup"><span data-stu-id="68a58-117">Change the directory back to the *unit-testing-vb-using-dotnet-test* directory.</span></span> <span data-ttu-id="68a58-118">Çalıştırma [ `dotnet sln add .\PrimeService\PrimeService.vbproj` ](../tools/dotnet-sln.md) sınıf kitaplığı proje çözüme eklemek için.</span><span class="sxs-lookup"><span data-stu-id="68a58-118">Run [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="68a58-119">Test projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="68a58-119">Creating the test project</span></span>

<span data-ttu-id="68a58-120">Ardından, oluşturun *PrimeService.Tests* dizini.</span><span class="sxs-lookup"><span data-stu-id="68a58-120">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="68a58-121">Aşağıdaki anahat dizin yapısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="68a58-121">The following outline shows the directory structure:</span></span>

```
/unit-testing-vb-using-dotnet-test
    unit-testing-vb-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

<span data-ttu-id="68a58-122">Olun *PrimeService.Tests* dizine geçerli ve kullanarak yeni bir proje oluşturun [ `dotnet new xunit -lang VB` ](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="68a58-122">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new xunit -lang VB`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="68a58-123">Bu komut xUnit test kitaplığını kullanan bir test projesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="68a58-123">This command creates a test project that uses xUnit as the test library.</span></span> <span data-ttu-id="68a58-124">Test Çalıştırıcısı'nda oluşturulan şablon yapılandırır *PrimeServiceTests.vbproj*:</span><span class="sxs-lookup"><span data-stu-id="68a58-124">The generated template configures the test runner in the *PrimeServiceTests.vbproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

<span data-ttu-id="68a58-125">Test projesi oluşturmak ve birim testleri çalıştırmak için diğer paketleri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="68a58-125">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="68a58-126">`dotnet new` Önceki adımda xUnit ve xUnit Çalıştırıcısı eklendi.</span><span class="sxs-lookup"><span data-stu-id="68a58-126">`dotnet new` in the previous step added xUnit and the xUnit runner.</span></span> <span data-ttu-id="68a58-127">Şimdi, ekleyin `PrimeService` sınıf kitaplığı proje için başka bir bağımlılık olarak.</span><span class="sxs-lookup"><span data-stu-id="68a58-127">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="68a58-128">Kullanım [ `dotnet add reference` ](../tools/dotnet-add-reference.md) komutu:</span><span class="sxs-lookup"><span data-stu-id="68a58-128">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.vbproj
```

<span data-ttu-id="68a58-129">Tüm dosyasında görebilirsiniz [örnekleri deposu](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService.Tests.vbproj) github'da.</span><span class="sxs-lookup"><span data-stu-id="68a58-129">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span></span>

<span data-ttu-id="68a58-130">Aşağıdaki son klasör düzeni vardır:</span><span class="sxs-lookup"><span data-stu-id="68a58-130">You have the following final folder layout:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.vbproj
```

<span data-ttu-id="68a58-131">Yürütme [ `dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj` ](../tools/dotnet-sln.md) içinde *unit-testing-vb-using-dotnet-test* dizini.</span><span class="sxs-lookup"><span data-stu-id="68a58-131">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) in the *unit-testing-vb-using-dotnet-test* directory.</span></span> 

## <a name="creating-the-first-test"></a><span data-ttu-id="68a58-132">İlk testi oluşturma</span><span class="sxs-lookup"><span data-stu-id="68a58-132">Creating the first test</span></span>

<span data-ttu-id="68a58-133">TDD yaklaşım geçirmek kolaylaştırarak ve süreci tekrarlayarak yazma bir başarısız test için çağırır.</span><span class="sxs-lookup"><span data-stu-id="68a58-133">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="68a58-134">Kaldırma *UnitTest1.vb* gelen *PrimeService.Tests* dizin ve adlı yeni bir Visual Basic dosyası oluşturma *PrimeService_IsPrimeShould.VB*.</span><span class="sxs-lookup"><span data-stu-id="68a58-134">Remove *UnitTest1.vb* from the *PrimeService.Tests* directory and create a new Visual Basic file named *PrimeService_IsPrimeShould.VB*.</span></span> <span data-ttu-id="68a58-135">Aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="68a58-135">Add the following code:</span></span>

```vb
Imports Xunit

Namespace PrimeService.Tests
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <Fact>
        Sub ReturnFalseGivenValueOf1()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

<span data-ttu-id="68a58-136">`<Fact>` Özniteliği test Çalıştırıcısı tarafından çalıştırılan test yöntemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="68a58-136">The `<Fact>` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="68a58-137">Gelen *birim testi-kullanma-dotnet-sınama*, yürütme [ `dotnet test` ](../tools/dotnet-test.md) testleri ve sınıf kitaplığı oluşturmak ve ardından testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="68a58-137">From the *unit-testing-using-dotnet-test*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="68a58-138">XUnit test Çalıştırıcısı testleri çalıştırmak için program giriş noktası içerir.</span><span class="sxs-lookup"><span data-stu-id="68a58-138">The xUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="68a58-139">`dotnet test` oluşturduğunuz birim testi projesi kullanarak test Çalıştırıcısı başlatır.</span><span class="sxs-lookup"><span data-stu-id="68a58-139">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="68a58-140">Testiniz başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="68a58-140">Your test fails.</span></span> <span data-ttu-id="68a58-141">Uygulama henüz oluşturmadınız.</span><span class="sxs-lookup"><span data-stu-id="68a58-141">You haven't created the implementation yet.</span></span> <span data-ttu-id="68a58-142">Bu test basit kod yazarken yapmasına `PrimeService` çalışır sınıfı:</span><span class="sxs-lookup"><span data-stu-id="68a58-142">Make this test by writing the simplest code in the `PrimeService` class that works:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first")
End Function
```

<span data-ttu-id="68a58-143">İçinde *unit-testing-vb-using-dotnet-test* çalışması dizini `dotnet test` yeniden.</span><span class="sxs-lookup"><span data-stu-id="68a58-143">In the *unit-testing-vb-using-dotnet-test* directory, run `dotnet test` again.</span></span> <span data-ttu-id="68a58-144">`dotnet test` Komutu çalıştıran bir yapı `PrimeService` proje ve ardından `PrimeService.Tests` projesi.</span><span class="sxs-lookup"><span data-stu-id="68a58-144">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="68a58-145">Her iki proje oluşturduktan sonra bu tek bir test çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="68a58-145">After building both projects, it runs this single test.</span></span> <span data-ttu-id="68a58-146">Bunu geçirir.</span><span class="sxs-lookup"><span data-stu-id="68a58-146">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="68a58-147">Daha fazla özellik ekleme</span><span class="sxs-lookup"><span data-stu-id="68a58-147">Adding more features</span></span>

<span data-ttu-id="68a58-148">Bir test geçirmek yapmış olduğunuz, daha fazla yazma zamanı geldi.</span><span class="sxs-lookup"><span data-stu-id="68a58-148">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="68a58-149">Diğer basit bazı durumlar asal sayılar için vardır: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="68a58-149">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="68a58-150">Bu gibi durumlarda yeni testleriyle olarak ekleyebilirsiniz `<Fact>` özniteliği, ancak, hızlı hale can sıkıcı.</span><span class="sxs-lookup"><span data-stu-id="68a58-150">You could add those cases as new tests with the `<Fact>` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="68a58-151">Benzer testleri dizisi yazmak için etkinleştirmek diğer xUnit özniteliği vardır.</span><span class="sxs-lookup"><span data-stu-id="68a58-151">There are other xUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="68a58-152">A `<Theory>` özniteliği, aynı kod yürütmek ancak farklı giriş bağımsız değişkeni olan testleri bir paketi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="68a58-152">A `<Theory>` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="68a58-153">Kullanabileceğiniz `<InlineData>` özniteliği bu girişleri için değerleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="68a58-153">You can use the `<InlineData>` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="68a58-154">Yeni testler oluşturmak yerine, tek bir kuramsal oluşturmak için bu iki öznitelikler uygulanır.</span><span class="sxs-lookup"><span data-stu-id="68a58-154">Instead of creating new tests, apply these two attributes to create a single theory.</span></span> <span data-ttu-id="68a58-155">Teorik asal numarası en düşük olduğu birden fazla değer ikiden az, testleri bir yöntemi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="68a58-155">The theory is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

<span data-ttu-id="68a58-156">Çalıştırma `dotnet test`, ve bunların ikisini sınamaları başarısız.</span><span class="sxs-lookup"><span data-stu-id="68a58-156">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="68a58-157">Tüm testleri geçişini yapmak için değiştirme `if` yöntemi başındaki yan tümcesi:</span><span class="sxs-lookup"><span data-stu-id="68a58-157">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```vb
if candidate < 2
```

<span data-ttu-id="68a58-158">Daha fazla testleri, daha fazla kuramlarý ve daha fazla kod ana kitaplıkta ekleyerek yinelemek devam edin.</span><span class="sxs-lookup"><span data-stu-id="68a58-158">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="68a58-159">Sahip olduğunuz [testleri tamamlanmış sürümü](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) ve [kitaplığının tam uygulama](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService/PrimeService.vb).</span><span class="sxs-lookup"><span data-stu-id="68a58-159">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="68a58-160">Küçük bir kitaplığı ve bu kitaplık için birim testleri kümesini temel aldık.</span><span class="sxs-lookup"><span data-stu-id="68a58-160">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="68a58-161">Böylece yeni paketleri ekleme çözümü yapılandırılmış ve testleri normal iş akışı bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="68a58-161">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="68a58-162">Çoğu zaman ve çaba uygulama amaçlarını çözme üzerinde yoğunlaşmıştır.</span><span class="sxs-lookup"><span data-stu-id="68a58-162">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
