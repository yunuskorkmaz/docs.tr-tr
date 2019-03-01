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
ms.openlocfilehash: 8441e619cdbd18545be72fd701c2cc9b1cf495d9
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971243"
---
# <a name="skip-clause-visual-basic"></a>Skip Tümcesi (Visual Basic)
Belirtilen sayıda bir koleksiyondaki öğeleri atlar ve kalan öğeleri döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Skip count  
```  
  
## <a name="parts"></a>Bölümler  
 `count`  
 Gerekli. Bir değer veya atlamak için dizisinin öğe sayısı için değerlendirilen bir ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 `Skip` Yan tümcesi bir sorgu sonuç listesini başındaki öğeleri atlamak ve kalan öğeleri döndürmek neden olur. Geçilecek öğelerin sayısı tarafından tanımlanan `count` parametresi.  
  
 Kullanabileceğiniz `Skip` yan tümcesiyle `Take` yan tümcesi bir sorgu herhangi bir segmentten veri aralığı döndürülecek. Bunu yapmak için dizini aralığın ilk öğesine geçirmek `Skip` yan tümcesi ve aralık için boyutunu `Take` yan tümcesi.  
  
 Kullanırken `Skip` sorgu yan tümcesi, aynı zamanda gerekebilir sonuçları olanak sağlayacak bir sırada döndürüldüğünden emin olunması `Skip` hedeflenen sonuçları atlamak için yan tümcesi. Sorgu sonuçlarını sıralama hakkında daha fazla bilgi için bkz. [Order By yan tümcesi](../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
 Kullanabileceğiniz `SkipWhile` yan tümcesi yalnızca belirli öğeleri, belirtilen bir koşula bağlı olarak göz ardı edilir olduğunu belirtmek için.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde `Skip` yan tümcesi ile birlikte `Take` veri sayfalarında sorgudan döndürülecek yan tümcesi. `GetCustomers` İşlevini kullanan `Skip` sağlanan başlangıç dizini kadar değer ve kullanımlar listesinde müşterileri atlamak için yan tümcesi `Take` yan tümcesi bu dizin değerden başlayan müşteriler bir sayfaya dönün.  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Visual Basic'de LINQ'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Sorgular](../../../visual-basic/language-reference/queries/index.md)
- [Select Yan Tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)
- [From Yan Tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)
- [Order By Yan Tümcesi](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Skip While Yan Tümcesi](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [Take Yan Tümcesi](../../../visual-basic/language-reference/queries/take-clause.md)
