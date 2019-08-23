---
title: IsFalse İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: 49b8493575685a220808df1522ce16835b3ce0ed
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917150"
---
# <a name="isfalse-operator-visual-basic"></a>IsFalse İşleci (Visual Basic)
Bir ifadenin `False`olup olmadığını belirler.  
  
 Kodunuzda açıkça çağrı `IsFalse` yapılamaz, ancak Visual Basic Derleyicisi bunu yan tümcelerden `AndAlso` kod oluşturmak için kullanabilir. Bir sınıf veya yapı tanımlayabilir ve sonra bir `AndAlso` yan tümce içinde bu türden bir değişken kullanırsanız, bu sınıf veya yapıda tanımlamanız `IsFalse` gerekir.  
  
 Derleyici, `IsFalse` ve `IsTrue` işleçlerini eşleşen bir *çift*olarak değerlendirir. Diğer bir deyişle, bunlardan birini tanımlarsanız, diğerini de tanımlamanız gerekir.  
  
> [!NOTE]
> İşleç aşırı yüklenebilir, yani işleneni Bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. `IsFalse` Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, `IsFalse` ve `IsTrue` işleçleri için tanımlar içeren bir yapının ana hattını tanımlar.  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IsTrue İşleci](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [Nasıl yapılır: Bir Işleç tanımlayın](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [AndAlso İşleci](../../../visual-basic/language-reference/operators/andalso-operator.md)
