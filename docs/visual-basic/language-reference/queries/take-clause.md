---
title: "Take Tümcesi (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.QueryTake
helpviewer_keywords:
- Take statement [Visual Basic]
- queries [Visual Basic], Take
- Take clause [Visual Basic]
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ee289a24c15226126a526af116ed53b4a9055b35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="take-clause-visual-basic"></a>Take Tümcesi (Visual Basic)
Belirtilen sayıda bitişik öğeyi koleksiyonu başından döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Take count  
```  
  
## <a name="parts"></a>Bölümler  
 `count`  
 Gerekli. Bir değer veya sıradaki döndürülecek sayısını veren ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 `Take` Yan tümcesinde belirtilen sayıda sonuç listesini başından bitişik öğeyi dahil etmek bir sorgu neden olur. Eklenecek öğe sayısı tarafından belirtilen `count` parametresi.  
  
 Kullanabileceğiniz `Take` yan tümcesiyle birlikte `Skip` herhangi bir sorgu segment veri aralığını döndürülecek yan tümcesi. Bunu yapmak için aralığın ilk öğenin dizini geçirmek `Skip` yan tümcesi ve aralığa boyutunu `Take` yan tümcesi. Bu durumda, `Take` yan tümcesinde belirtilen, sonra `Skip` yan tümcesi.  
  
 Kullandığınızda `Take` yan tümcesinin sorgudaki de ihtiyacınız olabilecek sonuçları etkinleştirecek bir sırada döndürüldüğünden emin olmak `Take` amaçlanan sonuçlara dahil etmek için yan tümcesi. Sorgu sonuçlarını sıralama hakkında daha fazla bilgi için bkz: [Order By yan tümcesi](../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
 Kullanabileceğiniz `TakeWhile` yan tümcesini yalnızca belirli öğeler, sağlanan bir koşula göre döndürülmesi gerektiğini belirtin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde `Take` yan tümcesi ile birlikte `Skip` sayfaları sorguda veri döndürmek için yan tümcesi. GetCustomers işlev kullanır `Skip` sağlanan başlangıç dizini kadar değeri ve kullandığı listesinde müşterileri atlamak için yan tümceyi `Take` yan tümcesi bu dizin değerden başlayan müşteriler, bir sayfaya dönün.  
  
 [!code-vb[VbSimpleQuerySamples#1](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/take-clause_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de LINQ'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Sorguları](../../../visual-basic/language-reference/queries/queries.md)  
 [Select tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From yan tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Order By tümcesi](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [Take While tümcesi](../../../visual-basic/language-reference/queries/take-while-clause.md)  
 [Skip tümcesi](../../../visual-basic/language-reference/queries/skip-clause.md)
