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
ms.openlocfilehash: 85a12fb52efe32083d21b9aad50f2d9c1d6f0785
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64602499"
---
# <a name="securing-state-data"></a>Durum Verilerinin Güvenliğini Sağlama
Hassas verileri işleyebilir veya herhangi bir türden güvenlik kararları olun uygulamalar bu verileri kendi denetimi altında tutmanız gerekir ve diğer kötü amaçlı olabilecek kod verilere doğrudan erişmek izin veremez. Verileri (kapsamla aynı derlemeye sınırlı) özel veya iç olarak bildirmek için bellekteki verileri korumak için en iyi yolu olan değişkenler. Ancak, bile bu veri bilincinde olmanız gereken erişim vardır:  
  
- Nesnenizin başvurabilirsiniz yüksek derecede güvenilen kod, yansıma mekanizmalarını kullanarak, alma ve özel üyeler ayarlayın.  
  
- Serileştirme kullanarak yüksek derecede güvenilen kod etkili bir şekilde almak ve nesnesinin seri hala getirilmiş biçimini karşılık gelen verileri erişebiliyorsa özel üyeler ayarlayın.  
  
- Hata ayıklama altında bu verileri okunabilir.  
  
 Kendi yöntemlerin hiçbiri emin olun veya özellikleri bu değerleri istemeden gösterir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli Kodlama Yönergeleri](../../../docs/standard/security/secure-coding-guidelines.md)
