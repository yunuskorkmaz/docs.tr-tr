---
title: 'Nasıl yapılır: Bir Nesne Değişkeninin Hangi Türe Başvurduğunu Belirleme'
ms.date: 07/20/2015
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
ms.openlocfilehash: 9f9b89e2fea0bd69cba6d50fa1d1fb9cc3927685
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348614"
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a>Nasıl yapılır: Bir Nesne Değişkeninin Hangi Türe Başvurduğunu Belirleme (Visual Basic)

Bir nesne değişkeni, başka bir yerde depolanan veriler için bir işaretçi içerir. Çalışma zamanı sırasında verilerin türü değişebilir. Herhangi bir anda, geçerli çalışma zamanı türünü veya geçerli çalışma zamanı türünün belirtilen türle uyumlu olup olmadığını [bulmak için <xref:System.Type.GetTypeCode%2A>](../../../../visual-basic/language-reference/operators/typeof-operator.md) yöntemini kullanabilirsiniz.

### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a>Şu anda başvurduğu bir nesne değişkeninin tam türünü belirleme

1. Nesne değişkeninde, bir <xref:System.Type?displayProperty=nameWithType> nesnesini almak için <xref:System.Object.GetType%2A> yöntemini çağırın.

    ```vb
    Dim myObject As Object
    myObject.GetType()
    ```

2. <xref:System.Type?displayProperty=nameWithType> sınıfında, nesne türü için <xref:System.TypeCode> numaralandırma değerini almak üzere <xref:System.Type.GetTypeCode%2A> paylaşılan yöntemi çağırın.

    ```vb
    Dim myObject As Object
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())
    MsgBox("myObject currently has type code " & CStr(datTyp))
    ```

    <xref:System.TypeCode> numaralandırma değerini, `Double`gibi, hangi numaralandırma üyelerinin ilgi alanına göre test edebilirsiniz.

### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a>Bir nesne değişkeninin türünün belirtilen tür ile uyumlu olup olmadığını belirleme

- Nesneyi bir `TypeOf`...`Is` ifadesi ile test etmek için with [işleci](../../../../visual-basic/language-reference/operators/is-operator.md) ile birlikte `TypeOf` işlecini kullanın.

    ```vb
    If TypeOf objA Is System.Windows.Forms.Control Then
        MsgBox("objA is compatible with the Control class")
    End If
    ```

    `TypeOf`...`Is` ifadesi, nesnenin çalışma zamanı türü belirtilen türle uyumluysa `True` döndürür.

    Uyumluluk ölçütü, belirtilen türün bir sınıf, yapı veya arabirim olmasına bağlıdır. Genel olarak, nesne aynı türde ise, öğesinden devralır veya belirtilen türü uygularsa türler uyumlu olur. Daha fazla bilgi için bkz. [typeof işleci](../../../../visual-basic/language-reference/operators/typeof-operator.md).

## <a name="compiling-the-code"></a>Kod Derleme

Belirtilen türün bir değişken veya ifade olamayacağını unutmayın. Sınıf, yapı veya arabirim gibi tanımlı bir türün adı olmalıdır. Bu, `Integer` ve `String`gibi iç türleri içerir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.GetTypeCode%2A>
- <xref:System.TypeCode>
- [Nesne Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Nesne Değişkeni Değerleri](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Object Veri Türü](../../../../visual-basic/language-reference/data-types/object-data-type.md)
