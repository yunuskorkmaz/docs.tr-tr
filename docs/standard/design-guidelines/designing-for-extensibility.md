---
title: Genişletilebilirlik için tasarlama
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- extending class libraries
- extensibility with class libraries in .NET Framework
- class library design guidelines [.NET Framework], extensibility
- class library extensibility [.NET Framework]
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 68419fe293dd25936aa3c1e3def10bbe8852e175
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="designing-for-extensibility"></a>Genişletilebilirlik için tasarlama
Bir çerçeve tasarlamanın önemli bir özelliği Genişletilebilirlik Çerçevesi dikkatle emin yapılmasıdır. Bu, çeşitli genişletilebilirlik mekanizmaları ile ilişkili yararlar ve maliyetleri anlamak gerektirir. Bu bölümde, genişletilebilirlik mekanizması karar vermenize yardımcı olan — sınıflara, olaylar, sanal üyeler, geri çağrılar ve benzeri —, framework gereksinimlerini en iyi karşılayabilecek.  
  
 Genişletilebilirlik içinde çerçeve izin vermek için birçok yolu vardır. Bunlar daha az güçlü ancak daha az maliyetli pahalı ancak çok güçlü aralığının. Tüm verilen genişletilebilirlik gereksinimini gereksinimlerini karşılayan en az maliyetli genişletilebilirlik mekanizmasını seçmeniz gerekir. Daha fazla genişletilebilirlik daha sonra eklemek genellikle mümkündür, ancak hiçbir zaman onu hemen önemli değişiklikler oluşturmaksızın yapabileceğiniz aklınızda bulundurun.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Mühürsüz Sınıflar](../../../docs/standard/design-guidelines/unsealed-classes.md)  
 [Korumalı Üyeler](../../../docs/standard/design-guidelines/protected-members.md)  
 [Etkinlikler ve Geri Aramalar](../../../docs/standard/design-guidelines/events-and-callbacks.md)  
 [Sanal Üyeler](../../../docs/standard/design-guidelines/virtual-members.md)  
 [Soyutlamalar (Soyut Türler ve Arabirimler)](../../../docs/standard/design-guidelines/abstractions-abstract-types-and-interfaces.md)  
 [Soyutlama Uygulamak için Temel Sınıflar](../../../docs/standard/design-guidelines/base-classes-for-implementing-abstractions.md)  
 [Mühürleme](../../../docs/standard/design-guidelines/sealing.md)  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
