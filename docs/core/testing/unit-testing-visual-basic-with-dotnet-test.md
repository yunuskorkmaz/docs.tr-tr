---
title: DotNet test ve xUnit ile .NET Core 'da birim testi Visual Basic
description: .NET Core 'da, DotNet test ve xUnit kullanarak örnek Visual Basic çözüm adım adım oluşturma adlı etkileşimli bir deneyim aracılığıyla birim testi kavramlarını öğrenin.
author: billwagner
ms.author: wiwagn
ms.date: 05/18/2020
ms.openlocfilehash: d384bf08f0b6031a519a8430c876eafc05d03a2e
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656429"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-xunit"></a>DotNet test ve xUnit kullanarak .NET Core kitaplıkları Visual Basic birim testi

Bu öğreticide, birim testi projesi ve kitaplık projesi içeren bir çözüm oluşturma gösterilmektedir. Önceden oluşturulmuş bir çözümü kullanarak öğreticiyi izlemek için [örnek kodu görüntüleyin veya indirin](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/). İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#view-and-download-samples).

## <a name="create-the-solution"></a>Çözümü oluşturma

Bu bölümde, kaynak ve test projelerini içeren bir çözüm oluşturulur. Tamamlanmış çözüm aşağıdaki dizin yapısına sahiptir:

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        PrimeService.vb
        PrimeService.vbproj
    /PrimeService.Tests
        PrimeService_IsPrimeShould.vb
        PrimeServiceTests.vbproj
```

Aşağıdaki yönergeler, test çözümünü oluşturmak için gereken adımları sağlar. Test çözümünü tek bir adımda oluşturmaya yönelik yönergeler için bkz. [Test çözümü oluşturma komutları](#create-test-cmd) .

* Bir kabuk penceresi açın.
* Şu komutu çalıştırın:

  ```dotnetcli
  dotnet new sln -o unit-testing-using-dotnet-test
  ```

  Bu [`dotnet new sln`](../tools/dotnet-new.md) komut, *birim-test-using-DotNet-test* dizininde yeni bir çözüm oluşturur.
* Dizini *birim-test-using-DotNet-test* klasörü ile değiştirin.
* Şu komutu çalıştırın:

  ```dotnetcli
  dotnet new classlib -o PrimeService --lang VB
  ```

   [`dotnet new classlib`](../tools/dotnet-new.md)Komut, *Primeservice* klasöründe yeni bir sınıf kitaplığı projesi oluşturur. Yeni sınıf kitaplığı sınanacak kodu içerecektir.
* *Class1. vb* ' i *primeservice. vb*olarak yeniden adlandırın.
* *Primeservice. vb* içindeki kodu aşağıdaki kodla değiştirin:
  
  ```vb
  Imports System
  
  Namespace Prime.Services
      Public Class PrimeService
          Public Function IsPrime(candidate As Integer) As Boolean
              Throw New NotImplementedException("Not implemented.")
          End Function
      End Class
  End Namespace
  ```

* Yukarıdaki kod:
  * <xref:System.NotImplementedException>Uygulanmadığını belirten bir ileti içeren bir iletisi oluşturur.
  * , Öğreticide daha sonra güncelleştirilir.

<!-- preceding code shows an english bias. Message makes no sense outside english -->

* *Birim-test-using-DotNet-test* dizini ' nde, sınıf kitaplığı projesini çözüme eklemek için aşağıdaki komutu çalıştırın:

  ```dotnetcli
  dotnet sln add ./PrimeService/PrimeService.vbproj
  ```

* Aşağıdaki komutu çalıştırarak *Primeservice. Tests* projesini oluşturun:

  ```dotnetcli
  dotnet new xunit -o PrimeService.Tests
  ```

* Yukarıdaki komut:
  * *Primeservice* . *Tests projesindeki primeservice. Tests* projesini oluşturur. Test projesi, test kitaplığı olarak [xUnit](https://xunit.net/) kullanır.
  * , Aşağıdaki öğeleri proje dosyasına ekleyerek Test Çalıştırıcısı 'nı yapılandırır `<PackageReference />` :
    * "Microsoft. NET. test. SDK"
    * xUnit
    * "xUnit. Runner. VisualStudio"

* Aşağıdaki komutu çalıştırarak test projesini çözüm dosyasına ekleyin:

  ```dotnetcli
  dotnet sln add ./PrimeService.Tests/PrimeService.Tests.vbproj
  ```

* `PrimeService`Sınıf kitaplığını, *Primeservice. Tests* projesine bağımlılık olarak ekleyin:

  ```dotnetcli
  dotnet add ./PrimeService.Tests/PrimeService.Tests.vbproj reference ./PrimeService/PrimeService.vbproj  
  ```

<a name="create-test-cmd"></a>

### <a name="commands-to-create-the-solution"></a>Çözüm oluşturma komutları

Bu bölüm, önceki bölümdeki tüm komutları özetler. Önceki bölümdeki adımları tamamladığınız takdirde bu bölümü atlayın.

Aşağıdaki komutlar, bir Windows makinesinde test çözümünü oluşturur. MacOS ve UNIX için, `ren` komutunu `ren` bir dosyayı yeniden adlandırmak üzere işletim sistemi sürümüne güncelleştirin:

```dotnetcli
dotnet new sln -o unit-testing-using-dotnet-test
cd unit-testing-using-dotnet-test
dotnet new classlib -o PrimeService
ren .\PrimeService\Class1.vb PrimeService.vb
dotnet sln add ./PrimeService/PrimeService.vbproj
dotnet new xunit -o PrimeService.Tests
dotnet add ./PrimeService.Tests/PrimeService.Tests.vbproj reference ./PrimeService/PrimeService.vbproj
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.vbproj
```

Önceki bölümde " *Primeservice. vb* Içindeki kodu değiştirin" konusundaki yönergeleri izleyin.

## <a name="create-a-test"></a>Test oluşturma

Test odaklı geliştirme (TDD) içinde popüler bir yaklaşım, hedef kodu uygulamadan önce bir test yazmaktır. Bu öğretici, TDD yaklaşımını kullanır. `IsPrime`Yöntem çağrılabilir, ancak uygulanmaz. Test çağrısı `IsPrime` başarısız. TDD ile başarısız olarak bilinen bir test yazılır. Hedef kodu test geçişini yapmak için güncellenir. Bu yaklaşımı tekrarlayarak, başarısız bir test yazarak ve ardından hedef kodu geçirilecek şekilde güncelleyebilirsiniz.

*Primeservice. Tests* projesini güncelleştirin:

* *Primeservice. Tests/UnitTest1. vb*öğesini silin.
* Bir *Primeservice. Tests/PrimeService_IsPrimeShould. vb*  dosyası oluşturun.
* *PrimeService_IsPrimeShould. vb* içindeki kodu aşağıdaki kodla değiştirin:

```vb
Imports Xunit

Namespace PrimeService.Tests
    Public Class PrimeService_IsPrimeShould
        Private ReadOnly _primeService As Prime.Services.PrimeService

        Public Sub New()
            _primeService = New Prime.Services.PrimeService()
        End Sub


        <Fact>
        Sub IsPrime_InputIs1_ReturnFalse()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

`[Fact]`Özniteliği, Test Çalıştırıcısı tarafından çalıştırılan bir test yöntemi bildirir. *Primeservice. Tests* klasöründen çalıştırın `dotnet test` . [DotNet test](../tools/dotnet-test.md) komutu her iki projeyi de oluşturur ve testleri çalıştırır. XUnit Test Çalıştırıcısı, testleri çalıştırmak için program giriş noktasını içerir. `dotnet test` birim test projesini kullanarak Test Çalıştırıcısı başlatır.

Test başarısız oldu, çünkü `IsPrime` uygulanmadı. TDD yaklaşımını kullanarak, bu testin başarılı olması için yalnızca yeterli kodu yazın. `IsPrime`Aşağıdaki kodla güncelleştirin:

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Not implemented.")
End Function
```

`dotnet test` öğesini çalıştırın. Test geçirilir.

### <a name="add-more-tests"></a>Daha fazla test ekleyin

0 ve-1 için asal sayı testleri ekleyin. Önceki testi kopyalayabilir ve aşağıdaki kodu 0 ve-1 kullanacak şekilde değiştirebilirsiniz:

```vb
Dim result As Boolean = _primeService.IsPrime(1)

Assert.False(result, "1 should not be prime")
```

Yalnızca bir parametre değiştiğinde test kodu kopyalama, kod yineleme ve test blobunun sonuçlarını değiştirir. Aşağıdaki xUnit öznitelikleri benzer testlerin bir paketini yazmayı etkinleştirir:

- `[Theory]` aynı kodu çalıştıran, ancak farklı giriş bağımsız değişkenlerine sahip olan testlerin paketini temsil eder.
- `[InlineData]` öznitelik, bu girişlerin değerlerini belirtir.

Yeni test oluşturmak yerine, tek bir teorisi oluşturmak için önceki xUnit özniteliklerini uygulayın. Aşağıdaki kodu değiştirin:

```vb
<Fact>
Sub IsPrime_InputIs1_ReturnFalse()
    Dim result As Boolean = _primeService.IsPrime(1)

    Assert.False(result, "1 should not be prime")
End Sub
```

aşağıdaki kodla:

```vb
<Theory>
<InlineData(-1)>
<InlineData(0)>
<InlineData(1)>
Sub IsPrime_ValuesLessThan2_ReturnFalse(ByVal value As Integer)
    Dim result As Boolean = _primeService.IsPrime(value)

    Assert.False(result, $"{value} should not be prime")
End Sub
```

Önceki kodda, `[Theory]` `[InlineData]` ikiden küçük olan birkaç değeri test etmeyi etkinleştirin. İki, en küçük asal sayıdır.

Çalıştırılan `dotnet test` testlerin ikisi de başarısız olur. Tüm testlerin geçişini yapmak için `IsPrime` yöntemini aşağıdaki kodla güncelleştirin:

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate < 2 Then
        Return False
    End If
    Throw New NotImplementedException("Not fully implemented.")
End Function
```

TDD yaklaşımını izleyerek, daha fazla başarısız test ekleyin ve ardından hedef kodu güncelleştirin. [Testlerin tamamlanmış sürümüne](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) ve [kitaplığın tüm uygulamasına](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService/PrimeService.vb)bakın.

Tamamlanan `IsPrime` Yöntem, test açısından etkili bir algoritma değildir.

### <a name="additional-resources"></a>Ek kaynaklar

- [xUnit.net resmi site](https://xunit.net/)
- [ASP.NET Core 'de test denetleyicisi mantığı](/aspnet/core/mvc/controllers/testing)
- [`dotnet add reference`](../tools/dotnet-add-reference.md)
