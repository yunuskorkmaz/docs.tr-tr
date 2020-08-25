---
title: İşleç
ms.date: 07/20/2015
f1_keywords:
- vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
ms.openlocfilehash: 1c2d87ef0a8202332c87af552f488d652c400213
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812269"
---
# <a name="is-operator-visual-basic"></a>İşleç (Visual Basic)

İki nesne başvuru değişkenini karşılaştırır.

## <a name="syntax"></a>Syntax

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

> [!NOTE]
> `Is`Anahtar sözcüğü, Select... içinde de kullanılır [. Case bildirisi](../statements/select-case-statement.md).
  
## <a name="example"></a>Örnek

Aşağıdaki örnek, `Is` nesne başvuruları çiftlerini karşılaştırmak için işlecini kullanır. Sonuçlar, `Boolean` iki nesnenin aynı olup olmadığını temsil eden bir değere atanır.

[!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]

Yukarıdaki örnekte gösterildiği gibi, `Is` işlecini kullanarak hem erken hem de geç bağlantılı nesneleri test edebilirsiniz.

## <a name="use-typeof-operator-with-is-operator"></a>With işleci ile TypeOf işleci kullanın

`Is` işleci, bir `TypeOf` `TypeOf` `Is` nesne değişkeninin bir veri türüyle uyumlu olup olmadığını test eden bir... ifadesi oluşturmak için anahtar sözcükle birlikte de kullanılabilir. Örnek:

```vb
If TypeOf sender Is Button Then
```

## <a name="see-also"></a>Ayrıca bkz.

- [TypeOf İşleci](typeof-operator.md)
- [IsNot İşleci](isnot-operator.md)
- [Visual Basic'de Karşılaştırma İşleçleri](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Visual Basic'de İşleç Önceliği](operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](operators-listed-by-functionality.md)
- [İşleçler ve Ifadeler](../../programming-guide/language-features/operators-and-expressions/index.md)
