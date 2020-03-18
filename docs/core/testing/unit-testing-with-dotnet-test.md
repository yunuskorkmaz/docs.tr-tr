---
title: Dotnet testi ve xUnit kullanarak .NET Core'da C# kodunu test etme birimi
description: Noktanet testi ve xUnit kullanarak adım adım örnek bir çözüm oluşturma etkileşimli bir deneyim le C# ve .NET Core'daki birim test kavramlarını öğrenin.
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: c9e3d63a2cf4f560591459833340b729ffec1b95
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240902"
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a>Dotnet testi ve xUnit kullanarak .NET Core'da C# testi

Bu öğretici, birim test projesi ve kaynak kodu projesi içeren bir çözümün nasıl oluşturulabildiğini gösterir. Önceden oluşturulmuş bir çözümü kullanarak öğreticiyi takip etmek için [örnek kodu görüntüleyin veya indirin.](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/) İndirme talimatları için [Örnekler ve Öğreticiler'e](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)bakın.

## <a name="create-the-solution"></a>Çözümü oluşturun

Bu bölümde, kaynak ve test projelerini içeren bir çözüm oluşturulur. Tamamlanan çözüm aşağıdaki dizin yapısına sahiptir:

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        PrimeService.cs
        PrimeService.csproj
    /PrimeService.Tests
        PrimeService_IsPrimeShould.cs
        PrimeServiceTests.csproj
```

Aşağıdaki yönergeler, test çözümlerini oluşturmak için adımları sağlar. Test çözümlerini tek adımda oluşturmak için talimatlar için test çözümü oluşturmak için [Komutlar'a](#create-test-cmd) bakın.

* Bir kabuk penceresi açın.
* Şu komutu çalıştırın:

  ```dotnetcli
  dotnet new sln -o unit-testing-using-dotnet-test
  ```

  Komut, [`dotnet new sln`](../tools/dotnet-new.md) *birim-test-using-dotnet-test* dizininde yeni bir çözüm oluşturur.
* *Dizin,birim-test-kullanarak-dotnet-test* klasörüne değiştirin.
* Şu komutu çalıştırın:

  ```dotnetcli
  dotnet new classlib -o PrimeService
  ```

   Komut, [`dotnet new classlib`](../tools/dotnet-new.md) *PrimeService* klasöründe yeni bir sınıf kitaplığı projesi oluşturur. Yeni sınıf kitaplığı sınanacak kodu içerir.
* *Class1.cs* *PrimeService.cs*yeniden adlandırın.
* *PrimeService.cs* kodu aşağıdaki kodla değiştirin:
  
  ```csharp
    using System;

    namespace Prime.Services
    {
        public class PrimeService
        {
            public bool IsPrime(int candidate)
            {
                throw new NotImplementedException("Not implemented.");
            }
        }
    }
  ```

* Yukarıdaki kod:
  * Uygulanmadığını <xref:System.NotImplementedException> belirten bir ileti atar.
  * Öğreticinin daha sonra güncellenir.

<!-- preceding code shows an english bias. Message makes no sense outside english -->

* *Birim-test-using-dotnet-test* dizininde, sınıf kitaplığı projesini çözüme eklemek için aşağıdaki komutu çalıştırın:

  ```dotnetcli
  dotnet sln add ./PrimeService/PrimeService.csproj
  ```

* Aşağıdaki komutu çalıştırarak *PrimeService.Tests* projesini oluşturun:

  ```dotnetcli
  dotnet new xunit -o PrimeService.Tests
  ```

* Yukarıdaki komut:
  * *PrimeService.Tests* dizininde *PrimeService.Tests* projesini oluşturur. Test projesi, test kitaplığı olarak [xUnit](https://xunit.github.io/) kullanır.
  * Proje dosyasına aşağıdaki `<PackageReference />`öğeleri ekleyerek test runnerını yapılandırır:
    * "Microsoft.NET.Test.Sdk"
    * "xunit"
    * "xunit.runner.visualstudio"

* Aşağıdaki komutu çalıştırarak çözüm dosyasına test projesini ekleyin:

  ```dotnetcli
  dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
  ```

* `PrimeService` Sınıf kitaplığını *PrimeService.Tests* projesine bağımlılık olarak ekleyin:

  ```dotnetcli
  dotnet add ./PrimeService.Tests/PrimeService.Tests.csproj reference ./PrimeService/PrimeService.csproj  
  ```

<a name="create-test-cmd"></a>

### <a name="commands-to-create-the-solution"></a>Çözümü oluşturmak için komutlar

Bu bölümde önceki bölümdeki tüm komutlar özetlenmiştir. Önceki bölümdeki adımları tamamladıysanız bu bölümü atlayın.

Aşağıdaki komutlar bir windows makinesinde test çözümcürse oluşturun. macOS ve Unix için, dosyayı `ren` yeniden `ren` adlandırmak için işletim sistemi sürümüne komutu güncelleştirin:

```dotnetcli
dotnet new sln -o unit-testing-using-dotnet-test
cd unit-testing-using-dotnet-test
dotnet new classlib -o PrimeService
ren .\PrimeService\Class1.cs PrimeService.cs
dotnet sln add ./PrimeService/PrimeService.csproj
dotnet new xunit -o PrimeService.Tests
dotnet add ./PrimeService.Tests/PrimeService.Tests.csproj reference ./PrimeService/PrimeService.csproj
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
```

Önceki bölümdeki *"Kodu PrimeService.cs* aşağıdaki kodla değiştirin" yönergelerini izleyin.

## <a name="create-a-test"></a>Test oluşturma

Test odaklı geliştirmede (TDD) popüler bir yaklaşım, hedef kodu uygulamadan önce bir test yazmaktır. Bu öğretici TDD yaklaşımını kullanır. Yöntem `IsPrime` çağrılabilir, ancak uygulanmaz. Başarısız olmak `IsPrime` için bir test çağrısı. TDD ile başarısız olduğu bilinen bir test yazılır. Hedef kod, test sınavını geçmek için güncelleştirilir. Bu yaklaşımı yinelemeye, başarısız bir test yazmaya ve ardından geçmek için hedef kodu güncelleştirmeye devam edin.

Güncelleştirme *PrimeService.Tests* proje:

* *Delete PrimeService.Tests/UnitTest1.cs*.
* *PrimeService.Tests/PrimeService_IsPrimeShould.cs* dosyası oluşturun.
* *PrimeService_IsPrimeShould.cs'deki* kodu aşağıdaki kodla değiştirin:

```csharp
using Xunit;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;

        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [Fact]
        public void IsPrime_InputIs1_ReturnFalse()
        {
            var result = _primeService.IsPrime(1);

            Assert.False(result, "1 should not be prime");
        }
    }
}
```

Öznitelik, `[Fact]` test koşucusu tarafından çalıştırılabilen bir test yöntemini bildirir. *PrimeService.Tests* klasöründen `dotnet test`çalıştırın. [dotnet test](../tools/dotnet-test.md) komutu her iki projeyi oluşturur ve testleri çalıştırar. xUnit test koşucusu testleri çalıştırmak için program giriş noktasını içerir. `dotnet test`ünite test projesini kullanarak test koşucusu başlatın.

Test başarısız `IsPrime` oldu çünkü uygulanmadı. TDD yaklaşımını kullanarak, bu testin geçmesi için yalnızca yeterli kodu yazın. Aşağıdaki `IsPrime` kodla güncelleştirin:

```csharp
public bool IsPrime(int candidate)
{
    if (candidate == 1)
    {
        return false;
    }
    throw new NotImplementedException("Not fully implemented.");
}
```

`dotnet test` öğesini çalıştırın. Test geçer.

### <a name="add-more-tests"></a>Daha fazla test ekleme

0 ve -1 için asal sayı testleri ekleyin. Önceki testi kopyalayabilir ve aşağıdaki kodu 0 ve -1'i kullanmak üzere değiştirebilirsiniz:

```csharp
var result = _primeService.IsPrime(1);

Assert.False(result, "1 should not be prime");
```

Yalnızca bir parametre değiştiğinde test kodunun kopyalanması kod çoğaltma ve test şişkinliğiyle sonuçlanır. Aşağıdaki xUnit öznitelikleri benzer testlerin bir paketi yazmayı sağlar:

- `[Theory]`aynı kodu çalıştıran ancak farklı giriş bağımsız değişkenleri olan bir test paketini temsil eder.

- `[InlineData]`öznitelik bu girişler için değerleri belirtir.

Yeni testler oluşturmak yerine, tek bir teori oluşturmak için önceki xUnit özniteliklerini uygulayın. Aşağıdaki kodu değiştirin:

```csharp
[Fact]
public void IsPrime_InputIs1_ReturnFalse()
{
    var result = _primeService.IsPrime(1);

    Assert.False(result, "1 should not be prime");
}
```

aşağıdaki kod ile:

[!code-csharp[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-using-dotnet-test/csharp/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

Önceki kodda `[Theory]` ve `[InlineData]` ikiden küçük birkaç değerin test edilmesini etkinleştirin. İki, en küçük asal sayıdır.

Çalıştır `dotnet test`, iki test başarısız. Tüm testlerin geçmesi için yöntemi `IsPrime` aşağıdaki kodla güncelleştirin:

```csharp
public bool IsPrime(int candidate)
{
    if (candidate < 2)
    {
        return false;
    }
    throw new NotImplementedException("Not fully implemented.");
}
```

TDD yaklaşımını izleyerek, daha fazla başarısız test ekleyin ve ardından hedef kodu güncelleştirin. [Testlerin tamamlanmış sürümüne](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) ve [kitaplığın tam uygulamasına](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs)bakın.

Tamamlanan `IsPrime` yöntem ilkelliği sınamak için etkili bir algoritma değildir.

### <a name="additional-resources"></a>Ek kaynaklar

- [resmi site xUnit.net](https://xunit.github.io)
- [ASP.NET Core'da test denetleyicisi mantığı](/aspnet/core/mvc/controllers/testing)
- [`dotnet add reference`](../tools/dotnet-add-reference.md)
