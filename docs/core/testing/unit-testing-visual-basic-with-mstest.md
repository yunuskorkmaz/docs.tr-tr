---
title: Dotnet testi ve MSTest ile .NET Core Visual Basic test birimi
description: Adım adım örnek Visual Basic çözüm oluşturma etkileşimli bir deneyim .NET Core birim testi kavramları öğrenin mstest'i kullanarak.
author: billwagner
ms.author: wiwagn
ms.date: 09/01/2017
dev_langs:
- vb
ms.custom: seodec18
ms.openlocfilehash: 035daf2ec7fa487c171317fd67e7c39fea7fc951
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67397608"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-mstest"></a>Birim testi dotnet testi ve MSTest kullanarak Visual Basic .NET Core kitaplıkları

Bu öğretici örnek bir çözüm birim testi kavramlarını öğrenmek için adım adım oluşturmaya etkileşimli deneyim gösterir. Önceden oluşturulmuş bir çözümü kullanarak öğreticiyi uygulamak isterseniz [görüntülemek veya örnek kodu indirdikten](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-mstest/) başlamadan önce. Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="creating-the-source-project"></a>Kaynak proje oluşturma

Shell penceresini açın. Adlı bir dizin oluşturun *birim testi vb mstest* çözüm tutacak.
Bu yeni dizin içinde çalıştırma [ `dotnet new sln` ](../tools/dotnet-new.md) yeni bir çözüm oluşturmak için. Bu yöntem, sınıf kitaplığı hem birim test projesi yönetmenizi kolaylaştırır.
Çözüm dizini içinde bir *PrimeService* dizin. Aşağıdaki dizin ve dosya yapısı şimdiye kadarki vardır:

```
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
```

Olun *PrimeService* geçerli dizin ve çalışma [ `dotnet new classlib -lang VB` ](../tools/dotnet-new.md) kaynak proje oluşturmak için. Yeniden adlandırma *Class1.VB* için *PrimeService.VB*. Bir başarısız uygulamasını oluşturun `PrimeService` sınıfı:

```vb
Imports System

Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first")
        End Function
    End Class
End Namespace
```

Dizine dön değişiklik *birim-test-vb-kullanarak-mstest* dizin. Çalıştırma [ `dotnet sln add .\PrimeService\PrimeService.vbproj` ](../tools/dotnet-sln.md) sınıf kitaplığı projesi çözüme eklemek için.

## <a name="creating-the-test-project"></a>Test projesi oluşturma

Ardından, oluşturma *PrimeService.Tests* dizin. Ana hat aşağıdaki dizin yapısını gösterir:

```
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

Olun *PrimeService.Tests* dizini geçerli dizin ve kullanarak yeni bir proje oluşturma [ `dotnet new mstest -lang VB` ](../tools/dotnet-new.md). Bu komut, MSTest test kitaplık olarak kullanan bir test projesi oluşturur. Test Çalıştırıcısı'nda oluşturulan şablon yapılandırır *PrimeServiceTests.vbproj*:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

Test projesi oluşturma ve birim testlerini çalıştırmak için diğer paketleri gerektirir. `dotnet new` Önceki adımda, MSTest ve MSTest Çalıştırıcısı eklendi. Şimdi ekleyin `PrimeService` sınıf kitaplığı projesine başka bir bağımlılık olarak. Kullanım [ `dotnet add reference` ](../tools/dotnet-add-reference.md) komutu:

```
dotnet add reference ../PrimeService/PrimeService.vbproj
```

Dosyanın tamamını görebilirsiniz [örnekleri depomuzdan](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService.Tests.vbproj) GitHub üzerinde.

Aşağıdaki nihai çözüm Düzen vardır:

```
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.vbproj
```

Yürütme [ `dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj` ](../tools/dotnet-sln.md) içinde *birim testi vb mstest* dizin.

## <a name="creating-the-first-test"></a>İlk testi oluşturma

Bir yazma, test başarısız kolaylaştırır geçişi, sonra işlemi yineleyin. Kaldırma *UnitTest1.vb* gelen *PrimeService.Tests* dizin adlı yeni bir Visual Basic dosyası oluşturup *PrimeService_IsPrimeShould.VB*. Aşağıdaki kodu ekleyin:

```vb
Imports Microsoft.VisualStudio.TestTools.UnitTesting

Namespace PrimeService.Tests
    <TestClass>
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <TestMethod>
        Sub ReturnFalseGivenValueOf1()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.IsFalse(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

`<TestClass>` Öznitelik, testleri içeren bir sınıfı gösterir. `<TestMethod>` Özniteliği test Çalıştırıcısı tarafından yürütülen bir yöntemi gösterir. Gelen *birim testi vb mstest*, yürütme [ `dotnet test` ](../tools/dotnet-test.md) testler ve sınıf kitaplığı oluşturun ve ardından testleri çalıştırın. Programın giriş noktası, testlerinizi çalıştırmak için MSTest test Çalıştırıcısı içerir. `dotnet test` oluşturduğunuz birim test projesi kullanarak test Çalıştırıcısı'nı başlatır.

Test başarısız olur. Uygulama henüz oluşturmadınız. En basit kod yazarak bu testin geçmesini `PrimeService` çalışır sınıfı:

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first")
End Function
```

İçinde *birim testi vb mstest* çalışması dizini `dotnet test` yeniden. `dotnet test` Komut çalıştıran bir derleme için `PrimeService` proje ve ardından `PrimeService.Tests` proje. Her iki proje oluşturduktan sonra bu tek bir test çalıştırır. Bu geçirir.

## <a name="adding-more-features"></a>Daha fazla özellik ekleme

Bir test geçirmek yaptığınız, daha fazla yazmak için zaman var. Birkaç basit durumlardaysa asal sayıları için vardır: 0, -1. Bu gibi durumlarda, yeni testleriyle olarak ekleyebilirsiniz `<TestMethod>` özniteliği ancak hızla olur yorucu bir süreç. Benzer testleri paketi yazmanızı sağlayan diğer MSTest öznitelikleri vardır.  A `<DataTestMethod>` öznitelik aynı kod yürütün, ancak farklı giriş bağımsız değişkenleri olan testleri paketi temsil eder. Kullanabileceğiniz `<DataRow>` bu girişleri değerlerini belirtmek için özniteliği.

Yeni testler oluşturmak yerine, tek bir kuramsal oluşturmak için bu iki öznitelikler uygulanır. Teorik asal numarası en düşük olan değerlerden küçüktür iki test yöntemi verilmiştir:

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

Çalıştırma `dotnet test`, ve bunlardan ikisi başarısız test eder. Tüm testler başarılı hale getirmek için değiştirme `if` yöntemin başında yan tümcesi:

```vb
if candidate < 2
```

Ana Kitaplığı'nda daha fazla test, daha fazla Teoriler ve daha fazla kod ekleyerek yinelemek devam edin. Sahip olduğunuz [testlerinin tamamlanmış bir sürümünü](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb) ve [Kitaplığı'nın tam bir uygulamaya](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService/PrimeService.vb).

Küçük bir kitaplık ve bu kitaplık için birim testleri bir dizi oluşturdunuz. Böylece yeni paketler ekleme çözüm yapılandırılmış ve testleri normal iş akışı bir parçasıdır. Zaman ve çaba çözme hedeflerinden biri, uygulama üzerinde en yoğun.
