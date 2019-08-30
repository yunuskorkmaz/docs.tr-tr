---
title: DotNet test C# ve xUnit kullanarak .NET Core 'da birim testi kodu
description: Ve .NET Core 'daki C# birim testi kavramlarını, DotNet test ve xUnit kullanarak örnek bir çözüm oluşturma adlı etkileşimli bir deneyim aracılığıyla öğrenin.
author: ardalis
ms.author: wiwagn
ms.date: 11/29/2017
ms.custom: seodec18
ms.openlocfilehash: 1013e14690bb3cfc17e339bfd5045e6d10bc3d3e
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168146"
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a>DotNet test C# ve xUnit kullanarak .NET Core 'da birim testi

Bu öğreticide, birim testi kavramlarını öğrenmek için bir örnek çözüm oluşturma adım adım yönergeler sunarak etkileşimli bir deneyim sağlanır. Önceden oluşturulmuş bir çözüm kullanarak öğreticiyi izlemeyi tercih ediyorsanız, başlamadan önce [örnek kodu görüntüleyin veya indirin](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/) . İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="creating-the-source-project"></a>Kaynak proje oluşturma

Bir kabuk penceresi açın. Çözümü tutmak için *birim-test-using-DotNet-test* adlı bir dizin oluşturun.
Yeni bir çözüm oluşturmak için bu [`dotnet new sln`](../tools/dotnet-new.md) yeni dizinin içinde öğesini çalıştırın. Bir çözüme sahip olmak, hem sınıf kitaplığını hem de birim testi projesini yönetmeyi kolaylaştırır.
Çözüm dizini içinde bir *Primeservice* dizini oluşturun. Bu nedenle, dizin ve dosya yapısı şu şekilde olmalıdır:

```console
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

Kaynak projeyi oluşturmak için *primeservice* 'i geçerli [`dotnet new classlib`](../tools/dotnet-new.md) Dizin yapın ve çalıştırın. *Class1.cs* olarak yenidenadlandırın. Önce `PrimeService` sınıfın başarısız bir uygulamasını oluşturursunuz:

```csharp
using System;

namespace Prime.Services
{
    public class PrimeService
    {
        public bool IsPrime(int candidate)
        {
            throw new NotImplementedException("Please create a test first.");
        }
    }
}
```

Dizini *birim-test-using-DotNet-test* dizinine geri çevirin.

Sınıf Kitaplığı projesini çözüme eklemek için [DotNet sln](../tools/dotnet-sln.md) komutunu çalıştırın:

```console
dotnet sln add ./PrimeService/PrimeService.csproj
```

## <a name="creating-the-test-project"></a>Test projesi oluşturma

Ardından, *Primeservice. Tests* dizinini oluşturun. Aşağıdaki ana hat dizin yapısını gösterir:

```console
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

*Primeservice. test* dizinini geçerli dizini yapın ve kullanarak [`dotnet new xunit`](../tools/dotnet-new.md)yeni bir proje oluşturun. Bu komut, test kitaplığı olarak [xUnit](https://xunit.github.io/) kullanan bir test projesi oluşturur. Oluşturulan şablon, *Primeservicetests. csproj* dosyasında aşağıdaki koda benzer Test Çalıştırıcısı 'nı yapılandırır:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

Test projesi, birim testlerini oluşturmak ve çalıştırmak için diğer paketlerin kullanılmasını gerektirir. `dotnet new`önceki adımda xUnit ve xUnit Çalıştırıcısı eklenmiştir. Şimdi, `PrimeService` sınıf kitaplığını projeye başka bir bağımlılık olarak ekleyin. [`dotnet add reference`](../tools/dotnet-add-reference.md) Şu komutu kullanın:

```console
dotnet add reference ../PrimeService/PrimeService.csproj
```

GitHub 'daki [örnekler deposunda](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj) dosyanın tamamını görebilirsiniz.

Son çözüm düzeni aşağıda gösterilmiştir:

```console
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

Çözüme test projesi eklemek için, *birim-test-using-DotNet-test* dizininde [DotNet sln](../tools/dotnet-sln.md) komutunu çalıştırın:

```console
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
```

## <a name="creating-the-first-test"></a>İlk test oluşturma

Başarısız bir test yazdığınızda, geçişi yapıp işlemi tekrarlayabilirsiniz. *UnitTest1.cs* öğesini *primeservice. Tests* dizininden kaldırın ve *PrimeService_IsPrimeShould. cs*adlı C# yeni bir dosya oluşturun. Aşağıdaki kodu ekleyin:

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

`[Fact]` Özniteliği, Test Çalıştırıcısı tarafından çalıştırılan bir test yöntemini gösterir. *Primeservice. Tests* klasöründen, testleri ve sınıf [`dotnet test`](../tools/dotnet-test.md) kitaplığını oluşturmak için yürütün ve ardından testleri çalıştırın. XUnit Test Çalıştırıcısı, testlerinizi çalıştırmak için program giriş noktasını içerir. `dotnet test`oluşturduğunuz birim test projesini kullanarak Test Çalıştırıcısı başlatır.

Testiniz başarısız oluyor. Uygulamayı henüz oluşturmadınız. Bu test geçişini, en basit kodu `PrimeService` çalıştıran sınıfa yazarak yapın. Mevcut `IsPrime` Yöntem uygulamasını şu kodla değiştirin:

```csharp
public bool IsPrime(int candidate)
{
    if (candidate == 1)
    {
        return false;
    }
    throw new NotImplementedException("Please create a test first.");
}
```

*Primeservice. Tests* dizininde yeniden çalıştırın `dotnet test` . Komutu, `PrimeService` proje için bir yapı ve ardından projeiçinçalışır.`PrimeService.Tests` `dotnet test` Her iki proje de oluşturulduktan sonra bu tek testi çalıştırır. Geçirir.

## <a name="adding-more-features"></a>Daha fazla özellik ekleme

Artık bir test geçişi yapmış olduğunuza göre daha fazla yazma zamanı vardır. Asal sayıların diğer birkaç basit durumu vardır: 0,-1. Bu servis taleplerini `[Fact]` özniteliğiyle yeni testler olarak ekleyebilirsiniz, ancak bu, hızlı bir şekilde sıkıcı hale gelir. Benzer testlerin bir paketini yazmanızı sağlayan başka xUnit öznitelikleri vardır:

- `[Theory]`aynı kodu çalıştıran, ancak farklı giriş bağımsız değişkenlerine sahip olan testlerin paketini temsil eder.

- `[InlineData]`öznitelik, bu girişlerin değerlerini belirtir.

Yeni testler oluşturmak yerine, bu iki özniteliği `[Theory]` uygulayın ve `[InlineData]`PrimeService_IsPrimeShould. cs dosyasında tek bir teorisi oluşturun. Teorisi, en düşük asal sayı olan iki değerden küçük birkaç değeri sınayan bir yöntemdir:

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

Yeniden `dotnet test` çalıştırın, bu testlerin ikisi de başarısız olmalıdır. Tüm testlerin geçişini yapmak için `if` *PrimeService.cs* dosyasındaki `IsPrime` yönteminin başındaki yan tümceyi değiştirin:

```csharp
if (candidate < 2)
```

Ana kitaplıkta daha fazla test, daha fazla yer ve daha fazla kod ekleyerek yinelemek için devam edin. [Testlerin tamamlanmış sürümüne](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) ve [kitaplığın tüm uygulamasına](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs)sahipsiniz.

### <a name="additional-resources"></a>Ek kaynaklar

- [xUnit.net resmi site](https://xunit.github.io)
- [ASP.NET Core 'de test denetleyicisi mantığı](/aspnet/core/mvc/controllers/testing)
