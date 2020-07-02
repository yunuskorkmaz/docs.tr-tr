---
title: Sanal Üyeler
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- overridable members
- virtual members
- members [.NET Framework], virtual
ms.assetid: 8ff4eb97-0364-43ec-8a02-934b5cd94d19
ms.openlocfilehash: 918208bb44f84988b7fe903c589e82c7bf1f59e3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620774"
---
# <a name="virtual-members"></a>Sanal Üyeler
Sanal Üyeler geçersiz kılınabilir, böylece alt sınıfın davranışı değiştirilir. Bunlar, sağladıkları genişletilebilirlik açısından geri çağırmaları oldukça benzerdir ancak yürütme performansı ve bellek tüketimi açısından daha iyidir. Ayrıca, sanal Üyeler var olan türde (özelleşme) özel bir tür oluşturulmasını gerektiren senaryolarda daha doğal bir şekilde çalışır.

 Sanal Üyeler geri çağırmaları ve olayları daha iyi gerçekleştirir, ancak sanal olmayan yöntemlerle daha iyi gerçekleştirmez.

 Sanal üyelerin ana dezavantajı, sanal bir üyenin davranışının yalnızca derleme sırasında değiştirilebilmesi olabilir. Bir geri aramanın davranışı çalışma zamanında değiştirilebilir.

 Bir sanal üyeye yapılan herhangi bir çağrı öngörülemeyen yollarla geçersiz kılınabileceğinden ve rastgele kod yürütebildiğinden, geri çağırmalar (ve geri çağırmaların daha fazlası) gibi sanal Üyeler tasarım, test ve bakım açısından maliyetlidir. Ayrıca, sanal üyelerin sözleşmesini açıkça tanımlamak için çok daha fazla çaba gerekir. bu nedenle, bunları tasarlama ve belgeleme maliyeti daha yüksektir.

 ❌Bunu yapmak için iyi bir nedeniniz olmadığı için, Üyeler sanal yapmayın ve sanal üyelerin tasarlanması, sınanması ve saklanması ile ilgili tüm maliyetlerden haberdar olmanız gerekir.

 Sanal üyeler, uyumluluk bozmadan bu kullanıcılara yapılabilecek değişikliklere göre daha az yasaklamalıdır. Ayrıca bunlar sanal olmayan üyelerden daha yavaştır, ancak sanal üyelere yapılan çağrılar satır içine alınmadı.

 ✔️ genişletilebilirliği yalnızca kesinlikle gerekli olan şekilde sınırlandırmaya yarar.

 ✔️, sanal üyeler için genel erişilebilirlik üzerinden korumalı erişilebilirliği tercih eder. Ortak Üyeler korumalı bir sanal üyeye çağırarak genişletilebilirlik (gerekliyse) sağlamalıdır.

 Bir sınıfın ortak üyeleri, bu sınıfın doğrudan tüketicilere yönelik doğru işlevsellik kümesini sağlamalıdır. Sanal üyeler, alt sınıflarda geçersiz kılınabilecek şekilde tasarlanmıştır ve korumalı erişilebilirlik, tüm sanal genişletilebilirlik noktalarını, kullanılabilecekleri yere kapsamı için harika bir yoldur.

 *Bölüm &copy; 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve tasarım yönergeleri](index.md)
- [Genişletilebilirlik için Tasarlama](designing-for-extensibility.md)
