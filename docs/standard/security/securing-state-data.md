---
title: "Durum Verilerinin Güvenliğini Sağlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [.NET Framework], state data
- code security, state data
- secure coding, state data
- state data security
ms.assetid: 12671309-2877-43fe-a3df-6863507e712d
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bd41f5174f426e723ea7e069eaee8f2d367625a1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="securing-state-data"></a>Durum Verilerinin Güvenliğini Sağlama
Hassas verileri işlemek veya herhangi bir tür güvenlik kararları olun uygulamalar bu verileri kendi denetimi altında tutmanız gerekir ve diğer kötü amaçlı kodlar verilere doğrudan erişmek izin veremez. Bellek verileri korumak için en iyi yolu veri özel veya dahili olarak (kapsamla aynı bütünleştirilmiş sınırlı) bildirmektir değişkenleri. Ancak, bile bu verileri bilincinde olmanız gereken erişim tabi şöyledir:  
  
-   Yansıma mekanizmalarını kullanarak, nesnenizin başvurabilir yüksek derecede güvenilen kodu alın ve özel üyelerin ayarlayın.  
  
-   Seri hale getirme kullanarak yüksek derecede güvenilen kod etkili bir şekilde almak ve karşılık gelen verilerin nesne seri hale getirilmiş biçiminde erişebiliyorsa özel üyeler ayarlayın.  
  
-   Hata ayıklama altında bu verileri okunabilir.  
  
 Kendi yöntemlerin hiçbiri emin olun veya özellikler bu değerleri kasıtsız olarak kullanıma sunar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenli kodlama yönergeleri](../../../docs/standard/security/secure-coding-guidelines.md)
