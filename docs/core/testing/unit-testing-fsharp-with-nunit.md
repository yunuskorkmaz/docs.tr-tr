---
title: "Birim F # kitaplığı .NET dotnet test ve NUnit kullanarak çekirdek testi"
description: "Birim testi kavramları F # .NET Core için adım adım örnek çözüm oluşturma bir etkileşimli deneyimler aracılığıyla öğrenmeniz dotnet test ve NUnit kullanarak."
author: rprouse
ms.date: 12/01/2017
ms.topic: article
dev_langs: fsharp
ms.prod: .net-core
ms.openlocfilehash: 27a7bb889fd736294252da39b1839b2197b8df03
ms.sourcegitcommit: 401c4427a3ec0d1263543033b3084039278509dc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/06/2017
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-nunit"></a><span data-ttu-id="d0661-103">Birim F # kitaplığı .NET dotnet test ve NUnit kullanarak çekirdek testi</span><span class="sxs-lookup"><span data-stu-id="d0661-103">Unit testing F# libraries in .NET Core using dotnet test and NUnit</span></span>

<span data-ttu-id="d0661-104">Bu öğretici birim testi kavramlarını öğrenmek için adım adım örnek çözüm oluşturma etkileşimli bir deneyim gösterir.</span><span class="sxs-lookup"><span data-stu-id="d0661-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="d0661-105">Önceden oluşturulmuş bir çözümü kullanarak öğreticiyi izleyin tercih ediyorsanız [görüntülemek veya karşıdan örnek kod](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-with-fsharp-nunit/) başlamadan önce.</span><span class="sxs-lookup"><span data-stu-id="d0661-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-with-fsharp-nunit/) before you begin.</span></span> <span data-ttu-id="d0661-106">Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="d0661-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="d0661-107">Kaynak projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="d0661-107">Creating the source project</span></span>

<span data-ttu-id="d0661-108">Kabuk penceresini açın.</span><span class="sxs-lookup"><span data-stu-id="d0661-108">Open a shell window.</span></span> <span data-ttu-id="d0661-109">Adlı bir dizin oluşturun *birim-test etme-ile-fsharp* çözümü tutmak için.</span><span class="sxs-lookup"><span data-stu-id="d0661-109">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="d0661-110">Bu yeni dizin içinde çalıştırmak [ `dotnet new sln` ](../tools/dotnet-new.md) yeni bir çözüm oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="d0661-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="d0661-111">Bu sınıf kitaplığı ve birim testi projesi yönetmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="d0661-111">This makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="d0661-112">Çözüm dizini içinde oluşturmak bir *MathService* dizini.</span><span class="sxs-lookup"><span data-stu-id="d0661-112">Inside the solution directory, create a *MathService* directory.</span></span> <span data-ttu-id="d0661-113">Dizin ve dosya yapısı bugüne kadarki aşağıda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="d0661-113">The directory and file structure thus far is shown below:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="d0661-114">Olun *MathService* geçerli dizin ve çalışma [ `dotnet new classlib -lang F#` ](../tools/dotnet-new.md) kaynak projesi oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="d0661-114">Make *MathService* the current directory and run [`dotnet new classlib -lang F#`](../tools/dotnet-new.md) to create the source project.</span></span>  <span data-ttu-id="d0661-115">Teste dayalı geliştirme (TDD) kullanmak için başarısız olan uygulama matematik hizmetinin oluşturursunuz:</span><span class="sxs-lookup"><span data-stu-id="d0661-115">To use test-driven development (TDD), you'll create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let sumOfSquares xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="d0661-116">Dizin geri değişiklik *birim-test etme-ile-fsharp* dizini.</span><span class="sxs-lookup"><span data-stu-id="d0661-116">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="d0661-117">Çalıştırma [ `dotnet sln add .\MathService\MathService.fsproj` ](../tools/dotnet-sln.md) sınıf kitaplığı proje çözüme eklemek için.</span><span class="sxs-lookup"><span data-stu-id="d0661-117">Run [`dotnet sln add .\MathService\MathService.fsproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="install-the-nunit-project-template"></a><span data-ttu-id="d0661-118">NUnit proje şablonu yükleyin</span><span class="sxs-lookup"><span data-stu-id="d0661-118">Install the NUnit project template</span></span>

<span data-ttu-id="d0661-119">NUnit test projesi şablonları bir test projesi oluşturmadan önce yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="d0661-119">The NUnit test project templates need to be installed before creating a test project.</span></span> <span data-ttu-id="d0661-120">Bu yalnızca bir kez yeni NUnit projeleri oluşturacağınız her geliştirici makinede yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d0661-120">This only needs to be done once on each developer machine where you'll create new NUnit projects.</span></span> <span data-ttu-id="d0661-121">Çalıştırma [ `dotnet new -i NUnit3.DotNetNew.Template` ](../tools/dotnet-new.md) NUnit şablonları yüklemek için.</span><span class="sxs-lookup"><span data-stu-id="d0661-121">Run [`dotnet new -i NUnit3.DotNetNew.Template`](../tools/dotnet-new.md) to install the NUnit templates.</span></span>

 ```
 dotnet new -i NUnit3.DotNetNew.Template
 ```

## <a name="creating-the-test-project"></a><span data-ttu-id="d0661-122">Test projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="d0661-122">Creating the test project</span></span>

<span data-ttu-id="d0661-123">Ardından, oluşturun *MathService.Tests* dizini.</span><span class="sxs-lookup"><span data-stu-id="d0661-123">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="d0661-124">Aşağıdaki anahat dizin yapısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="d0661-124">The following outline shows the directory structure:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="d0661-125">Olun *MathService.Tests* dizine geçerli ve kullanarak yeni bir proje oluşturun [ `dotnet new nunit -lang F#` ](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="d0661-125">Make the *MathService.Tests* directory the current directory and create a new project using [`dotnet new nunit -lang F#`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="d0661-126">Bu NUnit test çerçevesi kullanan bir test projesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d0661-126">This creates a test project that uses NUnit as the test framework.</span></span> <span data-ttu-id="d0661-127">Test Çalıştırıcısı'nda oluşturulan şablon yapılandırır *MathServiceTests.fsproj*:</span><span class="sxs-lookup"><span data-stu-id="d0661-127">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

<span data-ttu-id="d0661-128">Test projesi oluşturmak ve birim testleri çalıştırmak için diğer paketleri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d0661-128">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="d0661-129">`dotnet new`Önceki adımda NUnit ve NUnit test bağdaştırıcısı eklendi.</span><span class="sxs-lookup"><span data-stu-id="d0661-129">`dotnet new` in the previous step added NUnit and the NUnit test adapter.</span></span> <span data-ttu-id="d0661-130">Şimdi, ekleyin `MathService` sınıf kitaplığı proje için başka bir bağımlılık olarak.</span><span class="sxs-lookup"><span data-stu-id="d0661-130">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="d0661-131">Kullanım [ `dotnet add reference` ](../tools/dotnet-add-reference.md) komutu:</span><span class="sxs-lookup"><span data-stu-id="d0661-131">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="d0661-132">Tüm dosyasında görebilirsiniz [örnekleri deposu](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) github'da.</span><span class="sxs-lookup"><span data-stu-id="d0661-132">You can see the entire file in the [samples repository](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="d0661-133">Aşağıdaki nihai çözüm düzeni vardır:</span><span class="sxs-lookup"><span data-stu-id="d0661-133">You have the following final solution layout:</span></span>

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

<span data-ttu-id="d0661-134">Yürütme [ `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` ](../tools/dotnet-sln.md) içinde *birim-test etme-ile-fsharp* dizini.</span><span class="sxs-lookup"><span data-stu-id="d0661-134">Execute [`dotnet sln add .\MathService.Tests\MathService.Tests.fsproj`](../tools/dotnet-sln.md) in the *unit-testing-with-fsharp* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="d0661-135">İlk testi oluşturma</span><span class="sxs-lookup"><span data-stu-id="d0661-135">Creating the first test</span></span>

<span data-ttu-id="d0661-136">TDD yaklaşım geçirmek kolaylaştırarak ve süreci tekrarlayarak yazma bir başarısız test için çağırır.</span><span class="sxs-lookup"><span data-stu-id="d0661-136">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="d0661-137">Açık *Tests.fs* ve aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d0661-137">Open *Tests.fs* and add the following code:</span></span>

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

<span data-ttu-id="d0661-138">`[<TestFixture>]` Özniteliği testleri içeren bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="d0661-138">The `[<TestFixture>]` attribute denotes a class that contains tests.</span></span> <span data-ttu-id="d0661-139">`[<Test>]` Özniteliği test Çalıştırıcısı tarafından çalıştırılan test yöntemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d0661-139">The `[<Test>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="d0661-140">Gelen *birim-test etme-ile-fsharp* dizin, yürütme [ `dotnet test` ](../tools/dotnet-test.md) testleri ve sınıf kitaplığı oluşturmak ve ardından testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d0661-140">From the *unit-testing-with-fsharp* directory, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="d0661-141">NUnit test Çalıştırıcısı testleri çalıştırmak için program giriş noktası içerir.</span><span class="sxs-lookup"><span data-stu-id="d0661-141">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="d0661-142">`dotnet test`oluşturduğunuz birim testi projesi kullanarak test Çalıştırıcısı başlatır.</span><span class="sxs-lookup"><span data-stu-id="d0661-142">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="d0661-143">Bu iki testleri en temel geçirme ve testleri başarısız gösterir.</span><span class="sxs-lookup"><span data-stu-id="d0661-143">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="d0661-144">`My test`geçirir, ve `Fail every time` başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="d0661-144">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="d0661-145">Şimdi, test için oluşturma `sumOfSquares` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d0661-145">Now, create a test for the `sumOfSquares` method.</span></span> <span data-ttu-id="d0661-146">`sumOfSquares` Yöntemi Giriş dizisinin bir parçası olan tüm tek sayılı tamsayı değerleri kareleri toplamını döndürür.</span><span class="sxs-lookup"><span data-stu-id="d0661-146">The `sumOfSquares` method returns the sum of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="d0661-147">Bu işlevlerin tümüne tek seferde yazmaya çalışırken yerine işlevselliğini doğrulama testleri tekrarlayarak oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0661-147">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="d0661-148">Yöntemi için gerekli işlevselliği oluşturma anlamına gelir geçirmek her test yapma.</span><span class="sxs-lookup"><span data-stu-id="d0661-148">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="d0661-149">Biz yazabilirler basit test çağırmaktır `sumOfSquares` tüm çift numaraları, burada sonucu olmalıdır boş bir tam sayı dizisidir.</span><span class="sxs-lookup"><span data-stu-id="d0661-149">The simplest test we can write is to call `sumOfSquares` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="d0661-150">Bu test şöyledir:</span><span class="sxs-lookup"><span data-stu-id="d0661-150">Here's that test:</span></span>

```fsharp
[<Test>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int> |> Seq.toList
    let actual = MyMath.sumOfSquares [2; 4; 6; 8; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="d0661-151">Dikkat `expected` sıralı liste dönüştürülmüş.</span><span class="sxs-lookup"><span data-stu-id="d0661-151">Notice that the `expected` sequence has been converted to a list.</span></span> <span data-ttu-id="d0661-152">NUnit framework birçok standart .NET türlerine dayanır.</span><span class="sxs-lookup"><span data-stu-id="d0661-152">The NUnit framework relies on many standard .NET types.</span></span> <span data-ttu-id="d0661-153">Destek bağımlılık ortak arabirimi anlamına gelir ve beklenen sonuçları <xref:System.Collections.ICollection> yerine <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="d0661-153">That dependency means that your public interface and expected results support <xref:System.Collections.ICollection> rather than <xref:System.Collections.IEnumerable>.</span></span>

<span data-ttu-id="d0661-154">Testi çalıştırdığınızda, testiniz başarısız olduğunu görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="d0661-154">When you run the test, you see that your test fails.</span></span> <span data-ttu-id="d0661-155">Uygulama henüz oluşturmadınız.</span><span class="sxs-lookup"><span data-stu-id="d0661-155">You haven't created the implementation yet.</span></span> <span data-ttu-id="d0661-156">Bu test basit kod yazarken yapmasına `Mathservice` çalışır sınıfı:</span><span class="sxs-lookup"><span data-stu-id="d0661-156">Make this test by writing the simplest code in the `Mathservice` class that works:</span></span>

```csharp
let sumOfSquares xs =
    Seq.empty<int> |> Seq.toList
```

<span data-ttu-id="d0661-157">İçinde *birim-test etme-ile-fsharp* çalışması dizini `dotnet test` yeniden.</span><span class="sxs-lookup"><span data-stu-id="d0661-157">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="d0661-158">`dotnet test` Komutu çalıştıran bir yapı `MathService` proje ve ardından `MathService.Tests` projesi.</span><span class="sxs-lookup"><span data-stu-id="d0661-158">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="d0661-159">Her iki proje oluşturduktan sonra bu tek bir test çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="d0661-159">After building both projects, it runs this single test.</span></span> <span data-ttu-id="d0661-160">Bunu geçirir.</span><span class="sxs-lookup"><span data-stu-id="d0661-160">It passes.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="d0661-161">Gereksinimleri Tamamlanıyor</span><span class="sxs-lookup"><span data-stu-id="d0661-161">Completing the requirements</span></span>

<span data-ttu-id="d0661-162">Bir test geçirmek yapmış olduğunuz, daha fazla yazma zamanı geldi.</span><span class="sxs-lookup"><span data-stu-id="d0661-162">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="d0661-163">Sonraki basit bir durumda, yalnızca tek sayı olan bir sıra ile çalışır `1`.</span><span class="sxs-lookup"><span data-stu-id="d0661-163">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="d0661-164">1 sayısı 1'in Kare 1 olduğundan daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="d0661-164">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="d0661-165">Sonraki test şöyledir:</span><span class="sxs-lookup"><span data-stu-id="d0661-165">Here's that next test:</span></span>

```fsharp
[<Test>]
member public this.SumOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.sumOfSquares [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="d0661-166">Yürütme `dotnet test` yeni sınama başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="d0661-166">Executing `dotnet test` fails the new test.</span></span> <span data-ttu-id="d0661-167">Güncelleştirmeniz gerekir `sumOfSquares` bu yeni test işlemek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="d0661-167">You must update the `sumOfSquares` method to handle this new test.</span></span> <span data-ttu-id="d0661-168">Geçirmek bu testi yapmak için sıra dışında tüm çift sayıları filtre gerekir.</span><span class="sxs-lookup"><span data-stu-id="d0661-168">You must filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="d0661-169">Küçük filtre işlevi yazma ve kullanarak bunu, `Seq.filter`:</span><span class="sxs-lookup"><span data-stu-id="d0661-169">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let sumOfSquares xs =
    xs
    |> Seq.filter isOdd
    |> Seq.toList
```

<span data-ttu-id="d0661-170">Çağrısını fark `Seq.toList`.</span><span class="sxs-lookup"><span data-stu-id="d0661-170">Notice the call to `Seq.toList`.</span></span> <span data-ttu-id="d0661-171">Arabirimini uygulayan bir liste oluşturur <xref:System.Collections.ICollection> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d0661-171">That creates a list, which implements the <xref:System.Collections.ICollection> interface.</span></span>

<span data-ttu-id="d0661-172">Gitmek için bir adım daha vardır: her tek sayıların karesini.</span><span class="sxs-lookup"><span data-stu-id="d0661-172">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="d0661-173">Yeni bir test yazarak başlatın:</span><span class="sxs-lookup"><span data-stu-id="d0661-173">Start by writing a new test:</span></span>

```fsharp
[<Test>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.sumOfSquares [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="d0661-174">Her tek sayı kare hesaplamak için eşleme işlemi aracılığıyla filtrelenmiş dizisi cmdlet'ine yönelterek test düzeltebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d0661-174">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let sumOfSquares xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
    |> Seq.toList
```

<span data-ttu-id="d0661-175">Küçük bir kitaplığı ve bu kitaplık için birim testleri kümesini temel aldık.</span><span class="sxs-lookup"><span data-stu-id="d0661-175">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="d0661-176">Böylece yeni paketleri ekleme çözümü yapılandırılmış ve testleri normal iş akışı bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="d0661-176">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="d0661-177">Çoğu zaman ve çaba uygulama amaçlarını çözme üzerinde yoğunlaşmıştır.</span><span class="sxs-lookup"><span data-stu-id="d0661-177">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
