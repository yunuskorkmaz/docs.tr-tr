---
title: "+= İşleci (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.+=
helpviewer_keywords:
- += operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- += operator [Visual Basic], appending strings
- compound assignment statements [Visual Basic]
ms.assetid: d3e959f4-85d4-4e47-87c4-77b62335a5b3
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4ac8f5679aa90c50c15c33a957cfc75d9ccecde6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a>+= İşleci (Visual Basic)
Sayısal bir ifadenin değerini sayısal değişken veya özellik değerine ekler ve değişken ya da özelliği için sonuç atar. Birleştirmek için de kullanılabilir bir `String` ifade bir `String` değişkeni veya özellik ve ata değişken veya özellik sonucu.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
variableorproperty += expression  
```  
  
## <a name="parts"></a>Bölümler  
 `variableorproperty`  
 Gerekli. Tüm sayısal veya `String` değişken veya özellik.  
  
 `expression`  
 Gerekli. Tüm sayısal veya `String` ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 Öğe sol tarafındaki `+=` işleci basit bir skaler değişkeni, bir özellik veya bir dizi öğesi olabilir. Değişken veya özellik olamaz [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 `+=` İşleci değeri değişken veya özellik, sol taraftaki sağındaki ekler ve değişkenin veya özelliğin, sol taraftaki sonucu atar. `+=` İşleci de kullanılabilir birleştirmek için `String` ifadesi, sağ taraftaki `String` değişken veya özelliği, solda ve ata değişkene sonuç veya kendi soldaki özelliği.  
  
> [!NOTE]
>  Kullandığınızda `+=` işleci, eklenmesi veya dize birleştirme oluşacaktır olup olmadığını belirlemek kuramıyor olabilir. Kullanım `&=` belirsizliği ortadan kaldırmak ve kendi kendine belgelendirme kod sağlamak için birleştirme için işleci.  
  
 Bu atama işleci derleme ortamı katı semantiği zorlarsa daraltma dönüşümleri değil ancak genişletme örtük olarak gerçekleştirir. Bu dönüştürme hakkında daha fazla bilgi için bkz: [Widening ve daraltma dönüşümleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md). Katı ve izin veren semantiği ile ilgili daha fazla bilgi için bkz: [Option Strict deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
 İzin veren semantiği izin veriliyorsa, `+=` işleci örtük olarak dize ve sayısal dönüşümler olanlar tarafından gerçekleştirilen özdeş çeşitli gerçekleştirir `+` işleci. Bu dönüştürme hakkında daha fazla bilgi için bkz: [+ işleci](../../../visual-basic/language-reference/operators/addition-operator.md).  
  
## <a name="overloading"></a>Aşırı Yükleme  
 `+` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir. Aşırı yükleme `+` işleci davranışını etkileyen `+=` işleci. Kodunuzu kullanıyorsa `+=` bir sınıf veya overloads yapısı `+`, yeniden tanımlanan davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `+=` bir değişkenin değerini başka bir işlemle birleştirme işleci. İlk bölümü kullanan `+=` sayısal değişkenleriyle başka bir değer ekleyin. İkinci bölümü'nü kullanan `+=` ile `String` başka bir değerle birleştirmek için değişkenleri. Her iki durumda da, sonuç ilk değişkene atanır.  
  
 [!code-vb[VbVbalrOperators#7](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-assignment-operator_1.vb)]  
  
 [!code-vb[VbVbalrOperators#8](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-assignment-operator_2.vb)]  
  
 Değeri `num1` 13 ve değerini sunulmuştur `str1` "103" sunulmuştur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [+ İşleci](../../../visual-basic/language-reference/operators/addition-operator.md)  
 [Atama İşleçleri](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [Aritmetik işleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Birleştirme işleçleri](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [İşlevselliğe göre listelenmiş işleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Deyimleri](../../../visual-basic/programming-guide/language-features/statements.md)
