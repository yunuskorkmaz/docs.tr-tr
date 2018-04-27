---
title: Mühürleme
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- limiting extensibility
- classes [.NET Framework], sealing
- preventing customization
- sealed classes
ms.assetid: cc42267f-bb7a-427a-845e-df97408528d4
caps.latest.revision: 10
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8a9ea7fd4f5df08631231db08ba7943a9c131012
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="sealing"></a>Mühürleme
Nesne odaklı çerçeveleri özelliklerini geliştiriciler genişletmek ve framework tasarımcıların beklenmedik şekilde özelleştirin biridir. Güç ve Genişletilebilir tasarımının tehlike budur. Framework'ünüzün tasarlarken, bu nedenle, olduğu, istendiğinde Genişletilebilirliğe dikkatle tasarlamak için ve genişletilebilirlik tehlikeli olduğunda sınırlamak için çok önemlidir.  
  
 Genişletilebilirlik engeller güçlü bir mekanizma mühürleme. Sınıf veya tek tek üyeleri korumaya. Bir sınıf mühürleme kullanıcıların sınıfından devralan engeller. Üye mühürleme, kullanıcıların belirli bir üye önlemiş olursunuz.  
  
 **X yok** sınıfları Bunu yapmak için iyi bir neden olmadan mühürlemek.  
  
 Bir sınıf bir genişletilebilirlik senaryo düşündüğünüz yapılamıyor çünkü mühürleme iyi bir nedenle değil. Framework kullanıcılar kolaylık üye ekleme gibi çeşitli nonobvious nedeniyle sınıflardan devralmak ister. Bkz: [korumasız sınıfları](../../../docs/standard/design-guidelines/unsealed-classes.md) nonobvious nedenleri örnekleri için kullanıcıları bir türünden devralan istiyor.  
  
 Bir sınıf mühürleme iyi nedenleri şunlardır:  
  
-   Sınıfı statik bir sınıftır. Bkz: [statik sınıf tasarımı](../../../docs/standard/design-guidelines/static-class.md).  
  
-   Sınıfı, güvenlik açısından duyarlı gizli devralınan korunan üyeleri depolar.  
  
-   Çok sayıda sanal üye sınıfı devralır ve tek tek mühürleme maliyetini korumasız sınıfı bırakarak, ağır basıyor.  
  
-   Sınıf çok hızlı çalışma zamanı arama gerektiren bir özniteliktir. Korumalı öznitelikleri korumasız olanları daha biraz daha yüksek performans düzeyine sahip. Bkz: [öznitelikleri](../../../docs/standard/design-guidelines/attributes.md).  
  
 **X yok** korumalı türlerde korunan veya sanal üyeleri bildirme.  
  
 Tanımı gereği, korumalı türlerde kaynağından devralındı olamaz. Bu, korumalı türlerde korunan üyeleri çağrılamaz ve korumalı türlerde sanal yöntemleri geçersiz kılınamaz anlamına gelir.  
  
 **✓ DÜŞÜNÜN** kılmanız üyeleri mühürleme.  
  
 Sanal üyeler Tanıtımı sonuçlanabilir sorunları (ele [sanal üyeler](../../../docs/standard/design-guidelines/virtual-members.md)) biraz daha düşük bir derecede rağmen de geçersiz kılmaları uygulamak. Bir geçersiz kılma korumalı hale getirilmesiyle, devralma hiyerarşisinde o noktadan başlayarak bu sorunlardan ayrıntılarından korur.  
  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)  
 [Genişletilebilirlik için Tasarlama](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 [Mühürsüz Sınıflar](../../../docs/standard/design-guidelines/unsealed-classes.md)
