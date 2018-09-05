---
title: Sıkıca bağlı istemci-sunucu uygulamaları ile LINQ to SQL
ms.date: 03/30/2017
ms.assetid: e083d805-dcf6-459d-b9af-9ef0563f2dd7
ms.openlocfilehash: 9c36fc1f402d3791611af47a3a6d997db4f31167
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43521886"
---
# <a name="linq-to-sql-with-tightly-coupled-client-server-applications"></a>Sıkıca bağlı istemci-sunucu uygulamaları ile LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sunu katmanı akıllı istemcilerde sıkı şekilde bağlı Orta katmanda kullanılabilir. Salt okunur veri erişimi yok iyimser eşzamanlılık denetimlerinin veya zaman damgası ile iyimser eşzamanlılık senaryolarda değil uzaktan olmayan senaryolar ile daha fazlasını karmaşıklığı yoktur. Ancak, bir veritabanı gerektirdiğinde iyimser eşzamanlılık denetler özgün değerleriyle [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] veri kümelerinde bulma veri gidiş dönüşü için destek düzeyini sağlamaz. Ancak, bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] orta katman herhangi bir platform üzerindeki istemcileri ile veri alışverişi.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] içinde [!INCLUDE[vs_orcas_long](../../../../../../includes/vs-orcas-long-md.md)] bunlar istemciye serileştirilmiş sonra varlık durumu izlemek için herhangi bir altyapı sağlar. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] veri ve sunu katmanı arasındaki etkileşimler küçük ve görece atomik olduğu hizmet odaklı mimari sağlar, ancak herhangi bir gidiş dönüşü özgün değer gerçekleştirmez. Bu nedenle, sıkı şekilde bağlı bir akıllı istemcisiyle kullanmak istiyorsanız [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]ve bir veritabanı, özgün değer ile iyimser eşzamanlılık kullanır, sunu katmanı ve orta arasındaki iletişim için kendi mekanizmalarını uygular gerekecektir katmanı. İçin mantıklı olmadığını karar vermek için sistem tasarımcısına kadar olan yapmak bu bit avantajları lisanslarınıza fazladan iş, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Orta katmanda sağlar. Öte yandan, veritabanını zaman damgaları varsa, sonra gerek yoktur özel değişiklik izleme mantığı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to SQL ile N Katmanı ve Uzak Uygulamalar](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)  
 [Web Hizmetleri ile LINQ to SQL N Katmanı](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-web-services.md)  
 [N katmanlı uygulamalarda veri kümeleriyle çalışma](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications)
