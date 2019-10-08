---
title: Take While Tümcesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
ms.openlocfilehash: fe6ee470698504bc0434930cc9aa6de712e04254
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004679"
---
# <a name="take-while-clause-visual-basic"></a>Take While Tümcesi (Visual Basic)
Belirtilen koşul `true` olduğu ve kalan öğeleri atlayan sürece bir koleksiyondaki öğeleri içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Take While expression  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`expression`|Gerekli. İçin öğeleri test eden bir koşulu temsil eden bir ifade. İfade, bir @no__t 0 değeri veya bir `Boolean` olarak değerlendirilecek `Integer` gibi işlevsel eşdeğerini döndürmelidir.|  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t-0 yan tümcesi, sağlanan `expression` `false` dönene kadar bir sorgu sonucunun başından itibaren öğeleri içerir. @No__t-0 ' ı `false` döndürürse, sorgu kalan tüm öğeleri atlar. @No__t-0, kalan sonuçlar için yok sayılır.  
  
 @No__t-0 yan tümcesi, `Where` yan tümcesinin belirli bir koşulu karşılayan bir sorgudaki tüm öğeleri dahil etmek için kullanılabilir `Where` tümceciğinden farklıdır. @No__t-0 yan tümcesi yalnızca koşul karşılanmadığı sürece öğeleri içerir. @No__t-0 yan tümcesi, sıralı bir sorgu sonucuyla çalışırken en yararlı seçenektir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, hiçbir sipariş olmadan ilk müşteri bulunana kadar sonuçları almak için `Take While` yan tümcesini kullanır.  
  
 [!code-vb[VbSimpleQuerySamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic LINQ 'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Sorgular](../../../visual-basic/language-reference/queries/index.md)
- [Select Yan Tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)
- [From Yan Tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)
- [Take Yan Tümcesi](../../../visual-basic/language-reference/queries/take-clause.md)
- [Skip While Yan Tümcesi](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [Where Yan Tümcesi](../../../visual-basic/language-reference/queries/where-clause.md)
