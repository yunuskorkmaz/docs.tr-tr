---
title: İki Dizinin Küme Birleşimini Döndürme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b8bd3cb-86d4-4a3b-9906-61f68726dd1f
ms.openlocfilehash: 1b981d3002cf4a23897ce98927aebe96086f8a4a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781226"
---
# <a name="return-the-set-union-of-two-sequences"></a>İki Dizinin Küme Birleşimini Döndürme
İki sıranın set birleşimini döndürmek için işlecinikullanın.<xref:System.Linq.Queryable.Union%2A>  
  
## <a name="example"></a>Örnek  
 Bu örnek, <xref:System.Linq.Queryable.Union%2A> ya `Customers` `Employees`da içinde olan tüm ülkelerin/bölgelerin bir dizisini döndürmek için kullanır.  
  
 [!code-csharp[DLinqQueryExamples#43](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#43)]
 [!code-vb[DLinqQueryExamples#43](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#43)]  
  
 ' De [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], [`UNION ALL`](https://docs.microsoft.com/sql/t-sql/language-elements/set-operators-union-transact-sql?view=sql-server-2017) işleç multisets 'ler için çoklu kümeler için tanımlanır (SQL 'de yan tümcesinin sonucu etkin değildir). <xref:System.Linq.Queryable.Union%2A>

Daha fazla bilgi ve örnek için bkz <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>.
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Örnekleri](query-examples.md)
- [Standart Sorgu İşleci Çevirisi](standard-query-operator-translation.md)
