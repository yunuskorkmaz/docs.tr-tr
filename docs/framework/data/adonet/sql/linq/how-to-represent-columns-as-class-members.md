---
title: 'Nasıl yapılır: Sütunları Sınıf Üyesi Olarak Temsil Etme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ab28021-4d15-4d9c-bf2e-6ccc0daa7d1a
ms.openlocfilehash: 515a8477b3a9c72934e0ad11d7b1bf599e8b16a2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793507"
---
# <a name="how-to-represent-columns-as-class-members"></a>Nasıl yapılır: Sütunları Sınıf Üyesi Olarak Temsil Etme
Bir alanı veya özelliği bir veritabanı sütunuyla ilişkilendirmek için özniteliğinikullanın.<xref:System.Data.Linq.Mapping.ColumnAttribute> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]  
  
### <a name="to-map-a-field-or-property-to-a-database-column"></a>Bir alanı veya özelliği bir veritabanı sütunuyla eşlemek için  
  
- <xref:System.Data.Linq.Mapping.ColumnAttribute> Özniteliği özellik veya alan bildirimine ekleyin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki `CustomerID` kod, `Customer` sınıfındaki `Customers` alanını veritabanı tablosundaki sütunuylaeşler.`CustomerID`  
  
 [!code-csharp[DLinqCustomize#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#2)]
 [!code-vb[DLinqCustomize#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#2)]  
  
 Ad çıkarsancan <xref:System.Data.Linq.Mapping.DataAttribute.Name%2A> özelliğini belirtmeniz gerekmez. Bir ad belirtmezseniz, ad, özellik veya alanla aynı ada sahip olacak şekilde adlandırılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL Nesne Modeli](the-linq-to-sql-object-model.md)
- [Nasıl yapılır: Kod düzenleyicisini kullanarak varlık sınıflarını özelleştirme](how-to-customize-entity-classes-by-using-the-code-editor.md)
