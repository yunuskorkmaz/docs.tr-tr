---
title: biçimindeki telefon numarasıdır. Operator - C# başvurusu
ms.custom: seodec18
ms.date: 02/25/2019
f1_keywords:
- ._CSharpKeyword
helpviewer_keywords:
- member access operator (.) [C#]
- . operator [C#]
- dot operator (.) [C#]
ms.assetid: a1f54b52-b686-4ae5-a48e-a2a9ebd0eb7b
ms.openlocfilehash: 2661676d53deb874c5e5a90b4443b301730e09df
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56836467"
---
# <a name="-operator-c-reference"></a>biçimindeki telefon numarasıdır. operator (C# Başvurusu)

Nokta `.`, genellikle üye erişimi için kullanılır.

Kullandığınız `.` aşağıdaki örneklerde gösterildiği gibi bir ad alanı veya tür, üye erişim belirteci:

- Kullanım `.` iç içe geçmiş ad alanı içinde bir ad alanı, aşağıdaki örnek olarak erişmek için bir [ `using` yönergesi](../keywords/using-directive.md) gösterir:

  [!code-csharp[nested namespaces](~/samples/snippets/csharp/language-reference/operators/MemberAccessExamples.cs#NestedNamespace)]

- Kullanım `.` forma bir *tam adı* aşağıdaki kodun gösterdiği gibi bir ad alanı içinde bir tür erişmek için:

  [!code-csharp[qualified name](~/samples/snippets/csharp/language-reference/operators/MemberAccessExamples.cs#QualifiedName)]

  Kullanma [ `using` yönergesi](../keywords/using-directive.md) nitelenmiş adlar kullanımı isteğe bağlı yapmak için.

- Kullanım `.` erişimi [üyelerini türü](../../programming-guide/classes-and-structs/index.md#members), statik ve statik olmayan, aşağıdaki kodun gösterdiği olarak:

  [!code-csharp-interactive[type members](~/samples/snippets/csharp/language-reference/operators/MemberAccessExamples.cs#TypeMemberAccess)]

Ayrıca `.` çağrılacak bir [genişletme yöntemi](../../programming-guide/classes-and-structs/extension-methods.md).

## <a name="operator-overloadability"></a>İşleç overloadability

İşleç `.` aşırı yüklenemez.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [üye erişimi](~/_csharplang/spec/expressions.md#member-access) bölümünü [ C# dil belirtimi](../language-specification/index.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# İşleçleri](index.md)
- [?. ve? [] işleçleri](null-conditional-operators.md)