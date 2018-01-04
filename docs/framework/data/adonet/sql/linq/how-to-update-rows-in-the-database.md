---
title: "Nasıl yapılır: veritabanındaki satırları güncelleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: a2b5c90f-6cc3-4128-bfab-1db488d5af26
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 8999b85da3f7d32cc1c64899dce5cdfeeafbefd5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-update-rows-in-the-database"></a>Nasıl yapılır: veritabanındaki satırları güncelleştirme
Üye değerleri ile ilişkili nesnelerin değiştirerek bir veritabanında satır güncelleştirebilirsiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> toplama ve değişiklikler veritabanına gönderiliyor. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Değişikliklerinizi uygun SQL içine çevirir `UPDATE` komutları.  
  
> [!NOTE]
>  Geçersiz kılabilirsiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] varsayılan yöntemlerini `Insert`, `Update`, ve `Delete` veritabanı işlemleri. Daha fazla bilgi için bkz: [özelleştirme ekleme, güncelleştirme ve silme işlemleri](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
>   
>  Kullanan geliştiriciler [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] kullanabilirsiniz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] aynı amaçla saklı yordamlar geliştirilir.  
  
 Aşağıdaki adımlarda varsayılmaktadır geçerli bir <xref:System.Data.Linq.DataContext> Northwind veritabanına bağlar. Daha fazla bilgi için bkz: [nasıl yapılır: bir veritabanına bağlanmak](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).  
  
### <a name="to-update-a-row-in-the-database"></a>Veritabanındaki bir satırı güncelleştirmek için  
  
1.  Veritabanı güncelleştirilmesi için satırı için sorgu.  
  
2.  Üye değerlerini elde edilen istenen değişiklik [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesnesi.  
  
3.  Değişiklikler veritabanına gönderin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, sipariş #11000 veritabanını sorgular ve değerlerini değiştirir `ShipName` ve `ShipVia` elde edilen içinde `Order` nesnesi. Son olarak, bu üye değerlerinin değişiklikleri veritabanına değişiklikler olarak gönderilen `ShipName` ve `ShipVia` sütun.  
  
 [!code-csharp[System.Data.Linq.Table#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.Table#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Değişiklik Çakışmalarını Yönetme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [Nasıl yapılır: güncelleştirme, ekleme ve silme (O/R Tasarımcısı) gerçekleştirmek için saklı yordamlar atayın](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)  
 [Veri Değişiklikleri Yapma ve Gönderme](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
