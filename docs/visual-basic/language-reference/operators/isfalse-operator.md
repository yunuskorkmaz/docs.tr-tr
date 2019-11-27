---
title: IsFalse İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: 51b7bfb2cf5301a39818e6566b408ee0677689f2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349523"
---
# <a name="isfalse-operator-visual-basic"></a>IsFalse İşleci (Visual Basic)
Bir ifadenin `False`olup olmadığını belirler.  
  
 Kodunuzda açıkça `IsFalse` çağrılamaz, ancak Visual Basic Derleyicisi bunu `AndAlso` yan tümcelerinden kod oluşturmak için kullanabilir. Bir sınıf veya yapı tanımlayabilir ve ardından `AndAlso` yan tümcesinde bu türden bir değişken kullanırsanız, bu sınıf veya yapıda `IsFalse` tanımlamanız gerekir.  
  
 Derleyici `IsFalse` ve `IsTrue` işleçlerini *eşleşen bir çift*olarak değerlendirir. Diğer bir deyişle, bunlardan birini tanımlarsanız, diğerini de tanımlamanız gerekir.  
  
> [!NOTE]
> `IsFalse` işleci *aşırı*yüklenebilir, yani işleneni Bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, `IsFalse` ve `IsTrue` işleçleri için tanımlar içeren bir yapının ana hattını tanımlar.  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IsTrue İşleci](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [Nasıl yapılır: İşleç Tanımlama](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [AndAlso İşleci](../../../visual-basic/language-reference/operators/andalso-operator.md)
