---
title: C# testini MSTest ve .NET Core ile test etme
description: Noktanet testi ve MSTest kullanarak adım adım örnek bir çözüm oluşturma etkileşimli bir deneyim le C# ve .NET Core'daki birim test kavramlarını öğrenin.
author: ncarandini
ms.author: wiwagn
ms.date: 09/08/2017
ms.openlocfilehash: bd7891243d84277a7578089f8b4629ff5bada577
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240915"
---
# <a name="unit-testing-c-with-mstest-and-net-core"></a>C# testini MSTest ve .NET Core ile test etme

Bu öğretici, birim test kavramlarını öğrenmek için adım adım örnek bir çözüm oluşturma etkileşimli bir deneyim sunar. Önceden oluşturulmuş bir çözüm kullanarak öğreticiyi izlemeyi tercih ederseniz, başlamadan önce [örnek kodu görüntüleyin veya indirin.](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/) İndirme talimatları için [Örnekler ve Öğreticiler'e](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)bakın.

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="create-the-source-project"></a>Kaynak projeoluşturma

Bir kabuk penceresi açın. Çözümü tutmak için *birim-test-using-mstest* adlı bir dizin oluşturun. Bu yeni dizinin içinde, sınıf kitaplığı ve test projesi için yeni bir çözüm dosyası oluşturmak için çalıştırın. [`dotnet new sln`](../tools/dotnet-new.md) Ardından, bir *PrimeService* dizini oluşturun. Aşağıdaki anahat şimdiye kadar dizin ve dosya yapısını gösterir:

```console
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
```

*PrimeService'i* geçerli dizin [`dotnet new classlib`](../tools/dotnet-new.md) yapın ve kaynak projeyi oluşturmak için çalıştırın. *Class1.cs* *PrimeService.cs*yeniden adlandırın. `PrimeService` Sınıfın başarısız bir uygulamasını oluşturursunuz:

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

Dizin geri *birim-test-using-mstest* dizin değiştirin. Sınıf [`dotnet sln add PrimeService/PrimeService.csproj`](../tools/dotnet-sln.md) kitaplığı projesini çözüme eklemek için çalıştırın.

## <a name="create-the-test-project"></a>Test projesini oluşturma

Ardından, *PrimeService.Tests* dizinini oluşturun. Aşağıdaki anahat dizin yapısını gösterir:

```console
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

*PrimeService.Tests* dizinini geçerli dizini oluşturun ve yeni [`dotnet new mstest`](../tools/dotnet-new.md)bir proje oluşturun. Dotnet yeni komutu, test kitaplığı olarak MSTest kullanan bir test projesi oluşturur. Oluşturulan *şablon, PrimeServiceTests.csproj* dosyasındaki test koşucusu yla yapılandırır:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

Test projesi, birim testleri oluşturmak ve çalıştırmak için diğer paketler gerektirir. `dotnet new`önceki adımda MSTest SDK, MSTest test çerçevesi ve MSTest runner eklendi. Şimdi, `PrimeService` sınıf kitaplığını projeye başka bir bağımlılık olarak ekleyin. Komutu [`dotnet add reference`](../tools/dotnet-add-reference.md) kullanın:

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.csproj
```

Tüm dosyayı GitHub'daki [örnek deposunda](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) görebilirsiniz.

Aşağıdaki anahat son çözüm düzenini gösterir:

```console
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

[`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) *Birim-test-using-mstest* dizininde yürütün.

## <a name="create-the-first-test"></a>İlk testi oluşturma

Başarısız bir test yazarsın, geçer ve işlemi tekrarlarsın. *UnitTest1.cs* *PrimeService.Tests* dizininden kaldırın ve aşağıdaki içeriği içeren *PrimeService_IsPrimeShould.cs* adlı yeni bir C# dosyası oluşturun:

```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    [TestClass]
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;

        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [TestMethod]
        public void IsPrime_InputIs1_ReturnFalse()
        {
            var result = _primeService.IsPrime(1);

            Assert.IsFalse(result, "1 should not be prime");
        }
    }
}
```

[TestClass özniteliği](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) birim testleri içeren bir sınıf gösterir. [TestMethod özniteliği](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) bir yöntemin bir test yöntemi olduğunu gösterir.

Bu dosyayı [`dotnet test`](../tools/dotnet-test.md) kaydedin ve testleri ve sınıf kitaplığını oluşturmak ve testleri çalıştırmak için çalıştırın. MSTest test koşucusu, testlerinizi çalıştırmak için program giriş noktasını içerir. `dotnet test`oluşturduğunuz birim test projesini kullanarak test koşucusu başlatın.

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

*Birim-test-using-mstest* dizininde, yeniden `dotnet test` çalıştırın. Komut, `dotnet test` proje ve ardından `PrimeService.Tests` proje için bir yapı çalışır. `PrimeService` Her iki projeyi de yaptıktan sonra, bu tek testi çalıştırAr. Geçiyor.

## <a name="add-more-features"></a>Daha fazla özellik ekleme

Artık bir test sınavını geçtiğine göre, daha fazla yazma nın zamanı. Asal sayılar için birkaç basit durum daha vardır: 0, -1. [TestMethod özniteliği](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute)ile yeni testler ekleyebilirsiniz, ancak bu hızla sıkıcı olur. Benzer testler paketi yazmanızı sağlayan başka MSTest öznitelikleri de vardır.  [DataTestMethod özniteliği,](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataTestMethodAttribute) aynı kodu çalıştıran ancak farklı giriş bağımsız değişkenleri olan bir test paketini temsil eder. Bu girişler için değerleri belirtmek için [DataRow özniteliğini](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataRowAttribute) kullanabilirsiniz.

Yeni testler oluşturmak yerine, tek bir veri odaklı test oluşturmak için bu iki öznitelikleri uygulayın. Veri odaklı test, ikiden küçük birkaç değeri sınayan ve en düşük asal sayı olan bir yöntemdir:

[!code-csharp[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-using-mstest/csharp/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

Çalıştır `dotnet test`Ve bu testlerin iki başarısız. Tüm testlerin geçmesi için yöntemin başındaki `if` tümceyi değiştirin:

```csharp
if (candidate < 2)
```

Ana kitaplığa daha fazla test, daha fazla teori ve daha fazla kod ekleyerek yinelemeye devam edin. [Testlerin tamamlanmış sürümüne](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) ve [kitaplığın tam uygulamasına](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs)sahipsiniz.

O kitaplık için küçük bir kitaplık ve bir dizi birim testi inşa ettin. Yeni paketler ve testler eklemek normal iş akışının bir parçası olacak şekilde çözümü yapılandırdınız. Zamanınızın ve çabanızın çoğunu uygulamanın hedeflerini çözmeye yoğunlaşmışsınız.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting>
- [Birim testlerinde MSTest çerçevesini kullanma](/visualstudio/test/using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests)
- [MSTest V2 test çerçeve dokümanları](https://github.com/Microsoft/testfx-docs)
