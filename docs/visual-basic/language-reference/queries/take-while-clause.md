---
title: Take While Yan Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
ms.openlocfilehash: 632e9e2195f21a3aa1d1ffd28e9838905c471156
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869663"
---
# <a name="take-while-clause-visual-basic"></a>Take While Tümcesi (Visual Basic)

Belirtilen koşul olduğu `true` ve kalan öğeleri atlayan sürece bir koleksiyondaki öğeleri içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Take While expression  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`expression`|Gereklidir. İçin öğeleri test eden bir koşulu temsil eden bir ifade. İfade bir `Boolean` değer veya işlev eşdeğerini döndürmelidir, örneğin, `Integer` bir olarak değerlendirilir `Boolean` .|  
  
## <a name="remarks"></a>Açıklamalar  

 `Take While`Yan tümcesi, sağlanan dönüşceye kadar bir sorgu sonucunun başından alınan öğeleri içerir `expression` `false` . `expression`Döndürmeden sonra `false` sorgu kalan tüm öğeleri atlar. `expression`Kalan sonuçlar için yok sayılır.  
  
 Yan tümcesi, `Take While` belirli bir `Where` `Where` koşulu karşılayan bir sorgudaki tüm öğeleri dahil etmek için kullanılan yan tümcesinden farklıdır. `Take While`Yan tümcesi yalnızca koşul karşılanmadığı sürece öğeleri içerir. `Take While`Yan tümce, sıralı bir sorgu sonucuyla çalışırken en yararlı seçenektir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod örneği, `Take While` bir sipariş olmadan ilk müşteri bulunana kadar sonuçları almak için yan tümcesini kullanır.  
  
 [!code-vb[VbSimpleQuerySamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de LINQ'e Giriş](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Sorgular](index.md)
- [Select yan tümcesi](select-clause.md)
- [From yan tümcesi](from-clause.md)
- [Take Yan Tümcesi](take-clause.md)
- [Skip While Yan Tümcesi](skip-while-clause.md)
- [WHERE yan tümcesi](where-clause.md)
