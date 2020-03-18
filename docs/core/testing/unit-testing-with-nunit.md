---
title: C# nunit ve .NET Core ile birim testi
description: Noktanet testi ve NUnit kullanarak adım adım örnek bir çözüm oluşturma etkileşimli bir deneyim le C# ve .NET Core'daki birim test kavramlarını öğrenin.
author: rprouse
ms.date: 08/31/2018
ms.openlocfilehash: 283aa5a28ed213d4290eb3c73a98af56ec074ad0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240889"
---
# <a name="unit-testing-c-with-nunit-and-net-core"></a>C# nunit ve .NET Core ile birim testi

Bu öğretici, birim test kavramlarını öğrenmek için adım adım örnek bir çözüm oluşturma etkileşimli bir deneyim sunar. Önceden oluşturulmuş bir çözüm kullanarak öğreticiyi izlemeyi tercih ederseniz, başlamadan önce [örnek kodu görüntüleyin veya indirin.](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/) İndirme talimatları için [Örnekler ve Öğreticiler'e](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)bakın.

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="prerequisites"></a>Önkoşullar

- [.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) veya sonraki sürümler.
- Tercih ettiğiniz bir metin veya kod düzenleyicisi.

## <a name="creating-the-source-project"></a>Kaynak proje oluşturma

Bir kabuk penceresi açın. Çözümü tutmak için *birim-test-using-nunit* adlı bir dizin oluşturun. Bu yeni dizinin içinde, sınıf kitaplığı ve test projesi için yeni bir çözüm dosyası oluşturmak için aşağıdaki komutu çalıştırın:

```dotnetcli
dotnet new sln
```

Ardından, bir *PrimeService* dizini oluşturun. Aşağıdaki anahat şimdiye kadar dizin ve dosya yapısını gösterir:

```console
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
```

*PrimeService'i* geçerli dizini yapın ve kaynak projeyi oluşturmak için aşağıdaki komutu çalıştırın:

```dotnetcli
dotnet new classlib
```

*Class1.cs* *PrimeService.cs*yeniden adlandırın. `PrimeService` Sınıfın başarısız bir uygulamasını oluşturursunuz:

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

Dizin geri *birim-test-kullanarak-nunit* dizini değiştirin. Sınıf kitaplığı projesini çözüme eklemek için aşağıdaki komutu çalıştırın:

```dotnetcli
dotnet sln add PrimeService/PrimeService.csproj
```

## <a name="creating-the-test-project"></a>Test projesini oluşturma

Ardından, *PrimeService.Tests* dizinini oluşturun. Aşağıdaki anahat dizin yapısını gösterir:

```console
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

*PrimeService.Tests* dizinini geçerli dizini oluşturun ve aşağıdaki komutu kullanarak yeni bir proje oluşturun:

```dotnetcli
dotnet new nunit
```

[Dotnet yeni](../tools/dotnet-new.md) komutu, test kitaplığı olarak NUnit kullanan bir test projesi oluşturur. Oluşturulan şablon *PrimeService.Tests.csproj* dosyasında test koşucusu yapılandırır:

[!code-xml[Packages](~/samples/snippets/core/testing/unit-testing-using-nunit/csharp/PrimeService.Tests/PrimeService.Tests.csproj#Packages)]

Test projesi, birim testleri oluşturmak ve çalıştırmak için diğer paketler gerektirir. `dotnet new`önceki adımda Microsoft test SDK, NUnit test çerçevesi ve NUnit test bağdaştırıcısı eklendi. Şimdi, `PrimeService` sınıf kitaplığını projeye başka bir bağımlılık olarak ekleyin. Komutu [`dotnet add reference`](../tools/dotnet-add-reference.md) kullanın:

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.csproj
```

Tüm dosyayı GitHub'daki [örnek deposunda](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj) görebilirsiniz.

Aşağıdaki anahat son çözüm düzenini gösterir:

```console
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeService.Tests.csproj
```

*Birim-test-using-nunit* dizininde aşağıdaki komutu çalıştırın:

```dotnetcli
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
```

## <a name="creating-the-first-test"></a>İlk testi oluşturma

Başarısız bir test yazarsın, geçer ve işlemi tekrarlarsın. *PrimeService.Tests* dizininde, *UnitTest1.cs* dosyasını *PrimeService_IsPrimeShould.cs* olarak yeniden adlandırın ve tüm içeriğini aşağıdaki kodla değiştirin:

[!code-csharp[Sample_FirstTest](~/samples/snippets/core/testing/unit-testing-using-nunit/csharp/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_FirstTest)]

Öznitelik `[TestFixture]` birim testleri içeren bir sınıf gösterir. Öznitelik `[Test]` bir yöntem bir test yöntemi olduğunu gösterir.

Bu dosyayı [`dotnet test`](../tools/dotnet-test.md) kaydedin ve testleri ve sınıf kitaplığını oluşturmak ve testleri çalıştırmak için çalıştırın. NUnit test koşucusu, testlerinizi çalıştırmak için program giriş noktasını içerir. `dotnet test`oluşturduğunuz birim test projesini kullanarak test koşucusu başlatın.

Sınavın başarısız oldu. Uygulamayı henüz oluşturmadın. Bu testin çalışmasını sağlayan `PrimeService` sınıftaki en basit kodu yazarak geçmesini sağla:

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

*Birim-test-using-nunit* dizininde, yeniden `dotnet test` çalıştırın. Komut, `dotnet test` proje ve ardından `PrimeService.Tests` proje için bir yapı çalışır. `PrimeService` Her iki projeyi de yaptıktan sonra, bu tek testi çalıştırAr. Geçiyor.

## <a name="adding-more-features"></a>Daha fazla özellik ekleme

Artık bir test sınavını geçtiğine göre, daha fazla yazma nın zamanı. Asal sayılar için birkaç basit durum daha vardır: 0, -1. Öznitelik ile `[Test]` yeni testler ekleyebilirsiniz, ancak bu hızla sıkıcı olur. Benzer testler paketi yazmanızı sağlayan başka NUnit öznitelikleri de vardır.  Öznitelik, `[TestCase]` aynı kodu çalıştıran ancak farklı giriş bağımsız değişkenleri olan bir test paketi oluşturmak için kullanılır. Bu girişler `[TestCase]` için değerleri belirtmek için özniteliği kullanabilirsiniz.

Yeni testler oluşturmak yerine, tek bir veri odaklı test oluşturmak için bu özniteliği uygulayın. Veri odaklı test, ikiden küçük birkaç değeri sınayan ve en düşük asal sayı olan bir yöntemdir:

[!code-csharp[Sample_TestCode](~/samples/snippets/core/testing/unit-testing-using-nunit/csharp/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

Çalıştır `dotnet test`Ve bu testlerin iki başarısız. Tüm testlerin geçmesi için, `if` `Main` *PrimeService.cs* dosyasındaki yöntemin başındaki yan tümceyi değiştirin:

```csharp
if (candidate < 2)
```

Ana kitaplığa daha fazla test, daha fazla teori ve daha fazla kod ekleyerek yinelemeye devam edin. [Testlerin tamamlanmış sürümüne](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs) ve [kitaplığın tam uygulamasına](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs)sahipsiniz.

O kitaplık için küçük bir kitaplık ve bir dizi birim testi inşa ettin. Yeni paketler ve testler eklemek normal iş akışının bir parçası olacak şekilde çözümü yapılandırdınız. Zamanınızın ve çabanızın çoğunu uygulamanın hedeflerini çözmeye yoğunlaşmışsınız.
