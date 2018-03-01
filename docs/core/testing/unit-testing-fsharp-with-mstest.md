---
title: "Birim F # kitaplığı .NET dotnet test ve mstest'i kullanarak çekirdek testi"
description: "Birim testi kavramları F # .NET Core için adım adım örnek çözüm oluşturma bir etkileşimli deneyimler aracılığıyla öğrenmeniz dotnet test ve mstest'i kullanarak."
author: billwagner
ms.author: wiwagn
ms.date: 08/30/2017
ms.topic: article
dev_langs:
- fsharp
ms.prod: .net-core
ms.workload:
- dotnetcore
ms.openlocfilehash: 6dc5388f8e5645530cdd12986a9e1e53e4115c9a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-mstest"></a><span data-ttu-id="e3979-103">Birim F # kitaplığı .NET dotnet test ve mstest'i kullanarak çekirdek testi</span><span class="sxs-lookup"><span data-stu-id="e3979-103">Unit testing F# libraries in .NET Core using dotnet test and MSTest</span></span>

<span data-ttu-id="e3979-104">Bu öğretici birim testi kavramlarını öğrenmek için adım adım örnek çözüm oluşturma etkileşimli bir deneyim gösterir.</span><span class="sxs-lookup"><span data-stu-id="e3979-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="e3979-105">Önceden oluşturulmuş bir çözümü kullanarak öğreticiyi izleyin tercih ediyorsanız [görüntülemek veya karşıdan örnek kod](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-with-fsharp-mstest/) başlamadan önce.</span><span class="sxs-lookup"><span data-stu-id="e3979-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-with-fsharp-mstest/) before you begin.</span></span> <span data-ttu-id="e3979-106">Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="e3979-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="e3979-107">Kaynak projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="e3979-107">Creating the source project</span></span>

<span data-ttu-id="e3979-108">Kabuk penceresini açın.</span><span class="sxs-lookup"><span data-stu-id="e3979-108">Open a shell window.</span></span> <span data-ttu-id="e3979-109">Adlı bir dizin oluşturun *birim-test etme-ile-fsharp* çözümü tutmak için.</span><span class="sxs-lookup"><span data-stu-id="e3979-109">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="e3979-110">Bu yeni dizin içinde çalıştırmak [ `dotnet new sln` ](../tools/dotnet-new.md) yeni bir çözüm oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="e3979-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="e3979-111">Bu sınıf kitaplığı ve birim testi projesi yönetmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="e3979-111">This makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="e3979-112">Çözüm dizini içinde oluşturmak bir *MathService* dizini.</span><span class="sxs-lookup"><span data-stu-id="e3979-112">Inside the solution directory, create a *MathService* directory.</span></span> <span data-ttu-id="e3979-113">Dizin ve dosya yapısı bugüne kadarki aşağıda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="e3979-113">The directory and file structure thus far is shown below:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="e3979-114">Olun *MathService* geçerli dizin ve çalışma [ `dotnet new classlib -lang F#` ](../tools/dotnet-new.md) kaynak projesi oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="e3979-114">Make *MathService* the current directory and run [`dotnet new classlib -lang F#`](../tools/dotnet-new.md) to create the source project.</span></span>  <span data-ttu-id="e3979-115">Teste dayalı geliştirme (TDD) kullanmak için başarısız olan uygulama matematik hizmetinin oluşturursunuz:</span><span class="sxs-lookup"><span data-stu-id="e3979-115">To use test-driven development (TDD), you'll create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let sumOfSquares xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="e3979-116">Dizin geri değişiklik *birim-test etme-ile-fsharp* dizini.</span><span class="sxs-lookup"><span data-stu-id="e3979-116">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="e3979-117">Çalıştırma [ `dotnet sln add .\MathService\MathService.fsproj` ](../tools/dotnet-sln.md) sınıf kitaplığı proje çözüme eklemek için.</span><span class="sxs-lookup"><span data-stu-id="e3979-117">Run [`dotnet sln add .\MathService\MathService.fsproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="e3979-118">Test projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="e3979-118">Creating the test project</span></span>

<span data-ttu-id="e3979-119">Ardından, oluşturun *MathService.Tests* dizini.</span><span class="sxs-lookup"><span data-stu-id="e3979-119">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="e3979-120">Aşağıdaki anahat dizin yapısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="e3979-120">The following outline shows the directory structure:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="e3979-121">Olun *MathService.Tests* dizine geçerli ve kullanarak yeni bir proje oluşturun [ `dotnet new mstest -lang F#` ](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="e3979-121">Make the *MathService.Tests* directory the current directory and create a new project using [`dotnet new mstest -lang F#`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="e3979-122">Mstest'i test çerçevesi kullanan bir test projesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e3979-122">This creates a test project that uses MSTest as the test framework.</span></span> <span data-ttu-id="e3979-123">Test Çalıştırıcısı'nda oluşturulan şablon yapılandırır *MathServiceTests.fsproj*:</span><span class="sxs-lookup"><span data-stu-id="e3979-123">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

<span data-ttu-id="e3979-124">Test projesi oluşturmak ve birim testleri çalıştırmak için diğer paketleri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e3979-124">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="e3979-125">`dotnet new`Önceki adımda mstest'i ve mstest'i Çalıştırıcısı eklendi.</span><span class="sxs-lookup"><span data-stu-id="e3979-125">`dotnet new` in the previous step added MSTest and the MSTest runner.</span></span> <span data-ttu-id="e3979-126">Şimdi, ekleyin `MathService` sınıf kitaplığı proje için başka bir bağımlılık olarak.</span><span class="sxs-lookup"><span data-stu-id="e3979-126">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="e3979-127">Kullanım [ `dotnet add reference` ](../tools/dotnet-add-reference.md) komutu:</span><span class="sxs-lookup"><span data-stu-id="e3979-127">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="e3979-128">Tüm dosyasında görebilirsiniz [örnekleri deposu](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) github'da.</span><span class="sxs-lookup"><span data-stu-id="e3979-128">You can see the entire file in the [samples repository](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="e3979-129">Aşağıdaki nihai çözüm düzeni vardır:</span><span class="sxs-lookup"><span data-stu-id="e3979-129">You have the following final solution layout:</span></span>

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

<span data-ttu-id="e3979-130">Yürütme [ `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` ](../tools/dotnet-sln.md) içinde *birim-test etme-ile-fsharp* dizini.</span><span class="sxs-lookup"><span data-stu-id="e3979-130">Execute [`dotnet sln add .\MathService.Tests\MathService.Tests.fsproj`](../tools/dotnet-sln.md) in the *unit-testing-with-fsharp* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="e3979-131">İlk testi oluşturma</span><span class="sxs-lookup"><span data-stu-id="e3979-131">Creating the first test</span></span>

<span data-ttu-id="e3979-132">TDD yaklaşım geçirmek kolaylaştırarak ve süreci tekrarlayarak yazma bir başarısız test için çağırır.</span><span class="sxs-lookup"><span data-stu-id="e3979-132">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="e3979-133">Açık *Tests.fs* ve aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e3979-133">Open *Tests.fs* and add the following code:</span></span>

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

<span data-ttu-id="e3979-134">`[<TestClass>]` Özniteliği testleri içeren bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="e3979-134">The `[<TestClass>]` attribute denotes a class that contains tests.</span></span> <span data-ttu-id="e3979-135">`[<TestMethod>]` Özniteliği test Çalıştırıcısı tarafından çalıştırılan test yöntemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e3979-135">The `[<TestMethod>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="e3979-136">Gelen *birim-test etme-ile-fsharp* dizin, yürütme [ `dotnet test` ](../tools/dotnet-test.md) testleri ve sınıf kitaplığı oluşturmak ve ardından testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e3979-136">From the *unit-testing-with-fsharp* directory, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="e3979-137">Mstest'i test Çalıştırıcısı testleri çalıştırmak için program giriş noktası içerir.</span><span class="sxs-lookup"><span data-stu-id="e3979-137">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="e3979-138">`dotnet test`oluşturduğunuz birim testi projesi kullanarak test Çalıştırıcısı başlatır.</span><span class="sxs-lookup"><span data-stu-id="e3979-138">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="e3979-139">Bu iki testleri en temel geçirme ve testleri başarısız gösterir.</span><span class="sxs-lookup"><span data-stu-id="e3979-139">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="e3979-140">`My test`geçirir, ve `Fail every time` başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="e3979-140">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="e3979-141">Şimdi, test için oluşturma `sumOfSquares` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e3979-141">Now, create a test for the `sumOfSquares` method.</span></span> <span data-ttu-id="e3979-142">`sumOfSquares` Yöntemi Giriş dizisinin bir parçası olan tüm tek sayılı tamsayı değerleri kareleri toplamını döndürür.</span><span class="sxs-lookup"><span data-stu-id="e3979-142">The `sumOfSquares` method returns the sum of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="e3979-143">Bu işlevlerin tümüne tek seferde yazmaya çalışırken yerine işlevselliğini doğrulama testleri tekrarlayarak oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e3979-143">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="e3979-144">Yöntemi için gerekli işlevselliği oluşturma anlamına gelir geçirmek her test yapma.</span><span class="sxs-lookup"><span data-stu-id="e3979-144">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="e3979-145">Biz yazabilirler basit test çağırmaktır `sumOfSquares` tüm çift numaraları, burada sonucu olmalıdır boş bir tam sayı dizisidir.</span><span class="sxs-lookup"><span data-stu-id="e3979-145">The simplest test we can write is to call `sumOfSquares` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="e3979-146">Bu test şöyledir:</span><span class="sxs-lookup"><span data-stu-id="e3979-146">Here's that test:</span></span>

```fsharp
[<TestMethod>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int> |> Seq.toList
    let actual = MyMath.sumOfSquares [2; 4; 6; 8; 10]
    Assert.AreEqual(expected, actual)
```

<span data-ttu-id="e3979-147">Dikkat `expected` sıralı liste dönüştürülmüş.</span><span class="sxs-lookup"><span data-stu-id="e3979-147">Notice that the `expected` sequence has been converted to a list.</span></span> <span data-ttu-id="e3979-148">Mstest'i kitaplığı birçok standart .NET türlerine dayanır.</span><span class="sxs-lookup"><span data-stu-id="e3979-148">The MSTest library relies on many standard .NET types.</span></span> <span data-ttu-id="e3979-149">Destek bağımlılık ortak arabirimi anlamına gelir ve beklenen sonuçları <xref:System.Collections.ICollection> yerine <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="e3979-149">That dependency means that your public interface and expected results support <xref:System.Collections.ICollection> rather than <xref:System.Collections.IEnumerable>.</span></span>

<span data-ttu-id="e3979-150">Testi çalıştırdığınızda, testiniz başarısız olduğunu görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="e3979-150">When you run the test, you see that your test fails.</span></span> <span data-ttu-id="e3979-151">Uygulama henüz oluşturmadınız.</span><span class="sxs-lookup"><span data-stu-id="e3979-151">You haven't created the implementation yet.</span></span> <span data-ttu-id="e3979-152">Bu test basit kod yazarken yapmasına `Mathservice` çalışır sınıfı:</span><span class="sxs-lookup"><span data-stu-id="e3979-152">Make this test by writing the simplest code in the `Mathservice` class that works:</span></span>

```csharp
let sumOfSquares xs =
    Seq.empty<int> |> Seq.toList
```

<span data-ttu-id="e3979-153">İçinde *birim-test etme-ile-fsharp* çalışması dizini `dotnet test` yeniden.</span><span class="sxs-lookup"><span data-stu-id="e3979-153">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="e3979-154">`dotnet test` Komutu çalıştıran bir yapı `MathService` proje ve ardından `MathService.Tests` projesi.</span><span class="sxs-lookup"><span data-stu-id="e3979-154">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="e3979-155">Her iki proje oluşturduktan sonra bu tek bir test çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="e3979-155">After building both projects, it runs this single test.</span></span> <span data-ttu-id="e3979-156">Bunu geçirir.</span><span class="sxs-lookup"><span data-stu-id="e3979-156">It passes.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="e3979-157">Gereksinimleri Tamamlanıyor</span><span class="sxs-lookup"><span data-stu-id="e3979-157">Completing the requirements</span></span>

<span data-ttu-id="e3979-158">Bir test geçirmek yapmış olduğunuz, daha fazla yazma zamanı geldi.</span><span class="sxs-lookup"><span data-stu-id="e3979-158">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="e3979-159">Sonraki basit bir durumda, yalnızca tek sayı olan bir sıra ile çalışır `1`.</span><span class="sxs-lookup"><span data-stu-id="e3979-159">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="e3979-160">1 sayısı 1'in Kare 1 olduğundan daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="e3979-160">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="e3979-161">Sonraki test şöyledir:</span><span class="sxs-lookup"><span data-stu-id="e3979-161">Here's that next test:</span></span>

```fsharp
[<TestMethod>]
member public this.SumOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.sumOfSquares [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.AreEqual(expected, actual)
```

<span data-ttu-id="e3979-162">Yürütme `dotnet test` yeni sınama başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="e3979-162">Executing `dotnet test` fails the new test.</span></span> <span data-ttu-id="e3979-163">Güncelleştirmeniz gerekir `sumOfSquares` bu yeni test işlemek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="e3979-163">You must update the `sumOfSquares` method to handle this new test.</span></span> <span data-ttu-id="e3979-164">Geçirmek bu testi yapmak için sıra dışında tüm çift sayıları filtre gerekir.</span><span class="sxs-lookup"><span data-stu-id="e3979-164">You must filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="e3979-165">Küçük filtre işlevi yazma ve kullanarak bunu, `Seq.filter`:</span><span class="sxs-lookup"><span data-stu-id="e3979-165">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let sumOfSquares xs =
    xs
    |> Seq.filter isOdd |> Seq.toList
```

<span data-ttu-id="e3979-166">Çağrısını fark `Seq.toList`.</span><span class="sxs-lookup"><span data-stu-id="e3979-166">Notice the call to `Seq.toList`.</span></span> <span data-ttu-id="e3979-167">Arabirimini uygulayan bir liste oluşturur <xref:System.Collections.ICollection> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="e3979-167">That creates a list, which implements the <xref:System.Collections.ICollection> interface.</span></span>

<span data-ttu-id="e3979-168">Gitmek için bir adım daha vardır: her tek sayıların karesini.</span><span class="sxs-lookup"><span data-stu-id="e3979-168">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="e3979-169">Yeni bir test yazarak başlatın:</span><span class="sxs-lookup"><span data-stu-id="e3979-169">Start by writing a new test:</span></span>

```fsharp
[<TestMethod>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.sumOfSquares [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.AreEqual(expected, actual)
```

<span data-ttu-id="e3979-170">Her tek sayı kare hesaplamak için eşleme işlemi aracılığıyla filtrelenmiş dizisi cmdlet'ine yönelterek test düzeltebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e3979-170">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let sumOfSquares xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
    |> Seq.toList
```

<span data-ttu-id="e3979-171">Küçük bir kitaplığı ve bu kitaplık için birim testleri kümesini temel aldık.</span><span class="sxs-lookup"><span data-stu-id="e3979-171">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="e3979-172">Böylece yeni paketleri ekleme çözümü yapılandırılmış ve testleri normal iş akışı bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="e3979-172">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="e3979-173">Çoğu zaman ve çaba uygulama amaçlarını çözme üzerinde yoğunlaşmıştır.</span><span class="sxs-lookup"><span data-stu-id="e3979-173">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
