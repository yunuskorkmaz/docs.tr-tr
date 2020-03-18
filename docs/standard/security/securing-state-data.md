---
title: Durum Verilerinin Güvenliğini Sağlama
description: Erişimi sınırlamak için durum verilerini özel veya dahili değişkenler olarak bildirin. Bu tür verilere yansıma, serileştirme ve hata ayıklama yoluyla erişilebilir.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], state data
- code security, state data
- secure coding, state data
- state data security
ms.assetid: 12671309-2877-43fe-a3df-6863507e712d
ms.openlocfilehash: f95bf409f7eef8c2636d3c180d2bbd95fbc689c1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186819"
---
# <a name="securing-state-data"></a>Durum Verilerinin Güvenliğini Sağlama
Hassas verileri işleyen veya her türlü güvenlik kararı veren uygulamaların bu verileri kendi denetimleri altında tutması gerekir ve diğer kötü amaçlı olabilecek kodların verilere doğrudan erişmesine izin veremez. Bellekteki verileri korumanın en iyi yolu, verileri özel veya dahili (kapsamı aynı derlemeyle sınırlı) değişkenler olarak bildirmektir. Ancak, bu veriler bile sizin bilmeniz gereken erişime tabidir:  
  
- Yansıma mekanizmaları kullanarak, nesnenize başvurulabilen son derece güvenilir kod özel üyeler alabilir ve ayarlayabilir.  
  
- Serileştirme kullanarak, yüksek güvenilen kod, nesnenin serileştirilmiş biçiminde karşılık gelen verilere erişebiliyorsa, özel üyeleri etkili bir şekilde alabilir ve ayarlayabilir.  
  
- Hata ayıklama altında, bu veriler okunabilir.  
  
 Kendi yöntemlerinizin veya özelliklerinizin bu değerleri istemeden ortaya çıkarmadığından emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli Kodlama Yönergeleri](../../../docs/standard/security/secure-coding-guidelines.md)
