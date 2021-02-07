---
description: 'Hakkında daha fazla bilgi edinin: Iki sıranın set birleşimini döndürün'
title: İki Dizinin Küme Birleşimini Döndürme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b8bd3cb-86d4-4a3b-9906-61f68726dd1f
ms.openlocfilehash: 5541316560c05712e22c54f706b02d868fadb381
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662968"
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
