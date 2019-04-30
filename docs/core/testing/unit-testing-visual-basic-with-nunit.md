---
title: Visual Basic .NET Core dotnet testi ve NUnit ile birim testi
description: Adım adım örnek Visual Basic çözüm oluşturma etkileşimli bir deneyim .NET Core birim testi kavramları öğrenin NUnit kullanarak.
author: rprouse
ms.date: 10/04/2018
dev_langs:
- vb
ms.custom: seodec18
ms.openlocfilehash: 2c8a6b86dd66b13faa242f94cf11cb940986fbd0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665565"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-nunit"></a>Birim testi dotnet testi ve NUnit kullanarak Visual Basic .NET Core kitaplıkları

Bu öğretici örnek bir çözüm birim testi kavramlarını öğrenmek için adım adım oluşturmaya etkileşimli deneyim gösterir. Önceden oluşturulmuş bir çözümü kullanarak öğreticiyi uygulamak isterseniz [görüntülemek veya örnek kodu indirdikten](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-nunit/) başlamadan önce. Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="prerequisites"></a>Önkoşullar

- [.NET core 2.1 SDK](https://www.microsoft.com/net/download) veya sonraki sürümler.
- Bir metin düzenleyicisi veya tercih ettiğiniz Kod Düzenleyicisi.

## <a name="creating-the-source-project"></a>Kaynak proje oluşturma

Shell penceresini açın. Adlı bir dizin oluşturun *birim testi vb nunit* çözüm tutacak. Bu yeni dizin içinde sınıf kitaplığı ve test projesi için yeni bir çözüm dosyası oluşturmak için aşağıdaki komutu çalıştırın:

```console
dotnet new sln
```

Ardından, oluşturun bir *PrimeService* dizin. Aşağıdaki ana hat kadar dosya yapısı gösterilmektedir:

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
```

Olun *PrimeService* aşağıdaki komut kaynak projesi oluşturmak için geçerli dizin ve çalıştırma:

```console
dotnet new classlib -lang VB
```

Yeniden adlandırma *Class1.VB* için *PrimeService.VB*. Bir başarısız uygulamasını oluşturun `PrimeService` sınıfı:

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

Dizine dön değişiklik *birim-test-vb-kullanarak-stest* dizin. Sınıf kitaplığı projesi çözüme eklemek için aşağıdaki komutu çalıştırın:

```console
dotnet sln add .\PrimeService\PrimeService.vbproj
```

## <a name="creating-the-test-project"></a>Test projesi oluşturma

Ardından, oluşturma *PrimeService.Tests* dizin. Ana hat aşağıdaki dizin yapısını gösterir:

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

Olun *PrimeService.Tests* dizini geçerli dizin ve aşağıdaki komutu kullanarak yeni bir proje oluşturun:

```console
dotnet new nunit -lang VB
```

[Yeni dotnet](../tools/dotnet-new.md) komut NUnit test kitaplık olarak kullanan bir test projesi oluşturur. Test Çalıştırıcısı'nda oluşturulan şablon yapılandırır *PrimeServiceTests.vbproj* dosyası:

[!code-xml[Packages](~/samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj#Packages)]

Test projesi oluşturma ve birim testlerini çalıştırmak için diğer paketleri gerektirir. `dotnet new` Önceki adımda NUnit ve NUnit test bağdaştırıcısı eklendi. Şimdi ekleyin `PrimeService` sınıf kitaplığı projesine başka bir bağımlılık olarak. Kullanım [ `dotnet add reference` ](../tools/dotnet-add-reference.md) komutu:

```console
dotnet add reference ../PrimeService/PrimeService.vbproj
```

Dosyanın tamamını görebilirsiniz [örnekleri depomuzdan](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) GitHub üzerinde.

Aşağıdaki nihai çözüm Düzen vardır:

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeService.Tests.vbproj
```

Aşağıdaki komutu yürütün *birim testi vb nunit* dizini:

```console
dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj
```

## <a name="creating-the-first-test"></a>İlk testi oluşturma

Bir yazma, test başarısız kolaylaştırır geçişi, sonra işlemi yineleyin. İçinde *PrimeService.Tests* dizini yeniden adlandırma *UnitTest1.vb* dosyasını *PrimeService_IsPrimeShould.VB* ve tüm içeriğini aşağıdaki kodla değiştirin:

```vb
Imports NUnit.Framework

Namespace PrimeService.Tests
    <TestFixture>
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <Test>
        Sub ReturnFalseGivenValueOf1()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

`<TestFixture>` Öznitelik, testleri içeren bir sınıfı gösterir. `<Test>` Özniteliği test Çalıştırıcısı tarafından yürütülen bir yöntemi gösterir. Gelen *birim testi vb nunit*, yürütme [ `dotnet test` ](../tools/dotnet-test.md) testler ve sınıf kitaplığı oluşturun ve ardından testleri çalıştırın. NUnit test Çalıştırıcısı, testlerinizi çalıştırmak için programın giriş noktası içerir. `dotnet test` oluşturduğunuz birim test projesi kullanarak test Çalıştırıcısı'nı başlatır.

Test başarısız olur. Uygulama henüz oluşturmadınız. En basit kod yazarak bu testin geçmesini `PrimeService` çalışır sınıfı:

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first")
End Function
```

İçinde *birim testi vb nunit* çalışması dizini `dotnet test` yeniden. `dotnet test` Komut çalıştıran bir derleme için `PrimeService` proje ve ardından `PrimeService.Tests` proje. Her iki proje oluşturduktan sonra bu tek bir test çalıştırır. Bu geçirir.

## <a name="adding-more-features"></a>Daha fazla özellik ekleme

Bir test geçirmek yaptığınız, daha fazla yazmak için zaman var. Birkaç basit durumlardaysa asal sayıları için vardır: 0, -1. Bu gibi durumlarda, yeni testleriyle olarak ekleyebilirsiniz `<Test>` özniteliği ancak hızla olur yorucu bir süreç. Benzer testleri paketi yazmanızı sağlayan diğer xUnit öznitelikleri vardır.  A `<TestCase>` öznitelik aynı kod yürütün, ancak farklı giriş bağımsız değişkenleri olan testleri paketi temsil eder. Kullanabileceğiniz `<TestCase>` bu girişleri değerlerini belirtmek için özniteliği.

Yeni testler oluşturmak yerine, asal numarası en düşük olan değerlerden küçüktür iki test bir test dizisi oluşturmak için bu iki öznitelikler uygulanır:

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

Çalıştırma `dotnet test`, ve bunlardan ikisi başarısız test eder. Tüm testleri geçer hale getirmek için değiştirme `if` başındaki yan tümcesi `Main` yönteminde *PrimeServices.cs* dosyası:

```vb
if candidate < 2
```

Ana Kitaplığı'nda daha fazla test, daha fazla Teoriler ve daha fazla kod ekleyerek yinelemek devam edin. Sahip olduğunuz [testlerinin tamamlanmış bir sürümünü](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) ve [Kitaplığı'nın tam bir uygulamaya](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb).

Küçük bir kitaplık ve bu kitaplık için birim testleri bir dizi oluşturdunuz. Böylece yeni paketler ekleme çözüm yapılandırılmış ve testleri normal iş akışı bir parçasıdır. Zaman ve çaba çözme hedeflerinden biri, uygulama üzerinde en yoğun.
