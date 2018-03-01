---
title: "Distinct Tümcesi (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryDistinct
helpviewer_keywords:
- Distinct clause [Visual Basic]
- Distinct statement [Visual Basic]
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6ed92d5d601c1ec329728346ac881c4fa2bad8aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="distinct-clause-visual-basic"></a>Distinct Tümcesi (Visual Basic)
Yinelenen değerler sonraki sorgu yan tümcelerinde ortadan kaldırmak için geçerli aralık değişkeni değerlerini kısıtlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Distinct  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanabileceğiniz `Distinct` benzersiz öğeleri listesini döndürmek için yan tümcesi. `Distinct` Yan tümcesi yinelenen sorgu sonuçları yoksaymak sorgu neden olur. `Distinct` Yan tümcesi tüm tarafından belirtilen alanları dönmek için yinelenen değerler geçerlidir `Select` yan tümcesi. Öyle değilse `Select` yan tümcesi belirtilirse, `Distinct` yan tümcesinin aralık değişkeni tanımlanan sorgu için uygulanan `From` yan tümcesi. Aralık değişkeni bir sabit türü değilse türdeki tüm üyelerin varolan bir sorgu sonuç eşleşiyorsa sorgu yalnızca bir sorgu sonucu göz ardı eder.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki sorgu ifadesi müşterilerin listesini ve müşteri siparişleri listesini birleştirir. `Distinct` Benzersiz Müşteri adlarının bir listesini döndürür ve tarihleri sipariş yan tümcesi eklenmiştir.  
  
 [!code-vb[VbSimpleQuerySamples#20](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/distinct-clause_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de LINQ'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Sorguları](../../../visual-basic/language-reference/queries/queries.md)  
 [From yan tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Select tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Burada yan tümcesi](../../../visual-basic/language-reference/queries/where-clause.md)
