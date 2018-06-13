---
title: IsNot İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: babee364d350ca84a8379f675acc4b5c87f98303
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603320"
---
# <a name="isnot-operator-visual-basic"></a>IsNot İşleci (Visual Basic)
İki nesne başvuru değişkenini karşılaştırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
result = object1 IsNot object2  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Gerekli. A `Boolean` değeri.  
  
 `object1`  
 Gerekli. Tüm `Object` değişken veya ifade.  
  
 `object2`  
 Gerekli. Tüm `Object` değişken veya ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 `IsNot` İşleci belirleyen iki nesne başvuruları farklı nesnelere atıfta durumunda. Ancak, değer karşılaştırmaları gerçekleştirmez. Varsa `object1` ve `object2` hem de tam aynı nesne örneği için bkz `result` olan `False`; yoksa `result` olan `True`.  
  
 `IsNot` tam tersidir `Is` işleci. Avantajı `IsNot` garip sözdizimiyle önleyebilirsiniz olan `Not` ve `Is`, hangi okumak zor olabilir.  
  
 Kullanabileceğiniz `Is` ve `IsNot` bağlı erken ve geç bağlama nesnelerini test etmek için işleçler.  
  
> [!NOTE]
>  `IsNot` İşleci, döndürülen ifadeleri Karşılaştırılacak kullanılamaz `TypeOf` işleci. Bunun yerine, kullanmanız gereken `Not` ve `Is` işleçler.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, her ikisi de kullanır `Is` işleci ve `IsNot` aynı karşılaştırma gerçekleştirmek için işleci.  
  
 [!code-vb[VbVbalrOperators#29](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/isnot-operator_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Is İşleci](../../../visual-basic/language-reference/operators/is-operator.md)  
 [TypeOf İşleci](../../../visual-basic/language-reference/operators/typeof-operator.md)  
 [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Nasıl yapılır: İki Nesnenin Aynı Olup Olmadığını Test Etme](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
