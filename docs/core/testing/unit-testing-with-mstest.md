---
title: C# testini MSTest ve .NET Core ile test etme
description: Noktanet testi ve MSTest kullanarak adım adım örnek bir çözüm oluşturma etkileşimli bir deneyim le C# ve .NET Core'daki birim test kavramlarını öğrenin.
author: ncarandini
ms.author: wiwagn
ms.date: 09/08/2017
ms.openlocfilehash: bd7891243d84277a7578089f8b4629ff5bada577
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240915"
---
# <a name="unit-testing-c-with-mstest-and-net-core"></a><span data-ttu-id="cb174-103">C# testini MSTest ve .NET Core ile test etme</span><span class="sxs-lookup"><span data-stu-id="cb174-103">Unit testing C# with MSTest and .NET Core</span></span>

<span data-ttu-id="cb174-104">Bu öğretici, birim test kavramlarını öğrenmek için adım adım örnek bir çözüm oluşturma etkileşimli bir deneyim sunar.</span><span class="sxs-lookup"><span data-stu-id="cb174-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="cb174-105">Önceden oluşturulmuş bir çözüm kullanarak öğreticiyi izlemeyi tercih ederseniz, başlamadan önce [örnek kodu görüntüleyin veya indirin.](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/)</span><span class="sxs-lookup"><span data-stu-id="cb174-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/) before you begin.</span></span> <span data-ttu-id="cb174-106">İndirme talimatları için [Örnekler ve Öğreticiler'e](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)bakın.</span><span class="sxs-lookup"><span data-stu-id="cb174-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="create-the-source-project"></a><span data-ttu-id="cb174-107">Kaynak projeoluşturma</span><span class="sxs-lookup"><span data-stu-id="cb174-107">Create the source project</span></span>

<span data-ttu-id="cb174-108">Bir kabuk penceresi açın.</span><span class="sxs-lookup"><span data-stu-id="cb174-108">Open a shell window.</span></span> <span data-ttu-id="cb174-109">Çözümü tutmak için *birim-test-using-mstest* adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cb174-109">Create a directory called *unit-testing-using-mstest* to hold the solution.</span></span> <span data-ttu-id="cb174-110">Bu yeni dizinin içinde, sınıf kitaplığı ve test projesi için yeni bir çözüm dosyası oluşturmak için çalıştırın. [`dotnet new sln`](../tools/dotnet-new.md)</span><span class="sxs-lookup"><span data-stu-id="cb174-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution file for the class library and the test project.</span></span> <span data-ttu-id="cb174-111">Ardından, bir *PrimeService* dizini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cb174-111">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="cb174-112">Aşağıdaki anahat şimdiye kadar dizin ve dosya yapısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="cb174-112">The following outline shows the directory and file structure thus far:</span></span>

```console
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
```

<span data-ttu-id="cb174-113">*PrimeService'i* geçerli dizin [`dotnet new classlib`](../tools/dotnet-new.md) yapın ve kaynak projeyi oluşturmak için çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cb174-113">Make *PrimeService* the current directory and run [`dotnet new classlib`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="cb174-114">*Class1.cs* *PrimeService.cs*yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="cb174-114">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="cb174-115">`PrimeService` Sınıfın başarısız bir uygulamasını oluşturursunuz:</span><span class="sxs-lookup"><span data-stu-id="cb174-115">You create a failing implementation of the `PrimeService` class:</span></span>

```csharp
using System;

namespace Prime.Services
{
    public class PrimeService
    {
        public bool IsPrime(int candidate)
        {
            throw new NotImplementedException("Please create a test first.");
        }
    }
}
```

<span data-ttu-id="cb174-116">Dizin geri *birim-test-using-mstest* dizin değiştirin.</span><span class="sxs-lookup"><span data-stu-id="cb174-116">Change the directory back to the *unit-testing-using-mstest* directory.</span></span> <span data-ttu-id="cb174-117">Sınıf [`dotnet sln add PrimeService/PrimeService.csproj`](../tools/dotnet-sln.md) kitaplığı projesini çözüme eklemek için çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cb174-117">Run [`dotnet sln add PrimeService/PrimeService.csproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="create-the-test-project"></a><span data-ttu-id="cb174-118">Test projesini oluşturma</span><span class="sxs-lookup"><span data-stu-id="cb174-118">Create the test project</span></span>

<span data-ttu-id="cb174-119">Ardından, *PrimeService.Tests* dizinini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cb174-119">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="cb174-120">Aşağıdaki anahat dizin yapısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="cb174-120">The following outline shows the directory structure:</span></span>

```console
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="cb174-121">*PrimeService.Tests* dizinini geçerli dizini oluşturun ve yeni [`dotnet new mstest`](../tools/dotnet-new.md)bir proje oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cb174-121">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new mstest`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="cb174-122">Dotnet yeni komutu, test kitaplığı olarak MSTest kullanan bir test projesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cb174-122">The dotnet new command creates a test project that uses MSTest as the test library.</span></span> <span data-ttu-id="cb174-123">Oluşturulan *şablon, PrimeServiceTests.csproj* dosyasındaki test koşucusu yla yapılandırır:</span><span class="sxs-lookup"><span data-stu-id="cb174-123">The generated template configures the test runner in the *PrimeServiceTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

<span data-ttu-id="cb174-124">Test projesi, birim testleri oluşturmak ve çalıştırmak için diğer paketler gerektirir.</span><span class="sxs-lookup"><span data-stu-id="cb174-124">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="cb174-125">`dotnet new`önceki adımda MSTest SDK, MSTest test çerçevesi ve MSTest runner eklendi.</span><span class="sxs-lookup"><span data-stu-id="cb174-125">`dotnet new` in the previous step added the MSTest SDK, the MSTest test framework, and the MSTest runner.</span></span> <span data-ttu-id="cb174-126">Şimdi, `PrimeService` sınıf kitaplığını projeye başka bir bağımlılık olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cb174-126">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="cb174-127">Komutu [`dotnet add reference`](../tools/dotnet-add-reference.md) kullanın:</span><span class="sxs-lookup"><span data-stu-id="cb174-127">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="cb174-128">Tüm dosyayı GitHub'daki [örnek deposunda](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cb174-128">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="cb174-129">Aşağıdaki anahat son çözüm düzenini gösterir:</span><span class="sxs-lookup"><span data-stu-id="cb174-129">The following outline shows the final solution layout:</span></span>

```console
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

<span data-ttu-id="cb174-130">[`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) *Birim-test-using-mstest* dizininde yürütün.</span><span class="sxs-lookup"><span data-stu-id="cb174-130">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) in the *unit-testing-using-mstest* directory.</span></span>

## <a name="create-the-first-test"></a><span data-ttu-id="cb174-131">İlk testi oluşturma</span><span class="sxs-lookup"><span data-stu-id="cb174-131">Create the first test</span></span>

<span data-ttu-id="cb174-132">Başarısız bir test yazarsın, geçer ve işlemi tekrarlarsın.</span><span class="sxs-lookup"><span data-stu-id="cb174-132">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="cb174-133">*UnitTest1.cs* *PrimeService.Tests* dizininden kaldırın ve aşağıdaki içeriği içeren *PrimeService_IsPrimeShould.cs* adlı yeni bir C# dosyası oluşturun:</span><span class="sxs-lookup"><span data-stu-id="cb174-133">Remove *UnitTest1.cs* from the *PrimeService.Tests* directory and create a new C# file named *PrimeService_IsPrimeShould.cs* with the following content:</span></span>

```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    [TestClass]
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;

        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [TestMethod]
        public void IsPrime_InputIs1_ReturnFalse()
        {
            var result = _primeService.IsPrime(1);

            Assert.IsFalse(result, "1 should not be prime");
        }
    }
}
```

<span data-ttu-id="cb174-134">[TestClass özniteliği](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) birim testleri içeren bir sınıf gösterir.</span><span class="sxs-lookup"><span data-stu-id="cb174-134">The [TestClass attribute](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) denotes a class that contains unit tests.</span></span> <span data-ttu-id="cb174-135">[TestMethod özniteliği](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) bir yöntemin bir test yöntemi olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="cb174-135">The [TestMethod attribute](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) indicates a method is a test method.</span></span>

<span data-ttu-id="cb174-136">Bu dosyayı [`dotnet test`](../tools/dotnet-test.md) kaydedin ve testleri ve sınıf kitaplığını oluşturmak ve testleri çalıştırmak için çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cb174-136">Save this file and execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="cb174-137">MSTest test koşucusu, testlerinizi çalıştırmak için program giriş noktasını içerir.</span><span class="sxs-lookup"><span data-stu-id="cb174-137">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="cb174-138">`dotnet test`oluşturduğunuz birim test projesini kullanarak test koşucusu başlatın.</span><span class="sxs-lookup"><span data-stu-id="cb174-138">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="cb174-139">Sınavın başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="cb174-139">Your test fails.</span></span> <span data-ttu-id="cb174-140">Uygulamayı henüz oluşturmadın.</span><span class="sxs-lookup"><span data-stu-id="cb174-140">You haven't created the implementation yet.</span></span> <span data-ttu-id="cb174-141">Bu testin çalışmasını sağlayan `PrimeService` sınıftaki en basit kodu yazarak geçmesini sağla:</span><span class="sxs-lookup"><span data-stu-id="cb174-141">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

```csharp
public bool IsPrime(int candidate)
{
    if (candidate == 1)
    {
        return false;
    }
    throw new NotImplementedException("Please create a test first.");
}
```

<span data-ttu-id="cb174-142">*Birim-test-using-mstest* dizininde, yeniden `dotnet test` çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cb174-142">In the *unit-testing-using-mstest* directory, run `dotnet test` again.</span></span> <span data-ttu-id="cb174-143">Komut, `dotnet test` proje ve ardından `PrimeService.Tests` proje için bir yapı çalışır. `PrimeService`</span><span class="sxs-lookup"><span data-stu-id="cb174-143">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="cb174-144">Her iki projeyi de yaptıktan sonra, bu tek testi çalıştırAr.</span><span class="sxs-lookup"><span data-stu-id="cb174-144">After building both projects, it runs this single test.</span></span> <span data-ttu-id="cb174-145">Geçiyor.</span><span class="sxs-lookup"><span data-stu-id="cb174-145">It passes.</span></span>

## <a name="add-more-features"></a><span data-ttu-id="cb174-146">Daha fazla özellik ekleme</span><span class="sxs-lookup"><span data-stu-id="cb174-146">Add more features</span></span>

<span data-ttu-id="cb174-147">Artık bir test sınavını geçtiğine göre, daha fazla yazma nın zamanı.</span><span class="sxs-lookup"><span data-stu-id="cb174-147">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="cb174-148">Asal sayılar için birkaç basit durum daha vardır: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="cb174-148">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="cb174-149">[TestMethod özniteliği](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute)ile yeni testler ekleyebilirsiniz, ancak bu hızla sıkıcı olur.</span><span class="sxs-lookup"><span data-stu-id="cb174-149">You could add new tests with the [TestMethod attribute](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute), but that quickly becomes tedious.</span></span> <span data-ttu-id="cb174-150">Benzer testler paketi yazmanızı sağlayan başka MSTest öznitelikleri de vardır.</span><span class="sxs-lookup"><span data-stu-id="cb174-150">There are other MSTest attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="cb174-151">[DataTestMethod özniteliği,](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataTestMethodAttribute) aynı kodu çalıştıran ancak farklı giriş bağımsız değişkenleri olan bir test paketini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="cb174-151">A [DataTestMethod attribute](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataTestMethodAttribute) represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="cb174-152">Bu girişler için değerleri belirtmek için [DataRow özniteliğini](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataRowAttribute) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cb174-152">You can use the [DataRow attribute](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataRowAttribute) to specify values for those inputs.</span></span>

<span data-ttu-id="cb174-153">Yeni testler oluşturmak yerine, tek bir veri odaklı test oluşturmak için bu iki öznitelikleri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="cb174-153">Instead of creating new tests, apply these two attributes to create a single data driven test.</span></span> <span data-ttu-id="cb174-154">Veri odaklı test, ikiden küçük birkaç değeri sınayan ve en düşük asal sayı olan bir yöntemdir:</span><span class="sxs-lookup"><span data-stu-id="cb174-154">The data driven test is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-csharp[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-using-mstest/csharp/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="cb174-155">Çalıştır `dotnet test`Ve bu testlerin iki başarısız.</span><span class="sxs-lookup"><span data-stu-id="cb174-155">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="cb174-156">Tüm testlerin geçmesi için yöntemin başındaki `if` tümceyi değiştirin:</span><span class="sxs-lookup"><span data-stu-id="cb174-156">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="cb174-157">Ana kitaplığa daha fazla test, daha fazla teori ve daha fazla kod ekleyerek yinelemeye devam edin.</span><span class="sxs-lookup"><span data-stu-id="cb174-157">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="cb174-158">[Testlerin tamamlanmış sürümüne](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) ve [kitaplığın tam uygulamasına](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs)sahipsiniz.</span><span class="sxs-lookup"><span data-stu-id="cb174-158">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="cb174-159">O kitaplık için küçük bir kitaplık ve bir dizi birim testi inşa ettin.</span><span class="sxs-lookup"><span data-stu-id="cb174-159">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="cb174-160">Yeni paketler ve testler eklemek normal iş akışının bir parçası olacak şekilde çözümü yapılandırdınız.</span><span class="sxs-lookup"><span data-stu-id="cb174-160">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="cb174-161">Zamanınızın ve çabanızın çoğunu uygulamanın hedeflerini çözmeye yoğunlaşmışsınız.</span><span class="sxs-lookup"><span data-stu-id="cb174-161">You've concentrated most of your time and effort on solving the goals of the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="cb174-162">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb174-162">See also</span></span>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting>
- [<span data-ttu-id="cb174-163">Birim testlerinde MSTest çerçevesini kullanma</span><span class="sxs-lookup"><span data-stu-id="cb174-163">Use the MSTest framework in unit tests</span></span>](/visualstudio/test/using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests)
- [<span data-ttu-id="cb174-164">MSTest V2 test çerçeve dokümanları</span><span class="sxs-lookup"><span data-stu-id="cb174-164">MSTest V2 test framework docs</span></span>](https://github.com/Microsoft/testfx-docs)
