---
title: 'Nasıl yapılır: Tek Seferde Birçok Nesne Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 18aff4d8-bde8-461b-9960-ccabb24e9d22
ms.openlocfilehash: 98827989f72b7922a325a9e13b5f46cb18ac5395
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197319"
---
# <a name="how-to-retrieve-many-objects-at-once"></a>Nasıl yapılır: Tek Seferde Birçok Nesne Alma

Kullanarak, bir sorgudaki birçok nesneyi alabilirsiniz <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> .  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod, <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> ve nesnelerini almak için yöntemini kullanır `Customer` `Order` .  
  
 [!code-csharp[DLinqQueryConcepts#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#9)]
 [!code-vb[DLinqQueryConcepts#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#9)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Kavramları](query-concepts.md)
