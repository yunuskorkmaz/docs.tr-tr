---
title: Korumalı üyeleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- members [.NET Framework], protected
- protected members
- classes [.NET Framework], unsealed
- classes [.NET Framework], protected members
- unsealed classes
- customizing class behavior
ms.assetid: aa0b58ee-3956-494d-ab48-471ae5db8740
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d4d334d9809f374442e19807d3b249a17a1d9df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="protected-members"></a>Korumalı üyeleri
Korumalı üyeleri kendileri tarafından hiçbir genişletilebilirlik sağlamaz, ancak bunlar genişletilebilirlik sınıflara aracılığıyla daha güçlü yapabilirsiniz. Gelişmiş özelleştirme seçenekleri gereksiz yere ana ortak arabirimi karmaşıklaştırarak olmadan kullanıma sunmak için kullanılabilir.  
  
 Framework tasarımcıları "korumalı" adı yanlış bir fikir güvenlik verebilirsiniz çünkü korumalı üyeleriyle dikkatli olmanız gerekir. Herhangi bir alt korumasız bir sınıf ve Korumalı Erişim üyeleri için bulabildiği ve bu nedenle aynı genel üyeler için kullanılan savunma kodlama uygulamalarını korumalı üyeleri için geçerli.  
  
 **✓ DÜŞÜNÜN** kullanarak korumalı üyeler için Gelişmiş özelleştirme.  
  
 **✓ YAPMAK** korumalı üyeleri korumasız sınıflarında güvenlik, belgelerine ve uyumluluk analiz amacıyla genel olarak ele alın.  
  
 Herhangi bir sınıftan ve korumalı üyeleri erişebilirsiniz.  
  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)  
 [Genişletilebilirlik için Tasarlama](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
