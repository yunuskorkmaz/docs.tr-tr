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
ms.openlocfilehash: 1e94038a41a6a6cc19be6c67bff2891397793fb3
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70924689"
---
# <a name="-and--operators-c-reference"></a>?? ve?? = işleçleri (C# başvuru)

Null birleşim işleci `??` , yoksa sol taraftaki işlenenin `null`değerini döndürür; Aksi takdirde, sağ işleneni değerlendirir ve sonucunu döndürür. Sol işlenen, null olmayan olarak değerlendirilirse işleçsağişleneninideğerlendirmez.`??`

C# 8,0 ve sonraki sürümlerde kullanılabilir, null birleşim atama işleci `??=` , sağ işleneninin değerini yalnızca sol işlenen olarak `null`değerlendirilirse, sol taraftaki işlenene atar. Sol işlenen, null olmayan olarak değerlendirilirse işleçsağişleneninideğerlendirmez.`??=`

[!code-csharp[null-coalescing assignment](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#Assignment)]

`??=` İşlecin sol işleneni bir değişken, [özellik](../../programming-guide/classes-and-structs/properties.md)veya [Dizin Oluşturucu](../../programming-guide/indexers/index.md) öğesi olmalıdır. Null birleşim atama hakkında daha fazla bilgi için bkz. [özellik teklifi Not](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md).

C# 7,3 ve önceki sürümlerde, `??` işlecin sol işlenenin türü bir başvuru türü ya da [null yapılabilir bir değer türü](../../programming-guide/nullable-types/index.md)olmalıdır. 8,0 ile C# başlayarak, bu gereksinim şu değerle değiştirilmiştir: `??` ve `??=` işleçlerinin sol tarafı işleneni, null olamayan bir değer türü olamaz. Özellikle, C# 8,0 ve üzeri sürümlerde kısıtlanmış tür parametreleriyle null birleşim işleçlerini kullanabilirsiniz:

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

`??` Ve`??=` işleçleri aşağıdaki senaryolarda yararlı olabilir:

- İle ifadeler de [null koşullu işleçleri?. ve ?[]](member-access-operators.md#null-conditional-operators--and-), null birleşim işleci ile null koşullu işlemler ifadenin sonucu olması durumunda değerlendirmek için alternatif bir ifade sağlamak için kullanabileceğiniz `null`:

  [!code-csharp-interactive[with null-conditional](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullConditional)]

- Null [yapılabilir değer türleriyle](../../programming-guide/nullable-types/index.md) çalışırken ve temel alınan değer türünde bir değer sağlamanız gerekiyorsa, null olabilen bir tür değeri `null`olması durumunda sağlanacak değeri belirtmek için null birleşim işlecini kullanın:

  [!code-csharp-interactive[with nullable types](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullableTypes)]

  Null yapılabilir bir tür değeri, `null` temel alınan değer türünün varsayılan değeri olması gerektiğinde yöntemikullanın.<xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType>

- 7,0 ile C# başlayarak, bağımsız değişken denetim kodunu daha kısa hale getirmek için null birleşim işlecinin sağ işleneni olarak bir [ `throw` ifade](../keywords/throw.md#the-throw-expression) kullanabilirsiniz:

  [!code-csharp[with throw expression](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithThrowExpression)]

  Yukarıdaki örnek ayrıca bir özelliği tanımlamak için [Expression-Bodied üyelerini](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) nasıl kullanacağınızı gösterir.

- 8,0 ile C# başlayarak, form kodunu değiştirmek için `??=` işlecini kullanabilirsiniz

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

İşleçler `??` ve`??=` aşırı yüklenemez.

## <a name="c-language-specification"></a>C# dili belirtimi

`??` İşleci hakkında daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [null birleşim işleci](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C# işleçleri](index.md)
- [?. ve ?[] işleçleri](member-access-operators.md#null-conditional-operators--and-)
- [?: işleci](conditional-operator.md)
