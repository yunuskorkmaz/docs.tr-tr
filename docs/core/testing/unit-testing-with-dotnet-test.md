---
title: Birim .NET çekirdek dotnet test ve xUnit kullanarak C# kodu testi
description: Adım adım örnek çözüm oluşturma etkileşimli bir deneyim aracılığıyla C# ve .NET Core birim testi kavramları hakkında bilgi dotnet test ve xUnit kullanarak.
author: ardalis
ms.author: wiwagn
ms.date: 11/29/2017
ms.openlocfilehash: 6f3b041bf690183f60b687699d878a4d5006be6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a>Birim testi C# .NET çekirdek dotnet test ve xUnit kullanma

Bu öğretici birim testi kavramlarını öğrenmek için adım adım örnek çözüm oluşturma etkileşimli bir deneyim gösterir. Önceden oluşturulmuş bir çözümü kullanarak öğreticiyi izleyin tercih ediyorsanız [görüntülemek veya karşıdan örnek kod](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/) başlamadan önce. Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="creating-the-source-project"></a>Kaynak projesi oluşturma

Kabuk penceresini açın. Adlı bir dizin oluşturun *birim testi-kullanma-dotnet-sınama* çözümü tutmak için.
Bu yeni dizin içinde çalıştırmak [ `dotnet new sln` ](../tools/dotnet-new.md) yeni bir çözüm oluşturmak için. Bir çözüm olan sınıf kitaplığı ve birim testi projesi yönetmeyi kolaylaştırır.
Çözüm dizini içinde oluşturmak bir *PrimeService* dizini. Dizin ve dosya yapısı bugüne kadarki şu şekilde olmalıdır:

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

Olun *PrimeService* geçerli dizin ve çalışma [ `dotnet new classlib` ](../tools/dotnet-new.md) kaynak projesi oluşturmak için. Yeniden Adlandır *Class1.cs* için *PrimeService.cs*. Teste dayalı geliştirme (TDD) kullanmak için önce başarısız olan uyarlamasını oluşturun `PrimeService` sınıfı:

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

Dizin geri değişiklik *birim testi-kullanma-dotnet-sınama* dizin.

Çalıştırma [dotnet sln](../tools/dotnet-sln.md) komutu sınıf kitaplığı proje çözüme eklemek için:

```
dotnet sln add .\PrimeService\PrimeService.csproj
```

## <a name="creating-the-test-project"></a>Test projesi oluşturma

Ardından, oluşturun *PrimeService.Tests* dizini. Aşağıdaki anahat dizin yapısını gösterir:

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

Olun *PrimeService.Tests* dizine geçerli ve kullanarak yeni bir proje oluşturun [ `dotnet new xunit` ](../tools/dotnet-new.md). Bu komut xUnit test kitaplığını kullanan bir test projesi oluşturur. Test Çalıştırıcısı'nda oluşturulan şablon yapılandırır *PrimeServiceTests.csproj* aşağıdaki kodu benzer dosya:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

Test projesi oluşturmak ve birim testleri çalıştırmak için diğer paketleri gerektirir. `dotnet new` Önceki adımda xUnit ve xUnit Çalıştırıcısı eklendi. Şimdi, ekleyin `PrimeService` sınıf kitaplığı proje için başka bir bağımlılık olarak. Kullanım [ `dotnet add reference` ](../tools/dotnet-add-reference.md) komutu:

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

Tüm dosyasında görebilirsiniz [örnekleri deposu](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj) github'da.

Aşağıdakiler, nihai çözüm düzeni gösterilir:

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

Oluşturduğunuz test projesinin çözüme eklemek için çalıştırın [dotnet sln](../tools/dotnet-sln.md) komutunu *birim testi-kullanma-dotnet-sınama* dizini:

```
dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj
```

## <a name="creating-the-first-test"></a>İlk testi oluşturma

TDD yaklaşım geçirmek kolaylaştırarak ve süreci tekrarlayarak yazma bir başarısız test için çağırır. Kaldırma *UnitTest1.cs* gelen *PrimeService.Tests* dizin ve adlı yeni bir C# dosya oluşturma *PrimeService_IsPrimeShould.cs*. Aşağıdaki kodu ekleyin:

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

`[Fact]` Özniteliği test Çalıştırıcısı tarafından çalıştırılan bir test yöntemi belirtir. Gelen *PrimeService.Tests* klasörü, yürütme [ `dotnet test` ](../tools/dotnet-test.md) testleri ve sınıf kitaplığı oluşturmak ve ardından testleri çalıştırın. XUnit test Çalıştırıcısı testleri çalıştırmak için program giriş noktası içerir. `dotnet test` oluşturduğunuz birim testi projesi kullanarak test Çalıştırıcısı başlatır.

Testiniz başarısız olur. Uygulama henüz oluşturmadınız. Bu test basit kod yazarken yapmasına `PrimeService` çalışır sınıfı. Varolan `IsPrime` aşağıdaki kod ile yöntemi uygulama:

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

İçinde *PrimeService.Tests* çalışması dizini `dotnet test` yeniden. `dotnet test` Komutu çalıştıran bir yapı `PrimeService` proje ve ardından `PrimeService.Tests` projesi. Her iki proje oluşturduktan sonra bu tek bir test çalıştırılır. Bunu geçirir.

## <a name="adding-more-features"></a>Daha fazla özellik ekleme

Bir test geçirmek yapmış olduğunuz, daha fazla yazma zamanı geldi. Diğer basit bazı durumlar asal sayılar için vardır: 0, -1. Bu gibi durumlarda yeni testleriyle olarak ekleyebilirsiniz `[Fact]` özniteliği, ancak, hızlı hale can sıkıcı. Benzer testleri dizisi yazmak için etkinleştirmek diğer xUnit öznitelikleri şunlardır:

- `[Theory]` aynı kod yürütmek ancak farklı giriş bağımsız değişkeni olan testleri bir paketi temsil eder.

- `[InlineData]` özniteliği bu giriş değerlerini belirtir.

Yeni testler oluşturmak yerine, bu iki özellik uygulamak `[Theory]` ve `[InlineData]`, tek bir teorik olarak oluşturmak için *PrimeService_IsPrimeShould.cs* dosya. Teorik asal numarası en düşük olduğu birden fazla değer ikiden az, testleri bir yöntemi aşağıdaki gibidir:

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

Çalıştırma `dotnet test` yeniden ve iki bu testler başarısız olması. Tüm testleri geçişini yapmak için değiştirme `if` başındaki yan tümcesi `IsPrime` yönteminde *PrimeService.cs* dosyası:

```csharp
if (candidate < 2)
```

Daha fazla testleri, daha fazla kuramlarý ve daha fazla kod ana kitaplıkta ekleyerek yinelemek devam edin. Sahip olduğunuz [testleri tamamlanmış sürümü](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) ve [kitaplığının tam uygulama](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).

### <a name="additional-resources"></a>Ek kaynaklar

[ASP.NET Core test denetleyicisi mantığı](/aspnet/core/mvc/controllers/testing)
