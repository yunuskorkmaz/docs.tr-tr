---
title: DotNet test F# ve xUnit Ile .NET Core 'da birim testi
description: .NET Core F# 'da, DotNet test ve xUnit kullanarak bir örnek çözüm oluşturma adlı etkileşimli bir deneyim aracılığıyla birim testi kavramlarını öğrenin.
author: billwagner
ms.author: wiwagn
ms.date: 08/30/2017
ms.custom: seodec18
ms.openlocfilehash: 7fd4a3e9629a497ba3650bd24f535e864bd68820
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71116617"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-xunit"></a><span data-ttu-id="69b9f-103">DotNet test F# ve xUnit kullanarak .NET Core 'da birim testi kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="69b9f-103">Unit testing F# libraries in .NET Core using dotnet test and xUnit</span></span>

<span data-ttu-id="69b9f-104">Bu öğreticide, birim testi kavramlarını öğrenmek için bir örnek çözüm oluşturma adım adım yönergeler sunarak etkileşimli bir deneyim sağlanır.</span><span class="sxs-lookup"><span data-stu-id="69b9f-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="69b9f-105">Önceden oluşturulmuş bir çözüm kullanarak öğreticiyi izlemeyi tercih ediyorsanız, başlamadan önce [örnek kodu görüntüleyin veya indirin](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp/) .</span><span class="sxs-lookup"><span data-stu-id="69b9f-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp/) before you begin.</span></span> <span data-ttu-id="69b9f-106">İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="69b9f-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="creating-the-source-project"></a><span data-ttu-id="69b9f-107">Kaynak proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="69b9f-107">Creating the source project</span></span>

<span data-ttu-id="69b9f-108">Bir kabuk penceresi açın.</span><span class="sxs-lookup"><span data-stu-id="69b9f-108">Open a shell window.</span></span> <span data-ttu-id="69b9f-109">Çözümü tutmak için- *FSharp ile birim-test* adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="69b9f-109">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="69b9f-110">Yeni bir çözüm oluşturmak için bu [`dotnet new sln`](../tools/dotnet-new.md) yeni dizinin içinde öğesini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="69b9f-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="69b9f-111">Bu, hem sınıf kitaplığını hem de birim testi projesini yönetmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="69b9f-111">This makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="69b9f-112">Çözüm dizini içinde bir *MathService* dizini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="69b9f-112">Inside the solution directory, create a *MathService* directory.</span></span> <span data-ttu-id="69b9f-113">Bu nedenle şu ana kadar dizin ve dosya yapısı aşağıda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="69b9f-113">The directory and file structure thus far is shown below:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="69b9f-114">*MathService* geçerli dizin yapın ve kaynak projeyi [`dotnet new classlib -lang F#`](../tools/dotnet-new.md) oluşturmak için çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="69b9f-114">Make *MathService* the current directory and run [`dotnet new classlib -lang F#`](../tools/dotnet-new.md) to create the source project.</span></span>  <span data-ttu-id="69b9f-115">Matematik hizmeti için başarısız bir uygulama oluşturacaksınız:</span><span class="sxs-lookup"><span data-stu-id="69b9f-115">You'll create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="69b9f-116">Dizini- *FSharp dizinine sahip birim-test ile* yeniden değiştirin.</span><span class="sxs-lookup"><span data-stu-id="69b9f-116">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="69b9f-117">Çözüme [`dotnet sln add .\MathService\MathService.fsproj`](../tools/dotnet-sln.md) Sınıf Kitaplığı projesini eklemek için ' i çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="69b9f-117">Run [`dotnet sln add .\MathService\MathService.fsproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="69b9f-118">Test projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="69b9f-118">Creating the test project</span></span>

<span data-ttu-id="69b9f-119">Sonra, *MathService. Tests* dizinini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="69b9f-119">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="69b9f-120">Aşağıdaki ana hat dizin yapısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="69b9f-120">The following outline shows the directory structure:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="69b9f-121">*MathService. Tests* dizinini geçerli dizin yapın ve kullanarak [`dotnet new xunit -lang F#`](../tools/dotnet-new.md)yeni bir proje oluşturun.</span><span class="sxs-lookup"><span data-stu-id="69b9f-121">Make the *MathService.Tests* directory the current directory and create a new project using [`dotnet new xunit -lang F#`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="69b9f-122">Bu, test kitaplığı olarak xUnit kullanan bir test projesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="69b9f-122">This creates a test project that uses xUnit as the test library.</span></span> <span data-ttu-id="69b9f-123">Oluşturulan şablon, *MathServiceTests. fsproj*içindeki Test Çalıştırıcısı 'nı yapılandırır:</span><span class="sxs-lookup"><span data-stu-id="69b9f-123">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

<span data-ttu-id="69b9f-124">Test projesi, birim testlerini oluşturmak ve çalıştırmak için diğer paketlerin kullanılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="69b9f-124">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="69b9f-125">`dotnet new`önceki adımda xUnit ve xUnit Çalıştırıcısı eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="69b9f-125">`dotnet new` in the previous step added xUnit and the xUnit runner.</span></span> <span data-ttu-id="69b9f-126">Şimdi, `MathService` sınıf kitaplığını projeye başka bir bağımlılık olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="69b9f-126">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="69b9f-127">[`dotnet add reference`](../tools/dotnet-add-reference.md) Şu komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="69b9f-127">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="69b9f-128">GitHub 'daki [örnekler deposunda](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) dosyanın tamamını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="69b9f-128">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="69b9f-129">Aşağıdaki son çözüm düzenine sahipsiniz:</span><span class="sxs-lookup"><span data-stu-id="69b9f-129">You have the following final solution layout:</span></span>

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

<span data-ttu-id="69b9f-130">\- [`dotnet sln add .\MathService.Tests\MathService.Tests.fsproj`](../tools/dotnet-sln.md) FSharp diziniyle *birlikte birim-test* ' i çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="69b9f-130">Execute [`dotnet sln add .\MathService.Tests\MathService.Tests.fsproj`](../tools/dotnet-sln.md) in the *unit-testing-with-fsharp* directory.</span></span> 

## <a name="creating-the-first-test"></a><span data-ttu-id="69b9f-131">İlk test oluşturma</span><span class="sxs-lookup"><span data-stu-id="69b9f-131">Creating the first test</span></span>

<span data-ttu-id="69b9f-132">Başarısız bir test yazdığınızda, geçişi yapıp işlemi tekrarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="69b9f-132">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="69b9f-133">*Tests. FS* ' i açın ve aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="69b9f-133">Open *Tests.fs* and add the following code:</span></span>

```fsharp
[<Fact>]
let ``My test`` () =
    Assert.True(true)

[<Fact>]
let ``Fail every time`` () = Assert.True(false)
```

<span data-ttu-id="69b9f-134">`[<Fact>]` Öznitelik, Test Çalıştırıcısı tarafından çalıştırılan bir test yöntemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="69b9f-134">The `[<Fact>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="69b9f-135">\- *FSharp olan birim-test*' den, testleri ve [`dotnet test`](../tools/dotnet-test.md) sınıf kitaplığını oluşturmak için yürütün ve ardından testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="69b9f-135">From the *unit-testing-with-fsharp*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="69b9f-136">XUnit Test Çalıştırıcısı, testlerinizi çalıştırmak için program giriş noktasını içerir.</span><span class="sxs-lookup"><span data-stu-id="69b9f-136">The xUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="69b9f-137">`dotnet test`oluşturduğunuz birim test projesini kullanarak Test Çalıştırıcısı başlatır.</span><span class="sxs-lookup"><span data-stu-id="69b9f-137">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="69b9f-138">Bu iki test, en temel geçirme ve başarısız testleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="69b9f-138">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="69b9f-139">`My test`geçirilir ve `Fail every time` başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="69b9f-139">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="69b9f-140">Şimdi, `squaresOfOdds` yöntemi için bir test oluşturun.</span><span class="sxs-lookup"><span data-stu-id="69b9f-140">Now, create a test for the `squaresOfOdds` method.</span></span> <span data-ttu-id="69b9f-141">`squaresOfOdds` Yöntemi, giriş dizisinin parçası olan tüm tek tamsayı değerlerinin karelerinin dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="69b9f-141">The `squaresOfOdds` method returns a sequence of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="69b9f-142">Bu işlevlerin tümünü aynı anda yazmaya çalışmak yerine, işlevi doğrulayan testleri tekrarlayarak oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="69b9f-142">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="69b9f-143">Her test geçişinin yapılması, yöntemi için gerekli işlevselliğin oluşturulması anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="69b9f-143">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="69b9f-144">Yazdığımız en basit test, sonucun boş bir `squaresOfOdds` tamsayılar dizisi olması gereken tüm çift sayılarla çağrıdır.</span><span class="sxs-lookup"><span data-stu-id="69b9f-144">The simplest test we can write is to call `squaresOfOdds` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="69b9f-145">Bu test şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="69b9f-145">Here's that test:</span></span>

```fsharp
[<Fact>]
let ``Sequence of Evens returns empty collection`` () =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

<span data-ttu-id="69b9f-146">Testiniz başarısız oluyor.</span><span class="sxs-lookup"><span data-stu-id="69b9f-146">Your test fails.</span></span> <span data-ttu-id="69b9f-147">Uygulamayı henüz oluşturmadınız.</span><span class="sxs-lookup"><span data-stu-id="69b9f-147">You haven't created the implementation yet.</span></span> <span data-ttu-id="69b9f-148">Bu test geçişini, çalıştıran `MathService` sınıfa en basit kodu yazarak yapın:</span><span class="sxs-lookup"><span data-stu-id="69b9f-148">Make this test pass by writing the simplest code in the `MathService` class that works:</span></span>

```fsharp
let squaresOfOdds xs =
    Seq.empty<int>
```

<span data-ttu-id="69b9f-149">*Birim-test--FSharp diziniyle birlikte* yeniden çalıştırın `dotnet test` .</span><span class="sxs-lookup"><span data-stu-id="69b9f-149">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="69b9f-150">Komutu, `MathService` proje için bir yapı ve ardından projeiçinçalışır.`MathService.Tests` `dotnet test`</span><span class="sxs-lookup"><span data-stu-id="69b9f-150">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="69b9f-151">Her iki proje de oluşturulduktan sonra bu tek testi çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="69b9f-151">After building both projects, it runs this single test.</span></span> <span data-ttu-id="69b9f-152">Geçirir.</span><span class="sxs-lookup"><span data-stu-id="69b9f-152">It passes.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="69b9f-153">Gereksinimleri tamamlama</span><span class="sxs-lookup"><span data-stu-id="69b9f-153">Completing the requirements</span></span>

<span data-ttu-id="69b9f-154">Artık bir test geçişi yapmış olduğunuza göre daha fazla yazma zamanı vardır.</span><span class="sxs-lookup"><span data-stu-id="69b9f-154">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="69b9f-155">Bir sonraki basit durum yalnızca tek sayı olan bir sıra ile birlikte kullanılır `1`.</span><span class="sxs-lookup"><span data-stu-id="69b9f-155">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="69b9f-156">1 numaralı kare 1 olduğundan, 1 sayısı daha kolay.</span><span class="sxs-lookup"><span data-stu-id="69b9f-156">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="69b9f-157">İşte bu sonraki test:</span><span class="sxs-lookup"><span data-stu-id="69b9f-157">Here's that next test:</span></span>

```fsharp
[<Fact>]
let ``Sequences of Ones and Evens returns Ones`` () =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

<span data-ttu-id="69b9f-158">Yürütme `dotnet test` , testlerinizi çalıştırır ve yeni testin başarısız olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="69b9f-158">Executing `dotnet test` runs your tests and shows you that the new test fails.</span></span> <span data-ttu-id="69b9f-159">Şimdi bu yeni testi `squaresOfOdds` işleyecek yöntemi güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="69b9f-159">Now, update the `squaresOfOdds` method to handle this new test.</span></span> <span data-ttu-id="69b9f-160">Bu test geçişini yapmak için tüm çift sayıları sıranın dışına filtreleyin.</span><span class="sxs-lookup"><span data-stu-id="69b9f-160">You filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="69b9f-161">Bunu, küçük bir filtre işlevi yazarak ve kullanarak `Seq.filter`yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="69b9f-161">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

<span data-ttu-id="69b9f-162">Bir adım daha vardır: her bir tek sayının kare sayısı.</span><span class="sxs-lookup"><span data-stu-id="69b9f-162">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="69b9f-163">Yeni bir test yazarak başlayın:</span><span class="sxs-lookup"><span data-stu-id="69b9f-163">Start by writing a new test:</span></span>

```fsharp
[<Fact>]
let ``SquaresOfOdds works`` () =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.Equal(expected, actual)
```

<span data-ttu-id="69b9f-164">Her bir tek sayının karesini hesaplamak için, filtre uygulanmış sırayı bir eşleme işlemi aracılığıyla ayırarak testi giderebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="69b9f-164">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs = 
    xs 
    |> Seq.filter isOdd 
    |> Seq.map square
```

<span data-ttu-id="69b9f-165">Bu kitaplık için küçük bir kitaplık ve birim testleri kümesi oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="69b9f-165">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="69b9f-166">Çözümü, yeni paket ve test eklemek normal iş akışının bir parçası olacak şekilde öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="69b9f-166">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="69b9f-167">Uygulamanın hedeflerini çözme konusunda zaman ve çaba harcamanızı en iyi şekilde gördünüz.</span><span class="sxs-lookup"><span data-stu-id="69b9f-167">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
