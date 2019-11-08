---
title: ?? ve?? = işleçler- C# başvuru
ms.custom: seodec18
ms.date: 09/10/2019
f1_keywords:
- ??_CSharpKeyword
- ??=_CSharpKeyword
helpviewer_keywords:
- null-coalescing operator [C#]
- ?? operator [C#]
- null-coalescing assignment [C#]
- ??= operator [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: 2bd6fe3d2d283e64eebc2251416fa5234e30bdad
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739663"
---
# <a name="-and--operators-c-reference"></a>?? ve?? = işleçleri (C# başvuru)

Null birleşim işleci `??` `null`değilse, sol taraftaki işlenenin değerini döndürür; Aksi takdirde, sağ işleneni değerlendirir ve sonucunu döndürür. Sol işlenen, null olmayan olarak değerlendirilirse `??` işleci sağ işleneni değerlendirmez.

C# 8,0 ve sonraki sürümlerde bulunan null birleşim atama işleci`??=`sağ işleneninin değerini sol taraftaki işlenene yalnızca sol işlenen`null`değerlendirirken atar. Sol işlenen, null olmayan olarak değerlendirilirse `??=` işleci sağ işleneni değerlendirmez.

[!code-csharp[null-coalescing assignment](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#Assignment)]

`??=` işlecinin sol tarafındaki işleneni bir değişken, [özellik](../../programming-guide/classes-and-structs/properties.md)veya [Dizin Oluşturucu](../../programming-guide/indexers/index.md) öğesi olmalıdır.

C# 7,3 ve önceki sürümlerde `??` işlecinin sol işlenenin türü bir [başvuru türü](../keywords/reference-types.md) ya da [null yapılabilir bir değer türü](../builtin-types/nullable-value-types.md)olmalıdır. 8,0 ile C# başlayarak, bu gereksinim aşağıdaki değerle değiştirilmiştir:`??`ve`??=`işleçlerinin sol taraftaki işleneninin türü null yapılamayan bir değer türü olamaz. Özellikle, 8,0 ile C# başlayarak, null birleşim işleçlerini kısıtlanmış olmayan tür parametreleriyle kullanabilirsiniz:

[!code-csharp[unconstrained type parameter](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#UnconstrainedType)]

Null birleştirme işleçleri doğru ilişkilendirilebilir. Diğer bir deyişle, formun ifadeleri

```csharp
a ?? b ?? c
d ??= e ??= f
```

şöyle değerlendirilir

```csharp
a ?? (b ?? c)
d ??= (e ??= f)
```

## <a name="examples"></a>Örnekler

`??` ve `??=` işleçleri aşağıdaki senaryolarda yararlı olabilir:

- [Null koşullu işleçlere sahip ifadelerde?. ve? []](member-access-operators.md#null-conditional-operators--and-), null koşullu işlemlere sahip ifadenin sonucu `null`olduğunda değerlendirmek için alternatif bir ifade sağlamak üzere `??` işlecini kullanabilirsiniz:

  [!code-csharp-interactive[with null-conditional](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullConditional)]

- [Null yapılabilir değer türleriyle](../builtin-types/nullable-value-types.md) çalıştığınızda ve temel alınan değer türünde bir değer sağlamanız gerekiyorsa, null yapılabilir bir tür değeri `null`olduğunda sağlamak üzere değer belirtmek için `??` işlecini kullanın:

  [!code-csharp-interactive[with nullable types](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullableTypes)]

  Null yapılabilir bir tür değeri `null`, temel alınan değer türünün varsayılan değeri olması durumunda kullanılacak değer <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> yöntemi kullanın.

- 7,0 ' C# den başlayarak bağımsız değişken denetim kodunu daha kısa hale getirmek için`??`işlecinin sağ işleneni olarak bir [`throw` ifadesini](../keywords/throw.md#the-throw-expression) kullanabilirsiniz:

  [!code-csharp[with throw expression](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithThrowExpression)]

  Yukarıdaki örnek ayrıca bir özelliği tanımlamak için [Expression-Bodied üyelerini](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) nasıl kullanacağınızı gösterir.

- 8,0 ile C# başlayarak, form kodunu değiştirmek için`??=`işlecini kullanabilirsiniz

  ```csharp
  if (variable is null)
  {
      variable = expression;
  }
  ```

  aşağıdaki kodla:

  ```csharp
  variable ??= expression;
  ```

## <a name="operator-overloadability"></a>Operatör overloadability

`??` ve `??=` işleçleri aşırı yüklenemez.

## <a name="c-language-specification"></a>C# dili belirtimi

`??` işleci hakkında daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [null birleşim işleci](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) bölümüne bakın.

`??=` işleci hakkında daha fazla bilgi için bkz. [özellik teklifi notunun](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C# işleçleri](index.md)
- [?. '? [] işleçleri](member-access-operators.md#null-conditional-operators--and-)
- [?: işleci](conditional-operator.md)
