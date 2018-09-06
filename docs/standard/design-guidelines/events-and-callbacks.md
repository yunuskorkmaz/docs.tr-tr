---
title: Etkinlikler ve geri aramalar
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- events [.NET Framework], extensibility
- methods [.NET Framework], callback
- callback methods
- callbacks
ms.assetid: 48b55c60-495f-4089-9396-97f9122bba7c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 390c12af7107bb78fc261c55ea15390cf9eaa5b7
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43862955"
---
# <a name="events-and-callbacks"></a>Etkinlikler ve geri aramalar
Geri çağırmalar, geri bir temsilci yoluyla kullanıcı kodu çağırmak bir çerçeve izin genişletilebilirlik noktalarıdır. Bu Temsilciler, genellikle bir yöntemin bir parametresi aracılığıyla framework geçirilir.  
  
 Temsilci (bir olay işleyicisi) sağlama için kullanışlı ve tutarlı bir söz dizimi destekleyen bir özel durum geri çağırmalar olaylardır. Ayrıca, Visual Studio'nun deyim tamamlama ve tasarımcılar olay-tabanlı API'ler kullanarak Yardım sağlayabilir. (Bkz [olay tasarımı](../../../docs/standard/design-guidelines/event.md).)  
  
 **✓ CONSIDER** çerçevesi tarafından yürütülecek özel kod sağlamak için kullanıcıların izin vermek için geri çağırmaları kullanma.  
  
 **✓ CONSIDER** framework nesne odaklı tasarım anlamak için gerek kalmadan davranışını özelleştirmek kullanıcıların olayları kullanarak.  
  
 **✓ DO** daha geniş bir grup geliştiriciler için tanıdık ve Visual Studio deyim tamamlama ile tümleşik olduğundan olayları düz geri aramalar tercih.  
  
 **X AVOID** geri aramalar performans duyarlı API'leri kullanarak.  
  
 **✓ DO** yeni `Func<...>`, `Action<...>`, veya `Expression<...>` API'leri ile geri aramalar tanımlarken özel temsilciler yerine türleri.  
  
 `Func<...>` ve `Action<...>` genel temsilciler temsil eder. `Expression<...>` derlenmiş ve daha sonra ancak çalışma zamanında da çağrılan temsil işlev tanımları sıralanabilir ve uzak işlemler geçirildi.  
  
 **✓ DO** ölçmek ve performans etkilerini kullanmanın `Expression<...>`, yerine `Func<...>` ve `Action<...>` temsilciler.  
  
 `Expression<...>` Çoğu durumda mantıksal eşdeğer türleridir `Func<...>` ve `Action<...>` temsilciler. Aralarındaki temel fark, temsilciler yerel işlem senaryolarda kullanılması amaçlanmıştır olan; ifadeleri yararlı ve uzak işlem veya makine ifadeyi değerlendirmek mümkün olduğu durumlarda yöneliktir.  
  
 **✓ DO** temsilci çağırarak rastgele kod yürütülmekte olduğunu anlamak ve güvenlik, doğruluk ve uyumluluk varsa sahip olabilir.  
  
 *Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Genişletilebilirlik için Tasarlama](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
