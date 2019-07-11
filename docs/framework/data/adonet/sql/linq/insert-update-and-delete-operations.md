---
title: Insert, Update ve Delete İşlemleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 26a43a4f-83c9-4732-806d-bb23aad0ff6b
ms.openlocfilehash: fa3690ae74869f5dc0fbaa8d824d4aebca8ce724
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743059"
---
# <a name="insert-update-and-delete-operations"></a>Insert, Update ve Delete İşlemleri
Gerçekleştirdiğiniz `Insert`, `Update`, ve `Delete` işlemlerinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ekleyerek, değiştirerek ve nesneler, nesne modelinde kaldırılıyor. Varsayılan olarak, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] eylemlerinizi SQL çevirir ve veritabanı değişiklikleri gönderir.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] düzenleme ve kalıcı yapma nesnelerinizi yaptığınız değişiklikler en üst düzeyde esneklik sunar. Varlık nesnesi (veya bir sorgu aracılığıyla alarak veya yenisini oluşturmak) kullanılabilir hemen sonra bunları uygulamanızda gibi tipik nesneleri değiştirebilirsiniz. Diğer bir deyişle, bunların değerlerini değiştirebilirsiniz, Koleksiyonlarınız için ekleyebilirsiniz ve, koleksiyonlardan kaldırabilirsiniz. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yaptığınız değişiklikleri izler ve çağırdığınızda, bunları veritabanına aktarmak hazır <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] desteklemez veya art arda silme işlemleri tanıyın. Bunu yönelik kısıtlamalar içeren bir tabloda bir satır silmek istiyorsanız, iki küme gerekir `ON DELETE CASCADE` veritabanında yabancı anahtar kısıtlaması kural ya da kendi kodunuzu ilk üst nesnenin silinmesini engelleyen alt nesneleri silmek için kullanın. Aksi takdirde, bir özel durum oluşturulur. Daha fazla bilgi için [nasıl yapılır: Veritabanından satır silme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).  
  
 Aşağıdaki forumlarından kullanım `Customer` ve `Order` Northwind örnek veritabanından sınıfları. Sınıf tanımları için kısaltma gösterilmez.  
  
 [!code-csharp[DLinqCRUDOps#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCRUDOps/cs/Program.cs#1)]
 [!code-vb[DLinqCRUDOps#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCRUDOps/vb/Module1.vb#1)]  
  
 Çağırdığınızda <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] otomatik olarak oluşturur ve değişikliklerinizi veritabanına aktarmak için gereken SQL komutları yürütür.  
  
> [!NOTE]
>  Genellikle bir saklı yordam yoluyla özel kendi mantığınızı kullanarak bu davranışı geçersiz kılabilirsiniz. Daha fazla bilgi için [sorumlulukları geliştirici olarak geçersiz kılma varsayılan davranış](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md).  
>   
>  Visual Studio kullanan geliştiricilerin, Nesne İlişkisel Tasarımcısı, bu amaç için saklı yordamlar geliştirmek için kullanabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Örnek Veritabanları İndirme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [Insert, Update ve Delete İşlemlerini Özelleştirme](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
