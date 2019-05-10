---
title: 'Nasıl yapılır: Sütunları Sınıf Üyesi Olarak Temsil Etme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ab28021-4d15-4d9c-bf2e-6ccc0daa7d1a
ms.openlocfilehash: 009da2579a6fe15cea3913ae5844fc886da2586c
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64910739"
---
# <a name="how-to-represent-columns-as-class-members"></a>Nasıl yapılır: Sütunları Sınıf Üyesi Olarak Temsil Etme
Kullanım [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute> bir alan veya özellik bir veritabanı sütunu ile ilişkilendirmek için özniteliği.  
  
### <a name="to-map-a-field-or-property-to-a-database-column"></a>Bir alan veya özellik bir veritabanı sütununa eşlemek için  
  
- Ekleme <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliği için özellik veya alan bildirimi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod haritaları `CustomerID` alanındaki `Customer` sınıfının `CustomerID` sütununda `Customers` veritabanı tablosu.  
  
 [!code-csharp[DLinqCustomize#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#2)]
 [!code-vb[DLinqCustomize#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#2)]  
  
 Belirtmek zorunda değilsiniz <xref:System.Data.Linq.Mapping.DataAttribute.Name%2A> adı çıkarılan varsa özelliği. Bir ad belirtmezseniz, adı, özellik veya alan aynı ada olduğu varsayılmıştır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL Nesne Modeli](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [Nasıl yapılır: Kod Düzenleyicisi'ni kullanarak varlık sınıflarını özelleştirme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
