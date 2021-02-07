---
description: 'Daha fazla bilgi edinin: mühürleme'
title: Mühürleme
ms.date: 10/22/2008
helpviewer_keywords:
- limiting extensibility
- classes [.NET Framework], sealing
- preventing customization
- sealed classes
ms.assetid: cc42267f-bb7a-427a-845e-df97408528d4
ms.openlocfilehash: 94673f793aa7373e1076e13cbda900fba83786f6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731727"
---
# <a name="sealing"></a>Mühürleme

Nesne yönelimli çerçevelerin özelliklerinden biri, geliştiricilerin bunları çerçeve tasarımcıları tarafından beklenmeyen yollarla genişletebileceği ve özelleştirebilleridir. Bu, Genişletilebilir tasarımın güç ve tehlike ' dir. Çatısını tasarladığınızda, bu, bu nedenle, gerektiğinde genişletilebilirlik için dikkatle tasarlamak ve çok önemli olduğunda genişletilebilirliği kısıtlamak için çok önemlidir.

 Genişletilebilirlik 'in mühürlediği güçlü bir mekanizma. Sınıfı ya da tek üyeleri mühürleyebilirsiniz. Bir sınıfı mühürleyen, kullanıcıların sınıfından devralmasını önler. Bir üyeyi mühürleyen, kullanıcıların belirli bir üyeyi geçersiz kılmasını önler.

 ❌ Bunu yapmak için iyi bir neden olmadan sınıfları mühürlemeyin.

 Bir sınıfı mühürleyen bir genişletilebilirlik senaryosunu düşünmek iyi bir neden değil. Kullanışlı Üyeler ekleme gibi belirgin olmayan çeşitli nedenlerle sınıflardan devralması gibi Framework kullanıcıları. Kullanıcıların bir türden kalýtýmla devralması için açık olmayan nedenler örnekleri için bkz. [korumasız sınıflar](unsealed-classes.md) .

 Bir sınıfı mühürleyen olası nedenler şunlardır:

- Sınıfı statik bir sınıftır. Bkz. [statik sınıf tasarımı](static-class.md).

- Sınıfı, devralınan korunan üyelerde güvenlik duyarlı gizli dizileri depolar.

- Sınıf birçok sanal üyeyi devralır ve tek tek mühürlemek, sınıfın korumasız bırakılması avantajlarından yararlanır.

- Sınıfı çok hızlı çalışma zamanı araması gerektiren bir özniteliktir. Sealed öznitelikleri, korumasız olanlardan biraz daha yüksek performans düzeylerine sahiptir. Bkz. [öznitelikler](attributes.md).

 ❌ Korumalı türler üzerinde korumalı veya sanal üye bildirme.

 Tanım olarak, korumalı türler öğesinden devralınamaz. Bu, korumalı türlerdeki korunan üyelerin çağrılabilmesi ve korumalı türlerde Sanal yöntemlerin geçersiz kılınamayacağını gösterir.

 ✔️, geçersiz kıldığınız üyeleri mühürden DEĞERLENDIRIN.

 Sanal üyelere ( [sanal Üyelerde](virtual-members.md)ele alınan) neden olan sorunlar, çok daha az bir ölçüde geçersiz kılmalara de uygulanır. Bir geçersiz kılmayı mühürleyen, devralma hiyerarşisindeki noktadan itibaren bu sorunlardan kalkan.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve tasarım yönergeleri](index.md)
- [Genişletilebilirlik için Tasarlama](designing-for-extensibility.md)
- [Korumasız sınıflar](unsealed-classes.md)
