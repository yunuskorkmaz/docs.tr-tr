---
title: += İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.+=
helpviewer_keywords:
- += operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- += operator [Visual Basic], appending strings
- compound assignment statements [Visual Basic]
ms.assetid: d3e959f4-85d4-4e47-87c4-77b62335a5b3
ms.openlocfilehash: c2ce384901a9f0207e8279a5a07a88600c875e7f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372213"
---
# <a name="-operator-visual-basic"></a>+= İşleci (Visual Basic)
Sayısal bir ifadenin değerini bir sayısal değişkenin veya özelliğin değerine ekler ve sonucu değişkenine veya özelliğe atar. , Bir `String` ifadeyi bir `String` değişkene veya özelliğe birleştirmek ve sonucu değişkene veya özelliğe atamak için de kullanılabilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
variableorproperty += expression  
```  
  
## <a name="parts"></a>Bölümler  
 `variableorproperty`  
 Gereklidir. Herhangi bir sayısal veya `String` değişken veya özellik.  
  
 `expression`  
 Gereklidir. Herhangi bir sayısal or `String` ifadesi.  
  
## <a name="remarks"></a>Açıklamalar  
 İşlecinin sol tarafındaki öğesi `+=` basit bir skaler değişken, bir özellik veya bir dizi öğesi olabilir. Değişken veya özellik [ReadOnly](../modifiers/readonly.md)olamaz.  
  
 `+=`İşleci, solundaki değeri, sol taraftaki değişkene veya özelliğe ekler ve sonucu, sol tarafında değişkenine veya özelliğe atar. `+=`İşleci Ayrıca, sol tarafında bulunan `String` değişken veya özellik için ifadeyi sağ tarafta birleştirmek `String` ve sonucu, sol tarafında değişken veya özelliğe atar.  
  
> [!NOTE]
> `+=`İşlecini kullandığınızda, ekleme veya dize birleştirme işleminin yapılıp yapılmayacağını belirleyemeyebilirsiniz. `&=`Belirsizliği ortadan kaldırmak ve kendi kendine belgeleme kodu sağlamak için birleştirme işlecini kullanın.  
  
 Bu atama işleci, derleme ortamı katı semantiği zorlarsa, örtülü olarak genişleyen ancak daraltma dönüştürmesi gerçekleştirmez. Bu dönüşümler hakkında daha fazla bilgi için bkz. [genişletme ve daraltma dönüştürmeleri](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md). Katı ve izin veren semantiği hakkında daha fazla bilgi için bkz. [Option Strict deyimin](../statements/option-strict-statement.md).  
  
 İzin verilen semantiğe izin veriliyorsa, `+=` işleç örtük olarak işleç tarafından gerçekleştirenlerle aynı şekilde çeşitli dize ve sayısal dönüşümler gerçekleştirir `+` . Bu dönüşümlerde Ayrıntılar için bkz. [+ işleci](addition-operator.md).  
  
## <a name="overloading"></a>Aşırı Yükleme  
 `+`İşleç *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. İşleci aşırı yüklemek `+` işlecin davranışını etkiler `+=` . Kodunuzun `+=` bir sınıf veya yapı üzerinde kullanması durumunda `+` , yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `+=` bir değişkenin değerini diğeri ile birleştirmek için işlecini kullanır. İlk bölüm, bir `+=` değeri başka bir değer eklemek için sayısal değişkenlerle birlikte kullanır. İkinci bölüm, `+=` `String` bir değeri başka bir değerle birleştirmek için değişkenlerle birlikte kullanır. Her iki durumda da sonuç ilk değişkene atanır.  
  
 [!code-vb[VbVbalrOperators#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#7)]  
  
 [!code-vb[VbVbalrOperators#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#8)]  
  
 Değeri `num1` artık 13 ' dir ve değeri `str1` artık "103".  
  
## <a name="see-also"></a>Ayrıca bkz.

- [+ İşleci](addition-operator.md)
- [Atama Işleçleri](assignment-operators.md)
- [Aritmetik İşleçler](arithmetic-operators.md)
- [Birleştirme İşleçleri](concatenation-operators.md)
- [Visual Basic'de İşleç Önceliği](operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](operators-listed-by-functionality.md)
- [Deyimler](../../programming-guide/language-features/statements.md)
