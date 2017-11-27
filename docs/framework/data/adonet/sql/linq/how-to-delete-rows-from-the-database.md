---
title: "Nasıl yapılır: veritabanından satırları silme"
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
ms.assetid: 2144c99b-8055-4080-a5c6-1ea14335e2a3
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2bf7a701831dd08803c7fff6455d6ec3898df363
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-delete-rows-from-the-database"></a>Nasıl yapılır: veritabanından satırları silme
Karşılık gelen kaldırarak bir veritabanında satır silebilirsiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kendi tablo ilişkili koleksiyon nesneleri. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Değişikliklerinizi uygun SQL çevirir `DELETE` komutları.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]desteklemez veya art arda silme işlemleri algılar. Bu karşı kısıtlamalarına sahip bir tablosunda bir satırı silmek istiyorsanız, aşağıdaki görevlerin birini tamamlamanız gerekir:  
  
-   Ayarlama `ON DELETE CASCADE` veritabanındaki yabancı anahtar kısıtlaması kuralında.  
  
-   İlk olarak üst nesneyi silinmesini engellemek bağımlı nesneleri Sil için kendi kodunuzu kullanın.  
  
 Aksi takdirde, bir özel durum oluşturulur. Bu konunun ilerleyen bölümlerinde ikinci kod örneğine bakın.  
  
> [!NOTE]
>  Geçersiz kılabilirsiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] varsayılan yöntemlerini `Insert`, `Update`, ve `Delete` veritabanı işlemleri. Daha fazla bilgi için bkz: [özelleştirme ekleme, güncelleştirme ve silme işlemleri](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
>   
>  Kullanan geliştiriciler [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] kullanabilirsiniz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] aynı amaçla saklı yordamlar geliştirilir.  
  
 Aşağıdaki adımlarda varsayılmaktadır geçerli bir <xref:System.Data.Linq.DataContext> Northwind veritabanına bağlar. Daha fazla bilgi için bkz: [nasıl yapılır: bir veritabanına bağlanmak](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).  
  
### <a name="to-delete-a-row-in-the-database"></a>Veritabanındaki bir satır silmek için  
  
1.  Satırın silinmesi için veritabanını sorgula.  
  
2.  Çağrı <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> yöntemi.  
  
3.  Veritabanı için değişiklik gönderin.  
  
## <a name="example"></a>Örnek  
 Bu ilk kod örneği veritabanı sipariş #11000 ait, bu sipariş ayrıntılarını silme işlemi için işaretler ve bu değişiklikler veritabanına gönderdiğinde sipariş ayrıntıları için sorgular.  
  
 [!code-csharp[System.Data.Linq.Table#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#3)]
 [!code-vb[System.Data.Linq.Table#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#3)]  
  
## <a name="example"></a>Örnek  
 Bu ikinci örnekte hedefi (#10250) sipariş kaldırmaktır. Kod ilk inceler `OrderDetails` kaldırılacak sırasını alt var olup olmadığını görmek için tablo. Sipariş alt öğe, alt ve sırası kaldırılmak üzere işaretlenmiş ilk varsa. <xref:System.Data.Linq.DataContext> Veritabanına gönderilen silme komutları veritabanı kısıtlamalar tarafından uymanız doğru sırayla gerçek siler geçirir.  
  
 [!code-csharp[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCascadeWorkaround/cs/Program.cs#1)]
 [!code-vb[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCascadeWorkaround/vb/Module1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: değişiklik çakışmalarını yönetin](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [Nasıl yapılır: güncelleştirme, ekleme ve silme (O/R Tasarımcısı) gerçekleştirmek için saklı yordamlar atayın](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)  
 [Sağlama ve veri değişiklikleri gönderme](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
