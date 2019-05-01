---
title: Is İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
ms.openlocfilehash: a59ff4c956724c614342f0ee4c0622a67f1c25e7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054975"
---
# <a name="is-operator-visual-basic"></a>Is İşleci (Visual Basic)
İki nesne başvurusu değişkenini karşılaştırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
result = object1 Is object2  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Gerekli. Tüm `Boolean` değeri.  
  
 `object1`  
 Gerekli. Tüm `Object` adı.  
  
 `object2`  
 Gerekli. Tüm `Object` adı.  
  
## <a name="remarks"></a>Açıklamalar  
 `Is` İşleci iki nesne başvurusunun aynı nesneye başvuruyorsa, belirler. Ancak, değer karşılaştırmaları gerçekleştirmez. Varsa `object1` ve `object2` hem de tam aynı nesne örneği için bkz `result` olduğu `True`; Eğer öyleyse, `result` olduğu `False`.  
  
 `Is` ile de kullanılabilir `TypeOf` yapmak için anahtar sözcüğü bir `TypeOf`... `Is` ifadesi, bir nesne değişkeninin veri türü ile uyumlu olup olmadığını test eder.  
  
> [!NOTE]
>  `Is` Anahtar sözcüğü kullanılan ayrıca [seçin... Case deyimi](../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `Is` nesne başvuruları çiftlerini karşılaştırmak için işleci. Sonuçları atanan bir `Boolean` iki nesnenin aynı olup olmadığını değerini temsil eden.  
  
 [!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]  
  
 Yukarıdaki örnekte de gösterildiği gibi kullanabileceğiniz `Is` işleci hem de test etmek için erken bağlı ve nesneler'geç bağlama.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [TypeOf İşleci](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [IsNot İşleci](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Visual Basic'de Karşılaştırma işleçleri](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [İşleçler ve İfadeler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
