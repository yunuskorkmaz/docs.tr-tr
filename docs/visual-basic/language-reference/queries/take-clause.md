---
title: Take Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTake
helpviewer_keywords:
- Take statement [Visual Basic]
- queries [Visual Basic], Take
- Take clause [Visual Basic]
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
ms.openlocfilehash: 3082954ef84560ccb70f7a47cd3532f622829392
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349641"
---
# <a name="take-clause-visual-basic"></a>Take Tümcesi (Visual Basic)
Bir koleksiyonun başından itibaren belirtilen sayıda bitişik öğeyi döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Take count  
```  
  
## <a name="parts"></a>Bölümler  
 `count`  
 Gerekli. Döndürülecek dizi öğe sayısını değerlendiren bir değer veya ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 `Take` yan tümcesi, bir sorgunun bir sonuç listesinin başından itibaren belirtilen sayıda bitişik öğe içermesini sağlar. Eklenecek öğe sayısı `count` parametresi tarafından belirtilir.  
  
 Sorgunun herhangi bir segmentinden bir veri aralığı döndürmek için `Skip` yan tümcesiyle `Take` yan tümcesini kullanabilirsiniz. Bunu yapmak için aralığın ilk öğesinin dizinini `Skip` yan tümcesine ve aralığın boyutunu `Take` yan tümcesine geçirin. Bu durumda, `Take` yan tümcesinin `Skip` yan tümcesinden sonra belirtilmesi gerekir.  
  
 Bir sorguda `Take` yan tümcesini kullandığınızda, sonuçların, `Take` yan tümcesinin amaçlanan sonuçları içermesini sağlayacak bir sırada döndürüldüğünden emin olmanız da gerekebilir. Sorgu sonuçlarını sıralama hakkında daha fazla bilgi için bkz. [order by yan tümcesi](../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
 Belirtilen koşula bağlı olarak yalnızca belirli öğelerin döndürüleceğini belirtmek için `TakeWhile` yan tümcesini kullanabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, sayfalardaki bir sorgudan veri döndürmek için `Skip` yan tümcesiyle birlikte `Take` yan tümcesini kullanır. GetCustomers işlevi, sağlanan başlangıç dizini değerine kadar listedeki müşterileri atlamak için `Skip` yan tümcesini kullanır ve bu dizin değerinden başlayan müşterilerin bir sayfasını döndürmek için `Take` yan tümcesini kullanır.  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic LINQ 'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Sorgular](../../../visual-basic/language-reference/queries/index.md)
- [Select Yan Tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)
- [From Yan Tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)
- [Order By Yan Tümcesi](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Take While Yan Tümcesi](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [Skip Yan Tümcesi](../../../visual-basic/language-reference/queries/skip-clause.md)
