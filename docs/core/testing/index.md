---
title: .NET Core ve .NET Standard birim testi
description: Bu makalede, .NET Core ve .NET Standard projeleri için birim testine kısa bir genel bakış verebilirsiniz.
author: ardalis
ms.author: wiwagn
ms.date: 08/30/2017
ms.openlocfilehash: 1263bfe337b9d6609c0ca7df70aa299a61a7f1a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78157407"
---
# <a name="unit-testing-in-net-core-and-net-standard"></a>.NET Core ve .NET Standard birim testi

.NET Core, birim testleri oluşturmayı kolaylaştırır. Bu makalede, birim testleri tanınır ve diğer test türlerinden nasıl farklı olduklarını göstermektedir. Sayfanın altındaki bağlı kaynaklar, çözümünüze nasıl bir test projesi ekleyeceğinizgösteriz. Test projenizi ayarladıktan sonra, komut satırını veya Visual Studio'yu kullanarak birim testlerinizi çalıştırabilirsiniz.

**Bir ASP.NET Core** projesini test ediyorsanız, ASP.NET [Core'daki Tümleştirme testlerine](/aspnet/core/test/integration-tests#test-app-prerequisites)bakın.

.NET Core 2.0 ve daha sonra [.NET Standart 2.0'ı](../../standard/net-standard.md)destekler ve birim testlerini göstermek için kitaplıklarını kullanırız.

C#, F# ve Visual Basic için dahili .NET Core 2.0 ve daha sonra birim test proje şablonlarını kişisel projeniz için başlangıç noktası olarak kullanabilirsiniz.

## <a name="what-are-unit-tests"></a>Birim testleri nedir?

Otomatik testler olması, bir yazılım uygulamasının yazarlarının yapmak istediği şeyi yapmasını sağlamanın harika bir yoludur. Yazılım uygulamaları için birden çok türde test vardır. Bunlar tümleştirme testleri, web testleri, yükleme testleri ve diğerleri içerir. Birim testleri tek tek yazılım bileşenlerini ve yöntemlerini **test eder.** Birim testleri yalnızca geliştiricinin denetiminde kodu test etmelidir. Altyapı endişelerini test etmemeliler. Altyapı yla ilgili endişeler veritabanlarını, dosya sistemlerini ve ağ kaynaklarını içerir.

Ayrıca, testler yazmak için en iyi uygulamalar olduğunu unutmayın. Örneğin, [Test Odaklı Geliştirme (TDD),](https://deviq.com/test-driven-development/) bir birim testinin, denetlemesi gereken koddan önce yazıldığı zaman dır. TDD, biz yazmadan önce bir kitap için bir anahat oluşturmak gibidir. Geliştiricilerin daha basit, daha okunabilir ve verimli kod yazmalarına yardımcı olmak içindir.

> [!NOTE]
> ASP.NET ekibi, geliştiricilerin test [sınıfları](https://github.com/dotnet/aspnetcore/wiki/Engineering-guidelines#unit-tests-and-functional-tests) ve yöntemleri için iyi adlar bulabına yardımcı olmak için bu kuralları izler.

Birim testleri yazarken altyapıya bağımlılık lar getirmemeye çalışın. Bunlar testleri yavaş ve kırılgan hale getirmek ve tümleştirme testleri için ayrılmış olmalıdır. [Açık Bağımlılıklar İlkesi'ni](https://deviq.com/explicit-dependencies-principle/) izleyerek ve Bağımlılık [Enjeksiyonu'nu](/aspnet/core/fundamentals/dependency-injection)kullanarak uygulamanızdaki bu bağımlılıkları önleyebilirsiniz. Birim testlerinizi tümleştirme testlerinizden ayrı bir projede de saklayabilirsiniz. Bu, birim test projenizin altyapı paketlerine referansları veya bunlara bağlı olmamasını sağlar.

## <a name="next-steps"></a>Sonraki adımlar

.NET Core projelerinde birim testi hakkında daha fazla bilgi:

.NET Çekirdek birim test projeleri için desteklenir:

- [C #](../../csharp/index.yml)
- [F#](../../fsharp/index.yml)
- [Visual Basic](../../visual-basic/index.yml)

Ayrıca aralarından seçim yapabilirsiniz:

- [xBirim](https://xunit.github.io)
- [NUnit](https://nunit.org)
- [MSTest](https://github.com/Microsoft/testfx-docs)

Aşağıdaki izlenebilir liklerde daha fazla bilgi edinebilirsiniz:

- [.NET Core CLI ile *xUnit* ve *C#* ](unit-testing-with-dotnet-test.md)kullanarak birim testleri oluşturun.
- [.NET Core CLI ile *NUnit* ve *C#* kullanarak](unit-testing-with-nunit.md)birim testleri oluşturun.
- [.NET Core CLI ile *MSTest* ve *C#* kullanarak](unit-testing-with-mstest.md)birim testleri oluşturun.
- [.NET Core CLI ile *xUnit* ve *F#* kullanarak](unit-testing-fsharp-with-dotnet-test.md)birim testleri oluşturun.
- [.NET Core CLI ile *NUnit* ve *F#* kullanarak](unit-testing-fsharp-with-nunit.md)birim testleri oluşturun.
- [.NET Core CLI ile *MSTest* ve *F#* kullanarak](unit-testing-fsharp-with-mstest.md)birim testleri oluşturun.
- [ *.NET* Core CLI ile xUnit ve *Visual Basic* kullanarak](unit-testing-visual-basic-with-dotnet-test.md)birim testleri oluşturun.
- [.NET Core CLI ile *NUnit* ve *Visual Basic* kullanarak](unit-testing-visual-basic-with-nunit.md)birim testleri oluşturun.
- [ *.NET* Core CLI ile MSTest ve *Visual Basic* kullanarak](unit-testing-visual-basic-with-mstest.md)birim testleri oluşturun.

Aşağıdaki makalelerde daha fazla bilgi edinebilirsiniz:

- Visual Studio Enterprise ,NET Core için harika test araçları sunar. Daha fazla bilgi edinmek için [Canlı Birim Testi'ne](/visualstudio/test/live-unit-testing) veya [kod kapsamına](https://github.com/Microsoft/vstest-docs/blob/master/docs/analyze.md#working-with-code-coverage) göz atın.
- Seçici birim testlerinin nasıl çalıştırılabildiğini hakkında daha [including and excluding tests with Visual Studio](/visualstudio/test/live-unit-testing#include-and-exclude-test-projects-and-test-methods)fazla bilgi için [bkz.](selective-unit-tests.md)
- [.NET Core ve Visual Studio ile xUnit nasıl kullanılır.](https://xunit.github.io/docs/getting-started-dotnet-core.html)
