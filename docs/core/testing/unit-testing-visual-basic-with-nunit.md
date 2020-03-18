---
title: Unit test Visual Basic in .NET Core,dotnet testi ve NUnit ile
description: Unit'i kullanarak örnek bir Visual Basic çözümü oluşturma etkileşimli bir deneyim le .NET Core'daki birim test kavramlarını öğrenin.
author: rprouse
ms.date: 10/04/2018
ms.openlocfilehash: a33447457344b241b4c2376d777b0deb7f556874
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240928"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-nunit"></a><span data-ttu-id="7288f-103">Unit test Visual Basic .NET Core kitaplıkları dotnet testi ve NUnit kullanarak</span><span class="sxs-lookup"><span data-stu-id="7288f-103">Unit testing Visual Basic .NET Core libraries using dotnet test and NUnit</span></span>

<span data-ttu-id="7288f-104">Bu öğretici, birim test kavramlarını öğrenmek için adım adım örnek bir çözüm oluşturma etkileşimli bir deneyim sunar.</span><span class="sxs-lookup"><span data-stu-id="7288f-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="7288f-105">Önceden oluşturulmuş bir çözüm kullanarak öğreticiyi izlemeyi tercih ederseniz, başlamadan önce [örnek kodu görüntüleyin veya indirin.](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-nunit/)</span><span class="sxs-lookup"><span data-stu-id="7288f-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-nunit/) before you begin.</span></span> <span data-ttu-id="7288f-106">İndirme talimatları için [Örnekler ve Öğreticiler'e](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)bakın.</span><span class="sxs-lookup"><span data-stu-id="7288f-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="prerequisites"></a><span data-ttu-id="7288f-107">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="7288f-107">Prerequisites</span></span>

- <span data-ttu-id="7288f-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) veya sonraki sürümler.</span><span class="sxs-lookup"><span data-stu-id="7288f-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later versions.</span></span>
- <span data-ttu-id="7288f-109">Tercih ettiğiniz bir metin veya kod düzenleyicisi.</span><span class="sxs-lookup"><span data-stu-id="7288f-109">A text editor or code editor of your choice.</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="7288f-110">Kaynak proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="7288f-110">Creating the source project</span></span>

<span data-ttu-id="7288f-111">Bir kabuk penceresi açın.</span><span class="sxs-lookup"><span data-stu-id="7288f-111">Open a shell window.</span></span> <span data-ttu-id="7288f-112">Çözümü tutmak için *birim-test-vb-nunit* adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7288f-112">Create a directory called *unit-testing-vb-nunit* to hold the solution.</span></span> <span data-ttu-id="7288f-113">Bu yeni dizinin içinde, sınıf kitaplığı ve test projesi için yeni bir çözüm dosyası oluşturmak için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="7288f-113">Inside this new directory, run the following command to create a new solution file for the class library and the test project:</span></span>

```dotnetcli
dotnet new sln
```

<span data-ttu-id="7288f-114">Ardından, bir *PrimeService* dizini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7288f-114">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="7288f-115">Aşağıdaki anahat şimdiye kadar dosya yapısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="7288f-115">The following outline shows the file structure so far:</span></span>

```console
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
```

<span data-ttu-id="7288f-116">*PrimeService'i* geçerli dizini yapın ve kaynak projeyi oluşturmak için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="7288f-116">Make *PrimeService* the current directory and run the following command to create the source project:</span></span>

```dotnetcli
dotnet new classlib -lang VB
```

<span data-ttu-id="7288f-117">*Class1.VB'yi* *PrimeService.VB*olarak yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="7288f-117">Rename *Class1.VB* to *PrimeService.VB*.</span></span> <span data-ttu-id="7288f-118">`PrimeService` Sınıfın başarısız bir uygulamasını oluşturursunuz:</span><span class="sxs-lookup"><span data-stu-id="7288f-118">You create a failing implementation of the `PrimeService` class:</span></span>

```vb
Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first.")
        End Function
    End Class
End Namespace
```

<span data-ttu-id="7288f-119">Dizin geri *birim-test-vb-using-mstest* dizini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="7288f-119">Change the directory back to the *unit-testing-vb-using-mstest* directory.</span></span> <span data-ttu-id="7288f-120">Sınıf kitaplığı projesini çözüme eklemek için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="7288f-120">Run the following command to add the class library project to the solution:</span></span>

```dotnetcli
dotnet sln add .\PrimeService\PrimeService.vbproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="7288f-121">Test projesini oluşturma</span><span class="sxs-lookup"><span data-stu-id="7288f-121">Creating the test project</span></span>

<span data-ttu-id="7288f-122">Ardından, *PrimeService.Tests* dizinini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7288f-122">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="7288f-123">Aşağıdaki anahat dizin yapısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="7288f-123">The following outline shows the directory structure:</span></span>

```console
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

<span data-ttu-id="7288f-124">*PrimeService.Tests* dizinini geçerli dizini oluşturun ve aşağıdaki komutu kullanarak yeni bir proje oluşturun:</span><span class="sxs-lookup"><span data-stu-id="7288f-124">Make the *PrimeService.Tests* directory the current directory and create a new project using the following command:</span></span>

```dotnetcli
dotnet new nunit -lang VB
```

<span data-ttu-id="7288f-125">[Dotnet yeni](../tools/dotnet-new.md) komutu, test kitaplığı olarak NUnit kullanan bir test projesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7288f-125">The [dotnet new](../tools/dotnet-new.md) command creates a test project that uses NUnit as the test library.</span></span> <span data-ttu-id="7288f-126">Oluşturulan *şablon, PrimeServiceTests.vbproj* dosyasındaki test koşucusu yla yapılandırır:</span><span class="sxs-lookup"><span data-stu-id="7288f-126">The generated template configures the test runner in the *PrimeServiceTests.vbproj* file:</span></span>

[!code-xml[Packages](~/samples/snippets/core/testing/unit-testing-vb-nunit/vb/PrimeService.Tests/PrimeService.Tests.vbproj#Packages)]

<span data-ttu-id="7288f-127">Test projesi, birim testleri oluşturmak ve çalıştırmak için diğer paketler gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7288f-127">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="7288f-128">`dotnet new`önceki adımda NUnit ve NUnit test bağdaştırıcısı eklendi.</span><span class="sxs-lookup"><span data-stu-id="7288f-128">`dotnet new` in the previous step added NUnit and the NUnit test adapter.</span></span> <span data-ttu-id="7288f-129">Şimdi, `PrimeService` sınıf kitaplığını projeye başka bir bağımlılık olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7288f-129">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="7288f-130">Komutu [`dotnet add reference`](../tools/dotnet-add-reference.md) kullanın:</span><span class="sxs-lookup"><span data-stu-id="7288f-130">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.vbproj
```

<span data-ttu-id="7288f-131">Tüm dosyayı GitHub'daki [örnek deposunda](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7288f-131">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span></span>

<span data-ttu-id="7288f-132">Aşağıdaki nihai çözüm düzenine sahipsiniz:</span><span class="sxs-lookup"><span data-stu-id="7288f-132">You have the following final solution layout:</span></span>

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

<span data-ttu-id="7288f-133">*Birim-test-vb-nunit* dizininde aşağıdaki komutu uygulayın:</span><span class="sxs-lookup"><span data-stu-id="7288f-133">Execute the following command in the *unit-testing-vb-nunit* directory:</span></span>

```dotnetcli
dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="7288f-134">İlk testi oluşturma</span><span class="sxs-lookup"><span data-stu-id="7288f-134">Creating the first test</span></span>

<span data-ttu-id="7288f-135">Başarısız bir test yazarsın, geçer ve işlemi tekrarlarsın.</span><span class="sxs-lookup"><span data-stu-id="7288f-135">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="7288f-136">*PrimeService.Tests* dizininde *UnitTest1.vb* dosyasını *PrimeService_IsPrimeShould.VB* olarak yeniden adlandırın ve tüm içeriğini aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="7288f-136">In the *PrimeService.Tests* directory, rename the *UnitTest1.vb* file to *PrimeService_IsPrimeShould.VB* and replace its entire contents with the following code:</span></span>

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

<span data-ttu-id="7288f-137">Öznitelik, `<TestFixture>` testleri içeren bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="7288f-137">The `<TestFixture>` attribute indicates a class that contains tests.</span></span> <span data-ttu-id="7288f-138">Öznitelik, `<Test>` test koşucusu tarafından çalıştırılabilen bir yöntemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="7288f-138">The `<Test>` attribute denotes a method that is run by the test runner.</span></span> <span data-ttu-id="7288f-139">*Birim-test-vb-nunit*itibaren, [`dotnet test`](../tools/dotnet-test.md) testleri ve sınıf kitaplığı oluşturmak ve daha sonra testleri çalıştırmak için çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7288f-139">From the *unit-testing-vb-nunit*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="7288f-140">NUnit test koşucusu, testlerinizi çalıştırmak için program giriş noktasını içerir.</span><span class="sxs-lookup"><span data-stu-id="7288f-140">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="7288f-141">`dotnet test`oluşturduğunuz birim test projesini kullanarak test koşucusu başlatın.</span><span class="sxs-lookup"><span data-stu-id="7288f-141">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="7288f-142">Sınavın başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="7288f-142">Your test fails.</span></span> <span data-ttu-id="7288f-143">Uygulamayı henüz oluşturmadın.</span><span class="sxs-lookup"><span data-stu-id="7288f-143">You haven't created the implementation yet.</span></span> <span data-ttu-id="7288f-144">Bu testin çalışmasını sağlayan `PrimeService` sınıftaki en basit kodu yazarak geçmesini sağla:</span><span class="sxs-lookup"><span data-stu-id="7288f-144">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first.")
End Function
```

<span data-ttu-id="7288f-145">*Birim-test-vb-nunit* dizininde, tekrar `dotnet test` çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7288f-145">In the *unit-testing-vb-nunit* directory, run `dotnet test` again.</span></span> <span data-ttu-id="7288f-146">Komut, `dotnet test` proje ve ardından `PrimeService.Tests` proje için bir yapı çalışır. `PrimeService`</span><span class="sxs-lookup"><span data-stu-id="7288f-146">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="7288f-147">Her iki projeyi de yaptıktan sonra, bu tek testi çalıştırAr.</span><span class="sxs-lookup"><span data-stu-id="7288f-147">After building both projects, it runs this single test.</span></span> <span data-ttu-id="7288f-148">Geçiyor.</span><span class="sxs-lookup"><span data-stu-id="7288f-148">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="7288f-149">Daha fazla özellik ekleme</span><span class="sxs-lookup"><span data-stu-id="7288f-149">Adding more features</span></span>

<span data-ttu-id="7288f-150">Artık bir test sınavını geçtiğine göre, daha fazla yazma nın zamanı.</span><span class="sxs-lookup"><span data-stu-id="7288f-150">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="7288f-151">Asal sayılar için birkaç basit durum daha vardır: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="7288f-151">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="7288f-152">Bu durumları öznitelik ile `<Test>` yeni testler olarak ekleyebilirsiniz, ancak bu hızla sıkıcı olur.</span><span class="sxs-lookup"><span data-stu-id="7288f-152">You could add those cases as new tests with the `<Test>` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="7288f-153">Benzer testler paketi yazmanızı sağlayan başka xUnit öznitelikleri de vardır.</span><span class="sxs-lookup"><span data-stu-id="7288f-153">There are other xUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="7288f-154">Öznitelik, `<TestCase>` aynı kodu çalıştıran ancak farklı giriş bağımsız değişkenleri olan bir test paketini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7288f-154">A `<TestCase>` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="7288f-155">Bu girişler `<TestCase>` için değerleri belirtmek için özniteliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7288f-155">You can use the `<TestCase>` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="7288f-156">Yeni testler oluşturmak yerine, bu iki öznitelikleri, ikiden küçük değerleri test eden bir dizi test oluşturmak için uygulayın, bu da en düşük asal sayıdır:</span><span class="sxs-lookup"><span data-stu-id="7288f-156">Instead of creating new tests, apply these two attributes to create a series of tests that test several values less than two, which is the lowest prime number:</span></span>

[!code-vb[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-vb-nunit/vb/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

<span data-ttu-id="7288f-157">Çalıştır `dotnet test`Ve bu testlerin iki başarısız.</span><span class="sxs-lookup"><span data-stu-id="7288f-157">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="7288f-158">Tüm testlerin geçmesi için, `if` `Main` *PrimeServices.cs* dosyasındaki yöntemin başındaki tümceyi değiştirin:</span><span class="sxs-lookup"><span data-stu-id="7288f-158">To make all of the tests pass, change the `if` clause at the beginning of the `Main` method in the *PrimeServices.cs* file:</span></span>

```vb
if candidate < 2
```

<span data-ttu-id="7288f-159">Ana kitaplığa daha fazla test, daha fazla teori ve daha fazla kod ekleyerek yinelemeye devam edin.</span><span class="sxs-lookup"><span data-stu-id="7288f-159">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="7288f-160">[Testlerin tamamlanmış sürümüne](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) ve [kitaplığın tam uygulamasına](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb)sahipsiniz.</span><span class="sxs-lookup"><span data-stu-id="7288f-160">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="7288f-161">O kitaplık için küçük bir kitaplık ve bir dizi birim testi inşa ettin.</span><span class="sxs-lookup"><span data-stu-id="7288f-161">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="7288f-162">Yeni paketler ve testler eklemek normal iş akışının bir parçası olacak şekilde çözümü yapılandırdınız.</span><span class="sxs-lookup"><span data-stu-id="7288f-162">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="7288f-163">Zamanınızın ve çabanızın çoğunu uygulamanın hedeflerini çözmeye yoğunlaşmışsınız.</span><span class="sxs-lookup"><span data-stu-id="7288f-163">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
