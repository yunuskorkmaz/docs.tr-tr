---
title: 'Nasıl yapılır: Veritabanından Satır Silme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2144c99b-8055-4080-a5c6-1ea14335e2a3
ms.openlocfilehash: 421735567c527ac9a70cc5eefdbd7570599faac7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782009"
---
# <a name="how-to-delete-rows-from-the-database"></a>Nasıl yapılır: Veritabanından Satır Silme

İlgili [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesneleri tablo ile ilgili koleksiyonlarından kaldırarak veritabanındaki satırları silebilirsiniz. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Değişikliklerinizi uygun SQL `DELETE` komutlarına çevirir.

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], Cascade silme işlemlerini desteklemez veya tanımıyor. Üzerinde kısıtlamalar bulunan bir tablodaki bir satırı silmek isterseniz, aşağıdaki görevlerden birini gerçekleştirmeniz gerekir:

- `ON DELETE CASCADE` Kuralı veritabanındaki yabancı anahtar kısıtlamasından ayarlayın.

- Üst nesnenin silinmesini önleyen alt nesneleri silmek için kendi kodunuzu kullanın.

 Aksi takdirde, bir özel durum oluşturulur. Bu konunun ilerleyen kısımlarında ikinci kod örneğine bakın.

> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Insert`, Ve`Delete`veritabanı işlemleri için varsayılan yöntemleri geçersiz kılabilirsiniz. `Update` Daha fazla bilgi için bkz. [Insert, Update ve DELETE Işlemlerini özelleştirme](customizing-insert-update-and-delete-operations.md).
>
> Visual Studio kullanan geliştiriciler, aynı amaçla saklı yordamlar geliştirmek için Nesne İlişkisel Tasarımcısı kullanabilir.

Aşağıdaki adımlarda, geçerli <xref:System.Data.Linq.DataContext> bir veritabanının Northwind veritabanına bağladığı varsayılır. Daha fazla bilgi için [nasıl yapılır: Bir veritabanına](how-to-connect-to-a-database.md)bağlanın.

### <a name="to-delete-a-row-in-the-database"></a>Veritabanındaki bir satırı silmek için

1. Silinecek satırın veritabanını sorgulayın.

2. Çağrı <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> yöntemi.

3. Değişikliği veritabanına gönderebilirsiniz.

## <a name="example"></a>Örnek

Bu ilk kod örneği, sırasıyla Order #11000 ait sipariş ayrıntıları için veritabanını sorgular, bu sıra ayrıntılarını silinmek üzere işaretler ve bu değişiklikleri veritabanına gönderir.

[!code-csharp[System.Data.Linq.Table#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#3)]
[!code-vb[System.Data.Linq.Table#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#3)]

## <a name="example"></a>Örnek

Bu ikinci örnekte, amaç bir siparişi kaldırmak (#10250). Kod önce, kaldırılacak siparişin `OrderDetails` alt öğeye sahip olup olmadığını görmek için tabloyu inceler. Sıralamada alt öğe varsa, önce alt öğeler ve sonra sıra kaldırma için işaretlenir. , <xref:System.Data.Linq.DataContext> Veritabanı kısıtlamaları tarafından veritabanı kısıtlamalarını veritabanına gönderilen silme komutlarının olması için gerçek silmeleri doğru sırada koyar.

[!code-csharp[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCascadeWorkaround/cs/Program.cs#1)]
[!code-vb[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCascadeWorkaround/vb/Module1.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Değişiklik çakışmalarını yönetme](how-to-manage-change-conflicts.md)
- [Nasıl yapılır: Güncelleştirme, ekleme ve silme işlemleri gerçekleştirmek için saklı yordamlar atama (O/R Tasarımcısı)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [Veri Değişiklikleri Yapma ve Gönderme](making-and-submitting-data-changes.md)
