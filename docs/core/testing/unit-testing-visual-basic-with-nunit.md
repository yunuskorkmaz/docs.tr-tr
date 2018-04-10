---
title: Visual Basic .NET çekirdek dotnet test ve NUnit kullanarak test birim
description: Adım adım örnek Visual Basic çözüm oluşturma etkileşimli bir deneyim aracılığıyla .NET Core olarak birim testi kavramları hakkında bilgi NUnit kullanarak.
author: rprouse
ms.date: 12/01/2017
ms.topic: article
dev_langs:
- vb
ms.prod: .net-core
ms.openlocfilehash: 9ddb6dc439e11b394bc71ac30b72310f122da498
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-nunit"></a>Birim testi dotnet test ve NUnit kullanarak Visual Basic .NET Core kitaplıkları

Bu öğretici birim testi kavramlarını öğrenmek için adım adım örnek çözüm oluşturma etkileşimli bir deneyim gösterir. Önceden oluşturulmuş bir çözümü kullanarak öğreticiyi izleyin tercih ediyorsanız [görüntülemek veya karşıdan örnek kod](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-nunit/) başlamadan önce. Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="creating-the-source-project"></a>Kaynak projesi oluşturma

Kabuk penceresini açın. Adlı bir dizin oluşturun *birim testi vb nunit* çözümü tutmak için. Bu yeni dizin içinde çalıştırmak [ `dotnet new sln` ](../tools/dotnet-new.md) yeni bir çözüm oluşturmak için. Bu yöntem, sınıf kitaplığı ve birim testi projesi yönetmeyi kolaylaştırır. Çözüm dizini içinde oluşturmak bir *PrimeService* dizini. Aşağıdaki dizin ve dosya yapısı bugüne kadarki vardır:

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
```

Olun *PrimeService* geçerli dizin ve çalışma [ `dotnet new classlib -lang VB` ](../tools/dotnet-new.md) kaynak projesi oluşturmak için. Yeniden Adlandır *Class1.vb'ye* için *PrimeService.VB*. Teste dayalı geliştirme (TDD) kullanmak için bir başarısız uygulaması oluşturun `PrimeService` sınıfı:

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

Dizin geri değişiklik *birim-test etme-vb-kullanma-stest* dizini. Çalıştırma [ `dotnet sln add .\PrimeService\PrimeService.vbproj` ](../tools/dotnet-sln.md) sınıf kitaplığı proje çözüme eklemek için.

## <a name="install-the-nunit-project-template"></a>NUnit proje şablonu yükleyin

NUnit test projesi şablonları bir test projesi oluşturmadan önce yüklenmesi gerekir. Bu yalnızca bir kez yeni NUnit projeleri oluşturacağınız her geliştirici makinede yapılmalıdır. Çalıştırma [ `dotnet new -i NUnit3.DotNetNew.Template` ](../tools/dotnet-new.md) NUnit şablonları yüklemek için.

 ```
 dotnet new -i NUnit3.DotNetNew.Template
 ```

## <a name="creating-the-test-project"></a>Test projesi oluşturma

Ardından, oluşturun *PrimeService.Tests* dizini. Aşağıdaki anahat dizin yapısını gösterir:

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

Olun *PrimeService.Tests* dizine geçerli ve kullanarak yeni bir proje oluşturun [ `dotnet new nunit -lang VB` ](../tools/dotnet-new.md). Bu komut NUnit test kitaplığını kullanan bir test projesi oluşturur. Test Çalıştırıcısı'nda oluşturulan şablon yapılandırır *PrimeServiceTests.vbproj*:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

Test projesi oluşturmak ve birim testleri çalıştırmak için diğer paketleri gerektirir. `dotnet new` Önceki adımda NUnit ve NUnit test bağdaştırıcısı eklendi. Şimdi, ekleyin `PrimeService` sınıf kitaplığı proje için başka bir bağımlılık olarak. Kullanım [ `dotnet add reference` ](../tools/dotnet-add-reference.md) komutu:

```
dotnet add reference ../PrimeService/PrimeService.vbproj
```

Tüm dosyasında görebilirsiniz [örnekleri deposu](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) github'da.

Aşağıdaki nihai çözüm düzeni vardır:

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.vbproj
```

Yürütme [ `dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj` ](../tools/dotnet-sln.md) içinde *birim testi vb nunit* dizini.

## <a name="creating-the-first-test"></a>İlk testi oluşturma

TDD yaklaşım geçirmek kolaylaştırarak ve süreci tekrarlayarak yazma bir başarısız test için çağırır. Kaldırma *UnitTest1.vb* gelen *PrimeService.Tests* dizin ve adlı yeni bir Visual Basic dosyası oluşturma *PrimeService_IsPrimeShould.VB*. Aşağıdaki kodu ekleyin:

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

`<TestFixture>` Öznitelik testleri içeren bir sınıfı gösterir. `<Test>` Özniteliği test Çalıştırıcısı tarafından çalıştırılan bir yöntemi gösterir. Gelen *birim testi vb nunit*, yürütme [ `dotnet test` ](../tools/dotnet-test.md) testleri ve sınıf kitaplığı oluşturmak ve ardından testleri çalıştırın. NUnit test Çalıştırıcısı testleri çalıştırmak için program giriş noktası içerir. `dotnet test` oluşturduğunuz birim testi projesi kullanarak test Çalıştırıcısı başlatır.

Testiniz başarısız olur. Uygulama henüz oluşturmadınız. Bu test basit kod yazarken yapmasına `PrimeService` çalışır sınıfı:

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first")
End Function
```

İçinde *birim testi vb nunit* çalışması dizini `dotnet test` yeniden. `dotnet test` Komutu çalıştıran bir yapı `PrimeService` proje ve ardından `PrimeService.Tests` projesi. Her iki proje oluşturduktan sonra bu tek bir test çalıştırılır. Bunu geçirir.

## <a name="adding-more-features"></a>Daha fazla özellik ekleme

Bir test geçirmek yapmış olduğunuz, daha fazla yazma zamanı geldi. Diğer basit bazı durumlar asal sayılar için vardır: 0, -1. Bu gibi durumlarda yeni testleriyle olarak ekleyebilirsiniz `<Test>` özniteliği, ancak, hızlı hale can sıkıcı. Benzer testleri dizisi yazmak için etkinleştirmek diğer xUnit özniteliği vardır.  A `<TestCase>` özniteliği, aynı kod yürütmek ancak farklı giriş bağımsız değişkeni olan testleri bir paketi temsil eder. Kullanabileceğiniz `<TestCase>` özniteliği bu girişleri için değerleri belirtin.

Yeni testler oluşturmak yerine, en düşük asal sayı olan bir dizi test çeşitli değerleri değerinden iki test oluşturmak için bu iki öznitelikler uygulanır:

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

Çalıştırma `dotnet test`, ve bunların ikisini sınamaları başarısız. Tüm testleri geçişini yapmak için değiştirme `if` yöntemi başındaki yan tümcesi:

```vb
if candidate < 2
```

Daha fazla testleri, daha fazla kuramlarý ve daha fazla kod ana kitaplıkta ekleyerek yinelemek devam edin. Sahip olduğunuz [testleri tamamlanmış sürümü](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) ve [kitaplığının tam uygulama](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb).

Küçük bir kitaplığı ve bu kitaplık için birim testleri kümesini temel aldık. Böylece yeni paketleri ekleme çözümü yapılandırılmış ve testleri normal iş akışı bir parçasıdır. Çoğu zaman ve çaba uygulama amaçlarını çözme üzerinde yoğunlaşmıştır.
