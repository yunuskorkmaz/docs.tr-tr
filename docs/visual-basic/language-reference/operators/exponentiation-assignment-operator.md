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
ms.openlocfilehash: a956ffdaa3456ed09443f25c3383b6aab52fb5bf
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867056"
---
# <a name="-operator-visual-basic"></a>^= İşleci (Visual Basic)

Bir değişkenin veya özelliğin değerini bir ifadenin gücüne yükseltir ve sonucu değişkene veya özelliğe geri atar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
variableorproperty ^= expression  
```  
  
## <a name="parts"></a>Bölümler  

 `variableorproperty`  
 Gereklidir. Herhangi bir sayısal değişken veya özellik.  
  
 `expression`  
 Gereklidir. Herhangi bir sayısal ifade.  
  
## <a name="remarks"></a>Açıklamalar  

 İşlecinin sol tarafındaki öğesi `^=` basit bir skaler değişken, bir özellik veya bir dizi öğesi olabilir. Değişken veya özellik [ReadOnly](../modifiers/readonly.md)olamaz.  
  
 `^=`İşleci ilk olarak, değişkenin veya özelliğin değerini (işlecin sol tarafında) ifadenin değerinin (işlecin sağ tarafında) kuvvetine yükseltir.. İşleci daha sonra bu işlemin sonucunu değişkenine veya özelliğe geri atar.  
  
 Visual Basic her zaman [Double veri türünde](../data-types/double-data-type.md)üs gerçekleştirir. Farklı türdeki işlenenler öğesine dönüştürülür `Double` ve sonuç her zaman olur `Double` .  
  
 Değeri `expression` kesirli, negatif veya her ikisi olabilir.  
  
## <a name="overloading"></a>Aşırı Yükleme  

 [^ İşleci](exponentiation-operator.md) *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. İşleci aşırı yüklemek `^` işlecin davranışını etkiler `^=` . Kodunuzun `^=` bir sınıf veya yapı üzerinde kullanması durumunda `^` , yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `^=` bir `Integer` değişkenin değerini ikinci bir değişkenin gücüne yükseltmek ve sonucu ilk değişkene atamak için işlecini kullanır.  
  
 [!code-vb[VbVbalrOperators#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [^ İşleci](exponentiation-operator.md)
- [Atama Işleçleri](assignment-operators.md)
- [Aritmetik Işleçler](arithmetic-operators.md)
- [Visual Basic'de İşleç Önceliği](operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](operators-listed-by-functionality.md)
- [Deyimler](../../programming-guide/language-features/statements.md)
