---
title: ?? Ve?? = işleçler - C# referans
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
ms.openlocfilehash: 69294f0fb706868b48b8d7fe8b95fa345af169b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847319"
---
# <a name="-and--operators-c-reference"></a>?? Ve?? = işleçler (C# referansı)

Null-coalescing operatör `??` sol operand değilse değerini `null`döndürür; aksi takdirde, sağ operand değerlendirir ve sonucu döndürür. Operatör `??` sağ operand'ı değerlendirmez ve sol operve null olmayan ı değerlendirirse.

C# 8.0 ve daha sonra mevcuttur, null-coalescing atama operatörü `??=` sağ operand değerini sol operand ve sadece sol operand `null`değerlendirirse atar . Operatör `??=` sağ operand'ı değerlendirmez ve sol operve null olmayan ı değerlendirirse.

[!code-csharp[null-coalescing assignment](snippets/NullCoalescingOperator.cs#Assignment)]

İşleticinin `??=` sol operand bir değişken, bir [özellik](../../programming-guide/classes-and-structs/properties.md)veya bir [dizinleyici](../../programming-guide/indexers/index.md) öğesi olmalıdır.

C# 7.3 ve daha önce, `??` işleç sol operand türü bir referans [türü](../keywords/reference-types.md) veya [nullable değer türü](../builtin-types/nullable-value-types.md)olmalıdır. C# 8.0 ile başlayarak, bu gereksinim aşağıdakilerle değiştirilir: sol el operand'ın türü `??` ve `??=` işleçler nullable değer türü olamaz. Özellikle, C# 8.0 ile başlayarak, sınırlandırılmamış tip parametreleri ile null-coalescing operatörleri kullanabilirsiniz:

[!code-csharp[unconstrained type parameter](snippets/NullCoalescingOperator.cs#UnconstrainedType)]

Null-coalescing operatörleri sağ-associative vardır. Diğer bir şey, formun ifadeleri

```csharp
a ?? b ?? c
d ??= e ??= f
```

olarak değerlendirilir

```csharp
a ?? (b ?? c)
d ??= (e ??= f)
```

## <a name="examples"></a>Örnekler

Ve `??` `??=` işleçleri aşağıdaki senaryolarda yararlı olabilir:

- [Null-koşullu işleçleri ile ifadelerde ?. ve ?[] , null-koşullu](member-access-operators.md#null-conditional-operators--and-)işlemler ile ifade sonucu durumunda değerlendirmek için alternatif bir ifade sağlamak için `??` işleç `null`kullanabilirsiniz:

  [!code-csharp-interactive[with null-conditional](snippets/NullCoalescingOperator.cs#WithNullConditional)]

- [Nullable değer türleri](../builtin-types/nullable-value-types.md) ile çalışıyorsanız ve temel değer türünün bir `??` değer sağlaması gerektiğinde, nullable bir tür `null`değeri durumunda sağlamak için değeri belirtmek için işleci kullanın:

  [!code-csharp-interactive[with nullable types](snippets/NullCoalescingOperator.cs#WithNullableTypes)]

  Nullable <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> türü değeri temel değer türünün varsayılan `null` değeri olduğunda kullanılacak değer varsa yöntemi kullanın.

- C# 7.0 ile başlayarak, bağımsız değişken denetimi kodunu daha `??` kısa yapmak için operatörün sağ operand'ı olarak bir [ `throw` ifade](../keywords/throw.md#the-throw-expression) kullanabilirsiniz:

  [!code-csharp[with throw expression](snippets/NullCoalescingOperator.cs#WithThrowExpression)]

  Önceki örnek, bir özelliği tanımlamak için [ifade gövdeli üyelerin](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) nasıl kullanılacağını da gösterir.

- C# 8.0 ile başlayarak, `??=` formun kodunu değiştirmek için işleci kullanabilirsiniz

  ```csharp
  if (variable is null)
  {
      variable = expression;
  }
  ```

  aşağıdaki kod ile:

  ```csharp
  variable ??= expression;
  ```

## <a name="operator-overloadability"></a>Operatör aşırı yüklenebilirlik

Operatörler `??` `??=` ve aşırı yüklenemez.

## <a name="c-language-specification"></a>C# dili belirtimi

Operatör hakkında daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [null birleştirme işleci](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) bölümüne bakın. `??`

Operatör hakkında daha fazla bilgi için [özellik teklifi notuna](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md)bakın. `??=`

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri](index.md)
- [?. Ve? [] işleçleri](member-access-operators.md#null-conditional-operators--and-)
- [?: operatör](conditional-operator.md)
