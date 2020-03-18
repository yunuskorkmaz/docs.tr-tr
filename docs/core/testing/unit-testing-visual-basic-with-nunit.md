---
title: Unit test Visual Basic in .NET Core,dotnet testi ve NUnit ile
description: Unit'i kullanarak örnek bir Visual Basic çözümü oluşturma etkileşimli bir deneyim le .NET Core'daki birim test kavramlarını öğrenin.
author: rprouse
ms.date: 10/04/2018
ms.openlocfilehash: a33447457344b241b4c2376d777b0deb7f556874
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240928"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-nunit"></a>Unit test Visual Basic .NET Core kitaplıkları dotnet testi ve NUnit kullanarak

Bu öğretici, birim test kavramlarını öğrenmek için adım adım örnek bir çözüm oluşturma etkileşimli bir deneyim sunar. Önceden oluşturulmuş bir çözüm kullanarak öğreticiyi izlemeyi tercih ederseniz, başlamadan önce [örnek kodu görüntüleyin veya indirin.](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-nunit/) İndirme talimatları için [Örnekler ve Öğreticiler'e](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)bakın.

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="prerequisites"></a>Önkoşullar

- [.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) veya sonraki sürümler.
- Tercih ettiğiniz bir metin veya kod düzenleyicisi.

## <a name="creating-the-source-project"></a>Kaynak proje oluşturma

Bir kabuk penceresi açın. Çözümü tutmak için *birim-test-vb-nunit* adlı bir dizin oluşturun. Bu yeni dizinin içinde, sınıf kitaplığı ve test projesi için yeni bir çözüm dosyası oluşturmak için aşağıdaki komutu çalıştırın:

```dotnetcli
dotnet new sln
```

Ardından, bir *PrimeService* dizini oluşturun. Aşağıdaki anahat şimdiye kadar dosya yapısını gösterir:

```console
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
```

*PrimeService'i* geçerli dizini yapın ve kaynak projeyi oluşturmak için aşağıdaki komutu çalıştırın:

```dotnetcli
dotnet new classlib -lang VB
```

*Class1.VB'yi* *PrimeService.VB*olarak yeniden adlandırın. `PrimeService` Sınıfın başarısız bir uygulamasını oluşturursunuz:

```vb
Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first.")
        End Function
    End Class
End Namespace
```

Dizin geri *birim-test-vb-using-mstest* dizini değiştirin. Sınıf kitaplığı projesini çözüme eklemek için aşağıdaki komutu çalıştırın:

```dotnetcli
dotnet sln add .\PrimeService\PrimeService.vbproj
```

## <a name="creating-the-test-project"></a>Test projesini oluşturma

Ardından, *PrimeService.Tests* dizinini oluşturun. Aşağıdaki anahat dizin yapısını gösterir:

```console
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

*PrimeService.Tests* dizinini geçerli dizini oluşturun ve aşağıdaki komutu kullanarak yeni bir proje oluşturun:

```dotnetcli
dotnet new nunit -lang VB
```

[Dotnet yeni](../tools/dotnet-new.md) komutu, test kitaplığı olarak NUnit kullanan bir test projesi oluşturur. Oluşturulan *şablon, PrimeServiceTests.vbproj* dosyasındaki test koşucusu yla yapılandırır:

[!code-xml[Packages](~/samples/snippets/core/testing/unit-testing-vb-nunit/vb/PrimeService.Tests/PrimeService.Tests.vbproj#Packages)]

Test projesi, birim testleri oluşturmak ve çalıştırmak için diğer paketler gerektirir. `dotnet new`önceki adımda NUnit ve NUnit test bağdaştırıcısı eklendi. Şimdi, `PrimeService` sınıf kitaplığını projeye başka bir bağımlılık olarak ekleyin. Komutu [`dotnet add reference`](../tools/dotnet-add-reference.md) kullanın:

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.vbproj
```

Tüm dosyayı GitHub'daki [örnek deposunda](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) görebilirsiniz.

Aşağıdaki nihai çözüm düzenine sahipsiniz:

```console
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeService.Tests.vbproj
```

*Birim-test-vb-nunit* dizininde aşağıdaki komutu uygulayın:

```dotnetcli
dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj
```

## <a name="creating-the-first-test"></a>İlk testi oluşturma

Başarısız bir test yazarsın, geçer ve işlemi tekrarlarsın. *PrimeService.Tests* dizininde *UnitTest1.vb* dosyasını *PrimeService_IsPrimeShould.VB* olarak yeniden adlandırın ve tüm içeriğini aşağıdaki kodla değiştirin:

```vb
Imports NUnit.Framework

Namespace PrimeService.Tests
    <TestFixture>
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <Test>
        Sub IsPrime_InputIs1_ReturnFalse()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

Öznitelik, `<TestFixture>` testleri içeren bir sınıfı gösterir. Öznitelik, `<Test>` test koşucusu tarafından çalıştırılabilen bir yöntemi gösterir. *Birim-test-vb-nunit*itibaren, [`dotnet test`](../tools/dotnet-test.md) testleri ve sınıf kitaplığı oluşturmak ve daha sonra testleri çalıştırmak için çalıştırın. NUnit test koşucusu, testlerinizi çalıştırmak için program giriş noktasını içerir. `dotnet test`oluşturduğunuz birim test projesini kullanarak test koşucusu başlatın.

Sınavın başarısız oldu. Uygulamayı henüz oluşturmadın. Bu testin çalışmasını sağlayan `PrimeService` sınıftaki en basit kodu yazarak geçmesini sağla:

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first.")
End Function
```

*Birim-test-vb-nunit* dizininde, tekrar `dotnet test` çalıştırın. Komut, `dotnet test` proje ve ardından `PrimeService.Tests` proje için bir yapı çalışır. `PrimeService` Her iki projeyi de yaptıktan sonra, bu tek testi çalıştırAr. Geçiyor.

## <a name="adding-more-features"></a>Daha fazla özellik ekleme

Artık bir test sınavını geçtiğine göre, daha fazla yazma nın zamanı. Asal sayılar için birkaç basit durum daha vardır: 0, -1. Bu durumları öznitelik ile `<Test>` yeni testler olarak ekleyebilirsiniz, ancak bu hızla sıkıcı olur. Benzer testler paketi yazmanızı sağlayan başka xUnit öznitelikleri de vardır.  Öznitelik, `<TestCase>` aynı kodu çalıştıran ancak farklı giriş bağımsız değişkenleri olan bir test paketini temsil eder. Bu girişler `<TestCase>` için değerleri belirtmek için özniteliği kullanabilirsiniz.

Yeni testler oluşturmak yerine, bu iki öznitelikleri, ikiden küçük değerleri test eden bir dizi test oluşturmak için uygulayın, bu da en düşük asal sayıdır:

[!code-vb[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-vb-nunit/vb/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

Çalıştır `dotnet test`Ve bu testlerin iki başarısız. Tüm testlerin geçmesi için, `if` `Main` *PrimeServices.cs* dosyasındaki yöntemin başındaki tümceyi değiştirin:

```vb
if candidate < 2
```

Ana kitaplığa daha fazla test, daha fazla teori ve daha fazla kod ekleyerek yinelemeye devam edin. [Testlerin tamamlanmış sürümüne](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) ve [kitaplığın tam uygulamasına](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb)sahipsiniz.

O kitaplık için küçük bir kitaplık ve bir dizi birim testi inşa ettin. Yeni paketler ve testler eklemek normal iş akışının bir parçası olacak şekilde çözümü yapılandırdınız. Zamanınızın ve çabanızın çoğunu uygulamanın hedeflerini çözmeye yoğunlaşmışsınız.
