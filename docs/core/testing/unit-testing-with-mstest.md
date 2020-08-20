---
title: MSTest ve .NET Core Ile birim testi C#
description: C# ve .NET Core 'daki birim testi kavramlarını, DotNet test ve MSTest kullanarak örnek bir çözüm oluşturarak bir etkileşimli deneyim aracılığıyla öğrenin.
author: ncarandini
ms.author: wiwagn
ms.date: 09/08/2017
ms.openlocfilehash: 765b57dce323c10dc5fcbf395cb7d52be76046c2
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656364"
---
# <a name="unit-testing-c-with-mstest-and-net-core"></a>MSTest ve .NET Core Ile birim testi C#

Bu öğreticide, birim testi kavramlarını öğrenmek için bir örnek çözüm oluşturma adım adım yönergeler sunarak etkileşimli bir deneyim sağlanır. Önceden oluşturulmuş bir çözüm kullanarak öğreticiyi izlemeyi tercih ediyorsanız, başlamadan önce [örnek kodu görüntüleyin veya indirin](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/) . İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#view-and-download-samples).

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="create-the-source-project"></a>Kaynak projeyi oluşturma

Bir kabuk penceresi açın. Çözümü tutmak için- *Testing-testusing* adlı bir dizin oluşturun. Bu yeni dizin içinde, [`dotnet new sln`](../tools/dotnet-new.md) sınıf kitaplığı ve test projesi için yeni bir çözüm dosyası oluşturmak üzere öğesini çalıştırın. Ardından, bir *Primeservice* dizini oluşturun. Aşağıdaki ana hat, şu ana kadar dizin ve dosya yapısını gösterir:

```console
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
```

Kaynak projeyi oluşturmak için *Primeservice* 'i geçerli dizin yapın ve çalıştırın [`dotnet new classlib`](../tools/dotnet-new.md) . *Class1.cs* *olarak yeniden*adlandırın. Sınıfın başarısız bir uygulamasını oluşturursunuz `PrimeService` :

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

Dizini *Unit-Testing-MSTest* dizinine doğru değiştirin. [`dotnet sln add PrimeService/PrimeService.csproj`](../tools/dotnet-sln.md)Çözüme Sınıf Kitaplığı projesini eklemek için ' i çalıştırın.

## <a name="create-the-test-project"></a>Test projesi oluşturma

Ardından, *Primeservice. Tests* dizinini oluşturun. Aşağıdaki ana hat dizin yapısını gösterir:

```console
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

*Primeservice. test* dizinini geçerli dizini yapın ve kullanarak yeni bir proje oluşturun [`dotnet new mstest`](../tools/dotnet-new.md) . DotNet New komutu, test kitaplığı olarak MSTest kullanan bir test projesi oluşturur. Oluşturulan şablon, *Primeservicetests. csproj* dosyasında Test Çalıştırıcısı 'nı yapılandırır:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

Test projesi, birim testlerini oluşturmak ve çalıştırmak için diğer paketlerin kullanılmasını gerektirir. `dotnet new` önceki adımda MSTest SDK, MSTest test çerçevesi ve MSTest Çalıştırıcısı eklenmiştir. Şimdi, `PrimeService` sınıf kitaplığını projeye başka bir bağımlılık olarak ekleyin. Şu [`dotnet add reference`](../tools/dotnet-add-reference.md) komutu kullanın:

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.csproj
```

GitHub 'daki [örnekler deposunda](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) dosyanın tamamını görebilirsiniz.

Aşağıdaki ana hat, son çözüm yerleşimini göstermektedir:

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

[`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) *Birim-test-using-MSTest* dizininde yürütün.

## <a name="create-the-first-test"></a>İlk testi oluşturma

Başarısız bir test yazdığınızda, geçişi yapıp işlemi tekrarlayabilirsiniz. *UnitTest1.cs* öğesini *primeservice. Tests* dizininden kaldırın ve aşağıdaki içeriğe sahip *PrimeService_IsPrimeShould. cs* adlı yeni bir C# dosyası oluşturun:

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

[TestClass özniteliği](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) birim testlerini içeren bir sınıfı gösterir. [TestMethod özniteliği](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) bir yöntemin test yöntemi olduğunu gösterir.

[`dotnet test`](../tools/dotnet-test.md)Testleri ve sınıf kitaplığını derlemek ve ardından testleri çalıştırmak için bu dosyayı kaydedin ve yürütün. MSTest Test Çalıştırıcısı, testlerinizi çalıştırmak için program giriş noktasını içerir. `dotnet test` oluşturduğunuz birim test projesini kullanarak Test Çalıştırıcısı başlatır.

Testiniz başarısız oluyor. Uygulamayı henüz oluşturmadınız. Bu test geçişini, çalıştıran sınıfa en basit kodu yazarak yapın `PrimeService` :

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

*Birim-test-using-MSTest* dizininde `dotnet test` yeniden çalıştırın. `dotnet test`Komutu, proje için bir yapı `PrimeService` ve ardından proje için çalışır `PrimeService.Tests` . Her iki proje de oluşturulduktan sonra bu tek testi çalıştırır. Geçirir.

## <a name="add-more-features"></a>Daha fazla özellik ekleyin

Artık bir test geçişi yapmış olduğunuza göre daha fazla yazma zamanı vardır. Asal sayıların diğer birkaç basit durumu vardır: 0,-1. [TestMethod özniteliğiyle](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute)yeni testler ekleyebilirsiniz, ancak bu hızlı bir şekilde sıkıcı hale gelir. Benzer testlerin bir paketini yazmanızı sağlayan başka bir MSTest özniteliği vardır.  [Datatestmethod özniteliği](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataTestMethodAttribute) , aynı kodu çalıştıran ancak farklı giriş bağımsız değişkenlerine sahip olan bir test paketini temsil eder. Bu girişlerin değerlerini belirtmek için [DataRow özniteliğini](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataRowAttribute) kullanabilirsiniz.

Yeni test oluşturmak yerine, tek bir veri temelli test oluşturmak için bu iki özniteliği uygulayın. Veri temelli test, en düşük asal sayı olan iki değerden küçük birkaç değeri sınayan bir yöntemdir:

[!code-csharp[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-using-mstest/csharp/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

Çalıştır `dotnet test` ve bu testlerin ikisi de başarısız olur. Tüm testlerin geçişini yapmak için `if` yönteminin başındaki yan tümceyi değiştirin:

```csharp
if (candidate < 2)
```

Ana kitaplıkta daha fazla test, daha fazla yer ve daha fazla kod ekleyerek yinelemek için devam edin. [Testlerin tamamlanmış sürümüne](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) ve [kitaplığın tüm uygulamasına](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs)sahipsiniz.

Bu kitaplık için küçük bir kitaplık ve birim testleri kümesi oluşturdunuz. Çözümü, yeni paket ve test eklemek normal iş akışının bir parçası olacak şekilde öğrendiniz. Uygulamanın hedeflerini çözme konusunda zaman ve çaba harcamanızı en iyi şekilde gördünüz.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting>
- [Birim testlerinde MSTest çerçevesini kullanma](/visualstudio/test/using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests)
- [MSTest v2 test çerçevesi belgeleri](https://github.com/Microsoft/testfx-docs)
