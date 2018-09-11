---
title: Birim testi NUnit ve .NET Core ile C#
description: Adım adım örnek bir çözüm oluşturmak bir etkileşimli deneyim C# ve .NET Core birim testi kavramları hakkında bilgi dotnet testi ve NUnit kullanarak.
author: rprouse
ms.date: 08/31/2018
ms.openlocfilehash: 253e07c16740a39566cf37ee5742a32342c78c49
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44276792"
---
# <a name="unit-testing-c-with-nunit-and-net-core"></a>Birim testi NUnit ve .NET Core ile C#

Bu öğretici örnek bir çözüm birim testi kavramlarını öğrenmek için adım adım oluşturmaya etkileşimli deneyim gösterir. Önceden oluşturulmuş bir çözümü kullanarak öğreticiyi uygulamak isterseniz [görüntülemek veya örnek kodu indirdikten](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/) başlamadan önce. Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="prerequisites"></a>Önkoşullar

- [.NET core SDK 2.1 (v. 2.1.400)](https://www.microsoft.com/net/download) veya sonraki sürümler.
- Bir metin düzenleyicisi veya tercih ettiğiniz Kod Düzenleyicisi.

## <a name="creating-the-source-project"></a>Kaynak proje oluşturma

Shell penceresini açın. Adlı bir dizin oluşturun *birim-test-kullanarak-nunit* çözüm tutacak. Bu yeni dizin içinde sınıf kitaplığı ve test projesi için yeni bir çözüm dosyası oluşturmak için aşağıdaki komutu çalıştırın:

```console
dotnet new sln
```
 
Ardından, oluşturun bir *PrimeService* dizin. Aşağıdaki ana hat dizin ve dosya yapısı şu ana kadar gösterilmektedir:

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
```

Olun *PrimeService* aşağıdaki komut kaynak projesi oluşturmak için geçerli dizin ve çalıştırma:

```console
dotnet new classlib
```

Yeniden adlandırma *Class1.cs* için *PrimeService.cs*. Teste dayalı geliştirme (TDD) kullanmak için bir başarısız uygulaması oluşturun. `PrimeService` sınıfı:

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

Dizine dön değişiklik *birim-test-kullanarak-nunit* dizin. Sınıf kitaplığı projesi çözüme eklemek için aşağıdaki komutu çalıştırın:

```console
dotnet sln add PrimeService/PrimeService.csproj
```

## <a name="creating-the-test-project"></a>Test projesi oluşturma

Ardından, oluşturma *PrimeService.Tests* dizin. Ana hat aşağıdaki dizin yapısını gösterir:

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

Olun *PrimeService.Tests* dizini geçerli dizin ve aşağıdaki komutu kullanarak yeni bir proje oluşturun:

```console
dotnet new nunit
```

[Yeni dotnet](../tools/dotnet-new.md) komut NUnit test kitaplık olarak kullanan bir test projesi oluşturur. Test Çalıştırıcısı'nda oluşturulan şablon yapılandırır *PrimeService.Tests.csproj* dosyası:

[!code-xml[Packages](~/samples/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj#Packages)]

Test projesi oluşturma ve birim testlerini çalıştırmak için diğer paketleri gerektirir. `dotnet new` Önceki adımda, Microsoft test SDK'sı, NUnit test çerçevesi ve NUnit test bağdaştırıcısı eklendi. Şimdi ekleyin `PrimeService` sınıf kitaplığı projesine başka bir bağımlılık olarak. Kullanım [ `dotnet add reference` ](../tools/dotnet-add-reference.md) komutu:

```console
dotnet add reference ../PrimeService/PrimeService.csproj
```

Dosyanın tamamını görebilirsiniz [örnekleri depomuzdan](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj) GitHub üzerinde.

Aşağıdaki ana hat nihai çözüm düzeni gösterilir:

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeService.Tests.csproj
```

Aşağıdaki komutu yürütün *birim testi-kullanarak-dotnet-test* dizini:

```console
dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj
```

## <a name="creating-the-first-test"></a>İlk testi oluşturma

TDD yaklaşım geçer hale getirme ve süreci tekrarlayarak yazma bir başarısız test için çağırır. İçinde *PrimeService.Tests* dizini yeniden adlandırma *UnitTest1.cs* dosyasını *PrimeService_IsPrimeShould.cs* ve tüm içeriğini aşağıdaki kodla değiştirin:

```csharp
using NUnit.Framework;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    [TestFixture]
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;

        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [Test]
        public void ReturnFalseGivenValueOf1()
        {
            var result = _primeService.IsPrime(1);

            Assert.IsFalse(result, "1 should not be prime");
        }
    }
}
```

`[TestFixture]` Özniteliği birim testleri içeren bir sınıfı gösterir. `[Test]` Öznitelik, bir yöntemi olan bir test yöntemi gösterir.

Bu dosyayı kaydedin ve yürütme [ `dotnet test` ](../tools/dotnet-test.md) testler ve sınıf kitaplığı oluşturun ve ardından testleri çalıştırın. NUnit test Çalıştırıcısı, testlerinizi çalıştırmak için programın giriş noktası içerir. `dotnet test` oluşturduğunuz birim test projesi kullanarak test Çalıştırıcısı'nı başlatır.

Test başarısız olur. Uygulama henüz oluşturmadınız. En basit kod yazarak geçirmek bu testin geçmesini `PrimeService` çalışır sınıfı:

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

İçinde *birim-test-kullanarak-nunit* çalışması dizini `dotnet test` yeniden. `dotnet test` Komut çalıştıran bir derleme için `PrimeService` proje ve ardından `PrimeService.Tests` proje. Her iki proje oluşturduktan sonra bu tek bir test çalıştırır. Bu geçirir.

## <a name="adding-more-features"></a>Daha fazla özellik ekleme

Bir test geçirmek yaptığınız, daha fazla yazmak için zaman var. Diğer basit bazı durumlar için asal sayıları: 0, -1. Yeni testleriyle ekleyebilirsiniz `[Test]` özniteliği ancak hızla olur yorucu bir süreç. Benzer testleri paketi yazmanızı sağlayan diğer NUnit öznitelikleri vardır.  A `[TestCase]` özniteliği, aynı kod yürütün, ancak farklı giriş bağımsız değişkenleri olan testleri paketi oluşturmak için kullanılır. Kullanabileceğiniz `[TestCase]` bu girişleri değerlerini belirtmek için özniteliği.

Yeni testler oluşturmak yerine, bu öznitelik, bir tek veri tabanlı test oluşturmak için geçerlidir. Test odaklı veri asal numarası en düşük olan değerlerden küçüktür iki test yöntemi verilmiştir:

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

Çalıştırma `dotnet test`, ve bunlardan ikisi başarısız test eder. Tüm testleri geçer hale getirmek için değiştirme `if` başındaki yan tümcesi `Main` yönteminde *PrimeService.cs* dosyası:

```csharp
if (candidate < 2)
```

Ana Kitaplığı'nda daha fazla test, daha fazla Teoriler ve daha fazla kod ekleyerek yinelemek devam edin. Sahip olduğunuz [testlerinin tamamlanmış bir sürümünü](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs) ve [Kitaplığı'nın tam bir uygulamaya](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs).

Küçük bir kitaplık ve bu kitaplık için birim testleri bir dizi oluşturdunuz. Böylece yeni paketler ekleme çözüm yapılandırılmış ve testleri normal iş akışı bir parçasıdır. Zaman ve çaba çözme hedeflerinden biri, uygulama üzerinde en yoğun.
