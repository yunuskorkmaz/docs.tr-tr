---
title: Dotnet testi ve xUnit ile .NET Core Visual Basic test birimi
description: Adım adım örnek Visual Basic çözüm oluşturma etkileşimli bir deneyim .NET Core birim testi kavramları öğrenin dotnet testi ve xUnit kullanma.
author: billwagner
ms.author: wiwagn
ms.date: 09/01/2017
dev_langs:
- vb
ms.custom: seodec18
ms.openlocfilehash: 193746e8efda5d7bc9e086bb0abf934cfeb1741a
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56748602"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-xunit"></a>Birim testi dotnet testi ve xUnit kullanarak Visual Basic .NET Core kitaplıkları

Bu öğretici örnek bir çözüm birim testi kavramlarını öğrenmek için adım adım oluşturmaya etkileşimli deneyim gösterir. Önceden oluşturulmuş bir çözümü kullanarak öğreticiyi uygulamak isterseniz [görüntülemek veya örnek kodu indirdikten](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-dotnet-test) başlamadan önce. Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="creating-the-source-project"></a>Kaynak proje oluşturma

Shell penceresini açın. Adlı bir dizin oluşturun *unit-testing-vb-using-dotnet-test* çözüm tutacak.
Bu yeni dizin içinde çalıştırma [ `dotnet new sln` ](../tools/dotnet-new.md) yeni bir çözüm oluşturmak için. Bu yöntem, sınıf kitaplığı hem birim test projesi yönetmenizi kolaylaştırır.
Çözüm dizini içinde bir *PrimeService* dizin. Aşağıdaki dizin ve dosya yapısı şimdiye kadarki vardır:

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

Olun *PrimeService* geçerli dizin ve çalışma [ `dotnet new classlib -lang VB` ](../tools/dotnet-new.md) kaynak proje oluşturmak için. Yeniden adlandırma *Class1.VB* için *PrimeService.VB*. Bir başarısız uygulamasını oluşturun `PrimeService` sınıfı:

```vb
Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first")
        End Function
    End Class
End Namespace
```

Dizine dön değişiklik *unit-testing-vb-using-dotnet-test* dizin. Çalıştırma [ `dotnet sln add .\PrimeService\PrimeService.vbproj` ](../tools/dotnet-sln.md) sınıf kitaplığı projesi çözüme eklemek için.

## <a name="creating-the-test-project"></a>Test projesi oluşturma

Ardından, oluşturma *PrimeService.Tests* dizin. Ana hat aşağıdaki dizin yapısını gösterir:

```
/unit-testing-vb-using-dotnet-test
    unit-testing-vb-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

Olun *PrimeService.Tests* dizini geçerli dizin ve kullanarak yeni bir proje oluşturma [ `dotnet new xunit -lang VB` ](../tools/dotnet-new.md). Bu komut, xUnit test kitaplık olarak kullanan bir test projesi oluşturur. Test Çalıştırıcısı'nda oluşturulan şablon yapılandırır *PrimeServiceTests.vbproj*:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

Test projesi oluşturma ve birim testlerini çalıştırmak için diğer paketleri gerektirir. `dotnet new` Önceki adımda, xUnit ve xUnit Çalıştırıcısı eklendi. Şimdi ekleyin `PrimeService` sınıf kitaplığı projesine başka bir bağımlılık olarak. Kullanım [ `dotnet add reference` ](../tools/dotnet-add-reference.md) komutu:

```
dotnet add reference ../PrimeService/PrimeService.vbproj
```

Dosyanın tamamını görebilirsiniz [örnekleri depomuzdan](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService.Tests.vbproj) GitHub üzerinde.

Aşağıdaki son klasör düzeni vardır:

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.vbproj
```

Yürütme [ `dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj` ](../tools/dotnet-sln.md) içinde *unit-testing-vb-using-dotnet-test* dizin. 

## <a name="creating-the-first-test"></a>İlk testi oluşturma

Bir yazma, test başarısız kolaylaştırır geçişi, sonra işlemi yineleyin. Kaldırma *UnitTest1.vb* gelen *PrimeService.Tests* dizin adlı yeni bir Visual Basic dosyası oluşturup *PrimeService_IsPrimeShould.VB*. Aşağıdaki kodu ekleyin:

```vb
Imports Xunit

Namespace PrimeService.Tests
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <Fact>
        Sub ReturnFalseGivenValueOf1()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

`<Fact>` Test Çalıştırıcısı tarafından yürütülen bir test metodu özniteliği gösterir. Gelen *birim testi-kullanarak-dotnet-test*, yürütme [ `dotnet test` ](../tools/dotnet-test.md) testler ve sınıf kitaplığı oluşturun ve ardından testleri çalıştırın. XUnit test Çalıştırıcısı, testlerinizi çalıştırmak için programın giriş noktası içerir. `dotnet test` oluşturduğunuz birim test projesi kullanarak test Çalıştırıcısı'nı başlatır.

Test başarısız olur. Uygulama henüz oluşturmadınız. En basit kod yazarak bu testin geçmesini `PrimeService` çalışır sınıfı:

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first")
End Function
```

İçinde *unit-testing-vb-using-dotnet-test* çalışması dizini `dotnet test` yeniden. `dotnet test` Komut çalıştıran bir derleme için `PrimeService` proje ve ardından `PrimeService.Tests` proje. Her iki proje oluşturduktan sonra bu tek bir test çalıştırır. Bu geçirir.

## <a name="adding-more-features"></a>Daha fazla özellik ekleme

Bir test geçirmek yaptığınız, daha fazla yazmak için zaman var. Birkaç basit durumlardaysa asal sayıları için vardır: 0, -1. Bu gibi durumlarda, yeni testleriyle olarak ekleyebilirsiniz `<Fact>` özniteliği ancak hızla olur yorucu bir süreç. Benzer testleri paketi yazmanızı sağlayan diğer xUnit öznitelikleri vardır.  A `<Theory>` öznitelik aynı kod yürütün, ancak farklı giriş bağımsız değişkenleri olan testleri paketi temsil eder. Kullanabileceğiniz `<InlineData>` bu girişleri değerlerini belirtmek için özniteliği.

Yeni testler oluşturmak yerine, tek bir kuramsal oluşturmak için bu iki öznitelikler uygulanır. Teorik asal numarası en düşük olan değerlerden küçüktür iki test yöntemi verilmiştir:

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

Çalıştırma `dotnet test`, ve bunlardan ikisi başarısız test eder. Tüm testler başarılı hale getirmek için değiştirme `if` yöntemin başında yan tümcesi:

```vb
if candidate < 2
```

Ana Kitaplığı'nda daha fazla test, daha fazla Teoriler ve daha fazla kod ekleyerek yinelemek devam edin. Sahip olduğunuz [testlerinin tamamlanmış bir sürümünü](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) ve [Kitaplığı'nın tam bir uygulamaya](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService/PrimeService.vb).

Küçük bir kitaplık ve bu kitaplık için birim testleri bir dizi oluşturdunuz. Böylece yeni paketler ekleme çözüm yapılandırılmış ve testleri normal iş akışı bir parçasıdır. Zaman ve çaba çözme hedeflerinden biri, uygulama üzerinde en yoğun.
