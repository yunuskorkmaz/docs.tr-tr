---
title: Dotnet testi ve xUnit ile .NET Core'da F# testi
description: Dotnet testi ve xUnit kullanarak adım adım örnek bir çözüm oluşturma etkileşimli bir deneyim le .NET Core'da F# için birim test kavramlarını öğrenin.
author: billwagner
ms.author: wiwagn
ms.date: 08/30/2017
ms.openlocfilehash: 5fe4a8faddd87334439513368f24d808abc58e65
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157316"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-xunit"></a><span data-ttu-id="89744-103">Dotnet testi ve xUnit kullanarak .NET Core'daki F# kitaplıklarını test etme birimi</span><span class="sxs-lookup"><span data-stu-id="89744-103">Unit testing F# libraries in .NET Core using dotnet test and xUnit</span></span>

<span data-ttu-id="89744-104">Bu öğretici, birim test kavramlarını öğrenmek için adım adım örnek bir çözüm oluşturma etkileşimli bir deneyim sunar.</span><span class="sxs-lookup"><span data-stu-id="89744-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="89744-105">Önceden oluşturulmuş bir çözüm kullanarak öğreticiyi izlemeyi tercih ederseniz, başlamadan önce [örnek kodu görüntüleyin veya indirin.](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp/)</span><span class="sxs-lookup"><span data-stu-id="89744-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp/) before you begin.</span></span> <span data-ttu-id="89744-106">İndirme talimatları için [Örnekler ve Öğreticiler'e](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)bakın.</span><span class="sxs-lookup"><span data-stu-id="89744-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="creating-the-source-project"></a><span data-ttu-id="89744-107">Kaynak proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="89744-107">Creating the source project</span></span>

<span data-ttu-id="89744-108">Bir kabuk penceresi açın.</span><span class="sxs-lookup"><span data-stu-id="89744-108">Open a shell window.</span></span> <span data-ttu-id="89744-109">Çözümü tutmak için *birim-test-fsharp adı* verilen bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="89744-109">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="89744-110">Bu yeni dizinin içinde, yeni bir çözüm oluşturmak için çalıştırın. `dotnet new sln`</span><span class="sxs-lookup"><span data-stu-id="89744-110">Inside this new directory, run `dotnet new sln` to create a new solution.</span></span> <span data-ttu-id="89744-111">Bu, hem sınıf kitaplığını hem de birim test projesini yönetmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="89744-111">This makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="89744-112">Çözüm dizininin içinde bir *MathService* dizini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="89744-112">Inside the solution directory, create a *MathService* directory.</span></span> <span data-ttu-id="89744-113">Dizin ve dosya yapısı şimdiye kadar aşağıda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="89744-113">The directory and file structure thus far is shown below:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="89744-114">*MathService'i* geçerli dizini `dotnet new classlib -lang "F#"` yapın ve kaynak projeyi oluşturmak için çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="89744-114">Make *MathService* the current directory, and run `dotnet new classlib -lang "F#"` to create the source project.</span></span> <span data-ttu-id="89744-115">Matematik hizmetinin başarısız bir uygulamasını oluşturursunuz:</span><span class="sxs-lookup"><span data-stu-id="89744-115">You'll create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="89744-116">Dizin geri *birim-test-with-fsharp* dizin değiştirin.</span><span class="sxs-lookup"><span data-stu-id="89744-116">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="89744-117">Sınıf `dotnet sln add .\MathService\MathService.fsproj` kitaplığı projesini çözüme eklemek için çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="89744-117">Run `dotnet sln add .\MathService\MathService.fsproj` to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="89744-118">Test projesini oluşturma</span><span class="sxs-lookup"><span data-stu-id="89744-118">Creating the test project</span></span>

<span data-ttu-id="89744-119">Ardından *MathService.Tests* dizinini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="89744-119">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="89744-120">Aşağıdaki anahat dizin yapısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="89744-120">The following outline shows the directory structure:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="89744-121">*MathService.Tests* dizinini geçerli dizini oluşturun ve yeni `dotnet new xunit -lang "F#"`bir proje oluşturun.</span><span class="sxs-lookup"><span data-stu-id="89744-121">Make the *MathService.Tests* directory the current directory and create a new project using `dotnet new xunit -lang "F#"`.</span></span> <span data-ttu-id="89744-122">Bu, test kitaplığı olarak xUnit kullanan bir test projesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="89744-122">This creates a test project that uses xUnit as the test library.</span></span> <span data-ttu-id="89744-123">Oluşturulan şablon *MathServiceTests.fsproj*test koşucusu yapılandırır:</span><span class="sxs-lookup"><span data-stu-id="89744-123">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

<span data-ttu-id="89744-124">Test projesi, birim testleri oluşturmak ve çalıştırmak için diğer paketler gerektirir.</span><span class="sxs-lookup"><span data-stu-id="89744-124">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="89744-125">`dotnet new`önceki adımda xUnit ve xUnit runner eklendi.</span><span class="sxs-lookup"><span data-stu-id="89744-125">`dotnet new` in the previous step added xUnit and the xUnit runner.</span></span> <span data-ttu-id="89744-126">Şimdi, `MathService` sınıf kitaplığını projeye başka bir bağımlılık olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="89744-126">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="89744-127">Komutu `dotnet add reference` kullanın:</span><span class="sxs-lookup"><span data-stu-id="89744-127">Use the `dotnet add reference` command:</span></span>

```dotnetcli
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="89744-128">Tüm dosyayı GitHub'daki [örnek deposunda](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="89744-128">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="89744-129">Aşağıdaki nihai çözüm düzenine sahipsiniz:</span><span class="sxs-lookup"><span data-stu-id="89744-129">You have the following final solution layout:</span></span>

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

<span data-ttu-id="89744-130">`dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` *Birim-test-with-fsharp* dizininde yürütün.</span><span class="sxs-lookup"><span data-stu-id="89744-130">Execute `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` in the *unit-testing-with-fsharp* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="89744-131">İlk testi oluşturma</span><span class="sxs-lookup"><span data-stu-id="89744-131">Creating the first test</span></span>

<span data-ttu-id="89744-132">Başarısız bir test yazarsın, geçer ve işlemi tekrarlarsın.</span><span class="sxs-lookup"><span data-stu-id="89744-132">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="89744-133">*Tests.fs'yi* açın ve aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="89744-133">Open *Tests.fs* and add the following code:</span></span>

```fsharp
[<Fact>]
let ``My test`` () =
    Assert.True(true)

[<Fact>]
let ``Fail every time`` () = Assert.True(false)
```

<span data-ttu-id="89744-134">Öznitelik, `[<Fact>]` test koşucusu tarafından çalıştırılabilen bir test yöntemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="89744-134">The `[<Fact>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="89744-135">*Birim-test-with-fsharp*itibaren, `dotnet test` testleri ve sınıf kitaplığı oluşturmak ve daha sonra testleri çalıştırmak için çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="89744-135">From the *unit-testing-with-fsharp*, execute `dotnet test` to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="89744-136">xUnit test koşucusu, testlerinizi çalıştırmak için program giriş noktasını içerir.</span><span class="sxs-lookup"><span data-stu-id="89744-136">The xUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="89744-137">`dotnet test`oluşturduğunuz birim test projesini kullanarak test koşucusu başlatın.</span><span class="sxs-lookup"><span data-stu-id="89744-137">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="89744-138">Bu iki test, en temel geçen ve başarısız testleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="89744-138">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="89744-139">`My test`geçer ve `Fail every time` başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="89744-139">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="89744-140">Şimdi, `squaresOfOdds` yöntem için bir test oluşturun.</span><span class="sxs-lookup"><span data-stu-id="89744-140">Now, create a test for the `squaresOfOdds` method.</span></span> <span data-ttu-id="89744-141">Yöntem, `squaresOfOdds` giriş sırasının bir parçası olan tüm tek tamsayı değerlerinin karelerinin bir sırasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="89744-141">The `squaresOfOdds` method returns a sequence of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="89744-142">Tüm bu işlevleri aynı anda yazmaya çalışmak yerine, işlevselliği doğrulayan testleri yinelemeli olarak oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="89744-142">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="89744-143">Her test geçişini yapmak, yöntem için gerekli işlevselliği oluşturmak anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="89744-143">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="89744-144">Yazabileceğimiz en basit test, `squaresOfOdds` sonucun boş bir toplamdarık dizisi olması gereken tüm çift sayılarla aramaktır.</span><span class="sxs-lookup"><span data-stu-id="89744-144">The simplest test we can write is to call `squaresOfOdds` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="89744-145">İşte o test:</span><span class="sxs-lookup"><span data-stu-id="89744-145">Here's that test:</span></span>

```fsharp
[<Fact>]
let ``Sequence of Evens returns empty collection`` () =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

<span data-ttu-id="89744-146">Sınavın başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="89744-146">Your test fails.</span></span> <span data-ttu-id="89744-147">Uygulamayı henüz oluşturmadın.</span><span class="sxs-lookup"><span data-stu-id="89744-147">You haven't created the implementation yet.</span></span> <span data-ttu-id="89744-148">Bu testin çalışmasını sağlayan `MathService` sınıftaki en basit kodu yazarak geçmesini sağla:</span><span class="sxs-lookup"><span data-stu-id="89744-148">Make this test pass by writing the simplest code in the `MathService` class that works:</span></span>

```fsharp
let squaresOfOdds xs =
    Seq.empty<int>
```

<span data-ttu-id="89744-149">*Birim-test-fsharp* dizininde, yeniden çalıştırın. `dotnet test`</span><span class="sxs-lookup"><span data-stu-id="89744-149">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="89744-150">Komut, `dotnet test` proje ve ardından `MathService.Tests` proje için bir yapı çalışır. `MathService`</span><span class="sxs-lookup"><span data-stu-id="89744-150">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="89744-151">Her iki projeyi de yaptıktan sonra, bu tek testi çalıştırAr.</span><span class="sxs-lookup"><span data-stu-id="89744-151">After building both projects, it runs this single test.</span></span> <span data-ttu-id="89744-152">Geçiyor.</span><span class="sxs-lookup"><span data-stu-id="89744-152">It passes.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="89744-153">Gereksinimleri nama</span><span class="sxs-lookup"><span data-stu-id="89744-153">Completing the requirements</span></span>

<span data-ttu-id="89744-154">Artık bir test sınavını geçtiğine göre, daha fazla yazma nın zamanı.</span><span class="sxs-lookup"><span data-stu-id="89744-154">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="89744-155">Sonraki basit durum, tek sayısı `1`.</span><span class="sxs-lookup"><span data-stu-id="89744-155">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="89744-156">1'in karesi 1 olduğundan 1 sayısı daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="89744-156">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="89744-157">İşte bir sonraki test:</span><span class="sxs-lookup"><span data-stu-id="89744-157">Here's that next test:</span></span>

```fsharp
[<Fact>]
let ``Sequences of Ones and Evens returns Ones`` () =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

<span data-ttu-id="89744-158">Yürütme `dotnet test` testlerinizi çalıştırıyor ve yeni testin başarısız olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="89744-158">Executing `dotnet test` runs your tests and shows you that the new test fails.</span></span> <span data-ttu-id="89744-159">Şimdi, bu `squaresOfOdds` yeni testi işlemek için yöntemi güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="89744-159">Now, update the `squaresOfOdds` method to handle this new test.</span></span> <span data-ttu-id="89744-160">Bu testin geçmesini sağlamak için tüm çift sayıları sıranın dışına süzersiniz.</span><span class="sxs-lookup"><span data-stu-id="89744-160">You filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="89744-161">Bunu küçük bir filtre işlevi yazarak `Seq.filter`ve şu ları kullanarak yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="89744-161">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

<span data-ttu-id="89744-162">Daha bir adım daha var: Tek sayıların her birini karelemek.</span><span class="sxs-lookup"><span data-stu-id="89744-162">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="89744-163">Yeni bir test yazarak başlayın:</span><span class="sxs-lookup"><span data-stu-id="89744-163">Start by writing a new test:</span></span>

```fsharp
[<Fact>]
let ``SquaresOfOdds works`` () =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.Equal(expected, actual)
```

<span data-ttu-id="89744-164">Her tek sayının karesini hesaplamak için filtreuygulanmış sırayı bir harita işlemi yle borulandırarak testi düzeltebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="89744-164">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
```

<span data-ttu-id="89744-165">O kitaplık için küçük bir kitaplık ve bir dizi birim testi inşa ettin.</span><span class="sxs-lookup"><span data-stu-id="89744-165">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="89744-166">Yeni paketler ve testler eklemek normal iş akışının bir parçası olacak şekilde çözümü yapılandırdınız.</span><span class="sxs-lookup"><span data-stu-id="89744-166">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="89744-167">Zamanınızın ve çabanızın çoğunu uygulamanın hedeflerini çözmeye yoğunlaşmışsınız.</span><span class="sxs-lookup"><span data-stu-id="89744-167">You've concentrated most of your time and effort on solving the goals of the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="89744-168">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89744-168">See also</span></span>

- [<span data-ttu-id="89744-169">dotnet new</span><span class="sxs-lookup"><span data-stu-id="89744-169">dotnet new</span></span>](../tools/dotnet-new.md)
- [<span data-ttu-id="89744-170">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="89744-170">dotnet sln</span></span>](../tools/dotnet-new.md)
- [<span data-ttu-id="89744-171">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="89744-171">dotnet add reference</span></span>](../tools/dotnet-add-reference.md)
- [<span data-ttu-id="89744-172">dotnet test</span><span class="sxs-lookup"><span data-stu-id="89744-172">dotnet test</span></span>](../tools/dotnet-test.md)
