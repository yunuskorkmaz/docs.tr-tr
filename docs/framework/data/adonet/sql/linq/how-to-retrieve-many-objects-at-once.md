---
description: 'Daha fazla bilgi edinin: nasıl yapılır: aynı anda birçok nesne alma'
title: 'Nasıl yapılır: Tek Seferde Birçok Nesne Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 18aff4d8-bde8-461b-9960-ccabb24e9d22
ms.openlocfilehash: 2bc202e09c64f2a1956b8688be30cfd87fb655c0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802014"
---
# <a name="how-to-retrieve-many-objects-at-once"></a>Nasıl yapılır: Tek Seferde Birçok Nesne Alma

Kullanarak, bir sorgudaki birçok nesneyi alabilirsiniz <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> .  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod, <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> ve nesnelerini almak için yöntemini kullanır `Customer` `Order` .  
  
 [!code-csharp[DLinqQueryConcepts#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#9)]
 [!code-vb[DLinqQueryConcepts#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#9)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Kavramları](query-concepts.md)
