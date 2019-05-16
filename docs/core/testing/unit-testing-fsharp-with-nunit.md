---
title: Birim testi F# .NET core'da dotnet testi ve NUnit ile
description: Birim test kavramlarını öğrenin F# dotnet testi ve NUnit kullanarak .NET core'da adım adım örnek çözüm oluşturma etkileşimli bir deneyim.
author: rprouse
ms.date: 10/04/2018
dev_langs:
- fsharp
ms.custom: seodec18
ms.openlocfilehash: 926e47c277c8649627482a8036ca3704be142f33
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65631875"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-nunit"></a>Birim testi F# dotnet testi ve NUnit kullanarak .NET core'da kitaplıkları

Bu öğretici örnek bir çözüm birim testi kavramlarını öğrenmek için adım adım oluşturmaya etkileşimli deneyim gösterir. Önceden oluşturulmuş bir çözümü kullanarak öğreticiyi uygulamak isterseniz [görüntülemek veya örnek kodu indirdikten](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-nunit/) başlamadan önce. Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="prerequisites"></a>Önkoşullar

- [.NET core 2.1 SDK](https://www.microsoft.com/net/download) veya sonraki sürümler.
- Bir metin düzenleyicisi veya tercih ettiğiniz Kod Düzenleyicisi.

## <a name="creating-the-source-project"></a>Kaynak proje oluşturma

Shell penceresini açın. Adlı bir dizin oluşturun *birim-test-ile-fsharp* çözüm tutacak.
Bu yeni dizin içinde sınıf kitaplığı ve test projesi için yeni bir çözüm dosyası oluşturmak için aşağıdaki komutu çalıştırın:

```console
dotnet new sln
```

Ardından, oluşturun bir *MathService* dizin. Aşağıdaki ana hat dizin ve dosya yapısı şu ana kadar gösterilmektedir:

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

Olun *MathService* aşağıdaki komut kaynak projesi oluşturmak için geçerli dizin ve çalıştırma:

```console
dotnet new classlib -lang F#
```

Bir matematik hizmetin başarısız uygulama oluşturun:

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

Dizine dön değişiklik *birim-test-ile-fsharp* dizin. Sınıf kitaplığı projesi çözüme eklemek için aşağıdaki komutu çalıştırın:

```console
dotnet sln add .\MathService\MathService.fsproj
```

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

Olun *MathService.Tests* dizini geçerli dizin ve aşağıdaki komutu kullanarak yeni bir proje oluşturun:

```console
dotnet new nunit -lang F#
```

Bu, NUnit test çerçevesi kullanan bir test projesi oluşturur. Test Çalıştırıcısı'nda oluşturulan şablon yapılandırır *MathServiceTests.fsproj*:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

Test projesi oluşturma ve birim testlerini çalıştırmak için diğer paketleri gerektirir. `dotnet new` Önceki adımda NUnit ve NUnit test bağdaştırıcısı eklendi. Şimdi ekleyin `MathService` sınıf kitaplığı projesine başka bir bağımlılık olarak. Kullanım [ `dotnet add reference` ](../tools/dotnet-add-reference.md) komutu:

```console
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
        MathService.Tests.fsproj
```

Aşağıdaki komutu yürütün *birim-test-ile-fsharp* dizini:

```console
dotnet sln add .\MathService.Tests\MathService.Tests.fsproj
```

## <a name="creating-the-first-test"></a>İlk testi oluşturma

Bir yazma, test başarısız kolaylaştırır geçişi, sonra işlemi yineleyin. Açık *UnitTest1.fs* ve aşağıdaki kodu ekleyin:

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

`[<TestFixture>]` Özniteliği testleri içeren bir sınıfı gösterir. `[<Test>]` Test Çalıştırıcısı tarafından yürütülen bir test metodu özniteliği gösterir. Gelen *birim-test-ile-fsharp* dizin yürütme [ `dotnet test` ](../tools/dotnet-test.md) testler ve sınıf kitaplığı oluşturun ve ardından testleri çalıştırın. NUnit test Çalıştırıcısı, testlerinizi çalıştırmak için programın giriş noktası içerir. `dotnet test` oluşturduğunuz birim test projesi kullanarak test Çalıştırıcısı'nı başlatır.

Bu iki testleri en temel geçirme ve testleri başarısız gösterir. `My test` geçer, ve `Fail every time` başarısız olur. Şimdi, test için oluşturma `squaresOfOdds` yöntemi. `squaresOfOdds` Yöntemi Giriş dizisinin bir parçası olan tüm tek tamsayı değerleri kareleri bir dizisi döndürür. Bu işlevlerin tümü aynı anda yazma çalışmak yerine, tekrarlayarak işlevselliğini doğrulama testleri oluşturabilirsiniz. Her test yöntemi için gereken işlevselliği oluşturma anlamına gelir geçirmek yapılıyor.

Biz yazabilirsiniz basit test çağırmaktır `squaresOfOdds` ile sonucu boş bir tam sayı dizisidir olması burada tüm çift sayılarla.  Test şu şekildedir:

```fsharp
[<Test>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

Dikkat `expected` sıralı bir listeye dönüştürülmüş. NUnit framework birçok standart .NET türü kullanır. Destek bağımlılık, ortak arabirim anlamına gelir ve beklenen sonuçları <xref:System.Collections.ICollection> yerine <xref:System.Collections.IEnumerable>.

Test çalıştırdığınızda, test başarısız olduğunu görürsünüz. Uygulama henüz oluşturmadınız. En basit kod yazarak geçirmek bu testin geçmesini *Library.fs* sınıfı MathService projenizdeki çalışır:

```csharp
let squaresOfOdds xs =
    Seq.empty<int>
```

İçinde *birim-test-ile-fsharp* çalışması dizini `dotnet test` yeniden. `dotnet test` Komut çalıştıran bir derleme için `MathService` proje ve ardından `MathService.Tests` proje. Her iki proje oluşturduktan sonra testlerinizi çalıştırır. Şimdi iki test geçirin.

## <a name="completing-the-requirements"></a>Gereksinimleri Tamamlanıyor

Bir test geçirmek yaptığınız, daha fazla yazmak için zaman var. Basit bir sonraki durumda, yalnızca tek sayı içeren bir dizisini çalışır `1`. Sayı 1, 1 karesini 1 olduğundan daha kolay olur. Sonraki test şu şekildedir:

```fsharp
[<Test>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

Yürütme `dotnet test` yeni test başarısız olur. Güncelleştirmeniz gerekir `squaresOfOdds` bu yeni test işlemek için yöntemi. Tüm çift sayıları geçirmek bu testi yapmak için sıra dışı filtrelemesi gerekir. Küçük bir filtre işlevi yazma ve kullanarak bunu yapabilirsiniz `Seq.filter`:

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

Çağrısını fark `Seq.toList`. Uygulayan bir liste oluşturur <xref:System.Collections.ICollection> arabirimi.

Gitmek için bir adım daha vardır: her biri tek sayıları kare. Yeni bir test yazarak başlatın:

```fsharp
[<Test>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.That(actual, Is.EqualTo(expected))
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
