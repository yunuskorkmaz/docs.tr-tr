---
title: 'Nasıl yapılır: Veritabanı veri türleri belirtme'
ms.date: 03/30/2017
ms.assetid: 2228fdad-7e6a-4b1b-b4d1-79d0198b7c28
ms.openlocfilehash: 566ff545cd493eed637093c378aacc865a7f5e20
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54620493"
---
# <a name="how-to-specify-database-data-types"></a>Nasıl yapılır: Veritabanı veri türleri belirtme
Kullanım [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> özelliği bir <xref:System.Data.Linq.Mapping.ColumnAttribute> sütunu bir T-SQL tablo bildiriminde tanımlayan tam metni belirtmek için özniteliği.  
  
 Belirtmelisiniz <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> yalnızca kullanmayı planlıyorsanız özelliği <xref:System.Data.Linq.DataContext.CreateDatabase%2A> veritabanı örneği oluşturmak için.  
  
 Kod örnekleri için bkz: <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.  
  
### <a name="to-specify-text-to-define-a-data-type-in-a-t-sql-table"></a>Bir T-SQL tablosunu bir veri türü tanımlamak için metin belirtmek için  
  
1.  Ekleme <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> özelliğini <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliği.  
  
2.  Değerini <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> T-SQL tarafından kullanılan tam metin özellik.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [LINQ to SQL Nesne Modeli](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [Nasıl yapılır: Kod Düzenleyicisi'ni kullanarak varlık sınıflarını özelleştirme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
