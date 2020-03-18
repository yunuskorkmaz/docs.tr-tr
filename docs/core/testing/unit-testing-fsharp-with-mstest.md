---
title: Dotnet testi ve MSTest ile .NET Core'da F# testi
description: Dotnet testi ve MSTest kullanarak adım adım örnek bir çözüm oluşturma etkileşimli bir deneyim le .NET Core'da F# için birim test kavramlarını öğrenin.
author: billwagner
ms.author: wiwagn
ms.date: 08/30/2017
ms.openlocfilehash: a685ed8a56393fb6e1c1b9400f0ed4bcef15f9b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714271"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-mstest"></a>Dotnet testi ve MSTest kullanarak .NET Core'daki F# kitaplıklarını test etme birimi

Bu öğretici, birim test kavramlarını öğrenmek için adım adım örnek bir çözüm oluşturma etkileşimli bir deneyim sunar. Önceden oluşturulmuş bir çözüm kullanarak öğreticiyi izlemeyi tercih ederseniz, başlamadan önce [örnek kodu görüntüleyin veya indirin.](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-mstest/) İndirme talimatları için [Örnekler ve Öğreticiler'e](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)bakın.

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="creating-the-source-project"></a>Kaynak proje oluşturma

Bir kabuk penceresi açın. Çözümü tutmak için *birim-test-fsharp adı* verilen bir dizin oluşturun.
Bu yeni dizinin içinde, yeni bir çözüm oluşturmak için çalıştırın. `dotnet new sln` Bu, hem sınıf kitaplığını hem de birim test projesini yönetmeyi kolaylaştırır.
Çözüm dizininin içinde bir *MathService* dizini oluşturun. Dizin ve dosya yapısı şimdiye kadar aşağıda gösterilmiştir:

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

*MathService'i* geçerli dizini `dotnet new classlib -lang "F#"` yapın ve kaynak projeyi oluşturmak için çalıştırın.  Matematik hizmetinin başarısız bir uygulamasını oluşturursunuz:

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

Dizin geri *birim-test-with-fsharp* dizin değiştirin. Sınıf `dotnet sln add .\MathService\MathService.fsproj` kitaplığı projesini çözüme eklemek için çalıştırın.

## <a name="creating-the-test-project"></a>Test projesini oluşturma

Ardından *MathService.Tests* dizinini oluşturun. Aşağıdaki anahat dizin yapısını gösterir:

```console
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

*MathService.Tests* dizinini geçerli dizini oluşturun ve yeni `dotnet new mstest -lang "F#"`bir proje oluşturun. Bu, test çerçevesi olarak MSTest kullanan bir test projesi oluşturur. Oluşturulan şablon *MathServiceTests.fsproj*test koşucusu yapılandırır:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

Test projesi, birim testleri oluşturmak ve çalıştırmak için diğer paketler gerektirir. `dotnet new`önceki adımda MSTest ve MSTest runner eklendi. Şimdi, `MathService` sınıf kitaplığını projeye başka bir bağımlılık olarak ekleyin. Komutu `dotnet add reference` kullanın:

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
        MathServiceTests.fsproj
```

`dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` *Birim-test-with-fsharp* dizininde yürütün.

## <a name="creating-the-first-test"></a>İlk testi oluşturma

Başarısız bir test yazarsın, geçer ve işlemi tekrarlarsın. *Tests.fs'yi* açın ve aşağıdaki kodu ekleyin:

```fsharp
namespace MathService.Tests

open System
open Microsoft.VisualStudio.TestTools.UnitTesting
open MathService

[<TestClass>]
type TestClass () =

    [<TestMethod>]
    member this.TestMethodPassing() =
        Assert.IsTrue(true)

    [<TestMethod>]
     member this.FailEveryTime() = Assert.IsTrue(false)
```

Öznitelik, `[<TestClass>]` testleri içeren bir sınıfı gösterir. Öznitelik, `[<TestMethod>]` test koşucusu tarafından çalıştırılabilen bir test yöntemini gösterir. *Birim-test-with-fsharp* dizininden, testleri `dotnet test` ve sınıf kitaplığını oluşturmak ve testleri çalıştırmak için çalıştırın. MSTest test koşucusu, testlerinizi çalıştırmak için program giriş noktasını içerir. `dotnet test`oluşturduğunuz birim test projesini kullanarak test koşucusu başlatın.

Bu iki test, en temel geçen ve başarısız testleri gösterir. `My test`geçer ve `Fail every time` başarısız olur. Şimdi, `squaresOfOdds` yöntem için bir test oluşturun. Yöntem, `squaresOfOdds` giriş sırasının bir parçası olan tüm tek tamsayı değerlerinin karelerinin listesini döndürür. Tüm bu işlevleri aynı anda yazmaya çalışmak yerine, işlevselliği doğrulayan testleri yinelemeli olarak oluşturabilirsiniz. Her test geçişini yapmak, yöntem için gerekli işlevselliği oluşturmak anlamına gelir.

Yazabileceğimiz en basit test, `squaresOfOdds` sonucun boş bir toplamdarık dizisi olması gereken tüm çift sayılarla aramaktır.  İşte o test:

```fsharp
[<TestMethod>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int> |> Seq.toList
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.AreEqual(expected, actual)
```

`expected` Dizinin bir listeye dönüştürüldüğünü unutmayın. MSTest kitaplığı birçok standart .NET türüne dayanır. Bu bağımlılık, ortak arabiriminizin ve <xref:System.Collections.ICollection> beklenen <xref:System.Collections.IEnumerable>sonuçların değil, 'yi desteklediği anlamına gelir.

Testi çalıştırdığınızda, testinizin başarısız olduğunu görürsünüz. Uygulamayı henüz oluşturmadın. Bu testin çalışmasını sağlayan `Mathservice` sınıftaki en basit kodu yazarak geçmesini sağla:

```fsharp
let squaresOfOdds xs =
    Seq.empty<int> |> Seq.toList
```

*Birim-test-fsharp* dizininde, yeniden çalıştırın. `dotnet test` Komut, `dotnet test` proje ve ardından `MathService.Tests` proje için bir yapı çalışır. `MathService` Her iki projeyi de yaptıktan sonra, bu tek testi çalıştırAr. Geçiyor.

## <a name="completing-the-requirements"></a>Gereksinimleri nama

Artık bir test sınavını geçtiğine göre, daha fazla yazma nın zamanı. Sonraki basit durum, tek sayısı `1`. 1'in karesi 1 olduğundan 1 sayısı daha kolaydır. İşte bir sonraki test:

```fsharp
[<TestMethod>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.AreEqual(expected, actual)
```

Yürütme `dotnet test` yeni test başarısız olur. Bu yeni `squaresOfOdds` testi işlemek için yöntemi güncelleştirmeniz gerekir. Bu testin geçmesi için tüm çift sayıları sıranın dışına filtrelemeniz gerekir. Bunu küçük bir filtre işlevi yazarak `Seq.filter`ve şu ları kullanarak yapabilirsiniz:

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd |> Seq.toList
```

Çağrıya dikkat `Seq.toList`edin. Bu, <xref:System.Collections.ICollection> arabirimi uygulayan bir liste oluşturur.

Daha bir adım daha var: Tek sayıların her birini karelemek. Yeni bir test yazarak başlayın:

```fsharp
[<TestMethod>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.AreEqual(expected, actual)
```

Her tek sayının karesini hesaplamak için filtreuygulanmış sırayı bir harita işlemi yle borulandırarak testi düzeltebilirsiniz:

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
    |> Seq.toList
```

O kitaplık için küçük bir kitaplık ve bir dizi birim testi inşa ettin. Yeni paketler ve testler eklemek normal iş akışının bir parçası olacak şekilde çözümü yapılandırdınız. Zamanınızın ve çabanızın çoğunu uygulamanın hedeflerini çözmeye yoğunlaşmışsınız.

## <a name="see-also"></a>Ayrıca bkz.

- [dotnet new](../tools/dotnet-new.md)
- [dotnet sln](../tools/dotnet-sln.md)
- [dotnet add reference](../tools/dotnet-add-reference.md)
- [dotnet test](../tools/dotnet-test.md)
