---
title: Birim testi F# .NET core'da dotnet testi ve MSTest ile
description: Birim test kavramlarını öğrenin F# dotnet testi ve MSTest, adım adım örnek çözüm oluşturma etkileşimli deneyim aracılığıyla .NET Core kullanarak.
author: billwagner
ms.author: wiwagn
ms.date: 08/30/2017
dev_langs:
- fsharp
ms.custom: seodec18
ms.openlocfilehash: 1765c16cb55857b83a8206ae97327d0fd2809019
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56747498"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-mstest"></a>Birim testi F# dotnet testi ve MSTest kullanarak .NET core'da kitaplıkları

Bu öğretici örnek bir çözüm birim testi kavramlarını öğrenmek için adım adım oluşturmaya etkileşimli deneyim gösterir. Önceden oluşturulmuş bir çözümü kullanarak öğreticiyi uygulamak isterseniz [görüntülemek veya örnek kodu indirdikten](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-mstest/) başlamadan önce. Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

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

Olun *MathService.Tests* dizini geçerli dizin ve kullanarak yeni bir proje oluşturma [ `dotnet new mstest -lang F#` ](../tools/dotnet-new.md). Bu, MSTest test çerçevesi kullanan bir test projesi oluşturur. Test Çalıştırıcısı'nda oluşturulan şablon yapılandırır *MathServiceTests.fsproj*:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

Test projesi oluşturma ve birim testlerini çalıştırmak için diğer paketleri gerektirir. `dotnet new` Önceki adımda, MSTest ve MSTest Çalıştırıcısı eklendi. Şimdi ekleyin `MathService` sınıf kitaplığı projesine başka bir bağımlılık olarak. Kullanım [ `dotnet add reference` ](../tools/dotnet-add-reference.md) komutu:

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

`[<TestClass>]` Özniteliği testleri içeren bir sınıfı gösterir. `[<TestMethod>]` Test Çalıştırıcısı tarafından yürütülen bir test metodu özniteliği gösterir. Gelen *birim-test-ile-fsharp* dizin yürütme [ `dotnet test` ](../tools/dotnet-test.md) testler ve sınıf kitaplığı oluşturun ve ardından testleri çalıştırın. Programın giriş noktası, testlerinizi çalıştırmak için MSTest test Çalıştırıcısı içerir. `dotnet test` oluşturduğunuz birim test projesi kullanarak test Çalıştırıcısı'nı başlatır.

Bu iki testleri en temel geçirme ve testleri başarısız gösterir. `My test` geçer, ve `Fail every time` başarısız olur. Şimdi, test için oluşturma `squaresOfOdds` yöntemi. `squaresOfOdds` Yöntemi kareler Giriş dizisinin bir parçası olan tüm tek sayılı tamsayı değerleri listesi döndürür. Bu işlevlerin tümü aynı anda yazma çalışmak yerine, tekrarlayarak işlevselliğini doğrulama testleri oluşturabilirsiniz. Her test yöntemi için gereken işlevselliği oluşturma anlamına gelir geçirmek yapılıyor.

Biz yazabilirsiniz basit test çağırmaktır `squaresOfOdds` ile sonucu boş bir tam sayı dizisidir olması burada tüm çift sayılarla.  Test şu şekildedir:

```fsharp
[<TestMethod>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int> |> Seq.toList
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.AreEqual(expected, actual)
```

Dikkat `expected` sıralı bir listeye dönüştürülmüş. MSTest kitaplığı çok sayıda standart .NET türlerini kullanır. Destek bağımlılık, ortak arabirim anlamına gelir ve beklenen sonuçları <xref:System.Collections.ICollection> yerine <xref:System.Collections.IEnumerable>.

Test çalıştırdığınızda, test başarısız olduğunu görürsünüz. Uygulama henüz oluşturmadınız. En basit kod yazarak bu testin geçmesini `Mathservice` çalışır sınıfı:

```csharp
let squaresOfOdds xs =
    Seq.empty<int> |> Seq.toList
```

İçinde *birim-test-ile-fsharp* çalışması dizini `dotnet test` yeniden. `dotnet test` Komut çalıştıran bir derleme için `MathService` proje ve ardından `MathService.Tests` proje. Her iki proje oluşturduktan sonra bu tek bir test çalıştırır. Bu geçirir.

## <a name="completing-the-requirements"></a>Gereksinimleri Tamamlanıyor

Bir test geçirmek yaptığınız, daha fazla yazmak için zaman var. Basit bir sonraki durumda, yalnızca tek sayı içeren bir dizisini çalışır `1`. Sayı 1, 1 karesini 1 olduğundan daha kolay olur. Sonraki test şu şekildedir:

```fsharp
[<TestMethod>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.AreEqual(expected, actual)
```

Yürütme `dotnet test` yeni test başarısız olur. Güncelleştirmeniz gerekir `squaresOfOdds` bu yeni test işlemek için yöntemi. Tüm çift sayıları geçirmek bu testi yapmak için sıra dışı filtrelemesi gerekir. Küçük bir filtre işlevi yazma ve kullanarak bunu yapabilirsiniz `Seq.filter`:

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd |> Seq.toList
```

Çağrısını fark `Seq.toList`. Uygulayan bir liste oluşturur <xref:System.Collections.ICollection> arabirimi.

Gitmek için bir adım daha vardır: her biri tek sayıları kare. Yeni bir test yazarak başlatın:

```fsharp
[<TestMethod>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.AreEqual(expected, actual)
```

Filtrelenmiş sırası tek her bir sayının karesini işlem için bir harita işlemi boyunca yönelterek test düzeltebilirsiniz:

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
    |> Seq.toList
```

Küçük bir kitaplık ve bu kitaplık için birim testleri bir dizi oluşturdunuz. Böylece yeni paketler ekleme çözüm yapılandırılmış ve testleri normal iş akışı bir parçasıdır. Zaman ve çaba çözme hedeflerinden biri, uygulama üzerinde en yoğun.
