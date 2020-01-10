---
title: DotNet test F# ve MSTest Ile .NET Core 'da birim testi
description: .NET Core 'da, DotNet F# test ve MSTest kullanarak örnek çözüm oluşturma adımları ile ilgili bir etkileşimli deneyim aracılığıyla birim testi kavramlarını öğrenin.
author: billwagner
ms.author: wiwagn
ms.date: 08/30/2017
ms.openlocfilehash: a685ed8a56393fb6e1c1b9400f0ed4bcef15f9b5
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714271"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-mstest"></a>DotNet test F# ve MSTest kullanarak .NET Core 'da birim testi kitaplıkları

Bu öğreticide, birim testi kavramlarını öğrenmek için bir örnek çözüm oluşturma adım adım yönergeler sunarak etkileşimli bir deneyim sağlanır. Önceden oluşturulmuş bir çözüm kullanarak öğreticiyi izlemeyi tercih ediyorsanız, başlamadan önce [örnek kodu görüntüleyin veya indirin](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-mstest/) . İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="creating-the-source-project"></a>Kaynak proje oluşturma

Bir kabuk penceresi açın. Çözümü tutmak için- *FSharp ile birim-test* adlı bir dizin oluşturun.
Yeni bir çözüm oluşturmak için bu yeni dizinin içinde `dotnet new sln` çalıştırın. Bu, hem sınıf kitaplığını hem de birim testi projesini yönetmeyi kolaylaştırır.
Çözüm dizini içinde bir *MathService* dizini oluşturun. Bu nedenle şu ana kadar dizin ve dosya yapısı aşağıda gösterilmiştir:

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

*MathService* geçerli dizin yapın ve kaynak projeyi oluşturmak için `dotnet new classlib -lang "F#"` çalıştırın.  Matematik hizmeti için başarısız bir uygulama oluşturacaksınız:

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

Dizini- *FSharp dizinine sahip birim-test ile* yeniden değiştirin. Çözüme Sınıf Kitaplığı projesini eklemek için `dotnet sln add .\MathService\MathService.fsproj` çalıştırın.

## <a name="creating-the-test-project"></a>Test projesi oluşturma

Sonra, *MathService. Tests* dizinini oluşturun. Aşağıdaki ana hat dizin yapısını gösterir:

```console
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

*MathService. Tests* dizinini geçerli dizini yapın ve `dotnet new mstest -lang "F#"`kullanarak yeni bir proje oluşturun. Bu, test çerçevesi olarak MSTest kullanan bir test projesi oluşturur. Oluşturulan şablon, *MathServiceTests. fsproj*içindeki Test Çalıştırıcısı 'nı yapılandırır:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

Test projesi, birim testlerini oluşturmak ve çalıştırmak için diğer paketlerin kullanılmasını gerektirir. önceki adımda `dotnet new` MSTest ve MSTest Çalıştırıcısı eklendi. Şimdi, `MathService` sınıf kitaplığını projeye başka bir bağımlılık olarak ekleyin. `dotnet add reference` komutunu kullanın:

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

*Birim-test--FSharp* diziniyle `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` yürütün.

## <a name="creating-the-first-test"></a>İlk test oluşturma

Başarısız bir test yazdığınızda, geçişi yapıp işlemi tekrarlayabilirsiniz. *Tests. FS* ' i açın ve aşağıdaki kodu ekleyin:

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

`[<TestClass>]` özniteliği, testleri içeren bir sınıfı gösterir. `[<TestMethod>]` özniteliği, Test Çalıştırıcısı tarafından çalıştırılan bir test yöntemini gösterir. *Birim-test--FSharp* dizininden, testleri ve sınıf kitaplığını oluşturmak için `dotnet test` yürütün ve ardından testleri çalıştırın. MSTest Test Çalıştırıcısı, testlerinizi çalıştırmak için program giriş noktasını içerir. `dotnet test`, oluşturduğunuz birim test projesini kullanarak Test Çalıştırıcısı başlatır.

Bu iki test, en temel geçirme ve başarısız testleri gösterir. `My test` geçirilir ve `Fail every time` başarısız olur. Şimdi `squaresOfOdds` yöntemi için bir test oluşturun. `squaresOfOdds` yöntemi, giriş dizisinin parçası olan tüm tek tamsayı değerlerinin karelerinin bir listesini döndürür. Bu işlevlerin tümünü aynı anda yazmaya çalışmak yerine, işlevi doğrulayan testleri tekrarlayarak oluşturabilirsiniz. Her test geçişinin yapılması, yöntemi için gerekli işlevselliğin oluşturulması anlamına gelir.

Yazdığımız en basit test, tüm çift sayılarla `squaresOfOdds` çağırmakta olduğundan, sonucun boş bir tamsayılar dizisi olması gerekir.  Bu test şu şekildedir:

```fsharp
[<TestMethod>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int> |> Seq.toList
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.AreEqual(expected, actual)
```

`expected` sırasının bir listeye dönüştürüldüğüne dikkat edin. MSTest kitaplığı birçok standart .NET türünü kullanır. Bu bağımlılık, genel arabiriminiz ve beklenen sonuçlar <xref:System.Collections.IEnumerable>yerine <xref:System.Collections.ICollection> destekledikleri anlamına gelir.

Testi çalıştırdığınızda, testinizin başarısız olduğunu görürsünüz. Uygulamayı henüz oluşturmadınız. Aşağıdaki `Mathservice` sınıfında en basit kodu yazarak bu test geçişini yapın:

```fsharp
let squaresOfOdds xs =
    Seq.empty<int> |> Seq.toList
```

*Birim-test--FSharp diziniyle birlikte* `dotnet test` yeniden çalıştırın. `dotnet test` komutu, `MathService` projesi için bir derleme ve sonra `MathService.Tests` projesi için çalışır. Her iki proje de oluşturulduktan sonra bu tek testi çalıştırır. Geçirir.

## <a name="completing-the-requirements"></a>Gereksinimleri tamamlama

Artık bir test geçişi yapmış olduğunuza göre daha fazla yazma zamanı vardır. Bir sonraki basit durum yalnızca tek sayı `1`olan bir sıra ile birlikte kullanılır. 1 numaralı kare 1 olduğundan, 1 sayısı daha kolay. İşte bu sonraki test:

```fsharp
[<TestMethod>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.AreEqual(expected, actual)
```

`dotnet test` yürütülmesi yeni test başarısız olur. Bu yeni testi işlemek için `squaresOfOdds` metodunu güncelleştirmeniz gerekir. Bu test geçişini yapmak için tüm çift sayıları sıranın dışına filtrelemeniz gerekir. Bunu, küçük bir filtre işlevi yazarak ve `Seq.filter`kullanarak yapabilirsiniz:

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd |> Seq.toList
```

`Seq.toList`çağrısına dikkat edin. Bu, <xref:System.Collections.ICollection> arabirimini uygulayan bir liste oluşturur.

Bir adım daha vardır: her bir tek sayının kare sayısı. Yeni bir test yazarak başlayın:

```fsharp
[<TestMethod>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.AreEqual(expected, actual)
```

Her bir tek sayının karesini hesaplamak için, filtre uygulanmış sırayı bir eşleme işlemi aracılığıyla ayırarak testi giderebilirsiniz:

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
    |> Seq.toList
```

Bu kitaplık için küçük bir kitaplık ve birim testleri kümesi oluşturdunuz. Çözümü, yeni paket ve test eklemek normal iş akışının bir parçası olacak şekilde öğrendiniz. Uygulamanın hedeflerini çözme konusunda zaman ve çaba harcamanızı en iyi şekilde gördünüz.

## <a name="see-also"></a>Ayrıca bkz.

- [dotnet new](../tools/dotnet-new.md)
- [dotnet sln](../tools/dotnet-sln.md)
- [dotnet add reference](../tools/dotnet-add-reference.md)
- [dotnet test](../tools/dotnet-test.md)
