---
title: 'Nasıl yapılır: Eşzamanlılık Çakışması Denetimini Belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2547fcb-58eb-4377-9948-1b8d76a0f3d7
ms.openlocfilehash: fd3db5eb5dc9b74d8ea33af56dd522cf2f3fecdb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781593"
---
# <a name="how-to-specify-concurrency-conflict-checking"></a>Nasıl yapılır: Eşzamanlılık Çakışması Denetimini Belirtme
Çağırdığınızda <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, hangi veritabanının sütunlarının eşzamanlılık çakışmaları için denetleneceğini belirtebilirsiniz. Daha fazla bilgi için [nasıl yapılır: Eşzamanlılık çakışmaları](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)Için hangi üyelerin test edildiğini belirtin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, `HomePage` üyenin güncelleştirme denetimleri sırasında asla sınanmaması gerektiğini belirtir. Daha fazla bilgi için bkz. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL Nesne Modeli](the-linq-to-sql-object-model.md)
- [Nasıl yapılır: Kod düzenleyicisini kullanarak varlık sınıflarını özelleştirme](how-to-customize-entity-classes-by-using-the-code-editor.md)
