---
title: Durum Verilerinin Güvenliğini Sağlama
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], state data
- code security, state data
- secure coding, state data
- state data security
ms.assetid: 12671309-2877-43fe-a3df-6863507e712d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fe941fff7091fb579e41a3c417dbb2129bcf3e8c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580789"
---
# <a name="securing-state-data"></a>Durum Verilerinin Güvenliğini Sağlama
Hassas verileri işlemek veya herhangi bir tür güvenlik kararları olun uygulamalar bu verileri kendi denetimi altında tutmanız gerekir ve diğer kötü amaçlı kodlar verilere doğrudan erişmek izin veremez. Bellek verileri korumak için en iyi yolu veri özel veya dahili olarak (kapsamla aynı bütünleştirilmiş sınırlı) bildirmektir değişkenleri. Ancak, bile bu verileri bilincinde olmanız gereken erişim tabi şöyledir:  
  
-   Yansıma mekanizmalarını kullanarak, nesnenizin başvurabilir yüksek derecede güvenilen kodu alın ve özel üyelerin ayarlayın.  
  
-   Seri hale getirme kullanarak yüksek derecede güvenilen kod etkili bir şekilde almak ve karşılık gelen verilerin nesne seri hale getirilmiş biçiminde erişebiliyorsa özel üyeler ayarlayın.  
  
-   Hata ayıklama altında bu verileri okunabilir.  
  
 Kendi yöntemlerin hiçbiri emin olun veya özellikler bu değerleri kasıtsız olarak kullanıma sunar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenli Kodlama Yönergeleri](../../../docs/standard/security/secure-coding-guidelines.md)
