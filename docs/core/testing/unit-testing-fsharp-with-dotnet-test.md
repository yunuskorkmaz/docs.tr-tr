---
title: 'Birim F # kitaplığı .NET dotnet test ve xUnit kullanarak çekirdek testi'
description: 'Birim testi kavramları F # .NET Core için adım adım örnek çözüm oluşturma bir etkileşimli deneyimler aracılığıyla öğrenmeniz dotnet test ve xUnit kullanarak.'
author: billwagner
ms.author: wiwagn
ms.date: 08/30/2017
ms.topic: conceptual
dev_langs:
- fsharp
ms.prod: dotnet-core
ms.workload:
- dotnetcore
ms.openlocfilehash: 11fab52cb426b0dbb173c9c6e2bd7b5766501964
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-xunit"></a><span data-ttu-id="9a3a2-103">Birim F # kitaplığı .NET dotnet test ve xUnit kullanarak çekirdek testi</span><span class="sxs-lookup"><span data-stu-id="9a3a2-103">Unit testing F# libraries in .NET Core using dotnet test and xUnit</span></span>

<span data-ttu-id="9a3a2-104">Bu öğretici birim testi kavramlarını öğrenmek için adım adım örnek çözüm oluşturma etkileşimli bir deneyim gösterir.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="9a3a2-105">Önceden oluşturulmuş bir çözümü kullanarak öğreticiyi izleyin tercih ediyorsanız [görüntülemek veya karşıdan örnek kod](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp/) başlamadan önce.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp/) before you begin.</span></span> <span data-ttu-id="9a3a2-106">Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="9a3a2-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="9a3a2-107">Kaynak projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="9a3a2-107">Creating the source project</span></span>

<span data-ttu-id="9a3a2-108">Kabuk penceresini açın.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-108">Open a shell window.</span></span> <span data-ttu-id="9a3a2-109">Adlı bir dizin oluşturun *birim-test etme-ile-fsharp* çözümü tutmak için.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-109">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="9a3a2-110">Bu yeni dizin içinde çalıştırmak [ `dotnet new sln` ](../tools/dotnet-new.md) yeni bir çözüm oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="9a3a2-111">Bu sınıf kitaplığı ve birim testi projesi yönetmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-111">This makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="9a3a2-112">Çözüm dizini içinde oluşturmak bir *MathService* dizini.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-112">Inside the solution directory, create a *MathService* directory.</span></span> <span data-ttu-id="9a3a2-113">Dizin ve dosya yapısı bugüne kadarki aşağıda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="9a3a2-113">The directory and file structure thus far is shown below:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="9a3a2-114">Olun *MathService* geçerli dizin ve çalışma [ `dotnet new classlib -lang F#` ](../tools/dotnet-new.md) kaynak projesi oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-114">Make *MathService* the current directory and run [`dotnet new classlib -lang F#`](../tools/dotnet-new.md) to create the source project.</span></span>  <span data-ttu-id="9a3a2-115">Teste dayalı geliştirme (TDD) kullanmak için başarısız olan uygulama matematik hizmetinin oluşturursunuz:</span><span class="sxs-lookup"><span data-stu-id="9a3a2-115">To use test-driven development (TDD), you'll create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="9a3a2-116">Dizin geri değişiklik *birim-test etme-ile-fsharp* dizini.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-116">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="9a3a2-117">Çalıştırma [ `dotnet sln add .\MathService\MathService.fsproj` ](../tools/dotnet-sln.md) sınıf kitaplığı proje çözüme eklemek için.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-117">Run [`dotnet sln add .\MathService\MathService.fsproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="9a3a2-118">Test projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="9a3a2-118">Creating the test project</span></span>

<span data-ttu-id="9a3a2-119">Ardından, oluşturun *MathService.Tests* dizini.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-119">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="9a3a2-120">Aşağıdaki anahat dizin yapısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="9a3a2-120">The following outline shows the directory structure:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="9a3a2-121">Olun *MathService.Tests* dizine geçerli ve kullanarak yeni bir proje oluşturun [ `dotnet new xunit -lang F#` ](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="9a3a2-121">Make the *MathService.Tests* directory the current directory and create a new project using [`dotnet new xunit -lang F#`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="9a3a2-122">Bu test kitaplık olarak xUnit kullanan bir test projesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-122">This creates a test project that uses xUnit as the test library.</span></span> <span data-ttu-id="9a3a2-123">Test Çalıştırıcısı'nda oluşturulan şablon yapılandırır *MathServiceTests.fsproj*:</span><span class="sxs-lookup"><span data-stu-id="9a3a2-123">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

<span data-ttu-id="9a3a2-124">Test projesi oluşturmak ve birim testleri çalıştırmak için diğer paketleri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-124">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="9a3a2-125">`dotnet new` Önceki adımda xUnit ve xUnit Çalıştırıcısı eklendi.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-125">`dotnet new` in the previous step added xUnit and the xUnit runner.</span></span> <span data-ttu-id="9a3a2-126">Şimdi, ekleyin `MathService` sınıf kitaplığı proje için başka bir bağımlılık olarak.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-126">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="9a3a2-127">Kullanım [ `dotnet add reference` ](../tools/dotnet-add-reference.md) komutu:</span><span class="sxs-lookup"><span data-stu-id="9a3a2-127">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="9a3a2-128">Tüm dosyasında görebilirsiniz [örnekleri deposu](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) github'da.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-128">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="9a3a2-129">Aşağıdaki nihai çözüm düzeni vardır:</span><span class="sxs-lookup"><span data-stu-id="9a3a2-129">You have the following final solution layout:</span></span>

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

<span data-ttu-id="9a3a2-130">Yürütme [ `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` ](../tools/dotnet-sln.md) içinde *birim-test etme-ile-fsharp* dizini.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-130">Execute [`dotnet sln add .\MathService.Tests\MathService.Tests.fsproj`](../tools/dotnet-sln.md) in the *unit-testing-with-fsharp* directory.</span></span> 

## <a name="creating-the-first-test"></a><span data-ttu-id="9a3a2-131">İlk testi oluşturma</span><span class="sxs-lookup"><span data-stu-id="9a3a2-131">Creating the first test</span></span>

<span data-ttu-id="9a3a2-132">TDD yaklaşım geçirmek kolaylaştırarak ve süreci tekrarlayarak yazma bir başarısız test için çağırır.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-132">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="9a3a2-133">Açık *Tests.fs* ve aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="9a3a2-133">Open *Tests.fs* and add the following code:</span></span>

```fsharp
[<Fact>]
let ``My test`` () =
    Assert.True(true)

[<Fact>]
let ``Fail every time`` () = Assert.True(false)
```

<span data-ttu-id="9a3a2-134">`[<Fact>]` Özniteliği test Çalıştırıcısı tarafından çalıştırılan test yöntemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-134">The `[<Fact>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="9a3a2-135">Gelen *birim-test etme-ile-fsharp*, yürütme [ `dotnet test` ](../tools/dotnet-test.md) testleri ve sınıf kitaplığı oluşturmak ve ardından testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-135">From the *unit-testing-with-fsharp*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="9a3a2-136">XUnit test Çalıştırıcısı testleri çalıştırmak için program giriş noktası içerir.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-136">The xUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="9a3a2-137">`dotnet test` oluşturduğunuz birim testi projesi kullanarak test Çalıştırıcısı başlatır.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-137">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="9a3a2-138">Bu iki testleri en temel geçirme ve testleri başarısız gösterir.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-138">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="9a3a2-139">`My test` geçirir, ve `Fail every time` başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-139">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="9a3a2-140">Şimdi, test için oluşturma `squaresOfOdds` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-140">Now, create a test for the `squaresOfOdds` method.</span></span> <span data-ttu-id="9a3a2-141">`squaresOfOdds` Yöntemi Giriş dizisinin bir parçası olan tüm tek sayılı tamsayı değerleri kareleri bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-141">The `squaresOfOdds` method returns a sequence of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="9a3a2-142">Bu işlevlerin tümüne tek seferde yazmaya çalışırken yerine işlevselliğini doğrulama testleri tekrarlayarak oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-142">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="9a3a2-143">Yöntemi için gerekli işlevselliği oluşturma anlamına gelir geçirmek her test yapma.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-143">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="9a3a2-144">Biz yazabilirler basit test çağırmaktır `squaresOfOdds` tüm çift numaraları, burada sonucu olmalıdır boş bir tam sayı dizisidir.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-144">The simplest test we can write is to call `squaresOfOdds` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="9a3a2-145">Bu test şöyledir:</span><span class="sxs-lookup"><span data-stu-id="9a3a2-145">Here's that test:</span></span>

```fsharp
[<Fact>]
let ``Sequence of Evens returns empty collection`` () =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

<span data-ttu-id="9a3a2-146">Testiniz başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-146">Your test fails.</span></span> <span data-ttu-id="9a3a2-147">Uygulama henüz oluşturmadınız.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-147">You haven't created the implementation yet.</span></span> <span data-ttu-id="9a3a2-148">Bu test basit kod yazarken yapmasına `MathService` çalışır sınıfı:</span><span class="sxs-lookup"><span data-stu-id="9a3a2-148">Make this test by writing the simplest code in the `MathService` class that works:</span></span>

```csharp
let squaresOfOdds xs =
    Seq.empty<int>
```

<span data-ttu-id="9a3a2-149">İçinde *birim-test etme-ile-fsharp* çalışması dizini `dotnet test` yeniden.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-149">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="9a3a2-150">`dotnet test` Komutu çalıştıran bir yapı `MathService` proje ve ardından `MathService.Tests` projesi.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-150">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="9a3a2-151">Her iki proje oluşturduktan sonra bu tek bir test çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-151">After building both projects, it runs this single test.</span></span> <span data-ttu-id="9a3a2-152">Bunu geçirir.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-152">It passes.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="9a3a2-153">Gereksinimleri Tamamlanıyor</span><span class="sxs-lookup"><span data-stu-id="9a3a2-153">Completing the requirements</span></span>

<span data-ttu-id="9a3a2-154">Bir test geçirmek yapmış olduğunuz, daha fazla yazma zamanı geldi.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-154">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="9a3a2-155">Sonraki basit bir durumda, yalnızca tek sayı olan bir sıra ile çalışır `1`.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-155">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="9a3a2-156">1 sayısı 1'in Kare 1 olduğundan daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-156">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="9a3a2-157">Sonraki test şöyledir:</span><span class="sxs-lookup"><span data-stu-id="9a3a2-157">Here's that next test:</span></span>

```fsharp
[<Fact>]
let ``Sequences of Ones and Evens returns Ones`` () =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

<span data-ttu-id="9a3a2-158">Yürütme `dotnet test` testlerinizi çalıştırır ve yeni test başarısız olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-158">Executing `dotnet test` runs your tests and shows you that the new test fails.</span></span> <span data-ttu-id="9a3a2-159">Şimdi, güncelleştirme `squaresOfOdds` bu yeni test işlemek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-159">Now, update the `squaresOfOdds` method to handle this new test.</span></span> <span data-ttu-id="9a3a2-160">Geçirmek bu testi yapmak için sıra dışında tüm çift sayıları filtreleyin.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-160">You filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="9a3a2-161">Küçük filtre işlevi yazma ve kullanarak bunu, `Seq.filter`:</span><span class="sxs-lookup"><span data-stu-id="9a3a2-161">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

<span data-ttu-id="9a3a2-162">Gitmek için bir adım daha vardır: her tek sayıların karesini.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-162">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="9a3a2-163">Yeni bir test yazarak başlatın:</span><span class="sxs-lookup"><span data-stu-id="9a3a2-163">Start by writing a new test:</span></span>

```fsharp
[<Fact>]
let ``SquaresOfOdds works`` () =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.Equal(expected, actual)
```

<span data-ttu-id="9a3a2-164">Her tek sayı kare hesaplamak için eşleme işlemi aracılığıyla filtrelenmiş dizisi cmdlet'ine yönelterek test düzeltebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9a3a2-164">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs = 
    xs 
    |> Seq.filter isOdd 
    |> Seq.map square
```

<span data-ttu-id="9a3a2-165">Küçük bir kitaplığı ve bu kitaplık için birim testleri kümesini temel aldık.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-165">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="9a3a2-166">Böylece yeni paketleri ekleme çözümü yapılandırılmış ve testleri normal iş akışı bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-166">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="9a3a2-167">Çoğu zaman ve çaba uygulama amaçlarını çözme üzerinde yoğunlaşmıştır.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-167">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
