---
title: Take Tümcesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTake
helpviewer_keywords:
- Take statement [Visual Basic]
- queries [Visual Basic], Take
- Take clause [Visual Basic]
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
ms.openlocfilehash: bfaccf470d93a6a72451e7ad8b41e8dbb1171c71
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43856586"
---
# <a name="take-clause-visual-basic"></a>Take Tümcesi (Visual Basic)
Bir koleksiyon başlangıcından belirtilen bir bitişik öğelerin sayısını döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Take count  
```  
  
## <a name="parts"></a>Bölümler  
 `count`  
 Gerekli. Bir değer veya döndürülecek dizisinin öğe sayısı için değerlendirilen bir ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 `Take` Yan tümcesi bir sorgu sonuç listesini başlangıcından bitişik öğelerin belirtilen bir sayı içerecek şekilde neden olur. Eklenecek öğe sayısı tarafından belirtilen `count` parametresi.  
  
 Kullanabileceğiniz `Take` yan tümcesiyle `Skip` yan tümcesi bir sorgu herhangi bir segmentten veri aralığı döndürülecek. Bunu yapmak için dizini aralığın ilk öğesine geçirmek `Skip` yan tümcesi ve aralık için boyutunu `Take` yan tümcesi. Bu durumda, `Take` yan belirtilen, sonra `Skip` yan tümcesi.  
  
 Kullanırken `Take` sorgu yan tümcesi, aynı zamanda gerekebilir sonuçları olanak sağlayacak bir sırada döndürüldüğünden emin olunması `Take` hedeflenen sonuçları içerecek şekilde yan tümcesi. Sorgu sonuçlarını sıralama hakkında daha fazla bilgi için bkz. [Order By yan tümcesi](../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
 Kullanabileceğiniz `TakeWhile` yan tümcesini yalnızca belirli öğeleri, belirtilen bir koşula bağlı olarak verilmesini belirtin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde `Take` yan tümcesi ile birlikte `Skip` veri sayfalarında sorgudan döndürülecek yan tümcesi. GetCustomers işlevini kullanan `Skip` sağlanan başlangıç dizini kadar değer ve kullanımlar listesinde müşterileri atlamak için yan tümcesi `Take` yan tümcesi bu dizin değerden başlayan müşteriler bir sayfaya dönün.  
  
 [!code-vb[VbSimpleQuerySamples#1](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/take-clause_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de LINQ'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Sorgular](../../../visual-basic/language-reference/queries/index.md)  
 [Select Yan Tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From Yan Tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Order By Yan Tümcesi](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [Take While Yan Tümcesi](../../../visual-basic/language-reference/queries/take-while-clause.md)  
 [Skip Yan Tümcesi](../../../visual-basic/language-reference/queries/skip-clause.md)
