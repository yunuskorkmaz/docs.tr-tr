---
title: 'Nasıl yapılır: Veritabanındaki satırları güncelleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a2b5c90f-6cc3-4128-bfab-1db488d5af26
ms.openlocfilehash: bfe01c4c54ac1d73ec806fb79730882458a87dac
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54494711"
---
# <a name="how-to-update-rows-in-the-database"></a>Nasıl yapılır: Veritabanındaki satırları güncelleştirme
Üye değerleri ile ilişkili nesnelerin değiştirerek bir veritabanındaki satırları güncelleştirebilirsiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> koleksiyonu ve ardından veritabanına değişiklikleri gönderme. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uygun SQL değişikliklerinizi çevirir `UPDATE` komutları.  
  
> [!NOTE]
>  Geçersiz kılabilirsiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] varsayılan yöntemleri `Insert`, `Update`, ve `Delete` operations veritabanı. Daha fazla bilgi için [özelleştirme ekleme, güncelleştirme ve silme işlemleri](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
>   
>  Visual Studio kullanan geliştiricilerin kullanabileceğiniz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] saklı yordamlar için aynı amaca geliştirilir.  
  
 Aşağıdaki adımlardan istediğinizi düşünelim. geçerli bir <xref:System.Data.Linq.DataContext> Northwind veritabanına bağlar. Daha fazla bilgi için [nasıl yapılır: Bir veritabanına bağlanma](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).  
  
### <a name="to-update-a-row-in-the-database"></a>Veritabanında bir satırı güncelleştirmek için  
  
1.  Güncelleştirilecek satırın veritabanını sorgulayın.  
  
2.  Ortaya çıkan üye değerleri istenen değişiklik [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesne.  
  
3.  Veritabanına değişiklikleri gönderme.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, sipariş #11000 veritabanını sorgular ve ardından değerlerini değiştirir `ShipName` ve `ShipVia` ortaya çıkan içinde `Order` nesne. Son olarak, bu üye değerlerinin değişiklikleri veritabanına değişiklikleri olarak gönderilen `ShipName` ve `ShipVia` sütun.  
  
 [!code-csharp[System.Data.Linq.Table#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.Table#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Değişiklik çakışmalarını yönetme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [Nasıl yapılır: Güncelleştirme, ekleme ve silme işlemleri gerçekleştirmek için saklı yordamlar atama (O/R Tasarımcısı)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [Veri Değişiklikleri Yapma ve Gönderme](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
