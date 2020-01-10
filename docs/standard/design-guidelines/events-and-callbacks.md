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
ms.openlocfilehash: 80c16e29f1d8a0653295ebc3cf25be6fb78b7dc9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709419"
---
# <a name="events-and-callbacks"></a>Etkinlikler ve Geri Aramalar
Geri çağrılar, bir çerçevenin bir temsilci aracılığıyla Kullanıcı koduna geri çağırmasını sağlayan genişletilebilirlik noktalarıdır. Bu temsilciler genellikle bir yöntemin parametresi aracılığıyla çerçeveye geçirilir.  
  
 Olaylar, temsilciyi (bir olay işleyicisi) sağlamak için uygun ve tutarlı sözdizimini destekleyen, geri çağırmaların özel bir durumdur. Ayrıca, Visual Studio 'nun bildirim tamamlama ve tasarımcıları, olay tabanlı API 'Leri kullanma konusunda yardım sağlar. (Bkz. [olay tasarımı](../../../docs/standard/design-guidelines/event.md).)  
  
 **✓ CONSIDER** çerçevesi tarafından yürütülecek özel kod sağlamak için kullanıcıların izin vermek için geri çağırmaları kullanma.  
  
 **✓ CONSIDER** framework nesne odaklı tasarım anlamak için gerek kalmadan davranışını özelleştirmek kullanıcıların olayları kullanarak.  
  
 **✓ DO** daha geniş bir grup geliştiriciler için tanıdık ve Visual Studio deyim tamamlama ile tümleşik olduğundan olayları düz geri aramalar tercih.  
  
 **X AVOID** geri aramalar performans duyarlı API'leri kullanarak.  
  
 **✓ DO** yeni `Func<...>`, `Action<...>`, veya `Expression<...>` API'leri ile geri aramalar tanımlarken özel temsilciler yerine türleri.  
  
 `Func<...>` ve `Action<...>` genel temsilcileri temsil eder. `Expression<...>`, derlenebilecek ve sonra çalışma zamanında çağrılabilen ancak aynı zamanda seri hale getirilebilir ve uzak işlemlere geçirilebilecek işlev tanımlarını temsil eder.  
  
 **✓ DO** ölçmek ve performans etkilerini kullanmanın `Expression<...>`, yerine `Func<...>` ve `Action<...>` temsilciler.  
  
 `Expression<...>` türler çoğu durumda `Func<...>` ve `Action<...>` temsilcilerle mantıksal olarak eşdeğerdir. Aralarındaki temel fark, temsilcilerin yerel işlem senaryolarında kullanılması amaçlanmasıdır; ifadeler, uzak bir işlem veya makinedeki ifadeyi değerlendirmek yararlı ve mümkün olduğu durumlar için tasarlanmıştır.  
  
 **✓ DO** temsilci çağırarak rastgele kod yürütülmekte olduğunu anlamak ve güvenlik, doğruluk ve uyumluluk varsa sahip olabilir.  
  
 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Genişletilebilirlik için Tasarlama](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
