---
title: Is İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
ms.openlocfilehash: a5481a9bce01e84ce4f078335c8cd15a747a3c51
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917213"
---
# <a name="is-operator-visual-basic"></a>Is İşleci (Visual Basic)
İki nesne başvuru değişkenini karşılaştırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
result = object1 Is object2  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Gerekli. Herhangi `Boolean` bir değer.  
  
 `object1`  
 Gerekli. Herhangi `Object` bir ad.  
  
 `object2`  
 Gerekli. Herhangi `Object` bir ad.  
  
## <a name="remarks"></a>Açıklamalar  
 `Is` İşleci iki nesne başvurusunun aynı nesneye başvurmasını belirler. Ancak, değer karşılaştırmaları gerçekleştirmez. `object1` Ve her`object2` ikisi de`result` tam aynınesne`result` örneğine `True` başvurur,`False`ise, olur.  
  
 `Is`Ayrıca, `TypeOf` `TypeOf`... yapmak için anahtar sözcükle birlikte kullanılabilir. `Is` bir nesne değişkeninin bir veri türüyle uyumlu olup olmadığını test eden ifadesi.  
  
> [!NOTE]
> `Is` Anahtar sözcüğü, [Select... içinde de kullanılır. Case bildirisi](../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, nesne başvuruları `Is` çiftlerini karşılaştırmak için işlecini kullanır. Sonuçlar, iki nesnenin aynı olup `Boolean` olmadığını temsil eden bir değere atanır.  
  
 [!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]  
  
 Yukarıdaki örnekte gösterildiği gibi, `Is` işlecini kullanarak hem erken hem de geç bağlantılı nesneleri test edebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [TypeOf İşleci](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [IsNot İşleci](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Visual Basic karşılaştırma Işleçleri](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [İşleçler ve İfadeler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
