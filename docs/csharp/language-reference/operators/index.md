---
title: C# işleçleri - C# referansı
ms.date: 04/22/2020
f1_keywords:
- cs.operators
helpviewer_keywords:
- operators [C#]
- operator precedence [C#]
- operator associativity [C#]
- expressions [C#]
ms.assetid: 0301e31f-22ad-49af-ac3c-d5eae7f0ac43
ms.openlocfilehash: fe4adf7df707eff0990e8c731a36d6177df228cf
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102027"
---
# <a name="c-operators-c-reference"></a>C# işleçleri (C# referansı)

C# yerleşik türleri tarafından desteklenen bir dizi işleç sağlar. Örneğin, [aritmetik işleçler](arithmetic-operators.md) sayısal operands ile aritmetik işlemler gerçekleştirmek ve [Boolean mantıksal işleçleri](boolean-logical-operators.md) [bool](../builtin-types/bool.md) operands ile mantıksal işlemler gerçekleştirin. Bazı operatörler [aşırı yüklenebilir.](operator-overloading.md) Operatör aşırı yüklemesi ile, kullanıcı tanımlı bir türün operands için işleç davranışı belirtebilirsiniz.

Bir [ifadede,](../../programming-guide/statements-expressions-operators/expressions.md)işleç önceliği ve bağlantı, işlemlerin gerçekleştirilme sırasını belirler. İşletici öncelik ve bağlılık tarafından dayatılan değerlendirme sırasını değiştirmek için parantezler kullanabilirsiniz.

## <a name="operator-precedence"></a>İşleç önceliği

Birden çok işleç içeren bir ifadede, daha yüksek önceliğe sahip işleçler daha düşük önceliğe sahip işleçlerden önce değerlendirilir. Aşağıdaki örnekte, toplama dan daha yüksek önceliğe sahip olduğu için önce çarpma gerçekleştirilir:

```csharp-interactive
var a = 2 + 2 * 2;
Console.WriteLine(a); //  output: 6
```

Operatör önceliği tarafından dayatılan değerlendirme sırasını değiştirmek için parantez kullanın:

```csharp-interactive
var a = (2 + 2) * 2;
Console.WriteLine(a); //  output: 8
```

Aşağıdaki tabloda, en düşükten en yüksek önceliğe sahip c# işleçleri listelenir. Her satırdaki işleçler aynı önceliğe sahiptir.

| İşleçler | Kategori veya ad |
| --------- | ---------------- |
| [x.y](member-access-operators.md#member-access-expression-), [f(x)](member-access-operators.md#invocation-expression-), [a&#91;i&#93;](member-access-operators.md#indexer-operator-), [x++](arithmetic-operators.md#increment-operator-), [x--](arithmetic-operators.md#decrement-operator---) [x!](null-forgiving.md), [yeni](new-operator.md), [typeof](type-testing-and-cast.md#typeof-operator), [kontrol ,](../keywords/checked.md) [işaretsiz](../keywords/unchecked.md), [varsayılan](default.md), [adof](nameof.md), [temsilci](delegate-operator.md), [sizeof](sizeof.md), [stackalloc](stackalloc.md), [x->y](pointer-related-operators.md#pointer-member-access-operator--) | Birincil |
| [+x](arithmetic-operators.md#unary-plus-and-minus-operators), [-x](arithmetic-operators.md#unary-plus-and-minus-operators), [ \!x](boolean-logical-operators.md#logical-negation-operator-), [~x](bitwise-and-shift-operators.md#bitwise-complement-operator-), [++x](arithmetic-operators.md#increment-operator-), [--x](arithmetic-operators.md#decrement-operator---), [^x](member-access-operators.md#index-from-end-operator-), [x?. y](member-access-operators.md#null-conditional-operators--and-), [x?[ y]](member-access-operators.md#null-conditional-operators--and-), [(T)x](type-testing-and-cast.md#cast-expression), [bekliyor](await.md), [&x](pointer-related-operators.md#address-of-operator-), [*x](pointer-related-operators.md#pointer-indirection-operator-), [doğru ve yanlış](true-false-operators.md) | Tekli |
| [X.. Y](member-access-operators.md#range-operator-) | Aralık |
| [switch](../../whats-new/csharp-8.md#switch-expressions) | `switch`Ifa -de |
| [x * y](arithmetic-operators.md#multiplication-operator-), [x / y](arithmetic-operators.md#division-operator-), x % [y](arithmetic-operators.md#remainder-operator-) | Çarpma|
| [x + y](arithmetic-operators.md#addition-operator-), [x – y](arithmetic-operators.md#subtraction-operator--) | Katkı |
| [ \< x \< y](bitwise-and-shift-operators.md#left-shift-operator-), [x >> y](bitwise-and-shift-operators.md#right-shift-operator-) | Shift |
| [x \< y](comparison-operators.md#less-than-operator-), [x > y](comparison-operators.md#greater-than-operator-), x [ \<= y](comparison-operators.md#less-than-or-equal-operator-), x >= [y](comparison-operators.md#greater-than-or-equal-operator-), [olarak](type-testing-and-cast.md#is-operator) [as](type-testing-and-cast.md#as-operator) | İlişkisel ve tip-test |
| [x == y](equality-operators.md#equality-operator-), [x != y](equality-operators.md#inequality-operator-) | Eşitlik |
| `x & y` | [Boolean mantıksal VE](boolean-logical-operators.md#logical-and-operator-) veya [bitwise mantıksal VE](bitwise-and-shift-operators.md#logical-and-operator-) |
| `x ^ y` | [Boolean mantıksal XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) veya [bitwise mantıksal XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) |
| <code>x &#124; y</code> | [Boolean mantıksal VEYA](boolean-logical-operators.md#logical-or-operator-) [bitwise mantıksal VEYA](bitwise-and-shift-operators.md#logical-or-operator-) |
| [x && y](boolean-logical-operators.md#conditional-logical-and-operator-) | Koşullu VE |
| [x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) | Koşullu VEYA |
| [X?? Y](null-coalescing-operator.md) | Null-coalescing operatörü |
| [C? t : f](conditional-operator.md) | Koşullu işleç |
| [x = y ,](assignment-operator.md) [x += y](arithmetic-operators.md#compound-assignment), x [-= y](arithmetic-operators.md#compound-assignment), x [*= y](arithmetic-operators.md#compound-assignment), x [/= y](arithmetic-operators.md#compound-assignment), x [%= y](arithmetic-operators.md#compound-assignment), x &= [y](boolean-logical-operators.md#compound-assignment), x &#124;[= y](boolean-logical-operators.md#compound-assignment), [x](boolean-logical-operators.md#compound-assignment) >>= y , x <<= [y](bitwise-and-shift-operators.md#compound-assignment), x >>[= y](bitwise-and-shift-operators.md#compound-assignment), [x ?? = y ,](null-coalescing-operator.md)[=>](lambda-operator.md) | Atama ve lambda beyanı |

## <a name="operator-associativity"></a>Operatör bağlantısı

İşleçler aynı önceliğe sahipolduğunda, işleçlerin birleştirilmesi, işlemlerin gerçekleştirilme sırasını belirler:

- *Sol-assosiyatif* operatörler soldan sağa sırayla değerlendirilir. [Atama işleçleri](assignment-operator.md) ve [null-coalescing işleçleri](null-coalescing-operator.md)dışında, tüm ikili işleçler sol-associative vardır. Örneğin, `a + b - c` olarak `(a + b) - c`değerlendirilir.
- *Sağ-assosiyatif* operatörler sağdan sola doğru sırayla değerlendirilir. Atama işleçleri, null-coalescing işleçleri ve [koşullu işleç `?:` ](conditional-operator.md) sağ-associative vardır. Örneğin, `x = y = z` olarak `x = (y = z)`değerlendirilir.

Operatör ler tarafından uygulanan değerlendirme sırasını değiştirmek için parantezkullanın:

```csharp-interactive
int a = 13 / 5 / 2;
int b = 13 / (5 / 2);
Console.WriteLine($"a = {a}, b = {b}");  // output: a = 1, b = 6
```

## <a name="operand-evaluation"></a>Operand değerlendirme

Operatör önceliği ve ilişkisi ile ilgisi olmayan bir ifadedeki operandlar soldan sağa değerlendirilir. Aşağıdaki örnekler, işleçlerin ve operandların değerlendirilme sırasını göstermektedir:

| İfadeler | Değerlendirme sırası |
| ---------- | ------------------- |
|`a + b`|a, b, +|
|`a + b * c`|a, b, c, *, +|
|`a / b + c * d`|a, b, /, c, d, *, +|
|`a / (b + c) * d`|a, b, c, +, /, d, *|

Tipik olarak, tüm operatör operands değerlendirilir. Ancak, bazı operatörler operands koşullu olarak değerlendirir. Diğer bir deyişle, böyle bir işleç sol operand değeri (veya) diğer operands değerlendirilmesi gerektiğini tanımlar. Bu işleçler koşullu mantıksal [AND`&&`( )](boolean-logical-operators.md#conditional-logical-and-operator-) ve OR ( [`||`)](boolean-logical-operators.md#conditional-logical-or-operator-) işleçleri, [null-coalescing operatörleri `??` ve `??=` ](null-coalescing-operator.md), [null-koşullu operatörler `?.` ve `?[]` ](member-access-operators.md#null-conditional-operators--and-), ve [koşullu işleç `?:` ](conditional-operator.md). Daha fazla bilgi için her işleç tanımına bakın.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Operatörler](~/_csharplang/spec/expressions.md#operators) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [İfadeler](../../programming-guide/statements-expressions-operators/expressions.md)
