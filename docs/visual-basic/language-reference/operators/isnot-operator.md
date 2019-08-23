---
title: IsNot İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: 0a83b48e5e415bd6ca0c777cef6d34f7127691b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966931"
---
# <a name="isnot-operator-visual-basic"></a>IsNot İşleci (Visual Basic)
İki nesne başvuru değişkenini karşılaştırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
result = object1 IsNot object2  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Gerekli. Bir `Boolean` değer.  
  
 `object1`  
 Gerekli. Herhangi `Object` bir değişken veya ifade.  
  
 `object2`  
 Gerekli. Herhangi `Object` bir değişken veya ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 `IsNot` İşleci iki nesne başvurusunun farklı nesnelere başvuracağını belirler. Ancak, değer karşılaştırmaları gerçekleştirmez. `object1` Ve her`object2` ikisi de`result` tam aynınesne`result` örneğine `False` başvurur,`True`ise, olur.  
  
 `IsNot`, `Is` işlecinin tersidir. ' Nin `IsNot` avantajı, ve ile `Not` garip söz dizimini önlemenize ve `Is`bu da okunması zor olabilir.  
  
 `Is` Ve`IsNot` işleçlerini, hem erken hem de geç bağlantılı nesneleri test etmek için kullanabilirsiniz.  
  
> [!NOTE]
> `IsNot` İşleç ,`TypeOf` işleçten döndürülen ifadeleri karşılaştırmak için kullanılamaz. Bunun yerine, `Not` ve `Is` işleçlerini kullanmanız gerekir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği aynı karşılaştırmayı başarmak için `Is` hem işlecini `IsNot` hem de işlecini kullanır.  
  
 [!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Is İşleci](../../../visual-basic/language-reference/operators/is-operator.md)
- [TypeOf İşleci](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Nasıl yapılır: Iki nesnenin aynı olup olmadığını test etme](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
