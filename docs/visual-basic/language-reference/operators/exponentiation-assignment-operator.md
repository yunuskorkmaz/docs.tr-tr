---
title: ^= İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.^=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- ^= operator [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 397da132-2d96-4a85-a7bc-f7c730a608c9
ms.openlocfilehash: fe5e8fc2b64b9e7c33483612071d338a0ee22768
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331301"
---
# <a name="-operator-visual-basic"></a>^= İşleci (Visual Basic)
Bir değişkenin veya özelliğin değerini bir ifadenin gücüne yükseltir ve sonucu değişkene veya özelliğe geri atar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
variableorproperty ^= expression  
```  
  
## <a name="parts"></a>Bölümler  
 `variableorproperty`  
 Gerekli. Herhangi bir sayısal değişken veya özellik.  
  
 `expression`  
 Gerekli. Herhangi bir sayısal ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 `^=` işlecinin sol tarafındaki öğe basit bir skaler değişken, bir özellik veya bir dizi öğesi olabilir. Değişken veya özellik [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)olamaz.  
  
 `^=` işleci ilk olarak, değişkenin veya özelliğin değerini (işlecin sol tarafında) ifadenin değerinin (işlecinin sağ tarafında) kuvvetine yükseltir (işlecin sağ tarafındaki). İşleci daha sonra bu işlemin sonucunu değişkenine veya özelliğe geri atar.  
  
 Visual Basic her zaman [Double veri türünde](../../../visual-basic/language-reference/data-types/double-data-type.md)üs gerçekleştirir. Farklı türdeki işlenenler `Double`dönüştürülür ve sonuç her zaman `Double`.  
  
 `expression` değeri kesirli, negatif veya her ikisi olabilir.  
  
## <a name="overloading"></a>Aşırı Yükleme  
 [^ İşleci](../../../visual-basic/language-reference/operators/exponentiation-operator.md) *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. `^` işleci aşırı yükleme `^=` işlecinin davranışını etkiler. Kodunuz, `^`aşırı yükleyen bir sınıf veya yapı üzerinde `^=` kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir `Integer` değişkeninin değerini ikinci bir değişkenin gücüne yükseltmek ve sonucu ilk değişkene atamak için `^=` işlecini kullanır.  
  
 [!code-vb[VbVbalrOperators#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [^ İşleci](../../../visual-basic/language-reference/operators/exponentiation-operator.md)
- [Atama İşleçleri](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Aritmetik İşleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Deyimler](../../../visual-basic/programming-guide/language-features/statements.md)
