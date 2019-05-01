---
title: Insert, Update ve Delete İşlemleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 26a43a4f-83c9-4732-806d-bb23aad0ff6b
ms.openlocfilehash: 6a25ea5fe80da1fed16f44fd3243ebea4d64069f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61902895"
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
>  Visual Studio kullanan geliştiricilerin kullanabileceğiniz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] saklı yordamlar bu amaç için geliştirilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Örnek Veritabanları İndirme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [Insert, Update ve Delete İşlemlerini Özelleştirme](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
