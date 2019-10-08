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
ms.openlocfilehash: e52de186e1475bfabd02821a0cd2384d8350eed3
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004772"
---
# <a name="skip-clause-visual-basic"></a>Skip Tümcesi (Visual Basic)
Koleksiyonda belirtilen sayıda öğeyi atlar ve kalan öğeleri döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Skip count  
```  
  
## <a name="parts"></a>Bölümler  
 `count`  
 Gerekli. Atlanacak dizinin öğe sayısını değerlendiren bir değer veya ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t-0 yan tümcesi, bir sorgunun bir sonuç listesinin başlangıcında öğeleri atlamasına ve kalan öğeleri döndürmesini sağlar. Atlanacak öğe sayısı `count` parametresiyle tanımlanır.  
  
 Sorgunun herhangi bir segmentinden bir veri aralığı döndürmek için `Take` yan tümcesiyle `Skip` yan tümcesini kullanabilirsiniz. Bunu yapmak için aralığın ilk öğesinin dizinini `Skip` yan tümcesine ve aralığın boyutunu `Take` yan tümcesine geçirin.  
  
 Bir sorguda `Skip` yan tümcesini kullandığınızda sonuçların, `Skip` yan tümcesinin amaçlanan sonuçları atlamasına olanak sağlayacak bir sırada döndürüldüğünden emin olmanız da gerekebilir. Sorgu sonuçlarını sıralama hakkında daha fazla bilgi için bkz. [order by yan tümcesi](../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
 Belirtilen koşula bağlı olarak yalnızca belirli öğelerin yoksayılacağını belirtmek için `SkipWhile` yan tümcesini kullanabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, sayfalardaki bir sorgudan veri döndürmek için `Take` yan tümcesiyle birlikte `Skip` yan tümcesini kullanır. @No__t-0 işlevi, sağlanan başlangıç dizini değerine kadar listedeki müşterileri atlamak için `Skip` yan tümcesini kullanır ve bu dizin değerinden başlayan müşterilerin bir sayfasını döndürmek için `Take` yan tümcesini kullanır.  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic LINQ 'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Sorgular](../../../visual-basic/language-reference/queries/index.md)
- [Select Yan Tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)
- [From Yan Tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)
- [Order By Yan Tümcesi](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Skip While Yan Tümcesi](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [Take Yan Tümcesi](../../../visual-basic/language-reference/queries/take-clause.md)
