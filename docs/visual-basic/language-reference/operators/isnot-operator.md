---
title: IsNot İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: 616506f64d20e1f150b443433f1b69040136a5ba
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74336070"
---
# <a name="isnot-operator-visual-basic"></a>IsNot İşleci (Visual Basic)

İki nesne başvuru değişkenini karşılaştırır.

## <a name="syntax"></a>Sözdizimi

```vb
result = object1 IsNot object2
```

## <a name="parts"></a>Bölümler
 `result` gerekiyor. Bir `Boolean` değeri.

 `object1` gerekiyor. Herhangi bir `Object` değişkeni veya ifadesi.

 `object2` gerekiyor. Herhangi bir `Object` değişkeni veya ifadesi.

## <a name="remarks"></a>Açıklamalar
 `IsNot` işleci, iki nesne başvurusunun farklı nesnelere başvuracağını belirler. Ancak, değer karşılaştırmaları gerçekleştirmez. `object1` ve `object2` her ikisi de tam aynı nesne örneğine başvurur, `result` `False`; Aksi takdirde, `result` `True`.

 `IsNot`, `Is` işlecinin tersidir. `IsNot` avantajı, okunması zor olabilecek `Not` ve `Is`ile garip söz dizimini önlemenize olanak sağlar.

 `Is` ve `IsNot` işleçlerini kullanarak hem erken hem de geç bağlantılı nesneleri test edebilirsiniz.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, aynı karşılaştırmayı başarmak için hem `Is` işlecini hem de `IsNot` işlecini kullanır.

 [!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]

## <a name="see-also"></a>Ayrıca bkz.

- [Is İşleci](is-operator.md)
- [TypeOf İşleci](typeof-operator.md)
- [Visual Basic operatör önceliği](operator-precedence.md)
- [Nasıl yapılır: İki Nesnenin Aynı Olup Olmadığını Test Etme](../../programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
