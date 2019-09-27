---
title: IsNot İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: 7e1ac1004e671f592c03bd44ee7ec2e8cc572933
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71331624"
---
# <a name="isnot-operator-visual-basic"></a>IsNot İşleci (Visual Basic)
İki nesne başvuru değişkenini karşılaştırır.

## <a name="syntax"></a>Sözdizimi

```vb
result = object1 IsNot object2
```

## <a name="parts"></a>Bölümler
 `result` gereklidir. @No__t-0 değeri.

 `object1` gereklidir. Herhangi bir `Object` değişkeni veya ifadesi.

 `object2` gereklidir. Herhangi bir `Object` değişkeni veya ifadesi.

## <a name="remarks"></a>Açıklamalar
 @No__t-0 işleci, iki nesne başvurusunun farklı nesnelere başvuracağını belirler. Ancak, değer karşılaştırmaları gerçekleştirmez. @No__t-0 ve `object2` her ikisi de tam aynı nesne örneğine başvurur, `result` `False`; Aksi takdirde, @no__t 4 `True` ' tir.

 `IsNot`, `Is` işlecinin tersidir. @No__t-0 ' nın avantajı, okunması zor olabilecek `Not` ve `Is` ile garip söz dizimini önlemenize olanak sağlar.

 @No__t-0 ve `IsNot` işleçlerini kullanarak hem erken hem de geç bağlantılı nesneleri test edebilirsiniz.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, aynı karşılaştırmayı gerçekleştirmek için hem `Is` işlecini hem de `IsNot` işlecini kullanır.

 [!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]

## <a name="see-also"></a>Ayrıca bkz.

- [Is İşleci](is-operator.md)
- [TypeOf İşleci](typeof-operator.md)
- [Visual Basic operatör önceliği](operator-precedence.md)
- [Nasıl yapılır: Iki nesnenin aynı olup olmadığını test edin @ no__t-0
