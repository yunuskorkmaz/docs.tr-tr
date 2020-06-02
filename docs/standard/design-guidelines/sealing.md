---
title: Mühürleme
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- limiting extensibility
- classes [.NET Framework], sealing
- preventing customization
- sealed classes
ms.assetid: cc42267f-bb7a-427a-845e-df97408528d4
ms.openlocfilehash: a54c68efb4ac114fe0e5a5712eca877bef35c103
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290116"
---
# <a name="sealing"></a>Mühürleme
Nesne yönelimli çerçevelerin özelliklerinden biri, geliştiricilerin bunları çerçeve tasarımcıları tarafından beklenmeyen yollarla genişletebileceği ve özelleştirebilleridir. Bu, Genişletilebilir tasarımın güç ve tehlike ' dir. Çatısını tasarladığınızda, bu, bu nedenle, gerektiğinde genişletilebilirlik için dikkatle tasarlamak ve çok önemli olduğunda genişletilebilirliği kısıtlamak için çok önemlidir.

 Genişletilebilirlik 'in mühürlediği güçlü bir mekanizma. Sınıfı ya da tek üyeleri mühürleyebilirsiniz. Bir sınıfı mühürleyen, kullanıcıların sınıfından devralmasını önler. Bir üyeyi mühürleyen, kullanıcıların belirli bir üyeyi geçersiz kılmasını önler.

 ❌Bunu yapmak için iyi bir neden olmadan sınıfları mühürlemeyin.

 Bir sınıfı mühürleyen bir genişletilebilirlik senaryosunu düşünmek iyi bir neden değil. Kullanışlı Üyeler ekleme gibi belirgin olmayan çeşitli nedenlerle sınıflardan devralması gibi Framework kullanıcıları. Kullanıcıların bir türden kalýtýmla devralması için açık olmayan nedenler örnekleri için bkz. [korumasız sınıflar](unsealed-classes.md) .

 Bir sınıfı mühürleyen olası nedenler şunlardır:

- Sınıfı statik bir sınıftır. Bkz. [statik sınıf tasarımı](static-class.md).

- Sınıfı, devralınan korunan üyelerde güvenlik duyarlı gizli dizileri depolar.

- Sınıf birçok sanal üyeyi devralır ve tek tek mühürlemek, sınıfın korumasız bırakılması avantajlarından yararlanır.

- Sınıfı çok hızlı çalışma zamanı araması gerektiren bir özniteliktir. Sealed öznitelikleri, korumasız olanlardan biraz daha yüksek performans düzeylerine sahiptir. Bkz. [öznitelikler](attributes.md).

 ❌Korumalı türler üzerinde korumalı veya sanal üye bildirme.

 Tanım olarak, korumalı türler öğesinden devralınamaz. Bu, korumalı türlerdeki korunan üyelerin çağrılabilmesi ve korumalı türlerde Sanal yöntemlerin geçersiz kılınamayacağını gösterir.

 ✔️, geçersiz kıldığınız üyeleri mühürden DEĞERLENDIRIN.

 Sanal üyelere ( [sanal Üyelerde](virtual-members.md)ele alınan) neden olan sorunlar, çok daha az bir ölçüde geçersiz kılmalara de uygulanır. Bir geçersiz kılmayı mühürleyen, devralma hiyerarşisindeki noktadan itibaren bu sorunlardan kalkan.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve tasarım yönergeleri](index.md)
- [Genişletilebilirlik için Tasarlama](designing-for-extensibility.md)
- [Korumasız sınıflar](unsealed-classes.md)
