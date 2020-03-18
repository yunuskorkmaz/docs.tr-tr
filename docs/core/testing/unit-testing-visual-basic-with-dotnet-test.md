---
title: Unit test Visual Basic in .NET Core ile dotnet testi ve xUnit
description: Noktanet testi ve xUnit kullanarak örnek bir Visual Basic çözümü adım adım oluşturma etkileşimli bir deneyim le .NET Core'daki birim test kavramlarını öğrenin.
author: billwagner
ms.author: wiwagn
ms.date: 09/01/2017
ms.openlocfilehash: 9a99d9031711a3e958132416d0235df76f4a9092
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240954"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-xunit"></a>Unit test Visual Basic .NET Core kitaplıkları dotnet testi ve xUnit kullanarak

Bu öğretici, birim test kavramlarını öğrenmek için adım adım örnek bir çözüm oluşturma etkileşimli bir deneyim sunar. Önceden oluşturulmuş bir çözüm kullanarak öğreticiyi izlemeyi tercih ederseniz, başlamadan önce [örnek kodu görüntüleyin veya indirin.](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-dotnet-test) İndirme talimatları için [Örnekler ve Öğreticiler'e](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)bakın.

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="creating-the-source-project"></a>Kaynak proje oluşturma

Bir kabuk penceresi açın. Çözümü tutmak için *birim-test-vb-using-dotnet-testi* adlı bir dizin oluşturun.
Bu yeni dizinin içinde, yeni bir çözüm oluşturmak için çalıştırın. [`dotnet new sln`](../tools/dotnet-new.md) Bu uygulama, hem sınıf kitaplığını hem de birim test projesini yönetmeyi kolaylaştırır.
Çözüm dizininin içinde bir *PrimeService* dizini oluşturun. Şimdiye kadar aşağıdaki dizin ve dosya yapısına sahipsiniz:

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

*PrimeService'i* geçerli dizin [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) yapın ve kaynak projeyi oluşturmak için çalıştırın. *Class1.VB'yi* *PrimeService.VB*olarak yeniden adlandırın. `PrimeService` Sınıfın başarısız bir uygulamasını oluşturursunuz:

```vb
Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first")
        End Function
    End Class
End Namespace
```

Dizin geri *birim-test-vb-using-dotnet-test* dizini değiştirin. Sınıf [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) kitaplığı projesini çözüme eklemek için çalıştırın.

## <a name="creating-the-test-project"></a>Test projesini oluşturma

Ardından, *PrimeService.Tests* dizinini oluşturun. Aşağıdaki anahat dizin yapısını gösterir:

```
/unit-testing-vb-using-dotnet-test
    unit-testing-vb-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

*PrimeService.Tests* dizinini geçerli dizini oluşturun ve yeni [`dotnet new xunit -lang VB`](../tools/dotnet-new.md)bir proje oluşturun. Bu komut, test kitaplığı olarak xUnit kullanan bir test projesi oluşturur. Oluşturulan şablon *PrimeServiceTests.vbproj*test koşucusu yapılandırır:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

Test projesi, birim testleri oluşturmak ve çalıştırmak için diğer paketler gerektirir. `dotnet new`önceki adımda xUnit ve xUnit runner eklendi. Şimdi, `PrimeService` sınıf kitaplığını projeye başka bir bağımlılık olarak ekleyin. Komutu [`dotnet add reference`](../tools/dotnet-add-reference.md) kullanın:

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.vbproj
```

Tüm dosyayı GitHub'daki [örnek deposunda](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService.Tests.vbproj) görebilirsiniz.

Aşağıdaki son klasör düzenine sahipsiniz:

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

[`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) *Birim-test-vb-using-dotnet-test* dizininde yürütün.

## <a name="creating-the-first-test"></a>İlk testi oluşturma

Başarısız bir test yazarsın, geçer ve işlemi tekrarlarsın. *UnitTest1.vb'i* *PrimeService.Tests* dizininden kaldırın ve *PrimeService_IsPrimeShould.VB*adlı yeni bir Visual Basic dosyası oluşturun. Aşağıdaki kodu ekleyin:

```vb
Imports Xunit

Namespace PrimeService.Tests
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <Fact>
        Sub IsPrime_InputIs1_ReturnFalse()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

Öznitelik, `<Fact>` test koşucusu tarafından çalıştırılabilen bir test yöntemini gösterir. *Birim-test-using-dotnet-testinden,* testleri [`dotnet test`](../tools/dotnet-test.md) ve sınıf kitaplığını oluşturmak ve testleri çalıştırmak için çalıştırın. xUnit test koşucusu, testlerinizi çalıştırmak için program giriş noktasını içerir. `dotnet test`oluşturduğunuz birim test projesini kullanarak test koşucusu başlatın.

Sınavın başarısız oldu. Uygulamayı henüz oluşturmadın. Bu testin çalışmasını sağlayan `PrimeService` sınıftaki en basit kodu yazarak geçmesini sağla:

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first.")
End Function
```

*Birim-test-vb-using-dotnet-test* dizininde, yeniden `dotnet test` çalıştırın. Komut, `dotnet test` proje ve ardından `PrimeService.Tests` proje için bir yapı çalışır. `PrimeService` Her iki projeyi de yaptıktan sonra, bu tek testi çalıştırAr. Geçiyor.

## <a name="adding-more-features"></a>Daha fazla özellik ekleme

Artık bir test sınavını geçtiğine göre, daha fazla yazma nın zamanı. Asal sayılar için birkaç basit durum daha vardır: 0, -1. Bu durumları öznitelik ile `<Fact>` yeni testler olarak ekleyebilirsiniz, ancak bu hızla sıkıcı olur. Benzer testler paketi yazmanızı sağlayan başka xUnit öznitelikleri de vardır.  Öznitelik, `<Theory>` aynı kodu çalıştıran ancak farklı giriş bağımsız değişkenleri olan bir test paketini temsil eder. Bu girişler `<InlineData>` için değerleri belirtmek için özniteliği kullanabilirsiniz.

Yeni testler oluşturmak yerine, tek bir teori oluşturmak için bu iki özniteliği uygulayın. Teori, ikiden küçük birkaç değeri test eden bir yöntemdir ve bu yöntem en düşük asal sayıdır:

[!code-vb[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-vb-dotnet-test/vb/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

Çalıştır `dotnet test`Ve bu testlerin iki başarısız. Tüm testlerin geçmesi için yöntemin başındaki `if` tümceyi değiştirin:

```vb
if candidate < 2
```

Ana kitaplığa daha fazla test, daha fazla teori ve daha fazla kod ekleyerek yinelemeye devam edin. [Testlerin tamamlanmış sürümüne](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) ve [kitaplığın tam uygulamasına](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService/PrimeService.vb)sahipsiniz.

O kitaplık için küçük bir kitaplık ve bir dizi birim testi inşa ettin. Yeni paketler ve testler eklemek normal iş akışının bir parçası olacak şekilde çözümü yapılandırdınız. Zamanınızın ve çabanızın çoğunu uygulamanın hedeflerini çözmeye yoğunlaşmışsınız.
