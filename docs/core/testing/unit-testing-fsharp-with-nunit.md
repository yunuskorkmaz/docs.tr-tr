---
title: Dotnet testi ve NUnit ile .NET Core'da F# testi
description: Dotnet testi ve NUnit kullanarak adım adım örnek bir çözüm oluşturma etkileşimli bir deneyim le .NET Core'da F# için birim test kavramlarını öğrenin.
author: rprouse
ms.date: 10/04/2018
dev_langs:
- fsharp
ms.openlocfilehash: 3347e5b90c31589e9a0f99ac0d9298927a717f56
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715441"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-nunit"></a><span data-ttu-id="985a2-103">Dotnet testi ve NUnit kullanarak .NET Core'daki F# kitaplıklarını test etme birimi</span><span class="sxs-lookup"><span data-stu-id="985a2-103">Unit testing F# libraries in .NET Core using dotnet test and NUnit</span></span>

<span data-ttu-id="985a2-104">Bu öğretici, birim test kavramlarını öğrenmek için adım adım örnek bir çözüm oluşturma etkileşimli bir deneyim sunar.</span><span class="sxs-lookup"><span data-stu-id="985a2-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="985a2-105">Önceden oluşturulmuş bir çözüm kullanarak öğreticiyi izlemeyi tercih ederseniz, başlamadan önce [örnek kodu görüntüleyin veya indirin.](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-nunit/)</span><span class="sxs-lookup"><span data-stu-id="985a2-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-nunit/) before you begin.</span></span> <span data-ttu-id="985a2-106">İndirme talimatları için [Örnekler ve Öğreticiler'e](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)bakın.</span><span class="sxs-lookup"><span data-stu-id="985a2-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="prerequisites"></a><span data-ttu-id="985a2-107">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="985a2-107">Prerequisites</span></span>

- <span data-ttu-id="985a2-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) veya sonraki sürümler.</span><span class="sxs-lookup"><span data-stu-id="985a2-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later versions.</span></span>
- <span data-ttu-id="985a2-109">Tercih ettiğiniz bir metin veya kod düzenleyicisi.</span><span class="sxs-lookup"><span data-stu-id="985a2-109">A text editor or code editor of your choice.</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="985a2-110">Kaynak proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="985a2-110">Creating the source project</span></span>

<span data-ttu-id="985a2-111">Bir kabuk penceresi açın.</span><span class="sxs-lookup"><span data-stu-id="985a2-111">Open a shell window.</span></span> <span data-ttu-id="985a2-112">Çözümü tutmak için *birim-test-fsharp adı* verilen bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="985a2-112">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="985a2-113">Bu yeni dizinin içinde, sınıf kitaplığı ve test projesi için yeni bir çözüm dosyası oluşturmak için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="985a2-113">Inside this new directory, run the following command to create a new solution file for the class library and the test project:</span></span>

```dotnetcli
dotnet new sln
```

<span data-ttu-id="985a2-114">Ardından, bir *MathService* dizini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="985a2-114">Next, create a *MathService* directory.</span></span> <span data-ttu-id="985a2-115">Aşağıdaki anahat şimdiye kadar dizin ve dosya yapısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="985a2-115">The following outline shows the directory and file structure so far:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="985a2-116">*MathService'i* geçerli dizini yapın ve kaynak projeyi oluşturmak için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="985a2-116">Make *MathService* the current directory and run the following command to create the source project:</span></span>

```dotnetcli
dotnet new classlib -lang "F#"
```

<span data-ttu-id="985a2-117">Matematik hizmetinin başarısız bir uygulamasını oluşturursunuz:</span><span class="sxs-lookup"><span data-stu-id="985a2-117">You create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="985a2-118">Dizin geri *birim-test-with-fsharp* dizin değiştirin.</span><span class="sxs-lookup"><span data-stu-id="985a2-118">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="985a2-119">Sınıf kitaplığı projesini çözüme eklemek için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="985a2-119">Run the following command to add the class library project to the solution:</span></span>

```dotnetcli
dotnet sln add .\MathService\MathService.fsproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="985a2-120">Test projesini oluşturma</span><span class="sxs-lookup"><span data-stu-id="985a2-120">Creating the test project</span></span>

<span data-ttu-id="985a2-121">Ardından *MathService.Tests* dizinini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="985a2-121">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="985a2-122">Aşağıdaki anahat dizin yapısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="985a2-122">The following outline shows the directory structure:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="985a2-123">*MathService.Tests* dizinini geçerli dizini oluşturun ve aşağıdaki komutu kullanarak yeni bir proje oluşturun:</span><span class="sxs-lookup"><span data-stu-id="985a2-123">Make the *MathService.Tests* directory the current directory and create a new project using the following command:</span></span>

```dotnetcli
dotnet new nunit -lang "F#"
```

<span data-ttu-id="985a2-124">Bu, test çerçevesi olarak NUnit kullanan bir test projesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="985a2-124">This creates a test project that uses NUnit as the test framework.</span></span> <span data-ttu-id="985a2-125">Oluşturulan şablon *MathServiceTests.fsproj*test koşucusu yapılandırır:</span><span class="sxs-lookup"><span data-stu-id="985a2-125">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

<span data-ttu-id="985a2-126">Test projesi, birim testleri oluşturmak ve çalıştırmak için diğer paketler gerektirir.</span><span class="sxs-lookup"><span data-stu-id="985a2-126">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="985a2-127">`dotnet new`önceki adımda NUnit ve NUnit test bağdaştırıcısı eklendi.</span><span class="sxs-lookup"><span data-stu-id="985a2-127">`dotnet new` in the previous step added NUnit and the NUnit test adapter.</span></span> <span data-ttu-id="985a2-128">Şimdi, `MathService` sınıf kitaplığını projeye başka bir bağımlılık olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="985a2-128">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="985a2-129">Komutu `dotnet add reference` kullanın:</span><span class="sxs-lookup"><span data-stu-id="985a2-129">Use the `dotnet add reference` command:</span></span>

```dotnetcli
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="985a2-130">Tüm dosyayı GitHub'daki [örnek deposunda](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="985a2-130">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="985a2-131">Aşağıdaki nihai çözüm düzenine sahipsiniz:</span><span class="sxs-lookup"><span data-stu-id="985a2-131">You have the following final solution layout:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
        Test Source Files
        MathService.Tests.fsproj
```

<span data-ttu-id="985a2-132">*Birim-test-with-fsharp* dizininde aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="985a2-132">Execute the following command in the *unit-testing-with-fsharp* directory:</span></span>

```dotnetcli
dotnet sln add .\MathService.Tests\MathService.Tests.fsproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="985a2-133">İlk testi oluşturma</span><span class="sxs-lookup"><span data-stu-id="985a2-133">Creating the first test</span></span>

<span data-ttu-id="985a2-134">Başarısız bir test yazarsın, geçer ve işlemi tekrarlarsın.</span><span class="sxs-lookup"><span data-stu-id="985a2-134">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="985a2-135">*UnitTest1.fs'yi* açın ve aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="985a2-135">Open *UnitTest1.fs* and add the following code:</span></span>

```fsharp
namespace MathService.Tests

open System
open NUnit.Framework
open MathService

[<TestFixture>]
type TestClass () =

    [<Test>]
    member this.TestMethodPassing() =
        Assert.True(true)

    [<Test>]
     member this.FailEveryTime() = Assert.True(false)
```

<span data-ttu-id="985a2-136">Öznitelik, `[<TestFixture>]` testleri içeren bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="985a2-136">The `[<TestFixture>]` attribute denotes a class that contains tests.</span></span> <span data-ttu-id="985a2-137">Öznitelik, `[<Test>]` test koşucusu tarafından çalıştırılabilen bir test yöntemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="985a2-137">The `[<Test>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="985a2-138">*Birim-test-with-fsharp* dizininden, testleri `dotnet test` ve sınıf kitaplığını oluşturmak ve testleri çalıştırmak için çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="985a2-138">From the *unit-testing-with-fsharp* directory, execute `dotnet test` to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="985a2-139">NUnit test koşucusu, testlerinizi çalıştırmak için program giriş noktasını içerir.</span><span class="sxs-lookup"><span data-stu-id="985a2-139">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="985a2-140">`dotnet test`oluşturduğunuz birim test projesini kullanarak test koşucusu başlatın.</span><span class="sxs-lookup"><span data-stu-id="985a2-140">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="985a2-141">Bu iki test, en temel geçen ve başarısız testleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="985a2-141">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="985a2-142">`My test`geçer ve `Fail every time` başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="985a2-142">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="985a2-143">Şimdi, `squaresOfOdds` yöntem için bir test oluşturun.</span><span class="sxs-lookup"><span data-stu-id="985a2-143">Now, create a test for the `squaresOfOdds` method.</span></span> <span data-ttu-id="985a2-144">Yöntem, `squaresOfOdds` giriş sırasının bir parçası olan tüm tek tamsayı değerlerinin karelerinin bir sırasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="985a2-144">The `squaresOfOdds` method returns a sequence of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="985a2-145">Tüm bu işlevleri aynı anda yazmaya çalışmak yerine, işlevselliği doğrulayan testleri yinelemeli olarak oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="985a2-145">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="985a2-146">Her test geçişini yapmak, yöntem için gerekli işlevselliği oluşturmak anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="985a2-146">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="985a2-147">Yazabileceğimiz en basit test, `squaresOfOdds` sonucun boş bir toplamdarık dizisi olması gereken tüm çift sayılarla aramaktır.</span><span class="sxs-lookup"><span data-stu-id="985a2-147">The simplest test we can write is to call `squaresOfOdds` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="985a2-148">İşte o test:</span><span class="sxs-lookup"><span data-stu-id="985a2-148">Here's that test:</span></span>

```fsharp
[<Test>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="985a2-149">`expected` Dizinin bir listeye dönüştürüldüğünü unutmayın.</span><span class="sxs-lookup"><span data-stu-id="985a2-149">Notice that the `expected` sequence has been converted to a list.</span></span> <span data-ttu-id="985a2-150">NUnit çerçevesi birçok standart .NET türüne dayanır.</span><span class="sxs-lookup"><span data-stu-id="985a2-150">The NUnit framework relies on many standard .NET types.</span></span> <span data-ttu-id="985a2-151">Bu bağımlılık, ortak arabiriminizin ve <xref:System.Collections.ICollection> beklenen <xref:System.Collections.IEnumerable>sonuçların değil, 'yi desteklediği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="985a2-151">That dependency means that your public interface and expected results support <xref:System.Collections.ICollection> rather than <xref:System.Collections.IEnumerable>.</span></span>

<span data-ttu-id="985a2-152">Testi çalıştırdığınızda, testinizin başarısız olduğunu görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="985a2-152">When you run the test, you see that your test fails.</span></span> <span data-ttu-id="985a2-153">Uygulamayı henüz oluşturmadın.</span><span class="sxs-lookup"><span data-stu-id="985a2-153">You haven't created the implementation yet.</span></span> <span data-ttu-id="985a2-154">MathService projenizde *Library.fs* sınıfında ki en basit kodu yazarak bu testi geçirin:</span><span class="sxs-lookup"><span data-stu-id="985a2-154">Make this test pass by writing the simplest code in the *Library.fs* class in your MathService project that works:</span></span>

```fsharp
let squaresOfOdds xs =
    Seq.empty<int>
```

<span data-ttu-id="985a2-155">*Birim-test-fsharp* dizininde, yeniden çalıştırın. `dotnet test`</span><span class="sxs-lookup"><span data-stu-id="985a2-155">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="985a2-156">Komut, `dotnet test` proje ve ardından `MathService.Tests` proje için bir yapı çalışır. `MathService`</span><span class="sxs-lookup"><span data-stu-id="985a2-156">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="985a2-157">Her iki projeyi de yaptıktan sonra, testlerinizi çalıştırAr.</span><span class="sxs-lookup"><span data-stu-id="985a2-157">After building both projects, it runs your tests.</span></span> <span data-ttu-id="985a2-158">Şimdi iki test geçti.</span><span class="sxs-lookup"><span data-stu-id="985a2-158">Two tests pass now.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="985a2-159">Gereksinimleri nama</span><span class="sxs-lookup"><span data-stu-id="985a2-159">Completing the requirements</span></span>

<span data-ttu-id="985a2-160">Artık bir test sınavını geçtiğine göre, daha fazla yazma nın zamanı.</span><span class="sxs-lookup"><span data-stu-id="985a2-160">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="985a2-161">Sonraki basit durum, tek sayısı `1`.</span><span class="sxs-lookup"><span data-stu-id="985a2-161">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="985a2-162">1'in karesi 1 olduğundan 1 sayısı daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="985a2-162">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="985a2-163">İşte bir sonraki test:</span><span class="sxs-lookup"><span data-stu-id="985a2-163">Here's that next test:</span></span>

```fsharp
[<Test>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="985a2-164">Yürütme `dotnet test` yeni test başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="985a2-164">Executing `dotnet test` fails the new test.</span></span> <span data-ttu-id="985a2-165">Bu yeni `squaresOfOdds` testi işlemek için yöntemi güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="985a2-165">You must update the `squaresOfOdds` method to handle this new test.</span></span> <span data-ttu-id="985a2-166">Bu testin geçmesi için tüm çift sayıları sıranın dışına filtrelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="985a2-166">You must filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="985a2-167">Bunu küçük bir filtre işlevi yazarak `Seq.filter`ve şu ları kullanarak yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="985a2-167">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

<span data-ttu-id="985a2-168">Çağrıya dikkat `Seq.toList`edin.</span><span class="sxs-lookup"><span data-stu-id="985a2-168">Notice the call to `Seq.toList`.</span></span> <span data-ttu-id="985a2-169">Bu, <xref:System.Collections.ICollection> arabirimi uygulayan bir liste oluşturur.</span><span class="sxs-lookup"><span data-stu-id="985a2-169">That creates a list, which implements the <xref:System.Collections.ICollection> interface.</span></span>

<span data-ttu-id="985a2-170">Daha bir adım daha var: Tek sayıların her birini karelemek.</span><span class="sxs-lookup"><span data-stu-id="985a2-170">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="985a2-171">Yeni bir test yazarak başlayın:</span><span class="sxs-lookup"><span data-stu-id="985a2-171">Start by writing a new test:</span></span>

```fsharp
[<Test>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="985a2-172">Her tek sayının karesini hesaplamak için filtreuygulanmış sırayı bir harita işlemi yle borulandırarak testi düzeltebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="985a2-172">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
```

<span data-ttu-id="985a2-173">O kitaplık için küçük bir kitaplık ve bir dizi birim testi inşa ettin.</span><span class="sxs-lookup"><span data-stu-id="985a2-173">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="985a2-174">Yeni paketler ve testler eklemek normal iş akışının bir parçası olacak şekilde çözümü yapılandırdınız.</span><span class="sxs-lookup"><span data-stu-id="985a2-174">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="985a2-175">Zamanınızın ve çabanızın çoğunu uygulamanın hedeflerini çözmeye yoğunlaşmışsınız.</span><span class="sxs-lookup"><span data-stu-id="985a2-175">You've concentrated most of your time and effort on solving the goals of the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="985a2-176">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="985a2-176">See also</span></span>

- [<span data-ttu-id="985a2-177">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="985a2-177">dotnet add reference</span></span>](../tools/dotnet-add-reference.md)
- [<span data-ttu-id="985a2-178">dotnet test</span><span class="sxs-lookup"><span data-stu-id="985a2-178">dotnet test</span></span>](../tools/dotnet-test.md)
