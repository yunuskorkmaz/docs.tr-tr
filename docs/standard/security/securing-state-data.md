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
ms.openlocfilehash: c30bd2fe9e1ed371be2db60739d3b329fea788c7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705905"
---
# <a name="securing-state-data"></a>Durum Verilerinin Güvenliğini Sağlama
Hassas verileri işleyen veya herhangi bir tür güvenlik kararı veren uygulamalar, bu verileri kendi denetimleri altında tutmanız gerekir ve diğer olası kötü amaçlı kodun verilere doğrudan erişmesine izin vermez. Bellekteki verileri korumanın en iyi yolu, verileri özel veya iç (aynı derleme ile sınırlı olan) değişkenleriyle bildirmenin en iyi yoludur. Bununla birlikte, bu veriler Access 'e bağlı olsa da şunları göz önünde bulundurun:  
  
- Yansıma mekanizmalarını kullanarak, nesnenizin başvurmasına başvuran, son derece güvenilen kod özel üyeleri alabilir ve ayarlayabilir.  
  
- Serileştirme kullanımı, son derece güvenilen kod, nesnenin serileştirilmiş formundaki karşılık gelen verilere erişebiliyorsa, etkin bir şekilde özel Üyeler alabilir ve ayarlayabilir.  
  
- Hata ayıklama altında bu veriler okunabilir.  
  
 Kendi yöntemlerinizin veya özelliklerinin hiçbirinin bu değerleri istemeden açığa çıkardığı emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli Kodlama Yönergeleri](../../../docs/standard/security/secure-coding-guidelines.md)
