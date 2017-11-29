---
title: "İki dizinin kümesi kesişimini döndürür"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d09c344e-3548-4944-a3ed-051880e3f5b8
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4ff65c310323f7505f00dc4a768869cac8226d25
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="return-the-set-intersection-of-two-sequences"></a>İki dizinin kümesi kesişimini döndürür
Kullanım <xref:System.Linq.Queryable.Intersect%2A> iki sıraları kümesi kesişimi işleci.  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Linq.Queryable.Intersect%2A> tüm ülkelerde dizisi hangi ikisi de döndürülecek `Customers` ve `Employees` Canlı.  
  
 [!code-csharp[DLinqQueryExamples#42](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#42)]
 [!code-vb[DLinqQueryExamples#42](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#42)]  
  
 İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Linq.Queryable.Intersect%2A> işlemi yalnızca kümeleri üzerinde iyi tanımlanmış. Multisets anlamları tanımlanmamıştır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sorgu örnekleri](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [Standart sorgu işleci çevirisi](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
