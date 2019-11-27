---
title: IsTrue İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
ms.openlocfilehash: 4b863eed8406a10b9a44d7139f8659ac5cb758ad
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349508"
---
# <a name="istrue-operator-visual-basic"></a>IsTrue İşleci (Visual Basic)
Bir ifadenin `True`olup olmadığını belirler.  
  
 Kodunuzda açıkça `IsTrue` çağrılamaz, ancak Visual Basic Derleyicisi bunu `OrElse` yan tümcelerinden kod oluşturmak için kullanabilir. Bir sınıf veya yapı tanımlayabilir ve ardından `OrElse` yan tümcesinde bu türden bir değişken kullanırsanız, bu sınıf veya yapıda `IsTrue` tanımlamanız gerekir.  
  
 Derleyici `IsTrue` ve `IsFalse` işleçlerini *eşleşen bir çift*olarak değerlendirir. Diğer bir deyişle, bunlardan birini tanımlarsanız, diğerini de tanımlamanız gerekir.  
  
## <a name="compiler-use-of-istrue"></a>Iıstrue derleyicisi kullanımı  
 Bir sınıf veya yapı tanımladığınızda, bir `For`, `If`, `Else If`veya `While` ifadesinde veya bir `When` yan tümcesinde bu türde bir değişken kullanabilirsiniz. Bunu yaparsanız, derleyici bir koşulu test edebilmesi için türünüzü `Boolean` bir değere dönüştüren bir operatör gerektirir. Uygun bir işleci aşağıdaki sırayla arar:  
  
1. Sınıfınız veya yapıınızdan `Boolean`genişletme işleci.  
  
2. Sınıfınız veya yapıınızdan `Boolean?`genişletme işleci.  
  
3. Sınıfınıza veya yapınızı `IsTrue` işleci.  
  
4. `Boolean` `Boolean?`'e dönüştürme içermeyen `Boolean?` için bir daraltma dönüştürmesi.  
  
5. Sınıfınız veya yapıınızdan `Boolean`daraltma dönüştürmesi işleci.  
  
 `Boolean` veya `IsTrue` işlecine herhangi bir dönüştürme tanımdıysanız, derleyici bir hata bildirir.  
  
> [!NOTE]
> `IsTrue` işleci *aşırı*yüklenebilir, yani işleneni Bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, `IsFalse` ve `IsTrue` işleçleri için tanımlar içeren bir yapının ana hattını tanımlar.  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IsFalse İşleci](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [Nasıl yapılır: İşleç Tanımlama](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [OrElse İşleci](../../../visual-basic/language-reference/operators/orelse-operator.md)
