---
title: 'Nasıl yapılır: Tabloları Sınıf Olarak Temsil Etme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 84dda12b-88a2-4cd2-92b3-8db87b28d14c
ms.openlocfilehash: 1169def4e0180b1d14103d4a968ff3ed56f63d0c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781761"
---
# <a name="how-to-represent-tables-as-classes"></a>Nasıl yapılır: Tabloları Sınıf Olarak Temsil Etme
Bir sınıfı bir veritabanı tablosuyla ilişkili bir varlık sınıfı olarak belirlemek için özniteliğinikullanın.<xref:System.Data.Linq.Mapping.TableAttribute> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]  
  
### <a name="to-map-a-class-to-a-database-table"></a>Bir sınıfı bir veritabanı tablosuyla eşlemek için  
  
- <xref:System.Data.Linq.Mapping.TableAttribute> Özniteliği sınıf bildirimine ekleyin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, `Customer` sınıfını `Customers` veritabanı tablosuyla ilişkili bir varlık sınıfı olarak oluşturur.  
  
 [!code-csharp[DLinqCustomize#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#1)]
 [!code-vb[DLinqCustomize#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#1)]  
  
 Ad çıkarsancan <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> özelliğini belirtmeniz gerekmez. Bir ad belirtmezseniz, ad, özellik veya alanla aynı ada sahip olacak şekilde adlandırılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL Nesne Modeli](the-linq-to-sql-object-model.md)
- [Nasıl yapılır: Kod düzenleyicisini kullanarak varlık sınıflarını özelleştirme](how-to-customize-entity-classes-by-using-the-code-editor.md)
