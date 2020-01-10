---
title: Mühürsüz Sınıflar
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
ms.openlocfilehash: 8a5f1142674f83b5ef77f9f7e7e3518afd475e7d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709016"
---
# <a name="unsealed-classes"></a>Mühürsüz Sınıflar
Korumalı sınıflar öğesinden devralınamaz ve genişletilebilirliği engeller. Buna karşılık, öğesinden devralınılabilecek sınıflar korumasız sınıflar olarak adlandırılır.  
  
 **✓ CONSIDER** olmadan korumasız sınıflarını kullanarak sanal ya da korumalı üyeleri ucuz sağlamak için kullanışlı bir yoludur henüz çok Genişletilebilirlik Çerçevesi için takdir olarak eklenemiyor.  
  
 Geliştiriciler, özel oluşturucular, yeni yöntemler veya yöntem aşırı yüklemeleri gibi kolay Üyeler eklemek için genellikle korumasız sınıflardan devralması ister. Örneğin, `System.Messaging.MessageQueue` korumasız olur ve bu sayede kullanıcıların belirli bir sıra yolu için varsayılan olarak özel kuyruklar oluşturmalarına veya belirli senaryolar için API 'YI basitleştiren özel yöntemler eklemesine olanak tanır.  
  
 Sınıflar çoğu programlama dilinde varsayılan olarak korumasız olur ve çerçeveler içindeki çoğu sınıf için de önerilen varsayılan değer budur. Korumasız türler tarafından sağlanan genişletilebilirlik, çatı kullanıcıları tarafından çok daha fazla teşekkürler ve korumasız türlerle ilişkili görece düşük test maliyetlerinden dolayı sağlanması oldukça ucuzdur.  
  
 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
- [Genişletilebilirlik için Tasarlama](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [Mühürleme](../../../docs/standard/design-guidelines/sealing.md)
