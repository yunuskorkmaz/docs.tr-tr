---
title: IsTrue İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
ms.openlocfilehash: 1152f4b512a85ae183f8fc8d476b69685e2926ef
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966913"
---
# <a name="istrue-operator-visual-basic"></a>IsTrue İşleci (Visual Basic)
Bir ifadenin `True`olup olmadığını belirler.  
  
 Kodunuzda açıkça çağrı `IsTrue` yapılamaz, ancak Visual Basic Derleyicisi bunu yan tümcelerden `OrElse` kod oluşturmak için kullanabilir. Bir sınıf veya yapı tanımlayabilir ve sonra bir `OrElse` yan tümce içinde bu türden bir değişken kullanırsanız, bu sınıf veya yapıda tanımlamanız `IsTrue` gerekir.  
  
 Derleyici, `IsTrue` ve `IsFalse` işleçlerini eşleşen bir *çift*olarak değerlendirir. Diğer bir deyişle, bunlardan birini tanımlarsanız, diğerini de tanımlamanız gerekir.  
  
## <a name="compiler-use-of-istrue"></a>Iıstrue derleyicisi kullanımı  
 Bir sınıf veya yapı tanımladığınızda,,, `For` `Else If`, veya `While` deyimi içinde `If`veya `When` yan tümcesinde bu türde bir değişken kullanabilirsiniz. Bunu yaparsanız, derleyici, bir koşulu test edebilmesi için türünüzü bir `Boolean` değere dönüştüren bir operatör gerektirir. Uygun bir işleci aşağıdaki sırayla arar:  
  
1. Sınıfınız veya yapıınızdan ' ye `Boolean`genişleyen bir dönüştürme işleci.  
  
2. Sınıfınız veya yapıınızdan ' ye `Boolean?`genişleyen bir dönüştürme işleci.  
  
3. Sınıfınıza veya yapınıza yönelik operatör.`IsTrue`  
  
4. ' A bir `Boolean` dönüştürme içermeyen bir daraltma dönüştürmesi `Boolean?` `Boolean?`.  
  
5. Sınıfınız veya yapıınızdan ' ye `Boolean`bir daraltma dönüştürme işleci.  
  
 `Boolean` Yadaişlecineherhangibirdönüştürmetanımdıysanız,`IsTrue` derleyici bir hata bildirir.  
  
> [!NOTE]
> İşleç aşırı yüklenebilir, yani işleneni Bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. `IsTrue` Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, `IsFalse` ve `IsTrue` işleçleri için tanımlar içeren bir yapının ana hattını tanımlar.  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IsFalse İşleci](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [Nasıl yapılır: Bir Işleç tanımlayın](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [OrElse İşleci](../../../visual-basic/language-reference/operators/orelse-operator.md)
