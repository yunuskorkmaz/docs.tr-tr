---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: veritabanı veri türlerini belirtme'
title: 'Nasıl yapılır: Veritabanı Veri Türleri Belirtme'
ms.date: 03/30/2017
ms.assetid: 2228fdad-7e6a-4b1b-b4d1-79d0198b7c28
ms.openlocfilehash: 004a16fe9dd0cda608485b13b03ce922d6a9f671
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785919"
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
