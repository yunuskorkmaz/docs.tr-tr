---
title: IsNot İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: e07a775eec003a3e488f6909181aed3f742b4b91
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58833522"
---
# <a name="isnot-operator-visual-basic"></a>IsNot İşleci (Visual Basic)
İki nesne başvurusu değişkenini karşılaştırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
result = object1 IsNot object2  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Gerekli. A `Boolean` değeri.  
  
 `object1`  
 Gerekli. Tüm `Object` değişkenin veya ifadenin.  
  
 `object2`  
 Gerekli. Tüm `Object` değişkenin veya ifadenin.  
  
## <a name="remarks"></a>Açıklamalar  
 `IsNot` İşleci belirleyen iki nesne başvuru farklı nesnelere başvuru değilse. Ancak, değer karşılaştırmaları gerçekleştirmez. Varsa `object1` ve `object2` hem de tam aynı nesne örneği için bkz `result` olduğu `False`; Eğer öyleyse, `result` olduğu `True`.  
  
 `IsNot` tersidir `Is` işleci. Avantajı `IsNot` garip söz dizimiyle kaçınabilirsiniz olan `Not` ve `Is`, hangi okumak zor olabilir.  
  
 Kullanabileceğiniz `Is` ve `IsNot` hem erken bağlanmış ve geç bağlama nesnelerini test etmek için işleçler.  
  
> [!NOTE]
>  `IsNot` Döndürüldüğü ifadeleri karşılaştırma işleci kullanılamaz `TypeOf` işleci. Bunun yerine, kullanmalısınız `Not` ve `Is` işleçleri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, hem de kullandığı `Is` işleci ve `IsNot` aynı karşılaştırma gerçekleştirmek için işleci.  
  
 [!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Is İşleci](../../../visual-basic/language-reference/operators/is-operator.md)
- [TypeOf İşleci](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Nasıl yapılır: İki nesnenin aynı olup olmadığını test etme](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
