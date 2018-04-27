---
title: Sanal üyeler
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- overridable members
- virtual members
- members [.NET Framework], virtual
ms.assetid: 8ff4eb97-0364-43ec-8a02-934b5cd94d19
caps.latest.revision: 9
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 1b7abe1dbeb7f4888dd8ee4001b410cc583935c4
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="virtual-members"></a>Sanal üyeler
Sanal üyeler, bu nedenle bir alt davranışını değiştirme geçersiz kılınabilir. Geri aramalar sağladıkları genişletilebilirlik bakımından oldukça benzer, ancak yürütme performans ve bellek tüketimi bakımından daha uygundur. Ayrıca, sanal üyeleri bir özel tür mevcut bir türle (uzmanlık) oluşturma gerektiren senaryolarda daha doğal eşitleyerek.  
  
 Sanal üyeler geri aramalar ve olayları daha iyi gerçekleştirir, ancak sanal olmayan yöntemler daha iyi gerçekleştirmeyin.  
  
 Sanal üyeler ana dezavantajı sanal üyesi davranışını yalnızca derleme zamanında değiştirilmesi olmasıdır. Bir geri çağırma davranışını çalışma zamanında değiştirilebilir.  
  
 Geri aramalar (ve belki de birden çok geri aramalar) gibi sanal üyeler tasarlamak, test ve çünkü sanal üyesi için herhangi bir çağrı beklenmedik şekilde geçersiz kılınabilir ve rasgele kod yürütebilir korumak maliyetlidir. Ayrıca, çok daha fazla çaba genellikle tasarlama ve bunları belgeleme maliyeti daha yüksek olacak şekilde sözleşme sanal üyeleri açıkça tanımlamak için gereklidir.  
  
 **X yok** üyeleri sanal sürece bunu yapmak için iyi bir nedeniniz yoksa ve tasarlamak, test ve sanal üyeleri koruma ile ilgili tüm maliyetler farkında olun.  
  
 Bunlara uyumluluk bozmadan yapılabilir değişiklikler açısından daha az forgiving sanal üyeleridir. Çoğunlukla çağrıları sanal üyelerine içermesinden olmadığından Ayrıca, kullanıcılar sanal olmayan üyeler yavaştır.  
  
 **✓ DÜŞÜNÜN** yalnızca kesinlikle gerekli nedir için genişletilebilirlik sınırlama.  
  
 **✓ YAPMAK** korumalı erişilebilirlik ortak erişilebilirlik sanal üyeleri için tercih eder. Genel üyeler genişletilebilirlik (gerekliyse) korumalı sanal üyesi çağırarak sağlamalıdır.  
  
 Bir sınıfın ortak üyelerine o sınıfın doğrudan Tüketiciler için işlev sağ kümesi sağlamalıdır. Sanal üyeler sınıflarında geçersiz kılınmak üzere tasarlanmıştır ve korumalı erişilebilirlik burada kullanılabilmeleri için tüm sanal genişletilebilirlik noktaları kapsam için harika bir yoludur.  
  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)  
 [Genişletilebilirlik için Tasarlama](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
