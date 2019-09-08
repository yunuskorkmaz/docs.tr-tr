---
title: 'Nasıl yapılır: Veritabanı Veri Türleri Belirtme'
ms.date: 03/30/2017
ms.assetid: 2228fdad-7e6a-4b1b-b4d1-79d0198b7c28
ms.openlocfilehash: 09ca8dc6fa440138523bcd2905335a04517dd806
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793265"
---
# <a name="how-to-specify-database-data-types"></a>Nasıl yapılır: Veritabanı Veri Türleri Belirtme
Bir T-SQL tablo <xref:System.Data.Linq.Mapping.ColumnAttribute> bildiriminde sütunu tanımlayan tam metni belirtmek için bir öznitelik üzerinde özelliğinikullanın.<xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]  
  
 <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> Özelliği yalnızca bir veritabanının örneğini oluşturmak için kullanmayı <xref:System.Data.Linq.DataContext.CreateDatabase%2A> planlıyorsanız belirtmeniz gerekir.  
  
 Kod örnekleri için bkz <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.  
  
### <a name="to-specify-text-to-define-a-data-type-in-a-t-sql-table"></a>T-SQL tablosunda veri türü tanımlamak üzere metin belirtmek için  
  
1. <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> Özelliği<xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliğine ekleyin.  
  
2. <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> Özelliğin değerini T-SQL tarafından kullanılan tam metin olarak ayarlayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL Nesne Modeli](the-linq-to-sql-object-model.md)
- [Nasıl yapılır: Kod düzenleyicisini kullanarak varlık sınıflarını özelleştirme](how-to-customize-entity-classes-by-using-the-code-editor.md)
