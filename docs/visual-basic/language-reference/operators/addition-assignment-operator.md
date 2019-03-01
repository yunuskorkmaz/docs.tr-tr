---
title: += İşleci (Visual Basic)
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
ms.openlocfilehash: 7fdf5cd422cf2a4081372bc14e74ed7463393520
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979859"
---
# <a name="-operator-visual-basic"></a>+= İşleci (Visual Basic)
Sayısal bir ifadenin değerini sayısal değişken veya özellik değerine ekler ve sonucu değişken veya özellik atar. Birleştirmek için de kullanılabilir bir `String` ifade bir `String` değişken veya özellik ve ata değişken veya özellik sonucu.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
variableorproperty += expression  
```  
  
## <a name="parts"></a>Bölümler  
 `variableorproperty`  
 Gerekli. Herhangi bir sayısal veya `String` değişken veya özellik.  
  
 `expression`  
 Gerekli. Herhangi bir sayısal veya `String` ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 Öğe sol tarafındaki `+=` işleci, bir basit skaler değişkeni, bir özellik veya dizi öğesi olabilir. Değişken veya özellik olamaz [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 `+=` İşleci sağındakiyle değişken veya özellik, sol taraftaki değer ekler ve sonucu bir değişken veya özellik, sol taraftaki atar. `+=` İşleci de kullanılabilir birleştirmek için `String` sağındakiyle için ifade `String` değişken veya özelliği, solda ve sonucu bir değişkene atayın ya da, sol taraftaki özellik.  
  
> [!NOTE]
>  Kullanırken `+=` işleci, yükleyemeyebilir eklenmesi veya dize birleştirme gerçekleşip gerçekleşmeyeceğini belirlemek. Kullanım `&=` birleştirme için işleç belirsizliği ortadan kaldırmak ve kendi kendine belgelendirme kodu sağlayabilir.  
  
 Bu atama işleci örtük olarak derleme ortamı katı semantiklerini zorlarsa daraltma dönüşümleri değil ancak genişletme gerçekleştirir. Bu dönüştürmeler hakkında daha fazla bilgi için bkz. [Widening ve daraltma dönüşümleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md). Katı ve esnek semantiği hakkında daha fazla bilgi için bkz. [Option Strict deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
 Esnek semantiği izin veriliyorsa `+=` işleci, örtük olarak olanlar tarafından gerçekleştirilen aynı dize ve sayısal dönüştürmeler çeşitli gerçekleştirir `+` işleci. Bu dönüştürmeler hakkında daha fazla bilgi için bkz: [+ işleci](../../../visual-basic/language-reference/operators/addition-operator.md).  
  
## <a name="overloading"></a>Aşırı Yükleme  
 `+` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir. Aşırı yükleme `+` işleci davranışını etkileyen `+=` işleci. Kodunuzu kullanıyorsa `+=` bir sınıf veya aşırı yapısı `+`, yeniden tanımlanan davranışını anladığınızdan emin olun. Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `+=` bir değişkenin değerini diğeriyle birleştirmek için işleci. İlk bölümü kullanan `+=` sayısal değişkenleriyle başka bir değer ekleyin. İkinci bölümü'nü kullanan `+=` ile `String` başka bir değerle birleştirilecek değişkenleri. Her iki durumda da sonucu ilk değişkenine atanır.  
  
 [!code-vb[VbVbalrOperators#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#7)]  
  
 [!code-vb[VbVbalrOperators#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#8)]  
  
 Değerini `num1` 13 ve değerini sunulmuştur `str1` "103" sunulmuştur.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [+ İşleci](../../../visual-basic/language-reference/operators/addition-operator.md)
- [Atama İşleçleri](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Aritmetik İşleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Birleştirme İşleçleri](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Deyimler](../../../visual-basic/programming-guide/language-features/statements.md)
