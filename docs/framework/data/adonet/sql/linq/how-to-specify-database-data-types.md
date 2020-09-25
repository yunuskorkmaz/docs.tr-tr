---
title: 'Nasıl yapılır: Veritabanı Veri Türleri Belirtme'
ms.date: 03/30/2017
ms.assetid: 2228fdad-7e6a-4b1b-b4d1-79d0198b7c28
ms.openlocfilehash: f070ff718ac10b9681c5ab3c0f4b46547349101b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197241"
---
# <a name="how-to-specify-database-data-types"></a>Nasıl yapılır: Veritabanı Veri Türleri Belirtme

Bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> <xref:System.Data.Linq.Mapping.ColumnAttribute> T-SQL tablo bildiriminde sütunu tanımlayan tam metni belirtmek için bir öznitelik üzerinde özelliğini kullanın.  
  
 <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>Özelliği yalnızca <xref:System.Data.Linq.DataContext.CreateDatabase%2A> bir veritabanının örneğini oluşturmak için kullanmayı planlıyorsanız belirtmeniz gerekir.  
  
 Kod örnekleri için bkz <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> ..  
  
### <a name="to-specify-text-to-define-a-data-type-in-a-t-sql-table"></a>T-SQL tablosunda veri türü tanımlamak üzere metin belirtmek için  
  
1. <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>Özelliği <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliğine ekleyin.  
  
2. <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>Özelliğin değerini T-SQL tarafından kullanılan tam metin olarak ayarlayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL Nesne Modeli](the-linq-to-sql-object-model.md)
- [Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme](how-to-customize-entity-classes-by-using-the-code-editor.md)
