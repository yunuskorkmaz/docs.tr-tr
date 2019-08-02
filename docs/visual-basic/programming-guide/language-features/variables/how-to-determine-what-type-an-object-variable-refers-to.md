---
title: 'Nasıl yapılır: Bir nesne değişkeninin hangi türe başvurduğunu belirleme (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
ms.openlocfilehash: 935623dd4b6edca188f932aca0e560130199e8f6
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626575"
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a>Nasıl yapılır: Bir nesne değişkeninin hangi türe başvurduğunu belirleme (Visual Basic)

Bir nesne değişkeni, başka bir yerde depolanan veriler için bir işaretçi içerir. Çalışma zamanı sırasında verilerin türü değişebilir. Herhangi bir anda, geçerli çalışma zamanı türünü <xref:System.Type.GetTypeCode%2A> veya geçerli çalışma zamanı türünün belirtilen türle uyumlu olup olmadığını bulmak için [typeof işlecini](../../../../visual-basic/language-reference/operators/typeof-operator.md) kullanabilirsiniz.

### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a>Şu anda başvurduğu bir nesne değişkeninin tam türünü belirleme

1. Nesne değişkeninde, bir <xref:System.Object.GetType%2A> <xref:System.Type?displayProperty=nameWithType> nesneyi almak için yöntemini çağırın.

    ```vb
    Dim myObject As Object
    myObject.GetType()
    ```

2. Sınıfında, nesne türü için <xref:System.TypeCode> numaralandırma değerini almak <xref:System.Type.GetTypeCode%2A> üzere paylaşılan yöntemi çağırın. <xref:System.Type?displayProperty=nameWithType>

    ```vb
    Dim myObject As Object
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())
    MsgBox("myObject currently has type code " & CStr(datTyp))
    ```

    <xref:System.TypeCode> Sabit listesi üyelerinin ilgi çekici olduğunu, örneğin olduğu `Double`gibi test edebilirsiniz.

### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a>Bir nesne değişkeninin türünün belirtilen tür ile uyumlu olup olmadığını belirleme

- Nesneyi bir`TypeOf`... ile test [](../../../../visual-basic/language-reference/operators/is-operator.md) etmek için işleçişleciilebirlikte`TypeOf` işleci kullanın `Is` ifadesi.

    ```vb
    If TypeOf objA Is System.Windows.Forms.Control Then
        MsgBox("objA is compatible with the Control class")
    End If
    ```

    `TypeOf`... ifade, nesnenin çalışma zamanı türü belirtilen türle uyumluysa döndürülür `True`. `Is`

    Uyumluluk ölçütü, belirtilen türün bir sınıf, yapı veya arabirim olmasına bağlıdır. Genel olarak, nesne aynı türde ise, öğesinden devralır veya belirtilen türü uygularsa türler uyumlu olur. Daha fazla bilgi için bkz. [typeof işleci](../../../../visual-basic/language-reference/operators/typeof-operator.md).

## <a name="compiling-the-code"></a>Kod Derleniyor

Belirtilen türün bir değişken veya ifade olamayacağını unutmayın. Sınıf, yapı veya arabirim gibi tanımlı bir türün adı olmalıdır. Bu `Integer` , ve `String`gibi iç türleri içerir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.GetTypeCode%2A>
- <xref:System.TypeCode>
- [Nesne Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Nesne Değişkeni Değerleri](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Object Veri Türü](../../../../visual-basic/language-reference/data-types/object-data-type.md)
