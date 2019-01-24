---
title: Korumalı üyeler
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- members [.NET Framework], protected
- protected members
- classes [.NET Framework], unsealed
- classes [.NET Framework], protected members
- unsealed classes
- customizing class behavior
ms.assetid: aa0b58ee-3956-494d-ab48-471ae5db8740
author: KrzysztofCwalina
ms.openlocfilehash: 7d940f10799df2efc6c6d031781e1ef7cf777dd6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559352"
---
# <a name="protected-members"></a>Korumalı üyeler
Korumalı üyeler başlarına herhangi bir genişletilebilirlik sağlamaz, ancak bunlar sınıflara aracılığıyla genişletilebilirlik daha güçlü hale getirebilirsiniz. Ana ortak arabirim gereksiz derecede karmaşık olmadan Gelişmiş özelleştirme seçeneklerini göstermek için kullanılabilir.  
  
 Framework tasarımcıları "korumalı" adı yanlış bir güvenlik fikir verebilir çünkü korumalı üyeleri ile dikkatli olmanız gerekir. Herkesin alt korumasız bir sınıf ve korunan üyeleri için mümkün ve bu nedenle aynı korumalı üyeler için kullanılan genel üyeler için savunma kodlama uygulamalarını uygulayın.  
  
 **✓ CONSIDER** kullanarak korumalı üyeler için Gelişmiş özelleştirme.  
  
 **✓ DO** korumalı üyeleri korumasız sınıflarında güvenlik, belgelerine ve uyumluluk analiz amacıyla genel olarak ele alın.  
  
 Herhangi bir sınıftan ve korumalı üyelere erişim.  
  
 *Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: Kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 Addison Wesley Professional ile Microsoft Windows geliştirme serisi bir parçası olarak yayımlandı.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
- [Genişletilebilirlik için Tasarlama](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
