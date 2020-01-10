---
title: Sanal Üyeler
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- overridable members
- virtual members
- members [.NET Framework], virtual
ms.assetid: 8ff4eb97-0364-43ec-8a02-934b5cd94d19
ms.openlocfilehash: 2c1e6d9aeafa1c9d7ee4b0c2c626b6fd7be6cf99
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708977"
---
# <a name="virtual-members"></a>Sanal Üyeler
Sanal Üyeler geçersiz kılınabilir, böylece alt sınıfın davranışı değiştirilir. Bunlar, sağladıkları genişletilebilirlik açısından geri çağırmaları oldukça benzerdir ancak yürütme performansı ve bellek tüketimi açısından daha iyidir. Ayrıca, sanal Üyeler var olan türde (özelleşme) özel bir tür oluşturulmasını gerektiren senaryolarda daha doğal bir şekilde çalışır.  
  
 Sanal Üyeler geri çağırmaları ve olayları daha iyi gerçekleştirir, ancak sanal olmayan yöntemlerle daha iyi gerçekleştirmez.  
  
 Sanal üyelerin ana dezavantajı, sanal bir üyenin davranışının yalnızca derleme sırasında değiştirilebilmesi olabilir. Bir geri aramanın davranışı çalışma zamanında değiştirilebilir.  
  
 Bir sanal üyeye yapılan herhangi bir çağrı öngörülemeyen yollarla geçersiz kılınabileceğinden ve rastgele kod yürütebildiğinden, geri çağırmalar (ve geri çağırmaların daha fazlası) gibi sanal Üyeler tasarım, test ve bakım açısından maliyetlidir. Ayrıca, sanal üyelerin sözleşmesini açıkça tanımlamak için çok daha fazla çaba gerekir. bu nedenle, bunları tasarlama ve belgeleme maliyeti daha yüksektir.  
  
 **X DO NOT** üyeleri sanal sürece bunu yapmak için iyi bir nedeniniz yoksa ve tasarlamak, test ve sanal üyeleri koruma ile ilgili tüm maliyetler farkında olun.  
  
 Sanal üyeler, uyumluluk bozmadan bu kullanıcılara yapılabilecek değişikliklere göre daha az yasaklamalıdır. Ayrıca bunlar sanal olmayan üyelerden daha yavaştır, ancak sanal üyelere yapılan çağrılar satır içine alınmadı.  
  
 **✓ CONSIDER** yalnızca kesinlikle gerekli nedir için genişletilebilirlik sınırlama.  
  
 **✓ DO** korumalı erişilebilirlik ortak erişilebilirlik sanal üyeleri için tercih eder. Ortak Üyeler korumalı bir sanal üyeye çağırarak genişletilebilirlik (gerekliyse) sağlamalıdır.  
  
 Bir sınıfın ortak üyeleri, bu sınıfın doğrudan tüketicilere yönelik doğru işlevsellik kümesini sağlamalıdır. Sanal üyeler, alt sınıflarda geçersiz kılınabilecek şekilde tasarlanmıştır ve korumalı erişilebilirlik, tüm sanal genişletilebilirlik noktalarını, kullanılabilecekleri yere kapsamı için harika bir yoldur.  
  
 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
- [Genişletilebilirlik için Tasarlama](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
