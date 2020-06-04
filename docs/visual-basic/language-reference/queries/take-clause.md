---
title: Take Yan Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTake
helpviewer_keywords:
- Take statement [Visual Basic]
- queries [Visual Basic], Take
- Take clause [Visual Basic]
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
ms.openlocfilehash: 25dd06905525a96bc1504f033eb4f19af6d454a2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359638"
---
# <a name="take-clause-visual-basic"></a>Take Tümcesi (Visual Basic)
Bir koleksiyonun başından itibaren belirtilen sayıda bitişik öğeyi döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Take count  
```  
  
## <a name="parts"></a>Bölümler  
 `count`  
 Gereklidir. Döndürülecek dizi öğe sayısını değerlendiren bir değer veya ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 `Take`Yan tümce bir sorgunun bir sonuç listesinin başından itibaren belirtilen sayıda bitişik öğe içermesini sağlar. Dahil edilecek öğe sayısı parametresi tarafından belirtilir `count` .  
  
 `Take` `Skip` Bir sorgunun herhangi bir segmentinden bir veri aralığı döndürmek için yan tümcesini kullanın. Bunu yapmak için aralığın ilk öğesinin dizinini `Skip` yan tümcesine ve aralığın boyutunu `Take` yan tümcesine geçirin. Bu durumda yan tümce, yan `Take` tümcesinden sonra belirtilmelidir `Skip` .  
  
 `Take`Bir sorguda yan tümcesini kullandığınızda, sonuçların `Take` amaçlanan sonuçları dahil etmek için yan tümce sağlayacak bir sırada döndürüldüğünden de emin olmanız gerekebilir. Sorgu sonuçlarını sıralama hakkında daha fazla bilgi için bkz. [order by yan tümcesi](order-by-clause.md).  
  
 `TakeWhile`Belirtilen koşula bağlı olarak yalnızca belirli öğelerin döndürüleceğini belirtmek için yan tümcesini kullanabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, yan tümcesini, `Take` `Skip` sayfalardaki bir sorgudan veri döndürmek için yan tümcesiyle birlikte kullanır. GetCustomers işlevi, `Skip` sağlanan başlangıç dizini değerine kadar listedeki müşterileri atlamak için yan tümcesini kullanır ve `Take` Bu dizin değerinden başlayan müşterilerin bir sayfasını döndürmek için yan tümcesini kullanır.  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de LINQ'e Giriş](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Sorgular](index.md)
- [Select yan tümcesi](select-clause.md)
- [From yan tümcesi](from-clause.md)
- [Order By Yan Tümcesi](order-by-clause.md)
- [Take While Yan Tümcesi](take-while-clause.md)
- [Skip Yan Tümcesi](skip-clause.md)
