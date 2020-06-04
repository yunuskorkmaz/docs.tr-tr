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
ms.openlocfilehash: 3cc0ae5f04358fbe6b2aabc50498f39ca7225164
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84370810"
---
# <a name="is-operator-visual-basic"></a>Is İşleci (Visual Basic)
İki nesne başvuru değişkenini karşılaştırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
result = object1 Is object2  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Gereklidir. Herhangi bir `Boolean` değer.  
  
 `object1`  
 Gereklidir. Herhangi bir `Object` ad.  
  
 `object2`  
 Gereklidir. Herhangi bir `Object` ad.  
  
## <a name="remarks"></a>Açıklamalar  
 `Is`İşleci iki nesne başvurusunun aynı nesneye başvurmasını belirler. Ancak, değer karşılaştırmaları gerçekleştirmez. `object1`Ve `object2` her ikisi de tam aynı nesne örneğine başvurur, ise, olur `result` `True` `result` `False` .  
  
 `Is``TypeOf` `TypeOf` `Is` , bir nesne değişkeninin veri türüyle uyumlu olup olmadığını test eden bir... ifadesi oluşturmak için anahtar sözcüğü ile de kullanılabilir.  
  
> [!NOTE]
> `Is`Anahtar sözcüğü, Select... içinde de kullanılır [. Case bildirisi](../statements/select-case-statement.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `Is` nesne başvuruları çiftlerini karşılaştırmak için işlecini kullanır. Sonuçlar, `Boolean` iki nesnenin aynı olup olmadığını temsil eden bir değere atanır.  
  
 [!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]  
  
 Yukarıdaki örnekte gösterildiği gibi, `Is` işlecini kullanarak hem erken hem de geç bağlantılı nesneleri test edebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [TypeOf İşleci](typeof-operator.md)
- [IsNot İşleci](isnot-operator.md)
- [Visual Basic'de Karşılaştırma İşleçleri](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Visual Basic'de İşleç Önceliği](operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](operators-listed-by-functionality.md)
- [İşleçler ve Ifadeler](../../programming-guide/language-features/operators-and-expressions/index.md)
