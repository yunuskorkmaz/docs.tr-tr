---
title: "IsTrue İşleci (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c0d261186ce68f06cec95251e815248a189f6da5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="istrue-operator-visual-basic"></a>IsTrue İşleci (Visual Basic)
Bir ifade olup olmadığını belirleyen `True`.  
  
 Çağıramazsınız `IsTrue` açıkça kodunuzu, ancak Visual Basic derleyici koddan oluşturmak için kullanabilmesi `OrElse` yan tümceleri. Bir sınıf veya yapı tanımlayın ve ardından bu tür bir değişken kullanırsanız bir `OrElse` yan tümcesi tanımlamalıdır `IsTrue` sınıf veya yapı.  
  
 Derleyici göz önünde bulundurur `IsTrue` ve `IsFalse` işletmenler olarak bir *çifti eşleşen*. Bu, bunlardan birini tanımlarsanız, ayrıca diğeri tanımlamanız gerektiğini anlamına gelir.  
  
## <a name="compiler-use-of-istrue"></a>IsTrue derleyici kullanımı  
 Bir sınıf veya yapı tanımlandığında, bu tür bir değişkeni kullanabilirsiniz bir `For`, `If`, `Else``If`, veya `While` deyimi, veya bir `When` yan tümcesi. Bunu yaparsanız, derleyici, türe dönüştürür bir işleç gerektiren bir `Boolean` bir koşulu test etmek için değer. Uygun bir işleç aşağıdaki sırayla arar:  
  
1.  Sınıf veya yapı için bir genişletme dönüşüm işleci `Boolean`.  
  
2.  Sınıf veya yapı için bir genişletme dönüşüm işleci `Boolean?`.  
  
3.  `IsTrue` Sınıf veya yapı işlecinin.  
  
4.  Daraltma dönüştürmeye `Boolean?` dönüştürme kapsamaz `Boolean` için `Boolean?`.  
  
5.  Sınıf veya yapı için daraltma bir dönüşüm işleci `Boolean`.  
  
 Herhangi bir dönüştürmeye tanımladıysanız `Boolean` veya bir `IsTrue` işleci, derleyici, bir hata bildirir.  
  
> [!NOTE]
>  `IsTrue` İşleci olabilir *aşırı*, kendi işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir. Bu tür bir sınıf veya yapı üzerinde kodunuzu bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği için tanımları içeren bir yapı özetini tanımlar `IsFalse` ve `IsTrue` işleçler.  
  
 [!code-vb[VbVbalrOperators#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/istrue-operator_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IsFalse işleci](../../../visual-basic/language-reference/operators/isfalse-operator.md)  
 [Nasıl yapılır: bir işleci tanımlama](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [OrElse işleci](../../../visual-basic/language-reference/operators/orelse-operator.md)
