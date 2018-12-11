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
author: KrzysztofCwalina
ms.openlocfilehash: fd1abdb4ff6f4850eea96bcfc3afbfe00a4ae56a
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53127699"
---
# <a name="sealing"></a>Mühürleme
Nesne yönelimli çerçeveleri özelliklerinin geliştiriciler genişletmek ve framework Designer'ların beklenmedik şekilde özelleştirin biridir. Güç ve Genişletilebilir tasarım tehlike budur. Framework'ünüzün tasarlarken, bu nedenle olduğu için genişletilebilirlik, istendiğinde dikkatlice tasarlayın ve tehlikeli olduğunda genişletilebilirlik sınırlamak için çok önemlidir.  
  
 Genişletilebilirlik engelleyen güçlü bir mekanizma mühürleme. Sınıf veya bireysel üyelere adımını. Bir sınıf mühürleme kullanıcıların sınıftan devralmasını engeller. Üye mühürleme, kullanıcıların belirli bir üye geçersiz kılmasını önler.  
  
 **X DO NOT** sınıfları Bunu yapmak için iyi bir neden olmadan mühürlemek.  
  
 Bir sınıf bir genişletilebilirlik senaryo düşündüğünüz olamaz çünkü mühürleme geçerli bir nedeniniz değil. Framework kullanıcılarını kolaylık üyeleri ekleme gibi çeşitli nonobvious nedeniyle sınıflardan devralmasına izin ister. Bkz: [Mühürsüz sınıflar](../../../docs/standard/design-guidelines/unsealed-classes.md) nonobvious nedenlerden örnekler için kullanıcıların bir türden devralmak istediğiniz.  
  
 Bir sınıf mühürleme için iyi nedenler şunlardır:  
  
-   Sınıfı statik bir sınıftır. Bkz: [statik sınıf tasarımı](../../../docs/standard/design-guidelines/static-class.md).  
  
-   Sınıfı, güvenlik açısından duyarlı gizli dizileri devralınan korunan üyeleri depolar.  
  
-   Sınıf çok sayıda sanal üyelerini devralır ve ayrı ayrı mühürleme maliyeti korumasız sınıfı bırakmanın basıyor.  
  
-   Sınıf çok hızlı çalışma zamanı arama gerektiren bir özniteliktir. Korumalı öznitelikleri korumasız yapılandırılanlardan biraz daha yüksek performans düzeyine sahip. bkz: [öznitelikleri](../../../docs/standard/design-guidelines/attributes.md).  
  
 **X DO NOT** korumalı türlerde korunan veya sanal üyeleri bildirme.  
  
 Tanımı gereği, mühürlenmiş türler öğesinden devralınamaz. Yani mühürlenmiş türler üzerindeki korunan üyeleri çağrılamaz ve mühürlenmiş türler üzerindeki sanal yöntemleri geçersiz kılınamaz.  
  
 **✓ CONSIDER** kılmanız üyeleri mühürleme.  
  
 Sanal üye eklemesini kaynaklanan sorunları (ele [sanal üyeleri](../../../docs/standard/design-guidelines/virtual-members.md)) ancak biraz daha düşük bir düzeyde de geçersiz kılmalar için geçerlidir. Bir geçersiz kılma mühürleme, devralma hiyerarşisinde o noktadan itibaren bu sorunlardan ayrıntılarından korur.  
  
 *Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: Kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 Addison Wesley Professional ile Microsoft Windows geliştirme serisi bir parçası olarak yayımlandı.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)  
- [Genişletilebilirlik için Tasarlama](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
- [Mühürsüz Sınıflar](../../../docs/standard/design-guidelines/unsealed-classes.md)
