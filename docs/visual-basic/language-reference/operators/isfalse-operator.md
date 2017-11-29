---
title: "IsFalse İşleci (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d85fc51a75f82c65cf226b8239a8eee6585bd18a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [IsTrue işleci](../../../visual-basic/language-reference/operators/istrue-operator.md)  
 [Nasıl yapılır: bir işleci tanımlama](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [AndAlso işleci](../../../visual-basic/language-reference/operators/andalso-operator.md)
