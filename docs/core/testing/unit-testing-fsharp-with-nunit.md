---
title: Birim testi F# .NET core'da dotnet testi ve NUnit ile
description: Birim test kavramlarını öğrenin F# dotnet testi ve NUnit kullanarak .NET core'da adım adım örnek çözüm oluşturma etkileşimli bir deneyim.
author: rprouse
ms.date: 10/04/2018
dev_langs:
- fsharp
ms.custom: seodec18
ms.openlocfilehash: e919da8910129be027ff7e2dbed8c4564738e023
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241768"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-nunit"></a><span data-ttu-id="74953-103">Birim testi F# dotnet testi ve NUnit kullanarak .NET core'da kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="74953-103">Unit testing F# libraries in .NET Core using dotnet test and NUnit</span></span>

<span data-ttu-id="74953-104">Bu öğretici örnek bir çözüm birim testi kavramlarını öğrenmek için adım adım oluşturmaya etkileşimli deneyim gösterir.</span><span class="sxs-lookup"><span data-stu-id="74953-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="74953-105">Önceden oluşturulmuş bir çözümü kullanarak öğreticiyi uygulamak isterseniz [görüntülemek veya örnek kodu indirdikten](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-nunit/) başlamadan önce.</span><span class="sxs-lookup"><span data-stu-id="74953-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-nunit/) before you begin.</span></span> <span data-ttu-id="74953-106">Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="74953-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="74953-107">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="74953-107">Prerequisites</span></span>

- <span data-ttu-id="74953-108">[.NET core 2.1 SDK](https://www.microsoft.com/net/download) veya sonraki sürümler.</span><span class="sxs-lookup"><span data-stu-id="74953-108">[.NET Core 2.1 SDK](https://www.microsoft.com/net/download) or later versions.</span></span>
- <span data-ttu-id="74953-109">Bir metin düzenleyicisi veya tercih ettiğiniz Kod Düzenleyicisi.</span><span class="sxs-lookup"><span data-stu-id="74953-109">A text editor or code editor of your choice.</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="74953-110">Kaynak proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="74953-110">Creating the source project</span></span>

<span data-ttu-id="74953-111">Shell penceresini açın.</span><span class="sxs-lookup"><span data-stu-id="74953-111">Open a shell window.</span></span> <span data-ttu-id="74953-112">Adlı bir dizin oluşturun *birim-test-ile-fsharp* çözüm tutacak.</span><span class="sxs-lookup"><span data-stu-id="74953-112">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="74953-113">Bu yeni dizin içinde sınıf kitaplığı ve test projesi için yeni bir çözüm dosyası oluşturmak için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="74953-113">Inside this new directory, run the following command to create a new solution file for the class library and the test project:</span></span>

```console
dotnet new sln
```

<span data-ttu-id="74953-114">Ardından, oluşturun bir *MathService* dizin.</span><span class="sxs-lookup"><span data-stu-id="74953-114">Next, create a *MathService* directory.</span></span> <span data-ttu-id="74953-115">Aşağıdaki ana hat dizin ve dosya yapısı şu ana kadar gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="74953-115">The following outline shows the directory and file structure so far:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="74953-116">Olun *MathService* aşağıdaki komut kaynak projesi oluşturmak için geçerli dizin ve çalıştırma:</span><span class="sxs-lookup"><span data-stu-id="74953-116">Make *MathService* the current directory and run the following command to create the source project:</span></span>

```console
dotnet new classlib -lang F#
```

<span data-ttu-id="74953-117">Teste dayalı geliştirme (TDD) kullanmak için bir matematik hizmetin başarısız uygulama oluşturun:</span><span class="sxs-lookup"><span data-stu-id="74953-117">To use test-driven development (TDD), you create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="74953-118">Dizine dön değişiklik *birim-test-ile-fsharp* dizin.</span><span class="sxs-lookup"><span data-stu-id="74953-118">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="74953-119">Sınıf kitaplığı projesi çözüme eklemek için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="74953-119">Run the following command to add the class library project to the solution:</span></span>

```console
dotnet sln add .\MathService\MathService.fsproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="74953-120">Test projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="74953-120">Creating the test project</span></span>

<span data-ttu-id="74953-121">Ardından, oluşturma *MathService.Tests* dizin.</span><span class="sxs-lookup"><span data-stu-id="74953-121">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="74953-122">Ana hat aşağıdaki dizin yapısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="74953-122">The following outline shows the directory structure:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="74953-123">Olun *MathService.Tests* dizini geçerli dizin ve aşağıdaki komutu kullanarak yeni bir proje oluşturun:</span><span class="sxs-lookup"><span data-stu-id="74953-123">Make the *MathService.Tests* directory the current directory and create a new project using the following command:</span></span>

```console
dotnet new nunit -lang F#
```

<span data-ttu-id="74953-124">Bu, NUnit test çerçevesi kullanan bir test projesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="74953-124">This creates a test project that uses NUnit as the test framework.</span></span> <span data-ttu-id="74953-125">Test Çalıştırıcısı'nda oluşturulan şablon yapılandırır *MathServiceTests.fsproj*:</span><span class="sxs-lookup"><span data-stu-id="74953-125">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

<span data-ttu-id="74953-126">Test projesi oluşturma ve birim testlerini çalıştırmak için diğer paketleri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="74953-126">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="74953-127">`dotnet new` Önceki adımda NUnit ve NUnit test bağdaştırıcısı eklendi.</span><span class="sxs-lookup"><span data-stu-id="74953-127">`dotnet new` in the previous step added NUnit and the NUnit test adapter.</span></span> <span data-ttu-id="74953-128">Şimdi ekleyin `MathService` sınıf kitaplığı projesine başka bir bağımlılık olarak.</span><span class="sxs-lookup"><span data-stu-id="74953-128">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="74953-129">Kullanım [ `dotnet add reference` ](../tools/dotnet-add-reference.md) komutu:</span><span class="sxs-lookup"><span data-stu-id="74953-129">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```console
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="74953-130">Dosyanın tamamını görebilirsiniz [örnekleri depomuzdan](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) GitHub üzerinde.</span><span class="sxs-lookup"><span data-stu-id="74953-130">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="74953-131">Aşağıdaki nihai çözüm Düzen vardır:</span><span class="sxs-lookup"><span data-stu-id="74953-131">You have the following final solution layout:</span></span>

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

<span data-ttu-id="74953-132">Aşağıdaki komutu yürütün *birim-test-ile-fsharp* dizini:</span><span class="sxs-lookup"><span data-stu-id="74953-132">Execute the following command in the *unit-testing-with-fsharp* directory:</span></span>

```console
dotnet sln add .\MathService.Tests\MathService.Tests.fsproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="74953-133">İlk testi oluşturma</span><span class="sxs-lookup"><span data-stu-id="74953-133">Creating the first test</span></span>

<span data-ttu-id="74953-134">TDD yaklaşım geçer hale getirme ve süreci tekrarlayarak yazma bir başarısız test için çağırır.</span><span class="sxs-lookup"><span data-stu-id="74953-134">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="74953-135">Açık *UnitTest1.fs* ve aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="74953-135">Open *UnitTest1.fs* and add the following code:</span></span>

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

<span data-ttu-id="74953-136">`[<TestFixture>]` Özniteliği testleri içeren bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="74953-136">The `[<TestFixture>]` attribute denotes a class that contains tests.</span></span> <span data-ttu-id="74953-137">`[<Test>]` Test Çalıştırıcısı tarafından yürütülen bir test metodu özniteliği gösterir.</span><span class="sxs-lookup"><span data-stu-id="74953-137">The `[<Test>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="74953-138">Gelen *birim-test-ile-fsharp* dizin yürütme [ `dotnet test` ](../tools/dotnet-test.md) testler ve sınıf kitaplığı oluşturun ve ardından testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="74953-138">From the *unit-testing-with-fsharp* directory, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="74953-139">NUnit test Çalıştırıcısı, testlerinizi çalıştırmak için programın giriş noktası içerir.</span><span class="sxs-lookup"><span data-stu-id="74953-139">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="74953-140">`dotnet test` oluşturduğunuz birim test projesi kullanarak test Çalıştırıcısı'nı başlatır.</span><span class="sxs-lookup"><span data-stu-id="74953-140">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="74953-141">Bu iki testleri en temel geçirme ve testleri başarısız gösterir.</span><span class="sxs-lookup"><span data-stu-id="74953-141">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="74953-142">`My test` geçer, ve `Fail every time` başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="74953-142">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="74953-143">Şimdi, test için oluşturma `squaresOfOdds` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="74953-143">Now, create a test for the `squaresOfOdds` method.</span></span> <span data-ttu-id="74953-144">`squaresOfOdds` Yöntemi Giriş dizisinin bir parçası olan tüm tek tamsayı değerleri kareleri bir dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="74953-144">The `squaresOfOdds` method returns a sequence of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="74953-145">Bu işlevlerin tümü aynı anda yazma çalışmak yerine, tekrarlayarak işlevselliğini doğrulama testleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74953-145">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="74953-146">Her test yöntemi için gereken işlevselliği oluşturma anlamına gelir geçirmek yapılıyor.</span><span class="sxs-lookup"><span data-stu-id="74953-146">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="74953-147">Biz yazabilirsiniz basit test çağırmaktır `squaresOfOdds` ile sonucu boş bir tam sayı dizisidir olması burada tüm çift sayılarla.</span><span class="sxs-lookup"><span data-stu-id="74953-147">The simplest test we can write is to call `squaresOfOdds` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="74953-148">Test şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="74953-148">Here's that test:</span></span>

```fsharp
[<Test>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="74953-149">Dikkat `expected` sıralı bir listeye dönüştürülmüş.</span><span class="sxs-lookup"><span data-stu-id="74953-149">Notice that the `expected` sequence has been converted to a list.</span></span> <span data-ttu-id="74953-150">NUnit framework birçok standart .NET türü kullanır.</span><span class="sxs-lookup"><span data-stu-id="74953-150">The NUnit framework relies on many standard .NET types.</span></span> <span data-ttu-id="74953-151">Destek bağımlılık, ortak arabirim anlamına gelir ve beklenen sonuçları <xref:System.Collections.ICollection> yerine <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="74953-151">That dependency means that your public interface and expected results support <xref:System.Collections.ICollection> rather than <xref:System.Collections.IEnumerable>.</span></span>

<span data-ttu-id="74953-152">Test çalıştırdığınızda, test başarısız olduğunu görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="74953-152">When you run the test, you see that your test fails.</span></span> <span data-ttu-id="74953-153">Uygulama henüz oluşturmadınız.</span><span class="sxs-lookup"><span data-stu-id="74953-153">You haven't created the implementation yet.</span></span> <span data-ttu-id="74953-154">En basit kod yazarak geçirmek bu testin geçmesini *Library.fs* sınıfı MathService projenizdeki çalışır:</span><span class="sxs-lookup"><span data-stu-id="74953-154">Make this test pass by writing the simplest code in the *Library.fs* class in your MathService project that works:</span></span>

```csharp
let squaresOfOdds xs =
    Seq.empty<int>
```

<span data-ttu-id="74953-155">İçinde *birim-test-ile-fsharp* çalışması dizini `dotnet test` yeniden.</span><span class="sxs-lookup"><span data-stu-id="74953-155">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="74953-156">`dotnet test` Komut çalıştıran bir derleme için `MathService` proje ve ardından `MathService.Tests` proje.</span><span class="sxs-lookup"><span data-stu-id="74953-156">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="74953-157">Her iki proje oluşturduktan sonra testlerinizi çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="74953-157">After building both projects, it runs your tests.</span></span> <span data-ttu-id="74953-158">Şimdi iki test geçirin.</span><span class="sxs-lookup"><span data-stu-id="74953-158">Two tests pass now.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="74953-159">Gereksinimleri Tamamlanıyor</span><span class="sxs-lookup"><span data-stu-id="74953-159">Completing the requirements</span></span>

<span data-ttu-id="74953-160">Bir test geçirmek yaptığınız, daha fazla yazmak için zaman var.</span><span class="sxs-lookup"><span data-stu-id="74953-160">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="74953-161">Basit bir sonraki durumda, yalnızca tek sayı içeren bir dizisini çalışır `1`.</span><span class="sxs-lookup"><span data-stu-id="74953-161">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="74953-162">Sayı 1, 1 karesini 1 olduğundan daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="74953-162">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="74953-163">Sonraki test şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="74953-163">Here's that next test:</span></span>

```fsharp
[<Test>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="74953-164">Yürütme `dotnet test` yeni test başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="74953-164">Executing `dotnet test` fails the new test.</span></span> <span data-ttu-id="74953-165">Güncelleştirmeniz gerekir `squaresOfOdds` bu yeni test işlemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="74953-165">You must update the `squaresOfOdds` method to handle this new test.</span></span> <span data-ttu-id="74953-166">Tüm çift sayıları geçirmek bu testi yapmak için sıra dışı filtrelemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="74953-166">You must filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="74953-167">Küçük bir filtre işlevi yazma ve kullanarak bunu yapabilirsiniz `Seq.filter`:</span><span class="sxs-lookup"><span data-stu-id="74953-167">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

<span data-ttu-id="74953-168">Çağrısını fark `Seq.toList`.</span><span class="sxs-lookup"><span data-stu-id="74953-168">Notice the call to `Seq.toList`.</span></span> <span data-ttu-id="74953-169">Uygulayan bir liste oluşturur <xref:System.Collections.ICollection> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="74953-169">That creates a list, which implements the <xref:System.Collections.ICollection> interface.</span></span>

<span data-ttu-id="74953-170">Gitmek için bir adım daha vardır: her biri tek sayıları kare.</span><span class="sxs-lookup"><span data-stu-id="74953-170">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="74953-171">Yeni bir test yazarak başlatın:</span><span class="sxs-lookup"><span data-stu-id="74953-171">Start by writing a new test:</span></span>

```fsharp
[<Test>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="74953-172">Filtrelenmiş sırası tek her bir sayının karesini işlem için bir harita işlemi boyunca yönelterek test düzeltebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="74953-172">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
```

<span data-ttu-id="74953-173">Küçük bir kitaplık ve bu kitaplık için birim testleri bir dizi oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="74953-173">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="74953-174">Böylece yeni paketler ekleme çözüm yapılandırılmış ve testleri normal iş akışı bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="74953-174">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="74953-175">Zaman ve çaba çözme hedeflerinden biri, uygulama üzerinde en yoğun.</span><span class="sxs-lookup"><span data-stu-id="74953-175">You've concentrated most of your time and effort on solving the goals of the application.</span></span>