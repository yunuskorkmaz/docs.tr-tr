---
title: ?? Operator - C# başvurusu
ms.custom: seodec18
ms.date: 06/07/2019
f1_keywords:
- ??_CSharpKeyword
helpviewer_keywords:
- null-coalescing operator [C#]
- ?? operator [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: 8ca97261b348b7813ab179abbc1f2c5f535966a1
ms.sourcegitcommit: 5ae6affa0b171be3bb5f4729fb68ea4fe799f959
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2019
ms.locfileid: "66816013"
---
# <a name="-operator-c-reference"></a>?? operator (C# Başvurusu)

Null birleşim işleci `??` değilse sol işlenenin değerini döndürür `null`; Aksi takdirde, sağ işlenen değerlendirilir ve sonucu döndürür. `??` İşleci sol işlenen null olmayan olarak değerlendirilirse, sağ işleneni değerlendirmek değil.

Null birleşim işleci sağla ilişkilendirilebilir, diğer bir deyişle, bir ifade formu

```csharp
a ?? b ?? c
```

olarak değerlendirilir

```csharp
a ?? (b ?? c)
```

`??` İşleci aşağıdaki senaryolarda yararlı olabilir:

- İle ifadeler de [null koşullu işleçleri?. ve?] ](member-access-operators.md#null-conditional-operators--and-), null birleşim işleci ile null koşullu işlemler ifadenin sonucu olması durumunda değerlendirmek için alternatif bir ifade sağlamak için kullanabileceğiniz `null`:

  [!code-csharp-interactive[with null-conditional](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullConditional)]

- İle çalıştığınızda [boş değer atanabilen değer türleri](../../programming-guide/nullable-types/index.md) ve temel alınan bir değer türünün bir değer belirtmeniz gerekiyorsa null birleşim işleci bir boş değer atanabilir bir tür değeri olması durumunda sağlamak için değeri belirtmek için kullanın `null`:

  [!code-csharp-interactive[with nullable types](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullableTypes)]

  Kullanım <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> yöntemi, bir boş değer atanabilir tür değeri olduğunda kullanılacak değer `null` temel değer türünün varsayılan değeri olmalıdır.

- İle başlayarak C# kullanabileceğiniz 7.0 bir [ `throw` ifade](../keywords/throw.md#the-throw-expression) sağ işleneni, bağımsız değişken denetimi kod daha kısa yapmak için null birleşim işleci olarak:

  [!code-csharp[with throw expression](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithThrowExpression)]

  Yukarıdaki örnekte ayrıca nasıl kullanılacağını gösterir [ifade gövdeli üyeler](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) bir özelliği tanımlamak için.

## <a name="operator-overloadability"></a>İşleç overloadability

Null birleşim işleci aşırı yüklenemez.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [null birleşim işleci](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# işleçleri](index.md)
- [?. ve? [] işleçleri](member-access-operators.md#null-conditional-operators--and-)
- [?: işleci](conditional-operator.md)
