---
title: İşleç Yordamları
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
ms.assetid: 8c513d38-246b-4fb7-8b75-29e1364e555b
ms.openlocfilehash: a1dd183570c8aa50efff85bdaebef90bd3b0120f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364324"
---
# <a name="operator-procedures-visual-basic"></a>İşleç Yordamları (Visual Basic)

İşleç yordamı, `*` `<>` `And` tanımladığınız bir sınıf veya yapıda standart işlecin (örneğin,, veya) davranışını tanımlayan Visual Basic deyimlerinin bir dizisidir. Buna *işleç aşırı yüklemesi*de denir.

## <a name="when-to-define-operator-procedures"></a>Operatör yordamları ne zaman tanımlanır

Bir sınıf veya yapı tanımladığınızda, değişkenleri bu sınıf veya yapının türünde olacak şekilde bildirebilirsiniz. Bazen bu tür bir değişkenin bir ifadenin parçası olarak bir işleme katılması gerekir. Bunu yapmak için, bir işlecinin işleneni olmalıdır.

Visual Basic işleçleri yalnızca temel veri türlerinde tanımlar. Bir işlecin bir veya her ikisi de sınıfınızın veya yapınızın türünden olduğunda bir işlecin davranışını tanımlayabilirsiniz.

Daha fazla bilgi için bkz. [operator deyimleri](../../../language-reference/statements/operator-statement.md).

## <a name="types-of-operator-procedure"></a>Işleç yordamının türleri

Bir işleç yordamı aşağıdaki türlerden biri olabilir:

- Bağımsız değişkenin sınıfınızın veya yapınızın türünde olduğu birli işlecin tanımı.

- Bağımsız değişkenlerden en az birinin sınıfınızın veya yapınızın türü olduğu bir ikili işlecinin tanımı.

- Bağımsız değişkenin sınıfınızın veya yapınızın türünde olduğu bir dönüştürme işlecinin tanımı.

- Sınıfınızın veya yapınızın türünü döndüren bir dönüştürme işlecinin tanımı.

 Dönüştürme işleçleri her zaman birli ve `CType` tanımladığınız operatör olarak her zaman kullanılır.

## <a name="declaration-syntax"></a>Bildirim Sözdizimi

Bir işleç yordamını bildirmek için sözdizimi aşağıdaki gibidir:

```vb
Public Shared [Widening | Narrowing] Operator operatorsymbol ( operand1 [,  operand2 ]) As datatype

' Statements of the operator procedure.

End Operator
```

`Widening`Or `Narrowing` anahtar sözcüğünü yalnızca bir tür dönüştürme işleci üzerinde kullanırsınız. İşleç sembolü, bir tür dönüştürme işleci için her zaman [CType işlevidir](../../../language-reference/functions/ctype-function.md) .

İkili bir işleç tanımlamak için iki işlenen bildirir ve bir tür dönüştürme işleci dahil birli işleç tanımlamak için bir işlenen bildirirsiniz. Tüm işlenenler bildirilmelidir `ByVal` .

Her işleneni, [Sub yordamları](./sub-procedures.md)için parametreleri bildirdiğiniz şekilde bildirirsiniz.

### <a name="data-type"></a>Veri Türü

Tanımladığınız bir sınıf veya yapı üzerinde bir işleç tanımladığınız için işlenenlerinden en az birinin bu sınıf veya yapının veri türünde olması gerekir. Bir tür dönüştürme işleci için, işlenen ya da dönüş türü, sınıfın veya yapının veri türünde olmalıdır.

Daha ayrıntılı bilgi için bkz. [Işleç açıklaması](../../../language-reference/statements/operator-statement.md).

## <a name="calling-syntax"></a>Çağırma sözdizimi

Bir ifadede işleç sembolünü kullanarak örtük olarak bir operatör yordamı çağırılır. İşlenenleri önceden tanımlanmış işleçler için yaptığınız şekilde sağlarsınız.

İşleç yordamına örtük çağrının sözdizimi aşağıdaki gibidir:

`Dim testStruct As`  *structurename*

`Dim testNewStruct As`  *structurename* `= testStruct` *operatorsymbol*      `10`

### <a name="illustration-of-declaration-and-call"></a>Bildirim ve çağrı gösterimi

Aşağıdaki yapı, imzalı bir 128 bitlik tamsayı değerini, anayen yüksek sıralı ve düşük sıralı parçalar olarak depolar. `+`İki `veryLong` değer eklemek ve elde edilen bir değer oluşturmak için işlecini tanımlar `veryLong` .

[!code-vb[VbVbcnProcedures#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#23)]

Aşağıdaki örnek, üzerinde tanımlanan işlecine tipik bir çağrı gösterir `+` `veryLong` .

[!code-vb[VbVbcnProcedures#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#24)]

## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Alt Yordamlar](./sub-procedures.md)
- [İşlev Yordamları](./function-procedures.md)
- [Özellik Yordamları](./property-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Operator Deyimi](../../../language-reference/statements/operator-statement.md)
- [Nasıl yapılır: İşleç Tanımlama](./how-to-define-an-operator.md)
- [Nasıl yapılır: Dönüştürme İşleci Tanımlama](./how-to-define-a-conversion-operator.md)
- [Nasıl yapılır: Bir İşleç Yordamı Çağırma](./how-to-call-an-operator-procedure.md)
- [Nasıl yapılır: İşleçleri Tanımlayan Bir Sınıf Kullanma](./how-to-use-a-class-that-defines-operators.md)
