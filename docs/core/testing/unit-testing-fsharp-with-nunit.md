---
title: DotNet test F# ve NUnit Ile .NET Core 'da birim testi
description: .NET Core F# 'da, DotNet test ve NUnit kullanarak örnek bir çözüm oluşturarak etkileşimli bir deneyim aracılığıyla birim testi kavramlarını öğrenin.
author: rprouse
ms.date: 10/04/2018
dev_langs:
- fsharp
ms.custom: seodec18
ms.openlocfilehash: cf313f8197280bdbb943c12ef0c7a29284ec01a5
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849769"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-nunit"></a><span data-ttu-id="5b144-103">DotNet test F# ve NUnit kullanarak .NET Core 'da birim testi kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="5b144-103">Unit testing F# libraries in .NET Core using dotnet test and NUnit</span></span>

<span data-ttu-id="5b144-104">Bu öğreticide, birim testi kavramlarını öğrenmek için bir örnek çözüm oluşturma adım adım yönergeler sunarak etkileşimli bir deneyim sağlanır.</span><span class="sxs-lookup"><span data-stu-id="5b144-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="5b144-105">Önceden oluşturulmuş bir çözüm kullanarak öğreticiyi izlemeyi tercih ediyorsanız, başlamadan önce [örnek kodu görüntüleyin veya indirin](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-nunit/) .</span><span class="sxs-lookup"><span data-stu-id="5b144-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-nunit/) before you begin.</span></span> <span data-ttu-id="5b144-106">İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="5b144-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="prerequisites"></a><span data-ttu-id="5b144-107">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="5b144-107">Prerequisites</span></span>

- <span data-ttu-id="5b144-108">[.NET Core 2,1 SDK](https://dotnet.microsoft.com/download) veya sonraki sürümleri.</span><span class="sxs-lookup"><span data-stu-id="5b144-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later versions.</span></span>
- <span data-ttu-id="5b144-109">Seçtiğiniz bir metin düzenleyici veya kod Düzenleyicisi.</span><span class="sxs-lookup"><span data-stu-id="5b144-109">A text editor or code editor of your choice.</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="5b144-110">Kaynak proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="5b144-110">Creating the source project</span></span>

<span data-ttu-id="5b144-111">Bir kabuk penceresi açın.</span><span class="sxs-lookup"><span data-stu-id="5b144-111">Open a shell window.</span></span> <span data-ttu-id="5b144-112">Çözümü tutmak için- *FSharp ile birim-test* adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5b144-112">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="5b144-113">Bu yeni dizin içinde, sınıf kitaplığı ve test projesi için yeni bir çözüm dosyası oluşturmak üzere aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="5b144-113">Inside this new directory, run the following command to create a new solution file for the class library and the test project:</span></span>

```console
dotnet new sln
```

<span data-ttu-id="5b144-114">Sonra bir *MathService* dizini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5b144-114">Next, create a *MathService* directory.</span></span> <span data-ttu-id="5b144-115">Aşağıdaki ana hat şu ana kadar dizin ve dosya yapısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="5b144-115">The following outline shows the directory and file structure so far:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="5b144-116">*MathService* geçerli dizin yapın ve kaynak projeyi oluşturmak için şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="5b144-116">Make *MathService* the current directory and run the following command to create the source project:</span></span>

```console
dotnet new classlib -lang F#
```

<span data-ttu-id="5b144-117">Matematik hizmetinin başarısız bir uygulamasını oluşturursunuz:</span><span class="sxs-lookup"><span data-stu-id="5b144-117">You create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="5b144-118">Dizini- *FSharp dizinine sahip birim-test ile* yeniden değiştirin.</span><span class="sxs-lookup"><span data-stu-id="5b144-118">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="5b144-119">Çözüme Sınıf Kitaplığı projesini eklemek için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="5b144-119">Run the following command to add the class library project to the solution:</span></span>

```console
dotnet sln add .\MathService\MathService.fsproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="5b144-120">Test projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="5b144-120">Creating the test project</span></span>

<span data-ttu-id="5b144-121">Sonra, *MathService. Tests* dizinini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5b144-121">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="5b144-122">Aşağıdaki ana hat dizin yapısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="5b144-122">The following outline shows the directory structure:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="5b144-123">*MathService. Tests* dizinini geçerli dizini yapın ve aşağıdaki komutu kullanarak yeni bir proje oluşturun:</span><span class="sxs-lookup"><span data-stu-id="5b144-123">Make the *MathService.Tests* directory the current directory and create a new project using the following command:</span></span>

```console
dotnet new nunit -lang F#
```

<span data-ttu-id="5b144-124">Bu, test çerçevesi olarak NUnit kullanan bir test projesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5b144-124">This creates a test project that uses NUnit as the test framework.</span></span> <span data-ttu-id="5b144-125">Oluşturulan şablon, *MathServiceTests. fsproj*içindeki Test Çalıştırıcısı 'nı yapılandırır:</span><span class="sxs-lookup"><span data-stu-id="5b144-125">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

<span data-ttu-id="5b144-126">Test projesi, birim testlerini oluşturmak ve çalıştırmak için diğer paketlerin kullanılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5b144-126">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="5b144-127">`dotnet new`önceki adımda NUnit ve NUnit test bağdaştırıcısı eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="5b144-127">`dotnet new` in the previous step added NUnit and the NUnit test adapter.</span></span> <span data-ttu-id="5b144-128">Şimdi, `MathService` sınıf kitaplığını projeye başka bir bağımlılık olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5b144-128">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="5b144-129">[`dotnet add reference`](../tools/dotnet-add-reference.md) Şu komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="5b144-129">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```console
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="5b144-130">GitHub 'daki [örnekler deposunda](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) dosyanın tamamını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b144-130">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="5b144-131">Aşağıdaki son çözüm düzenine sahipsiniz:</span><span class="sxs-lookup"><span data-stu-id="5b144-131">You have the following final solution layout:</span></span>

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

<span data-ttu-id="5b144-132">*Birim-test--FSharp* dizininde aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="5b144-132">Execute the following command in the *unit-testing-with-fsharp* directory:</span></span>

```console
dotnet sln add .\MathService.Tests\MathService.Tests.fsproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="5b144-133">İlk test oluşturma</span><span class="sxs-lookup"><span data-stu-id="5b144-133">Creating the first test</span></span>

<span data-ttu-id="5b144-134">Başarısız bir test yazdığınızda, geçişi yapıp işlemi tekrarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b144-134">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="5b144-135">*UnitTest1. FS* ' i açın ve aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="5b144-135">Open *UnitTest1.fs* and add the following code:</span></span>

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

<span data-ttu-id="5b144-136">Öznitelik `[<TestFixture>]` , testleri içeren bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="5b144-136">The `[<TestFixture>]` attribute denotes a class that contains tests.</span></span> <span data-ttu-id="5b144-137">`[<Test>]` Öznitelik, Test Çalıştırıcısı tarafından çalıştırılan bir test yöntemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5b144-137">The `[<Test>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="5b144-138">*Birim-test--FSharp* dizininden, testleri ve sınıf kitaplığını [`dotnet test`](../tools/dotnet-test.md) oluşturmak için yürütün ve ardından testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5b144-138">From the *unit-testing-with-fsharp* directory, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="5b144-139">NUnit Test Çalıştırıcısı, testlerinizi çalıştırmak için program giriş noktasını içerir.</span><span class="sxs-lookup"><span data-stu-id="5b144-139">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="5b144-140">`dotnet test`oluşturduğunuz birim test projesini kullanarak Test Çalıştırıcısı başlatır.</span><span class="sxs-lookup"><span data-stu-id="5b144-140">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="5b144-141">Bu iki test, en temel geçirme ve başarısız testleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="5b144-141">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="5b144-142">`My test`geçirilir ve `Fail every time` başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="5b144-142">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="5b144-143">Şimdi, `squaresOfOdds` yöntemi için bir test oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5b144-143">Now, create a test for the `squaresOfOdds` method.</span></span> <span data-ttu-id="5b144-144">`squaresOfOdds` Yöntemi, giriş dizisinin parçası olan tüm tek tamsayı değerlerinin karelerinin dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="5b144-144">The `squaresOfOdds` method returns a sequence of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="5b144-145">Bu işlevlerin tümünü aynı anda yazmaya çalışmak yerine, işlevi doğrulayan testleri tekrarlayarak oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b144-145">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="5b144-146">Her test geçişinin yapılması, yöntemi için gerekli işlevselliğin oluşturulması anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5b144-146">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="5b144-147">Yazdığımız en basit test, sonucun boş bir `squaresOfOdds` tamsayılar dizisi olması gereken tüm çift sayılarla çağrıdır.</span><span class="sxs-lookup"><span data-stu-id="5b144-147">The simplest test we can write is to call `squaresOfOdds` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="5b144-148">Bu test şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="5b144-148">Here's that test:</span></span>

```fsharp
[<Test>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="5b144-149">`expected` Sıranın bir listeye dönüştürüldüğüne dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="5b144-149">Notice that the `expected` sequence has been converted to a list.</span></span> <span data-ttu-id="5b144-150">NUnit çerçevesi birçok standart .NET türünü temel alır.</span><span class="sxs-lookup"><span data-stu-id="5b144-150">The NUnit framework relies on many standard .NET types.</span></span> <span data-ttu-id="5b144-151">Bu bağımlılık, genel arabiriminiz ve <xref:System.Collections.ICollection> <xref:System.Collections.IEnumerable>yerine beklenen sonuç desteğinden biridir.</span><span class="sxs-lookup"><span data-stu-id="5b144-151">That dependency means that your public interface and expected results support <xref:System.Collections.ICollection> rather than <xref:System.Collections.IEnumerable>.</span></span>

<span data-ttu-id="5b144-152">Testi çalıştırdığınızda, testinizin başarısız olduğunu görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="5b144-152">When you run the test, you see that your test fails.</span></span> <span data-ttu-id="5b144-153">Uygulamayı henüz oluşturmadınız.</span><span class="sxs-lookup"><span data-stu-id="5b144-153">You haven't created the implementation yet.</span></span> <span data-ttu-id="5b144-154">MathService projenizdeki *Library. FS* sınıfına en basit kodu yazarak bu test geçişini yapın:</span><span class="sxs-lookup"><span data-stu-id="5b144-154">Make this test pass by writing the simplest code in the *Library.fs* class in your MathService project that works:</span></span>

```fsharp
let squaresOfOdds xs =
    Seq.empty<int>
```

<span data-ttu-id="5b144-155">*Birim-test--FSharp diziniyle birlikte* yeniden çalıştırın `dotnet test` .</span><span class="sxs-lookup"><span data-stu-id="5b144-155">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="5b144-156">Komutu, `MathService` proje için bir yapı ve ardından projeiçinçalışır.`MathService.Tests` `dotnet test`</span><span class="sxs-lookup"><span data-stu-id="5b144-156">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="5b144-157">Her iki proje de oluşturulduktan sonra testlerinizi çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="5b144-157">After building both projects, it runs your tests.</span></span> <span data-ttu-id="5b144-158">İki test şimdi geçer.</span><span class="sxs-lookup"><span data-stu-id="5b144-158">Two tests pass now.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="5b144-159">Gereksinimleri tamamlama</span><span class="sxs-lookup"><span data-stu-id="5b144-159">Completing the requirements</span></span>

<span data-ttu-id="5b144-160">Artık bir test geçişi yapmış olduğunuza göre daha fazla yazma zamanı vardır.</span><span class="sxs-lookup"><span data-stu-id="5b144-160">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="5b144-161">Bir sonraki basit durum yalnızca tek sayı olan bir sıra ile birlikte kullanılır `1`.</span><span class="sxs-lookup"><span data-stu-id="5b144-161">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="5b144-162">1 numaralı kare 1 olduğundan, 1 sayısı daha kolay.</span><span class="sxs-lookup"><span data-stu-id="5b144-162">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="5b144-163">İşte bu sonraki test:</span><span class="sxs-lookup"><span data-stu-id="5b144-163">Here's that next test:</span></span>

```fsharp
[<Test>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="5b144-164">Yürütme `dotnet test` işlemi yeni test başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="5b144-164">Executing `dotnet test` fails the new test.</span></span> <span data-ttu-id="5b144-165">Bu yeni testi işlemek `squaresOfOdds` için yöntemini güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5b144-165">You must update the `squaresOfOdds` method to handle this new test.</span></span> <span data-ttu-id="5b144-166">Bu test geçişini yapmak için tüm çift sayıları sıranın dışına filtrelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5b144-166">You must filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="5b144-167">Bunu, küçük bir filtre işlevi yazarak ve kullanarak `Seq.filter`yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5b144-167">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

<span data-ttu-id="5b144-168">Çağrısına dikkat edin `Seq.toList`.</span><span class="sxs-lookup"><span data-stu-id="5b144-168">Notice the call to `Seq.toList`.</span></span> <span data-ttu-id="5b144-169">Bu, <xref:System.Collections.ICollection> arabirimini uygulayan bir liste oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5b144-169">That creates a list, which implements the <xref:System.Collections.ICollection> interface.</span></span>

<span data-ttu-id="5b144-170">Bir adım daha vardır: her bir tek sayının kare sayısı.</span><span class="sxs-lookup"><span data-stu-id="5b144-170">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="5b144-171">Yeni bir test yazarak başlayın:</span><span class="sxs-lookup"><span data-stu-id="5b144-171">Start by writing a new test:</span></span>

```fsharp
[<Test>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="5b144-172">Her bir tek sayının karesini hesaplamak için, filtre uygulanmış sırayı bir eşleme işlemi aracılığıyla ayırarak testi giderebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5b144-172">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
```

<span data-ttu-id="5b144-173">Bu kitaplık için küçük bir kitaplık ve birim testleri kümesi oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="5b144-173">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="5b144-174">Çözümü, yeni paket ve test eklemek normal iş akışının bir parçası olacak şekilde öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="5b144-174">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="5b144-175">Uygulamanın hedeflerini çözme konusunda zaman ve çaba harcamanızı en iyi şekilde gördünüz.</span><span class="sxs-lookup"><span data-stu-id="5b144-175">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
