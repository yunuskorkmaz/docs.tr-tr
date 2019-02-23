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
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-xunit"></a>Birim testi F# kitaplıkları .NET core'da dotnet testi ve xUnit kullanma

Bu öğretici örnek bir çözüm birim testi kavramlarını öğrenmek için adım adım oluşturmaya etkileşimli deneyim gösterir. Önceden oluşturulmuş bir çözümü kullanarak öğreticiyi uygulamak isterseniz [görüntülemek veya örnek kodu indirdikten](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp/) başlamadan önce. Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="creating-the-source-project"></a>Kaynak proje oluşturma

Shell penceresini açın. Adlı bir dizin oluşturun *birim-test-ile-fsharp* çözüm tutacak.
Bu yeni dizin içinde çalıştırma [ `dotnet new sln` ](../tools/dotnet-new.md) yeni bir çözüm oluşturmak için. Bu, hem sınıf kitaplığı ve birim testi projesi yönetmenizi kolaylaştırır.
Çözüm dizini içinde bir *MathService* dizin. Dizin ve dosya yapısı, şimdiye kadarki aşağıda gösterilmiştir:

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

Olun *MathService* geçerli dizin ve çalışma [ `dotnet new classlib -lang F#` ](../tools/dotnet-new.md) kaynak proje oluşturmak için.  Matematik hizmet başarısız uyarlamasını oluşturacaksınız:

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

Dizine dön değişiklik *birim-test-ile-fsharp* dizin. Çalıştırma [ `dotnet sln add .\MathService\MathService.fsproj` ](../tools/dotnet-sln.md) sınıf kitaplığı projesi çözüme eklemek için.

## <a name="creating-the-test-project"></a>Test projesi oluşturma

Ardından, oluşturma *MathService.Tests* dizin. Ana hat aşağıdaki dizin yapısını gösterir:

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

Olun *MathService.Tests* dizini geçerli dizin ve kullanarak yeni bir proje oluşturma [ `dotnet new xunit -lang F#` ](../tools/dotnet-new.md). Bu, xUnit test kitaplık olarak kullanan bir test projesi oluşturur. Test Çalıştırıcısı'nda oluşturulan şablon yapılandırır *MathServiceTests.fsproj*:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

Test projesi oluşturma ve birim testlerini çalıştırmak için diğer paketleri gerektirir. `dotnet new` Önceki adımda, xUnit ve xUnit Çalıştırıcısı eklendi. Şimdi ekleyin `MathService` sınıf kitaplığı projesine başka bir bağımlılık olarak. Kullanım [ `dotnet add reference` ](../tools/dotnet-add-reference.md) komutu:

```
dotnet add reference ../MathService/MathService.fsproj
```

Dosyanın tamamını görebilirsiniz [örnekleri depomuzdan](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) GitHub üzerinde.

Aşağıdaki nihai çözüm Düzen vardır:

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

Yürütme [ `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` ](../tools/dotnet-sln.md) içinde *birim-test-ile-fsharp* dizin. 

## <a name="creating-the-first-test"></a>İlk testi oluşturma

Bir yazma, test başarısız kolaylaştırır geçişi, sonra işlemi yineleyin. Açık *Tests.fs* ve aşağıdaki kodu ekleyin:

```fsharp
[<Fact>]
let ``My test`` () =
    Assert.True(true)

[<Fact>]
let ``Fail every time`` () = Assert.True(false)
```

`[<Fact>]` Test Çalıştırıcısı tarafından yürütülen bir test metodu özniteliği gösterir. Gelen *birim-test-ile-fsharp*, yürütme [ `dotnet test` ](../tools/dotnet-test.md) testler ve sınıf kitaplığı oluşturun ve ardından testleri çalıştırın. XUnit test Çalıştırıcısı, testlerinizi çalıştırmak için programın giriş noktası içerir. `dotnet test` oluşturduğunuz birim test projesi kullanarak test Çalıştırıcısı'nı başlatır.

Bu iki testleri en temel geçirme ve testleri başarısız gösterir. `My test` geçer, ve `Fail every time` başarısız olur. Şimdi, test için oluşturma `squaresOfOdds` yöntemi. `squaresOfOdds` Yöntemi Giriş dizisinin bir parçası olan tüm tek tamsayı değerleri kareleri bir dizisi döndürür. Bu işlevlerin tümü aynı anda yazma çalışmak yerine, tekrarlayarak işlevselliğini doğrulama testleri oluşturabilirsiniz. Her test yöntemi için gereken işlevselliği oluşturma anlamına gelir geçirmek yapılıyor.

Biz yazabilirsiniz basit test çağırmaktır `squaresOfOdds` ile sonucu boş bir tam sayı dizisidir olması burada tüm çift sayılarla.  Test şu şekildedir:

```fsharp
[<Fact>]
let ``Sequence of Evens returns empty collection`` () =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

Test başarısız olur. Uygulama henüz oluşturmadınız. En basit kod yazarak bu testin geçmesini `MathService` çalışır sınıfı:

```csharp
let squaresOfOdds xs =
    Seq.empty<int>
```

İçinde *birim-test-ile-fsharp* çalışması dizini `dotnet test` yeniden. `dotnet test` Komut çalıştıran bir derleme için `MathService` proje ve ardından `MathService.Tests` proje. Her iki proje oluşturduktan sonra bu tek bir test çalıştırır. Bu geçirir.

## <a name="completing-the-requirements"></a>Gereksinimleri Tamamlanıyor

Bir test geçirmek yaptığınız, daha fazla yazmak için zaman var. Basit bir sonraki durumda, yalnızca tek sayı içeren bir dizisini çalışır `1`. Sayı 1, 1 karesini 1 olduğundan daha kolay olur. Sonraki test şu şekildedir:

```fsharp
[<Fact>]
let ``Sequences of Ones and Evens returns Ones`` () =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.Equal<Collections.Generic.IEnumerable<int>>(expected, actual)
```

Yürütme `dotnet test` Testlerinizi çalıştırma ve yeni test başarısız olduğunu gösterir. Şimdi, güncelleştirme `squaresOfOdds` bu yeni test işlemek için yöntemi. Tüm çift sayıları geçirmek bu testi yapmak için sıra dışı filtre. Küçük bir filtre işlevi yazma ve kullanarak bunu yapabilirsiniz `Seq.filter`:

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

Gitmek için bir adım daha vardır: her biri tek sayıları kare. Yeni bir test yazarak başlatın:

```fsharp
[<Fact>]
let ``SquaresOfOdds works`` () =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.Equal(expected, actual)
```

Filtrelenmiş sırası tek her bir sayının karesini işlem için bir harita işlemi boyunca yönelterek test düzeltebilirsiniz:

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs = 
    xs 
    |> Seq.filter isOdd 
    |> Seq.map square
```

Küçük bir kitaplık ve bu kitaplık için birim testleri bir dizi oluşturdunuz. Böylece yeni paketler ekleme çözüm yapılandırılmış ve testleri normal iş akışı bir parçasıdır. Zaman ve çaba çözme hedeflerinden biri, uygulama üzerinde en yoğun.
