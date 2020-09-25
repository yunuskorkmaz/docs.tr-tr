---
title: İki Dizinin Küme Birleşimini Döndürme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b8bd3cb-86d4-4a3b-9906-61f68726dd1f
ms.openlocfilehash: 0fe32d8c3c37e99a50ca03262dc6184337b4450e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200215"
---
# <a name="return-the-set-union-of-two-sequences"></a>İki Dizinin Küme Birleşimini Döndürme

<xref:System.Linq.Queryable.Union%2A>İki sıranın set birleşimini döndürmek için işlecini kullanın.  
  
## <a name="example"></a>Örnek  

 Bu örnek <xref:System.Linq.Queryable.Union%2A> , ya da içinde olan tüm ülkelerin/bölgelerin bir dizisini döndürmek için kullanır `Customers` `Employees` .  
  
 [!code-csharp[DLinqQueryExamples#43](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#43)]
 [!code-vb[DLinqQueryExamples#43](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#43)]  
  
 ' De, işleç multisets 'ler [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Linq.Queryable.Union%2A> için çoklu kümeler için TANıMLANıR ( [`UNION ALL`](/sql/t-sql/language-elements/set-operators-union-transact-sql) SQL 'de yan tümcesinin sonucu etkin değildir).

Daha fazla bilgi ve örnek için bkz <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType> ..
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu örnekleri](query-examples.md)
- [Standart Sorgu İşleci Çevirisi](standard-query-operator-translation.md)
