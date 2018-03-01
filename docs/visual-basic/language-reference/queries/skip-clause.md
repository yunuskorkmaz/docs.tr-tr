---
title: "Skip Tümcesi (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 508f3c094df4c834305bcb4a78223c1cee82b1c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="skip-clause-visual-basic"></a>Skip Tümcesi (Visual Basic)
Belirtilen bir koleksiyondaki öğelerin sayısı atlar ve kalan öğeleri döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Skip count  
```  
  
## <a name="parts"></a>Bölümler  
 `count`  
 Gerekli. Bir değer veya atlamak için sıradaki sayısını veren ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 `Skip` Yan tümcesi sonuçları listesinin başında öğeleri atlamak ve kalan öğeleri döndürmek bir sorgu neden olur. Atlamayı öğelerin sayısı tarafından tanımlanan `count` parametresi.  
  
 Kullanabileceğiniz `Skip` yan tümcesiyle birlikte `Take` herhangi bir sorgu segment veri aralığını döndürülecek yan tümcesi. Bunu yapmak için aralığın ilk öğenin dizini geçirmek `Skip` yan tümcesi ve aralığa boyutunu `Take` yan tümcesi.  
  
 Kullandığınızda `Skip` yan tümcesinin sorgudaki de ihtiyacınız olabilecek sonuçları etkinleştirecek bir sırada döndürüldüğünden emin olmak `Skip` hedeflenen sonuçları atlamak için yan tümcesi. Sorgu sonuçlarını sıralama hakkında daha fazla bilgi için bkz: [Order By yan tümcesi](../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
 Kullanabileceğiniz `SkipWhile` yan tümcesi yalnızca belirli öğeler, sağlanan bir koşula göre göz ardı edilir olduğunu belirtmek için.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde `Skip` yan tümcesi ile birlikte `Take` sayfaları sorguda veri döndürmek için yan tümcesi. `GetCustomers` İşlev kullanır `Skip` sağlanan başlangıç dizini kadar değeri ve kullandığı listesinde müşterileri atlamak için yan tümceyi `Take` yan tümcesi bu dizin değerden başlayan müşteriler, bir sayfaya dönün.  
  
 [!code-vb[VbSimpleQuerySamples#1](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/skip-clause_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de LINQ'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Sorguları](../../../visual-basic/language-reference/queries/queries.md)  
 [Select tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From yan tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Order By tümcesi](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [Skip While tümcesi](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [Take tümcesi](../../../visual-basic/language-reference/queries/take-clause.md)
