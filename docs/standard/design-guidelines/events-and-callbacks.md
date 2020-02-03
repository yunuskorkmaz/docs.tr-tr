---
title: Etkinlikler ve Geri Aramalar
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- events [.NET Framework], extensibility
- methods [.NET Framework], callback
- callback methods
- callbacks
ms.assetid: 48b55c60-495f-4089-9396-97f9122bba7c
ms.openlocfilehash: 7dab759ba48104530fc41e46f6f2bba18d6c4456
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741662"
---
# <a name="events-and-callbacks"></a>Etkinlikler ve Geri Aramalar
Geri çağrılar, bir çerçevenin bir temsilci aracılığıyla Kullanıcı koduna geri çağırmasını sağlayan genişletilebilirlik noktalarıdır. Bu temsilciler genellikle bir yöntemin parametresi aracılığıyla çerçeveye geçirilir.

 Olaylar, temsilciyi (bir olay işleyicisi) sağlamak için uygun ve tutarlı sözdizimini destekleyen, geri çağırmaların özel bir durumdur. Ayrıca, Visual Studio 'nun bildirim tamamlama ve tasarımcıları, olay tabanlı API 'Leri kullanma konusunda yardım sağlar. (Bkz. [olay tasarımı](../../../docs/standard/design-guidelines/event.md).)

 ✔️, kullanıcıların çerçeve tarafından yürütülmesi için özel kod sağlamasına izin vermek için geri çağırmaları kullanmayı düşünün.

 ✔️, kullanıcıların, nesne odaklı tasarımı anlamak zorunda kalmadan bir Framework davranışını özelleştirmesini sağlamak için olayları kullanmayı düşünün.

 ✔️, daha geniş bir geliştirici yelpazdakilere daha tanıdık ve Visual Studio deyimin tamamlanmasına tümleştirildiği için düz geri çağırmalar üzerinde olayları tercih etme.

 ❌, performans duyarlı API 'lerde geri çağırmaları kullanmaktan kaçının.

 ✔️, geri çağırmalar ile API 'Leri tanımlarken özel temsilciler yerine yeni `Func<...>`, `Action<...>`veya `Expression<...>` türlerini kullanır.

 `Func<...>` ve `Action<...>` genel temsilcileri temsil eder. `Expression<...>`, derlenebilecek ve sonra çalışma zamanında çağrılabilen ancak aynı zamanda seri hale getirilebilir ve uzak işlemlere geçirilebilecek işlev tanımlarını temsil eder.

 ✔️, `Func<...>` ve `Action<...>` temsilcileri kullanmak yerine `Expression<...>`kullanmanın performansını ölçmenize ve anlayamalıdır.

 `Expression<...>` türler çoğu durumda `Func<...>` ve `Action<...>` temsilcilerle mantıksal olarak eşdeğerdir. Aralarındaki temel fark, temsilcilerin yerel işlem senaryolarında kullanılması amaçlanmasıdır; ifadeler, uzak bir işlem veya makinedeki ifadeyi değerlendirmek yararlı ve mümkün olduğu durumlar için tasarlanmıştır.

 ✔️, bir temsilciyi çağırarak, rastgele kod yürüttüğünü ve güvenlik, doğruluk ve uyumluluk repercusumu olduğunu anlamış olursunuz.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Genişletilebilirlik için Tasarlama](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
