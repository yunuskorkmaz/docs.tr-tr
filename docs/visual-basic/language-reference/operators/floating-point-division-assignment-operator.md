---
description: Hakkında daha fazla bilgi edinin:/= Işleci (Visual Basic)
title: /= İşleci
ms.date: 07/20/2015
f1_keywords:
- vb./=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- /= operator [Visual Basic]
- operator /=
- compound assignment statements [Visual Basic]
ms.assetid: a1e22d0e-8380-4761-9da1-84fb51c34821
ms.openlocfilehash: 3020372be18f554df18fa6dac539ab9d0b2f725e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666036"
---
# <a name="-operator-visual-basic"></a>/= İşleci (Visual Basic)

Bir değişkenin veya özelliğin değerini bir ifadenin değerine böler ve kayan nokta sonucunu değişkenine veya özelliğe atar.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
variableorproperty /= expression  
```  
  
## <a name="parts"></a>Bölümler  

 `variableorproperty`  
 Gereklidir. Herhangi bir sayısal değişken veya özellik.  
  
 `expression`  
 Gereklidir. Herhangi bir sayısal ifade.  
  
## <a name="remarks"></a>Açıklamalar  

 İşlecinin sol tarafındaki öğesi `/=` basit bir skaler değişken, bir özellik veya bir dizi öğesi olabilir. Değişken veya özellik [ReadOnly](../modifiers/readonly.md)olamaz.  
  
 `/=`İşleci ilk olarak, değişkenin değerini (işlecin sol tarafında), ifadenin değerine (işlecinin sağ tarafında) böler (işleci). İşleci daha sonra bu işlemin kayan nokta sonucunu değişkenine veya özelliğe atar.  
  
 Bu ifade `Double` , sol taraftaki değişkene veya özelliğe bir değer atar. İse `Option Strict` `On` , `variableorproperty` bir olmalıdır `Double` . `Option Strict`İse, `Off` Visual Basic örtük bir dönüştürme gerçekleştirir ve elde edilen değeri `variableorproperty` çalışma zamanında olası bir hatayla atar. Daha fazla bilgi için bkz. [genişletme ve daraltma dönüştürmeleri](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) ve [Option Strict deyimdir](../statements/option-strict-statement.md).  
  
## <a name="overloading"></a>Aşırı Yükleme  

 [/İşleci (Visual Basic)](floating-point-division-operator.md) *aşırı* yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. İşleci aşırı yüklemek `/` işlecin davranışını etkiler `/=` . Kodunuzun `/=` bir sınıf veya yapı üzerinde kullanması durumunda `/` , yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `/=` bir `Integer` değişkeni ikinci bir kez bölmek ve bölümü ilk değişkene atamak için işlecini kullanır.  
  
 [!code-vb[VbVbalrOperators#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [/İşleci (Visual Basic)](floating-point-division-operator.md)
- [\\= İşleci](integer-division-assignment-operator.md)
- [Atama Işleçleri](assignment-operators.md)
- [Aritmetik Işleçler](arithmetic-operators.md)
- [Visual Basic'de İşleç Önceliği](operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](operators-listed-by-functionality.md)
- [Deyimler](../../programming-guide/language-features/statements.md)
