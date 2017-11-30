---
title: "Is İşleci (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4b1f3f0fa1fd782550c08c816f47b7541399198e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="is-operator-visual-basic"></a>Is İşleci (Visual Basic)
İki nesne başvuru değişkenini karşılaştırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
result = object1 Is object2  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Gerekli. Tüm `Boolean` değeri.  
  
 `object1`  
 Gerekli. Tüm `Object` adı.  
  
 `object2`  
 Gerekli. Tüm `Object` adı.  
  
## <a name="remarks"></a>Açıklamalar  
 `Is` İşleci belirleyen iki nesne başvuruları aynı nesneye başvuran durumunda. Ancak, değer karşılaştırmaları gerçekleştirmez. Varsa `object1` ve `object2` hem de tam aynı nesne örneği için bkz `result` olan `True`; yoksa `result` olan `False`.  
  
 `Is`ile de kullanılabilir `TypeOf` yapmak için anahtar sözcüğü bir `TypeOf`... `Is` bir nesne değişkeninin veri türü ile uyumlu olup olmadığını sınar ifadesi,.  
  
> [!NOTE]
>  `Is` Anahtar sözcüğü kullanılan de [seçin... Case deyimi](../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `Is` nesne başvuruları çiftlerini karşılaştırmak için işleci. Sonuçları atanan bir `Boolean` iki nesnenin aynı olup olmadığını gösteren değeri.  
  
 [!code-vb[VbVbalrOperators#27](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/is-operator_1.vb)]  
  
 Önceki örnekte gösterdiği gibi kullanabileceğiniz `Is` hem de test etmek için işleci erken bağlama ve nesneleri'geç bağlama.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [TypeOf işleci](../../../visual-basic/language-reference/operators/typeof-operator.md)  
 [IsNot işleci](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [Visual Basic'de Karşılaştırma işleçleri](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [İşlevselliğe göre listelenmiş işleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [İşleçler ve ifadeler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
