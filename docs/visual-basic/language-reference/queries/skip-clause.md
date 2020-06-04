---
title: Skip Yan Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
ms.openlocfilehash: 427d14453260a54bd3f2ab9a8ac75dedacd291f4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359664"
---
# <a name="skip-clause-visual-basic"></a>Skip Tümcesi (Visual Basic)
Koleksiyonda belirtilen sayıda öğeyi atlar ve kalan öğeleri döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Skip count  
```  
  
## <a name="parts"></a>Bölümler  
 `count`  
 Gereklidir. Atlanacak dizinin öğe sayısını değerlendiren bir değer veya ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 `Skip`Yan tümce bir sorgunun bir sonuç listesinin başlangıcında öğeleri atlamasına ve kalan öğeleri döndürmesini sağlar. Atlanacak öğe sayısı parametresi tarafından tanımlanır `count` .  
  
 `Skip` `Take` Bir sorgunun herhangi bir segmentinden bir veri aralığı döndürmek için yan tümcesini kullanın. Bunu yapmak için aralığın ilk öğesinin dizinini `Skip` yan tümcesine ve aralığın boyutunu `Take` yan tümcesine geçirin.  
  
 `Skip`Bir sorguda yan tümcesini kullandığınızda, sonuçların `Skip` amaçlanan sonuçları atlayıp atlamalarını sağlayacak bir sırada döndürüldüğünden emin olmanız da gerekebilir. Sorgu sonuçlarını sıralama hakkında daha fazla bilgi için bkz. [order by yan tümcesi](order-by-clause.md).  
  
 `SkipWhile`Belirtilen koşula bağlı olarak yalnızca belirli öğelerin yoksayılacağını belirtmek için yan tümcesini kullanabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, yan tümcesini, `Skip` `Take` sayfalardaki bir sorgudan veri döndürmek için yan tümcesiyle birlikte kullanır. `GetCustomers`İşlevi, `Skip` sağlanan başlangıç dizini değerine kadar listedeki müşterileri atlamak için yan tümcesini kullanır ve `Take` Bu dizin değerinden başlayan müşterilerin bir sayfasını döndürmek için yan tümcesini kullanır.  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de LINQ'e Giriş](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Sorgular](index.md)
- [Select yan tümcesi](select-clause.md)
- [From yan tümcesi](from-clause.md)
- [Order By Yan Tümcesi](order-by-clause.md)
- [Skip While Yan Tümcesi](skip-while-clause.md)
- [Take Yan Tümcesi](take-clause.md)
