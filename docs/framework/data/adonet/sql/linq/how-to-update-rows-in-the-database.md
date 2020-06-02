---
title: 'Nasıl yapılır: Veritabanında Satırları Güncelleştirme'
description: Tablo ile ilgili bir koleksiyondaki LINQ to SQL nesneleri değiştirerek veritabanındaki satırları güncelleştirmeyi öğrenin. LINQ to SQL, eklemeleri SQL UPDATE komutlarına çevirir.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a2b5c90f-6cc3-4128-bfab-1db488d5af26
ms.openlocfilehash: f25efb91fb5a83fb1c7c109bd018c8210edaec8b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286345"
---
# <a name="how-to-update-rows-in-the-database"></a>Nasıl yapılır: Veritabanında Satırları Güncelleştirme

Bir veritabanındaki satırları, koleksiyonla ilişkili nesnelerin üye değerlerini değiştirerek [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> ve sonra değişiklikleri veritabanına göndererek güncelleştirebilirsiniz. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Değişikliklerinizi uygun SQL `UPDATE` komutlarına çevirir.

> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Insert` , `Update` Ve veritabanı işlemleri için varsayılan yöntemleri geçersiz kılabilirsiniz `Delete` . Daha fazla bilgi için bkz. [Insert, Update ve DELETE Işlemlerini özelleştirme](customizing-insert-update-and-delete-operations.md).
>
> Visual Studio kullanan geliştiriciler, aynı amaçla saklı yordamlar geliştirmek için Nesne İlişkisel Tasarımcısı kullanabilir.

Aşağıdaki adımlarda, geçerli bir <xref:System.Data.Linq.DataContext> veritabanının Northwind veritabanına bağladığı varsayılır. Daha fazla bilgi için bkz. [nasıl yapılır: bir veritabanına bağlanma](how-to-connect-to-a-database.md).

### <a name="to-update-a-row-in-the-database"></a>Veritabanındaki bir satırı güncelleştirmek için

1. Güncelleştirileceği satırın veritabanını sorgulayın.

2. Sonuç nesnesindeki üye değerlerinde istenen değişiklikleri yapın [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .

3. Değişiklikleri veritabanına gönderebilirsiniz.

## <a name="example"></a>Örnek

Aşağıdaki örnek, #11000 sıra için veritabanını sorgular ve `ShipName` sonuç nesnesinde ve değerlerini değiştirir `ShipVia` `Order` . Son olarak, bu üye değerlerindeki değişiklikler veritabanına ve sütunlarında değişiklik olarak veritabanına gönderilir `ShipName` `ShipVia` .

[!code-csharp[System.Data.Linq.Table#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#2)]
[!code-vb[System.Data.Linq.Table#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#2)]

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Değişiklik Çakışmalarını Yönetme](how-to-manage-change-conflicts.md)
- [Nasıl yapılır: Güncelleştirme, ekleme ve silme işlemleri gerçekleştirmek için saklı yordamlar atama (O/R Tasarımcısı)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [Veri Değişiklikleri Yapma ve Gönderme](making-and-submitting-data-changes.md)
