---
title: 'Nasıl yapılır: Eşzamanlılık Çakışması Denetimini Belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2547fcb-58eb-4377-9948-1b8d76a0f3d7
ms.openlocfilehash: 7adacdccd12c6493ff7c62c0e6a44058a9719d7d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197215"
---
# <a name="how-to-specify-concurrency-conflict-checking"></a>Nasıl yapılır: Eşzamanlılık Çakışması Denetimini Belirtme

Çağırdığınızda, hangi veritabanının sütunlarının eşzamanlılık çakışmaları için denetleneceğini belirtebilirsiniz <xref:System.Data.Linq.DataContext.SubmitChanges%2A> . Daha fazla bilgi için bkz. [nasıl yapılır: eşzamanlılık çakışmaları Için hangi üyelerin test edildiğini belirtme](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod, `HomePage` üyenin güncelleştirme denetimleri sırasında asla sınanmaması gerektiğini belirtir. Daha fazla bilgi için bkz. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL Nesne Modeli](the-linq-to-sql-object-model.md)
- [Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme](how-to-customize-entity-classes-by-using-the-code-editor.md)
