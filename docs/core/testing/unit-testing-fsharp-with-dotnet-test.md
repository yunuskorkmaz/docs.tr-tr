---
title: "Birim F # kitaplığı .NET dotnet test ve xUnit kullanarak çekirdek testi"
description: "Birim testi kavramları F # .NET Core için adım adım örnek çözüm oluşturma bir etkileşimli deneyimler aracılığıyla öğrenmeniz dotnet test ve xUnit kullanarak."
author: billwagner
ms.author: wiwagn
ms.date: 08/30/2017
ms.topic: article
dev_langs: fsharp
ms.prod: .net-core
ms.workload: dotnetcore
ms.openlocfilehash: 6a9596db49024bead9c33b52642f46f519bb2b4c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-xunit"></a>Birim F # kitaplığı .NET dotnet test ve xUnit kullanarak çekirdek testi

Bu öğretici birim testi kavramlarını öğrenmek için adım adım örnek çözüm oluşturma etkileşimli bir deneyim gösterir. Önceden oluşturulmuş bir çözümü kullanarak öğreticiyi izleyin tercih ediyorsanız [görüntülemek veya karşıdan örnek kod](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-with-fsharp/) başlamadan önce. Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="creating-the-source-project"></a>Kaynak projesi oluşturma

Kabuk penceresini açın. Adlı bir dizin oluşturun *birim-test etme-ile-fsharp* çözümü tutmak için.
Bu yeni dizin içinde çalıştırmak [ `dotnet new sln` ](../tools/dotnet-new.md) yeni bir çözüm oluşturmak için. Bu sınıf kitaplığı ve birim testi projesi yönetmeyi kolaylaştırır.
Çözüm dizini içinde oluşturmak bir *MathService* dizini. Dizin ve dosya yapısı bugüne kadarki aşağıda gösterilmiştir:

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

Olun *MathService* geçerli dizin ve çalışma [ `dotnet new classlib -lang F#` ](../tools/dotnet-new.md) kaynak projesi oluşturmak için.  Teste dayalı geliştirme (TDD) kullanmak için başarısız olan uygulama matematik hizmetinin oluşturursunuz:

```fsharp
module MyMath =
    let sumOfSquares xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

Dizin geri değişiklik *birim-test etme-ile-fsharp* dizini. Çalıştırma [ `dotnet sln add .\MathService\MathService.fsproj` ](../tools/dotnet-sln.md) sınıf kitaplığı proje çözüme eklemek için.

## <a name="creating-the-test-project"></a>Test projesi oluşturma

Ardından, oluşturun *MathService.Tests* dizini. Aşağıdaki anahat dizin yapısını gösterir:

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

Olun *MathService.Tests* dizine geçerli ve kullanarak yeni bir proje oluşturun [ `dotnet new xunit -lang F#` ](../tools/dotnet-new.md). Bu test kitaplık olarak xUnit kullanan bir test projesi oluşturur. Test Çalıştırıcısı'nda oluşturulan şablon yapılandırır *MathServiceTests.fsproj*:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

Test projesi oluşturmak ve birim testleri çalıştırmak için diğer paketleri gerektirir. `dotnet new`Önceki adımda xUnit ve xUnit Çalıştırıcısı eklendi. Şimdi, ekleyin `MathService` sınıf kitaplığı proje için başka bir bağımlılık olarak. Kullanım [ `dotnet add reference` ](../tools/dotnet-add-reference.md) komutu:

```
dotnet add reference ../MathService/MathService.fsproj
```

Tüm dosyasında görebilirsiniz [örnekleri deposu](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) github'da.

Aşağıdaki nihai çözüm düzeni vardır:

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

Yürütme [ `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` ](../tools/dotnet-sln.md) içinde *birim-test etme-ile-fsharp* dizini. 

## <a name="creating-the-first-test"></a>İlk testi oluşturma

TDD yaklaşım geçirmek kolaylaştırarak ve süreci tekrarlayarak yazma bir başarısız test için çağırır. Açık *Tests.fs* ve aşağıdaki kodu ekleyin:

```fsharp
[<Fact>]
let ``My test`` () =
    Assert.True(true)

[<Fact>]
let ``Fail every time`` () = Assert.True(false)
```

`[<Fact>]` Özniteliği test Çalıştırıcısı tarafından çalıştırılan test yöntemini gösterir. Gelen *birim-test etme-ile-fsharp*, yürütme [ `dotnet test` ](../tools/dotnet-test.md) testleri ve sınıf kitaplığı oluşturmak ve ardından testleri çalıştırın. XUnit test Çalıştırıcısı testleri çalıştırmak için program giriş noktası içerir. `dotnet test`oluşturduğunuz birim testi projesi kullanarak test Çalıştırıcısı başlatır.

Bu iki testleri en temel geçirme ve testleri başarısız gösterir. `My test`geçirir, ve `Fail every time` başarısız olur. Şimdi, test için oluşturma `sumOfSquares` yöntemi. `sumOfSquares` Yöntemi Giriş dizisinin bir parçası olan tüm tek sayılı tamsayı değerleri kareleri toplamını döndürür. Bu işlevlerin tümüne tek seferde yazmaya çalışırken yerine işlevselliğini doğrulama testleri tekrarlayarak oluşturabilirsiniz. Yöntemi için gerekli işlevselliği oluşturma anlamına gelir geçirmek her test yapma.

Biz yazabilirler basit test çağırmaktır `sumOfSquares` tüm çift numaraları, burada sonucu olmalıdır boş bir tam sayı dizisidir.  Bu test şöyledir:

```fsharp
[<Fact>]
let ``Sum of evens returns empty collection`` () =
    let expected = Seq.empty<int>
    let actual = MyMath.sumOfSquares [2; 4; 6; 8; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

Testiniz başarısız olur. Uygulama henüz oluşturmadınız. Bu test basit kod yazarken yapmasına `MathService` çalışır sınıfı:

```csharp
let sumOfSquares xs =
    Seq.empty<int>
```

İçinde *birim-test etme-ile-fsharp* çalışması dizini `dotnet test` yeniden. `dotnet test` Komutu çalıştıran bir yapı `MathService` proje ve ardından `MathService.Tests` projesi. Her iki proje oluşturduktan sonra bu tek bir test çalıştırılır. Bunu geçirir.

## <a name="completing-the-requirements"></a>Gereksinimleri Tamamlanıyor

Bir test geçirmek yapmış olduğunuz, daha fazla yazma zamanı geldi. Sonraki basit bir durumda, yalnızca tek sayı olan bir sıra ile çalışır `1`. 1 sayısı 1'in Kare 1 olduğundan daha kolay olur. Sonraki test şöyledir:

```fsharp
[<Fact>]
let ``Sum of sequences of Ones and Evens`` () =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.sumOfSquares [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

Yürütme `dotnet test` testlerinizi çalıştırır ve yeni test başarısız olduğunu gösterir. Şimdi, güncelleştirme `sumOfSquares` bu yeni test işlemek için yöntem. Geçirmek bu testi yapmak için sıra dışında tüm çift sayıları filtreleyin. Küçük filtre işlevi yazma ve kullanarak bunu, `Seq.filter`:

```fsharp
let private isOdd x = x % 2 <> 0

let sumOfSquares xs =
    xs
    |> Seq.filter isOdd
```

Gitmek için bir adım daha vardır: her tek sayıların karesini. Yeni bir test yazarak başlatın:

```fsharp
[<Fact>]
let ``SquaresOfOdds works`` () =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.sumOfSquares [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.Equal(expected, actual)
```

Her tek sayı kare hesaplamak için eşleme işlemi aracılığıyla filtrelenmiş dizisi cmdlet'ine yönelterek test düzeltebilirsiniz:

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let sumOfSquares xs = 
    xs 
    |> Seq.filter isOdd 
    |> Seq.map square
```

Küçük bir kitaplığı ve bu kitaplık için birim testleri kümesini temel aldık. Böylece yeni paketleri ekleme çözümü yapılandırılmış ve testleri normal iş akışı bir parçasıdır. Çoğu zaman ve çaba uygulama amaçlarını çözme üzerinde yoğunlaşmıştır.
