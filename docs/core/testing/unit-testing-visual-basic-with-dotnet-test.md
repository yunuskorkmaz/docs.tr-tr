---
title: Unit test Visual Basic in .NET Core ile dotnet testi ve xUnit
description: Noktanet testi ve xUnit kullanarak örnek bir Visual Basic çözümü adım adım oluşturma etkileşimli bir deneyim le .NET Core'daki birim test kavramlarını öğrenin.
author: billwagner
ms.author: wiwagn
ms.date: 09/01/2017
ms.openlocfilehash: 9a99d9031711a3e958132416d0235df76f4a9092
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240954"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-xunit"></a><span data-ttu-id="b2568-103">Unit test Visual Basic .NET Core kitaplıkları dotnet testi ve xUnit kullanarak</span><span class="sxs-lookup"><span data-stu-id="b2568-103">Unit testing Visual Basic .NET Core libraries using dotnet test and xUnit</span></span>

<span data-ttu-id="b2568-104">Bu öğretici, birim test kavramlarını öğrenmek için adım adım örnek bir çözüm oluşturma etkileşimli bir deneyim sunar.</span><span class="sxs-lookup"><span data-stu-id="b2568-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="b2568-105">Önceden oluşturulmuş bir çözüm kullanarak öğreticiyi izlemeyi tercih ederseniz, başlamadan önce [örnek kodu görüntüleyin veya indirin.](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-dotnet-test)</span><span class="sxs-lookup"><span data-stu-id="b2568-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-dotnet-test) before you begin.</span></span> <span data-ttu-id="b2568-106">İndirme talimatları için [Örnekler ve Öğreticiler'e](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)bakın.</span><span class="sxs-lookup"><span data-stu-id="b2568-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="creating-the-source-project"></a><span data-ttu-id="b2568-107">Kaynak proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="b2568-107">Creating the source project</span></span>

<span data-ttu-id="b2568-108">Bir kabuk penceresi açın.</span><span class="sxs-lookup"><span data-stu-id="b2568-108">Open a shell window.</span></span> <span data-ttu-id="b2568-109">Çözümü tutmak için *birim-test-vb-using-dotnet-testi* adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b2568-109">Create a directory called *unit-testing-vb-using-dotnet-test* to hold the solution.</span></span>
<span data-ttu-id="b2568-110">Bu yeni dizinin içinde, yeni bir çözüm oluşturmak için çalıştırın. [`dotnet new sln`](../tools/dotnet-new.md)</span><span class="sxs-lookup"><span data-stu-id="b2568-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="b2568-111">Bu uygulama, hem sınıf kitaplığını hem de birim test projesini yönetmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="b2568-111">This practice makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="b2568-112">Çözüm dizininin içinde bir *PrimeService* dizini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b2568-112">Inside the solution directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="b2568-113">Şimdiye kadar aşağıdaki dizin ve dosya yapısına sahipsiniz:</span><span class="sxs-lookup"><span data-stu-id="b2568-113">You have the following directory and file structure thus far:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

<span data-ttu-id="b2568-114">*PrimeService'i* geçerli dizin [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) yapın ve kaynak projeyi oluşturmak için çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b2568-114">Make *PrimeService* the current directory and run [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="b2568-115">*Class1.VB'yi* *PrimeService.VB*olarak yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="b2568-115">Rename *Class1.VB* to *PrimeService.VB*.</span></span> <span data-ttu-id="b2568-116">`PrimeService` Sınıfın başarısız bir uygulamasını oluşturursunuz:</span><span class="sxs-lookup"><span data-stu-id="b2568-116">You create a failing implementation of the `PrimeService` class:</span></span>

```vb
Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first")
        End Function
    End Class
End Namespace
```

<span data-ttu-id="b2568-117">Dizin geri *birim-test-vb-using-dotnet-test* dizini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b2568-117">Change the directory back to the *unit-testing-vb-using-dotnet-test* directory.</span></span> <span data-ttu-id="b2568-118">Sınıf [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) kitaplığı projesini çözüme eklemek için çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b2568-118">Run [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="b2568-119">Test projesini oluşturma</span><span class="sxs-lookup"><span data-stu-id="b2568-119">Creating the test project</span></span>

<span data-ttu-id="b2568-120">Ardından, *PrimeService.Tests* dizinini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b2568-120">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="b2568-121">Aşağıdaki anahat dizin yapısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="b2568-121">The following outline shows the directory structure:</span></span>

```
/unit-testing-vb-using-dotnet-test
    unit-testing-vb-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

<span data-ttu-id="b2568-122">*PrimeService.Tests* dizinini geçerli dizini oluşturun ve yeni [`dotnet new xunit -lang VB`](../tools/dotnet-new.md)bir proje oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b2568-122">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new xunit -lang VB`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="b2568-123">Bu komut, test kitaplığı olarak xUnit kullanan bir test projesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b2568-123">This command creates a test project that uses xUnit as the test library.</span></span> <span data-ttu-id="b2568-124">Oluşturulan şablon *PrimeServiceTests.vbproj*test koşucusu yapılandırır:</span><span class="sxs-lookup"><span data-stu-id="b2568-124">The generated template configures the test runner in the *PrimeServiceTests.vbproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

<span data-ttu-id="b2568-125">Test projesi, birim testleri oluşturmak ve çalıştırmak için diğer paketler gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b2568-125">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="b2568-126">`dotnet new`önceki adımda xUnit ve xUnit runner eklendi.</span><span class="sxs-lookup"><span data-stu-id="b2568-126">`dotnet new` in the previous step added xUnit and the xUnit runner.</span></span> <span data-ttu-id="b2568-127">Şimdi, `PrimeService` sınıf kitaplığını projeye başka bir bağımlılık olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b2568-127">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="b2568-128">Komutu [`dotnet add reference`](../tools/dotnet-add-reference.md) kullanın:</span><span class="sxs-lookup"><span data-stu-id="b2568-128">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.vbproj
```

<span data-ttu-id="b2568-129">Tüm dosyayı GitHub'daki [örnek deposunda](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService.Tests.vbproj) görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2568-129">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span></span>

<span data-ttu-id="b2568-130">Aşağıdaki son klasör düzenine sahipsiniz:</span><span class="sxs-lookup"><span data-stu-id="b2568-130">You have the following final folder layout:</span></span>

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

<span data-ttu-id="b2568-131">[`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) *Birim-test-vb-using-dotnet-test* dizininde yürütün.</span><span class="sxs-lookup"><span data-stu-id="b2568-131">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) in the *unit-testing-vb-using-dotnet-test* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="b2568-132">İlk testi oluşturma</span><span class="sxs-lookup"><span data-stu-id="b2568-132">Creating the first test</span></span>

<span data-ttu-id="b2568-133">Başarısız bir test yazarsın, geçer ve işlemi tekrarlarsın.</span><span class="sxs-lookup"><span data-stu-id="b2568-133">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="b2568-134">*UnitTest1.vb'i* *PrimeService.Tests* dizininden kaldırın ve *PrimeService_IsPrimeShould.VB*adlı yeni bir Visual Basic dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b2568-134">Remove *UnitTest1.vb* from the *PrimeService.Tests* directory and create a new Visual Basic file named *PrimeService_IsPrimeShould.VB*.</span></span> <span data-ttu-id="b2568-135">Aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b2568-135">Add the following code:</span></span>

```vb
Imports Xunit

Namespace PrimeService.Tests
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <Fact>
        Sub IsPrime_InputIs1_ReturnFalse()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

<span data-ttu-id="b2568-136">Öznitelik, `<Fact>` test koşucusu tarafından çalıştırılabilen bir test yöntemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b2568-136">The `<Fact>` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="b2568-137">*Birim-test-using-dotnet-testinden,* testleri [`dotnet test`](../tools/dotnet-test.md) ve sınıf kitaplığını oluşturmak ve testleri çalıştırmak için çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b2568-137">From the *unit-testing-using-dotnet-test*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="b2568-138">xUnit test koşucusu, testlerinizi çalıştırmak için program giriş noktasını içerir.</span><span class="sxs-lookup"><span data-stu-id="b2568-138">The xUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="b2568-139">`dotnet test`oluşturduğunuz birim test projesini kullanarak test koşucusu başlatın.</span><span class="sxs-lookup"><span data-stu-id="b2568-139">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="b2568-140">Sınavın başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="b2568-140">Your test fails.</span></span> <span data-ttu-id="b2568-141">Uygulamayı henüz oluşturmadın.</span><span class="sxs-lookup"><span data-stu-id="b2568-141">You haven't created the implementation yet.</span></span> <span data-ttu-id="b2568-142">Bu testin çalışmasını sağlayan `PrimeService` sınıftaki en basit kodu yazarak geçmesini sağla:</span><span class="sxs-lookup"><span data-stu-id="b2568-142">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first.")
End Function
```

<span data-ttu-id="b2568-143">*Birim-test-vb-using-dotnet-test* dizininde, yeniden `dotnet test` çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b2568-143">In the *unit-testing-vb-using-dotnet-test* directory, run `dotnet test` again.</span></span> <span data-ttu-id="b2568-144">Komut, `dotnet test` proje ve ardından `PrimeService.Tests` proje için bir yapı çalışır. `PrimeService`</span><span class="sxs-lookup"><span data-stu-id="b2568-144">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="b2568-145">Her iki projeyi de yaptıktan sonra, bu tek testi çalıştırAr.</span><span class="sxs-lookup"><span data-stu-id="b2568-145">After building both projects, it runs this single test.</span></span> <span data-ttu-id="b2568-146">Geçiyor.</span><span class="sxs-lookup"><span data-stu-id="b2568-146">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="b2568-147">Daha fazla özellik ekleme</span><span class="sxs-lookup"><span data-stu-id="b2568-147">Adding more features</span></span>

<span data-ttu-id="b2568-148">Artık bir test sınavını geçtiğine göre, daha fazla yazma nın zamanı.</span><span class="sxs-lookup"><span data-stu-id="b2568-148">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="b2568-149">Asal sayılar için birkaç basit durum daha vardır: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="b2568-149">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="b2568-150">Bu durumları öznitelik ile `<Fact>` yeni testler olarak ekleyebilirsiniz, ancak bu hızla sıkıcı olur.</span><span class="sxs-lookup"><span data-stu-id="b2568-150">You could add those cases as new tests with the `<Fact>` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="b2568-151">Benzer testler paketi yazmanızı sağlayan başka xUnit öznitelikleri de vardır.</span><span class="sxs-lookup"><span data-stu-id="b2568-151">There are other xUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="b2568-152">Öznitelik, `<Theory>` aynı kodu çalıştıran ancak farklı giriş bağımsız değişkenleri olan bir test paketini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b2568-152">A `<Theory>` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="b2568-153">Bu girişler `<InlineData>` için değerleri belirtmek için özniteliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2568-153">You can use the `<InlineData>` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="b2568-154">Yeni testler oluşturmak yerine, tek bir teori oluşturmak için bu iki özniteliği uygulayın.</span><span class="sxs-lookup"><span data-stu-id="b2568-154">Instead of creating new tests, apply these two attributes to create a single theory.</span></span> <span data-ttu-id="b2568-155">Teori, ikiden küçük birkaç değeri test eden bir yöntemdir ve bu yöntem en düşük asal sayıdır:</span><span class="sxs-lookup"><span data-stu-id="b2568-155">The theory is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-vb[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-vb-dotnet-test/vb/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

<span data-ttu-id="b2568-156">Çalıştır `dotnet test`Ve bu testlerin iki başarısız.</span><span class="sxs-lookup"><span data-stu-id="b2568-156">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="b2568-157">Tüm testlerin geçmesi için yöntemin başındaki `if` tümceyi değiştirin:</span><span class="sxs-lookup"><span data-stu-id="b2568-157">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```vb
if candidate < 2
```

<span data-ttu-id="b2568-158">Ana kitaplığa daha fazla test, daha fazla teori ve daha fazla kod ekleyerek yinelemeye devam edin.</span><span class="sxs-lookup"><span data-stu-id="b2568-158">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="b2568-159">[Testlerin tamamlanmış sürümüne](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) ve [kitaplığın tam uygulamasına](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService/PrimeService.vb)sahipsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2568-159">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="b2568-160">O kitaplık için küçük bir kitaplık ve bir dizi birim testi inşa ettin.</span><span class="sxs-lookup"><span data-stu-id="b2568-160">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="b2568-161">Yeni paketler ve testler eklemek normal iş akışının bir parçası olacak şekilde çözümü yapılandırdınız.</span><span class="sxs-lookup"><span data-stu-id="b2568-161">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="b2568-162">Zamanınızın ve çabanızın çoğunu uygulamanın hedeflerini çözmeye yoğunlaşmışsınız.</span><span class="sxs-lookup"><span data-stu-id="b2568-162">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
