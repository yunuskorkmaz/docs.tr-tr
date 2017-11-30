---
title: "IsNot İşleci (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.isnot
helpviewer_keywords: IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 969fdebdf15a1f779075c58616ccd16c64976a35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
  
 `IsNot`tam tersidir `Is` işleci. Avantajı `IsNot` garip sözdizimiyle önleyebilirsiniz olan `Not` ve `Is`, hangi okumak zor olabilir.  
  
 Kullanabileceğiniz `Is` ve `IsNot` bağlı erken ve geç bağlama nesnelerini test etmek için işleçler.  
  
> [!NOTE]
>  `IsNot` İşleci, döndürülen ifadeleri Karşılaştırılacak kullanılamaz `TypeOf` işleci. Bunun yerine, kullanmanız gereken `Not` ve `Is` işleçler.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, her ikisi de kullanır `Is` işleci ve `IsNot` aynı karşılaştırma gerçekleştirmek için işleci.  
  
 [!code-vb[VbVbalrOperators#29](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/isnot-operator_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Is işleci](../../../visual-basic/language-reference/operators/is-operator.md)  
 [TypeOf işleci](../../../visual-basic/language-reference/operators/typeof-operator.md)  
 [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Nasıl yapılır: iki nesnenin aynı olup olmadığını test etme](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
