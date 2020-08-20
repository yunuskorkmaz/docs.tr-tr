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
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-xunit"></a>DotNet test ve xUnit kullanarak .NET Core 'daki birim testi F # kitaplıkları

Bu öğreticide, birim testi kavramlarını öğrenmek için bir örnek çözüm oluşturma adım adım yönergeler sunarak etkileşimli bir deneyim sağlanır. Önceden oluşturulmuş bir çözüm kullanarak öğreticiyi izlemeyi tercih ediyorsanız, başlamadan önce [örnek kodu görüntüleyin veya indirin](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp/) . İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#view-and-download-samples).

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="creating-the-source-project"></a>Kaynak proje oluşturma

Bir kabuk penceresi açın. Çözümü tutmak için- *FSharp ile birim-test* adlı bir dizin oluşturun.
Yeni bir çözüm oluşturmak için bu yeni dizinin içinde öğesini çalıştırın `dotnet new sln` . Bu, hem sınıf kitaplığını hem de birim testi projesini yönetmeyi kolaylaştırır.
Çözüm dizini içinde bir *MathService* dizini oluşturun. Bu nedenle şu ana kadar dizin ve dosya yapısı aşağıda gösterilmiştir:

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

*MathService* geçerli dizin yapın ve `dotnet new classlib -lang "F#"` kaynak projeyi oluşturmak için çalıştırın. Matematik hizmeti için başarısız bir uygulama oluşturacaksınız:

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

Dizini- *FSharp dizinine sahip birim-test ile* yeniden değiştirin. `dotnet sln add .\MathService\MathService.fsproj`Çözüme Sınıf Kitaplığı projesini eklemek için ' i çalıştırın.

## <a name="creating-the-test-project"></a>Test projesi oluşturma

Sonra, *MathService. Tests* dizinini oluşturun. Aşağıdaki ana hat dizin yapısını gösterir:

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

*MathService. Tests* dizinini geçerli dizin yapın ve kullanarak yeni bir proje oluşturun `dotnet new xunit -lang "F#"` . Bu, test kitaplığı olarak xUnit kullanan bir test projesi oluşturur. Oluşturulan şablon, *MathServiceTests. fsproj*içindeki Test Çalıştırıcısı 'nı yapılandırır:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

Test projesi, birim testlerini oluşturmak ve çalıştırmak için diğer paketlerin kullanılmasını gerektirir. `dotnet new` önceki adımda xUnit ve xUnit Çalıştırıcısı eklenmiştir. Şimdi, `MathService` sınıf kitaplığını projeye başka bir bağımlılık olarak ekleyin. Şu `dotnet add reference` komutu kullanın:

```dotnetcli
dotnet add reference ../MathService/MathService.fsproj
```

GitHub 'daki [örnekler deposunda](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) dosyanın tamamını görebilirsiniz.

Aşağıdaki son çözüm düzenine sahipsiniz:

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

- `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` FSharp diziniyle *birlikte birim-test* ' i çalıştırın.

## <a name="creating-the-first-test"></a>İlk test oluşturma

Başarısız bir test yazdığınızda, geçişi yapıp işlemi tekrarlayabilirsiniz. *Tests. FS* ' i açın ve aşağıdaki kodu ekleyin:

```fsharp
[<Fact>]
let ``My test`` () =
    Assert.True(true)

[<Fact>]
let ``Fail every time`` () = Assert.True(false)
```

`[<Fact>]`Öznitelik, Test Çalıştırıcısı tarafından çalıştırılan bir test yöntemini gösterir. - *FSharp olan birim-test*' den, `dotnet test` Testleri ve sınıf kitaplığını oluşturmak için yürütün ve ardından testleri çalıştırın. XUnit Test Çalıştırıcısı, testlerinizi çalıştırmak için program giriş noktasını içerir. `dotnet test` oluşturduğunuz birim test projesini kullanarak Test Çalıştırıcısı başlatır.

Bu iki test, en temel geçirme ve başarısız testleri gösterir. `My test` geçirilir ve `Fail every time` başarısız olur. Şimdi, yöntemi için bir test oluşturun `squaresOfOdds` . `squaresOfOdds`Yöntemi, giriş dizisinin parçası olan tüm tek tamsayı değerlerinin karelerinin dizisini döndürür. Bu işlevlerin tümünü aynı anda yazmaya çalışmak yerine, işlevi doğrulayan testleri tekrarlayarak oluşturabilirsiniz. Her test geçişinin yapılması, yöntemi için gerekli işlevselliğin oluşturulması anlamına gelir.

Yazdığımız en basit test, `squaresOfOdds` sonucun boş bir tamsayılar dizisi olması gereken tüm çift sayılarla çağrıdır.  Bu test şu şekildedir:

```fsharp
[<Fact>]
let ``Sequence of Evens returns empty collection`` () =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

Testiniz başarısız oluyor. Uygulamayı henüz oluşturmadınız. Bu test geçişini, çalıştıran sınıfa en basit kodu yazarak yapın `MathService` :

```fsharp
let squaresOfOdds xs =
    Seq.empty<int>
```

*Birim-test--FSharp diziniyle birlikte* `dotnet test` yeniden çalıştırın. `dotnet test`Komutu, proje için bir yapı `MathService` ve ardından proje için çalışır `MathService.Tests` . Her iki proje de oluşturulduktan sonra bu tek testi çalıştırır. Geçirir.

## <a name="completing-the-requirements"></a>Gereksinimleri tamamlama

Artık bir test geçişi yapmış olduğunuza göre daha fazla yazma zamanı vardır. Bir sonraki basit durum yalnızca tek sayı olan bir sıra ile birlikte kullanılır `1` . 1 numaralı kare 1 olduğundan, 1 sayısı daha kolay. İşte bu sonraki test:

```fsharp
[<Fact>]
let ``Sequences of Ones and Evens returns Ones`` () =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

Yürütme, `dotnet test` testlerinizi çalıştırır ve yeni testin başarısız olduğunu gösterir. Şimdi `squaresOfOdds` Bu yeni testi işleyecek yöntemi güncelleştirin. Bu test geçişini yapmak için tüm çift sayıları sıranın dışına filtreleyin. Bunu, küçük bir filtre işlevi yazarak ve kullanarak yapabilirsiniz `Seq.filter` :

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

Bir adım daha vardır: her bir tek sayının kare sayısı. Yeni bir test yazarak başlayın:

```fsharp
[<Fact>]
let ``SquaresOfOdds works`` () =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.Equal(expected, actual)
```

Her bir tek sayının karesini hesaplamak için, filtre uygulanmış sırayı bir eşleme işlemi aracılığıyla ayırarak testi giderebilirsiniz:

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
```

Bu kitaplık için küçük bir kitaplık ve birim testleri kümesi oluşturdunuz. Çözümü, yeni paket ve test eklemek normal iş akışının bir parçası olacak şekilde öğrendiniz. Uygulamanın hedeflerini çözme konusunda zaman ve çaba harcamanızı en iyi şekilde gördünüz.

## <a name="see-also"></a>Ayrıca bkz.

- [dotnet new](../tools/dotnet-new.md)
- [dotnet sln](../tools/dotnet-new.md)
- [dotnet add reference](../tools/dotnet-add-reference.md)
- [dotnet test](../tools/dotnet-test.md)
