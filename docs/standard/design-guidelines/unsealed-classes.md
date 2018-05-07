---
title: Korumasız sınıfları
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 672d36c6b888ee9a89a76d5d417a7a7e92dd8f36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="unsealed-classes"></a>Korumasız sınıfları
Sealed sınıfları devralınan olamaz ve bunlar genişletilebilirlik engeller. Buna karşılık, kaynağından devralındı sınıfları korumasız sınıfları denir.  
  
 **✓ DÜŞÜNÜN** olmadan korumasız sınıflarını kullanarak sanal ya da korumalı üyeleri ucuz sağlamak için kullanışlı bir yoludur henüz çok Genişletilebilirlik Çerçevesi için takdir olarak eklenemiyor.  
  
 Geliştiriciler genellikle özel oluşturucular, yeni yöntemleri veya yöntemi aşırı gibi kolaylık üye eklemek amacıyla korumasız sınıflardan devralan istersiniz. Örneğin, `System.Messaging.MessageQueue` korumasız olduğundan ve bu nedenle kullanıcıların belirli sıra yolu için varsayılan özel kuyruk oluşturmak için veya belirli senaryolar için API basitleştirmek özel yöntemler eklemenize olanak tanır.  
  
 Varsayılan olarak en programlama dillerinde sınıfları korumasız ve ayrıca çerçeveleri çoğu sınıfları için önerilen varsayılan değer budur. Korumasız türleri tarafından karşılanan genişletilebilirlik çok takdir framework kullanıcılar tarafından ve korumasız türleriyle ilişkili nispeten düşük test maliyetleri nedeniyle sağlamak oldukça uygun maliyetli ' dir.  
  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)  
 [Genişletilebilirlik için Tasarlama](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 [Mühürleme](../../../docs/standard/design-guidelines/sealing.md)
