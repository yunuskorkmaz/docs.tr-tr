---
description: 'Hakkında daha fazla bilgi edinin: ınot Işleci (Visual Basic)'
title: IsNot işleci
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- comparison operators [Visual Basic]
- TypeOf...IsNot expression
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: ac3e127676dfa57d14e07838152022de62fc336b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665672"
---
# <a name="isnot-operator-visual-basic"></a>IsNot İşleci (Visual Basic)

İki nesne başvuru değişkenini karşılaştırır.

## <a name="syntax"></a>Syntax

```vb
result = object1 IsNot object2
```

## <a name="parts"></a>Bölümler

- `result`

  Gereklidir. Bir `Boolean` değer.

- `object1`

  Gereklidir. Herhangi bir `Object` değişken veya ifade.

- `object2`

  Gereklidir. Herhangi bir `Object` değişken veya ifade.

## <a name="remarks"></a>Açıklamalar

`IsNot`İşleci iki nesne başvurusunun farklı nesnelere başvuracağını belirler. Ancak, değer karşılaştırmaları gerçekleştirmez. `object1`Ve `object2` her ikisi de tam aynı nesne örneğine başvurur, ise, olur `result` `False` `result` `True` .

`IsNot` , `Is` işlecinin tersidir. ' Nin avantajı, `IsNot` ve ile garip söz dizimini önlemenize `Not` ve bu `Is` da okunması zor olabilir.

 `Is`Ve `IsNot` işleçlerini, hem erken hem de geç bağlantılı nesneleri test etmek için kullanabilirsiniz.

## <a name="example"></a>Örnek

Aşağıdaki kod örneği `Is` `IsNot` aynı karşılaştırmayı başarmak için hem işlecini hem de işlecini kullanır.

[!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]

## <a name="use-typeof-operator-with-isnot-operator"></a>IsNot işleci ile TypeOf işleci kullanın

Visual Basic 14 ' ten başlayarak, bir `TypeOf` `IsNot` nesnenin veri türüyle uyumlu olup olmadığını test etmek için işlecini işleciyle kullanabilirsiniz  . Örneğin:

```vb
If TypeOf sender IsNot Button Then
```

## <a name="see-also"></a>Ayrıca bkz.

- [Is İşleci](is-operator.md)
- [TypeOf İşleci](typeof-operator.md)
- [Visual Basic'de İşleç Önceliği](operator-precedence.md)
- [Nasıl yapılır: İki Nesnenin Aynı Olup Olmadığını Test Etme](../../programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
