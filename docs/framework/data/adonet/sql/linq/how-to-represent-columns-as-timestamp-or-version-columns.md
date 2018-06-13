---
title: 'Nasıl yapılır: zaman damgası veya sürümü sütunları sütunları temsil eder'
ms.date: 03/30/2017
ms.assetid: 5afd5ce8-1d20-4bc3-a34f-49d95449f493
ms.openlocfilehash: 2fc8aaf260dc3657e33e539939fdf58ad8224c93
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33361245"
---
# <a name="how-to-represent-columns-as-timestamp-or-version-columns"></a>Nasıl yapılır: zaman damgası veya sürümü sütunları sütunları temsil eder
Kullanım [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> özelliği <xref:System.Data.Linq.Mapping.ColumnAttribute> veritabanı zaman damgaları ya da sürüm numaralarıyla tutan bir veritabanı sütununa temsil eden farklı bir alan veya özellik atamak özniteliği.  
  
 Kod örnekleri için bkz: <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.  
  
### <a name="to-designate-a-field-or-property-as-representing-a-timestamp-or-version-column"></a>Bir alan veya özellik bir zaman damgası veya sürüm sütunu temsil eden olarak atamak için  
  
1.  Ekleme <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> özelliğine <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliği.  
  
2.  Ayarlama <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> özellik değerine `true`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to SQL Nesne Modeli](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [Nasıl yapılır: Hangi Üyelerin Eşzamanlılık Çakışmaları için Test Edildiğini Belirtme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)  
 [Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
