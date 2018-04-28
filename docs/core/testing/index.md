---
title: Birim testi .NET çekirdek
description: Birim testi hiç daha kolay olmamıştı. Birim testi .NET Core ve .NET standart projelerinde kullanma konusuna bakın.
author: ardalis
ms.author: wiwagn
ms.date: 08/30/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 652378bc6518218d25d2db1b5d1eceb60e53cde5
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="unit-testing-in-net-core-and-net-standard"></a>Birim .NET Core ve .NET standart testi

Böylece, uygulamalarınız için birim testleri oluşturma zamankinden daha kolay .NET core unutmayın, sınanabilirlik ile tasarlanmıştır. Bu makalede kısaca birim testleri (ve bunların diğer tür testlerin farklılıklar) sunar. Bağlı kaynaklar, bir test projesi çözümünüze ekleyin ve ardından komut satırından veya Visual Studio kullanarak birim testleri çalıştırma göstermektedir.

.NET core 2.0 destekleyen [.NET standart 2.0](../../standard/net-standard.md). Birim testi Bu bölümde göstermek için kullanılan kitaplıkları standart .NET kullanır ve diğer proje türleri de çalışır.

.NET Core 2.0 ile başlayarak, Visual Basic ve F # yanı sıra C# için birim testi projesi şablonları vardır.

## <a name="getting-started-with-testing"></a>Testi ile çalışmaya başlama

Otomatikleştirilmiş testleri dizisi sahip ne kendi yazarlar Bunu yapmak için hedeflenen yazılım uygulama olmadığından emin olmak için en iyi yollarından biri. Testleri tümleştirme testleri, web testleri, yük testleri ve diğerleri de dahil olmak üzere yazılım uygulamaları için farklı tür vardır. Bağımsız yazılım bileşenleri veya yöntemlerini test birim testleri en düşük düzey testleri ' dir. Birim testleri Geliştirici denetim içindeki kod yalnızca test etmeniz gerekir ve veritabanları, dosya sistemleri veya ağ kaynakları gibi altyapı sorunları sınamalısınız değil. Birim testleri kullanarak yazılabilir [Test güdümlü geliştirme (TDD)](http://deviq.com/test-driven-development/), ya da kendi doğruluğunu onaylamak için var olan kodu eklenebilir. Değişikliklerinizi projenin paylaşılan kod depoya göndermeden önce bunları yüzlerce çalıştırılabilmesi için istediğiniz ideal olarak bu yana her iki durumda da, bunlar küçük, iyi adlandırılmış ve hızlı olması gerekir.

> [!NOTE]
> Geliştiriciler genellikle kendi test sınıflar ve yöntemler için iyi adlarıyla yaklaşan ile güçlük. Bir başlangıç noktası olarak ASP.NET ürün ekibi izleyen [bu kuralları](https://github.com/aspnet/Home/wiki/Engineering-guidelines#unit-tests-and-functional-tests).

Birim testleri yazma, altyapı bağımlılıkları yanlışlıkla tanıtmak yok dikkatli olun. Bu testleri daha yavaş ve daha kırılır olun eğilimindedir ve böylece tümleştirme testleri için ayrılmış olması gerekir. İzleyerek uygulama kodunuzda bu gizli bağımlılıklar önleyebilirsiniz [açık bağımlılıkları ilkesine](http://deviq.com/explicit-dependencies-principle/) ve kullanarak [bağımlılık ekleme](/aspnet/core/fundamentals/dependency-injection) , bağımlılıkları çerçevesinden istemek için. Birim testleri ayrı bir projede tümleştirme testlerinizi tutmak ve birim testi projesi altyapı paketleri başvurular veya bağımlılıkları yok emin olun.

Birim testi .NET Core projelerinde hakkında daha fazla bilgi edinin:

İçin desteklenen birim testi projelerini .NET Core için [C#](../../csharp/index.md), [F #](../../fsharp/index.md) ve [Visual Basic](../../visual-basic/index.md). Arasından seçim yapabilirsiniz [xUnit](http://xunit.github.io), [NUnit](http://nunit.org) ve [mstest'i](https://github.com/Microsoft/vstest-docs).

Bu izlenecek yollar kurulumundaki birleşimler hakkında bilgi edinebilirsiniz:

* Kullanarak birim testleri oluşturma [ *XUnit* ve *C#* .NET Core CLI ile](unit-testing-with-dotnet-test.md).
* Kullanarak birim testleri oluşturma [ *NUnit* ve *C#* .NET Core CLI ile](unit-testing-with-nunit.md).
* Kullanarak birim testleri oluşturma [ *mstest'i* ve *C#* .NET Core CLI ile](unit-testing-with-mstest.md).
* Kullanarak birim testleri oluşturma [ *XUnit* ve *F #* .NET Core CLI ile](unit-testing-fsharp-with-dotnet-test.md).
* Kullanarak birim testleri oluşturma [ *NUnit* ve *F #* .NET Core CLI ile](unit-testing-fsharp-with-nunit.md).
* Kullanarak birim testleri oluşturma [ *mstest'i* ve *F #* .NET Core CLI ile](unit-testing-fsharp-with-mstest.md).
* Kullanarak birim testleri oluşturma [ *XUnit* ve *Visual Basic* .NET Core CLI ile](unit-testing-visual-basic-with-dotnet-test.md).
* Kullanarak birim testleri oluşturma [ *NUnit* ve *Visual Basic* .NET Core CLI ile](unit-testing-visual-basic-with-nunit.md).
* Kullanarak birim testleri oluşturma [ *mstest'i* ve *Visual Basic* .NET Core CLI ile](unit-testing-visual-basic-with-mstest.md).

Farklı diller için sınıf kitaplıkları seçebilir ve kitaplıkları, birim testi. Nasıl karıştırma ve eşleşen izlenecek yollar yukarıda başvurulan öğrenebilirsiniz.

* Visual Studio Enterprise .NET Core için harika test araçları sunar. Kullanıma [Canlı birim testi](/visualstudio/test/live-unit-testing) veya [kod kapsamı](https://github.com/Microsoft/vstest-docs/blob/master/docs/analyze.md#working-with-code-coverage) daha fazla bilgi için.
* Ek bilgi ve seçmeli birim testi filtreleme kullanma hakkında örnekler için bkz: [seçmeli birim testlerini çalıştırma](selective-unit-tests.md), veya [ve Visual Studio ile testleri hariç dahil](/visualstudio/test/live-unit-testing#including-and-excluding-test-projects-and-test-methods).
* XUnit takım gösteren bir öğretici yazmıştır [xUnit .NET Core ve Visual Studio ile nasıl kullanılacağı](http://xunit.github.io/docs/getting-started-dotnet-core.html).
