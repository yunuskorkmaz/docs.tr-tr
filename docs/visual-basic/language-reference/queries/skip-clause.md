---
title: Skip Tümcesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
ms.openlocfilehash: 1810bf4a6573c6fa36f1d8149bf341d45cfd6f52
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
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
 [Sorgular](../../../visual-basic/language-reference/queries/queries.md)  
 [Select Yan Tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From Yan Tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Order By Yan Tümcesi](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [Skip While Yan Tümcesi](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [Take Yan Tümcesi](../../../visual-basic/language-reference/queries/take-clause.md)
