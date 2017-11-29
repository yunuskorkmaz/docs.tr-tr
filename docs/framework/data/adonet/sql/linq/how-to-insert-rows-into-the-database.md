---
title: "Nasıl yapılır: veritabanına Satır Ekle"
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
ms.assetid: 44d99680-69c7-4879-a732-f6771b334211
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a96a0ab800076db16022f5b02c84d7a53ca99147
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-insert-rows-into-the-database"></a>Nasıl yapılır: veritabanına Satır Ekle
Nesneleri ile ilişkili için ekleyerek bir veritabanına Satır Ekle [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> toplama ve değişiklikler veritabanına gönderiliyor. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Değişikliklerinizi uygun SQL içine çevirir `INSERT` komutları.  
  
> [!NOTE]
>  Geçersiz kılabilirsiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] varsayılan yöntemlerini `Insert`, `Update`, ve `Delete` veritabanı işlemleri. Daha fazla bilgi için bkz: [özelleştirme ekleme, güncelleştirme ve silme işlemleri](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
>   
>  Kullanan geliştiriciler [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] kullanabilirsiniz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] aynı amaçla saklı yordamlar geliştirilir.  
  
 Aşağıdaki adımlarda varsayılmaktadır geçerli bir <xref:System.Data.Linq.DataContext> Northwind veritabanına bağlar. Daha fazla bilgi için bkz: [nasıl yapılır: bir veritabanına bağlanmak](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).  
  
### <a name="to-insert-a-row-into-the-database"></a>Veritabanına bir satır eklemek için  
  
1.  Gönderilecek sütun verileri içeren yeni bir nesne oluşturun.  
  
2.  Yeni nesne için ekleme [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` veritabanındaki hedef tabloyla ilişkili koleksiyonu.  
  
3.  Veritabanı için değişiklik gönderin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde türünde yeni bir nesne oluşturur `Order` ve uygun değerlerle doldurur. Ardından yeni nesneye ekler `Order` koleksiyonu. Son olarak, yeni bir satır olarak değişiklik veritabanına gönderdiğinde `Orders` tablo.  
  
 [!code-csharp[System.Data.Linq.Table#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.Table#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: değişiklik çakışmalarını yönetin](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [DataContext yöntemleri (O/R Tasarımcısı)](/visualstudio/data-tools/datacontext-methods-o-r-designer)  
 [Nasıl yapılır: güncelleştirme, ekleme ve silme (O/R Tasarımcısı) gerçekleştirmek için saklı yordamlar atayın](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)  
 [Sağlama ve veri değişiklikleri gönderme](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
