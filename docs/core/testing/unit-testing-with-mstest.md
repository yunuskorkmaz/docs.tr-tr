---
title: MSTest ve C# .NET Core ile birim testi
description: Ve .NET Core 'daki C# birim testi kavramlarını, DotNet test ve MSTest kullanarak örnek bir çözüm oluşturarak bir etkileşimli deneyim aracılığıyla öğrenin.
author: ncarandini
ms.author: wiwagn
ms.date: 09/08/2017
ms.openlocfilehash: bd7891243d84277a7578089f8b4629ff5bada577
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240915"
---
# <a name="unit-testing-c-with-mstest-and-net-core"></a><span data-ttu-id="ef3b3-103">MSTest ve C# .NET Core ile birim testi</span><span class="sxs-lookup"><span data-stu-id="ef3b3-103">Unit testing C# with MSTest and .NET Core</span></span>

<span data-ttu-id="ef3b3-104">Bu öğreticide, birim testi kavramlarını öğrenmek için bir örnek çözüm oluşturma adım adım yönergeler sunarak etkileşimli bir deneyim sağlanır.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="ef3b3-105">Önceden oluşturulmuş bir çözüm kullanarak öğreticiyi izlemeyi tercih ediyorsanız, başlamadan önce [örnek kodu görüntüleyin veya indirin](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/) .</span><span class="sxs-lookup"><span data-stu-id="ef3b3-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/) before you begin.</span></span> <span data-ttu-id="ef3b3-106">İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="ef3b3-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="create-the-source-project"></a><span data-ttu-id="ef3b3-107">Kaynak projeyi oluşturma</span><span class="sxs-lookup"><span data-stu-id="ef3b3-107">Create the source project</span></span>

<span data-ttu-id="ef3b3-108">Bir kabuk penceresi açın.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-108">Open a shell window.</span></span> <span data-ttu-id="ef3b3-109">Çözümü tutmak için- *Testing-testusing* adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-109">Create a directory called *unit-testing-using-mstest* to hold the solution.</span></span> <span data-ttu-id="ef3b3-110">Bu yeni dizinin içinde, sınıf kitaplığı ve test projesi için yeni bir çözüm dosyası oluşturmak üzere [`dotnet new sln`](../tools/dotnet-new.md) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution file for the class library and the test project.</span></span> <span data-ttu-id="ef3b3-111">Ardından, bir *Primeservice* dizini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-111">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="ef3b3-112">Aşağıdaki ana hat, şu ana kadar dizin ve dosya yapısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="ef3b3-112">The following outline shows the directory and file structure thus far:</span></span>

```console
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
```

<span data-ttu-id="ef3b3-113">Kaynak projeyi oluşturmak için *Primeservice* 'i geçerli dizin yapın ve [`dotnet new classlib`](../tools/dotnet-new.md) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-113">Make *PrimeService* the current directory and run [`dotnet new classlib`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="ef3b3-114">*Class1.cs* *olarak yeniden*adlandırın.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-114">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="ef3b3-115">`PrimeService` sınıfının başarısız bir uygulamasını oluşturursunuz:</span><span class="sxs-lookup"><span data-stu-id="ef3b3-115">You create a failing implementation of the `PrimeService` class:</span></span>

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

<span data-ttu-id="ef3b3-116">Dizini *Unit-Testing-MSTest* dizinine doğru değiştirin.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-116">Change the directory back to the *unit-testing-using-mstest* directory.</span></span> <span data-ttu-id="ef3b3-117">Çözüme Sınıf Kitaplığı projesini eklemek için [`dotnet sln add PrimeService/PrimeService.csproj`](../tools/dotnet-sln.md) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-117">Run [`dotnet sln add PrimeService/PrimeService.csproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="create-the-test-project"></a><span data-ttu-id="ef3b3-118">Test projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="ef3b3-118">Create the test project</span></span>

<span data-ttu-id="ef3b3-119">Ardından, *Primeservice. Tests* dizinini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-119">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="ef3b3-120">Aşağıdaki ana hat dizin yapısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="ef3b3-120">The following outline shows the directory structure:</span></span>

```console
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="ef3b3-121">*Primeservice. test* dizinini geçerli dizini yapın ve [`dotnet new mstest`](../tools/dotnet-new.md)kullanarak yeni bir proje oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-121">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new mstest`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="ef3b3-122">DotNet New komutu, test kitaplığı olarak MSTest kullanan bir test projesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-122">The dotnet new command creates a test project that uses MSTest as the test library.</span></span> <span data-ttu-id="ef3b3-123">Oluşturulan şablon, *Primeservicetests. csproj* dosyasında Test Çalıştırıcısı 'nı yapılandırır:</span><span class="sxs-lookup"><span data-stu-id="ef3b3-123">The generated template configures the test runner in the *PrimeServiceTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

<span data-ttu-id="ef3b3-124">Test projesi, birim testlerini oluşturmak ve çalıştırmak için diğer paketlerin kullanılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-124">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="ef3b3-125">önceki adımda `dotnet new` MSTest SDK, MSTest test çerçevesi ve MSTest Çalıştırıcısı eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-125">`dotnet new` in the previous step added the MSTest SDK, the MSTest test framework, and the MSTest runner.</span></span> <span data-ttu-id="ef3b3-126">Şimdi, `PrimeService` sınıf kitaplığını projeye başka bir bağımlılık olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-126">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="ef3b3-127">[`dotnet add reference`](../tools/dotnet-add-reference.md) komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="ef3b3-127">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="ef3b3-128">GitHub 'daki [örnekler deposunda](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) dosyanın tamamını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-128">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="ef3b3-129">Aşağıdaki ana hat, son çözüm yerleşimini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="ef3b3-129">The following outline shows the final solution layout:</span></span>

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

<span data-ttu-id="ef3b3-130">[`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) *birim-test-using-MSTest* dizininde yürütün.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-130">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) in the *unit-testing-using-mstest* directory.</span></span>

## <a name="create-the-first-test"></a><span data-ttu-id="ef3b3-131">İlk testi oluşturma</span><span class="sxs-lookup"><span data-stu-id="ef3b3-131">Create the first test</span></span>

<span data-ttu-id="ef3b3-132">Başarısız bir test yazdığınızda, geçişi yapıp işlemi tekrarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-132">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="ef3b3-133">*UnitTest1.cs* öğesini *primeservice. Tests* dizininden kaldırın ve aşağıdaki içeriğe sahip C# *PrimeService_IsPrimeShould. cs* adlı yeni bir dosya oluşturun:</span><span class="sxs-lookup"><span data-stu-id="ef3b3-133">Remove *UnitTest1.cs* from the *PrimeService.Tests* directory and create a new C# file named *PrimeService_IsPrimeShould.cs* with the following content:</span></span>

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

<span data-ttu-id="ef3b3-134">[TestClass özniteliği](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) birim testlerini içeren bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-134">The [TestClass attribute](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) denotes a class that contains unit tests.</span></span> <span data-ttu-id="ef3b3-135">[TestMethod özniteliği](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) bir yöntemin test yöntemi olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-135">The [TestMethod attribute](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) indicates a method is a test method.</span></span>

<span data-ttu-id="ef3b3-136">Testleri ve sınıf kitaplığını oluşturmak için bu dosyayı kaydedin ve [`dotnet test`](../tools/dotnet-test.md) yürütün ve ardından testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-136">Save this file and execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="ef3b3-137">MSTest Test Çalıştırıcısı, testlerinizi çalıştırmak için program giriş noktasını içerir.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-137">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="ef3b3-138">`dotnet test`, oluşturduğunuz birim test projesini kullanarak Test Çalıştırıcısı başlatır.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-138">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="ef3b3-139">Testiniz başarısız oluyor.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-139">Your test fails.</span></span> <span data-ttu-id="ef3b3-140">Uygulamayı henüz oluşturmadınız.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-140">You haven't created the implementation yet.</span></span> <span data-ttu-id="ef3b3-141">Aşağıdaki `PrimeService` sınıfında en basit kodu yazarak bu test geçişini yapın:</span><span class="sxs-lookup"><span data-stu-id="ef3b3-141">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

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

<span data-ttu-id="ef3b3-142">*Birim-test-using-MSTest* dizininde `dotnet test` yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-142">In the *unit-testing-using-mstest* directory, run `dotnet test` again.</span></span> <span data-ttu-id="ef3b3-143">`dotnet test` komutu, `PrimeService` projesi için bir derleme ve sonra `PrimeService.Tests` projesi için çalışır.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-143">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="ef3b3-144">Her iki proje de oluşturulduktan sonra bu tek testi çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-144">After building both projects, it runs this single test.</span></span> <span data-ttu-id="ef3b3-145">Geçirir.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-145">It passes.</span></span>

## <a name="add-more-features"></a><span data-ttu-id="ef3b3-146">Daha fazla özellik ekleyin</span><span class="sxs-lookup"><span data-stu-id="ef3b3-146">Add more features</span></span>

<span data-ttu-id="ef3b3-147">Artık bir test geçişi yapmış olduğunuza göre daha fazla yazma zamanı vardır.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-147">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="ef3b3-148">Asal sayıların diğer birkaç basit durumu vardır: 0,-1.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-148">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="ef3b3-149">[TestMethod özniteliğiyle](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute)yeni testler ekleyebilirsiniz, ancak bu hızlı bir şekilde sıkıcı hale gelir.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-149">You could add new tests with the [TestMethod attribute](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute), but that quickly becomes tedious.</span></span> <span data-ttu-id="ef3b3-150">Benzer testlerin bir paketini yazmanızı sağlayan başka bir MSTest özniteliği vardır.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-150">There are other MSTest attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="ef3b3-151">[Datatestmethod özniteliği](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataTestMethodAttribute) , aynı kodu çalıştıran ancak farklı giriş bağımsız değişkenlerine sahip olan bir test paketini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-151">A [DataTestMethod attribute](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataTestMethodAttribute) represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="ef3b3-152">Bu girişlerin değerlerini belirtmek için [DataRow özniteliğini](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataRowAttribute) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-152">You can use the [DataRow attribute](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataRowAttribute) to specify values for those inputs.</span></span>

<span data-ttu-id="ef3b3-153">Yeni test oluşturmak yerine, tek bir veri temelli test oluşturmak için bu iki özniteliği uygulayın.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-153">Instead of creating new tests, apply these two attributes to create a single data driven test.</span></span> <span data-ttu-id="ef3b3-154">Veri temelli test, en düşük asal sayı olan iki değerden küçük birkaç değeri sınayan bir yöntemdir:</span><span class="sxs-lookup"><span data-stu-id="ef3b3-154">The data driven test is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-csharp[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-using-mstest/csharp/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="ef3b3-155">`dotnet test`çalıştırın, bu testlerin ikisi de başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-155">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="ef3b3-156">Tüm testlerin geçişini yapmak için, yönteminin başındaki `if` yan tümcesini değiştirin:</span><span class="sxs-lookup"><span data-stu-id="ef3b3-156">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="ef3b3-157">Ana kitaplıkta daha fazla test, daha fazla yer ve daha fazla kod ekleyerek yinelemek için devam edin.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-157">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="ef3b3-158">[Testlerin tamamlanmış sürümüne](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) ve [kitaplığın tüm uygulamasına](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs)sahipsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-158">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="ef3b3-159">Bu kitaplık için küçük bir kitaplık ve birim testleri kümesi oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-159">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="ef3b3-160">Çözümü, yeni paket ve test eklemek normal iş akışının bir parçası olacak şekilde öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-160">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="ef3b3-161">Uygulamanın hedeflerini çözme konusunda zaman ve çaba harcamanızı en iyi şekilde gördünüz.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-161">You've concentrated most of your time and effort on solving the goals of the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="ef3b3-162">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-162">See also</span></span>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting>
- [<span data-ttu-id="ef3b3-163">Birim testlerinde MSTest çerçevesini kullanma</span><span class="sxs-lookup"><span data-stu-id="ef3b3-163">Use the MSTest framework in unit tests</span></span>](/visualstudio/test/using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests)
- [<span data-ttu-id="ef3b3-164">MSTest v2 test çerçevesi belgeleri</span><span class="sxs-lookup"><span data-stu-id="ef3b3-164">MSTest V2 test framework docs</span></span>](https://github.com/Microsoft/testfx-docs)
