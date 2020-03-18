---
title: Dotnet testi ve MSTest ile .NET Core'da F# testi
description: Dotnet testi ve MSTest kullanarak adım adım örnek bir çözüm oluşturma etkileşimli bir deneyim le .NET Core'da F# için birim test kavramlarını öğrenin.
author: billwagner
ms.author: wiwagn
ms.date: 08/30/2017
ms.openlocfilehash: a685ed8a56393fb6e1c1b9400f0ed4bcef15f9b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714271"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-mstest"></a><span data-ttu-id="bdcd3-103">Dotnet testi ve MSTest kullanarak .NET Core'daki F# kitaplıklarını test etme birimi</span><span class="sxs-lookup"><span data-stu-id="bdcd3-103">Unit testing F# libraries in .NET Core using dotnet test and MSTest</span></span>

<span data-ttu-id="bdcd3-104">Bu öğretici, birim test kavramlarını öğrenmek için adım adım örnek bir çözüm oluşturma etkileşimli bir deneyim sunar.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="bdcd3-105">Önceden oluşturulmuş bir çözüm kullanarak öğreticiyi izlemeyi tercih ederseniz, başlamadan önce [örnek kodu görüntüleyin veya indirin.](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-mstest/)</span><span class="sxs-lookup"><span data-stu-id="bdcd3-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-mstest/) before you begin.</span></span> <span data-ttu-id="bdcd3-106">İndirme talimatları için [Örnekler ve Öğreticiler'e](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)bakın.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="creating-the-source-project"></a><span data-ttu-id="bdcd3-107">Kaynak proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="bdcd3-107">Creating the source project</span></span>

<span data-ttu-id="bdcd3-108">Bir kabuk penceresi açın.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-108">Open a shell window.</span></span> <span data-ttu-id="bdcd3-109">Çözümü tutmak için *birim-test-fsharp adı* verilen bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-109">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="bdcd3-110">Bu yeni dizinin içinde, yeni bir çözüm oluşturmak için çalıştırın. `dotnet new sln`</span><span class="sxs-lookup"><span data-stu-id="bdcd3-110">Inside this new directory, run `dotnet new sln` to create a new solution.</span></span> <span data-ttu-id="bdcd3-111">Bu, hem sınıf kitaplığını hem de birim test projesini yönetmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-111">This makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="bdcd3-112">Çözüm dizininin içinde bir *MathService* dizini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-112">Inside the solution directory, create a *MathService* directory.</span></span> <span data-ttu-id="bdcd3-113">Dizin ve dosya yapısı şimdiye kadar aşağıda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="bdcd3-113">The directory and file structure thus far is shown below:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="bdcd3-114">*MathService'i* geçerli dizini `dotnet new classlib -lang "F#"` yapın ve kaynak projeyi oluşturmak için çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-114">Make *MathService* the current directory and run `dotnet new classlib -lang "F#"` to create the source project.</span></span>  <span data-ttu-id="bdcd3-115">Matematik hizmetinin başarısız bir uygulamasını oluşturursunuz:</span><span class="sxs-lookup"><span data-stu-id="bdcd3-115">You'll create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="bdcd3-116">Dizin geri *birim-test-with-fsharp* dizin değiştirin.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-116">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="bdcd3-117">Sınıf `dotnet sln add .\MathService\MathService.fsproj` kitaplığı projesini çözüme eklemek için çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-117">Run `dotnet sln add .\MathService\MathService.fsproj` to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="bdcd3-118">Test projesini oluşturma</span><span class="sxs-lookup"><span data-stu-id="bdcd3-118">Creating the test project</span></span>

<span data-ttu-id="bdcd3-119">Ardından *MathService.Tests* dizinini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-119">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="bdcd3-120">Aşağıdaki anahat dizin yapısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="bdcd3-120">The following outline shows the directory structure:</span></span>

```console
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="bdcd3-121">*MathService.Tests* dizinini geçerli dizini oluşturun ve yeni `dotnet new mstest -lang "F#"`bir proje oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-121">Make the *MathService.Tests* directory the current directory and create a new project using `dotnet new mstest -lang "F#"`.</span></span> <span data-ttu-id="bdcd3-122">Bu, test çerçevesi olarak MSTest kullanan bir test projesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-122">This creates a test project that uses MSTest as the test framework.</span></span> <span data-ttu-id="bdcd3-123">Oluşturulan şablon *MathServiceTests.fsproj*test koşucusu yapılandırır:</span><span class="sxs-lookup"><span data-stu-id="bdcd3-123">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

<span data-ttu-id="bdcd3-124">Test projesi, birim testleri oluşturmak ve çalıştırmak için diğer paketler gerektirir.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-124">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="bdcd3-125">`dotnet new`önceki adımda MSTest ve MSTest runner eklendi.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-125">`dotnet new` in the previous step added MSTest and the MSTest runner.</span></span> <span data-ttu-id="bdcd3-126">Şimdi, `MathService` sınıf kitaplığını projeye başka bir bağımlılık olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-126">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="bdcd3-127">Komutu `dotnet add reference` kullanın:</span><span class="sxs-lookup"><span data-stu-id="bdcd3-127">Use the `dotnet add reference` command:</span></span>

```dotnetcli
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="bdcd3-128">Tüm dosyayı GitHub'daki [örnek deposunda](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-128">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="bdcd3-129">Aşağıdaki nihai çözüm düzenine sahipsiniz:</span><span class="sxs-lookup"><span data-stu-id="bdcd3-129">You have the following final solution layout:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
        Test Source Files
        MathServiceTests.fsproj
```

<span data-ttu-id="bdcd3-130">`dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` *Birim-test-with-fsharp* dizininde yürütün.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-130">Execute `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` in the *unit-testing-with-fsharp* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="bdcd3-131">İlk testi oluşturma</span><span class="sxs-lookup"><span data-stu-id="bdcd3-131">Creating the first test</span></span>

<span data-ttu-id="bdcd3-132">Başarısız bir test yazarsın, geçer ve işlemi tekrarlarsın.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-132">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="bdcd3-133">*Tests.fs'yi* açın ve aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bdcd3-133">Open *Tests.fs* and add the following code:</span></span>

```fsharp
namespace MathService.Tests

open System
open Microsoft.VisualStudio.TestTools.UnitTesting
open MathService

[<TestClass>]
type TestClass () =

    [<TestMethod>]
    member this.TestMethodPassing() =
        Assert.IsTrue(true)

    [<TestMethod>]
     member this.FailEveryTime() = Assert.IsTrue(false)
```

<span data-ttu-id="bdcd3-134">Öznitelik, `[<TestClass>]` testleri içeren bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-134">The `[<TestClass>]` attribute denotes a class that contains tests.</span></span> <span data-ttu-id="bdcd3-135">Öznitelik, `[<TestMethod>]` test koşucusu tarafından çalıştırılabilen bir test yöntemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-135">The `[<TestMethod>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="bdcd3-136">*Birim-test-with-fsharp* dizininden, testleri `dotnet test` ve sınıf kitaplığını oluşturmak ve testleri çalıştırmak için çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-136">From the *unit-testing-with-fsharp* directory, execute `dotnet test` to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="bdcd3-137">MSTest test koşucusu, testlerinizi çalıştırmak için program giriş noktasını içerir.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-137">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="bdcd3-138">`dotnet test`oluşturduğunuz birim test projesini kullanarak test koşucusu başlatın.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-138">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="bdcd3-139">Bu iki test, en temel geçen ve başarısız testleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-139">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="bdcd3-140">`My test`geçer ve `Fail every time` başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-140">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="bdcd3-141">Şimdi, `squaresOfOdds` yöntem için bir test oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-141">Now, create a test for the `squaresOfOdds` method.</span></span> <span data-ttu-id="bdcd3-142">Yöntem, `squaresOfOdds` giriş sırasının bir parçası olan tüm tek tamsayı değerlerinin karelerinin listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-142">The `squaresOfOdds` method returns a list of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="bdcd3-143">Tüm bu işlevleri aynı anda yazmaya çalışmak yerine, işlevselliği doğrulayan testleri yinelemeli olarak oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-143">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="bdcd3-144">Her test geçişini yapmak, yöntem için gerekli işlevselliği oluşturmak anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-144">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="bdcd3-145">Yazabileceğimiz en basit test, `squaresOfOdds` sonucun boş bir toplamdarık dizisi olması gereken tüm çift sayılarla aramaktır.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-145">The simplest test we can write is to call `squaresOfOdds` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="bdcd3-146">İşte o test:</span><span class="sxs-lookup"><span data-stu-id="bdcd3-146">Here's that test:</span></span>

```fsharp
[<TestMethod>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int> |> Seq.toList
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.AreEqual(expected, actual)
```

<span data-ttu-id="bdcd3-147">`expected` Dizinin bir listeye dönüştürüldüğünü unutmayın.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-147">Notice that the `expected` sequence has been converted to a list.</span></span> <span data-ttu-id="bdcd3-148">MSTest kitaplığı birçok standart .NET türüne dayanır.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-148">The MSTest library relies on many standard .NET types.</span></span> <span data-ttu-id="bdcd3-149">Bu bağımlılık, ortak arabiriminizin ve <xref:System.Collections.ICollection> beklenen <xref:System.Collections.IEnumerable>sonuçların değil, 'yi desteklediği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-149">That dependency means that your public interface and expected results support <xref:System.Collections.ICollection> rather than <xref:System.Collections.IEnumerable>.</span></span>

<span data-ttu-id="bdcd3-150">Testi çalıştırdığınızda, testinizin başarısız olduğunu görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-150">When you run the test, you see that your test fails.</span></span> <span data-ttu-id="bdcd3-151">Uygulamayı henüz oluşturmadın.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-151">You haven't created the implementation yet.</span></span> <span data-ttu-id="bdcd3-152">Bu testin çalışmasını sağlayan `Mathservice` sınıftaki en basit kodu yazarak geçmesini sağla:</span><span class="sxs-lookup"><span data-stu-id="bdcd3-152">Make this test pass by writing the simplest code in the `Mathservice` class that works:</span></span>

```fsharp
let squaresOfOdds xs =
    Seq.empty<int> |> Seq.toList
```

<span data-ttu-id="bdcd3-153">*Birim-test-fsharp* dizininde, yeniden çalıştırın. `dotnet test`</span><span class="sxs-lookup"><span data-stu-id="bdcd3-153">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="bdcd3-154">Komut, `dotnet test` proje ve ardından `MathService.Tests` proje için bir yapı çalışır. `MathService`</span><span class="sxs-lookup"><span data-stu-id="bdcd3-154">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="bdcd3-155">Her iki projeyi de yaptıktan sonra, bu tek testi çalıştırAr.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-155">After building both projects, it runs this single test.</span></span> <span data-ttu-id="bdcd3-156">Geçiyor.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-156">It passes.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="bdcd3-157">Gereksinimleri nama</span><span class="sxs-lookup"><span data-stu-id="bdcd3-157">Completing the requirements</span></span>

<span data-ttu-id="bdcd3-158">Artık bir test sınavını geçtiğine göre, daha fazla yazma nın zamanı.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-158">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="bdcd3-159">Sonraki basit durum, tek sayısı `1`.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-159">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="bdcd3-160">1'in karesi 1 olduğundan 1 sayısı daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-160">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="bdcd3-161">İşte bir sonraki test:</span><span class="sxs-lookup"><span data-stu-id="bdcd3-161">Here's that next test:</span></span>

```fsharp
[<TestMethod>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.AreEqual(expected, actual)
```

<span data-ttu-id="bdcd3-162">Yürütme `dotnet test` yeni test başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-162">Executing `dotnet test` fails the new test.</span></span> <span data-ttu-id="bdcd3-163">Bu yeni `squaresOfOdds` testi işlemek için yöntemi güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-163">You must update the `squaresOfOdds` method to handle this new test.</span></span> <span data-ttu-id="bdcd3-164">Bu testin geçmesi için tüm çift sayıları sıranın dışına filtrelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-164">You must filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="bdcd3-165">Bunu küçük bir filtre işlevi yazarak `Seq.filter`ve şu ları kullanarak yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bdcd3-165">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd |> Seq.toList
```

<span data-ttu-id="bdcd3-166">Çağrıya dikkat `Seq.toList`edin.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-166">Notice the call to `Seq.toList`.</span></span> <span data-ttu-id="bdcd3-167">Bu, <xref:System.Collections.ICollection> arabirimi uygulayan bir liste oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-167">That creates a list, which implements the <xref:System.Collections.ICollection> interface.</span></span>

<span data-ttu-id="bdcd3-168">Daha bir adım daha var: Tek sayıların her birini karelemek.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-168">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="bdcd3-169">Yeni bir test yazarak başlayın:</span><span class="sxs-lookup"><span data-stu-id="bdcd3-169">Start by writing a new test:</span></span>

```fsharp
[<TestMethod>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.AreEqual(expected, actual)
```

<span data-ttu-id="bdcd3-170">Her tek sayının karesini hesaplamak için filtreuygulanmış sırayı bir harita işlemi yle borulandırarak testi düzeltebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bdcd3-170">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
    |> Seq.toList
```

<span data-ttu-id="bdcd3-171">O kitaplık için küçük bir kitaplık ve bir dizi birim testi inşa ettin.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-171">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="bdcd3-172">Yeni paketler ve testler eklemek normal iş akışının bir parçası olacak şekilde çözümü yapılandırdınız.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-172">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="bdcd3-173">Zamanınızın ve çabanızın çoğunu uygulamanın hedeflerini çözmeye yoğunlaşmışsınız.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-173">You've concentrated most of your time and effort on solving the goals of the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="bdcd3-174">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bdcd3-174">See also</span></span>

- [<span data-ttu-id="bdcd3-175">dotnet new</span><span class="sxs-lookup"><span data-stu-id="bdcd3-175">dotnet new</span></span>](../tools/dotnet-new.md)
- [<span data-ttu-id="bdcd3-176">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="bdcd3-176">dotnet sln</span></span>](../tools/dotnet-sln.md)
- [<span data-ttu-id="bdcd3-177">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="bdcd3-177">dotnet add reference</span></span>](../tools/dotnet-add-reference.md)
- [<span data-ttu-id="bdcd3-178">dotnet test</span><span class="sxs-lookup"><span data-stu-id="bdcd3-178">dotnet test</span></span>](../tools/dotnet-test.md)
