---
title: Sanal üyeler
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- overridable members
- virtual members
- members [.NET Framework], virtual
ms.assetid: 8ff4eb97-0364-43ec-8a02-934b5cd94d19
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fa4227fc4476b86f07216650b22fccc25af7dd98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573097"
---
# <a name="virtual-members"></a>Sanal üyeler
Sanal üyeler, bu nedenle bir alt davranışını değiştirme geçersiz kılınabilir. Geri aramalar sağladıkları genişletilebilirlik bakımından oldukça benzer, ancak yürütme performans ve bellek tüketimi bakımından daha uygundur. Ayrıca, sanal üyeleri bir özel tür mevcut bir türle (uzmanlık) oluşturma gerektiren senaryolarda daha doğal eşitleyerek.  
  
 Sanal üyeler geri aramalar ve olayları daha iyi gerçekleştirir, ancak sanal olmayan yöntemler daha iyi gerçekleştirmeyin.  
  
 Sanal üyeler ana dezavantajı sanal üyesi davranışını yalnızca derleme zamanında değiştirilmesi olmasıdır. Bir geri çağırma davranışını çalışma zamanında değiştirilebilir.  
  
 Geri aramalar (ve belki de birden çok geri aramalar) gibi sanal üyeler tasarlamak, test ve çünkü sanal üyesi için herhangi bir çağrı beklenmedik şekilde geçersiz kılınabilir ve rasgele kod yürütebilir korumak maliyetlidir. Ayrıca, çok daha fazla çaba genellikle tasarlama ve bunları belgeleme maliyeti daha yüksek olacak şekilde sözleşme sanal üyeleri açıkça tanımlamak için gereklidir.  
  
 **X DO NOT** üyeleri sanal sürece bunu yapmak için iyi bir nedeniniz yoksa ve tasarlamak, test ve sanal üyeleri koruma ile ilgili tüm maliyetler farkında olun.  
  
 Bunlara uyumluluk bozmadan yapılabilir değişiklikler açısından daha az forgiving sanal üyeleridir. Çoğunlukla çağrıları sanal üyelerine içermesinden olmadığından Ayrıca, kullanıcılar sanal olmayan üyeler yavaştır.  
  
 **✓ CONSIDER** yalnızca kesinlikle gerekli nedir için genişletilebilirlik sınırlama.  
  
 **✓ DO** korumalı erişilebilirlik ortak erişilebilirlik sanal üyeleri için tercih eder. Genel üyeler genişletilebilirlik (gerekliyse) korumalı sanal üyesi çağırarak sağlamalıdır.  
  
 Bir sınıfın ortak üyelerine o sınıfın doğrudan Tüketiciler için işlev sağ kümesi sağlamalıdır. Sanal üyeler sınıflarında geçersiz kılınmak üzere tasarlanmıştır ve korumalı erişilebilirlik burada kullanılabilmeleri için tüm sanal genişletilebilirlik noktaları kapsam için harika bir yoludur.  
  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)  
 [Genişletilebilirlik için Tasarlama](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
