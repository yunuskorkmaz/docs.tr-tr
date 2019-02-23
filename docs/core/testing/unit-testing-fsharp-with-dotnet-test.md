---
title: Birim testi F# .NET core'da dotnet testi ve xUnit ile
description: Birim test kavramlarını öğrenin F# dotnet testi ve xUnit, adım adım örnek çözüm oluşturma etkileşimli deneyim aracılığıyla .NET Core kullanarak.
author: billwagner
ms.author: wiwagn
ms.date: 08/30/2017
dev_langs:
- fsharp
ms.custom: seodec18
ms.openlocfilehash: 9765c463bb427f79dcd0308e7e4fc643fdc06968
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56745952"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-xunit"></a><span data-ttu-id="df4fe-103">Birim testi F# kitaplıkları .NET core'da dotnet testi ve xUnit kullanma</span><span class="sxs-lookup"><span data-stu-id="df4fe-103">Unit testing F# libraries in .NET Core using dotnet test and xUnit</span></span>

<span data-ttu-id="df4fe-104">Bu öğretici örnek bir çözüm birim testi kavramlarını öğrenmek için adım adım oluşturmaya etkileşimli deneyim gösterir.</span><span class="sxs-lookup"><span data-stu-id="df4fe-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="df4fe-105">Önceden oluşturulmuş bir çözümü kullanarak öğreticiyi uygulamak isterseniz [görüntülemek veya örnek kodu indirdikten](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp/) başlamadan önce.</span><span class="sxs-lookup"><span data-stu-id="df4fe-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp/) before you begin.</span></span> <span data-ttu-id="df4fe-106">Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="df4fe-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="df4fe-107">Kaynak proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="df4fe-107">Creating the source project</span></span>

<span data-ttu-id="df4fe-108">Shell penceresini açın.</span><span class="sxs-lookup"><span data-stu-id="df4fe-108">Open a shell window.</span></span> <span data-ttu-id="df4fe-109">Adlı bir dizin oluşturun *birim-test-ile-fsharp* çözüm tutacak.</span><span class="sxs-lookup"><span data-stu-id="df4fe-109">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="df4fe-110">Bu yeni dizin içinde çalıştırma [ `dotnet new sln` ](../tools/dotnet-new.md) yeni bir çözüm oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="df4fe-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="df4fe-111">Bu, hem sınıf kitaplığı ve birim testi projesi yönetmenizi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="df4fe-111">This makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="df4fe-112">Çözüm dizini içinde bir *MathService* dizin.</span><span class="sxs-lookup"><span data-stu-id="df4fe-112">Inside the solution directory, create a *MathService* directory.</span></span> <span data-ttu-id="df4fe-113">Dizin ve dosya yapısı, şimdiye kadarki aşağıda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="df4fe-113">The directory and file structure thus far is shown below:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="df4fe-114">Olun *MathService* geçerli dizin ve çalışma [ `dotnet new classlib -lang F#` ](../tools/dotnet-new.md) kaynak proje oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="df4fe-114">Make *MathService* the current directory and run [`dotnet new classlib -lang F#`](../tools/dotnet-new.md) to create the source project.</span></span>  <span data-ttu-id="df4fe-115">Matematik hizmet başarısız uyarlamasını oluşturacaksınız:</span><span class="sxs-lookup"><span data-stu-id="df4fe-115">You'll create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="df4fe-116">Dizine dön değişiklik *birim-test-ile-fsharp* dizin.</span><span class="sxs-lookup"><span data-stu-id="df4fe-116">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="df4fe-117">Çalıştırma [ `dotnet sln add .\MathService\MathService.fsproj` ](../tools/dotnet-sln.md) sınıf kitaplığı projesi çözüme eklemek için.</span><span class="sxs-lookup"><span data-stu-id="df4fe-117">Run [`dotnet sln add .\MathService\MathService.fsproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="df4fe-118">Test projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="df4fe-118">Creating the test project</span></span>

<span data-ttu-id="df4fe-119">Ardından, oluşturma *MathService.Tests* dizin.</span><span class="sxs-lookup"><span data-stu-id="df4fe-119">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="df4fe-120">Ana hat aşağıdaki dizin yapısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="df4fe-120">The following outline shows the directory structure:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="df4fe-121">Olun *MathService.Tests* dizini geçerli dizin ve kullanarak yeni bir proje oluşturma [ `dotnet new xunit -lang F#` ](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="df4fe-121">Make the *MathService.Tests* directory the current directory and create a new project using [`dotnet new xunit -lang F#`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="df4fe-122">Bu, xUnit test kitaplık olarak kullanan bir test projesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="df4fe-122">This creates a test project that uses xUnit as the test library.</span></span> <span data-ttu-id="df4fe-123">Test Çalıştırıcısı'nda oluşturulan şablon yapılandırır *MathServiceTests.fsproj*:</span><span class="sxs-lookup"><span data-stu-id="df4fe-123">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

<span data-ttu-id="df4fe-124">Test projesi oluşturma ve birim testlerini çalıştırmak için diğer paketleri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="df4fe-124">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="df4fe-125">`dotnet new` Önceki adımda, xUnit ve xUnit Çalıştırıcısı eklendi.</span><span class="sxs-lookup"><span data-stu-id="df4fe-125">`dotnet new` in the previous step added xUnit and the xUnit runner.</span></span> <span data-ttu-id="df4fe-126">Şimdi ekleyin `MathService` sınıf kitaplığı projesine başka bir bağımlılık olarak.</span><span class="sxs-lookup"><span data-stu-id="df4fe-126">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="df4fe-127">Kullanım [ `dotnet add reference` ](../tools/dotnet-add-reference.md) komutu:</span><span class="sxs-lookup"><span data-stu-id="df4fe-127">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="df4fe-128">Dosyanın tamamını görebilirsiniz [örnekleri depomuzdan](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) GitHub üzerinde.</span><span class="sxs-lookup"><span data-stu-id="df4fe-128">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="df4fe-129">Aşağıdaki nihai çözüm Düzen vardır:</span><span class="sxs-lookup"><span data-stu-id="df4fe-129">You have the following final solution layout:</span></span>

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

<span data-ttu-id="df4fe-130">Yürütme [ `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` ](../tools/dotnet-sln.md) içinde *birim-test-ile-fsharp* dizin.</span><span class="sxs-lookup"><span data-stu-id="df4fe-130">Execute [`dotnet sln add .\MathService.Tests\MathService.Tests.fsproj`](../tools/dotnet-sln.md) in the *unit-testing-with-fsharp* directory.</span></span> 

## <a name="creating-the-first-test"></a><span data-ttu-id="df4fe-131">İlk testi oluşturma</span><span class="sxs-lookup"><span data-stu-id="df4fe-131">Creating the first test</span></span>

<span data-ttu-id="df4fe-132">Bir yazma, test başarısız kolaylaştırır geçişi, sonra işlemi yineleyin.</span><span class="sxs-lookup"><span data-stu-id="df4fe-132">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="df4fe-133">Açık *Tests.fs* ve aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="df4fe-133">Open *Tests.fs* and add the following code:</span></span>

```fsharp
[<Fact>]
let ``My test`` () =
    Assert.True(true)

[<Fact>]
let ``Fail every time`` () = Assert.True(false)
```

<span data-ttu-id="df4fe-134">`[<Fact>]` Test Çalıştırıcısı tarafından yürütülen bir test metodu özniteliği gösterir.</span><span class="sxs-lookup"><span data-stu-id="df4fe-134">The `[<Fact>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="df4fe-135">Gelen *birim-test-ile-fsharp*, yürütme [ `dotnet test` ](../tools/dotnet-test.md) testler ve sınıf kitaplığı oluşturun ve ardından testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="df4fe-135">From the *unit-testing-with-fsharp*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="df4fe-136">XUnit test Çalıştırıcısı, testlerinizi çalıştırmak için programın giriş noktası içerir.</span><span class="sxs-lookup"><span data-stu-id="df4fe-136">The xUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="df4fe-137">`dotnet test` oluşturduğunuz birim test projesi kullanarak test Çalıştırıcısı'nı başlatır.</span><span class="sxs-lookup"><span data-stu-id="df4fe-137">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="df4fe-138">Bu iki testleri en temel geçirme ve testleri başarısız gösterir.</span><span class="sxs-lookup"><span data-stu-id="df4fe-138">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="df4fe-139">`My test` geçer, ve `Fail every time` başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="df4fe-139">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="df4fe-140">Şimdi, test için oluşturma `squaresOfOdds` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="df4fe-140">Now, create a test for the `squaresOfOdds` method.</span></span> <span data-ttu-id="df4fe-141">`squaresOfOdds` Yöntemi Giriş dizisinin bir parçası olan tüm tek tamsayı değerleri kareleri bir dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="df4fe-141">The `squaresOfOdds` method returns a sequence of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="df4fe-142">Bu işlevlerin tümü aynı anda yazma çalışmak yerine, tekrarlayarak işlevselliğini doğrulama testleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df4fe-142">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="df4fe-143">Her test yöntemi için gereken işlevselliği oluşturma anlamına gelir geçirmek yapılıyor.</span><span class="sxs-lookup"><span data-stu-id="df4fe-143">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="df4fe-144">Biz yazabilirsiniz basit test çağırmaktır `squaresOfOdds` ile sonucu boş bir tam sayı dizisidir olması burada tüm çift sayılarla.</span><span class="sxs-lookup"><span data-stu-id="df4fe-144">The simplest test we can write is to call `squaresOfOdds` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="df4fe-145">Test şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="df4fe-145">Here's that test:</span></span>

```fsharp
[<Fact>]
let ``Sequence of Evens returns empty collection`` () =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

<span data-ttu-id="df4fe-146">Test başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="df4fe-146">Your test fails.</span></span> <span data-ttu-id="df4fe-147">Uygulama henüz oluşturmadınız.</span><span class="sxs-lookup"><span data-stu-id="df4fe-147">You haven't created the implementation yet.</span></span> <span data-ttu-id="df4fe-148">En basit kod yazarak bu testin geçmesini `MathService` çalışır sınıfı:</span><span class="sxs-lookup"><span data-stu-id="df4fe-148">Make this test by writing the simplest code in the `MathService` class that works:</span></span>

```csharp
let squaresOfOdds xs =
    Seq.empty<int>
```

<span data-ttu-id="df4fe-149">İçinde *birim-test-ile-fsharp* çalışması dizini `dotnet test` yeniden.</span><span class="sxs-lookup"><span data-stu-id="df4fe-149">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="df4fe-150">`dotnet test` Komut çalıştıran bir derleme için `MathService` proje ve ardından `MathService.Tests` proje.</span><span class="sxs-lookup"><span data-stu-id="df4fe-150">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="df4fe-151">Her iki proje oluşturduktan sonra bu tek bir test çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="df4fe-151">After building both projects, it runs this single test.</span></span> <span data-ttu-id="df4fe-152">Bu geçirir.</span><span class="sxs-lookup"><span data-stu-id="df4fe-152">It passes.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="df4fe-153">Gereksinimleri Tamamlanıyor</span><span class="sxs-lookup"><span data-stu-id="df4fe-153">Completing the requirements</span></span>

<span data-ttu-id="df4fe-154">Bir test geçirmek yaptığınız, daha fazla yazmak için zaman var.</span><span class="sxs-lookup"><span data-stu-id="df4fe-154">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="df4fe-155">Basit bir sonraki durumda, yalnızca tek sayı içeren bir dizisini çalışır `1`.</span><span class="sxs-lookup"><span data-stu-id="df4fe-155">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="df4fe-156">Sayı 1, 1 karesini 1 olduğundan daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="df4fe-156">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="df4fe-157">Sonraki test şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="df4fe-157">Here's that next test:</span></span>

```fsharp
[<Fact>]
let ``Sequences of Ones and Evens returns Ones`` () =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

<span data-ttu-id="df4fe-158">Yürütme `dotnet test` Testlerinizi çalıştırma ve yeni test başarısız olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="df4fe-158">Executing `dotnet test` runs your tests and shows you that the new test fails.</span></span> <span data-ttu-id="df4fe-159">Şimdi, güncelleştirme `squaresOfOdds` bu yeni test işlemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="df4fe-159">Now, update the `squaresOfOdds` method to handle this new test.</span></span> <span data-ttu-id="df4fe-160">Tüm çift sayıları geçirmek bu testi yapmak için sıra dışı filtre.</span><span class="sxs-lookup"><span data-stu-id="df4fe-160">You filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="df4fe-161">Küçük bir filtre işlevi yazma ve kullanarak bunu yapabilirsiniz `Seq.filter`:</span><span class="sxs-lookup"><span data-stu-id="df4fe-161">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

<span data-ttu-id="df4fe-162">Gitmek için bir adım daha vardır: her biri tek sayıları kare.</span><span class="sxs-lookup"><span data-stu-id="df4fe-162">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="df4fe-163">Yeni bir test yazarak başlatın:</span><span class="sxs-lookup"><span data-stu-id="df4fe-163">Start by writing a new test:</span></span>

```fsharp
[<Fact>]
let ``SquaresOfOdds works`` () =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.Equal(expected, actual)
```

<span data-ttu-id="df4fe-164">Filtrelenmiş sırası tek her bir sayının karesini işlem için bir harita işlemi boyunca yönelterek test düzeltebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="df4fe-164">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs = 
    xs 
    |> Seq.filter isOdd 
    |> Seq.map square
```

<span data-ttu-id="df4fe-165">Küçük bir kitaplık ve bu kitaplık için birim testleri bir dizi oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="df4fe-165">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="df4fe-166">Böylece yeni paketler ekleme çözüm yapılandırılmış ve testleri normal iş akışı bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="df4fe-166">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="df4fe-167">Zaman ve çaba çözme hedeflerinden biri, uygulama üzerinde en yoğun.</span><span class="sxs-lookup"><span data-stu-id="df4fe-167">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
