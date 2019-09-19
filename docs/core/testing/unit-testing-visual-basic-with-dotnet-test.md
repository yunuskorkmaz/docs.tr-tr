---
title: DotNet test ve xUnit ile .NET Core 'da birim testi Visual Basic
description: .NET Core 'da, DotNet test ve xUnit kullanarak örnek Visual Basic çözüm adım adım oluşturma adlı etkileşimli bir deneyim aracılığıyla birim testi kavramlarını öğrenin.
author: billwagner
ms.author: wiwagn
ms.date: 09/01/2017
ms.custom: seodec18
ms.openlocfilehash: 1738aa805947fbe0c1b7c2c770947ce650692b5f
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117053"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-xunit"></a><span data-ttu-id="9537c-103">DotNet test ve xUnit kullanarak .NET Core kitaplıkları Visual Basic birim testi</span><span class="sxs-lookup"><span data-stu-id="9537c-103">Unit testing Visual Basic .NET Core libraries using dotnet test and xUnit</span></span>

<span data-ttu-id="9537c-104">Bu öğreticide, birim testi kavramlarını öğrenmek için bir örnek çözüm oluşturma adım adım yönergeler sunarak etkileşimli bir deneyim sağlanır.</span><span class="sxs-lookup"><span data-stu-id="9537c-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="9537c-105">Önceden oluşturulmuş bir çözüm kullanarak öğreticiyi izlemeyi tercih ediyorsanız, başlamadan önce [örnek kodu görüntüleyin veya indirin](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-dotnet-test) .</span><span class="sxs-lookup"><span data-stu-id="9537c-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-dotnet-test) before you begin.</span></span> <span data-ttu-id="9537c-106">İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="9537c-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="creating-the-source-project"></a><span data-ttu-id="9537c-107">Kaynak proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="9537c-107">Creating the source project</span></span>

<span data-ttu-id="9537c-108">Bir kabuk penceresi açın.</span><span class="sxs-lookup"><span data-stu-id="9537c-108">Open a shell window.</span></span> <span data-ttu-id="9537c-109">Çözümü tutmak için *birim-test-vb-using-DotNet-test* adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9537c-109">Create a directory called *unit-testing-vb-using-dotnet-test* to hold the solution.</span></span>
<span data-ttu-id="9537c-110">Yeni bir çözüm oluşturmak için bu [`dotnet new sln`](../tools/dotnet-new.md) yeni dizinin içinde öğesini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9537c-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="9537c-111">Bu uygulama, hem sınıf kitaplığını hem de birim testi projesini yönetmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="9537c-111">This practice makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="9537c-112">Çözüm dizini içinde bir *Primeservice* dizini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9537c-112">Inside the solution directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="9537c-113">Şu ana kadar Şu dizin ve dosya yapısına sahipsiniz:</span><span class="sxs-lookup"><span data-stu-id="9537c-113">You have the following directory and file structure thus far:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

<span data-ttu-id="9537c-114">Kaynak projeyi oluşturmak için *primeservice* 'i geçerli [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) Dizin yapın ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9537c-114">Make *PrimeService* the current directory and run [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="9537c-115">*Class1. vb* ' i *primeservice. vb*olarak yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="9537c-115">Rename *Class1.VB* to *PrimeService.VB*.</span></span> <span data-ttu-id="9537c-116">`PrimeService` Sınıfın başarısız bir uygulamasını oluşturursunuz:</span><span class="sxs-lookup"><span data-stu-id="9537c-116">You create a failing implementation of the `PrimeService` class:</span></span>

```vb
Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first")
        End Function
    End Class
End Namespace
```

<span data-ttu-id="9537c-117">Dizini *birim-test-vb-using-DotNet-test* dizini olarak yeniden değiştirin.</span><span class="sxs-lookup"><span data-stu-id="9537c-117">Change the directory back to the *unit-testing-vb-using-dotnet-test* directory.</span></span> <span data-ttu-id="9537c-118">Çözüme [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) Sınıf Kitaplığı projesini eklemek için ' i çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9537c-118">Run [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="9537c-119">Test projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="9537c-119">Creating the test project</span></span>

<span data-ttu-id="9537c-120">Ardından, *Primeservice. Tests* dizinini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9537c-120">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="9537c-121">Aşağıdaki ana hat dizin yapısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="9537c-121">The following outline shows the directory structure:</span></span>

```
/unit-testing-vb-using-dotnet-test
    unit-testing-vb-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

<span data-ttu-id="9537c-122">*Primeservice. test* dizinini geçerli dizini yapın ve kullanarak [`dotnet new xunit -lang VB`](../tools/dotnet-new.md)yeni bir proje oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9537c-122">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new xunit -lang VB`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="9537c-123">Bu komut, test kitaplığı olarak xUnit kullanan bir test projesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9537c-123">This command creates a test project that uses xUnit as the test library.</span></span> <span data-ttu-id="9537c-124">Oluşturulan şablon, *Primeservicetests. vbproj*içindeki Test Çalıştırıcısı 'nı yapılandırır:</span><span class="sxs-lookup"><span data-stu-id="9537c-124">The generated template configures the test runner in the *PrimeServiceTests.vbproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

<span data-ttu-id="9537c-125">Test projesi, birim testlerini oluşturmak ve çalıştırmak için diğer paketlerin kullanılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9537c-125">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="9537c-126">`dotnet new`önceki adımda xUnit ve xUnit Çalıştırıcısı eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="9537c-126">`dotnet new` in the previous step added xUnit and the xUnit runner.</span></span> <span data-ttu-id="9537c-127">Şimdi, `PrimeService` sınıf kitaplığını projeye başka bir bağımlılık olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9537c-127">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="9537c-128">[`dotnet add reference`](../tools/dotnet-add-reference.md) Şu komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="9537c-128">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.vbproj
```

<span data-ttu-id="9537c-129">GitHub 'daki [örnekler deposunda](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService.Tests.vbproj) dosyanın tamamını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9537c-129">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span></span>

<span data-ttu-id="9537c-130">Aşağıdaki son klasör düzenine sahipsiniz:</span><span class="sxs-lookup"><span data-stu-id="9537c-130">You have the following final folder layout:</span></span>

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

<span data-ttu-id="9537c-131">[`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) *Birim-test-vb-using-DotNet-test* dizininde yürütün.</span><span class="sxs-lookup"><span data-stu-id="9537c-131">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) in the *unit-testing-vb-using-dotnet-test* directory.</span></span> 

## <a name="creating-the-first-test"></a><span data-ttu-id="9537c-132">İlk test oluşturma</span><span class="sxs-lookup"><span data-stu-id="9537c-132">Creating the first test</span></span>

<span data-ttu-id="9537c-133">Başarısız bir test yazdığınızda, geçişi yapıp işlemi tekrarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9537c-133">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="9537c-134">*UnitTest1. vb* 'Yi *primeservice. Tests* dizininden KALDıRıN ve *PrimeService_IsPrimeShould. vb*adlı yeni bir Visual Basic dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9537c-134">Remove *UnitTest1.vb* from the *PrimeService.Tests* directory and create a new Visual Basic file named *PrimeService_IsPrimeShould.VB*.</span></span> <span data-ttu-id="9537c-135">Aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="9537c-135">Add the following code:</span></span>

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

<span data-ttu-id="9537c-136">`<Fact>` Öznitelik, Test Çalıştırıcısı tarafından çalıştırılan bir test yöntemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9537c-136">The `<Fact>` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="9537c-137">*Birim-test--DotNet-test*' i [`dotnet test`](../tools/dotnet-test.md) kullanarak testleri ve sınıf kitaplığını oluşturup testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9537c-137">From the *unit-testing-using-dotnet-test*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="9537c-138">XUnit Test Çalıştırıcısı, testlerinizi çalıştırmak için program giriş noktasını içerir.</span><span class="sxs-lookup"><span data-stu-id="9537c-138">The xUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="9537c-139">`dotnet test`oluşturduğunuz birim test projesini kullanarak Test Çalıştırıcısı başlatır.</span><span class="sxs-lookup"><span data-stu-id="9537c-139">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="9537c-140">Testiniz başarısız oluyor.</span><span class="sxs-lookup"><span data-stu-id="9537c-140">Your test fails.</span></span> <span data-ttu-id="9537c-141">Uygulamayı henüz oluşturmadınız.</span><span class="sxs-lookup"><span data-stu-id="9537c-141">You haven't created the implementation yet.</span></span> <span data-ttu-id="9537c-142">Bu test geçişini, çalıştıran `PrimeService` sınıfa en basit kodu yazarak yapın:</span><span class="sxs-lookup"><span data-stu-id="9537c-142">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first.")
End Function
```

<span data-ttu-id="9537c-143">*Birim-test-vb-using-DotNet-test* dizininde yeniden çalıştırın `dotnet test` .</span><span class="sxs-lookup"><span data-stu-id="9537c-143">In the *unit-testing-vb-using-dotnet-test* directory, run `dotnet test` again.</span></span> <span data-ttu-id="9537c-144">Komutu, `PrimeService` proje için bir yapı ve ardından projeiçinçalışır.`PrimeService.Tests` `dotnet test`</span><span class="sxs-lookup"><span data-stu-id="9537c-144">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="9537c-145">Her iki proje de oluşturulduktan sonra bu tek testi çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="9537c-145">After building both projects, it runs this single test.</span></span> <span data-ttu-id="9537c-146">Geçirir.</span><span class="sxs-lookup"><span data-stu-id="9537c-146">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="9537c-147">Daha fazla özellik ekleme</span><span class="sxs-lookup"><span data-stu-id="9537c-147">Adding more features</span></span>

<span data-ttu-id="9537c-148">Artık bir test geçişi yapmış olduğunuza göre daha fazla yazma zamanı vardır.</span><span class="sxs-lookup"><span data-stu-id="9537c-148">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="9537c-149">Asal sayıların diğer birkaç basit durumu vardır: 0,-1.</span><span class="sxs-lookup"><span data-stu-id="9537c-149">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="9537c-150">Bu servis taleplerini `<Fact>` özniteliğiyle yeni testler olarak ekleyebilirsiniz, ancak bu, hızlı bir şekilde sıkıcı hale gelir.</span><span class="sxs-lookup"><span data-stu-id="9537c-150">You could add those cases as new tests with the `<Fact>` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="9537c-151">Benzer testlerin bir paketini yazmanızı sağlayan başka xUnit öznitelikleri vardır.</span><span class="sxs-lookup"><span data-stu-id="9537c-151">There are other xUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="9537c-152">`<Theory>` Öznitelik, aynı kodu çalıştıran ancak farklı giriş bağımsız değişkenlerine sahip olan bir test paketini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9537c-152">A `<Theory>` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="9537c-153">Bu girişlerin değerlerini belirtmek `<InlineData>` için özniteliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9537c-153">You can use the `<InlineData>` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="9537c-154">Yeni test oluşturmak yerine, tek bir teorisi oluşturmak için bu iki özniteliği uygulayın.</span><span class="sxs-lookup"><span data-stu-id="9537c-154">Instead of creating new tests, apply these two attributes to create a single theory.</span></span> <span data-ttu-id="9537c-155">Teorisi, en düşük asal sayı olan iki değerden küçük birkaç değeri sınayan bir yöntemdir:</span><span class="sxs-lookup"><span data-stu-id="9537c-155">The theory is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

<span data-ttu-id="9537c-156">Çalıştır `dotnet test`ve bu testlerin ikisi de başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="9537c-156">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="9537c-157">Tüm testlerin geçişini yapmak için yönteminin başındaki `if` yan tümceyi değiştirin:</span><span class="sxs-lookup"><span data-stu-id="9537c-157">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```vb
if candidate < 2
```

<span data-ttu-id="9537c-158">Ana kitaplıkta daha fazla test, daha fazla yer ve daha fazla kod ekleyerek yinelemek için devam edin.</span><span class="sxs-lookup"><span data-stu-id="9537c-158">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="9537c-159">[Testlerin tamamlanmış sürümüne](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) ve [kitaplığın tüm uygulamasına](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService/PrimeService.vb)sahipsiniz.</span><span class="sxs-lookup"><span data-stu-id="9537c-159">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="9537c-160">Bu kitaplık için küçük bir kitaplık ve birim testleri kümesi oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="9537c-160">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="9537c-161">Çözümü, yeni paket ve test eklemek normal iş akışının bir parçası olacak şekilde öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="9537c-161">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="9537c-162">Uygulamanın hedeflerini çözme konusunda zaman ve çaba harcamanızı en iyi şekilde gördünüz.</span><span class="sxs-lookup"><span data-stu-id="9537c-162">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
