---
title: 'Nasıl yapılır: Eşzamanlılık çakışması denetimini belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2547fcb-58eb-4377-9948-1b8d76a0f3d7
ms.openlocfilehash: 033a547b25e7280eb39be2698963391543437083
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573731"
---
# <a name="how-to-specify-concurrency-conflict-checking"></a>Nasıl yapılır: Eşzamanlılık çakışması denetimini belirtme
Hangi sütunların veritabanının çağırdığınızda eşzamanlılık çakışmaları için denetlenecek olan belirtebilirsiniz <xref:System.Data.Linq.DataContext.SubmitChanges%2A>. Daha fazla bilgi için [nasıl yapılır: Hangi üyelerin eşzamanlılık çakışmaları için test edildiğini belirtme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod belirten `HomePage` üye hiçbir zaman test edilemez güncelleştirme denetimler sırasında. Daha fazla bilgi için bkz. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [LINQ to SQL Nesne Modeli](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [Nasıl yapılır: Kod Düzenleyicisi'ni kullanarak varlık sınıflarını özelleştirme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
