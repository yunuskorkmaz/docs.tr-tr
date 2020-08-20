---
title: "DotNet test ve NUnit ile .NET Core 'da birim testi F #"
description: ".NET Core 'daki F # için birim testi kavramlarını, DotNet test ve NUnit kullanarak bir örnek çözüm oluşturma adlı etkileşimli bir deneyim aracılığıyla öğrenin."
author: rprouse
ms.date: 10/04/2018
dev_langs:
- fsharp
ms.openlocfilehash: 9a1b4bb7e5e705cf1c71cd44827d4a2e0a3f8cf6
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656481"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-nunit"></a>DotNet test ve NUnit kullanarak .NET Core 'daki birim testi F # kitaplıkları

Bu öğreticide, birim testi kavramlarını öğrenmek için bir örnek çözüm oluşturma adım adım yönergeler sunarak etkileşimli bir deneyim sağlanır. Önceden oluşturulmuş bir çözüm kullanarak öğreticiyi izlemeyi tercih ediyorsanız, başlamadan önce [örnek kodu görüntüleyin veya indirin](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-nunit/) . İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#view-and-download-samples).

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="prerequisites"></a>Önkoşullar

- [.NET Core 2,1 SDK](https://dotnet.microsoft.com/download) veya sonraki sürümleri.
- Tercih ettiğiniz bir metin veya kod düzenleyicisi.

## <a name="creating-the-source-project"></a>Kaynak proje oluşturma

Bir kabuk penceresi açın. Çözümü tutmak için- *FSharp ile birim-test* adlı bir dizin oluşturun.
Bu yeni dizin içinde, sınıf kitaplığı ve test projesi için yeni bir çözüm dosyası oluşturmak üzere aşağıdaki komutu çalıştırın:

```dotnetcli
dotnet new sln
```

Sonra bir *MathService* dizini oluşturun. Aşağıdaki ana hat şu ana kadar dizin ve dosya yapısını gösterir:

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

*MathService* geçerli dizin yapın ve kaynak projeyi oluşturmak için şu komutu çalıştırın:

```dotnetcli
dotnet new classlib -lang "F#"
```

Matematik hizmetinin başarısız bir uygulamasını oluşturursunuz:

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

Dizini- *FSharp dizinine sahip birim-test ile* yeniden değiştirin. Çözüme Sınıf Kitaplığı projesini eklemek için aşağıdaki komutu çalıştırın:

```dotnetcli
dotnet sln add .\MathService\MathService.fsproj
```

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

*MathService. Tests* dizinini geçerli dizini yapın ve aşağıdaki komutu kullanarak yeni bir proje oluşturun:

```dotnetcli
dotnet new nunit -lang "F#"
```

Bu, test çerçevesi olarak NUnit kullanan bir test projesi oluşturur. Oluşturulan şablon, *MathServiceTests. fsproj*içindeki Test Çalıştırıcısı 'nı yapılandırır:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

Test projesi, birim testlerini oluşturmak ve çalıştırmak için diğer paketlerin kullanılmasını gerektirir. `dotnet new` önceki adımda NUnit ve NUnit test bağdaştırıcısı eklenmiştir. Şimdi, `MathService` sınıf kitaplığını projeye başka bir bağımlılık olarak ekleyin. Şu `dotnet add reference` komutu kullanın:

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
        MathService.Tests.fsproj
```

*Birim-test--FSharp* dizininde aşağıdaki komutu yürütün:

```dotnetcli
dotnet sln add .\MathService.Tests\MathService.Tests.fsproj
```

## <a name="creating-the-first-test"></a>İlk test oluşturma

Başarısız bir test yazdığınızda, geçişi yapıp işlemi tekrarlayabilirsiniz. *UnitTest1. FS* ' i açın ve aşağıdaki kodu ekleyin:

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

`[<TestFixture>]`Öznitelik, testleri içeren bir sınıfı gösterir. `[<Test>]`Öznitelik, Test Çalıştırıcısı tarafından çalıştırılan bir test yöntemini gösterir. *Birim-test--FSharp* dizininden, `dotnet test` Testleri ve sınıf kitaplığını oluşturmak için yürütün ve ardından testleri çalıştırın. NUnit Test Çalıştırıcısı, testlerinizi çalıştırmak için program giriş noktasını içerir. `dotnet test` oluşturduğunuz birim test projesini kullanarak Test Çalıştırıcısı başlatır.

Bu iki test, en temel geçirme ve başarısız testleri gösterir. `My test` geçirilir ve `Fail every time` başarısız olur. Şimdi, yöntemi için bir test oluşturun `squaresOfOdds` . `squaresOfOdds`Yöntemi, giriş dizisinin parçası olan tüm tek tamsayı değerlerinin karelerinin dizisini döndürür. Bu işlevlerin tümünü aynı anda yazmaya çalışmak yerine, işlevi doğrulayan testleri tekrarlayarak oluşturabilirsiniz. Her test geçişinin yapılması, yöntemi için gerekli işlevselliğin oluşturulması anlamına gelir.

Yazdığımız en basit test, `squaresOfOdds` sonucun boş bir tamsayılar dizisi olması gereken tüm çift sayılarla çağrıdır.  Bu test şu şekildedir:

```fsharp
[<Test>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

`expected`Sıranın bir listeye dönüştürüldüğüne dikkat edin. NUnit çerçevesi birçok standart .NET türünü temel alır. Bu bağımlılık, genel arabiriminiz ve yerine beklenen sonuç desteğinden biridir <xref:System.Collections.ICollection> <xref:System.Collections.IEnumerable> .

Testi çalıştırdığınızda, testinizin başarısız olduğunu görürsünüz. Uygulamayı henüz oluşturmadınız. MathService projenizdeki *Library. FS* sınıfına en basit kodu yazarak bu test geçişini yapın:

```fsharp
let squaresOfOdds xs =
    Seq.empty<int>
```

*Birim-test--FSharp diziniyle birlikte* `dotnet test` yeniden çalıştırın. `dotnet test`Komutu, proje için bir yapı `MathService` ve ardından proje için çalışır `MathService.Tests` . Her iki proje de oluşturulduktan sonra testlerinizi çalıştırır. İki test şimdi geçer.

## <a name="completing-the-requirements"></a>Gereksinimleri tamamlama

Artık bir test geçişi yapmış olduğunuza göre daha fazla yazma zamanı vardır. Bir sonraki basit durum yalnızca tek sayı olan bir sıra ile birlikte kullanılır `1` . 1 numaralı kare 1 olduğundan, 1 sayısı daha kolay. İşte bu sonraki test:

```fsharp
[<Test>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

Yürütme `dotnet test` işlemi yeni test başarısız olur. `squaresOfOdds`Bu yeni testi işlemek için yöntemini güncelleştirmeniz gerekir. Bu test geçişini yapmak için tüm çift sayıları sıranın dışına filtrelemeniz gerekir. Bunu, küçük bir filtre işlevi yazarak ve kullanarak yapabilirsiniz `Seq.filter` :

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

Çağrısına dikkat edin `Seq.toList` . Bu, arabirimini uygulayan bir liste oluşturur <xref:System.Collections.ICollection> .

Bir adım daha vardır: her bir tek sayının kare sayısı. Yeni bir test yazarak başlayın:

```fsharp
[<Test>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.That(actual, Is.EqualTo(expected))
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

- [dotnet add reference](../tools/dotnet-add-reference.md)
- [dotnet test](../tools/dotnet-test.md)
