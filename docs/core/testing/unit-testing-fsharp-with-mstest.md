---
title: Birim testi F# .NET core'da dotnet testi ve MSTest ile
description: Birim test kavramlarını öğrenin F# dotnet testi ve MSTest, adım adım örnek çözüm oluşturma etkileşimli deneyim aracılığıyla .NET Core kullanarak.
author: billwagner
ms.author: wiwagn
ms.date: 08/30/2017
dev_langs:
- fsharp
ms.custom: seodec18
ms.openlocfilehash: 1765c16cb55857b83a8206ae97327d0fd2809019
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56747498"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-mstest"></a><span data-ttu-id="99a36-103">Birim testi F# dotnet testi ve MSTest kullanarak .NET core'da kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="99a36-103">Unit testing F# libraries in .NET Core using dotnet test and MSTest</span></span>

<span data-ttu-id="99a36-104">Bu öğretici örnek bir çözüm birim testi kavramlarını öğrenmek için adım adım oluşturmaya etkileşimli deneyim gösterir.</span><span class="sxs-lookup"><span data-stu-id="99a36-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="99a36-105">Önceden oluşturulmuş bir çözümü kullanarak öğreticiyi uygulamak isterseniz [görüntülemek veya örnek kodu indirdikten](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-mstest/) başlamadan önce.</span><span class="sxs-lookup"><span data-stu-id="99a36-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-mstest/) before you begin.</span></span> <span data-ttu-id="99a36-106">Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="99a36-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="99a36-107">Kaynak proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="99a36-107">Creating the source project</span></span>

<span data-ttu-id="99a36-108">Shell penceresini açın.</span><span class="sxs-lookup"><span data-stu-id="99a36-108">Open a shell window.</span></span> <span data-ttu-id="99a36-109">Adlı bir dizin oluşturun *birim-test-ile-fsharp* çözüm tutacak.</span><span class="sxs-lookup"><span data-stu-id="99a36-109">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="99a36-110">Bu yeni dizin içinde çalıştırma [ `dotnet new sln` ](../tools/dotnet-new.md) yeni bir çözüm oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="99a36-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="99a36-111">Bu, hem sınıf kitaplığı ve birim testi projesi yönetmenizi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="99a36-111">This makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="99a36-112">Çözüm dizini içinde bir *MathService* dizin.</span><span class="sxs-lookup"><span data-stu-id="99a36-112">Inside the solution directory, create a *MathService* directory.</span></span> <span data-ttu-id="99a36-113">Dizin ve dosya yapısı, şimdiye kadarki aşağıda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="99a36-113">The directory and file structure thus far is shown below:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="99a36-114">Olun *MathService* geçerli dizin ve çalışma [ `dotnet new classlib -lang F#` ](../tools/dotnet-new.md) kaynak proje oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="99a36-114">Make *MathService* the current directory and run [`dotnet new classlib -lang F#`](../tools/dotnet-new.md) to create the source project.</span></span>  <span data-ttu-id="99a36-115">Matematik hizmet başarısız uyarlamasını oluşturacaksınız:</span><span class="sxs-lookup"><span data-stu-id="99a36-115">You'll create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="99a36-116">Dizine dön değişiklik *birim-test-ile-fsharp* dizin.</span><span class="sxs-lookup"><span data-stu-id="99a36-116">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="99a36-117">Çalıştırma [ `dotnet sln add .\MathService\MathService.fsproj` ](../tools/dotnet-sln.md) sınıf kitaplığı projesi çözüme eklemek için.</span><span class="sxs-lookup"><span data-stu-id="99a36-117">Run [`dotnet sln add .\MathService\MathService.fsproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="99a36-118">Test projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="99a36-118">Creating the test project</span></span>

<span data-ttu-id="99a36-119">Ardından, oluşturma *MathService.Tests* dizin.</span><span class="sxs-lookup"><span data-stu-id="99a36-119">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="99a36-120">Ana hat aşağıdaki dizin yapısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="99a36-120">The following outline shows the directory structure:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="99a36-121">Olun *MathService.Tests* dizini geçerli dizin ve kullanarak yeni bir proje oluşturma [ `dotnet new mstest -lang F#` ](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="99a36-121">Make the *MathService.Tests* directory the current directory and create a new project using [`dotnet new mstest -lang F#`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="99a36-122">Bu, MSTest test çerçevesi kullanan bir test projesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="99a36-122">This creates a test project that uses MSTest as the test framework.</span></span> <span data-ttu-id="99a36-123">Test Çalıştırıcısı'nda oluşturulan şablon yapılandırır *MathServiceTests.fsproj*:</span><span class="sxs-lookup"><span data-stu-id="99a36-123">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

<span data-ttu-id="99a36-124">Test projesi oluşturma ve birim testlerini çalıştırmak için diğer paketleri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="99a36-124">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="99a36-125">`dotnet new` Önceki adımda, MSTest ve MSTest Çalıştırıcısı eklendi.</span><span class="sxs-lookup"><span data-stu-id="99a36-125">`dotnet new` in the previous step added MSTest and the MSTest runner.</span></span> <span data-ttu-id="99a36-126">Şimdi ekleyin `MathService` sınıf kitaplığı projesine başka bir bağımlılık olarak.</span><span class="sxs-lookup"><span data-stu-id="99a36-126">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="99a36-127">Kullanım [ `dotnet add reference` ](../tools/dotnet-add-reference.md) komutu:</span><span class="sxs-lookup"><span data-stu-id="99a36-127">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="99a36-128">Dosyanın tamamını görebilirsiniz [örnekleri depomuzdan](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) GitHub üzerinde.</span><span class="sxs-lookup"><span data-stu-id="99a36-128">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="99a36-129">Aşağıdaki nihai çözüm Düzen vardır:</span><span class="sxs-lookup"><span data-stu-id="99a36-129">You have the following final solution layout:</span></span>

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

<span data-ttu-id="99a36-130">Yürütme [ `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` ](../tools/dotnet-sln.md) içinde *birim-test-ile-fsharp* dizin.</span><span class="sxs-lookup"><span data-stu-id="99a36-130">Execute [`dotnet sln add .\MathService.Tests\MathService.Tests.fsproj`](../tools/dotnet-sln.md) in the *unit-testing-with-fsharp* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="99a36-131">İlk testi oluşturma</span><span class="sxs-lookup"><span data-stu-id="99a36-131">Creating the first test</span></span>

<span data-ttu-id="99a36-132">Bir yazma, test başarısız kolaylaştırır geçişi, sonra işlemi yineleyin.</span><span class="sxs-lookup"><span data-stu-id="99a36-132">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="99a36-133">Açık *Tests.fs* ve aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="99a36-133">Open *Tests.fs* and add the following code:</span></span>

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

<span data-ttu-id="99a36-134">`[<TestClass>]` Özniteliği testleri içeren bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="99a36-134">The `[<TestClass>]` attribute denotes a class that contains tests.</span></span> <span data-ttu-id="99a36-135">`[<TestMethod>]` Test Çalıştırıcısı tarafından yürütülen bir test metodu özniteliği gösterir.</span><span class="sxs-lookup"><span data-stu-id="99a36-135">The `[<TestMethod>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="99a36-136">Gelen *birim-test-ile-fsharp* dizin yürütme [ `dotnet test` ](../tools/dotnet-test.md) testler ve sınıf kitaplığı oluşturun ve ardından testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="99a36-136">From the *unit-testing-with-fsharp* directory, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="99a36-137">Programın giriş noktası, testlerinizi çalıştırmak için MSTest test Çalıştırıcısı içerir.</span><span class="sxs-lookup"><span data-stu-id="99a36-137">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="99a36-138">`dotnet test` oluşturduğunuz birim test projesi kullanarak test Çalıştırıcısı'nı başlatır.</span><span class="sxs-lookup"><span data-stu-id="99a36-138">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="99a36-139">Bu iki testleri en temel geçirme ve testleri başarısız gösterir.</span><span class="sxs-lookup"><span data-stu-id="99a36-139">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="99a36-140">`My test` geçer, ve `Fail every time` başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="99a36-140">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="99a36-141">Şimdi, test için oluşturma `squaresOfOdds` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="99a36-141">Now, create a test for the `squaresOfOdds` method.</span></span> <span data-ttu-id="99a36-142">`squaresOfOdds` Yöntemi kareler Giriş dizisinin bir parçası olan tüm tek sayılı tamsayı değerleri listesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="99a36-142">The `squaresOfOdds` method returns a list of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="99a36-143">Bu işlevlerin tümü aynı anda yazma çalışmak yerine, tekrarlayarak işlevselliğini doğrulama testleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99a36-143">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="99a36-144">Her test yöntemi için gereken işlevselliği oluşturma anlamına gelir geçirmek yapılıyor.</span><span class="sxs-lookup"><span data-stu-id="99a36-144">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="99a36-145">Biz yazabilirsiniz basit test çağırmaktır `squaresOfOdds` ile sonucu boş bir tam sayı dizisidir olması burada tüm çift sayılarla.</span><span class="sxs-lookup"><span data-stu-id="99a36-145">The simplest test we can write is to call `squaresOfOdds` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="99a36-146">Test şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="99a36-146">Here's that test:</span></span>

```fsharp
[<TestMethod>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int> |> Seq.toList
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.AreEqual(expected, actual)
```

<span data-ttu-id="99a36-147">Dikkat `expected` sıralı bir listeye dönüştürülmüş.</span><span class="sxs-lookup"><span data-stu-id="99a36-147">Notice that the `expected` sequence has been converted to a list.</span></span> <span data-ttu-id="99a36-148">MSTest kitaplığı çok sayıda standart .NET türlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="99a36-148">The MSTest library relies on many standard .NET types.</span></span> <span data-ttu-id="99a36-149">Destek bağımlılık, ortak arabirim anlamına gelir ve beklenen sonuçları <xref:System.Collections.ICollection> yerine <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="99a36-149">That dependency means that your public interface and expected results support <xref:System.Collections.ICollection> rather than <xref:System.Collections.IEnumerable>.</span></span>

<span data-ttu-id="99a36-150">Test çalıştırdığınızda, test başarısız olduğunu görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="99a36-150">When you run the test, you see that your test fails.</span></span> <span data-ttu-id="99a36-151">Uygulama henüz oluşturmadınız.</span><span class="sxs-lookup"><span data-stu-id="99a36-151">You haven't created the implementation yet.</span></span> <span data-ttu-id="99a36-152">En basit kod yazarak bu testin geçmesini `Mathservice` çalışır sınıfı:</span><span class="sxs-lookup"><span data-stu-id="99a36-152">Make this test by writing the simplest code in the `Mathservice` class that works:</span></span>

```csharp
let squaresOfOdds xs =
    Seq.empty<int> |> Seq.toList
```

<span data-ttu-id="99a36-153">İçinde *birim-test-ile-fsharp* çalışması dizini `dotnet test` yeniden.</span><span class="sxs-lookup"><span data-stu-id="99a36-153">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="99a36-154">`dotnet test` Komut çalıştıran bir derleme için `MathService` proje ve ardından `MathService.Tests` proje.</span><span class="sxs-lookup"><span data-stu-id="99a36-154">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="99a36-155">Her iki proje oluşturduktan sonra bu tek bir test çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="99a36-155">After building both projects, it runs this single test.</span></span> <span data-ttu-id="99a36-156">Bu geçirir.</span><span class="sxs-lookup"><span data-stu-id="99a36-156">It passes.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="99a36-157">Gereksinimleri Tamamlanıyor</span><span class="sxs-lookup"><span data-stu-id="99a36-157">Completing the requirements</span></span>

<span data-ttu-id="99a36-158">Bir test geçirmek yaptığınız, daha fazla yazmak için zaman var.</span><span class="sxs-lookup"><span data-stu-id="99a36-158">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="99a36-159">Basit bir sonraki durumda, yalnızca tek sayı içeren bir dizisini çalışır `1`.</span><span class="sxs-lookup"><span data-stu-id="99a36-159">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="99a36-160">Sayı 1, 1 karesini 1 olduğundan daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="99a36-160">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="99a36-161">Sonraki test şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="99a36-161">Here's that next test:</span></span>

```fsharp
[<TestMethod>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.AreEqual(expected, actual)
```

<span data-ttu-id="99a36-162">Yürütme `dotnet test` yeni test başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="99a36-162">Executing `dotnet test` fails the new test.</span></span> <span data-ttu-id="99a36-163">Güncelleştirmeniz gerekir `squaresOfOdds` bu yeni test işlemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="99a36-163">You must update the `squaresOfOdds` method to handle this new test.</span></span> <span data-ttu-id="99a36-164">Tüm çift sayıları geçirmek bu testi yapmak için sıra dışı filtrelemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="99a36-164">You must filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="99a36-165">Küçük bir filtre işlevi yazma ve kullanarak bunu yapabilirsiniz `Seq.filter`:</span><span class="sxs-lookup"><span data-stu-id="99a36-165">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd |> Seq.toList
```

<span data-ttu-id="99a36-166">Çağrısını fark `Seq.toList`.</span><span class="sxs-lookup"><span data-stu-id="99a36-166">Notice the call to `Seq.toList`.</span></span> <span data-ttu-id="99a36-167">Uygulayan bir liste oluşturur <xref:System.Collections.ICollection> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="99a36-167">That creates a list, which implements the <xref:System.Collections.ICollection> interface.</span></span>

<span data-ttu-id="99a36-168">Gitmek için bir adım daha vardır: her biri tek sayıları kare.</span><span class="sxs-lookup"><span data-stu-id="99a36-168">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="99a36-169">Yeni bir test yazarak başlatın:</span><span class="sxs-lookup"><span data-stu-id="99a36-169">Start by writing a new test:</span></span>

```fsharp
[<TestMethod>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.AreEqual(expected, actual)
```

<span data-ttu-id="99a36-170">Filtrelenmiş sırası tek her bir sayının karesini işlem için bir harita işlemi boyunca yönelterek test düzeltebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="99a36-170">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
    |> Seq.toList
```

<span data-ttu-id="99a36-171">Küçük bir kitaplık ve bu kitaplık için birim testleri bir dizi oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="99a36-171">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="99a36-172">Böylece yeni paketler ekleme çözüm yapılandırılmış ve testleri normal iş akışı bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="99a36-172">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="99a36-173">Zaman ve çaba çözme hedeflerinden biri, uygulama üzerinde en yoğun.</span><span class="sxs-lookup"><span data-stu-id="99a36-173">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
