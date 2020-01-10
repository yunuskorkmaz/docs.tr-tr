---
title: DotNet test C# ve xUnit kullanarak .NET Core 'da birim testi kodu
description: Ve .NET Core 'daki C# birim testi kavramlarını, DotNet test ve xUnit kullanarak örnek bir çözüm oluşturma adlı etkileşimli bir deneyim aracılığıyla öğrenin.
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: 226db54047747fbd065c64f5e4812094921c7f62
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714232"
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a>DotNet test C# ve xUnit kullanarak .NET Core 'da birim testi

Bu öğreticide, birim testi projesi ve kaynak kodu projesi içeren bir çözüm oluşturma gösterilmektedir. Önceden oluşturulmuş bir çözümü kullanarak öğreticiyi izlemek için [örnek kodu görüntüleyin veya indirin](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/). İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="create-the-solution"></a>Çözümü oluşturma

Bu bölümde, kaynak ve test projelerini içeren bir çözüm oluşturulur. Tamamlanmış çözüm aşağıdaki dizin yapısına sahiptir:

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

Aşağıdaki yönergeler, test çözümünü oluşturmak için gereken adımları sağlar. Test çözümünü tek bir adımda oluşturmaya yönelik yönergeler için bkz. [Test çözümü oluşturma komutları](#create-test-cmd) .

* Bir kabuk penceresi açın.
* Şu komutu çalıştırın:

  ```dotnetcli
  dotnet new sln -o unit-testing-using-dotnet-test
  ```

  [`dotnet new sln`](../tools/dotnet-new.md) komutu, *birim-test-using-DotNet-test* dizininde yeni bir çözüm oluşturur.
* Dizini *birim-test-using-DotNet-test* klasörü ile değiştirin.
* Şu komutu çalıştırın:

  ```dotnetcli
  dotnet new classlib -o PrimeService
  ```

   [`dotnet new classlib`](../tools/dotnet-new.md) komutu, *primeservice* klasöründe yeni bir sınıf kitaplığı projesi oluşturur. Yeni sınıf kitaplığı sınanacak kodu içerecektir.
* *Class1.cs* *olarak yeniden*adlandırın.
* *PrimeService.cs* içindeki kodu aşağıdaki kodla değiştirin:
  
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
  * Uygulanmadığını belirten bir ileti içeren bir <xref:System.NotImplementedException> oluşturur.
  * , Öğreticide daha sonra güncelleştirilir.

<!-- preceding code shows an english bias. Message makes no sense outside english -->

* *Birim-test-using-DotNet-test* dizini ' nde, sınıf kitaplığı projesini çözüme eklemek için aşağıdaki komutu çalıştırın:

  ```dotnetcli
  dotnet sln add ./PrimeService/PrimeService.csproj
  ```

* Aşağıdaki komutu çalıştırarak *Primeservice. Tests* projesini oluşturun:

  ```dotnetcli
  dotnet new xunit -o PrimeService.Tests
  ```

* Yukarıdaki komut:
  * *Primeservice* . *Tests projesindeki primeservice. Tests* projesini oluşturur. Test projesi, test kitaplığı olarak [xUnit](https://xunit.github.io/) kullanır.
  * , Aşağıdaki `<PackageReference />`öğelerini proje dosyasına ekleyerek Test Çalıştırıcısı 'nı yapılandırır:
    * "Microsoft. NET. test. SDK"
    * xUnit
    * "xUnit. Runner. VisualStudio"

* Aşağıdaki komutu çalıştırarak test projesini çözüm dosyasına ekleyin:

  ```dotnetcli
  dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
  ```

* `PrimeService` sınıf kitaplığını, *Primeservice. Tests* projesine bağımlılık olarak ekleyin:

  ```dotnetcli
  dotnet add ./PrimeService.Tests/PrimeService.Tests.csproj reference ./PrimeService/PrimeService.csproj  
  ```

<a name="create-test-cmd"></a>

### <a name="commands-to-create-the-solution"></a>Çözüm oluşturma komutları

Bu bölüm, önceki bölümdeki tüm komutları özetler. Önceki bölümdeki adımları tamamladığınız takdirde bu bölümü atlayın.

Aşağıdaki komutlar, bir Windows makinesinde test çözümünü oluşturur. MacOS ve UNIX için, bir dosyayı yeniden adlandırmak üzere `ren` komutunu `ren` işletim sistemi sürümüne güncelleştirin:

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

Önceki bölümde " *PrimeService.cs* içindeki kodu aşağıdaki kodla değiştirin" yönergelerini izleyin.

## <a name="create-a-test"></a>Test oluşturma

Test odaklı geliştirme (TDD) içinde popüler bir yaklaşım, hedef kodu uygulamadan önce bir test yazmaktır. Bu öğretici, TDD yaklaşımını kullanır. `IsPrime` yöntemi çağrılabilir, ancak uygulanmaz. `IsPrime` için test çağrısı başarısız olur. TDD ile başarısız olarak bilinen bir test yazılır. Hedef kodu test geçişini yapmak için güncellenir. Bu yaklaşımı tekrarlayarak, başarısız bir test yazarak ve ardından hedef kodu geçirilecek şekilde güncelleyebilirsiniz.

*Primeservice. Tests* projesini güncelleştirin:

* *Primeservice. Tests/UnitTest1. cs*öğesini silin.
* Bir *Primeservice. Tests/PrimeService_IsPrimeShould. cs* dosyası oluşturun.
* *PrimeService_IsPrimeShould. cs* içindeki kodu aşağıdaki kodla değiştirin:

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

`[Fact]` özniteliği, Test Çalıştırıcısı tarafından çalıştırılan bir test yöntemi bildirir. *Primeservice. Tests* klasöründen `dotnet test`çalıştırın. [DotNet test](../tools/dotnet-test.md) komutu her iki projeyi de oluşturur ve testleri çalıştırır. XUnit Test Çalıştırıcısı, testleri çalıştırmak için program giriş noktasını içerir. `dotnet test`, Test Çalıştırıcısı birimini birim testi projesi kullanarak başlatır.

`IsPrime` uygulanmadığı için test başarısız olur. TDD yaklaşımını kullanarak, bu testin başarılı olması için yalnızca yeterli kodu yazın. `IsPrime` aşağıdaki kodla güncelleştirin:

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

`dotnet test`'i çalıştırın. Test başarılı olur.

### <a name="add-more-tests"></a>Daha fazla test ekleyin

0 ve-1 için asal sayı testleri ekleyin. Önceki testi kopyalayabilir ve aşağıdaki kodu 0 ve-1 kullanacak şekilde değiştirebilirsiniz:

```csharp
var result = _primeService.IsPrime(1);

Assert.False(result, "1 should not be prime");
```

Yalnızca bir parametre değiştiğinde test kodu kopyalama, kod yineleme ve test blobunun sonuçlarını değiştirir. Aşağıdaki xUnit öznitelikleri benzer testlerin bir paketini yazmayı etkinleştirir:

- `[Theory]`, aynı kodu çalıştıran ancak farklı giriş bağımsız değişkenlerine sahip olan bir test paketini temsil eder.

- `[InlineData]` öznitelik, bu girişlerin değerlerini belirtir.

Yeni test oluşturmak yerine, tek bir teorisi oluşturmak için önceki xUnit özniteliklerini uygulayın. Aşağıdaki kodu değiştirin:

```csharp
[Fact]
public void IsPrime_InputIs1_ReturnFalse()
{
    var result = _primeService.IsPrime(1);

    Assert.False(result, "1 should not be prime");
}
```

aşağıdaki kodla:

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

Yukarıdaki kodda, `[Theory]` ve `[InlineData]` iki değerden küçük bir testi etkinleştirir. İki, en küçük asal sayıdır.

`dotnet test`çalıştırın, testlerin ikisi başarısız olur. Tüm testlerin geçişini yapmak için `IsPrime` yöntemini aşağıdaki kodla güncelleştirin:

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

TDD yaklaşımını izleyerek, daha fazla başarısız test ekleyin ve ardından hedef kodu güncelleştirin. [Testlerin tamamlanmış sürümüne](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) ve [kitaplığın tüm uygulamasına](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs)bakın.

Tamamlanan `IsPrime` yöntemi, test pridiklerine yönelik etkili bir algoritma değildir.

### <a name="additional-resources"></a>Ek kaynaklar

- [xUnit.net resmi site](https://xunit.github.io)
- [ASP.NET Core 'de test denetleyicisi mantığı](/aspnet/core/mvc/controllers/testing)
- [`dotnet add reference`](../tools/dotnet-add-reference.md)
