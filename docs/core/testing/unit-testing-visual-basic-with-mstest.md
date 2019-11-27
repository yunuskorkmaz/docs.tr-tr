---
title: DotNet test ve MSTest ile .NET Core 'da birim testi Visual Basic
description: Etkileşimli bir deneyim aracılığıyla .NET Core 'daki birim testi kavramlarını, MSTest kullanarak bir örnek Visual Basic çözüm oluşturma adımını öğrenin.
author: billwagner
ms.author: wiwagn
ms.date: 09/01/2017
ms.custom: seodec18
ms.openlocfilehash: c52fc7393718f6af44bd85dd23353f3e32f29f79
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428721"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-mstest"></a><span data-ttu-id="af43c-103">DotNet test ve MSTest kullanarak .NET Core kitaplıkları Visual Basic birim testi</span><span class="sxs-lookup"><span data-stu-id="af43c-103">Unit testing Visual Basic .NET Core libraries using dotnet test and MSTest</span></span>

<span data-ttu-id="af43c-104">Bu öğreticide, birim testi kavramlarını öğrenmek için bir örnek çözüm oluşturma adım adım yönergeler sunarak etkileşimli bir deneyim sağlanır.</span><span class="sxs-lookup"><span data-stu-id="af43c-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="af43c-105">Önceden oluşturulmuş bir çözüm kullanarak öğreticiyi izlemeyi tercih ediyorsanız, başlamadan önce [örnek kodu görüntüleyin veya indirin](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-mstest/) .</span><span class="sxs-lookup"><span data-stu-id="af43c-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-mstest/) before you begin.</span></span> <span data-ttu-id="af43c-106">İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="af43c-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="creating-the-source-project"></a><span data-ttu-id="af43c-107">Kaynak proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="af43c-107">Creating the source project</span></span>

<span data-ttu-id="af43c-108">Bir kabuk penceresi açın.</span><span class="sxs-lookup"><span data-stu-id="af43c-108">Open a shell window.</span></span> <span data-ttu-id="af43c-109">Çözümü tutmak için *Unit-Testing-vb-MSTest* adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="af43c-109">Create a directory called *unit-testing-vb-mstest* to hold the solution.</span></span>
<span data-ttu-id="af43c-110">Yeni bir çözüm oluşturmak için bu yeni dizinin içinde [`dotnet new sln`](../tools/dotnet-new.md) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="af43c-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="af43c-111">Bu uygulama, hem sınıf kitaplığını hem de birim testi projesini yönetmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="af43c-111">This practice makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="af43c-112">Çözüm dizini içinde bir *Primeservice* dizini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="af43c-112">Inside the solution directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="af43c-113">Şu ana kadar Şu dizin ve dosya yapısına sahipsiniz:</span><span class="sxs-lookup"><span data-stu-id="af43c-113">You have the following directory and file structure thus far:</span></span>

```console
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
```

<span data-ttu-id="af43c-114">Kaynak projeyi oluşturmak için *Primeservice* 'i geçerli dizin yapın ve [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="af43c-114">Make *PrimeService* the current directory and run [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="af43c-115">*Class1. vb* ' i *primeservice. vb*olarak yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="af43c-115">Rename *Class1.VB* to *PrimeService.VB*.</span></span> <span data-ttu-id="af43c-116">`PrimeService` sınıfının başarısız bir uygulamasını oluşturursunuz:</span><span class="sxs-lookup"><span data-stu-id="af43c-116">You create a failing implementation of the `PrimeService` class:</span></span>

```vb
Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first")
        End Function
    End Class
End Namespace
```

<span data-ttu-id="af43c-117">Dizini *birim-test-vb-using-MSTest* dizinine geri çevirin.</span><span class="sxs-lookup"><span data-stu-id="af43c-117">Change the directory back to the *unit-testing-vb-using-mstest* directory.</span></span> <span data-ttu-id="af43c-118">Çözüme Sınıf Kitaplığı projesini eklemek için [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="af43c-118">Run [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="af43c-119">Test projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="af43c-119">Creating the test project</span></span>

<span data-ttu-id="af43c-120">Ardından, *Primeservice. Tests* dizinini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="af43c-120">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="af43c-121">Aşağıdaki ana hat dizin yapısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="af43c-121">The following outline shows the directory structure:</span></span>

```console
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

<span data-ttu-id="af43c-122">*Primeservice. test* dizinini geçerli dizini yapın ve [`dotnet new mstest -lang VB`](../tools/dotnet-new.md)kullanarak yeni bir proje oluşturun.</span><span class="sxs-lookup"><span data-stu-id="af43c-122">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new mstest -lang VB`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="af43c-123">Bu komut, test kitaplığı olarak MSTest kullanan bir test projesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="af43c-123">This command creates a test project that uses MSTest as the test library.</span></span> <span data-ttu-id="af43c-124">Oluşturulan şablon, *Primeservicetests. vbproj*içindeki Test Çalıştırıcısı 'nı yapılandırır:</span><span class="sxs-lookup"><span data-stu-id="af43c-124">The generated template configures the test runner in the *PrimeServiceTests.vbproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

<span data-ttu-id="af43c-125">Test projesi, birim testlerini oluşturmak ve çalıştırmak için diğer paketlerin kullanılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="af43c-125">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="af43c-126">önceki adımda `dotnet new` MSTest ve MSTest Çalıştırıcısı eklendi.</span><span class="sxs-lookup"><span data-stu-id="af43c-126">`dotnet new` in the previous step added MSTest and the MSTest runner.</span></span> <span data-ttu-id="af43c-127">Şimdi, `PrimeService` sınıf kitaplığını projeye başka bir bağımlılık olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="af43c-127">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="af43c-128">[`dotnet add reference`](../tools/dotnet-add-reference.md) komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="af43c-128">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.vbproj
```

<span data-ttu-id="af43c-129">GitHub 'daki [örnekler deposunda](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService.Tests.vbproj) dosyanın tamamını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="af43c-129">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span></span>

<span data-ttu-id="af43c-130">Aşağıdaki son çözüm düzenine sahipsiniz:</span><span class="sxs-lookup"><span data-stu-id="af43c-130">You have the following final solution layout:</span></span>

```console
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.vbproj
```

<span data-ttu-id="af43c-131">[`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) , *birim-test-vb-MSTest* dizininde yürütün.</span><span class="sxs-lookup"><span data-stu-id="af43c-131">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) in the *unit-testing-vb-mstest* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="af43c-132">İlk test oluşturma</span><span class="sxs-lookup"><span data-stu-id="af43c-132">Creating the first test</span></span>

<span data-ttu-id="af43c-133">Başarısız bir test yazdığınızda, geçişi yapıp işlemi tekrarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="af43c-133">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="af43c-134">*UnitTest1. vb* 'Yi *primeservice. Tests* dizininden KALDıRıN ve *PrimeService_IsPrimeShould. vb*adlı yeni bir Visual Basic dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="af43c-134">Remove *UnitTest1.vb* from the *PrimeService.Tests* directory and create a new Visual Basic file named *PrimeService_IsPrimeShould.VB*.</span></span> <span data-ttu-id="af43c-135">Aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="af43c-135">Add the following code:</span></span>

```vb
Imports Microsoft.VisualStudio.TestTools.UnitTesting

Namespace PrimeService.Tests
    <TestClass>
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <TestMethod>
        Sub IsPrime_InputIs1_ReturnFalse()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.IsFalse(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

<span data-ttu-id="af43c-136">`<TestClass>` özniteliği, testleri içeren bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="af43c-136">The `<TestClass>` attribute indicates a class that contains tests.</span></span> <span data-ttu-id="af43c-137">`<TestMethod>` özniteliği, Test Çalıştırıcısı tarafından çalıştırılan bir yöntemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="af43c-137">The `<TestMethod>` attribute denotes a method that is run by the test runner.</span></span> <span data-ttu-id="af43c-138">*-Testing-vb-MSTest*, testleri ve sınıf kitaplığını oluşturmak ve ardından testleri çalıştırmak için [`dotnet test`](../tools/dotnet-test.md) yürütün.</span><span class="sxs-lookup"><span data-stu-id="af43c-138">From the *unit-testing-vb-mstest*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="af43c-139">MSTest Test Çalıştırıcısı, testlerinizi çalıştırmak için program giriş noktasını içerir.</span><span class="sxs-lookup"><span data-stu-id="af43c-139">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="af43c-140">`dotnet test`, oluşturduğunuz birim test projesini kullanarak Test Çalıştırıcısı başlatır.</span><span class="sxs-lookup"><span data-stu-id="af43c-140">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="af43c-141">Testiniz başarısız oluyor.</span><span class="sxs-lookup"><span data-stu-id="af43c-141">Your test fails.</span></span> <span data-ttu-id="af43c-142">Uygulamayı henüz oluşturmadınız.</span><span class="sxs-lookup"><span data-stu-id="af43c-142">You haven't created the implementation yet.</span></span> <span data-ttu-id="af43c-143">Aşağıdaki `PrimeService` sınıfında en basit kodu yazarak bu test geçişini yapın:</span><span class="sxs-lookup"><span data-stu-id="af43c-143">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first.")
End Function
```

<span data-ttu-id="af43c-144">*Birim-test-vb-MSTest* dizininde `dotnet test` yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="af43c-144">In the *unit-testing-vb-mstest* directory, run `dotnet test` again.</span></span> <span data-ttu-id="af43c-145">`dotnet test` komutu, `PrimeService` projesi için bir derleme ve sonra `PrimeService.Tests` projesi için çalışır.</span><span class="sxs-lookup"><span data-stu-id="af43c-145">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="af43c-146">Her iki proje de oluşturulduktan sonra bu tek testi çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="af43c-146">After building both projects, it runs this single test.</span></span> <span data-ttu-id="af43c-147">Geçirir.</span><span class="sxs-lookup"><span data-stu-id="af43c-147">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="af43c-148">Daha fazla özellik ekleme</span><span class="sxs-lookup"><span data-stu-id="af43c-148">Adding more features</span></span>

<span data-ttu-id="af43c-149">Artık bir test geçişi yapmış olduğunuza göre daha fazla yazma zamanı vardır.</span><span class="sxs-lookup"><span data-stu-id="af43c-149">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="af43c-150">Asal sayıların diğer birkaç basit durumu vardır: 0,-1.</span><span class="sxs-lookup"><span data-stu-id="af43c-150">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="af43c-151">Bu servis taleplerini `<TestMethod>` özniteliğiyle yeni testler olarak ekleyebilirsiniz, ancak bu hızlı bir şekilde sıkıcı olur.</span><span class="sxs-lookup"><span data-stu-id="af43c-151">You could add those cases as new tests with the `<TestMethod>` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="af43c-152">Benzer testlerin bir paketini yazmanızı sağlayan başka bir MSTest özniteliği vardır.</span><span class="sxs-lookup"><span data-stu-id="af43c-152">There are other MSTest attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="af43c-153">Bir `<DataTestMethod>` özniteliği, aynı kodu çalıştıran ancak farklı giriş bağımsız değişkenlerine sahip olan bir test paketini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="af43c-153">A `<DataTestMethod>` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="af43c-154">Bu girişlerin değerlerini belirtmek için `<DataRow>` özniteliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="af43c-154">You can use the `<DataRow>` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="af43c-155">Yeni test oluşturmak yerine, tek bir teorisi oluşturmak için bu iki özniteliği uygulayın.</span><span class="sxs-lookup"><span data-stu-id="af43c-155">Instead of creating new tests, apply these two attributes to create a single theory.</span></span> <span data-ttu-id="af43c-156">Teorisi, en düşük asal sayı olan iki değerden küçük birkaç değeri sınayan bir yöntemdir:</span><span class="sxs-lookup"><span data-stu-id="af43c-156">The theory is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

<span data-ttu-id="af43c-157">`dotnet test`çalıştırın, bu testlerin ikisi de başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="af43c-157">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="af43c-158">Tüm testlerin geçişini yapmak için, yönteminin başındaki `if` yan tümcesini değiştirin:</span><span class="sxs-lookup"><span data-stu-id="af43c-158">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```vb
if candidate < 2
```

<span data-ttu-id="af43c-159">Ana kitaplıkta daha fazla test, daha fazla yer ve daha fazla kod ekleyerek yinelemek için devam edin.</span><span class="sxs-lookup"><span data-stu-id="af43c-159">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="af43c-160">[Testlerin tamamlanmış sürümüne](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb) ve [kitaplığın tüm uygulamasına](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService/PrimeService.vb)sahipsiniz.</span><span class="sxs-lookup"><span data-stu-id="af43c-160">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="af43c-161">Bu kitaplık için küçük bir kitaplık ve birim testleri kümesi oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="af43c-161">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="af43c-162">Çözümü, yeni paket ve test eklemek normal iş akışının bir parçası olacak şekilde öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="af43c-162">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="af43c-163">Uygulamanın hedeflerini çözme konusunda zaman ve çaba harcamanızı en iyi şekilde gördünüz.</span><span class="sxs-lookup"><span data-stu-id="af43c-163">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
