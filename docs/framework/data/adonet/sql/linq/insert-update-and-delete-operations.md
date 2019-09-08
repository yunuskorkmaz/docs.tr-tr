---
title: Insert, Update ve Delete İşlemleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 26a43a4f-83c9-4732-806d-bb23aad0ff6b
ms.openlocfilehash: fac89f905b85493bc0ec36a85635f369bb354266
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793051"
---
# <a name="insert-update-and-delete-operations"></a>Insert, Update ve Delete İşlemleri

Nesne modelinize nesneleri ekleyerek `Delete` , değiştirerek [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ve kaldırarak işlemleri gerçekleştirirsiniz `Insert`. `Update` Varsayılan olarak, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] eylemlerinizi SQL 'e çevirir ve değişiklikleri veritabanına gönderir.

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], nesneleriniz üzerinde yaptığınız işleme ve kalıcı değişiklikler için en yüksek esnekliği sunar. Varlık nesneleri kullanılabilir duruma geldiğinde (bir sorgu aracılığıyla ya da onları bir sorgu aracılığıyla alarak), bunları uygulamanızda tipik nesneler olarak değiştirebilirsiniz. Diğer bir deyişle, değerlerini değiştirebilir, koleksiyonlarınıza ekleyebilirsiniz ve bunları Koleksiyonlarınızdan kaldırabilirsiniz. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]değişikliklerinizi izler ve çağırdığınızda <xref:System.Data.Linq.DataContext.SubmitChanges%2A>veritabanına geri aktarılmaya hazırlanın.

> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], Cascade silme işlemlerini desteklemez veya tanımıyor. Üzerinde kısıtlamalar bulunan bir tablodaki bir satırı silmek istiyorsanız, `ON DELETE CASCADE` kuralı veritabanındaki yabancı anahtar kısıtlamasında ayarlamanız veya üst nesnenin silinmesini önleyen alt nesneleri silmek için kendi kodunuzu kullanmanız gerekir. Aksi takdirde, bir özel durum oluşturulur. Daha fazla bilgi için [nasıl yapılır: Veritabanından](how-to-delete-rows-from-the-database.md)satırları silin.

Aşağıdaki alıntıları, Northwind örnek `Customer` veritabanındaki `Order` ve sınıflarını kullanır. Sınıf tanımları breçekimi için gösterilmez.

[!code-csharp[DLinqCRUDOps#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCRUDOps/cs/Program.cs#1)]
[!code-vb[DLinqCRUDOps#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCRUDOps/vb/Module1.vb#1)]

' İ çağırdığınızda <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] değişikliklerinizi veritabanına geri aktarmak için sahip olması gereken SQL komutlarını otomatik olarak oluşturur ve yürütür.

> [!NOTE]
> Bu davranışı, genellikle saklı bir yordamın yoluyla kendi özel mantığınızı kullanarak geçersiz kılabilirsiniz. Daha fazla bilgi için, [varsayılan davranışı geçersiz kılan geliştiricinin sorumluluklarına](responsibilities-of-the-developer-in-overriding-default-behavior.md)bakın.
>
> Visual Studio kullanan geliştiriciler, bu amaçla saklı yordamlar geliştirmek için Nesne İlişkisel Tasarımcısı kullanabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Örnek Veritabanları İndirme](downloading-sample-databases.md)
- [Insert, Update ve Delete İşlemlerini Özelleştirme](customizing-insert-update-and-delete-operations.md)
