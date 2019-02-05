---
title: C# kod dotnet testi ve xUnit kullanarak .NET Core birim testi
description: Adım adım örnek bir çözüm oluşturmak bir etkileşimli deneyim C# ve .NET Core birim testi kavramları hakkında bilgi dotnet testi ve xUnit kullanma.
author: ardalis
ms.author: wiwagn
ms.date: 11/29/2017
ms.custom: seodec18
ms.openlocfilehash: 556da93d6237836dc32fc3f6715909593907ba74
ms.sourcegitcommit: facefcacd7ae2e5645e463bc841df213c505ffd4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/05/2019
ms.locfileid: "55738740"
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a>Birim testi C# .NET Core dotnet testi ve xUnit kullanma

Bu öğretici örnek bir çözüm birim testi kavramlarını öğrenmek için adım adım oluşturmaya etkileşimli deneyim gösterir. Önceden oluşturulmuş bir çözümü kullanarak öğreticiyi uygulamak isterseniz [görüntülemek veya örnek kodu indirdikten](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/) başlamadan önce. Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="creating-the-source-project"></a>Kaynak proje oluşturma

Shell penceresini açın. Adlı bir dizin oluşturun *birim testi-kullanarak-dotnet-test* çözüm tutacak.
Bu yeni dizin içinde çalıştırma [ `dotnet new sln` ](../tools/dotnet-new.md) yeni bir çözüm oluşturmak için. Bir çözüm olan sınıf kitaplığı hem birim test projesi yönetmenizi kolaylaştırır.
Çözüm dizini içinde bir *PrimeService* dizin. Şimdiye kadar dizin ve dosya yapısı şu şekilde olmalıdır:

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

Olun *PrimeService* geçerli dizin ve çalışma [ `dotnet new classlib` ](../tools/dotnet-new.md) kaynak proje oluşturmak için. Yeniden adlandırma *Class1.cs* için *PrimeService.cs*. Teste dayalı geliştirme (TDD) kullanmak için önce başarısız olan bir uygulamasını oluşturun `PrimeService` sınıfı:

```csharp
using System;

namespace Prime.Services
{
    public class PrimeService
    {
        public bool IsPrime(int candidate)
        {
            throw new NotImplementedException("Please create a test first");
        }
    }
}
```

Dizine dön değişiklik *birim testi-kullanarak-dotnet-test* dizin.

Çalıştırma [dotnet sln](../tools/dotnet-sln.md) sınıf kitaplığı projesi çözüme eklenecek komut:

```
dotnet sln add .\PrimeService\PrimeService.csproj
```

## <a name="creating-the-test-project"></a>Test projesi oluşturma

Ardından, oluşturma *PrimeService.Tests* dizin. Ana hat aşağıdaki dizin yapısını gösterir:

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

Olun *PrimeService.Tests* dizini geçerli dizin ve kullanarak yeni bir proje oluşturma [ `dotnet new xunit` ](../tools/dotnet-new.md). Bu komut, kullanan bir test projesi oluşturur. [xUnit](https://xunit.github.io/) test kitaplığı olarak. Test Çalıştırıcısı'nda oluşturulan şablon yapılandırır *PrimeServiceTests.csproj* aşağıdaki koda benzer dosya:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

Test projesi oluşturma ve birim testlerini çalıştırmak için diğer paketleri gerektirir. `dotnet new` Önceki adımda, xUnit ve xUnit Çalıştırıcısı eklendi. Şimdi ekleyin `PrimeService` sınıf kitaplığı projesine başka bir bağımlılık olarak. Kullanım [ `dotnet add reference` ](../tools/dotnet-add-reference.md) komutu:

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

Dosyanın tamamını görebilirsiniz [örnekleri depomuzdan](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj) GitHub üzerinde.

Aşağıda, nihai çözüm Düzen gösterilmiştir:

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

Test projesi çözüme eklemek için çalıştırın [dotnet sln](../tools/dotnet-sln.md) komutunu *birim testi-kullanarak-dotnet-test* dizini:

```
dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj
```

## <a name="creating-the-first-test"></a>İlk testi oluşturma

TDD yaklaşım geçer hale getirme ve süreci tekrarlayarak yazma bir başarısız test için çağırır. Kaldırma *UnitTest1.cs* gelen *PrimeService.Tests* dizin ve yeni bir C# adlı dosya *PrimeService_IsPrimeShould.cs*. Aşağıdaki kodu ekleyin:

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
        public void ReturnFalseGivenValueOf1()
        {
            var result = _primeService.IsPrime(1);

            Assert.False(result, "1 should not be prime");
        }
    }
}
```

`[Fact]` Test Çalıştırıcısı tarafından yürütülen bir test metodu özniteliği gösterir. Gelen *PrimeService.Tests* klasöründe yürütme [ `dotnet test` ](../tools/dotnet-test.md) testler ve sınıf kitaplığı oluşturun ve ardından testleri çalıştırın. XUnit test Çalıştırıcısı, testlerinizi çalıştırmak için programın giriş noktası içerir. `dotnet test` oluşturduğunuz birim test projesi kullanarak test Çalıştırıcısı'nı başlatır.

Test başarısız olur. Uygulama henüz oluşturmadınız. En basit kod yazarak geçirmek bu testin geçmesini `PrimeService` çalışır sınıfı. Varolan `IsPrime` yöntemi uygulamasını aşağıdaki kod ile:

```csharp
public bool IsPrime(int candidate)
{
    if (candidate == 1)
    {
        return false;
    }
    throw new NotImplementedException("Please create a test first");
}
```

İçinde *PrimeService.Tests* çalışması dizini `dotnet test` yeniden. `dotnet test` Komut çalıştıran bir derleme için `PrimeService` proje ve ardından `PrimeService.Tests` proje. Her iki proje oluşturduktan sonra bu tek bir test çalıştırır. Bu geçirir.

## <a name="adding-more-features"></a>Daha fazla özellik ekleme

Bir test geçirmek yaptığınız, daha fazla yazmak için zaman var. Birkaç basit durumlardaysa asal sayıları için vardır: 0, -1. Bu gibi durumlarda, yeni testleriyle olarak ekleyebilirsiniz `[Fact]` özniteliği ancak hızla olur yorucu bir süreç. Benzer testleri paketi yazmanızı sağlayan diğer xUnit öznitelikleri vardır:

- `[Theory]` aynı kod yürütün, ancak farklı giriş bağımsız değişkenleri olan testleri paketi temsil eder.

- `[InlineData]` özniteliği, bu girişleri için değerleri belirtir.

Yeni testler oluşturmak yerine, bu iki öznitelik geçerli `[Theory]` ve `[InlineData]`tek bir teorik olarak oluşturmak için *PrimeService_IsPrimeShould.cs* dosya. Teorik asal numarası en düşük olan değerlerden küçüktür iki test yöntemi verilmiştir:

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

Çalıştırma `dotnet test` yeniden ve iki bu testler başarısız olması. Tüm testleri geçer hale getirmek için değiştirme `if` başındaki yan tümcesi `IsPrime` yönteminde *PrimeService.cs* dosyası:

```csharp
if (candidate < 2)
```

Ana Kitaplığı'nda daha fazla test, daha fazla Teoriler ve daha fazla kod ekleyerek yinelemek devam edin. Sahip olduğunuz [testlerinin tamamlanmış bir sürümünü](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) ve [Kitaplığı'nın tam bir uygulamaya](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).

### <a name="additional-resources"></a>Ek kaynaklar

- [xUnit.net resmi sitesi](https://xunit.github.io)
- [ASP.NET Core test denetleyici mantığında](/aspnet/core/mvc/controllers/testing)
