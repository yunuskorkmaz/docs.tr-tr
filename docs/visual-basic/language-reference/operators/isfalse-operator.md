---
title: IsFalse İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: e84b2162eb0763725f05bc52d5c4223d7c430b81
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="isfalse-operator-visual-basic"></a>IsFalse İşleci (Visual Basic)
Bir ifade olup olmadığını belirleyen `False`.  
  
 Çağıramazsınız `IsFalse` açıkça kodunuzu, ancak Visual Basic derleyici koddan oluşturmak için kullanabilmesi `AndAlso` yan tümceleri. Bir sınıf veya yapı tanımlayın ve ardından bu tür bir değişken kullanırsanız bir `AndAlso` yan tümcesi tanımlamalıdır `IsFalse` sınıf veya yapı.  
  
 Derleyici göz önünde bulundurur `IsFalse` ve `IsTrue` işletmenler olarak bir *çifti eşleşen*. Bu, bunlardan birini tanımlarsanız, ayrıca diğeri tanımlamanız gerektiğini anlamına gelir.  
  
> [!NOTE]
>  `IsFalse` İşleci olabilir *aşırı*, kendi işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir. Bu tür bir sınıf veya yapı üzerinde kodunuzu bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği için tanımları içeren bir yapı özetini tanımlar `IsFalse` ve `IsTrue` işleçler.  
  
 [!code-vb[VbVbalrOperators#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/isfalse-operator_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IsTrue İşleci](../../../visual-basic/language-reference/operators/istrue-operator.md)  
 [Nasıl yapılır: İşleç Tanımlama](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [AndAlso İşleci](../../../visual-basic/language-reference/operators/andalso-operator.md)
