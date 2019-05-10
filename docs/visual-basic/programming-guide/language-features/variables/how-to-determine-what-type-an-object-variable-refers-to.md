---
title: 'Nasıl yapılır: Bir nesne değişkeninin (Visual Basic) hangi türe başvurduğunu belirleme'
ms.date: 07/20/2015
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
ms.openlocfilehash: 4ae73e6b3dec7864eb670bed67630b1cc96e5e61
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663544"
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a>Nasıl yapılır: Bir nesne değişkeninin (Visual Basic) hangi türe başvurduğunu belirleme
Bir nesne değişkeni başka bir yere depolanmış veriler için bir işaretçi içerir. Çalışma zamanı sırasında bu veri türünü değiştirebilirsiniz. Herhangi bir anda kullanabileceğiniz <xref:System.Type.GetTypeCode%2A> geçerli çalışma zamanı türü belirlemek için yöntemi veya [TypeOf işleci](../../../../visual-basic/language-reference/operators/typeof-operator.md) geçerli olmadığını anlamak için çalışma zamanı türü belirtilen bir tür ile uyumludur.  
  
### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a>Tam bir nesne değişkeni şu anda türünü belirlemek için başvuruyor  
  
1. Nesne değişkeni üzerinde çağrı <xref:System.Object.GetType%2A> almak için yöntemi bir <xref:System.Type?displayProperty=nameWithType> nesne.  
  
    ```  
    Dim myObject As Object  
    myObject.GetType()  
    ```  
  
2. Üzerinde <xref:System.Type?displayProperty=nameWithType> sınıfı, paylaşılan yöntemi çağırın <xref:System.Type.GetTypeCode%2A> alınacak <xref:System.TypeCode> nesnenin türü için değer sabit listesi.  
  
    ```  
    Dim myObject As Object  
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())  
    MsgBox("myObject currently has type code " & CStr(datTyp))  
    ```  
  
     Test edebilirsiniz <xref:System.TypeCode> hangi numaralandırma üyelerini, gibi ilgilendiğiniz karşı numaralandırma değeri `Double`.  
  
### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a>Bir nesne olup olmadığını belirlemek için değişkenin türü ile belirtilen bir türün uyumlu  
  
- Kullanım `TypeOf` işleci ile birlikte [işleci olan](../../../../visual-basic/language-reference/operators/is-operator.md) nesnesi ile test etmek için bir `TypeOf`... `Is` ifade.  
  
    ```  
    If TypeOf objA Is System.Windows.Forms.Control Then  
        MsgBox("objA is compatible with the Control class")  
    End If  
    ```  
  
     `TypeOf`... `Is` ifade döndürür `True` çalışma zamanı nesne türü belirtilen tür ile uyumludur.  
  
     Uyumluluk için ölçüt, belirtilen türün bir sınıf, yapı veya arabirim olduğuna bağlıdır. Genel olarak, nesneyi aynı türde ise, devralan veya belirtilen türün uyguladığı türleri uyumlu değildir. Daha fazla bilgi için [TypeOf işleci](../../../../visual-basic/language-reference/operators/typeof-operator.md).  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Belirtilen türde bir değişkenin veya ifadenin olamayacağını unutmayın. Bu sınıf, yapı veya arabirim gibi tanımlanan bir tür adı olmalıdır. Bu gibi iç türleri içerir `Integer` ve `String`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.GetTypeCode%2A>
- <xref:System.TypeCode>
- [Nesne Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Nesne Değişkeni Değerleri](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Object Veri Türü](../../../../visual-basic/language-reference/data-types/object-data-type.md)
