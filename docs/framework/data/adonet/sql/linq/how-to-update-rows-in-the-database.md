---
title: 'Nasıl yapılır: Veritabanında Satırları Güncelleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a2b5c90f-6cc3-4128-bfab-1db488d5af26
ms.openlocfilehash: bf4c50bba4b4bc2bf6b7b1c2b79426566c874dd4
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70043568"
---
# <a name="how-to-update-rows-in-the-database"></a>Nasıl yapılır: Veritabanında Satırları Güncelleştirme

Bir veritabanındaki satırları, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> koleksiyonla ilişkili nesnelerin üye değerlerini değiştirerek ve sonra değişiklikleri veritabanına göndererek güncelleştirebilirsiniz. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Değişikliklerinizi uygun SQL `UPDATE` komutlarına çevirir.

> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Insert`, Ve`Delete`veritabanı işlemleri için varsayılan yöntemleri geçersiz kılabilirsiniz. `Update` Daha fazla bilgi için bkz. [Insert, Update ve DELETE Işlemlerini özelleştirme](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).
>
> Visual Studio kullanan geliştiriciler, aynı amaçla saklı yordamlar geliştirmek için Nesne İlişkisel Tasarımcısı kullanabilir.

Aşağıdaki adımlarda, geçerli <xref:System.Data.Linq.DataContext> bir veritabanının Northwind veritabanına bağladığı varsayılır. Daha fazla bilgi için [nasıl yapılır: Bir veritabanına](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md)bağlanın.

### <a name="to-update-a-row-in-the-database"></a>Veritabanındaki bir satırı güncelleştirmek için

1. Güncelleştirileceği satırın veritabanını sorgulayın.

2. Sonuç [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesnesindeki üye değerlerinde istenen değişiklikleri yapın.

3. Değişiklikleri veritabanına gönderebilirsiniz.

## <a name="example"></a>Örnek

Aşağıdaki örnek, #11000 sıra için veritabanını sorgular ve sonuç `ShipName` `Order` nesnesinde ve `ShipVia` değerlerini değiştirir. Son olarak, bu üye değerlerindeki değişiklikler veritabanına `ShipName` ve `ShipVia` sütunlarında değişiklik olarak veritabanına gönderilir.

[!code-csharp[System.Data.Linq.Table#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#2)]
[!code-vb[System.Data.Linq.Table#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#2)]

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Değişiklik çakışmalarını yönetme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [Nasıl yapılır: Güncelleştirme, ekleme ve silme işlemleri gerçekleştirmek için saklı yordamlar atama (O/R Tasarımcısı)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [Veri Değişiklikleri Yapma ve Gönderme](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
