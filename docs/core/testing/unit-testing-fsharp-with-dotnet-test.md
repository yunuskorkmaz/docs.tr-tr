---
title: "DotNet test ve xUnit ile .NET Core 'da birim testi F #"
description: ".NET Core 'daki F # için birim testi kavramlarını, DotNet test ve xUnit kullanarak örnek bir çözüm oluşturma adlı etkileşimli bir deneyim aracılığıyla öğrenin."
author: billwagner
ms.author: wiwagn
ms.date: 08/30/2017
ms.openlocfilehash: e0f2b6f88a650f412148f51cc0236fa46ed8c618
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656559"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-xunit"></a><span data-ttu-id="b918e-103">DotNet test ve xUnit kullanarak .NET Core 'daki birim testi F # kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="b918e-103">Unit testing F# libraries in .NET Core using dotnet test and xUnit</span></span>

<span data-ttu-id="b918e-104">Bu öğreticide, birim testi kavramlarını öğrenmek için bir örnek çözüm oluşturma adım adım yönergeler sunarak etkileşimli bir deneyim sağlanır.</span><span class="sxs-lookup"><span data-stu-id="b918e-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="b918e-105">Önceden oluşturulmuş bir çözüm kullanarak öğreticiyi izlemeyi tercih ediyorsanız, başlamadan önce [örnek kodu görüntüleyin veya indirin](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp/) .</span><span class="sxs-lookup"><span data-stu-id="b918e-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp/) before you begin.</span></span> <span data-ttu-id="b918e-106">İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#view-and-download-samples).</span><span class="sxs-lookup"><span data-stu-id="b918e-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#view-and-download-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="creating-the-source-project"></a><span data-ttu-id="b918e-107">Kaynak proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="b918e-107">Creating the source project</span></span>

<span data-ttu-id="b918e-108">Bir kabuk penceresi açın.</span><span class="sxs-lookup"><span data-stu-id="b918e-108">Open a shell window.</span></span> <span data-ttu-id="b918e-109">Çözümü tutmak için- *FSharp ile birim-test* adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b918e-109">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="b918e-110">Yeni bir çözüm oluşturmak için bu yeni dizinin içinde öğesini çalıştırın `dotnet new sln` .</span><span class="sxs-lookup"><span data-stu-id="b918e-110">Inside this new directory, run `dotnet new sln` to create a new solution.</span></span> <span data-ttu-id="b918e-111">Bu, hem sınıf kitaplığını hem de birim testi projesini yönetmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="b918e-111">This makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="b918e-112">Çözüm dizini içinde bir *MathService* dizini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b918e-112">Inside the solution directory, create a *MathService* directory.</span></span> <span data-ttu-id="b918e-113">Bu nedenle şu ana kadar dizin ve dosya yapısı aşağıda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="b918e-113">The directory and file structure thus far is shown below:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="b918e-114">*MathService* geçerli dizin yapın ve `dotnet new classlib -lang "F#"` kaynak projeyi oluşturmak için çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b918e-114">Make *MathService* the current directory, and run `dotnet new classlib -lang "F#"` to create the source project.</span></span> <span data-ttu-id="b918e-115">Matematik hizmeti için başarısız bir uygulama oluşturacaksınız:</span><span class="sxs-lookup"><span data-stu-id="b918e-115">You'll create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="b918e-116">Dizini- *FSharp dizinine sahip birim-test ile* yeniden değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b918e-116">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="b918e-117">`dotnet sln add .\MathService\MathService.fsproj`Çözüme Sınıf Kitaplığı projesini eklemek için ' i çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b918e-117">Run `dotnet sln add .\MathService\MathService.fsproj` to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="b918e-118">Test projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="b918e-118">Creating the test project</span></span>

<span data-ttu-id="b918e-119">Sonra, *MathService. Tests* dizinini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b918e-119">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="b918e-120">Aşağıdaki ana hat dizin yapısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="b918e-120">The following outline shows the directory structure:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="b918e-121">*MathService. Tests* dizinini geçerli dizin yapın ve kullanarak yeni bir proje oluşturun `dotnet new xunit -lang "F#"` .</span><span class="sxs-lookup"><span data-stu-id="b918e-121">Make the *MathService.Tests* directory the current directory and create a new project using `dotnet new xunit -lang "F#"`.</span></span> <span data-ttu-id="b918e-122">Bu, test kitaplığı olarak xUnit kullanan bir test projesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b918e-122">This creates a test project that uses xUnit as the test library.</span></span> <span data-ttu-id="b918e-123">Oluşturulan şablon, *MathServiceTests. fsproj*içindeki Test Çalıştırıcısı 'nı yapılandırır:</span><span class="sxs-lookup"><span data-stu-id="b918e-123">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

<span data-ttu-id="b918e-124">Test projesi, birim testlerini oluşturmak ve çalıştırmak için diğer paketlerin kullanılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b918e-124">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="b918e-125">`dotnet new` önceki adımda xUnit ve xUnit Çalıştırıcısı eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="b918e-125">`dotnet new` in the previous step added xUnit and the xUnit runner.</span></span> <span data-ttu-id="b918e-126">Şimdi, `MathService` sınıf kitaplığını projeye başka bir bağımlılık olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b918e-126">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="b918e-127">Şu `dotnet add reference` komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="b918e-127">Use the `dotnet add reference` command:</span></span>

```dotnetcli
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="b918e-128">GitHub 'daki [örnekler deposunda](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) dosyanın tamamını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b918e-128">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="b918e-129">Aşağıdaki son çözüm düzenine sahipsiniz:</span><span class="sxs-lookup"><span data-stu-id="b918e-129">You have the following final solution layout:</span></span>

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

<span data-ttu-id="b918e-130">- `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` FSharp diziniyle *birlikte birim-test* ' i çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b918e-130">Execute `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` in the *unit-testing-with-fsharp* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="b918e-131">İlk test oluşturma</span><span class="sxs-lookup"><span data-stu-id="b918e-131">Creating the first test</span></span>

<span data-ttu-id="b918e-132">Başarısız bir test yazdığınızda, geçişi yapıp işlemi tekrarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b918e-132">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="b918e-133">*Tests. FS* ' i açın ve aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b918e-133">Open *Tests.fs* and add the following code:</span></span>

```fsharp
[<Fact>]
let ``My test`` () =
    Assert.True(true)

[<Fact>]
let ``Fail every time`` () = Assert.True(false)
```

<span data-ttu-id="b918e-134">`[<Fact>]`Öznitelik, Test Çalıştırıcısı tarafından çalıştırılan bir test yöntemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b918e-134">The `[<Fact>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="b918e-135">- *FSharp olan birim-test*' den, `dotnet test` Testleri ve sınıf kitaplığını oluşturmak için yürütün ve ardından testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b918e-135">From the *unit-testing-with-fsharp*, execute `dotnet test` to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="b918e-136">XUnit Test Çalıştırıcısı, testlerinizi çalıştırmak için program giriş noktasını içerir.</span><span class="sxs-lookup"><span data-stu-id="b918e-136">The xUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="b918e-137">`dotnet test` oluşturduğunuz birim test projesini kullanarak Test Çalıştırıcısı başlatır.</span><span class="sxs-lookup"><span data-stu-id="b918e-137">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="b918e-138">Bu iki test, en temel geçirme ve başarısız testleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="b918e-138">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="b918e-139">`My test` geçirilir ve `Fail every time` başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="b918e-139">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="b918e-140">Şimdi, yöntemi için bir test oluşturun `squaresOfOdds` .</span><span class="sxs-lookup"><span data-stu-id="b918e-140">Now, create a test for the `squaresOfOdds` method.</span></span> <span data-ttu-id="b918e-141">`squaresOfOdds`Yöntemi, giriş dizisinin parçası olan tüm tek tamsayı değerlerinin karelerinin dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="b918e-141">The `squaresOfOdds` method returns a sequence of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="b918e-142">Bu işlevlerin tümünü aynı anda yazmaya çalışmak yerine, işlevi doğrulayan testleri tekrarlayarak oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b918e-142">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="b918e-143">Her test geçişinin yapılması, yöntemi için gerekli işlevselliğin oluşturulması anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b918e-143">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="b918e-144">Yazdığımız en basit test, `squaresOfOdds` sonucun boş bir tamsayılar dizisi olması gereken tüm çift sayılarla çağrıdır.</span><span class="sxs-lookup"><span data-stu-id="b918e-144">The simplest test we can write is to call `squaresOfOdds` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="b918e-145">Bu test şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="b918e-145">Here's that test:</span></span>

```fsharp
[<Fact>]
let ``Sequence of Evens returns empty collection`` () =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

<span data-ttu-id="b918e-146">Testiniz başarısız oluyor.</span><span class="sxs-lookup"><span data-stu-id="b918e-146">Your test fails.</span></span> <span data-ttu-id="b918e-147">Uygulamayı henüz oluşturmadınız.</span><span class="sxs-lookup"><span data-stu-id="b918e-147">You haven't created the implementation yet.</span></span> <span data-ttu-id="b918e-148">Bu test geçişini, çalıştıran sınıfa en basit kodu yazarak yapın `MathService` :</span><span class="sxs-lookup"><span data-stu-id="b918e-148">Make this test pass by writing the simplest code in the `MathService` class that works:</span></span>

```fsharp
let squaresOfOdds xs =
    Seq.empty<int>
```

<span data-ttu-id="b918e-149">*Birim-test--FSharp diziniyle birlikte* `dotnet test` yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b918e-149">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="b918e-150">`dotnet test`Komutu, proje için bir yapı `MathService` ve ardından proje için çalışır `MathService.Tests` .</span><span class="sxs-lookup"><span data-stu-id="b918e-150">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="b918e-151">Her iki proje de oluşturulduktan sonra bu tek testi çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="b918e-151">After building both projects, it runs this single test.</span></span> <span data-ttu-id="b918e-152">Geçirir.</span><span class="sxs-lookup"><span data-stu-id="b918e-152">It passes.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="b918e-153">Gereksinimleri tamamlama</span><span class="sxs-lookup"><span data-stu-id="b918e-153">Completing the requirements</span></span>

<span data-ttu-id="b918e-154">Artık bir test geçişi yapmış olduğunuza göre daha fazla yazma zamanı vardır.</span><span class="sxs-lookup"><span data-stu-id="b918e-154">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="b918e-155">Bir sonraki basit durum yalnızca tek sayı olan bir sıra ile birlikte kullanılır `1` .</span><span class="sxs-lookup"><span data-stu-id="b918e-155">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="b918e-156">1 numaralı kare 1 olduğundan, 1 sayısı daha kolay.</span><span class="sxs-lookup"><span data-stu-id="b918e-156">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="b918e-157">İşte bu sonraki test:</span><span class="sxs-lookup"><span data-stu-id="b918e-157">Here's that next test:</span></span>

```fsharp
[<Fact>]
let ``Sequences of Ones and Evens returns Ones`` () =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

<span data-ttu-id="b918e-158">Yürütme, `dotnet test` testlerinizi çalıştırır ve yeni testin başarısız olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b918e-158">Executing `dotnet test` runs your tests and shows you that the new test fails.</span></span> <span data-ttu-id="b918e-159">Şimdi `squaresOfOdds` Bu yeni testi işleyecek yöntemi güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="b918e-159">Now, update the `squaresOfOdds` method to handle this new test.</span></span> <span data-ttu-id="b918e-160">Bu test geçişini yapmak için tüm çift sayıları sıranın dışına filtreleyin.</span><span class="sxs-lookup"><span data-stu-id="b918e-160">You filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="b918e-161">Bunu, küçük bir filtre işlevi yazarak ve kullanarak yapabilirsiniz `Seq.filter` :</span><span class="sxs-lookup"><span data-stu-id="b918e-161">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

<span data-ttu-id="b918e-162">Bir adım daha vardır: her bir tek sayının kare sayısı.</span><span class="sxs-lookup"><span data-stu-id="b918e-162">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="b918e-163">Yeni bir test yazarak başlayın:</span><span class="sxs-lookup"><span data-stu-id="b918e-163">Start by writing a new test:</span></span>

```fsharp
[<Fact>]
let ``SquaresOfOdds works`` () =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.Equal(expected, actual)
```

<span data-ttu-id="b918e-164">Her bir tek sayının karesini hesaplamak için, filtre uygulanmış sırayı bir eşleme işlemi aracılığıyla ayırarak testi giderebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b918e-164">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
```

<span data-ttu-id="b918e-165">Bu kitaplık için küçük bir kitaplık ve birim testleri kümesi oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="b918e-165">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="b918e-166">Çözümü, yeni paket ve test eklemek normal iş akışının bir parçası olacak şekilde öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="b918e-166">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="b918e-167">Uygulamanın hedeflerini çözme konusunda zaman ve çaba harcamanızı en iyi şekilde gördünüz.</span><span class="sxs-lookup"><span data-stu-id="b918e-167">You've concentrated most of your time and effort on solving the goals of the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="b918e-168">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b918e-168">See also</span></span>

- [<span data-ttu-id="b918e-169">dotnet new</span><span class="sxs-lookup"><span data-stu-id="b918e-169">dotnet new</span></span>](../tools/dotnet-new.md)
- [<span data-ttu-id="b918e-170">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="b918e-170">dotnet sln</span></span>](../tools/dotnet-new.md)
- [<span data-ttu-id="b918e-171">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="b918e-171">dotnet add reference</span></span>](../tools/dotnet-add-reference.md)
- [<span data-ttu-id="b918e-172">dotnet test</span><span class="sxs-lookup"><span data-stu-id="b918e-172">dotnet test</span></span>](../tools/dotnet-test.md)
