---
title: Dotnet testi ve NUnit ile .NET Core'da F# testi
description: Dotnet testi ve NUnit kullanarak adım adım örnek bir çözüm oluşturma etkileşimli bir deneyim le .NET Core'da F# için birim test kavramlarını öğrenin.
author: rprouse
ms.date: 10/04/2018
dev_langs:
- fsharp
ms.openlocfilehash: 3347e5b90c31589e9a0f99ac0d9298927a717f56
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715441"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-nunit"></a>Dotnet testi ve NUnit kullanarak .NET Core'daki F# kitaplıklarını test etme birimi

Bu öğretici, birim test kavramlarını öğrenmek için adım adım örnek bir çözüm oluşturma etkileşimli bir deneyim sunar. Önceden oluşturulmuş bir çözüm kullanarak öğreticiyi izlemeyi tercih ederseniz, başlamadan önce [örnek kodu görüntüleyin veya indirin.](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-nunit/) İndirme talimatları için [Örnekler ve Öğreticiler'e](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)bakın.

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="prerequisites"></a>Önkoşullar

- [.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) veya sonraki sürümler.
- Tercih ettiğiniz bir metin veya kod düzenleyicisi.

## <a name="creating-the-source-project"></a>Kaynak proje oluşturma

Bir kabuk penceresi açın. Çözümü tutmak için *birim-test-fsharp adı* verilen bir dizin oluşturun.
Bu yeni dizinin içinde, sınıf kitaplığı ve test projesi için yeni bir çözüm dosyası oluşturmak için aşağıdaki komutu çalıştırın:

```dotnetcli
dotnet new sln
```

Ardından, bir *MathService* dizini oluşturun. Aşağıdaki anahat şimdiye kadar dizin ve dosya yapısını gösterir:

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

*MathService'i* geçerli dizini yapın ve kaynak projeyi oluşturmak için aşağıdaki komutu çalıştırın:

```dotnetcli
dotnet new classlib -lang "F#"
```

Matematik hizmetinin başarısız bir uygulamasını oluşturursunuz:

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

Dizin geri *birim-test-with-fsharp* dizin değiştirin. Sınıf kitaplığı projesini çözüme eklemek için aşağıdaki komutu çalıştırın:

```dotnetcli
dotnet sln add .\MathService\MathService.fsproj
```

## <a name="creating-the-test-project"></a>Test projesini oluşturma

Ardından *MathService.Tests* dizinini oluşturun. Aşağıdaki anahat dizin yapısını gösterir:

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

*MathService.Tests* dizinini geçerli dizini oluşturun ve aşağıdaki komutu kullanarak yeni bir proje oluşturun:

```dotnetcli
dotnet new nunit -lang "F#"
```

Bu, test çerçevesi olarak NUnit kullanan bir test projesi oluşturur. Oluşturulan şablon *MathServiceTests.fsproj*test koşucusu yapılandırır:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

Test projesi, birim testleri oluşturmak ve çalıştırmak için diğer paketler gerektirir. `dotnet new`önceki adımda NUnit ve NUnit test bağdaştırıcısı eklendi. Şimdi, `MathService` sınıf kitaplığını projeye başka bir bağımlılık olarak ekleyin. Komutu `dotnet add reference` kullanın:

```dotnetcli
dotnet add reference ../MathService/MathService.fsproj
```

Tüm dosyayı GitHub'daki [örnek deposunda](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) görebilirsiniz.

Aşağıdaki nihai çözüm düzenine sahipsiniz:

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

*Birim-test-with-fsharp* dizininde aşağıdaki komutu çalıştırın:

```dotnetcli
dotnet sln add .\MathService.Tests\MathService.Tests.fsproj
```

## <a name="creating-the-first-test"></a>İlk testi oluşturma

Başarısız bir test yazarsın, geçer ve işlemi tekrarlarsın. *UnitTest1.fs'yi* açın ve aşağıdaki kodu ekleyin:

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

Öznitelik, `[<TestFixture>]` testleri içeren bir sınıfı gösterir. Öznitelik, `[<Test>]` test koşucusu tarafından çalıştırılabilen bir test yöntemini gösterir. *Birim-test-with-fsharp* dizininden, testleri `dotnet test` ve sınıf kitaplığını oluşturmak ve testleri çalıştırmak için çalıştırın. NUnit test koşucusu, testlerinizi çalıştırmak için program giriş noktasını içerir. `dotnet test`oluşturduğunuz birim test projesini kullanarak test koşucusu başlatın.

Bu iki test, en temel geçen ve başarısız testleri gösterir. `My test`geçer ve `Fail every time` başarısız olur. Şimdi, `squaresOfOdds` yöntem için bir test oluşturun. Yöntem, `squaresOfOdds` giriş sırasının bir parçası olan tüm tek tamsayı değerlerinin karelerinin bir sırasını döndürür. Tüm bu işlevleri aynı anda yazmaya çalışmak yerine, işlevselliği doğrulayan testleri yinelemeli olarak oluşturabilirsiniz. Her test geçişini yapmak, yöntem için gerekli işlevselliği oluşturmak anlamına gelir.

Yazabileceğimiz en basit test, `squaresOfOdds` sonucun boş bir toplamdarık dizisi olması gereken tüm çift sayılarla aramaktır.  İşte o test:

```fsharp
[<Test>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

`expected` Dizinin bir listeye dönüştürüldüğünü unutmayın. NUnit çerçevesi birçok standart .NET türüne dayanır. Bu bağımlılık, ortak arabiriminizin ve <xref:System.Collections.ICollection> beklenen <xref:System.Collections.IEnumerable>sonuçların değil, 'yi desteklediği anlamına gelir.

Testi çalıştırdığınızda, testinizin başarısız olduğunu görürsünüz. Uygulamayı henüz oluşturmadın. MathService projenizde *Library.fs* sınıfında ki en basit kodu yazarak bu testi geçirin:

```fsharp
let squaresOfOdds xs =
    Seq.empty<int>
```

*Birim-test-fsharp* dizininde, yeniden çalıştırın. `dotnet test` Komut, `dotnet test` proje ve ardından `MathService.Tests` proje için bir yapı çalışır. `MathService` Her iki projeyi de yaptıktan sonra, testlerinizi çalıştırAr. Şimdi iki test geçti.

## <a name="completing-the-requirements"></a>Gereksinimleri nama

Artık bir test sınavını geçtiğine göre, daha fazla yazma nın zamanı. Sonraki basit durum, tek sayısı `1`. 1'in karesi 1 olduğundan 1 sayısı daha kolaydır. İşte bir sonraki test:

```fsharp
[<Test>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

Yürütme `dotnet test` yeni test başarısız olur. Bu yeni `squaresOfOdds` testi işlemek için yöntemi güncelleştirmeniz gerekir. Bu testin geçmesi için tüm çift sayıları sıranın dışına filtrelemeniz gerekir. Bunu küçük bir filtre işlevi yazarak `Seq.filter`ve şu ları kullanarak yapabilirsiniz:

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

Çağrıya dikkat `Seq.toList`edin. Bu, <xref:System.Collections.ICollection> arabirimi uygulayan bir liste oluşturur.

Daha bir adım daha var: Tek sayıların her birini karelemek. Yeni bir test yazarak başlayın:

```fsharp
[<Test>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

Her tek sayının karesini hesaplamak için filtreuygulanmış sırayı bir harita işlemi yle borulandırarak testi düzeltebilirsiniz:

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
```

O kitaplık için küçük bir kitaplık ve bir dizi birim testi inşa ettin. Yeni paketler ve testler eklemek normal iş akışının bir parçası olacak şekilde çözümü yapılandırdınız. Zamanınızın ve çabanızın çoğunu uygulamanın hedeflerini çözmeye yoğunlaşmışsınız.

## <a name="see-also"></a>Ayrıca bkz.

- [dotnet add reference](../tools/dotnet-add-reference.md)
- [dotnet test](../tools/dotnet-test.md)
