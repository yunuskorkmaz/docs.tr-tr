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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6ff0ee9019f8c61ad2fc18c5d22240abb2dc6b9b
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="linq-to-sql-with-tightly-coupled-client-server-applications"></a>LINQ-SQL ile sıkı şekilde bağlı istemci-sunucu uygulamaları
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Orta katmanda, sunu katmanı akıllı istemcilerde sıkı şekilde bağlı ile kullanılabilir. Salt okunur veri erişimi, hiçbir iyimser eşzamanlılık denetimleri veya zaman damgalı iyimser eşzamanlılık ilgili senaryolarda yok uzaktan olmayan senaryolar ile daha çok daha karmaşık. Ancak, ne zaman bir veritabanı gerektirir iyimser eşzamanlılık denetler özgün değerleriyle [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] veri kümelerinde bulma verileri gidiş için destek düzeyini sağlamaz. Ancak, bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] orta katman herhangi bir platformda istemcileri ile veri değişimi.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]içinde [!INCLUDE[vs_orcas_long](../../../../../../includes/vs-orcas-long-md.md)] bunlar bir istemciye serileştirilmiş sonra varlık durumu izleme için hiçbir altyapı sağlar. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]verileri ve sunu katmanı arasındaki etkileşimler küçük ve görece atomik nerede hizmet odaklı mimari sağlar, ancak özgün değerlere herhangi gidiş gerçekleştirmez. Bu nedenle, sıkı şekilde bağlı bir akıllı istemciyle kullanmak isteyip istemediğinizi [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]ve bir veritabanı iyimser eşzamanlılık özgün değerleriyle kullanır, değişiklikleri sunu katmanı ve orta arasındaki iletişim için kendi mekanizması uygulamak gerekir katmanı. İçin mantıklıdır olup olmadığını karar vermek için Sistem Tasarımcısı kadar olan yapmak bu bit ek iş faydaları karşılığında, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Orta katmanda sağlar. Diğer taraftan, veritabanını zaman damgaları varsa, sonra gerek yoktur özel değişiklik izleme mantığı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to SQL ile N Katmanı ve Uzak Uygulamalar](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)  
 [Web Hizmetleri ile LINQ to SQL N Katmanı](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-web-services.md)  
 [N katmanlı uygulamalarda veri kümeleriyle çalışma](http://msdn.microsoft.com/library/f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20)
