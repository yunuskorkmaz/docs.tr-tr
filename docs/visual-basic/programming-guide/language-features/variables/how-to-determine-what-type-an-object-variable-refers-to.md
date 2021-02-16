---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: bir nesne değişkeninin hangi türe başvurduğunu belirleme (Visual Basic)'
title: 'Nasıl yapılır: Bir Nesne Değişkeninin Hangi Türe Başvurduğunu Belirleme'
ms.date: 07/20/2015
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
ms.openlocfilehash: 699a8c5c075fc923a61a66f617c255f193cd8797
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481928"
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a>Nasıl yapılır: Bir Nesne Değişkeninin Hangi Türe Başvurduğunu Belirleme (Visual Basic)

Bir nesne değişkeni, başka bir yerde depolanan veriler için bir işaretçi içerir. Çalışma zamanı sırasında verilerin türü değişebilir. Herhangi bir anda, geçerli <xref:System.Type.GetTypeCode%2A> çalışma zamanı türünü veya geçerli çalışma zamanı türünün belirtilen türle uyumlu olup olmadığını bulmak Için [typeof işlecini](../../../language-reference/operators/typeof-operator.md) kullanabilirsiniz.

### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a>Şu anda başvurduğu bir nesne değişkeninin tam türünü belirleme

1. Nesne değişkeninde, <xref:System.Object.GetType%2A> bir nesneyi almak için yöntemini çağırın <xref:System.Type?displayProperty=nameWithType> .

    ```vb
    Dim myObject As Object
    myObject.GetType()
    ```

2. <xref:System.Type?displayProperty=nameWithType>Sınıfında, <xref:System.Type.GetTypeCode%2A> <xref:System.TypeCode> nesne türü için numaralandırma değerini almak üzere paylaşılan yöntemi çağırın.

    ```vb
    Dim myObject As Object
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())
    MsgBox("myObject currently has type code " & CStr(datTyp))
    ```

    <xref:System.TypeCode>Sabit listesi üyelerinin ilgi çekici olduğunu, örneğin olduğu gibi test edebilirsiniz `Double` .

### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a>Bir nesne değişkeninin türünün belirtilen tür ile uyumlu olup olmadığını belirleme

- `TypeOf`Nesneyi bir [](../../../language-reference/operators/is-operator.md) `TypeOf` ... ifadesi Ile test etmek için, işleç işleç ile birlikte kullanın `Is` .

    ```vb
    If TypeOf objA Is System.Windows.Forms.Control Then
        MsgBox("objA is compatible with the Control class")
    End If
    ```

    `TypeOf`... `Is` İfadesi, `True` nesnenin çalışma zamanı türünün belirtilen türle uyumlu olup olmadığını döndürür.

    Uyumluluk ölçütü, belirtilen türün bir sınıf, yapı veya arabirim olmasına bağlıdır. Genel olarak, nesne aynı türde ise, öğesinden devralır veya belirtilen türü uygularsa türler uyumlu olur. Daha fazla bilgi için bkz. [typeof işleci](../../../language-reference/operators/typeof-operator.md).

## <a name="compile-the-code"></a>Kodu derle

Belirtilen türün bir değişken veya ifade olamayacağını unutmayın. Sınıf, yapı veya arabirim gibi tanımlı bir türün adı olmalıdır. Bu, ve gibi iç türleri `Integer` içerir `String` .

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.GetTypeCode%2A>
- <xref:System.TypeCode>
- [Nesne Değişkenleri](object-variables.md)
- [Nesne Değişkeni Değerleri](object-variable-values.md)
- [Nesne Veri Türü](../../../language-reference/data-types/object-data-type.md)
