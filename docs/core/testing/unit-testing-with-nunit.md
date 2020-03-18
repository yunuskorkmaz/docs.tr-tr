---
title: C# nunit ve .NET Core ile birim testi
description: Noktanet testi ve NUnit kullanarak adım adım örnek bir çözüm oluşturma etkileşimli bir deneyim le C# ve .NET Core'daki birim test kavramlarını öğrenin.
author: rprouse
ms.date: 08/31/2018
ms.openlocfilehash: 283aa5a28ed213d4290eb3c73a98af56ec074ad0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240889"
---
# <a name="unit-testing-c-with-nunit-and-net-core"></a><span data-ttu-id="e54a3-103">C# nunit ve .NET Core ile birim testi</span><span class="sxs-lookup"><span data-stu-id="e54a3-103">Unit testing C# with NUnit and .NET Core</span></span>

<span data-ttu-id="e54a3-104">Bu öğretici, birim test kavramlarını öğrenmek için adım adım örnek bir çözüm oluşturma etkileşimli bir deneyim sunar.</span><span class="sxs-lookup"><span data-stu-id="e54a3-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="e54a3-105">Önceden oluşturulmuş bir çözüm kullanarak öğreticiyi izlemeyi tercih ederseniz, başlamadan önce [örnek kodu görüntüleyin veya indirin.](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/)</span><span class="sxs-lookup"><span data-stu-id="e54a3-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/) before you begin.</span></span> <span data-ttu-id="e54a3-106">İndirme talimatları için [Örnekler ve Öğreticiler'e](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)bakın.</span><span class="sxs-lookup"><span data-stu-id="e54a3-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="prerequisites"></a><span data-ttu-id="e54a3-107">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="e54a3-107">Prerequisites</span></span>

- <span data-ttu-id="e54a3-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) veya sonraki sürümler.</span><span class="sxs-lookup"><span data-stu-id="e54a3-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later versions.</span></span>
- <span data-ttu-id="e54a3-109">Tercih ettiğiniz bir metin veya kod düzenleyicisi.</span><span class="sxs-lookup"><span data-stu-id="e54a3-109">A text editor or code editor of your choice.</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="e54a3-110">Kaynak proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="e54a3-110">Creating the source project</span></span>

<span data-ttu-id="e54a3-111">Bir kabuk penceresi açın.</span><span class="sxs-lookup"><span data-stu-id="e54a3-111">Open a shell window.</span></span> <span data-ttu-id="e54a3-112">Çözümü tutmak için *birim-test-using-nunit* adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e54a3-112">Create a directory called *unit-testing-using-nunit* to hold the solution.</span></span> <span data-ttu-id="e54a3-113">Bu yeni dizinin içinde, sınıf kitaplığı ve test projesi için yeni bir çözüm dosyası oluşturmak için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="e54a3-113">Inside this new directory, run the following command to create a new solution file for the class library and the test project:</span></span>

```dotnetcli
dotnet new sln
```

<span data-ttu-id="e54a3-114">Ardından, bir *PrimeService* dizini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e54a3-114">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="e54a3-115">Aşağıdaki anahat şimdiye kadar dizin ve dosya yapısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="e54a3-115">The following outline shows the directory and file structure so far:</span></span>

```console
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
```

<span data-ttu-id="e54a3-116">*PrimeService'i* geçerli dizini yapın ve kaynak projeyi oluşturmak için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="e54a3-116">Make *PrimeService* the current directory and run the following command to create the source project:</span></span>

```dotnetcli
dotnet new classlib
```

<span data-ttu-id="e54a3-117">*Class1.cs* *PrimeService.cs*yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="e54a3-117">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="e54a3-118">`PrimeService` Sınıfın başarısız bir uygulamasını oluşturursunuz:</span><span class="sxs-lookup"><span data-stu-id="e54a3-118">You create a failing implementation of the `PrimeService` class:</span></span>

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

<span data-ttu-id="e54a3-119">Dizin geri *birim-test-kullanarak-nunit* dizini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e54a3-119">Change the directory back to the *unit-testing-using-nunit* directory.</span></span> <span data-ttu-id="e54a3-120">Sınıf kitaplığı projesini çözüme eklemek için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="e54a3-120">Run the following command to add the class library project to the solution:</span></span>

```dotnetcli
dotnet sln add PrimeService/PrimeService.csproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="e54a3-121">Test projesini oluşturma</span><span class="sxs-lookup"><span data-stu-id="e54a3-121">Creating the test project</span></span>

<span data-ttu-id="e54a3-122">Ardından, *PrimeService.Tests* dizinini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e54a3-122">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="e54a3-123">Aşağıdaki anahat dizin yapısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="e54a3-123">The following outline shows the directory structure:</span></span>

```console
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="e54a3-124">*PrimeService.Tests* dizinini geçerli dizini oluşturun ve aşağıdaki komutu kullanarak yeni bir proje oluşturun:</span><span class="sxs-lookup"><span data-stu-id="e54a3-124">Make the *PrimeService.Tests* directory the current directory and create a new project using the following command:</span></span>

```dotnetcli
dotnet new nunit
```

<span data-ttu-id="e54a3-125">[Dotnet yeni](../tools/dotnet-new.md) komutu, test kitaplığı olarak NUnit kullanan bir test projesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e54a3-125">The [dotnet new](../tools/dotnet-new.md) command creates a test project that uses NUnit as the test library.</span></span> <span data-ttu-id="e54a3-126">Oluşturulan şablon *PrimeService.Tests.csproj* dosyasında test koşucusu yapılandırır:</span><span class="sxs-lookup"><span data-stu-id="e54a3-126">The generated template configures the test runner in the *PrimeService.Tests.csproj* file:</span></span>

[!code-xml[Packages](~/samples/snippets/core/testing/unit-testing-using-nunit/csharp/PrimeService.Tests/PrimeService.Tests.csproj#Packages)]

<span data-ttu-id="e54a3-127">Test projesi, birim testleri oluşturmak ve çalıştırmak için diğer paketler gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e54a3-127">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="e54a3-128">`dotnet new`önceki adımda Microsoft test SDK, NUnit test çerçevesi ve NUnit test bağdaştırıcısı eklendi.</span><span class="sxs-lookup"><span data-stu-id="e54a3-128">`dotnet new` in the previous step added the Microsoft test SDK, the NUnit test framework, and the NUnit test adapter.</span></span> <span data-ttu-id="e54a3-129">Şimdi, `PrimeService` sınıf kitaplığını projeye başka bir bağımlılık olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e54a3-129">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="e54a3-130">Komutu [`dotnet add reference`](../tools/dotnet-add-reference.md) kullanın:</span><span class="sxs-lookup"><span data-stu-id="e54a3-130">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="e54a3-131">Tüm dosyayı GitHub'daki [örnek deposunda](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj) görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e54a3-131">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="e54a3-132">Aşağıdaki anahat son çözüm düzenini gösterir:</span><span class="sxs-lookup"><span data-stu-id="e54a3-132">The following outline shows the final solution layout:</span></span>

```console
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeService.Tests.csproj
```

<span data-ttu-id="e54a3-133">*Birim-test-using-nunit* dizininde aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="e54a3-133">Execute the following command in the *unit-testing-using-nunit* directory:</span></span>

```dotnetcli
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="e54a3-134">İlk testi oluşturma</span><span class="sxs-lookup"><span data-stu-id="e54a3-134">Creating the first test</span></span>

<span data-ttu-id="e54a3-135">Başarısız bir test yazarsın, geçer ve işlemi tekrarlarsın.</span><span class="sxs-lookup"><span data-stu-id="e54a3-135">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="e54a3-136">*PrimeService.Tests* dizininde, *UnitTest1.cs* dosyasını *PrimeService_IsPrimeShould.cs* olarak yeniden adlandırın ve tüm içeriğini aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="e54a3-136">In the *PrimeService.Tests* directory, rename the *UnitTest1.cs* file to *PrimeService_IsPrimeShould.cs* and replace its entire contents with the following code:</span></span>

[!code-csharp[Sample_FirstTest](~/samples/snippets/core/testing/unit-testing-using-nunit/csharp/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_FirstTest)]

<span data-ttu-id="e54a3-137">Öznitelik `[TestFixture]` birim testleri içeren bir sınıf gösterir.</span><span class="sxs-lookup"><span data-stu-id="e54a3-137">The `[TestFixture]` attribute denotes a class that contains unit tests.</span></span> <span data-ttu-id="e54a3-138">Öznitelik `[Test]` bir yöntem bir test yöntemi olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e54a3-138">The `[Test]` attribute indicates a method is a test method.</span></span>

<span data-ttu-id="e54a3-139">Bu dosyayı [`dotnet test`](../tools/dotnet-test.md) kaydedin ve testleri ve sınıf kitaplığını oluşturmak ve testleri çalıştırmak için çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e54a3-139">Save this file and execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="e54a3-140">NUnit test koşucusu, testlerinizi çalıştırmak için program giriş noktasını içerir.</span><span class="sxs-lookup"><span data-stu-id="e54a3-140">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="e54a3-141">`dotnet test`oluşturduğunuz birim test projesini kullanarak test koşucusu başlatın.</span><span class="sxs-lookup"><span data-stu-id="e54a3-141">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="e54a3-142">Sınavın başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="e54a3-142">Your test fails.</span></span> <span data-ttu-id="e54a3-143">Uygulamayı henüz oluşturmadın.</span><span class="sxs-lookup"><span data-stu-id="e54a3-143">You haven't created the implementation yet.</span></span> <span data-ttu-id="e54a3-144">Bu testin çalışmasını sağlayan `PrimeService` sınıftaki en basit kodu yazarak geçmesini sağla:</span><span class="sxs-lookup"><span data-stu-id="e54a3-144">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

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

<span data-ttu-id="e54a3-145">*Birim-test-using-nunit* dizininde, yeniden `dotnet test` çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e54a3-145">In the *unit-testing-using-nunit* directory, run `dotnet test` again.</span></span> <span data-ttu-id="e54a3-146">Komut, `dotnet test` proje ve ardından `PrimeService.Tests` proje için bir yapı çalışır. `PrimeService`</span><span class="sxs-lookup"><span data-stu-id="e54a3-146">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="e54a3-147">Her iki projeyi de yaptıktan sonra, bu tek testi çalıştırAr.</span><span class="sxs-lookup"><span data-stu-id="e54a3-147">After building both projects, it runs this single test.</span></span> <span data-ttu-id="e54a3-148">Geçiyor.</span><span class="sxs-lookup"><span data-stu-id="e54a3-148">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="e54a3-149">Daha fazla özellik ekleme</span><span class="sxs-lookup"><span data-stu-id="e54a3-149">Adding more features</span></span>

<span data-ttu-id="e54a3-150">Artık bir test sınavını geçtiğine göre, daha fazla yazma nın zamanı.</span><span class="sxs-lookup"><span data-stu-id="e54a3-150">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="e54a3-151">Asal sayılar için birkaç basit durum daha vardır: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="e54a3-151">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="e54a3-152">Öznitelik ile `[Test]` yeni testler ekleyebilirsiniz, ancak bu hızla sıkıcı olur.</span><span class="sxs-lookup"><span data-stu-id="e54a3-152">You could add new tests with the `[Test]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="e54a3-153">Benzer testler paketi yazmanızı sağlayan başka NUnit öznitelikleri de vardır.</span><span class="sxs-lookup"><span data-stu-id="e54a3-153">There are other NUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="e54a3-154">Öznitelik, `[TestCase]` aynı kodu çalıştıran ancak farklı giriş bağımsız değişkenleri olan bir test paketi oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e54a3-154">A `[TestCase]` attribute is used to create a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="e54a3-155">Bu girişler `[TestCase]` için değerleri belirtmek için özniteliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e54a3-155">You can use the `[TestCase]` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="e54a3-156">Yeni testler oluşturmak yerine, tek bir veri odaklı test oluşturmak için bu özniteliği uygulayın.</span><span class="sxs-lookup"><span data-stu-id="e54a3-156">Instead of creating new tests, apply this attribute to create a single data driven test.</span></span> <span data-ttu-id="e54a3-157">Veri odaklı test, ikiden küçük birkaç değeri sınayan ve en düşük asal sayı olan bir yöntemdir:</span><span class="sxs-lookup"><span data-stu-id="e54a3-157">The data driven test is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-csharp[Sample_TestCode](~/samples/snippets/core/testing/unit-testing-using-nunit/csharp/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="e54a3-158">Çalıştır `dotnet test`Ve bu testlerin iki başarısız.</span><span class="sxs-lookup"><span data-stu-id="e54a3-158">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="e54a3-159">Tüm testlerin geçmesi için, `if` `Main` *PrimeService.cs* dosyasındaki yöntemin başındaki yan tümceyi değiştirin:</span><span class="sxs-lookup"><span data-stu-id="e54a3-159">To make all of the tests pass, change the `if` clause at the beginning of the `Main` method in the *PrimeService.cs* file:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="e54a3-160">Ana kitaplığa daha fazla test, daha fazla teori ve daha fazla kod ekleyerek yinelemeye devam edin.</span><span class="sxs-lookup"><span data-stu-id="e54a3-160">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="e54a3-161">[Testlerin tamamlanmış sürümüne](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs) ve [kitaplığın tam uygulamasına](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs)sahipsiniz.</span><span class="sxs-lookup"><span data-stu-id="e54a3-161">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="e54a3-162">O kitaplık için küçük bir kitaplık ve bir dizi birim testi inşa ettin.</span><span class="sxs-lookup"><span data-stu-id="e54a3-162">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="e54a3-163">Yeni paketler ve testler eklemek normal iş akışının bir parçası olacak şekilde çözümü yapılandırdınız.</span><span class="sxs-lookup"><span data-stu-id="e54a3-163">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="e54a3-164">Zamanınızın ve çabanızın çoğunu uygulamanın hedeflerini çözmeye yoğunlaşmışsınız.</span><span class="sxs-lookup"><span data-stu-id="e54a3-164">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
