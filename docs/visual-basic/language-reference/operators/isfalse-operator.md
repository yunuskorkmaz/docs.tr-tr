---
title: IsFalse İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: 85fd6b9264fa80c3636f2cb839c8fc5ed855ddc8
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965663"
---
# <a name="isfalse-operator-visual-basic"></a>IsFalse İşleci (Visual Basic)
Bir ifade olup olmadığını belirler `False`.  
  
 Çağıramazsınız `IsFalse` açıkça kodunuzu kullanabilirsiniz, ancak Visual Basic derleyici Bu kod oluşturmak için `AndAlso` yan tümceleri. Bir sınıf veya yapı tanımlayın ve ardından bu türde bir değişken kullanmak, bir `AndAlso` yan tümcesi tanımlamalıdır `IsFalse` Bu sınıf ya da yapı üzerinde.  
  
 Derleyici göz önünde bulundurur `IsFalse` ve `IsTrue` işleçleri bir *çifti eşleşen*. Başka bir deyişle, bir tanesi tanımlarsanız, ayrıca diğeri tanımladığınız gerekir.  
  
> [!NOTE]
>  `IsFalse` İşleci olabilir *aşırı*, kendi işleneninin türü, sınıfın veya yapının olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir. Kodunuz bu tür bir sınıf veya yapı üzerinde bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun. Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği için tanımları içeren bir yapının anahat tanımlar `IsFalse` ve `IsTrue` işleçleri.  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [IsTrue İşleci](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [Nasıl yapılır: Bir işleci tanımlama](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [AndAlso İşleci](../../../visual-basic/language-reference/operators/andalso-operator.md)
