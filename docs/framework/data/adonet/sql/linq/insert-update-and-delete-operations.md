---
description: 'Daha fazla bilgi edinin: ekleme, güncelleştirme ve silme Işlemleri'
title: Insert, Update ve Delete İşlemleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 26a43a4f-83c9-4732-806d-bb23aad0ff6b
ms.openlocfilehash: 2d0470ed6abe654ca08f954c3de97de207adb75d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803825"
---
# <a name="insert-update-and-delete-operations"></a>Insert, Update ve Delete İşlemleri

`Insert` `Update` `Delete` [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Nesne modelinize nesneleri ekleyerek, değiştirerek ve kaldırarak işlemleri gerçekleştirirsiniz. Varsayılan olarak, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] EYLEMLERINIZI SQL 'e çevirir ve değişiklikleri veritabanına gönderir.

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , nesneleriniz üzerinde yaptığınız işleme ve kalıcı değişiklikler için en yüksek esnekliği sunar. Varlık nesneleri kullanılabilir duruma geldiğinde (bir sorgu aracılığıyla ya da onları bir sorgu aracılığıyla alarak), bunları uygulamanızda tipik nesneler olarak değiştirebilirsiniz. Diğer bir deyişle, değerlerini değiştirebilir, koleksiyonlarınıza ekleyebilirsiniz ve bunları Koleksiyonlarınızdan kaldırabilirsiniz. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] değişikliklerinizi izler ve çağırdığınızda veritabanına geri aktarılmaya hazırlanın <xref:System.Data.Linq.DataContext.SubmitChanges%2A> .

> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , Cascade silme işlemlerini desteklemez veya tanımıyor. Üzerinde kısıtlamalar bulunan bir tablodaki bir satırı silmek istiyorsanız, `ON DELETE CASCADE` kuralı veritabanındaki yabancı anahtar kısıtlamasında ayarlamanız veya üst nesnenin silinmesini önleyen alt nesneleri silmek için kendi kodunuzu kullanmanız gerekir. Aksi takdirde, bir özel durum oluşturulur. Daha fazla bilgi için bkz. [nasıl yapılır: veritabanından satırları silme](how-to-delete-rows-from-the-database.md).

Aşağıdaki alıntıları, `Customer` `Order` Northwind örnek veritabanındaki ve sınıflarını kullanır. Sınıf tanımları breçekimi için gösterilmez.

[!code-csharp[DLinqCRUDOps#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCRUDOps/cs/Program.cs#1)]
[!code-vb[DLinqCRUDOps#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCRUDOps/vb/Module1.vb#1)]

<xref:System.Data.Linq.DataContext.SubmitChanges%2A>' İ çağırdığınızda, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] değişikliklerinizi veritabanına geri aktarmak için sahip olması gereken SQL komutlarını otomatik olarak oluşturur ve yürütür.

> [!NOTE]
> Bu davranışı, genellikle saklı bir yordamın yoluyla kendi özel mantığınızı kullanarak geçersiz kılabilirsiniz. Daha fazla bilgi için, [varsayılan davranışı geçersiz kılan geliştiricinin sorumluluklarına](responsibilities-of-the-developer-in-overriding-default-behavior.md)bakın.
>
> Visual Studio kullanan geliştiriciler, bu amaçla saklı yordamlar geliştirmek için Nesne İlişkisel Tasarımcısı kullanabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Örnek Veritabanları İndirme](downloading-sample-databases.md)
- [Insert, Update ve Delete İşlemlerini Özelleştirme](customizing-insert-update-and-delete-operations.md)
