---
title: 'Nasıl yapılır: Tek Seferde Birçok Nesne Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 18aff4d8-bde8-461b-9960-ccabb24e9d22
ms.openlocfilehash: 48cdb47bec35b5315e03629d3a01657136bf7ed2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781675"
---
# <a name="how-to-retrieve-many-objects-at-once"></a>Nasıl yapılır: Tek Seferde Birçok Nesne Alma
Kullanarak <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>, bir sorgudaki birçok nesneyi alabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> `Customer` ve `Order` nesnelerini almak için yöntemini kullanır.  
  
 [!code-csharp[DLinqQueryConcepts#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#9)]
 [!code-vb[DLinqQueryConcepts#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#9)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Kavramları](query-concepts.md)
