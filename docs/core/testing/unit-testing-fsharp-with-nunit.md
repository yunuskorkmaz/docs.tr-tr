---
title: DotNet test F# ve NUnit Ile .NET Core 'da birim testi
description: .NET Core F# 'da, DotNet test ve NUnit kullanarak örnek bir çözüm oluşturarak etkileşimli bir deneyim aracılığıyla birim testi kavramlarını öğrenin.
author: rprouse
ms.date: 10/04/2018
dev_langs:
- fsharp
ms.openlocfilehash: 3347e5b90c31589e9a0f99ac0d9298927a717f56
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715441"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-nunit"></a>DotNet test F# ve NUnit kullanarak .NET Core 'da birim testi kitaplıkları

Bu öğreticide, birim testi kavramlarını öğrenmek için bir örnek çözüm oluşturma adım adım yönergeler sunarak etkileşimli bir deneyim sağlanır. Önceden oluşturulmuş bir çözüm kullanarak öğreticiyi izlemeyi tercih ediyorsanız, başlamadan önce [örnek kodu görüntüleyin veya indirin](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-nunit/) . İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="prerequisites"></a>Prerequisites

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

Test projesi, birim testlerini oluşturmak ve çalıştırmak için diğer paketlerin kullanılmasını gerektirir. önceki adımda `dotnet new` NUnit ve NUnit test bağdaştırıcısı eklenmiştir. Şimdi, `MathService` sınıf kitaplığını projeye başka bir bağımlılık olarak ekleyin. `dotnet add reference` komutunu kullanın:

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

`[<TestFixture>]` özniteliği, testleri içeren bir sınıfı gösterir. `[<Test>]` özniteliği, Test Çalıştırıcısı tarafından çalıştırılan bir test yöntemini gösterir. *Birim-test--FSharp* dizininden, testleri ve sınıf kitaplığını oluşturmak için `dotnet test` yürütün ve ardından testleri çalıştırın. NUnit Test Çalıştırıcısı, testlerinizi çalıştırmak için program giriş noktasını içerir. `dotnet test`, oluşturduğunuz birim test projesini kullanarak Test Çalıştırıcısı başlatır.

Bu iki test, en temel geçirme ve başarısız testleri gösterir. `My test` geçirilir ve `Fail every time` başarısız olur. Şimdi `squaresOfOdds` yöntemi için bir test oluşturun. `squaresOfOdds` yöntemi, giriş dizisinin parçası olan tüm tek tamsayı değerlerinin karelerinin dizisini döndürür. Bu işlevlerin tümünü aynı anda yazmaya çalışmak yerine, işlevi doğrulayan testleri tekrarlayarak oluşturabilirsiniz. Her test geçişinin yapılması, yöntemi için gerekli işlevselliğin oluşturulması anlamına gelir.

Yazdığımız en basit test, tüm çift sayılarla `squaresOfOdds` çağırmakta olduğundan, sonucun boş bir tamsayılar dizisi olması gerekir.  Bu test şu şekildedir:

```fsharp
[<Test>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

`expected` sırasının bir listeye dönüştürüldüğüne dikkat edin. NUnit çerçevesi birçok standart .NET türünü temel alır. Bu bağımlılık, genel arabiriminiz ve beklenen sonuçlar <xref:System.Collections.IEnumerable>yerine <xref:System.Collections.ICollection> destekledikleri anlamına gelir.

Testi çalıştırdığınızda, testinizin başarısız olduğunu görürsünüz. Uygulamayı henüz oluşturmadınız. MathService projenizdeki *Library. FS* sınıfına en basit kodu yazarak bu test geçişini yapın:

```fsharp
let squaresOfOdds xs =
    Seq.empty<int>
```

*Birim-test--FSharp diziniyle birlikte* `dotnet test` yeniden çalıştırın. `dotnet test` komutu, `MathService` projesi için bir derleme ve sonra `MathService.Tests` projesi için çalışır. Her iki proje de oluşturulduktan sonra testlerinizi çalıştırır. İki test şimdi geçer.

## <a name="completing-the-requirements"></a>Gereksinimleri tamamlama

Artık bir test geçişi yapmış olduğunuza göre daha fazla yazma zamanı vardır. Bir sonraki basit durum yalnızca tek sayı `1`olan bir sıra ile birlikte kullanılır. 1 numaralı kare 1 olduğundan, 1 sayısı daha kolay. İşte bu sonraki test:

```fsharp
[<Test>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

`dotnet test` yürütülmesi yeni test başarısız olur. Bu yeni testi işlemek için `squaresOfOdds` metodunu güncelleştirmeniz gerekir. Bu test geçişini yapmak için tüm çift sayıları sıranın dışına filtrelemeniz gerekir. Bunu, küçük bir filtre işlevi yazarak ve `Seq.filter`kullanarak yapabilirsiniz:

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

`Seq.toList`çağrısına dikkat edin. Bu, <xref:System.Collections.ICollection> arabirimini uygulayan bir liste oluşturur.

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
