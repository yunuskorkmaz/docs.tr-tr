---
title: 'Nasıl yapılır: Sütunları Sınıf Üyesi Olarak Temsil Etme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ab28021-4d15-4d9c-bf2e-6ccc0daa7d1a
ms.openlocfilehash: e73b017b5a500a8c48b3fe22557f6c6619f3b227
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166358"
---
# <a name="how-to-represent-columns-as-class-members"></a>Nasıl yapılır: Sütunları Sınıf Üyesi Olarak Temsil Etme

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute> Bir alanı veya özelliği bir veritabanı sütunuyla ilişkilendirmek için özniteliğini kullanın.  
  
### <a name="to-map-a-field-or-property-to-a-database-column"></a>Bir alanı veya özelliği bir veritabanı sütunuyla eşlemek için  
  
- <xref:System.Data.Linq.Mapping.ColumnAttribute>Özniteliği özellik veya alan bildirimine ekleyin.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod, `CustomerID` `Customer` sınıfındaki alanını `CustomerID` `Customers` veritabanı tablosundaki sütunuyla eşler.  
  
 [!code-csharp[DLinqCustomize#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#2)]
 [!code-vb[DLinqCustomize#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#2)]  
  
 <xref:System.Data.Linq.Mapping.DataAttribute.Name%2A>Ad çıkarsancan özelliğini belirtmeniz gerekmez. Bir ad belirtmezseniz, ad, özellik veya alanla aynı ada sahip olacak şekilde adlandırılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL Nesne Modeli](the-linq-to-sql-object-model.md)
- [Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme](how-to-customize-entity-classes-by-using-the-code-editor.md)
