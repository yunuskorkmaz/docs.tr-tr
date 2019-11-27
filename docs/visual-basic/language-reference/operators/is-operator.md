---
title: Is İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
ms.openlocfilehash: 52fbb39ab0a36c8b947b78f464fad26be05ce204
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349543"
---
# <a name="is-operator-visual-basic"></a>Is İşleci (Visual Basic)
İki nesne başvuru değişkenini karşılaştırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
result = object1 Is object2  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Gerekli. Herhangi bir `Boolean` değeri.  
  
 `object1`  
 Gerekli. Herhangi bir `Object` adı.  
  
 `object2`  
 Gerekli. Herhangi bir `Object` adı.  
  
## <a name="remarks"></a>Açıklamalar  
 `Is` işleci, iki nesne başvurusunun aynı nesneye başvurmasını belirler. Ancak, değer karşılaştırmaları gerçekleştirmez. `object1` ve `object2` her ikisi de tam aynı nesne örneğine başvurur, `result` `True`; Aksi takdirde, `result` `False`.  
  
 `Is` Ayrıca bir nesne değişkeninin bir veri türüyle uyumlu olup olmadığını test eden bir `TypeOf`...`Is` ifadesi oluşturmak için `TypeOf` anahtar sözcüğüyle birlikte kullanılabilir.  
  
> [!NOTE]
> `Is` anahtar sözcüğü, Select... içinde de kullanılır [. Case bildirisi](../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, nesne başvuruları çiftlerini karşılaştırmak için `Is` işlecini kullanır. Sonuçlar, iki nesnenin aynı olup olmadığını temsil eden `Boolean` bir değere atanır.  
  
 [!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]  
  
 Yukarıdaki örnekte gösterildiği gibi, `Is` işlecini kullanarak hem erken hem de geç bağlantılı nesneleri test edebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [TypeOf İşleci](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [IsNot İşleci](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Visual Basic karşılaştırma Işleçleri](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [İşleçler ve İfadeler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
