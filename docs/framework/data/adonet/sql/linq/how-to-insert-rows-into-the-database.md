---
title: 'Nasıl yapılır: Veritabanına Satır Ekleme'
description: Tablo ile ilgili bir koleksiyona LINQ to SQL nesneleri ekleyerek veritabanına satır eklemeyi öğrenin. LINQ to SQL, eklemeleri SQL INSERT komutlarına çevirir.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 44d99680-69c7-4879-a732-f6771b334211
ms.openlocfilehash: 39eee6edf59d2adb7de41efd88899050fbe69fd8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286358"
---
# <a name="how-to-insert-rows-into-the-database"></a>Nasıl yapılır: Veritabanına Satır Ekleme

İlişkili koleksiyona nesneler ekleyerek [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> ve sonra değişiklikleri veritabanına göndererek bir veritabanına satır eklersiniz. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Değişikliklerinizi uygun SQL `INSERT` komutlarına çevirir.

> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Insert` , `Update` Ve veritabanı işlemleri için varsayılan yöntemleri geçersiz kılabilirsiniz `Delete` . Daha fazla bilgi için bkz. [Insert, Update ve DELETE Işlemlerini özelleştirme](customizing-insert-update-and-delete-operations.md).
>
> Visual Studio kullanan geliştiriciler, aynı amaçla saklı yordamlar geliştirmek için Nesne İlişkisel Tasarımcısı kullanabilir.

Aşağıdaki adımlarda, geçerli bir <xref:System.Data.Linq.DataContext> veritabanının Northwind veritabanına bağladığı varsayılır. Daha fazla bilgi için bkz. [nasıl yapılır: bir veritabanına bağlanma](how-to-connect-to-a-database.md).

### <a name="to-insert-a-row-into-the-database"></a>Veritabanına bir satır eklemek için

1. Gönderilecek sütun verilerini içeren yeni bir nesne oluşturun.

2. Yeni nesneyi [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` veritabanındaki hedef tabloyla ilişkili koleksiyona ekleyin.

3. Değişikliği veritabanına gönderebilirsiniz.

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, türünde yeni bir nesne oluşturur `Order` ve uygun değerlerle doldurur. Daha sonra yeni nesneyi `Order` koleksiyona ekler. Son olarak, değişikliği veritabanına tabloya yeni bir satır olarak gönderir `Orders` .

[!code-csharp[System.Data.Linq.Table#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#1)]
[!code-vb[System.Data.Linq.Table#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Değişiklik Çakışmalarını Yönetme](how-to-manage-change-conflicts.md)
- [DataContext Metotları (O/R Tasarımcısı)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [Nasıl yapılır: Güncelleştirme, ekleme ve silme işlemleri gerçekleştirmek için saklı yordamlar atama (O/R Tasarımcısı)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [Veri Değişiklikleri Yapma ve Gönderme](making-and-submitting-data-changes.md)
