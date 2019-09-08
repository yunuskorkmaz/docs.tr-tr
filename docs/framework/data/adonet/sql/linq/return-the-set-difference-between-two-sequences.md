---
title: İki Dizi Arasındaki Küme Farkını Döndürme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62efb546-c898-408f-af21-36e7c6fed217
ms.openlocfilehash: 92513ed33e2afb785edbdd462ba7bc14923aa6b0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781150"
---
# <a name="return-the-set-difference-between-two-sequences"></a>İki Dizi Arasındaki Küme Farkını Döndürme
İki sıra arasındaki küme farkını döndürmek için işlecinikullanın.<xref:System.Linq.Queryable.Except%2A>  
  
## <a name="example"></a>Örnek  
 Bu örnek, <xref:System.Linq.Queryable.Except%2A> `Customers` canlı ancak canlı olmayan `Employees` tüm ülkelerin/bölgelerin bir dizisini döndürmek için kullanır.  
  
 [!code-csharp[DLinqQueryExamples#41](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#41)]
 [!code-vb[DLinqQueryExamples#41](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#41)]  
  
 ' De [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], işlemyalnızcakümelerüzerindetanımlıdır.<xref:System.Linq.Queryable.Except%2A> Multisets semantiği tanımsızdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Örnekleri](query-examples.md)
- [Standart Sorgu İşleci Çevirisi](standard-query-operator-translation.md)
