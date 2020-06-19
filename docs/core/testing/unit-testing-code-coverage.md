---
title: Birim testi için kod kapsamını kullanma
description: .NET birim testleri için kod kapsamı özelliklerini nasıl kullanacağınızı öğrenin.
author: IEvangelist
ms.author: dapine
ms.date: 06/16/2020
ms.openlocfilehash: 47f10ae367f511d5d02d32bfcb35bf4775a3e946
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990286"
---
# <a name="use-code-coverage-for-unit-testing"></a>Birim testi için kod kapsamını kullanma

Birim testleri işlevselliğin sağlanmasına yardımcı olur ve yeniden düzenleme çabalarına yönelik bir doğrulama yöntemi sağlar. Kod kapsamı, birim testleri tarafından çalıştırılan kod miktarının bir ölçümüdür; çizgiler, dallar ya da Yöntemler. Örnek olarak, yalnızca iki koşullu kod dalı (_dal a_ve _dal b_) olan basit bir uygulamanız varsa, koşullu _dalı doğrulayan bir_ birim testi %50 şube kodu kapsamını rapor eder.

Bu makalede, ReportGenerator kullanarak kapak ve rapor oluşturma ile birim testi için kod kapsamının kullanımı ele alınmaktadır. Bu makale, test çerçevesi olarak C# ve xUnit 'e odaklanırken hem MSTest hem de NUnit de çalışır. Kapak, C# için platformlar arası kod kapsamı çerçevesi sağlayan [GitHub üzerinde açık kaynaklı bir projem](https://github.com/coverlet-coverage/coverlet) . [Kapak Let](https://dotnetfoundation.org/projects/coverlet) , .net Foundation 'ın bir parçasıdır. Kapak Let, rapor oluşturma için kullanılan Cobertura kapsam testi çalıştırma verilerini toplar.

Ayrıca, bu makalede bir rapor oluşturmak için bir kapak Let testi çalıştırmasında toplanan kod kapsamı bilgilerinin nasıl kullanılacağı açıklanır. Rapor oluşturma, [GitHub-ReportGenerator üzerinde başka bir açık kaynak proje](https://github.com/danielpalme/ReportGenerator)kullanılarak mümkündür. ReportGenerator, Cobertura tarafından üretilen kapsam raporlarını birçok farklı biçimdeki insanlar tarafından okunabilen raporlar halinde dönüştürür.

## <a name="system-under-test"></a>Test altındaki sistem

"Test edilen sistem", birim testlerini yazarken bir nesne, hizmet veya diğer herhangi bir şey olabilir. Bu makalenin amacına yönelik olarak, test altında sistem olacak bir sınıf kitaplığı ve buna karşılık gelen iki birim test projesi oluşturacaksınız.

### <a name="create-a-class-library"></a>Sınıf kitaplığı oluşturma

Adlı yeni bir dizindeki komut isteminden `UnitTestingCodeCoverage` , komutunu kullanarak yeni bir .net standart sınıf kitaplığı oluşturun [`dotnet new classlib`](../tools/dotnet-new.md#classlib) :

```dotnetcli
dotnet new classlib -n Numbers
```

Aşağıdaki kod parçacığı `PrimeService` bir sayının asal olup olmadığını denetlemek için işlevsellik sağlayan basit bir sınıfı tanımlar. Aşağıdaki kod parçacığını kopyalayın ve *sayılar* dizininde otomatik olarak oluşturulan *Class1.cs* dosyasının içeriğini değiştirin. *Class1.cs* dosyasını *PrimeService.cs*olarak yeniden adlandırın.

```csharp
namespace System.Numbers
{
    public class PrimeService
    {
        public bool IsPrime(int candidate)
        {
            if (candidate < 2)
            {
                return false;
            }

            for (int divisor = 2; divisor <= Math.Sqrt(candidate); ++divisor)
            {
                if (candidate % divisor == 0)
                {
                    return false;
                }
            }
            return true;
        }
    }
}
```

> [!TIP]
> Bu, `Numbers` sınıf kitaplığının ad alanına kasıtlı olarak eklendiğini ifade etmek için gereklidir `System` . Bu, <xref:System.Math?displayProperty=fullName> bir ad alanı bildirimi olmadan erişilebilir olmasını sağlar `using System;` . Daha fazla bilgi için bkz. [ad alanı (C# Başvurusu)](../../csharp/language-reference/keywords/namespace.md).

### <a name="create-test-projects"></a>Test projeleri oluşturma

Komutunu kullanarak aynı komut isteminden iki yeni **xUnit test projesi (.NET Core)** şablonu oluşturun [`dotnet new xunit`](../tools/dotnet-new.md#test) :

```dotnetcli
dotnet new xunit -n XUnit.Coverlet.Collector
```

```dotnetcli
dotnet new xunit -n XUnit.Coverlet.MSBuild
```

Yeni oluşturulan xUnit test projelerinin her ikisi de, *sayılar* sınıf kitaplığının bir proje başvurusunu eklemesi gerekir. Bu sayede test projelerinin test için *Primeservice* 'e erişimi olur. Komut isteminden şu [`dotnet add`](../tools/dotnet-add-reference.md) komutu kullanın:

```dotnetcli
dotnet add XUnit.Coverlet.Collector\XUnit.Coverlet.Collector.csproj reference Numbers\Numbers.csproj
```

```dotnetcli
dotnet add XUnit.Coverlet.MSBuild\XUnit.Coverlet.MSBuild.csproj reference Numbers\Numbers.csproj
```

*MSBuild* projesi, [Kapak Let. MSBuild](https://www.nuget.org/packages/coverlet.msbuild) NuGet paketine bağlı olacağı için uygun şekilde adlandırılır. Şu komutu çalıştırarak bu paket bağımlılığını ekleyin [`dotnet add package`](../tools/dotnet-add-package.md) :

```dotnetcli
cd XUnit.Coverlet.MSBuild && dotnet add package coverlet.msbuild && cd ..
```

Önceki komut, dizinleri *MSBuild* test projesine etkin bir biçimde değiştirdi ve ardından NuGet paketini ekledi. Bu işlem tamamlandığında, dizinler değiştirilmiştir ve bir düzey daha sonra çalışır.

Her iki *UnitTest1.cs* dosyasını açın ve içeriğini aşağıdaki kod parçacığıyla değiştirin. *UnitTest1.cs* dosyalarını *PrimeServiceTests.cs*olarak yeniden adlandırın.

```csharp
using System.Numbers;
using Xunit;

namespace XUnit.Coverlet
{
    public class PrimeServiceTests
    {
        readonly PrimeService _primeService;

        public PrimeServiceTests() => _primeService = new PrimeService();

        [
            Theory,
            InlineData(-1), InlineData(0), InlineData(1)
        ]
        public void IsPrime_ValuesLessThan2_ReturnFalse(int value) =>
            Assert.False(_primeService.IsPrime(value), $"{value} should not be prime");

        [
            Theory,
            InlineData(2), InlineData(3), InlineData(5), InlineData(7)
        ]
        public void IsPrime_PrimesLessThan10_ReturnTrue(int value) =>
            Assert.True(_primeService.IsPrime(value), $"{value} should be prime");

        [
            Theory,
            InlineData(4), InlineData(6), InlineData(8), InlineData(9)
        ]
        public void IsPrime_NonPrimesLessThan10_ReturnFalse(int value) =>
            Assert.False(_primeService.IsPrime(value), $"{value} should not be prime");
    }
}
```

### <a name="create-a-solution"></a>Çözüm oluşturma

Komut isteminden, sınıf kitaplığını ve iki test projesini kapsüllemek için yeni bir çözüm oluşturun. Komutunu kullanarak [`dotnet sln`](../tools/dotnet-sln.md) :

```dotnetcli
dotnet new sln -n XUnit.Coverage
```

Bu işlem `XUnit.Coverage` *Unittestingcodecoverage* dizininde yeni bir çözüm dosya adı oluşturur. Projeleri çözümün köküne ekleyin.

## <a name="linux"></a>[Linux](#tab/linux)

```dotnetcli
dotnet sln XUnit.Coverage.sln add **/*.csproj --in-root
```

## <a name="windows"></a>[Windows](#tab/windows)

```dotnetcli
dotnet sln XUnit.Coverage.sln add (ls **/*.csproj) --in-root
```

---

Şu komutu kullanarak çözümü oluşturun [`dotnet build`](../tools/dotnet-build.md) :

```dotnetcli
dotnet build
```

Yapı başarılı olursa, bu üç projeyi, uygun şekilde Başvurulmuş proje ve paketleri oluşturmuş ve kaynak kodu doğru bir şekilde güncelleştirdiniz. Bravo!

## <a name="tooling"></a>Araçlar

İki tür kod kapsama aracı vardır:

- **Veri toplayıcılar:** Veri toplayıcıları test yürütmeyi izler ve test çalıştırmaları hakkında bilgi toplar. Toplanan bilgileri XML ve JSON gibi çeşitli çıkış biçimlerinde raporlarlar. Daha fazla bilgi için [Ilk veri toplayıcısına](https://github.com/Microsoft/vstest-docs/blob/master/docs/extensions/datacollector.md)bakın.
- **Rapor oluşturucuları:** Genellikle stilli HTML olarak rapor oluşturmak için test çalıştırmalarından toplanan verileri kullanın.

Bu bölümde, odak veri toplayıcı araçlarıdır. Kod kapsamı için kapak Let 'i kullanmak için, var olan bir birim testi projesi uygun paket bağımlılıklarına sahip olmalıdır veya alternatif olarak [.net küresel araçları](../tools/global-tools.md) ve buna karşılık gelen [Kapak Let. Console](https://www.nuget.org/packages/coverlet.console) NuGet paketini kullanır.

## <a name="integrate-with-net-test"></a>.NET test ile tümleştirin

XUnit test projesi şablonu, varsayılan olarak, [Şimdi kapak Let. Collector](https://www.nuget.org/packages/coverlet.collector) ile tümleşir.
Komut isteminden dizinleri *xUnit. Projeklet. Collector* projesiyle değiştirin ve şu [`dotnet test`](../tools/dotnet-test.md) komutu çalıştırın:

```dotnetcli
cd XUnit.Coverlet.Collector && dotnet test --collect:"XPlat Code Coverage"
```

> [!NOTE]
> `"XPlat Code Coverage"`Bağımsız değişkeni, kapak Let veri toplayıcılarına karşılık gelen kolay bir addır. Bu ad gereklidir, ancak büyük/küçük harfe duyarlıdır.

Çalıştırmanın bir parçası olarak `dotnet test` , elde edilen bir *coverage.cobertura.xml* dosyası *TestResults* dizinine çıktıdır. XML dosyası sonuçları içerir. Bu, .NET Core CLI temel alan platformlar arası bir seçenektir ve MSBuild 'in kullanılamadığı yapı sistemleri için idealdir.

Örnek *coverage.cobertura.xml* dosya aşağıda verilmiştir.

```xml
<?xml version="1.0" encoding="utf-8"?>
<coverage line-rate="1" branch-rate="1" version="1.9" timestamp="1592248008"
          lines-covered="12" lines-valid="12" branches-covered="6" branches-valid="6">
  <sources>
    <source>C:\</source>
  </sources>
  <packages>
    <package name="Numbers" line-rate="1" branch-rate="1" complexity="6">
      <classes>
        <class name="Numbers.PrimeService" line-rate="1" branch-rate="1" complexity="6"
               filename="Numbers\PrimeService.cs">
          <methods>
            <method name="IsPrime" signature="(System.Int32)" line-rate="1"
                    branch-rate="1" complexity="6">
              <lines>
                <line number="8" hits="11" branch="False" />
                <line number="9" hits="11" branch="True" condition-coverage="100% (2/2)">
                  <conditions>
                    <condition number="7" type="jump" coverage="100%" />
                  </conditions>
                </line>
                <line number="10" hits="3" branch="False" />
                <line number="11" hits="3" branch="False" />
                <line number="14" hits="22" branch="True" condition-coverage="100% (2/2)">
                  <conditions>
                    <condition number="57" type="jump" coverage="100%" />
                  </conditions>
                </line>
                <line number="15" hits="7" branch="False" />
                <line number="16" hits="7" branch="True" condition-coverage="100% (2/2)">
                  <conditions>
                    <condition number="27" type="jump" coverage="100%" />
                  </conditions>
                </line>
                <line number="17" hits="4" branch="False" />
                <line number="18" hits="4" branch="False" />
                <line number="20" hits="3" branch="False" />
                <line number="21" hits="4" branch="False" />
                <line number="23" hits="11" branch="False" />
              </lines>
            </method>
          </methods>
          <lines>
            <line number="8" hits="11" branch="False" />
            <line number="9" hits="11" branch="True" condition-coverage="100% (2/2)">
              <conditions>
                <condition number="7" type="jump" coverage="100%" />
              </conditions>
            </line>
            <line number="10" hits="3" branch="False" />
            <line number="11" hits="3" branch="False" />
            <line number="14" hits="22" branch="True" condition-coverage="100% (2/2)">
              <conditions>
                <condition number="57" type="jump" coverage="100%" />
              </conditions>
            </line>
            <line number="15" hits="7" branch="False" />
            <line number="16" hits="7" branch="True" condition-coverage="100% (2/2)">
              <conditions>
                <condition number="27" type="jump" coverage="100%" />
              </conditions>
            </line>
            <line number="17" hits="4" branch="False" />
            <line number="18" hits="4" branch="False" />
            <line number="20" hits="3" branch="False" />
            <line number="21" hits="4" branch="False" />
            <line number="23" hits="11" branch="False" />
          </lines>
        </class>
      </classes>
    </package>
  </packages>
</coverage>
```

> [!TIP]
> Alternatif olarak, yapı sisteminiz zaten MSBuild kullanıyorsa MSBuild paketini kullanabilirsiniz. Komut isteminden dizinleri *xUnit. Projeklet. MSBuild* projesiyle değiştirin ve şu `dotnet test` komutu çalıştırın:
>
> ```dotnetcli
> dotnet test --collect:"XPlat Code Coverage"
> ```
>
> Elde edilen *coverage.cobertura.xml* dosyası çıktı.

## <a name="generate-reports"></a>Rapor oluştur

Artık birim testi çalıştırmalarının verilerini toplayabilolduğunuza göre, [Reportgenerator](https://github.com/danielpalme/ReportGenerator)kullanarak raporlar oluşturabilirsiniz. [Reportgenerator](https://www.nuget.org/packages/dotnet-reportgenerator-globaltool) NuGet paketini [.net küresel aracı](../tools/global-tools.md)olarak yüklemek için şu [`dotnet tool install`](../tools/dotnet-tool-install.md) komutu kullanın:

```dotnetcli
dotnet tool install -g dotnet-reportgenerator-globaltool
```

Aracı çalıştırın ve önceki Test çalıştırmasında çıktı *coverage.cobertura.xml* dosyası verildiğinde istenen seçenekleri sağlayın.

```console
reportgenerator
"-reports:Path\To\TestProject\TestResults\{guid}\coverage.cobertura.xml"
"-targetdir:coveragereport"
-reporttypes:Html
```

Bu komutu çalıştırdıktan sonra, bir HTML dosyası oluşturulan raporu temsil eder.

:::image type="content" source="media/test-report.png" lightbox="media/test-report.png" alt-text="Birim testi tarafından oluşturulan rapor":::

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio birim testi kapağı kapsamı](/visualstudio/test/using-code-coverage-to-determine-how-much-code-is-being-tested)
- [GitHub-kapak Let deposu](https://github.com/coverlet-coverage/coverlet)
- [GitHub-ReportGenerator deposu](https://github.com/danielpalme/ReportGenerator)
- [ReportGenerator proje sitesi](https://danielpalme.github.io/ReportGenerator)
- [Test komutunu .NET Core CLI](../tools/dotnet-test.md)

## <a name="next-steps"></a>Sonraki Adımlar

> [!div class="nextstepaction"]
> [Birim testi en iyi deneyimler](unit-testing-best-practices.md)
