---
title: Visual Basic .NET Core dotnet testi ve NUnit ile birim testi
description: Adım adım örnek Visual Basic çözüm oluşturma etkileşimli bir deneyim .NET Core birim testi kavramları öğrenin NUnit kullanarak.
author: rprouse
ms.date: 10/04/2018
dev_langs:
- vb
ms.custom: seodec18
ms.openlocfilehash: cf8a81241c93a6eeecf04052aba57750774aa050
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67397501"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-nunit"></a><span data-ttu-id="d4376-103">Birim testi dotnet testi ve NUnit kullanarak Visual Basic .NET Core kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="d4376-103">Unit testing Visual Basic .NET Core libraries using dotnet test and NUnit</span></span>

<span data-ttu-id="d4376-104">Bu öğretici örnek bir çözüm birim testi kavramlarını öğrenmek için adım adım oluşturmaya etkileşimli deneyim gösterir.</span><span class="sxs-lookup"><span data-stu-id="d4376-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="d4376-105">Önceden oluşturulmuş bir çözümü kullanarak öğreticiyi uygulamak isterseniz [görüntülemek veya örnek kodu indirdikten](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-nunit/) başlamadan önce.</span><span class="sxs-lookup"><span data-stu-id="d4376-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-nunit/) before you begin.</span></span> <span data-ttu-id="d4376-106">Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="d4376-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d4376-107">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="d4376-107">Prerequisites</span></span>

- <span data-ttu-id="d4376-108">[.NET core 2.1 SDK](https://www.microsoft.com/net/download) veya sonraki sürümler.</span><span class="sxs-lookup"><span data-stu-id="d4376-108">[.NET Core 2.1 SDK](https://www.microsoft.com/net/download) or later versions.</span></span>
- <span data-ttu-id="d4376-109">Bir metin düzenleyicisi veya tercih ettiğiniz Kod Düzenleyicisi.</span><span class="sxs-lookup"><span data-stu-id="d4376-109">A text editor or code editor of your choice.</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="d4376-110">Kaynak proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="d4376-110">Creating the source project</span></span>

<span data-ttu-id="d4376-111">Shell penceresini açın.</span><span class="sxs-lookup"><span data-stu-id="d4376-111">Open a shell window.</span></span> <span data-ttu-id="d4376-112">Adlı bir dizin oluşturun *birim testi vb nunit* çözüm tutacak.</span><span class="sxs-lookup"><span data-stu-id="d4376-112">Create a directory called *unit-testing-vb-nunit* to hold the solution.</span></span> <span data-ttu-id="d4376-113">Bu yeni dizin içinde sınıf kitaplığı ve test projesi için yeni bir çözüm dosyası oluşturmak için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="d4376-113">Inside this new directory, run the following command to create a new solution file for the class library and the test project:</span></span>

```console
dotnet new sln
```

<span data-ttu-id="d4376-114">Ardından, oluşturun bir *PrimeService* dizin.</span><span class="sxs-lookup"><span data-stu-id="d4376-114">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="d4376-115">Aşağıdaki ana hat kadar dosya yapısı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="d4376-115">The following outline shows the file structure so far:</span></span>

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
```

<span data-ttu-id="d4376-116">Olun *PrimeService* aşağıdaki komut kaynak projesi oluşturmak için geçerli dizin ve çalıştırma:</span><span class="sxs-lookup"><span data-stu-id="d4376-116">Make *PrimeService* the current directory and run the following command to create the source project:</span></span>

```console
dotnet new classlib -lang VB
```

<span data-ttu-id="d4376-117">Yeniden adlandırma *Class1.VB* için *PrimeService.VB*.</span><span class="sxs-lookup"><span data-stu-id="d4376-117">Rename *Class1.VB* to *PrimeService.VB*.</span></span> <span data-ttu-id="d4376-118">Bir başarısız uygulamasını oluşturun `PrimeService` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="d4376-118">You create a failing implementation of the `PrimeService` class:</span></span>

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

<span data-ttu-id="d4376-119">Dizine dön değişiklik *birim-test-vb-kullanarak-mstest* dizin.</span><span class="sxs-lookup"><span data-stu-id="d4376-119">Change the directory back to the *unit-testing-vb-using-mstest* directory.</span></span> <span data-ttu-id="d4376-120">Sınıf kitaplığı projesi çözüme eklemek için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="d4376-120">Run the following command to add the class library project to the solution:</span></span>

```console
dotnet sln add .\PrimeService\PrimeService.vbproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="d4376-121">Test projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="d4376-121">Creating the test project</span></span>

<span data-ttu-id="d4376-122">Ardından, oluşturma *PrimeService.Tests* dizin.</span><span class="sxs-lookup"><span data-stu-id="d4376-122">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="d4376-123">Ana hat aşağıdaki dizin yapısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="d4376-123">The following outline shows the directory structure:</span></span>

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

<span data-ttu-id="d4376-124">Olun *PrimeService.Tests* dizini geçerli dizin ve aşağıdaki komutu kullanarak yeni bir proje oluşturun:</span><span class="sxs-lookup"><span data-stu-id="d4376-124">Make the *PrimeService.Tests* directory the current directory and create a new project using the following command:</span></span>

```console
dotnet new nunit -lang VB
```

<span data-ttu-id="d4376-125">[Yeni dotnet](../tools/dotnet-new.md) komut NUnit test kitaplık olarak kullanan bir test projesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d4376-125">The [dotnet new](../tools/dotnet-new.md) command creates a test project that uses NUnit as the test library.</span></span> <span data-ttu-id="d4376-126">Test Çalıştırıcısı'nda oluşturulan şablon yapılandırır *PrimeServiceTests.vbproj* dosyası:</span><span class="sxs-lookup"><span data-stu-id="d4376-126">The generated template configures the test runner in the *PrimeServiceTests.vbproj* file:</span></span>

[!code-xml[Packages](~/samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj#Packages)]

<span data-ttu-id="d4376-127">Test projesi oluşturma ve birim testlerini çalıştırmak için diğer paketleri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d4376-127">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="d4376-128">`dotnet new` Önceki adımda NUnit ve NUnit test bağdaştırıcısı eklendi.</span><span class="sxs-lookup"><span data-stu-id="d4376-128">`dotnet new` in the previous step added NUnit and the NUnit test adapter.</span></span> <span data-ttu-id="d4376-129">Şimdi ekleyin `PrimeService` sınıf kitaplığı projesine başka bir bağımlılık olarak.</span><span class="sxs-lookup"><span data-stu-id="d4376-129">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="d4376-130">Kullanım [ `dotnet add reference` ](../tools/dotnet-add-reference.md) komutu:</span><span class="sxs-lookup"><span data-stu-id="d4376-130">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```console
dotnet add reference ../PrimeService/PrimeService.vbproj
```

<span data-ttu-id="d4376-131">Dosyanın tamamını görebilirsiniz [örnekleri depomuzdan](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) GitHub üzerinde.</span><span class="sxs-lookup"><span data-stu-id="d4376-131">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span></span>

<span data-ttu-id="d4376-132">Aşağıdaki nihai çözüm Düzen vardır:</span><span class="sxs-lookup"><span data-stu-id="d4376-132">You have the following final solution layout:</span></span>

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeService.Tests.vbproj
```

<span data-ttu-id="d4376-133">Aşağıdaki komutu yürütün *birim testi vb nunit* dizini:</span><span class="sxs-lookup"><span data-stu-id="d4376-133">Execute the following command in the *unit-testing-vb-nunit* directory:</span></span>

```console
dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="d4376-134">İlk testi oluşturma</span><span class="sxs-lookup"><span data-stu-id="d4376-134">Creating the first test</span></span>

<span data-ttu-id="d4376-135">Bir yazma, test başarısız kolaylaştırır geçişi, sonra işlemi yineleyin.</span><span class="sxs-lookup"><span data-stu-id="d4376-135">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="d4376-136">İçinde *PrimeService.Tests* dizini yeniden adlandırma *UnitTest1.vb* dosyasını *PrimeService_IsPrimeShould.VB* ve tüm içeriğini aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="d4376-136">In the *PrimeService.Tests* directory, rename the *UnitTest1.vb* file to *PrimeService_IsPrimeShould.VB* and replace its entire contents with the following code:</span></span>

```vb
Imports NUnit.Framework

Namespace PrimeService.Tests
    <TestFixture>
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <Test>
        Sub ReturnFalseGivenValueOf1()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

<span data-ttu-id="d4376-137">`<TestFixture>` Öznitelik, testleri içeren bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="d4376-137">The `<TestFixture>` attribute indicates a class that contains tests.</span></span> <span data-ttu-id="d4376-138">`<Test>` Özniteliği test Çalıştırıcısı tarafından yürütülen bir yöntemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="d4376-138">The `<Test>` attribute denotes a method that is run by the test runner.</span></span> <span data-ttu-id="d4376-139">Gelen *birim testi vb nunit*, yürütme [ `dotnet test` ](../tools/dotnet-test.md) testler ve sınıf kitaplığı oluşturun ve ardından testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d4376-139">From the *unit-testing-vb-nunit*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="d4376-140">NUnit test Çalıştırıcısı, testlerinizi çalıştırmak için programın giriş noktası içerir.</span><span class="sxs-lookup"><span data-stu-id="d4376-140">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="d4376-141">`dotnet test` oluşturduğunuz birim test projesi kullanarak test Çalıştırıcısı'nı başlatır.</span><span class="sxs-lookup"><span data-stu-id="d4376-141">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="d4376-142">Test başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="d4376-142">Your test fails.</span></span> <span data-ttu-id="d4376-143">Uygulama henüz oluşturmadınız.</span><span class="sxs-lookup"><span data-stu-id="d4376-143">You haven't created the implementation yet.</span></span> <span data-ttu-id="d4376-144">En basit kod yazarak bu testin geçmesini `PrimeService` çalışır sınıfı:</span><span class="sxs-lookup"><span data-stu-id="d4376-144">Make this test by writing the simplest code in the `PrimeService` class that works:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first")
End Function
```

<span data-ttu-id="d4376-145">İçinde *birim testi vb nunit* çalışması dizini `dotnet test` yeniden.</span><span class="sxs-lookup"><span data-stu-id="d4376-145">In the *unit-testing-vb-nunit* directory, run `dotnet test` again.</span></span> <span data-ttu-id="d4376-146">`dotnet test` Komut çalıştıran bir derleme için `PrimeService` proje ve ardından `PrimeService.Tests` proje.</span><span class="sxs-lookup"><span data-stu-id="d4376-146">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="d4376-147">Her iki proje oluşturduktan sonra bu tek bir test çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="d4376-147">After building both projects, it runs this single test.</span></span> <span data-ttu-id="d4376-148">Bu geçirir.</span><span class="sxs-lookup"><span data-stu-id="d4376-148">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="d4376-149">Daha fazla özellik ekleme</span><span class="sxs-lookup"><span data-stu-id="d4376-149">Adding more features</span></span>

<span data-ttu-id="d4376-150">Bir test geçirmek yaptığınız, daha fazla yazmak için zaman var.</span><span class="sxs-lookup"><span data-stu-id="d4376-150">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="d4376-151">Birkaç basit durumlardaysa asal sayıları için vardır: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="d4376-151">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="d4376-152">Bu gibi durumlarda, yeni testleriyle olarak ekleyebilirsiniz `<Test>` özniteliği ancak hızla olur yorucu bir süreç.</span><span class="sxs-lookup"><span data-stu-id="d4376-152">You could add those cases as new tests with the `<Test>` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="d4376-153">Benzer testleri paketi yazmanızı sağlayan diğer xUnit öznitelikleri vardır.</span><span class="sxs-lookup"><span data-stu-id="d4376-153">There are other xUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="d4376-154">A `<TestCase>` öznitelik aynı kod yürütün, ancak farklı giriş bağımsız değişkenleri olan testleri paketi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d4376-154">A `<TestCase>` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="d4376-155">Kullanabileceğiniz `<TestCase>` bu girişleri değerlerini belirtmek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="d4376-155">You can use the `<TestCase>` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="d4376-156">Yeni testler oluşturmak yerine, asal numarası en düşük olan değerlerden küçüktür iki test bir test dizisi oluşturmak için bu iki öznitelikler uygulanır:</span><span class="sxs-lookup"><span data-stu-id="d4376-156">Instead of creating new tests, apply these two attributes to create a series of tests that test several values less than two, which is the lowest prime number:</span></span>

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

<span data-ttu-id="d4376-157">Çalıştırma `dotnet test`, ve bunlardan ikisi başarısız test eder.</span><span class="sxs-lookup"><span data-stu-id="d4376-157">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="d4376-158">Tüm testleri geçer hale getirmek için değiştirme `if` başındaki yan tümcesi `Main` yönteminde *PrimeServices.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="d4376-158">To make all of the tests pass, change the `if` clause at the beginning of the `Main` method in the *PrimeServices.cs* file:</span></span>

```vb
if candidate < 2
```

<span data-ttu-id="d4376-159">Ana Kitaplığı'nda daha fazla test, daha fazla Teoriler ve daha fazla kod ekleyerek yinelemek devam edin.</span><span class="sxs-lookup"><span data-stu-id="d4376-159">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="d4376-160">Sahip olduğunuz [testlerinin tamamlanmış bir sürümünü](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) ve [Kitaplığı'nın tam bir uygulamaya](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb).</span><span class="sxs-lookup"><span data-stu-id="d4376-160">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="d4376-161">Küçük bir kitaplık ve bu kitaplık için birim testleri bir dizi oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="d4376-161">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="d4376-162">Böylece yeni paketler ekleme çözüm yapılandırılmış ve testleri normal iş akışı bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="d4376-162">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="d4376-163">Zaman ve çaba çözme hedeflerinden biri, uygulama üzerinde en yoğun.</span><span class="sxs-lookup"><span data-stu-id="d4376-163">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
