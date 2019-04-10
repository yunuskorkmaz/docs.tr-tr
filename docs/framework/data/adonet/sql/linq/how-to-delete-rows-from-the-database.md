---
title: 'Nasıl yapılır: Veritabanından Satır Silme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2144c99b-8055-4080-a5c6-1ea14335e2a3
ms.openlocfilehash: 401d445e49e3712b8c59fa9bc9a2e53500a5db16
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59331682"
---
# <a name="how-to-delete-rows-from-the-database"></a>Nasıl yapılır: Veritabanından Satır Silme
Buna karşılık gelen kaldırarak bir veritabanındaki satırları silebilirsiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ilgili tablo koleksiyonu nesneleri. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uygun SQL yaptığınız değişiklikleri çevirir `DELETE` komutları.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] desteklemez veya art arda silme işlemleri tanıyın. Bunu yönelik kısıtlamalar içeren bir tabloda bir satır silmek istiyorsanız, aşağıdaki görevlerden birini tamamlamanız gerekir:  
  
-   Ayarlama `ON DELETE CASCADE` veritabanında yabancı anahtar kısıtlaması kuralı.  
  
-   Kendi kodunuzu ilk üst nesnenin silinmesini engelleyen alt nesneleri silmek için kullanın.  
  
 Aksi takdirde, bir özel durum oluşturulur. İkinci kod örneğinde bu konunun ilerleyen bölümlerinde bkz.  
  
> [!NOTE]
>  Geçersiz kılabilirsiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] varsayılan yöntemleri `Insert`, `Update`, ve `Delete` operations veritabanı. Daha fazla bilgi için [özelleştirme ekleme, güncelleştirme ve silme işlemleri](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
>   
>  Visual Studio kullanan geliştiricilerin kullanabileceğiniz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] saklı yordamlar için aynı amaca geliştirilir.  
  
 Aşağıdaki adımlardan istediğinizi düşünelim. geçerli bir <xref:System.Data.Linq.DataContext> Northwind veritabanına bağlar. Daha fazla bilgi için [nasıl yapılır: Bir veritabanına bağlanma](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).  
  
### <a name="to-delete-a-row-in-the-database"></a>Veritabanı bir satırı silin  
  
1. Silinecek satırın veritabanını sorgulayın.  
  
2. Çağrı <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> yöntemi.  
  
3. Veritabanı için değişiklik gönderin.  
  
## <a name="example"></a>Örnek  
 Bu ilk kod örneği veritabanı için sipariş #11000 ait, bu Sipariş Ayrıntıları silme işlemi için işaretler ve bu değişiklikleri veritabanına gönderdiğinde sipariş ayrıntıları için sorgular.  
  
 [!code-csharp[System.Data.Linq.Table#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#3)]
 [!code-vb[System.Data.Linq.Table#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#3)]  
  
## <a name="example"></a>Örnek  
 Bu ikinci örnekte hedefi bir sipariş (#10250) kaldırılmasıdır. İlk olarak kodu inceler `OrderDetails` sırasını kaldırılacak şekilde alt öğeleri var olup olmadığını görmek için tabloyu. Sipariş alt öğeleri, ilk alt ve sırasını kaldırılmak üzere işaretlenir varsa. <xref:System.Data.Linq.DataContext> Veritabanı kısıtlamaları silme komutlarını veritabanına gönderilen uymayı doğru sırada gerçek siler geçirir.  
  
 [!code-csharp[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCascadeWorkaround/cs/Program.cs#1)]
 [!code-vb[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCascadeWorkaround/vb/Module1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Değişiklik Çakışmalarını Yönetme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [Nasıl yapılır: Güncelleştirme, ekleme ve silme (O/R Tasarımcısı) gerçekleştirmek için saklı yordamlar atama](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [Veri Değişiklikleri Yapma ve Gönderme](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
