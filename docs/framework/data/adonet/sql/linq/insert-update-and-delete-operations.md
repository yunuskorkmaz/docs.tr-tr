---
title: Insert, Update ve Delete İşlemleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 26a43a4f-83c9-4732-806d-bb23aad0ff6b
ms.openlocfilehash: e0d2889ef0aeab4a1ca60b1b44a067a221ab541c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956834"
---
# <a name="insert-update-and-delete-operations"></a>Insert, Update ve Delete İşlemleri
Nesne modelinize nesneleri ekleyerek `Delete` , değiştirerek [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ve kaldırarak işlemleri gerçekleştirirsiniz `Insert`. `Update` Varsayılan olarak, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] eylemlerinizi SQL 'e çevirir ve değişiklikleri veritabanına gönderir.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], nesneleriniz üzerinde yaptığınız işleme ve kalıcı değişiklikler için en yüksek esnekliği sunar. Varlık nesneleri kullanılabilir duruma geldiğinde (bir sorgu aracılığıyla ya da onları bir sorgu aracılığıyla alarak), bunları uygulamanızda tipik nesneler olarak değiştirebilirsiniz. Diğer bir deyişle, değerlerini değiştirebilir, koleksiyonlarınıza ekleyebilirsiniz ve bunları Koleksiyonlarınızdan kaldırabilirsiniz. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]değişikliklerinizi izler ve çağırdığınızda <xref:System.Data.Linq.DataContext.SubmitChanges%2A>veritabanına geri aktarılmaya hazırlanın.  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], Cascade silme işlemlerini desteklemez veya tanımıyor. Üzerinde kısıtlamalar bulunan bir tablodaki bir satırı silmek istiyorsanız, `ON DELETE CASCADE` kuralı veritabanındaki yabancı anahtar kısıtlamasında ayarlamanız veya üst nesnenin silinmesini önleyen alt nesneleri silmek için kendi kodunuzu kullanmanız gerekir. Aksi takdirde, bir özel durum oluşturulur. Daha fazla bilgi için [nasıl yapılır: Veritabanından](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md)satırları silin.  
  
 Aşağıdaki alıntıları, Northwind örnek `Customer` veritabanındaki `Order` ve sınıflarını kullanır. Sınıf tanımları breçekimi için gösterilmez.  
  
 [!code-csharp[DLinqCRUDOps#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCRUDOps/cs/Program.cs#1)]
 [!code-vb[DLinqCRUDOps#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCRUDOps/vb/Module1.vb#1)]  
  
 ' İ çağırdığınızda <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] değişikliklerinizi veritabanına geri aktarmak için sahip olması gereken SQL komutlarını otomatik olarak oluşturur ve yürütür.  
  
> [!NOTE]
> Bu davranışı, genellikle saklı bir yordamın yoluyla kendi özel mantığınızı kullanarak geçersiz kılabilirsiniz. Daha fazla bilgi için, [varsayılan davranışı geçersiz kılan geliştiricinin sorumluluklarına](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)bakın.  
>   
>  Visual Studio kullanan geliştiriciler, bu amaçla saklı yordamlar geliştirmek için Nesne İlişkisel Tasarımcısı kullanabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Örnek Veritabanları İndirme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [Insert, Update ve Delete İşlemlerini Özelleştirme](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
