---
title: "Visual Basic .NET çekirdek dotnet test ve NUnit kullanarak test birim"
description: "Adım adım örnek Visual Basic çözüm oluşturma etkileşimli bir deneyim aracılığıyla .NET Core olarak birim testi kavramları hakkında bilgi NUnit kullanarak."
author: rprouse
ms.date: 12/01/2017
ms.topic: article
dev_langs: vb
ms.prod: .net-core
ms.openlocfilehash: 2166da36fe9d0297f03e7c38249135d281b9a5d6
ms.sourcegitcommit: 401c4427a3ec0d1263543033b3084039278509dc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/06/2017
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-nunit"></a><span data-ttu-id="3370d-103">Birim testi dotnet test ve NUnit kullanarak Visual Basic .NET Core kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="3370d-103">Unit testing Visual Basic .NET Core libraries using dotnet test and NUnit</span></span>

<span data-ttu-id="3370d-104">Bu öğretici birim testi kavramlarını öğrenmek için adım adım örnek çözüm oluşturma etkileşimli bir deneyim gösterir.</span><span class="sxs-lookup"><span data-stu-id="3370d-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="3370d-105">Önceden oluşturulmuş bir çözümü kullanarak öğreticiyi izleyin tercih ediyorsanız [görüntülemek veya karşıdan örnek kod](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-vb-nunit/) başlamadan önce.</span><span class="sxs-lookup"><span data-stu-id="3370d-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-vb-nunit/) before you begin.</span></span> <span data-ttu-id="3370d-106">Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="3370d-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="3370d-107">Kaynak projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="3370d-107">Creating the source project</span></span>

<span data-ttu-id="3370d-108">Kabuk penceresini açın.</span><span class="sxs-lookup"><span data-stu-id="3370d-108">Open a shell window.</span></span> <span data-ttu-id="3370d-109">Adlı bir dizin oluşturun *birim testi vb nunit* çözümü tutmak için.</span><span class="sxs-lookup"><span data-stu-id="3370d-109">Create a directory called *unit-testing-vb-nunit* to hold the solution.</span></span> <span data-ttu-id="3370d-110">Bu yeni dizin içinde çalıştırmak [ `dotnet new sln` ](../tools/dotnet-new.md) yeni bir çözüm oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="3370d-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="3370d-111">Bu yöntem, sınıf kitaplığı ve birim testi projesi yönetmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="3370d-111">This practice makes it easier to manage both the class library and the unit test project.</span></span> <span data-ttu-id="3370d-112">Çözüm dizini içinde oluşturmak bir *PrimeService* dizini.</span><span class="sxs-lookup"><span data-stu-id="3370d-112">Inside the solution directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="3370d-113">Aşağıdaki dizin ve dosya yapısı bugüne kadarki vardır:</span><span class="sxs-lookup"><span data-stu-id="3370d-113">You have the following directory and file structure thus far:</span></span>

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
```

<span data-ttu-id="3370d-114">Olun *PrimeService* geçerli dizin ve çalışma [ `dotnet new classlib -lang VB` ](../tools/dotnet-new.md) kaynak projesi oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="3370d-114">Make *PrimeService* the current directory and run [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="3370d-115">Yeniden Adlandır *Class1.vb'ye* için *PrimeService.VB*.</span><span class="sxs-lookup"><span data-stu-id="3370d-115">Rename *Class1.VB* to *PrimeService.VB*.</span></span> <span data-ttu-id="3370d-116">Teste dayalı geliştirme (TDD) kullanmak için bir başarısız uygulaması oluşturun `PrimeService` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="3370d-116">To use test-driven development (TDD), you create a failing implementation of the `PrimeService` class:</span></span>

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

<span data-ttu-id="3370d-117">Dizin geri değişiklik *birim-test etme-vb-kullanma-stest* dizini.</span><span class="sxs-lookup"><span data-stu-id="3370d-117">Change the directory back to the *unit-testing-vb-using-stest* directory.</span></span> <span data-ttu-id="3370d-118">Çalıştırma [ `dotnet sln add .\PrimeService\PrimeService.vbproj` ](../tools/dotnet-sln.md) sınıf kitaplığı proje çözüme eklemek için.</span><span class="sxs-lookup"><span data-stu-id="3370d-118">Run [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="install-the-nunit-project-template"></a><span data-ttu-id="3370d-119">NUnit proje şablonu yükleyin</span><span class="sxs-lookup"><span data-stu-id="3370d-119">Install the NUnit project template</span></span>

<span data-ttu-id="3370d-120">NUnit test projesi şablonları bir test projesi oluşturmadan önce yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="3370d-120">The NUnit test project templates need to be installed before creating a test project.</span></span> <span data-ttu-id="3370d-121">Bu yalnızca bir kez yeni NUnit projeleri oluşturacağınız her geliştirici makinede yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3370d-121">This only needs to be done once on each developer machine where you'll create new NUnit projects.</span></span> <span data-ttu-id="3370d-122">Çalıştırma [ `dotnet new -i NUnit3.DotNetNew.Template` ](../tools/dotnet-new.md) NUnit şablonları yüklemek için.</span><span class="sxs-lookup"><span data-stu-id="3370d-122">Run [`dotnet new -i NUnit3.DotNetNew.Template`](../tools/dotnet-new.md) to install the NUnit templates.</span></span>

 ```
 dotnet new -i NUnit3.DotNetNew.Template
 ```

## <a name="creating-the-test-project"></a><span data-ttu-id="3370d-123">Test projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="3370d-123">Creating the test project</span></span>

<span data-ttu-id="3370d-124">Ardından, oluşturun *PrimeService.Tests* dizini.</span><span class="sxs-lookup"><span data-stu-id="3370d-124">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="3370d-125">Aşağıdaki anahat dizin yapısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="3370d-125">The following outline shows the directory structure:</span></span>

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

<span data-ttu-id="3370d-126">Olun *PrimeService.Tests* dizine geçerli ve kullanarak yeni bir proje oluşturun [ `dotnet new nunit -lang VB` ](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="3370d-126">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new nunit -lang VB`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="3370d-127">Bu komut NUnit test kitaplığını kullanan bir test projesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3370d-127">This command creates a test project that uses NUnit as the test library.</span></span> <span data-ttu-id="3370d-128">Test Çalıştırıcısı'nda oluşturulan şablon yapılandırır *PrimeServiceTests.vbproj*:</span><span class="sxs-lookup"><span data-stu-id="3370d-128">The generated template configures the test runner in the *PrimeServiceTests.vbproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

<span data-ttu-id="3370d-129">Test projesi oluşturmak ve birim testleri çalıştırmak için diğer paketleri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3370d-129">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="3370d-130">`dotnet new`Önceki adımda NUnit ve NUnit test bağdaştırıcısı eklendi.</span><span class="sxs-lookup"><span data-stu-id="3370d-130">`dotnet new` in the previous step added NUnit and the NUnit test adapter.</span></span> <span data-ttu-id="3370d-131">Şimdi, ekleyin `PrimeService` sınıf kitaplığı proje için başka bir bağımlılık olarak.</span><span class="sxs-lookup"><span data-stu-id="3370d-131">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="3370d-132">Kullanım [ `dotnet add reference` ](../tools/dotnet-add-reference.md) komutu:</span><span class="sxs-lookup"><span data-stu-id="3370d-132">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.vbproj
```

<span data-ttu-id="3370d-133">Tüm dosyasında görebilirsiniz [örnekleri deposu](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) github'da.</span><span class="sxs-lookup"><span data-stu-id="3370d-133">You can see the entire file in the [samples repository](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span></span>

<span data-ttu-id="3370d-134">Aşağıdaki nihai çözüm düzeni vardır:</span><span class="sxs-lookup"><span data-stu-id="3370d-134">You have the following final solution layout:</span></span>

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.vbproj
```

<span data-ttu-id="3370d-135">Yürütme [ `dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj` ](../tools/dotnet-sln.md) içinde *birim testi vb nunit* dizini.</span><span class="sxs-lookup"><span data-stu-id="3370d-135">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) in the *unit-testing-vb-nunit* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="3370d-136">İlk testi oluşturma</span><span class="sxs-lookup"><span data-stu-id="3370d-136">Creating the first test</span></span>

<span data-ttu-id="3370d-137">TDD yaklaşım geçirmek kolaylaştırarak ve süreci tekrarlayarak yazma bir başarısız test için çağırır.</span><span class="sxs-lookup"><span data-stu-id="3370d-137">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="3370d-138">Kaldırma *UnitTest1.vb* gelen *PrimeService.Tests* dizin ve adlı yeni bir Visual Basic dosyası oluşturma *PrimeService_IsPrimeShould.VB*.</span><span class="sxs-lookup"><span data-stu-id="3370d-138">Remove *UnitTest1.vb* from the *PrimeService.Tests* directory and create a new Visual Basic file named *PrimeService_IsPrimeShould.VB*.</span></span> <span data-ttu-id="3370d-139">Aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="3370d-139">Add the following code:</span></span>

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

<span data-ttu-id="3370d-140">`<TestFixture>` Öznitelik testleri içeren bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="3370d-140">The `<TestFixture>` attribute indicates a class that contains tests.</span></span> <span data-ttu-id="3370d-141">`<Test>` Özniteliği test Çalıştırıcısı tarafından çalıştırılan bir yöntemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="3370d-141">The `<Test>` attribute denotes a method that is run by the test runner.</span></span> <span data-ttu-id="3370d-142">Gelen *birim testi vb nunit*, yürütme [ `dotnet test` ](../tools/dotnet-test.md) testleri ve sınıf kitaplığı oluşturmak ve ardından testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3370d-142">From the *unit-testing-vb-nunit*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="3370d-143">NUnit test Çalıştırıcısı testleri çalıştırmak için program giriş noktası içerir.</span><span class="sxs-lookup"><span data-stu-id="3370d-143">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="3370d-144">`dotnet test`oluşturduğunuz birim testi projesi kullanarak test Çalıştırıcısı başlatır.</span><span class="sxs-lookup"><span data-stu-id="3370d-144">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="3370d-145">Testiniz başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="3370d-145">Your test fails.</span></span> <span data-ttu-id="3370d-146">Uygulama henüz oluşturmadınız.</span><span class="sxs-lookup"><span data-stu-id="3370d-146">You haven't created the implementation yet.</span></span> <span data-ttu-id="3370d-147">Bu test basit kod yazarken yapmasına `PrimeService` çalışır sınıfı:</span><span class="sxs-lookup"><span data-stu-id="3370d-147">Make this test by writing the simplest code in the `PrimeService` class that works:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first")
End Function
```

<span data-ttu-id="3370d-148">İçinde *birim testi vb nunit* çalışması dizini `dotnet test` yeniden.</span><span class="sxs-lookup"><span data-stu-id="3370d-148">In the *unit-testing-vb-nunit* directory, run `dotnet test` again.</span></span> <span data-ttu-id="3370d-149">`dotnet test` Komutu çalıştıran bir yapı `PrimeService` proje ve ardından `PrimeService.Tests` projesi.</span><span class="sxs-lookup"><span data-stu-id="3370d-149">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="3370d-150">Her iki proje oluşturduktan sonra bu tek bir test çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="3370d-150">After building both projects, it runs this single test.</span></span> <span data-ttu-id="3370d-151">Bunu geçirir.</span><span class="sxs-lookup"><span data-stu-id="3370d-151">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="3370d-152">Daha fazla özellik ekleme</span><span class="sxs-lookup"><span data-stu-id="3370d-152">Adding more features</span></span>

<span data-ttu-id="3370d-153">Bir test geçirmek yapmış olduğunuz, daha fazla yazma zamanı geldi.</span><span class="sxs-lookup"><span data-stu-id="3370d-153">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="3370d-154">Diğer basit bazı durumlar asal sayılar için vardır: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="3370d-154">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="3370d-155">Bu gibi durumlarda yeni testleriyle olarak ekleyebilirsiniz `<Test>` özniteliği, ancak, hızlı hale can sıkıcı.</span><span class="sxs-lookup"><span data-stu-id="3370d-155">You could add those cases as new tests with the `<Test>` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="3370d-156">Benzer testleri dizisi yazmak için etkinleştirmek diğer xUnit özniteliği vardır.</span><span class="sxs-lookup"><span data-stu-id="3370d-156">There are other xUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="3370d-157">A `<TestCase>` özniteliği, aynı kod yürütmek ancak farklı giriş bağımsız değişkeni olan testleri bir paketi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3370d-157">A `<TestCase>` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="3370d-158">Kullanabileceğiniz `<TestCase>` özniteliği bu girişleri için değerleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="3370d-158">You can use the `<TestCase>` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="3370d-159">Yeni testler oluşturmak yerine, en düşük asal sayı olan bir dizi test çeşitli değerleri değerinden iki test oluşturmak için bu iki öznitelikler uygulanır:</span><span class="sxs-lookup"><span data-stu-id="3370d-159">Instead of creating new tests, apply these two attributes to create a series of tests that test several values less than two, which is the lowest prime number:</span></span>

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

<span data-ttu-id="3370d-160">Çalıştırma `dotnet test`, ve bunların ikisini sınamaları başarısız.</span><span class="sxs-lookup"><span data-stu-id="3370d-160">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="3370d-161">Tüm testleri geçişini yapmak için değiştirme `if` yöntemi başındaki yan tümcesi:</span><span class="sxs-lookup"><span data-stu-id="3370d-161">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```vb
if candidate < 2
```

<span data-ttu-id="3370d-162">Daha fazla testleri, daha fazla kuramlarý ve daha fazla kod ana kitaplıkta ekleyerek yinelemek devam edin.</span><span class="sxs-lookup"><span data-stu-id="3370d-162">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="3370d-163">Sahip olduğunuz [testleri tamamlanmış sürümü](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) ve [kitaplığının tam uygulama](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb).</span><span class="sxs-lookup"><span data-stu-id="3370d-163">You have the [finished version of the tests](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="3370d-164">Küçük bir kitaplığı ve bu kitaplık için birim testleri kümesini temel aldık.</span><span class="sxs-lookup"><span data-stu-id="3370d-164">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="3370d-165">Böylece yeni paketleri ekleme çözümü yapılandırılmış ve testleri normal iş akışı bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="3370d-165">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="3370d-166">Çoğu zaman ve çaba uygulama amaçlarını çözme üzerinde yoğunlaşmıştır.</span><span class="sxs-lookup"><span data-stu-id="3370d-166">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
