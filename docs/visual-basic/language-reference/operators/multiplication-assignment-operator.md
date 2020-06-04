---
title: '*= İşleci'
ms.date: 07/20/2015
f1_keywords:
- vb.*=
helpviewer_keywords:
- operator *=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '*= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 96c86509-6eb8-4682-8226-3852e049376f
ms.openlocfilehash: b06ebcb4f4100a0621f52a769543c0fb24fbb4bf
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401504"
---
# <a name="-operator-visual-basic"></a>*= İşleci (Visual Basic)
Bir değişkenin veya özelliğin değerini bir ifadenin değeri ile çarpar ve sonucu değişkenine veya özelliğe atar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
variableorproperty *= expression  
```  
  
## <a name="parts"></a>Bölümler  
 `variableorproperty`  
 Gereklidir. Herhangi bir sayısal değişken veya özellik.  
  
 `expression`  
 Gereklidir. Herhangi bir sayısal ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 İşlecinin sol tarafındaki öğesi `*=` basit bir skaler değişken, bir özellik veya bir dizi öğesi olabilir. Değişken veya özellik [ReadOnly](../modifiers/readonly.md)olamaz.  
  
 `*=`İşleci ilk olarak, ifadenin değerini (işlecin sağ tarafında) değişkenin veya özelliğin değeri (işlecin sol tarafında) ile çarpar. İşleci daha sonra bu işlemin sonucunu değişkenine veya özelliğe atar.  
  
## <a name="overloading"></a>Aşırı Yükleme  
 [* İşleci](multiplication-operator.md) *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. İşleci aşırı yüklemek `*` işlecin davranışını etkiler `*=` . Kodunuzun `*=` bir sınıf veya yapı üzerinde kullanması durumunda `*` , yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `*=` bir `Integer` değişkeni ikinci olarak çarpmak ve sonucu ilk değişkene atamak için işlecini kullanır.  
  
 [!code-vb[VbVbalrOperators#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [* İşleci](multiplication-operator.md)
- [Atama Işleçleri](assignment-operators.md)
- [Aritmetik İşleçler](arithmetic-operators.md)
- [Visual Basic'de İşleç Önceliği](operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](operators-listed-by-functionality.md)
- [Deyimler](../../programming-guide/language-features/statements.md)
