---
title: "Nasıl yapılır: sütun sınıf üyeleri olarak temsil eder"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 7ab28021-4d15-4d9c-bf2e-6ccc0daa7d1a
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f0e797886b5e2fedafccf08b71e8cbb2791ea72b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-represent-columns-as-class-members"></a>Nasıl yapılır: sütun sınıf üyeleri olarak temsil eder
Kullanım [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute> bir alan veya özellik bir veritabanı sütununa ile ilişkilendirilecek özniteliği.  
  
### <a name="to-map-a-field-or-property-to-a-database-column"></a>Bir alan veya özellik için bir veritabanı sütununa eşlemek için  
  
-   Ekleme <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliği için özelliği veya alanı bildirimi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod eşlemeleri `CustomerID` alanındaki `Customer` sınıfının `CustomerID` sütununda `Customers` veritabanı tablosu.  
  
 [!code-csharp[DLinqCustomize#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#2)]
 [!code-vb[DLinqCustomize#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#2)]  
  
 Belirtmek zorunda değilsiniz <xref:System.Data.Linq.Mapping.DataAttribute.Name%2A> adı çıkarsanabileceği varsa özelliği. Bir ad belirtmezseniz, adı, özellik veya alan aynı adı olduğu kabul edilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to SQL nesne modeli](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [Nasıl yapılır: kod düzenleyicisini kullanarak sınıflar özelleştirme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
