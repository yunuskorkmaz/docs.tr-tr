---
title: DotNet test ve NUnit ile .NET Core 'da birim testi Visual Basic
description: .NET Core 'daki birim testi kavramlarını, NUnit kullanarak örnek Visual Basic çözüm oluşturma adlı etkileşimli bir deneyim aracılığıyla öğrenin.
author: rprouse
ms.date: 10/04/2018
ms.openlocfilehash: 4b807463d29f271d1a707b6254b7b5e66f745319
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656416"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-nunit"></a><span data-ttu-id="5813b-103">DotNet test ve NUnit kullanarak .NET Core kitaplıkları Visual Basic birim testi</span><span class="sxs-lookup"><span data-stu-id="5813b-103">Unit testing Visual Basic .NET Core libraries using dotnet test and NUnit</span></span>

<span data-ttu-id="5813b-104">Bu öğreticide, birim testi kavramlarını öğrenmek için bir örnek çözüm oluşturma adım adım yönergeler sunarak etkileşimli bir deneyim sağlanır.</span><span class="sxs-lookup"><span data-stu-id="5813b-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="5813b-105">Önceden oluşturulmuş bir çözüm kullanarak öğreticiyi izlemeyi tercih ediyorsanız, başlamadan önce [örnek kodu görüntüleyin veya indirin](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-nunit/) .</span><span class="sxs-lookup"><span data-stu-id="5813b-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-nunit/) before you begin.</span></span> <span data-ttu-id="5813b-106">İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#view-and-download-samples).</span><span class="sxs-lookup"><span data-stu-id="5813b-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#view-and-download-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="prerequisites"></a><span data-ttu-id="5813b-107">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="5813b-107">Prerequisites</span></span>

- <span data-ttu-id="5813b-108">[.NET Core 2,1 SDK](https://dotnet.microsoft.com/download) veya sonraki sürümleri.</span><span class="sxs-lookup"><span data-stu-id="5813b-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later versions.</span></span>
- <span data-ttu-id="5813b-109">Tercih ettiğiniz bir metin veya kod düzenleyicisi.</span><span class="sxs-lookup"><span data-stu-id="5813b-109">A text editor or code editor of your choice.</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="5813b-110">Kaynak proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="5813b-110">Creating the source project</span></span>

<span data-ttu-id="5813b-111">Bir kabuk penceresi açın.</span><span class="sxs-lookup"><span data-stu-id="5813b-111">Open a shell window.</span></span> <span data-ttu-id="5813b-112">Çözümü tutmak için *birim-test-vb-NUnit* adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5813b-112">Create a directory called *unit-testing-vb-nunit* to hold the solution.</span></span> <span data-ttu-id="5813b-113">Bu yeni dizin içinde, sınıf kitaplığı ve test projesi için yeni bir çözüm dosyası oluşturmak üzere aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="5813b-113">Inside this new directory, run the following command to create a new solution file for the class library and the test project:</span></span>

```dotnetcli
dotnet new sln
```

<span data-ttu-id="5813b-114">Ardından, bir *Primeservice* dizini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5813b-114">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="5813b-115">Aşağıdaki ana hat şu ana kadar dosya yapısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="5813b-115">The following outline shows the file structure so far:</span></span>

```console
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
```

<span data-ttu-id="5813b-116">Kaynak projeyi oluşturmak için *Primeservice* 'i geçerli dizin yapın ve şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="5813b-116">Make *PrimeService* the current directory and run the following command to create the source project:</span></span>

```dotnetcli
dotnet new classlib -lang VB
```

<span data-ttu-id="5813b-117">*Class1. vb* ' i *primeservice. vb*olarak yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="5813b-117">Rename *Class1.VB* to *PrimeService.VB*.</span></span> <span data-ttu-id="5813b-118">Sınıfın başarısız bir uygulamasını oluşturursunuz `PrimeService` :</span><span class="sxs-lookup"><span data-stu-id="5813b-118">You create a failing implementation of the `PrimeService` class:</span></span>

```vb
Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first.")
        End Function
    End Class
End Namespace
```

<span data-ttu-id="5813b-119">Dizini *birim-test-vb-using-MSTest* dizinine geri çevirin.</span><span class="sxs-lookup"><span data-stu-id="5813b-119">Change the directory back to the *unit-testing-vb-using-mstest* directory.</span></span> <span data-ttu-id="5813b-120">Çözüme Sınıf Kitaplığı projesini eklemek için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="5813b-120">Run the following command to add the class library project to the solution:</span></span>

```dotnetcli
dotnet sln add .\PrimeService\PrimeService.vbproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="5813b-121">Test projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="5813b-121">Creating the test project</span></span>

<span data-ttu-id="5813b-122">Ardından, *Primeservice. Tests* dizinini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5813b-122">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="5813b-123">Aşağıdaki ana hat dizin yapısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="5813b-123">The following outline shows the directory structure:</span></span>

```console
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

<span data-ttu-id="5813b-124">*Primeservice. test* dizinini geçerli dizini yapın ve aşağıdaki komutu kullanarak yeni bir proje oluşturun:</span><span class="sxs-lookup"><span data-stu-id="5813b-124">Make the *PrimeService.Tests* directory the current directory and create a new project using the following command:</span></span>

```dotnetcli
dotnet new nunit -lang VB
```

<span data-ttu-id="5813b-125">[DotNet New](../tools/dotnet-new.md) komutu, test kitaplığı olarak NUnit kullanan bir test projesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5813b-125">The [dotnet new](../tools/dotnet-new.md) command creates a test project that uses NUnit as the test library.</span></span> <span data-ttu-id="5813b-126">Oluşturulan şablon, *Primeservicetests. vbproj* dosyasında Test Çalıştırıcısı 'nı yapılandırır:</span><span class="sxs-lookup"><span data-stu-id="5813b-126">The generated template configures the test runner in the *PrimeServiceTests.vbproj* file:</span></span>

[!code-xml[Packages](~/samples/snippets/core/testing/unit-testing-vb-nunit/vb/PrimeService.Tests/PrimeService.Tests.vbproj#Packages)]

<span data-ttu-id="5813b-127">Test projesi, birim testlerini oluşturmak ve çalıştırmak için diğer paketlerin kullanılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5813b-127">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="5813b-128">`dotnet new` önceki adımda NUnit ve NUnit test bağdaştırıcısı eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="5813b-128">`dotnet new` in the previous step added NUnit and the NUnit test adapter.</span></span> <span data-ttu-id="5813b-129">Şimdi, `PrimeService` sınıf kitaplığını projeye başka bir bağımlılık olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5813b-129">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="5813b-130">Şu [`dotnet add reference`](../tools/dotnet-add-reference.md) komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="5813b-130">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.vbproj
```

<span data-ttu-id="5813b-131">GitHub 'daki [örnekler deposunda](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) dosyanın tamamını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5813b-131">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span></span>

<span data-ttu-id="5813b-132">Aşağıdaki son çözüm düzenine sahipsiniz:</span><span class="sxs-lookup"><span data-stu-id="5813b-132">You have the following final solution layout:</span></span>

```console
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeService.Tests.vbproj
```

<span data-ttu-id="5813b-133">*Birim-test-vb-NUnit* dizininde aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="5813b-133">Execute the following command in the *unit-testing-vb-nunit* directory:</span></span>

```dotnetcli
dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="5813b-134">İlk test oluşturma</span><span class="sxs-lookup"><span data-stu-id="5813b-134">Creating the first test</span></span>

<span data-ttu-id="5813b-135">Başarısız bir test yazdığınızda, geçişi yapıp işlemi tekrarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5813b-135">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="5813b-136">*Primeservice. Tests* dizininde, *UnitTest1. vb* dosyasını *PrimeService_IsPrimeShould. vb* olarak yeniden adlandırın ve tüm içeriğini aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="5813b-136">In the *PrimeService.Tests* directory, rename the *UnitTest1.vb* file to *PrimeService_IsPrimeShould.VB* and replace its entire contents with the following code:</span></span>

```vb
Imports NUnit.Framework

Namespace PrimeService.Tests
    <TestFixture>
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <Test>
        Sub IsPrime_InputIs1_ReturnFalse()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

<span data-ttu-id="5813b-137">`<TestFixture>`Öznitelik, testleri içeren bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="5813b-137">The `<TestFixture>` attribute indicates a class that contains tests.</span></span> <span data-ttu-id="5813b-138">`<Test>`Öznitelik, Test Çalıştırıcısı tarafından çalıştırılan bir yöntemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="5813b-138">The `<Test>` attribute denotes a method that is run by the test runner.</span></span> <span data-ttu-id="5813b-139">*Birim-test-vb-NUnit*, [`dotnet test`](../tools/dotnet-test.md) Testleri ve sınıf kitaplığını oluşturmak için yürütün ve ardından testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5813b-139">From the *unit-testing-vb-nunit*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="5813b-140">NUnit Test Çalıştırıcısı, testlerinizi çalıştırmak için program giriş noktasını içerir.</span><span class="sxs-lookup"><span data-stu-id="5813b-140">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="5813b-141">`dotnet test` oluşturduğunuz birim test projesini kullanarak Test Çalıştırıcısı başlatır.</span><span class="sxs-lookup"><span data-stu-id="5813b-141">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="5813b-142">Testiniz başarısız oluyor.</span><span class="sxs-lookup"><span data-stu-id="5813b-142">Your test fails.</span></span> <span data-ttu-id="5813b-143">Uygulamayı henüz oluşturmadınız.</span><span class="sxs-lookup"><span data-stu-id="5813b-143">You haven't created the implementation yet.</span></span> <span data-ttu-id="5813b-144">Bu test geçişini, çalıştıran sınıfa en basit kodu yazarak yapın `PrimeService` :</span><span class="sxs-lookup"><span data-stu-id="5813b-144">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first.")
End Function
```

<span data-ttu-id="5813b-145">*Birim-test-vb-NUnit* dizininde `dotnet test` yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5813b-145">In the *unit-testing-vb-nunit* directory, run `dotnet test` again.</span></span> <span data-ttu-id="5813b-146">`dotnet test`Komutu, proje için bir yapı `PrimeService` ve ardından proje için çalışır `PrimeService.Tests` .</span><span class="sxs-lookup"><span data-stu-id="5813b-146">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="5813b-147">Her iki proje de oluşturulduktan sonra bu tek testi çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="5813b-147">After building both projects, it runs this single test.</span></span> <span data-ttu-id="5813b-148">Geçirir.</span><span class="sxs-lookup"><span data-stu-id="5813b-148">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="5813b-149">Daha fazla özellik ekleme</span><span class="sxs-lookup"><span data-stu-id="5813b-149">Adding more features</span></span>

<span data-ttu-id="5813b-150">Artık bir test geçişi yapmış olduğunuza göre daha fazla yazma zamanı vardır.</span><span class="sxs-lookup"><span data-stu-id="5813b-150">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="5813b-151">Asal sayıların diğer birkaç basit durumu vardır: 0,-1.</span><span class="sxs-lookup"><span data-stu-id="5813b-151">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="5813b-152">Bu servis taleplerini özniteliğiyle yeni testler olarak ekleyebilirsiniz `<Test>` , ancak bu, hızlı bir şekilde sıkıcı hale gelir.</span><span class="sxs-lookup"><span data-stu-id="5813b-152">You could add those cases as new tests with the `<Test>` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="5813b-153">Benzer testlerin bir paketini yazmanızı sağlayan başka xUnit öznitelikleri vardır.</span><span class="sxs-lookup"><span data-stu-id="5813b-153">There are other xUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="5813b-154">`<TestCase>`Öznitelik, aynı kodu çalıştıran ancak farklı giriş bağımsız değişkenlerine sahip olan bir test paketini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5813b-154">A `<TestCase>` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="5813b-155">`<TestCase>`Bu girişlerin değerlerini belirtmek için özniteliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5813b-155">You can use the `<TestCase>` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="5813b-156">Yeni testler oluşturmak yerine, bu iki özniteliği, en düşük asal sayı olan iki değerden küçük olan birkaç değeri test eden bir dizi testi oluşturacak şekilde uygulayın:</span><span class="sxs-lookup"><span data-stu-id="5813b-156">Instead of creating new tests, apply these two attributes to create a series of tests that test several values less than two, which is the lowest prime number:</span></span>

[!code-vb[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-vb-nunit/vb/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

<span data-ttu-id="5813b-157">Çalıştır `dotnet test` ve bu testlerin ikisi de başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="5813b-157">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="5813b-158">Tüm testlerin geçişini yapmak için `if` `Main` *PrimeServices.cs* dosyasındaki yönteminin başındaki yan tümceyi değiştirin:</span><span class="sxs-lookup"><span data-stu-id="5813b-158">To make all of the tests pass, change the `if` clause at the beginning of the `Main` method in the *PrimeServices.cs* file:</span></span>

```vb
if candidate < 2
```

<span data-ttu-id="5813b-159">Ana kitaplıkta daha fazla test, daha fazla yer ve daha fazla kod ekleyerek yinelemek için devam edin.</span><span class="sxs-lookup"><span data-stu-id="5813b-159">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="5813b-160">[Testlerin tamamlanmış sürümüne](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) ve [kitaplığın tüm uygulamasına](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb)sahipsiniz.</span><span class="sxs-lookup"><span data-stu-id="5813b-160">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="5813b-161">Bu kitaplık için küçük bir kitaplık ve birim testleri kümesi oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="5813b-161">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="5813b-162">Çözümü, yeni paket ve test eklemek normal iş akışının bir parçası olacak şekilde öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="5813b-162">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="5813b-163">Uygulamanın hedeflerini çözme konusunda zaman ve çaba harcamanızı en iyi şekilde gördünüz.</span><span class="sxs-lookup"><span data-stu-id="5813b-163">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
