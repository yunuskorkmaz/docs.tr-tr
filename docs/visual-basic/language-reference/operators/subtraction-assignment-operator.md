---
title: -= İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.-=
helpviewer_keywords:
- -= operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator -=
- compound assignment statements [Visual Basic]
ms.assetid: 5ead0c37-ae50-48f7-8435-8e341d81cae1
ms.openlocfilehash: 4f403cd8a28f8d9d0ba1d24b0792a352a9c961db
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406411"
---
# <a name="--operator-visual-basic"></a>-= İşleci (Visual Basic)
Bir ifadenin değerini bir değişkenin veya özelliğin değerinden çıkartır ve sonucu değişkenine veya özelliğe atar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
variableorproperty -= expression  
```  
  
## <a name="parts"></a>Bölümler  
 `variableorproperty`  
 Gereklidir. Herhangi bir sayısal değişken veya özellik.  
  
 `expression`  
 Gereklidir. Herhangi bir sayısal ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 İşlecinin sol tarafındaki öğesi `-=` basit bir skaler değişken, bir özellik veya bir dizi öğesi olabilir. Değişken veya özellik [ReadOnly](../modifiers/readonly.md)olamaz.  
  
 `-=`İşleci ilk olarak, ifadenin değerini (işlecin sağ tarafında) değişkenin veya özelliğin değerinden (işlecin sol tarafında) çıkartır (işlecinin sol tarafındaki). İşleci daha sonra bu işlemin sonucunu değişkenine veya özelliğe atar.  
  
## <a name="overloading"></a>Aşırı Yükleme  
 [-İşleci (Visual Basic)](subtraction-operator.md) *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. İşleci aşırı yüklemek `-` işlecin davranışını etkiler `-=` . Kodunuzun `-=` bir sınıf veya yapı üzerinde kullanması durumunda `-` , yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir `-=` değişkeni diğerinden çıkarmak için işlecini kullanır `Integer` ve sonucu ikinci değişkene atar.  
  
 [!code-vb[VbVbalrOperators#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#11)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [-İşleci (Visual Basic)](subtraction-operator.md)
- [Atama Işleçleri](assignment-operators.md)
- [Aritmetik İşleçler](arithmetic-operators.md)
- [Visual Basic'de İşleç Önceliği](operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](operators-listed-by-functionality.md)
- [Deyimler](../../programming-guide/language-features/statements.md)
