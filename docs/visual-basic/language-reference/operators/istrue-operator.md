---
title: IsTrue İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
ms.openlocfilehash: 2e67a4adabe58ab12d317ae6318c0a2fac29da7d
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866940"
---
# <a name="istrue-operator-visual-basic"></a>IsTrue İşleci (Visual Basic)

Bir ifadenin olup olmadığını belirler `True` .  
  
 `IsTrue`Kodunuzda açıkça çağrı yapılamaz, ancak Visual Basic Derleyicisi bunu yan tümcelerden kod oluşturmak için kullanabilir `OrElse` . Bir sınıf veya yapı tanımlayabilir ve sonra bir yan tümce içinde bu türden bir değişken kullanırsanız `OrElse` , `IsTrue` Bu sınıf veya yapıda tanımlamanız gerekir.  
  
 Derleyici, `IsTrue` ve `IsFalse` işleçlerini *eşleşen bir çift*olarak değerlendirir. Diğer bir deyişle, bunlardan birini tanımlarsanız, diğerini de tanımlamanız gerekir.  
  
## <a name="compiler-use-of-istrue"></a>Iıstrue derleyicisi kullanımı  

 Bir sınıf veya yapı tanımladığınızda,,, `For` `If` `Else If` , veya `While` deyimi içinde veya `When` yan tümcesinde bu türde bir değişken kullanabilirsiniz. Bunu yaparsanız, derleyici, `Boolean` bir koşulu test edebilmesi için türünüzü bir değere dönüştüren bir operatör gerektirir. Uygun bir işleci aşağıdaki sırayla arar:  
  
1. Sınıfınız veya yapıınızdan ' ye genişleyen bir dönüştürme işleci `Boolean` .  
  
2. Sınıfınız veya yapıınızdan ' ye genişleyen bir dönüştürme işleci `Boolean?` .  
  
3. `IsTrue`Sınıfınıza veya yapınıza yönelik operatör.  
  
4. ' A `Boolean?` bir dönüştürme içermeyen bir daraltma dönüştürmesi `Boolean` `Boolean?` .  
  
5. Sınıfınız veya yapıınızdan ' ye bir daraltma dönüştürme işleci `Boolean` .  
  
 Ya da işlecine herhangi bir dönüştürme tanımdıysanız `Boolean` `IsTrue` , derleyici bir hata bildirir.  
  
> [!NOTE]
> `IsTrue`İşleç *aşırı*yüklenebilir, yani işleneni Bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod örneği, ve işleçleri için tanımlar içeren bir yapının ana hattını tanımlar `IsFalse` `IsTrue` .  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IsFalse İşleci](isfalse-operator.md)
- [Nasıl yapılır: İşleç Tanımlama](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [OrElse İşleci](orelse-operator.md)
