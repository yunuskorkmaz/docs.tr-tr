---
title: Birim testi .NET Core
description: Birim testi hiç olmadığı kadar kolaylaştı. Birim testi .NET Core ve .NET Standard projeleri kullanacağınızı öğrenin.
author: ardalis
ms.author: wiwagn
ms.date: 08/30/2017
ms.openlocfilehash: 4a1d880da796aac40da93ca2513b6163200ca3c1
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43254796"
---
# <a name="unit-testing-in-net-core-and-net-standard"></a>.NET Core ve .NET standart birim testi

Böylece uygulamalarınız için birim testleri oluşturma zamankinden çok daha kolay unutmayın, Test Edilebilirlik ile .NET core tasarlanmıştır. Bu makalede kısaca birim testleri (ve diğer tür testlerin farkı) da tanıtılmaktadır. Bağlı kaynaklar, bir test projesi çözümünüze ekleyin ve ardından komut satırını veya Visual Studio kullanarak birim testleri çalıştırmak nasıl ekleyebileceğiniz gösterilmektedir.

.NET core 2.0 destekler [.NET Standard 2.0](../../standard/net-standard.md). Birim testi Bu bölümde göstermek için kullanılan kitaplıklar .NET Standard'ı kullanan ve diğer proje türleri de çalışır.

.NET Core 2.0 ile başlayarak, C#, F # ve Visual Basic için birim test proje şablonları vardır.

## <a name="getting-started-with-testing"></a>Test ile çalışmaya başlama

Otomatikleştirilmiş testleri paketi olan kendi yazarlar Bunu yapmak için amaçlanan bir yazılım uygulaması mu emin olmak için en iyi yollarından biridir. Tümleştirme testleri, web testleri, yük testleri ve diğerleri dahil olmak üzere, yazılım uygulamaları için testleri farklı tür vardır. Tek tek yazılım bileşenlerini ve yöntemleri test birim testleri en düşük düzey testlerdir. Birim testleri, yalnızca kod geliştiricinin denetimi içinde test etmeniz gerekir ve veritabanları, dosya sistemleri veya ağ kaynakları gibi altyapıyla ilgili endişelerini test yok. Kullanarak birim testleri yazılabilir [Test odaklı geliştirme (TDD)](http://deviq.com/test-driven-development/), ya da kendi doğruluğunu onaylamak için mevcut kodu eklenebilir. Değişikliklerinizi projenin paylaşılan kod deposuna göndermeden önce bunları yüzlerce çalıştırabilir olmak isteyeceğiniz ideal olarak her iki durumda da, bunlar küçük, iyi adlandırılmış ve daha hızlı olmalıdır.

> [!NOTE]
> Geliştiriciler genellikle kendi test sınıflar ve yöntemler için iyi adlarla yakında ile uğraşır. ASP.NET ürün ekibine bir başlangıç noktası olarak aşağıdaki [bu kuralları](https://github.com/aspnet/Home/wiki/Engineering-guidelines#unit-tests-and-functional-tests).

Birim testleri yazılırken altyapı bağımlılıkları yanlışlıkla açmadığınızdan dikkatli olun. Bunlar testlerden daha yavaş ve kırılgan daha eğilimindedir ve bu nedenle tümleştirme testleri için ayrılmış olması gerekir. Takip ederek, uygulama kodunuzda bu gizli bağımlılıklar kaçınabilirsiniz [açık bağımlılıkları İlkesi](http://deviq.com/explicit-dependencies-principle/) ve kullanarak [bağımlılık ekleme](/aspnet/core/fundamentals/dependency-injection) Framework'ten bağımlılıklarınızı istemek için. Ayrıca, Birim testlerinizin ayrı bir projede, tümleştirme testleri tutun ve altyapı paketleri, birim testi projesi başvuruları veya bağımlılıkları sahip olun.

Birim testi .NET Core projelerinde hakkında daha fazla bilgi edinin:

.NET Core birim testi projeleri için desteklenen [C#](../../csharp/index.md), [F #](../../fsharp/index.md) ve [Visual Basic](../../visual-basic/index.md). Arasından seçim yapabilirsiniz [xUnit](http://xunit.github.io), [NUnit](http://nunit.org) ve [MSTest](https://github.com/Microsoft/vstest-docs).

Bu izlenecek yollar birleşimler hakkında bilgi edinebilirsiniz:

* Kullanarak birim testleri oluşturma [ *xUnit* ve *C#* .NET Core CLI ile](unit-testing-with-dotnet-test.md).
* Kullanarak birim testleri oluşturma [ *NUnit* ve *C#* .NET Core CLI ile](unit-testing-with-nunit.md).
* Kullanarak birim testleri oluşturma [ *MSTest* ve *C#* .NET Core CLI ile](unit-testing-with-mstest.md).
* Kullanarak birim testleri oluşturma [ *xUnit* ve *F #* .NET Core CLI ile](unit-testing-fsharp-with-dotnet-test.md).
* Kullanarak birim testleri oluşturma [ *NUnit* ve *F #* .NET Core CLI ile](unit-testing-fsharp-with-nunit.md).
* Kullanarak birim testleri oluşturma [ *MSTest* ve *F #* .NET Core CLI ile](unit-testing-fsharp-with-mstest.md).
* Kullanarak birim testleri oluşturma [ *xUnit* ve *Visual Basic* .NET Core CLI ile](unit-testing-visual-basic-with-dotnet-test.md).
* Kullanarak birim testleri oluşturma [ *NUnit* ve *Visual Basic* .NET Core CLI ile](unit-testing-visual-basic-with-nunit.md).
* Kullanarak birim testleri oluşturma [ *MSTest* ve *Visual Basic* .NET Core CLI ile](unit-testing-visual-basic-with-mstest.md).

Farklı diller için sınıf kitaplıkları seçebilirsiniz ve kitaplıkları, birim testi. Nasıl karıştırma ve eşleştirme izlenecek yollar yukarıda anılan öğrenebilirsiniz.

* Visual Studio Enterprise, .NET Core için harika bir test araçları sunar. Kullanıma [Live Unit Testing](/visualstudio/test/live-unit-testing) veya [kod kapsamı](https://github.com/Microsoft/vstest-docs/blob/master/docs/analyze.md#working-with-code-coverage) daha fazla bilgi için.
* Ek bilgi ve seçmeli birim testi filtreleme kullanma hakkında daha fazla örnek için bkz. [seçmeli birim testleri çalıştırma](selective-unit-tests.md), veya [dahil etme ve dışlama Visual Studio ile testleri](/visualstudio/test/live-unit-testing#include-and-exclude-test-projects-and-test-methods).
* XUnit takım gösteren bir öğretici yazmıştır [xUnit .NET Core ve Visual Studio ile nasıl kullanılacağını](http://xunit.github.io/docs/getting-started-dotnet-core.html).
