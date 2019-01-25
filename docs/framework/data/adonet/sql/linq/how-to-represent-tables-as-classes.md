---
title: 'Nasıl yapılır: Tabloları sınıf olarak temsil eder.'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 84dda12b-88a2-4cd2-92b3-8db87b28d14c
ms.openlocfilehash: 307356e056aae29af7c8ceafae0ca02604658aab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54509616"
---
# <a name="how-to-represent-tables-as-classes"></a>Nasıl yapılır: Tabloları sınıf olarak temsil eder.
Kullanım [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.TableAttribute> bir sınıf, bir veritabanı tablosu ile ilişkili bir varlık sınıfı olarak belirtmek için özniteliği.  
  
### <a name="to-map-a-class-to-a-database-table"></a>Bir sınıf için bir veritabanı tablosu eşlemek için  
  
-   Ekleme <xref:System.Data.Linq.Mapping.TableAttribute> sınıf bildirimine özniteliği.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod kurar `Customer` sınıf ile ilişkili bir varlık sınıfı olarak `Customers` veritabanı tablosu.  
  
 [!code-csharp[DLinqCustomize#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#1)]
 [!code-vb[DLinqCustomize#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#1)]  
  
 Belirtmek zorunda değilsiniz <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> adı çıkarılan varsa özelliği. Bir ad belirtmezseniz, adı, özellik veya alan aynı ada olduğu varsayılmıştır.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [LINQ to SQL Nesne Modeli](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [Nasıl yapılır: Kod Düzenleyicisi'ni kullanarak varlık sınıflarını özelleştirme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
