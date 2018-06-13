---
title: LINQ-SQL ile sıkı şekilde bağlı istemci-sunucu uygulamaları
ms.date: 03/30/2017
ms.assetid: e083d805-dcf6-459d-b9af-9ef0563f2dd7
ms.openlocfilehash: f094bb319a4ca5241e60993770c9c49c3151635c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33359926"
---
# <a name="linq-to-sql-with-tightly-coupled-client-server-applications"></a>LINQ-SQL ile sıkı şekilde bağlı istemci-sunucu uygulamaları
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Orta katmanda, sunu katmanı akıllı istemcilerde sıkı şekilde bağlı ile kullanılabilir. Salt okunur veri erişimi, hiçbir iyimser eşzamanlılık denetimleri veya zaman damgalı iyimser eşzamanlılık ilgili senaryolarda yok uzaktan olmayan senaryolar ile daha çok daha karmaşık. Ancak, ne zaman bir veritabanı gerektirir iyimser eşzamanlılık denetler özgün değerleriyle [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] veri kümelerinde bulma verileri gidiş için destek düzeyini sağlamaz. Ancak, bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] orta katman herhangi bir platformda istemcileri ile veri değişimi.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] içinde [!INCLUDE[vs_orcas_long](../../../../../../includes/vs-orcas-long-md.md)] bunlar bir istemciye serileştirilmiş sonra varlık durumu izleme için hiçbir altyapı sağlar. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] verileri ve sunu katmanı arasındaki etkileşimler küçük ve görece atomik nerede hizmet odaklı mimari sağlar, ancak özgün değerlere herhangi gidiş gerçekleştirmez. Bu nedenle, sıkı şekilde bağlı bir akıllı istemciyle kullanmak isteyip istemediğinizi [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]ve bir veritabanı iyimser eşzamanlılık özgün değerleriyle kullanır, değişiklikleri sunu katmanı ve orta arasındaki iletişim için kendi mekanizması uygulamak gerekir katmanı. İçin mantıklıdır olup olmadığını karar vermek için Sistem Tasarımcısı kadar olan yapmak bu bit ek iş faydaları karşılığında, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Orta katmanda sağlar. Diğer taraftan, veritabanını zaman damgaları varsa, sonra gerek yoktur özel değişiklik izleme mantığı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to SQL ile N Katmanı ve Uzak Uygulamalar](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)  
 [Web Hizmetleri ile LINQ to SQL N Katmanı](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-web-services.md)  
 [N katmanlı uygulamalarda veri kümeleriyle çalışma](http://msdn.microsoft.com/library/f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20)
