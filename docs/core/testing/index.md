---
title: .NET Core ve .NET Standard birim testi
description: Bu makalede, .NET Core ve .NET Standard projelerine yönelik birim testi hakkında kısa bir genel bakış sunulmaktadır.
author: ardalis
ms.author: wiwagn
ms.date: 05/18/2020
zone_pivot_groups: unit-testing-framework-set-one
ms.openlocfilehash: e15f80b173389cdff86c6e62013e9c0f21171dd6
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703097"
---
# <a name="unit-testing-in-net-core-and-net-standard"></a>.NET Core ve .NET Standard birim testi

.NET Core, birim testlerini oluşturmayı kolaylaştırır. Bu makale, birim testlerini tanıtır ve diğer test türlerinden farklı şekilde nasıl farklılık gösterir. Sayfanın alt kısmındaki bağlantılı kaynaklar çözümünüze bir test projesi nasıl ekleneceğini gösterir. Test projenizi ayarladıktan sonra, komut satırını veya Visual Studio 'Yu kullanarak birim testlerinizi çalıştırabileceksiniz.

Bir **ASP.NET Core** projesi test ediyorsanız bkz. [ASP.NET Core tümleştirme testleri](/aspnet/core/test/integration-tests#test-app-prerequisites).

.NET Core 2,0 ve üzeri [.NET Standard 2,0](../../standard/net-standard.md)' i destekler. Bu, birim testlerini göstermek için kitaplıklarını kullanacağız.

C#, F # ve Visual Basic için yerleşik .NET Core 2,0 ve sonraki birim test projesi şablonlarını, kişisel projeniz için bir başlangıç noktası olarak kullanabilirsiniz.

## <a name="what-are-unit-tests"></a>Birim testi nedir?

Otomatikleştirilmiş testlerin olması, bir yazılım uygulamasının yazarlarını yapmak için yaptığı şeyleri yaptığını sağlamak için harika bir yoldur. Yazılım uygulamaları için birden çok test türü vardır. Bu, tümleştirme testlerini, Web testlerini, yük testlerini ve diğerlerini içerir. **Birim testleri** , bireysel yazılım bileşenlerini ve yöntemlerini test eder. Birim testleri yalnızca geliştiricinin denetimindeki kodu test etmelidir. Altyapı sorunlarını test etmez. Altyapı sorunları veritabanları, dosya sistemleri ve ağ kaynaklarıdır.

Ayrıca, testlerin yazılması için en iyi uygulamaları aklınızda bulundurun. Örneğin, [test odaklı geliştirme (TDD)](https://deviq.com/test-driven-development/) , bir birim testinin denetlenecek kodun önüne yazıldığı bir birimdir. TDD yazmadan önce kitap için bir ana hat oluşturma gibidir. Geliştiricilerin daha basit, daha okunabilir ve verimli bir kod yazmasına yardımcı olmak için tasarlanmıştır.

> [!NOTE]
> ASP.NET ekibi, geliştiricilerin test sınıfları ve yöntemleri için iyi adlarla karşılaşmalarına yardımcı olmak için [Bu kuralları](https://github.com/dotnet/aspnetcore/wiki/Engineering-guidelines#unit-tests-and-functional-tests) izler.

Birim testlerini yazarken altyapıya bağımlılıklar tanıtmamanızda deneyin. Bunlar testleri yavaş ve Brittle yapar ve tümleştirme testleri için ayrılmış olmalıdır. [Açık bağımlılıklar ilkesini](https://deviq.com/explicit-dependencies-principle/) Izleyerek ve [bağımlılık ekleme](/aspnet/core/fundamentals/dependency-injection)'yi kullanarak uygulamanızdaki bu bağımlılıklardan kaçınabilirsiniz. Ayrıca, birim testlerinizi tümleştirme testlerinizden ayrı bir projede tutabilirsiniz. Bu, birim testi projenizin altyapı paketlerine yönelik başvuruları veya bağımlılıkları olmamasını sağlar.

## <a name="next-steps"></a>Sonraki adımlar

.NET Core projelerinde birim testi hakkında daha fazla bilgi:

.NET Core birim testi projeleri için desteklenir:

- [C#](../../csharp/index.yml)
- [F#](../../fsharp/index.yml)
- [Visual Basic](../../visual-basic/index.yml)

Ayrıca, çeşitli birim test çerçeveleri arasından seçim yapabilirsiniz:

- [xUnit](https://xunit.net/)
- [NUnit](https://nunit.org)
- [MSTest](https://github.com/Microsoft/testfx-docs)

Aşağıdaki izlenecek yollarda daha fazla bilgi edinebilirsiniz:

:::zone pivot="mstest"

- [ *MSTest* ve *C#* kullanarak .NET Core CLI](unit-testing-with-mstest.md)birim testleri oluşturun.
- [ *MSTest* ve *F #* kullanarak .NET Core CLI](unit-testing-fsharp-with-mstest.md)birim testleri oluşturun.
- [ *MSTest* ve *Visual Basic* ](unit-testing-visual-basic-with-mstest.md)kullanarak birim testleri oluşturun .NET Core CLI.

:::zone-end
:::zone pivot="xunit"

- [.NET Core CLI Ile *xUnit* ve *C#* ](unit-testing-with-dotnet-test.md)kullanarak birim testleri oluşturun.
- [.NET Core CLI Ile *xUnit* ve *F #* ](unit-testing-fsharp-with-dotnet-test.md)kullanarak birim testleri oluşturun.
- [ *XUnit* kullanarak birim testleri oluşturun ve .NET Core CLI *Visual Basic* ](unit-testing-visual-basic-with-dotnet-test.md).

:::zone-end
:::zone pivot="nunit"

- [.NET Core CLI Ile *NUnit* ve *C#* ](unit-testing-with-nunit.md)kullanarak birim testleri oluşturun.
- [.NET Core CLI Ile *NUnit* ve *F #* ](unit-testing-fsharp-with-nunit.md)kullanarak birim testleri oluşturun.
- [ *NUnit* ve .NET Core CLI *Visual Basic* ](unit-testing-visual-basic-with-nunit.md)kullanarak birim testleri oluşturun.

:::zone-end

Aşağıdaki makalelerde daha fazla bilgi edinebilirsiniz:

- Visual Studio Enterprise .NET Core için harika test araçları sunmaktadır. Daha fazla bilgi edinmek için [Live Unit Testing](/visualstudio/test/live-unit-testing) veya [kod kapsamına](https://github.com/Microsoft/vstest-docs/blob/master/docs/analyze.md#working-with-code-coverage) göz atın.
- Seçmeli birim testlerini çalıştırma hakkında daha fazla bilgi için bkz. [Seçmeli birim testlerini çalıştırma](selective-unit-tests.md)veya [Testleri Visual Studio ile dahil etme ve hariç tutma](/visualstudio/test/live-unit-testing#include-and-exclude-test-projects-and-test-methods).
- [.NET Core ve Visual Studio Ile xUnit kullanma](https://xunit.github.io/docs/getting-started-dotnet-core.html).
