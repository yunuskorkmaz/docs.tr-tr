---
title: "Korumasız sınıfları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f950d8de2681868fe28e09e4b51bd8156cd12e94
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="unsealed-classes"></a>Korumasız sınıfları
Sealed sınıfları devralınan olamaz ve bunlar genişletilebilirlik engeller. Buna karşılık, kaynağından devralındı sınıfları korumasız sınıfları denir.  
  
 **✓ DÜŞÜNÜN** olmadan korumasız sınıflarını kullanarak sanal ya da korumalı üyeleri ucuz sağlamak için kullanışlı bir yoludur henüz çok Genişletilebilirlik Çerçevesi için takdir olarak eklenemiyor.  
  
 Geliştiriciler genellikle özel oluşturucular, yeni yöntemleri veya yöntemi aşırı gibi kolaylık üye eklemek amacıyla korumasız sınıflardan devralan istersiniz. Örneğin, `System.Messaging.MessageQueue` korumasız olduğundan ve bu nedenle kullanıcıların belirli sıra yolu için varsayılan özel kuyruk oluşturmak için veya belirli senaryolar için API basitleştirmek özel yöntemler eklemenize olanak tanır.  
  
 Varsayılan olarak en programlama dillerinde sınıfları korumasız ve ayrıca çerçeveleri çoğu sınıfları için önerilen varsayılan değer budur. Korumasız türleri tarafından karşılanan genişletilebilirlik çok takdir framework kullanıcılar tarafından ve korumasız türleriyle ilişkili nispeten düşük test maliyetleri nedeniyle sağlamak oldukça uygun maliyetli ' dir.  
  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Framework tasarım yönergeleri](../../../docs/standard/design-guidelines/index.md)  
 [Genişletilebilirlik için tasarlama](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 [Mühürleme](../../../docs/standard/design-guidelines/sealing.md)
