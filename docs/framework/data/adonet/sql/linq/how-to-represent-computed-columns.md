---
title: 'Nasıl yapılır: Hesaplanan sütunları temsil eder'
ms.date: 03/30/2017
ms.assetid: 4025f1fd-9dfa-46c0-b04f-34e8bc7957a2
ms.openlocfilehash: 97db5d69cd97922acefb0b1f3b10f69cf99e3583
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608342"
---
# <a name="how-to-represent-computed-columns"></a>Nasıl yapılır: Hesaplanan sütunları temsil eder
Kullanım [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> özelliği bir <xref:System.Data.Linq.Mapping.ColumnAttribute> hesaplamanın sonucu olan bir sütun göstermek için özniteliği.  
  
 Kod örnekleri için bkz: <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Hesaplanan sütunlar, birincil anahtar olarak desteklemez.  
  
### <a name="to-represent-a-computed-column"></a>Hesaplanmış bir sütun göstermek için  
  
1.  Ekleme <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> özelliğini <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliği.  
  
2.  Formül dize gösterimini atama <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> özelliği.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [LINQ to SQL Nesne Modeli](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [Nasıl yapılır: Kod Düzenleyicisi'ni kullanarak varlık sınıflarını özelleştirme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
