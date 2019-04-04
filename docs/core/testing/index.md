---
title: .NET Core ve .NET standart birim testi
description: Bu makalede, birim testi .NET Core ve .NET Standard projeleri için kısa bir genel bakış sağlar.
author: ardalis
ms.author: wiwagn
ms.date: 08/30/2017
ms.custom: seodec18
ms.openlocfilehash: 73667843452bbcab52a8cd4aa7906beecc095677
ms.sourcegitcommit: 462dc41a13942e467984e48f4018d1f79ae67346
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58185512"
---
# <a name="unit-testing-in-net-core-and-net-standard"></a>.NET Core ve .NET standart birim testi

.NET core birim testleri oluşturmayı kolay hale getirir. Bu makalede, birim testleri tanıtır ve diğer tür testlerin farkı göstermektedir. Sayfanın alt kısmındaki bağlı kaynaklar, bir test projesi çözümünüze ekleyin gösterilmektedir. Test projenizin ayarladıktan sonra komut satırında veya Visual Studio kullanarak birim testleri çalıştırmak mümkün olacaktır.

.NET core 2.0 ve sonraki [.NET Standard 2.0](../../standard/net-standard.md), ve kitaplıklarını birim testleri göstermek için kullanacağız.

Yerleşik .NET Core 2.0 ve sonraki birim test projesi şablonları kullanabilmek için C#, F# ve Visual Basic kişisel projeniz için bir başlangıç noktası olarak.

## <a name="what-are-unit-tests"></a>Birim testleri nelerdir?

Otomatikleştirilmiş testleri sahip bir yazılım uygulaması ne yapması, yazarlar düşündüğünüz mu emin olmak için harika bir yoludur. Yazılım uygulamaları için testleri birden çok tür vardır. Bunlar tümleştirme testleri, web testleri, yük testleri ve diğerleri de içerir. **Birim testleri** bireysel yazılım bileşenlerini ve yöntemleri test edin. Birim testleri yalnızca geliştiricinin denetimi içindeki kod test etmeniz gerekir. Bunlar, altyapıdan kaynaklanan yüklerden test. Altyapıdan kaynaklanan yüklerden veritabanları, dosya sistemi ve ağ kaynaklarını içerir. 

Ayrıca unutmayın, testleri yazmak için en iyi yöntemler. Örneğin, [Test odaklı geliştirme (TDD)](https://deviq.com/test-driven-development/) birim testi geliyordu denetlemek için önce kodu yazıldığı durumdur. TDD biz yazmadan önce bir kitap için bir ana hat oluşturma gibi bağlıdır. Geliştiriciler daha basit, daha okunabilir ve verimli kod yazmak için tasarlanmıştır. 

> [!NOTE]
> ASP.NET takım aşağıdaki [bu kuralları](https://github.com/aspnet/Home/wiki/Engineering-guidelines#unit-tests-and-functional-tests) geliştiricilerin test sınıflar ve yöntemler için iyi adlarla bulabilmesine yardımcı olmak için.

Altyapı bağımlı birim testleri yazılırken İstemediğimiz deneyin. Bunlar yavaş ve kırılgan testleri yapın ve tümleştirme testleri için ayrılmış olması gerekir. İzleyerek uygulamanızda Bu bağımlılıklar kaçınabilirsiniz [açık bağımlılıkları İlkesi](https://deviq.com/explicit-dependencies-principle/) ve kullanarak [bağımlılık ekleme](/aspnet/core/fundamentals/dependency-injection). Ayrıca, tümleştirme testleri ayrı bir projede Birim testlerinizin tutabilirsiniz. Bu, birim testi projesi başvuruları veya bağımlılıkları altyapı paketleri yok sağlar.

## <a name="next-steps"></a>Sonraki adımlar

Birim testi .NET Core projelerinde hakkında daha fazla bilgi:

.NET core birim testi projeleri için desteklenir:
* [C#](../../csharp/index.md)
* [F#](../../fsharp/index.md)
* [Visual Basic](../../visual-basic/index.md) 

Arasında seçim yapabilirsiniz:
* [xUnit](https://xunit.github.io) 
* [NUnit](https://nunit.org)
* [MSTest](https://github.com/Microsoft/testfx-docs)

Aşağıdaki izlenecek yollardaki daha fazla bilgi edinebilirsiniz:

* Kullanarak birim testleri oluşturma [ *xUnit* ve *C#* .NET Core CLI ile](unit-testing-with-dotnet-test.md).
* Kullanarak birim testleri oluşturma [ *NUnit* ve *C#* .NET Core CLI ile](unit-testing-with-nunit.md).
* Kullanarak birim testleri oluşturma [ *MSTest* ve *C#* .NET Core CLI ile](unit-testing-with-mstest.md).
* Kullanarak birim testleri oluşturma [ *xUnit* ve *F#* .NET Core CLI ile](unit-testing-fsharp-with-dotnet-test.md).
* Kullanarak birim testleri oluşturma [ *NUnit* ve *F#* .NET Core CLI ile](unit-testing-fsharp-with-nunit.md).
* Kullanarak birim testleri oluşturma [ *MSTest* ve *F#* .NET Core CLI ile](unit-testing-fsharp-with-mstest.md).
* Kullanarak birim testleri oluşturma [ *xUnit* ve *Visual Basic* .NET Core CLI ile](unit-testing-visual-basic-with-dotnet-test.md).
* Kullanarak birim testleri oluşturma [ *NUnit* ve *Visual Basic* .NET Core CLI ile](unit-testing-visual-basic-with-nunit.md).
* Kullanarak birim testleri oluşturma [ *MSTest* ve *Visual Basic* .NET Core CLI ile](unit-testing-visual-basic-with-mstest.md).

Aşağıdaki makalelerde daha fazla bilgi edinebilirsiniz:

* Visual Studio Enterprise, .NET Core için harika bir test araçları sunar. Kullanıma [Live Unit Testing](/visualstudio/test/live-unit-testing) veya [kod kapsamı](https://github.com/Microsoft/vstest-docs/blob/master/docs/analyze.md#working-with-code-coverage) daha fazla bilgi için.
* Seçmeli birim testlerin nasıl çalıştırılacağı hakkında daha fazla bilgi için bkz. [seçmeli birim testleri çalıştırma](selective-unit-tests.md), veya [dahil etme ve dışlama Visual Studio ile testleri](/visualstudio/test/live-unit-testing#include-and-exclude-test-projects-and-test-methods).
* [Visual Studio ve .NET Core ile xUnit kullanmayı](https://xunit.github.io/docs/getting-started-dotnet-core.html).
