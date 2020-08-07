---
title: ?? ve?? = işleçleri-C# başvurusu
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
ms.openlocfilehash: 58c60dad3badc62f850f737a3d210ec486809272
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916739"
---
# <a name="-and--operators-c-reference"></a>?? ve?? = işleçleri (C# Başvurusu)

Null birleşim işleci, yoksa `??` sol taraftaki işlenenin değerini döndürür `null` ; Aksi takdirde, sağ işleneni değerlendirir ve sonucunu döndürür. `??`Sol işlenen, null olmayan olarak değerlendirilirse işleç sağ işlenenini değerlendirmez.

C# 8,0 ve üzeri sürümlerde bulunan null birleşim atama işleci, sağ işleneninin `??=` değerini yalnızca sol işlenen olarak değerlendirilirse, sol taraftaki işlenene atar `null` . `??=`Sol işlenen, null olmayan olarak değerlendirilirse işleç sağ işlenenini değerlendirmez.

[!code-csharp[null-coalescing assignment](snippets/shared/NullCoalescingOperator.cs#Assignment)]

İşlecin sol işleneni `??=` bir değişken, [özellik](../../programming-guide/classes-and-structs/properties.md)veya [Dizin Oluşturucu](../../programming-guide/indexers/index.md) öğesi olmalıdır.

C# 7,3 ve önceki sürümlerde, işlecin sol işleneninin türü `??` bir [başvuru türü](../keywords/reference-types.md) veya [null olabilen bir değer türü](../builtin-types/nullable-value-types.md)olmalıdır. C# 8,0 ' den başlayarak, bu gereksinim aşağıdaki değerle değiştirilmiştir: ve işleçlerinin sol tarafı işleneni, `??` `??=` null olamayan bir değer türü olamaz. Özellikle C# 8,0 ' den başlayarak, null birleşim işleçlerini kısıtlanmış olmayan tür parametreleriyle kullanabilirsiniz:

[!code-csharp[unconstrained type parameter](snippets/shared/NullCoalescingOperator.cs#UnconstrainedType)]

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

`??`Ve `??=` işleçleri aşağıdaki senaryolarda yararlı olabilir:

- [Null koşullu işleçlere sahip ifadelerde?. ve? []](member-access-operators.md#null-conditional-operators--and-), `??` null koşullu işlemlere sahip ifadenin sonucu olarak değerlendirmek için alternatif bir ifade sağlamak üzere işlecini kullanabilirsiniz `null` :

  [!code-csharp-interactive[with null-conditional](snippets/shared/NullCoalescingOperator.cs#WithNullConditional)]

- [Null yapılabilir değer türleriyle](../builtin-types/nullable-value-types.md) çalıştığınızda ve temel alınan değer türünde bir değer sağlamanız gerekiyorsa, `??` null yapılabilir bir tür değeri olması durumunda sağlayacak değeri belirtmek için işlecini kullanın `null` :

  [!code-csharp-interactive[with nullable types](snippets/shared/NullCoalescingOperator.cs#WithNullableTypes)]

  <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType>Null yapılabilir bir tür değeri, `null` temel alınan değer türünün varsayılan değeri olması gerektiğinde yöntemi kullanın.

- C# 7,0 ' den başlayarak [ `throw` ](../keywords/throw.md#the-throw-expression) `??` bağımsız değişken denetim kodunu daha kısa hale getirmek için işlecin sağ işleneni olarak bir ifade kullanabilirsiniz:

  [!code-csharp[with throw expression](snippets/shared/NullCoalescingOperator.cs#WithThrowExpression)]

  Yukarıdaki örnek ayrıca bir özelliği tanımlamak için [Expression-Bodied üyelerini](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) nasıl kullanacağınızı gösterir.

- C# 8,0 ' den başlayarak, `??=` form kodunu değiştirmek için işlecini kullanabilirsiniz

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

İşleçler `??` ve `??=` aşırı yüklenemez.

## <a name="c-language-specification"></a>C# dili belirtimi

İşleci hakkında daha fazla bilgi için `??` [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [null birleşim işleci](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) bölümüne bakın.

İşleci hakkında daha fazla bilgi için `??=` bkz. [özellik teklifi Note](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri ve ifadeleri](index.md)
- [?. '? [] işleçleri](member-access-operators.md#null-conditional-operators--and-)
- [?: işleci](conditional-operator.md)
