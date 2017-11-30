---
title: "LINQ-SQL ile sıkı şekilde bağlı istemci-sunucu uygulamaları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e083d805-dcf6-459d-b9af-9ef0563f2dd7
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e3879d8eeec498f2855ee2b540f77570ee91109f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="linq-to-sql-with-tightly-coupled-client-server-applications"></a>LINQ-SQL ile sıkı şekilde bağlı istemci-sunucu uygulamaları
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Orta katmanda, sunu katmanı akıllı istemcilerde sıkı şekilde bağlı ile kullanılabilir. Salt okunur veri erişimi, hiçbir iyimser eşzamanlılık denetimleri veya zaman damgalı iyimser eşzamanlılık ilgili senaryolarda yok uzaktan olmayan senaryolar ile daha çok daha karmaşık. Ancak, ne zaman bir veritabanı gerektirir iyimser eşzamanlılık denetler özgün değerleriyle [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] veri kümelerinde bulma verileri gidiş için destek düzeyini sağlamaz. Ancak, bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] orta katman herhangi bir platformda istemcileri ile veri değişimi.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]içinde [!INCLUDE[vs_orcas_long](../../../../../../includes/vs-orcas-long-md.md)] bunlar bir istemciye serileştirilmiş sonra varlık durumu izleme için hiçbir altyapı sağlar. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]verileri ve sunu katmanı arasındaki etkileşimler küçük ve görece atomik nerede hizmet odaklı mimari sağlar, ancak özgün değerlere herhangi gidiş gerçekleştirmez. Bu nedenle, sıkı şekilde bağlı bir akıllı istemciyle kullanmak isteyip istemediğinizi [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]ve bir veritabanı iyimser eşzamanlılık özgün değerleriyle kullanır, değişiklikleri sunu katmanı ve orta arasındaki iletişim için kendi mekanizması uygulamak gerekir katmanı. İçin mantıklıdır olup olmadığını karar vermek için Sistem Tasarımcısı kadar olan yapmak bu bit ek iş faydaları karşılığında, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Orta katmanda sağlar. Diğer taraftan, veritabanını zaman damgaları varsa, sonra gerek yoktur özel değişiklik izleme mantığı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [N katmanlı ve uzak uygulamalarla LINQ-SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)  
 [LINQ-SQL N katmanlı Web Hizmetleri](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-web-services.md)  
 [N katmanlı uygulamalarda veri kümeleriyle çalışma](http://msdn.microsoft.com/library/f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20)
