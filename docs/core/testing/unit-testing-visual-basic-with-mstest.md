---
title: DotNet test ve MSTest ile .NET Core 'da birim testi Visual Basic
description: Etkileşimli bir deneyim aracılığıyla .NET Core 'daki birim testi kavramlarını, MSTest kullanarak bir örnek Visual Basic çözüm oluşturma adımını öğrenin.
author: billwagner
ms.author: wiwagn
ms.date: 09/01/2017
ms.openlocfilehash: df167e0559c841510df17ba39801e43315036241
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240941"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-mstest"></a>DotNet test ve MSTest kullanarak .NET Core kitaplıkları Visual Basic birim testi

Bu öğreticide, birim testi kavramlarını öğrenmek için bir örnek çözüm oluşturma adım adım yönergeler sunarak etkileşimli bir deneyim sağlanır. Önceden oluşturulmuş bir çözüm kullanarak öğreticiyi izlemeyi tercih ediyorsanız, başlamadan önce [örnek kodu görüntüleyin veya indirin](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-mstest/) . İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="creating-the-source-project"></a>Kaynak proje oluşturma

Bir kabuk penceresi açın. Çözümü tutmak için *Unit-Testing-vb-MSTest* adlı bir dizin oluşturun.
Yeni bir çözüm oluşturmak için bu yeni dizinin içinde [`dotnet new sln`](../tools/dotnet-new.md) çalıştırın. Bu uygulama, hem sınıf kitaplığını hem de birim testi projesini yönetmeyi kolaylaştırır.
Çözüm dizini içinde bir *Primeservice* dizini oluşturun. Şu ana kadar Şu dizin ve dosya yapısına sahipsiniz:

```console
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
```

Kaynak projeyi oluşturmak için *Primeservice* 'i geçerli dizin yapın ve [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) çalıştırın. *Class1. vb* ' i *primeservice. vb*olarak yeniden adlandırın. `PrimeService` sınıfının başarısız bir uygulamasını oluşturursunuz:

```vb
Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first")
        End Function
    End Class
End Namespace
```

Dizini *birim-test-vb-using-MSTest* dizinine geri çevirin. Çözüme Sınıf Kitaplığı projesini eklemek için [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) çalıştırın.

## <a name="creating-the-test-project"></a>Test projesi oluşturma

Ardından, *Primeservice. Tests* dizinini oluşturun. Aşağıdaki ana hat dizin yapısını gösterir:

```console
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

*Primeservice. test* dizinini geçerli dizini yapın ve [`dotnet new mstest -lang VB`](../tools/dotnet-new.md)kullanarak yeni bir proje oluşturun. Bu komut, test kitaplığı olarak MSTest kullanan bir test projesi oluşturur. Oluşturulan şablon, *Primeservicetests. vbproj*içindeki Test Çalıştırıcısı 'nı yapılandırır:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

Test projesi, birim testlerini oluşturmak ve çalıştırmak için diğer paketlerin kullanılmasını gerektirir. önceki adımda `dotnet new` MSTest ve MSTest Çalıştırıcısı eklendi. Şimdi, `PrimeService` sınıf kitaplığını projeye başka bir bağımlılık olarak ekleyin. [`dotnet add reference`](../tools/dotnet-add-reference.md) komutunu kullanın:

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.vbproj
```

GitHub 'daki [örnekler deposunda](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService.Tests.vbproj) dosyanın tamamını görebilirsiniz.

Aşağıdaki son çözüm düzenine sahipsiniz:

```console
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.vbproj
```

[`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) , *birim-test-vb-MSTest* dizininde yürütün.

## <a name="creating-the-first-test"></a>İlk test oluşturma

Başarısız bir test yazdığınızda, geçişi yapıp işlemi tekrarlayabilirsiniz. *UnitTest1. vb* 'Yi *primeservice. Tests* dizininden KALDıRıN ve *PrimeService_IsPrimeShould. vb*adlı yeni bir Visual Basic dosya oluşturun. Aşağıdaki kodu ekleyin:

```vb
Imports Microsoft.VisualStudio.TestTools.UnitTesting

Namespace PrimeService.Tests
    <TestClass>
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <TestMethod>
        Sub IsPrime_InputIs1_ReturnFalse()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.IsFalse(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

`<TestClass>` özniteliği, testleri içeren bir sınıfı gösterir. `<TestMethod>` özniteliği, Test Çalıştırıcısı tarafından çalıştırılan bir yöntemi gösterir. *-Testing-vb-MSTest*, testleri ve sınıf kitaplığını oluşturmak ve ardından testleri çalıştırmak için [`dotnet test`](../tools/dotnet-test.md) yürütün. MSTest Test Çalıştırıcısı, testlerinizi çalıştırmak için program giriş noktasını içerir. `dotnet test`, oluşturduğunuz birim test projesini kullanarak Test Çalıştırıcısı başlatır.

Testiniz başarısız oluyor. Uygulamayı henüz oluşturmadınız. Aşağıdaki `PrimeService` sınıfında en basit kodu yazarak bu test geçişini yapın:

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first.")
End Function
```

*Birim-test-vb-MSTest* dizininde `dotnet test` yeniden çalıştırın. `dotnet test` komutu, `PrimeService` projesi için bir derleme ve sonra `PrimeService.Tests` projesi için çalışır. Her iki proje de oluşturulduktan sonra bu tek testi çalıştırır. Geçirir.

## <a name="adding-more-features"></a>Daha fazla özellik ekleme

Artık bir test geçişi yapmış olduğunuza göre daha fazla yazma zamanı vardır. Asal sayıların diğer birkaç basit durumu vardır: 0,-1. Bu servis taleplerini `<TestMethod>` özniteliğiyle yeni testler olarak ekleyebilirsiniz, ancak bu hızlı bir şekilde sıkıcı olur. Benzer testlerin bir paketini yazmanızı sağlayan başka bir MSTest özniteliği vardır.  Bir `<DataTestMethod>` özniteliği, aynı kodu çalıştıran ancak farklı giriş bağımsız değişkenlerine sahip olan bir test paketini temsil eder. Bu girişlerin değerlerini belirtmek için `<DataRow>` özniteliğini kullanabilirsiniz.

Yeni test oluşturmak yerine, tek bir teorisi oluşturmak için bu iki özniteliği uygulayın. Teorisi, en düşük asal sayı olan iki değerden küçük birkaç değeri sınayan bir yöntemdir:

[!code-vb[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-vb-mstest/vb/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

`dotnet test`çalıştırın, bu testlerin ikisi de başarısız olur. Tüm testlerin geçişini yapmak için, yönteminin başındaki `if` yan tümcesini değiştirin:

```vb
if candidate < 2
```

Ana kitaplıkta daha fazla test, daha fazla yer ve daha fazla kod ekleyerek yinelemek için devam edin. [Testlerin tamamlanmış sürümüne](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb) ve [kitaplığın tüm uygulamasına](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService/PrimeService.vb)sahipsiniz.

Bu kitaplık için küçük bir kitaplık ve birim testleri kümesi oluşturdunuz. Çözümü, yeni paket ve test eklemek normal iş akışının bir parçası olacak şekilde öğrendiniz. Uygulamanın hedeflerini çözme konusunda zaman ve çaba harcamanızı en iyi şekilde gördünüz.
