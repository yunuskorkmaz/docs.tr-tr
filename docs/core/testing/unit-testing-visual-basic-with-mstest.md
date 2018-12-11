---
title: Dotnet testi ve MSTest ile .NET Core Visual Basic test birimi
description: Adım adım örnek Visual Basic çözüm oluşturma etkileşimli bir deneyim .NET Core birim testi kavramları öğrenin mstest'i kullanarak.
author: billwagner
ms.author: wiwagn
ms.date: 09/01/2017
dev_langs:
- vb
ms.custom: seodec18
ms.openlocfilehash: cc4f84551d28ad531713e31a27df723a78b338cb
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53242470"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-mstest"></a><span data-ttu-id="97ba1-103">Birim testi dotnet testi ve MStest kullanarak Visual Basic .NET Core kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="97ba1-103">Unit testing Visual Basic .NET Core libraries using dotnet test and MStest</span></span>

<span data-ttu-id="97ba1-104">Bu öğretici örnek bir çözüm birim testi kavramlarını öğrenmek için adım adım oluşturmaya etkileşimli deneyim gösterir.</span><span class="sxs-lookup"><span data-stu-id="97ba1-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="97ba1-105">Önceden oluşturulmuş bir çözümü kullanarak öğreticiyi uygulamak isterseniz [görüntülemek veya örnek kodu indirdikten](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-mstest/) başlamadan önce.</span><span class="sxs-lookup"><span data-stu-id="97ba1-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-mstest/) before you begin.</span></span> <span data-ttu-id="97ba1-106">Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="97ba1-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="97ba1-107">Kaynak proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="97ba1-107">Creating the source project</span></span>

<span data-ttu-id="97ba1-108">Shell penceresini açın.</span><span class="sxs-lookup"><span data-stu-id="97ba1-108">Open a shell window.</span></span> <span data-ttu-id="97ba1-109">Adlı bir dizin oluşturun *birim testi vb mstest* çözüm tutacak.</span><span class="sxs-lookup"><span data-stu-id="97ba1-109">Create a directory called *unit-testing-vb-mstest* to hold the solution.</span></span>
<span data-ttu-id="97ba1-110">Bu yeni dizin içinde çalıştırma [ `dotnet new sln` ](../tools/dotnet-new.md) yeni bir çözüm oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="97ba1-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="97ba1-111">Bu yöntem, sınıf kitaplığı hem birim test projesi yönetmenizi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="97ba1-111">This practice makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="97ba1-112">Çözüm dizini içinde bir *PrimeService* dizin.</span><span class="sxs-lookup"><span data-stu-id="97ba1-112">Inside the solution directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="97ba1-113">Aşağıdaki dizin ve dosya yapısı şimdiye kadarki vardır:</span><span class="sxs-lookup"><span data-stu-id="97ba1-113">You have the following directory and file structure thus far:</span></span>

```
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
```

<span data-ttu-id="97ba1-114">Olun *PrimeService* geçerli dizin ve çalışma [ `dotnet new classlib -lang VB` ](../tools/dotnet-new.md) kaynak proje oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="97ba1-114">Make *PrimeService* the current directory and run [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="97ba1-115">Yeniden adlandırma *Class1.VB* için *PrimeService.VB*.</span><span class="sxs-lookup"><span data-stu-id="97ba1-115">Rename *Class1.VB* to *PrimeService.VB*.</span></span> <span data-ttu-id="97ba1-116">Teste dayalı geliştirme (TDD) kullanmak için bir başarısız uygulaması oluşturun. `PrimeService` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="97ba1-116">To use test-driven development (TDD), you create a failing implementation of the `PrimeService` class:</span></span>

```vb
Imports System

Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first")
        End Function
    End Class
End Namespace
```

<span data-ttu-id="97ba1-117">Dizine dön değişiklik *birim-test-vb-kullanarak-stest* dizin.</span><span class="sxs-lookup"><span data-stu-id="97ba1-117">Change the directory back to the *unit-testing-vb-using-stest* directory.</span></span> <span data-ttu-id="97ba1-118">Çalıştırma [ `dotnet sln add .\PrimeService\PrimeService.vbproj` ](../tools/dotnet-sln.md) sınıf kitaplığı projesi çözüme eklemek için.</span><span class="sxs-lookup"><span data-stu-id="97ba1-118">Run [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="97ba1-119">Test projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="97ba1-119">Creating the test project</span></span>

<span data-ttu-id="97ba1-120">Ardından, oluşturma *PrimeService.Tests* dizin.</span><span class="sxs-lookup"><span data-stu-id="97ba1-120">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="97ba1-121">Ana hat aşağıdaki dizin yapısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="97ba1-121">The following outline shows the directory structure:</span></span>

```
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

<span data-ttu-id="97ba1-122">Olun *PrimeService.Tests* dizini geçerli dizin ve kullanarak yeni bir proje oluşturma [ `dotnet new mstest -lang VB` ](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="97ba1-122">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new mstest -lang VB`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="97ba1-123">Bu komut, MSTest test kitaplık olarak kullanan bir test projesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="97ba1-123">This command creates a test project that uses MSTest as the test library.</span></span> <span data-ttu-id="97ba1-124">Test Çalıştırıcısı'nda oluşturulan şablon yapılandırır *PrimeServiceTests.vbproj*:</span><span class="sxs-lookup"><span data-stu-id="97ba1-124">The generated template configures the test runner in the *PrimeServiceTests.vbproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

<span data-ttu-id="97ba1-125">Test projesi oluşturma ve birim testlerini çalıştırmak için diğer paketleri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="97ba1-125">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="97ba1-126">`dotnet new` Önceki adımda, MSTest ve MSTest Çalıştırıcısı eklendi.</span><span class="sxs-lookup"><span data-stu-id="97ba1-126">`dotnet new` in the previous step added MSTest and the MSTest runner.</span></span> <span data-ttu-id="97ba1-127">Şimdi ekleyin `PrimeService` sınıf kitaplığı projesine başka bir bağımlılık olarak.</span><span class="sxs-lookup"><span data-stu-id="97ba1-127">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="97ba1-128">Kullanım [ `dotnet add reference` ](../tools/dotnet-add-reference.md) komutu:</span><span class="sxs-lookup"><span data-stu-id="97ba1-128">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.vbproj
```

<span data-ttu-id="97ba1-129">Dosyanın tamamını görebilirsiniz [örnekleri depomuzdan](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService.Tests.vbproj) GitHub üzerinde.</span><span class="sxs-lookup"><span data-stu-id="97ba1-129">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span></span>

<span data-ttu-id="97ba1-130">Aşağıdaki nihai çözüm Düzen vardır:</span><span class="sxs-lookup"><span data-stu-id="97ba1-130">You have the following final solution layout:</span></span>

```
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.vbproj
```

<span data-ttu-id="97ba1-131">Yürütme [ `dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj` ](../tools/dotnet-sln.md) içinde *birim testi vb mstest* dizin.</span><span class="sxs-lookup"><span data-stu-id="97ba1-131">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) in the *unit-testing-vb-mstest* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="97ba1-132">İlk testi oluşturma</span><span class="sxs-lookup"><span data-stu-id="97ba1-132">Creating the first test</span></span>

<span data-ttu-id="97ba1-133">TDD yaklaşım geçer hale getirme ve süreci tekrarlayarak yazma bir başarısız test için çağırır.</span><span class="sxs-lookup"><span data-stu-id="97ba1-133">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="97ba1-134">Kaldırma *UnitTest1.vb* gelen *PrimeService.Tests* dizin adlı yeni bir Visual Basic dosyası oluşturup *PrimeService_IsPrimeShould.VB*.</span><span class="sxs-lookup"><span data-stu-id="97ba1-134">Remove *UnitTest1.vb* from the *PrimeService.Tests* directory and create a new Visual Basic file named *PrimeService_IsPrimeShould.VB*.</span></span> <span data-ttu-id="97ba1-135">Aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="97ba1-135">Add the following code:</span></span>

```vb
Imports Microsoft.VisualStudio.TestTools.UnitTesting

Namespace PrimeService.Tests
    <TestClass>
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <TestMethod>
        Sub ReturnFalseGivenValueOf1()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

<span data-ttu-id="97ba1-136">`<TestClass>` Öznitelik, testleri içeren bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="97ba1-136">The `<TestClass>` attribute indicates a class that contains tests.</span></span> <span data-ttu-id="97ba1-137">`<TestMethod>` Özniteliği test Çalıştırıcısı tarafından yürütülen bir yöntemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="97ba1-137">The `<TestMethod>` attribute denotes a method that is run by the test runner.</span></span> <span data-ttu-id="97ba1-138">Gelen *birim testi vb mstest*, yürütme [ `dotnet test` ](../tools/dotnet-test.md) testler ve sınıf kitaplığı oluşturun ve ardından testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="97ba1-138">From the *unit-testing-vb-mstest*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="97ba1-139">Programın giriş noktası, testlerinizi çalıştırmak için MSTest test Çalıştırıcısı içerir.</span><span class="sxs-lookup"><span data-stu-id="97ba1-139">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="97ba1-140">`dotnet test` oluşturduğunuz birim test projesi kullanarak test Çalıştırıcısı'nı başlatır.</span><span class="sxs-lookup"><span data-stu-id="97ba1-140">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="97ba1-141">Test başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="97ba1-141">Your test fails.</span></span> <span data-ttu-id="97ba1-142">Uygulama henüz oluşturmadınız.</span><span class="sxs-lookup"><span data-stu-id="97ba1-142">You haven't created the implementation yet.</span></span> <span data-ttu-id="97ba1-143">En basit kod yazarak bu testin geçmesini `PrimeService` çalışır sınıfı:</span><span class="sxs-lookup"><span data-stu-id="97ba1-143">Make this test by writing the simplest code in the `PrimeService` class that works:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first")
End Function
```

<span data-ttu-id="97ba1-144">İçinde *birim testi vb mstest* çalışması dizini `dotnet test` yeniden.</span><span class="sxs-lookup"><span data-stu-id="97ba1-144">In the *unit-testing-vb-mstest* directory, run `dotnet test` again.</span></span> <span data-ttu-id="97ba1-145">`dotnet test` Komut çalıştıran bir derleme için `PrimeService` proje ve ardından `PrimeService.Tests` proje.</span><span class="sxs-lookup"><span data-stu-id="97ba1-145">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="97ba1-146">Her iki proje oluşturduktan sonra bu tek bir test çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="97ba1-146">After building both projects, it runs this single test.</span></span> <span data-ttu-id="97ba1-147">Bu geçirir.</span><span class="sxs-lookup"><span data-stu-id="97ba1-147">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="97ba1-148">Daha fazla özellik ekleme</span><span class="sxs-lookup"><span data-stu-id="97ba1-148">Adding more features</span></span>

<span data-ttu-id="97ba1-149">Bir test geçirmek yaptığınız, daha fazla yazmak için zaman var.</span><span class="sxs-lookup"><span data-stu-id="97ba1-149">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="97ba1-150">Birkaç basit durumlardaysa asal sayıları için vardır: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="97ba1-150">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="97ba1-151">Bu gibi durumlarda, yeni testleriyle olarak ekleyebilirsiniz `<TestMethod>` özniteliği ancak hızla olur yorucu bir süreç.</span><span class="sxs-lookup"><span data-stu-id="97ba1-151">You could add those cases as new tests with the `<TestMethod>` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="97ba1-152">Benzer testleri paketi yazmanızı sağlayan diğer MSTest öznitelikleri vardır.</span><span class="sxs-lookup"><span data-stu-id="97ba1-152">There are other MSTest attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="97ba1-153">A `<DataTestMethod>` öznitelik aynı kod yürütün, ancak farklı giriş bağımsız değişkenleri olan testleri paketi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="97ba1-153">A `<DataTestMethod>` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="97ba1-154">Kullanabileceğiniz `<DataRow>` bu girişleri değerlerini belirtmek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="97ba1-154">You can use the `<DataRow>` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="97ba1-155">Yeni testler oluşturmak yerine, tek bir kuramsal oluşturmak için bu iki öznitelikler uygulanır.</span><span class="sxs-lookup"><span data-stu-id="97ba1-155">Instead of creating new tests, apply these two attributes to create a single theory.</span></span> <span data-ttu-id="97ba1-156">Teorik asal numarası en düşük olan değerlerden küçüktür iki test yöntemi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="97ba1-156">The theory is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

<span data-ttu-id="97ba1-157">Çalıştırma `dotnet test`, ve bunlardan ikisi başarısız test eder.</span><span class="sxs-lookup"><span data-stu-id="97ba1-157">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="97ba1-158">Tüm testler başarılı hale getirmek için değiştirme `if` yöntemin başında yan tümcesi:</span><span class="sxs-lookup"><span data-stu-id="97ba1-158">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```vb
if candidate < 2
```

<span data-ttu-id="97ba1-159">Ana Kitaplığı'nda daha fazla test, daha fazla Teoriler ve daha fazla kod ekleyerek yinelemek devam edin.</span><span class="sxs-lookup"><span data-stu-id="97ba1-159">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="97ba1-160">Sahip olduğunuz [testlerinin tamamlanmış bir sürümünü](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb) ve [Kitaplığı'nın tam bir uygulamaya](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService/PrimeService.vb).</span><span class="sxs-lookup"><span data-stu-id="97ba1-160">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="97ba1-161">Küçük bir kitaplık ve bu kitaplık için birim testleri bir dizi oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="97ba1-161">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="97ba1-162">Böylece yeni paketler ekleme çözüm yapılandırılmış ve testleri normal iş akışı bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="97ba1-162">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="97ba1-163">Zaman ve çaba çözme hedeflerinden biri, uygulama üzerinde en yoğun.</span><span class="sxs-lookup"><span data-stu-id="97ba1-163">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
