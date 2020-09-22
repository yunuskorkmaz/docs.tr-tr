---
title: Skip While Yan Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
ms.openlocfilehash: af722f7aee021f244b411cdc61619b7de3c20607
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866235"
---
# <a name="skip-while-clause-visual-basic"></a>Skip While Tümcesi (Visual Basic)

Belirtilen koşul olduğu sürece bir koleksiyondaki öğeleri atlar `true` ve kalan öğeleri döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Skip While expression  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`expression`|Gereklidir. İçin öğeleri test eden bir koşulu temsil eden bir ifade. İfade bir `Boolean` değer veya işlev eşdeğerini döndürmelidir, örneğin, `Integer` bir olarak değerlendirilir `Boolean` .|  
  
## <a name="remarks"></a>Açıklamalar  

 `Skip While`Yan tümce, sağlanan döndürene kadar öğeleri bir sorgu sonucunun başından atlar `expression` `false` . `expression`Geri döndüğünde `false` , sorgu kalan tüm öğeleri döndürür. `expression`Kalan sonuçlar için yok sayılır.  
  
 Yan tümcesi, `Skip While` belirli bir `Where` `Where` koşulu karşılamayan bir sorgudaki tüm öğeleri dışlamak için kullanılan yan tümcesinden farklıdır. `Skip While`Yan tümcesi, yalnızca koşul karşılanmadığı sürece öğeleri dışlar. `Skip While`Yan tümce, sıralı bir sorgu sonucuyla çalışırken en yararlı seçenektir.  
  
 Yan tümcesini kullanarak, bir sorgu sonucunun başından belirli bir sonuç sayısını atlayabilirsiniz `Skip` .  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod örneği, `Skip While` Birleşik Devletler ilk müşteri bulunana kadar sonuçları atlamak için yan tümcesini kullanır.  
  
 [!code-vb[VbSimpleQuerySamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de LINQ'e Giriş](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Sorgular](index.md)
- [Select yan tümcesi](select-clause.md)
- [From yan tümcesi](from-clause.md)
- [Skip Yan Tümcesi](skip-clause.md)
- [Take While Yan Tümcesi](take-while-clause.md)
- [WHERE yan tümcesi](where-clause.md)
