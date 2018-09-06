---
title: IsTrue İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
ms.openlocfilehash: bf81384b0cecfd1ee3d438e4463949381279a181
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43785198"
---
# <a name="istrue-operator-visual-basic"></a>IsTrue İşleci (Visual Basic)
Bir ifade olup olmadığını belirler `True`.  
  
 Çağıramazsınız `IsTrue` açıkça kodunuzu kullanabilirsiniz, ancak Visual Basic derleyici Bu kod oluşturmak için `OrElse` yan tümceleri. Bir sınıf veya yapı tanımlayın ve ardından bu türde bir değişken kullanmak, bir `OrElse` yan tümcesi tanımlamalıdır `IsTrue` Bu sınıf ya da yapı üzerinde.  
  
 Derleyici göz önünde bulundurur `IsTrue` ve `IsFalse` işleçleri bir *çifti eşleşen*. Başka bir deyişle, bir tanesi tanımlarsanız, ayrıca diğeri tanımladığınız gerekir.  
  
## <a name="compiler-use-of-istrue"></a>IsTrue derleyici kullanımı  
 Bir sınıf veya yapı tanımlandığında, bu türde bir değişken kullanabileceğiniz bir `For`, `If`, `Else If`, veya `While` deyimi veya bir `When` yan tümcesi. Bunu yaparsanız, derleyici, türüne dönüştürür bir işleç gerektiriyor. bir `Boolean` koşul sınayabilmeniz değeri. Uygun bir işleç şu sırayla arar:  
  
1.  Genişleyen bir dönüştürme operatörünün sınıfı veya yapısına `Boolean`.  
  
2.  Genişleyen bir dönüştürme operatörünün sınıfı veya yapısına `Boolean?`.  
  
3.  `IsTrue` İşleci, sınıf ya da yapı üzerinde.  
  
4.  Bir daraltma dönüşümü için `Boolean?` , değil içeren bir dönüştürme `Boolean` için `Boolean?`.  
  
5.  Bir daraltma dönüşümü işleci sınıfı veya yapısına `Boolean`.  
  
 Herhangi bir dönüştürmeyi tanımlamadıysanız `Boolean` veya `IsTrue` işleci, derleyici bir hata bildirir.  
  
> [!NOTE]
>  `IsTrue` İşleci olabilir *aşırı*, kendi işleneninin türü, sınıfın veya yapının olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir. Kodunuz bu tür bir sınıf veya yapı üzerinde bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun. Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği için tanımları içeren bir yapının anahat tanımlar `IsFalse` ve `IsTrue` işleçleri.  
  
 [!code-vb[VbVbalrOperators#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/istrue-operator_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IsFalse İşleci](../../../visual-basic/language-reference/operators/isfalse-operator.md)  
 [Nasıl yapılır: İşleç Tanımlama](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [OrElse İşleci](../../../visual-basic/language-reference/operators/orelse-operator.md)
