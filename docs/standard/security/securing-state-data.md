---
title: Durum Verilerinin Güvenliğini Sağlama
description: Durum verilerini, erişimi sınırlandırmak için özel veya iç değişkenler olarak bildirin. Bu verilere, hala yansıma, serileştirme ve hata ayıklama aracılığıyla erişilebilir.
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET], state data
- code security, state data
- secure coding, state data
- state data security
ms.assetid: 12671309-2877-43fe-a3df-6863507e712d
ms.openlocfilehash: 849ed993befaceda1b04becbb7fb2530c5c62a77
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94824167"
---
# <a name="securing-state-data"></a>Durum Verilerinin Güvenliğini Sağlama

Hassas verileri işleyen veya herhangi bir tür güvenlik kararı veren uygulamalar, bu verileri kendi denetimleri altında tutmanız gerekir ve diğer olası kötü amaçlı kodun verilere doğrudan erişmesine izin vermez. Bellekteki verileri korumanın en iyi yolu, verileri özel veya iç (aynı derleme ile sınırlı olan) değişkenleriyle bildirmenin en iyi yoludur. Bununla birlikte, bu veriler Access 'e bağlı olsa da şunları göz önünde bulundurun:  
  
- Yansıma mekanizmalarını kullanarak, nesnenizin başvurmasına başvuran, son derece güvenilen kod özel üyeleri alabilir ve ayarlayabilir.  
  
- Serileştirme kullanımı, son derece güvenilen kod, nesnenin serileştirilmiş formundaki karşılık gelen verilere erişebiliyorsa, etkin bir şekilde özel Üyeler alabilir ve ayarlayabilir.  
  
- Hata ayıklama altında bu veriler okunabilir.  
  
 Kendi yöntemlerinizin veya özelliklerinin hiçbirinin bu değerleri istemeden açığa çıkardığı emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli Kodlama Yönergeleri](secure-coding-guidelines.md)
- [ASP.NET Core güvenliği](/aspnet/core/security/)
