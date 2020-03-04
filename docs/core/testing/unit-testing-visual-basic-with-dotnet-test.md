---
title: DotNet test ve xUnit ile .NET Core 'da birim testi Visual Basic
description: .NET Core 'da, DotNet test ve xUnit kullanarak örnek Visual Basic çözüm adım adım oluşturma adlı etkileşimli bir deneyim aracılığıyla birim testi kavramlarını öğrenin.
author: billwagner
ms.author: wiwagn
ms.date: 09/01/2017
ms.openlocfilehash: 9a99d9031711a3e958132416d0235df76f4a9092
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240954"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-xunit"></a><span data-ttu-id="668f7-103">DotNet test ve xUnit kullanarak .NET Core kitaplıkları Visual Basic birim testi</span><span class="sxs-lookup"><span data-stu-id="668f7-103">Unit testing Visual Basic .NET Core libraries using dotnet test and xUnit</span></span>

<span data-ttu-id="668f7-104">Bu öğreticide, birim testi kavramlarını öğrenmek için bir örnek çözüm oluşturma adım adım yönergeler sunarak etkileşimli bir deneyim sağlanır.</span><span class="sxs-lookup"><span data-stu-id="668f7-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="668f7-105">Önceden oluşturulmuş bir çözüm kullanarak öğreticiyi izlemeyi tercih ediyorsanız, başlamadan önce [örnek kodu görüntüleyin veya indirin](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-dotnet-test) .</span><span class="sxs-lookup"><span data-stu-id="668f7-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-dotnet-test) before you begin.</span></span> <span data-ttu-id="668f7-106">İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="668f7-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="creating-the-source-project"></a><span data-ttu-id="668f7-107">Kaynak proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="668f7-107">Creating the source project</span></span>

<span data-ttu-id="668f7-108">Bir kabuk penceresi açın.</span><span class="sxs-lookup"><span data-stu-id="668f7-108">Open a shell window.</span></span> <span data-ttu-id="668f7-109">Çözümü tutmak için *birim-test-vb-using-DotNet-test* adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="668f7-109">Create a directory called *unit-testing-vb-using-dotnet-test* to hold the solution.</span></span>
<span data-ttu-id="668f7-110">Yeni bir çözüm oluşturmak için bu yeni dizinin içinde [`dotnet new sln`](../tools/dotnet-new.md) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="668f7-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="668f7-111">Bu uygulama, hem sınıf kitaplığını hem de birim testi projesini yönetmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="668f7-111">This practice makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="668f7-112">Çözüm dizini içinde bir *Primeservice* dizini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="668f7-112">Inside the solution directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="668f7-113">Şu ana kadar Şu dizin ve dosya yapısına sahipsiniz:</span><span class="sxs-lookup"><span data-stu-id="668f7-113">You have the following directory and file structure thus far:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

<span data-ttu-id="668f7-114">Kaynak projeyi oluşturmak için *Primeservice* 'i geçerli dizin yapın ve [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="668f7-114">Make *PrimeService* the current directory and run [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="668f7-115">*Class1. vb* ' i *primeservice. vb*olarak yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="668f7-115">Rename *Class1.VB* to *PrimeService.VB*.</span></span> <span data-ttu-id="668f7-116">`PrimeService` sınıfının başarısız bir uygulamasını oluşturursunuz:</span><span class="sxs-lookup"><span data-stu-id="668f7-116">You create a failing implementation of the `PrimeService` class:</span></span>

```vb
Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first")
        End Function
    End Class
End Namespace
```

<span data-ttu-id="668f7-117">Dizini *birim-test-vb-using-DotNet-test* dizini olarak yeniden değiştirin.</span><span class="sxs-lookup"><span data-stu-id="668f7-117">Change the directory back to the *unit-testing-vb-using-dotnet-test* directory.</span></span> <span data-ttu-id="668f7-118">Çözüme Sınıf Kitaplığı projesini eklemek için [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="668f7-118">Run [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="668f7-119">Test projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="668f7-119">Creating the test project</span></span>

<span data-ttu-id="668f7-120">Ardından, *Primeservice. Tests* dizinini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="668f7-120">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="668f7-121">Aşağıdaki ana hat dizin yapısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="668f7-121">The following outline shows the directory structure:</span></span>

```
/unit-testing-vb-using-dotnet-test
    unit-testing-vb-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

<span data-ttu-id="668f7-122">*Primeservice. test* dizinini geçerli dizini yapın ve [`dotnet new xunit -lang VB`](../tools/dotnet-new.md)kullanarak yeni bir proje oluşturun.</span><span class="sxs-lookup"><span data-stu-id="668f7-122">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new xunit -lang VB`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="668f7-123">Bu komut, test kitaplığı olarak xUnit kullanan bir test projesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="668f7-123">This command creates a test project that uses xUnit as the test library.</span></span> <span data-ttu-id="668f7-124">Oluşturulan şablon, *Primeservicetests. vbproj*içindeki Test Çalıştırıcısı 'nı yapılandırır:</span><span class="sxs-lookup"><span data-stu-id="668f7-124">The generated template configures the test runner in the *PrimeServiceTests.vbproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

<span data-ttu-id="668f7-125">Test projesi, birim testlerini oluşturmak ve çalıştırmak için diğer paketlerin kullanılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="668f7-125">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="668f7-126">önceki adımda `dotnet new` xUnit ve xUnit Çalıştırıcısı eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="668f7-126">`dotnet new` in the previous step added xUnit and the xUnit runner.</span></span> <span data-ttu-id="668f7-127">Şimdi, `PrimeService` sınıf kitaplığını projeye başka bir bağımlılık olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="668f7-127">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="668f7-128">[`dotnet add reference`](../tools/dotnet-add-reference.md) komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="668f7-128">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.vbproj
```

<span data-ttu-id="668f7-129">GitHub 'daki [örnekler deposunda](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService.Tests.vbproj) dosyanın tamamını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="668f7-129">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span></span>

<span data-ttu-id="668f7-130">Aşağıdaki son klasör düzenine sahipsiniz:</span><span class="sxs-lookup"><span data-stu-id="668f7-130">You have the following final folder layout:</span></span>

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

<span data-ttu-id="668f7-131">[`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) *birim-test-vb-using-DotNet-test* dizininde yürütün.</span><span class="sxs-lookup"><span data-stu-id="668f7-131">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) in the *unit-testing-vb-using-dotnet-test* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="668f7-132">İlk test oluşturma</span><span class="sxs-lookup"><span data-stu-id="668f7-132">Creating the first test</span></span>

<span data-ttu-id="668f7-133">Başarısız bir test yazdığınızda, geçişi yapıp işlemi tekrarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="668f7-133">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="668f7-134">*UnitTest1. vb* 'Yi *primeservice. Tests* dizininden KALDıRıN ve *PrimeService_IsPrimeShould. vb*adlı yeni bir Visual Basic dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="668f7-134">Remove *UnitTest1.vb* from the *PrimeService.Tests* directory and create a new Visual Basic file named *PrimeService_IsPrimeShould.VB*.</span></span> <span data-ttu-id="668f7-135">Aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="668f7-135">Add the following code:</span></span>

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

<span data-ttu-id="668f7-136">`<Fact>` özniteliği, Test Çalıştırıcısı tarafından çalıştırılan bir test yöntemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="668f7-136">The `<Fact>` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="668f7-137">*Birim-test--DotNet-test*' i kullanarak, testleri ve sınıf kitaplığını oluşturmak için [`dotnet test`](../tools/dotnet-test.md) yürütün ve ardından testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="668f7-137">From the *unit-testing-using-dotnet-test*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="668f7-138">XUnit Test Çalıştırıcısı, testlerinizi çalıştırmak için program giriş noktasını içerir.</span><span class="sxs-lookup"><span data-stu-id="668f7-138">The xUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="668f7-139">`dotnet test`, oluşturduğunuz birim test projesini kullanarak Test Çalıştırıcısı başlatır.</span><span class="sxs-lookup"><span data-stu-id="668f7-139">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="668f7-140">Testiniz başarısız oluyor.</span><span class="sxs-lookup"><span data-stu-id="668f7-140">Your test fails.</span></span> <span data-ttu-id="668f7-141">Uygulamayı henüz oluşturmadınız.</span><span class="sxs-lookup"><span data-stu-id="668f7-141">You haven't created the implementation yet.</span></span> <span data-ttu-id="668f7-142">Aşağıdaki `PrimeService` sınıfında en basit kodu yazarak bu test geçişini yapın:</span><span class="sxs-lookup"><span data-stu-id="668f7-142">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first.")
End Function
```

<span data-ttu-id="668f7-143">*Birim-test-vb-using-DotNet-test* dizininde, `dotnet test` yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="668f7-143">In the *unit-testing-vb-using-dotnet-test* directory, run `dotnet test` again.</span></span> <span data-ttu-id="668f7-144">`dotnet test` komutu, `PrimeService` projesi için bir derleme ve sonra `PrimeService.Tests` projesi için çalışır.</span><span class="sxs-lookup"><span data-stu-id="668f7-144">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="668f7-145">Her iki proje de oluşturulduktan sonra bu tek testi çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="668f7-145">After building both projects, it runs this single test.</span></span> <span data-ttu-id="668f7-146">Geçirir.</span><span class="sxs-lookup"><span data-stu-id="668f7-146">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="668f7-147">Daha fazla özellik ekleme</span><span class="sxs-lookup"><span data-stu-id="668f7-147">Adding more features</span></span>

<span data-ttu-id="668f7-148">Artık bir test geçişi yapmış olduğunuza göre daha fazla yazma zamanı vardır.</span><span class="sxs-lookup"><span data-stu-id="668f7-148">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="668f7-149">Asal sayıların diğer birkaç basit durumu vardır: 0,-1.</span><span class="sxs-lookup"><span data-stu-id="668f7-149">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="668f7-150">Bu servis taleplerini `<Fact>` özniteliğiyle yeni testler olarak ekleyebilirsiniz, ancak bu hızlı bir şekilde sıkıcı olur.</span><span class="sxs-lookup"><span data-stu-id="668f7-150">You could add those cases as new tests with the `<Fact>` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="668f7-151">Benzer testlerin bir paketini yazmanızı sağlayan başka xUnit öznitelikleri vardır.</span><span class="sxs-lookup"><span data-stu-id="668f7-151">There are other xUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="668f7-152">Bir `<Theory>` özniteliği, aynı kodu çalıştıran ancak farklı giriş bağımsız değişkenlerine sahip olan bir test paketini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="668f7-152">A `<Theory>` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="668f7-153">Bu girişlerin değerlerini belirtmek için `<InlineData>` özniteliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="668f7-153">You can use the `<InlineData>` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="668f7-154">Yeni test oluşturmak yerine, tek bir teorisi oluşturmak için bu iki özniteliği uygulayın.</span><span class="sxs-lookup"><span data-stu-id="668f7-154">Instead of creating new tests, apply these two attributes to create a single theory.</span></span> <span data-ttu-id="668f7-155">Teorisi, en düşük asal sayı olan iki değerden küçük birkaç değeri sınayan bir yöntemdir:</span><span class="sxs-lookup"><span data-stu-id="668f7-155">The theory is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-vb[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-vb-dotnet-test/vb/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

<span data-ttu-id="668f7-156">`dotnet test`çalıştırın, bu testlerin ikisi de başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="668f7-156">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="668f7-157">Tüm testlerin geçişini yapmak için, yönteminin başındaki `if` yan tümcesini değiştirin:</span><span class="sxs-lookup"><span data-stu-id="668f7-157">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```vb
if candidate < 2
```

<span data-ttu-id="668f7-158">Ana kitaplıkta daha fazla test, daha fazla yer ve daha fazla kod ekleyerek yinelemek için devam edin.</span><span class="sxs-lookup"><span data-stu-id="668f7-158">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="668f7-159">[Testlerin tamamlanmış sürümüne](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) ve [kitaplığın tüm uygulamasına](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService/PrimeService.vb)sahipsiniz.</span><span class="sxs-lookup"><span data-stu-id="668f7-159">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="668f7-160">Bu kitaplık için küçük bir kitaplık ve birim testleri kümesi oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="668f7-160">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="668f7-161">Çözümü, yeni paket ve test eklemek normal iş akışının bir parçası olacak şekilde öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="668f7-161">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="668f7-162">Uygulamanın hedeflerini çözme konusunda zaman ve çaba harcamanızı en iyi şekilde gördünüz.</span><span class="sxs-lookup"><span data-stu-id="668f7-162">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
