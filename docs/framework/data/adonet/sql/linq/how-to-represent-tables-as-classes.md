---
title: 'Nasıl yapılır: temsil eden sınıflar olarak tabloları'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 84dda12b-88a2-4cd2-92b3-8db87b28d14c
ms.openlocfilehash: 363efa4e4a6e3e7cfb757ee554e24a7963882278
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362983"
---
# <a name="how-to-represent-tables-as-classes"></a>Nasıl yapılır: temsil eden sınıflar olarak tabloları
Kullanım [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.TableAttribute> özniteliği bir sınıf bir veritabanı tablosu ile ilişkilendirilmiş bir varlık sınıfı olarak belirleyin.  
  
### <a name="to-map-a-class-to-a-database-table"></a>Bir sınıf bir veritabanı tablosuna eşlemek için  
  
-   Ekleme <xref:System.Data.Linq.Mapping.TableAttribute> özniteliği sınıf bildirimi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod kurar `Customer` sınıf ile ilişkili bir varlık sınıfı olarak `Customers` veritabanı tablosu.  
  
 [!code-csharp[DLinqCustomize#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#1)]
 [!code-vb[DLinqCustomize#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#1)]  
  
 Belirtmek zorunda değilsiniz <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> adı çıkarsanabileceği varsa özelliği. Bir ad belirtmezseniz, adı, özellik veya alan aynı adı olduğu kabul edilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to SQL Nesne Modeli](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
