---
title: true işleci (C# Başvurusu)
ms.date: 12/03/2018
helpviewer_keywords:
- true operator [C#]
ms.assetid: acaba817-5da5-4364-b3b2-2e5c75ec1839
ms.openlocfilehash: 17830e5ae842255dcf71e73097779d17520b81e6
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130682"
---
# <a name="true-operator-c-reference"></a><span data-ttu-id="549c2-102">true işleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="549c2-102">true operator (C# Reference)</span></span>

<span data-ttu-id="549c2-103">Döndürür [bool](bool.md) değer `true` işleneni kesinlikle doğru olduğunu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="549c2-103">Returns the [bool](bool.md) value `true` to indicate that an operand is definitely true.</span></span> <span data-ttu-id="549c2-104">Bir türü tanımlıyorsa `true` işleci, bu da tanımlamalıdır [false işleci](false-operator.md).</span><span class="sxs-lookup"><span data-stu-id="549c2-104">If a type defines the `true` operator, it must also define the [false operator](false-operator.md).</span></span> <span data-ttu-id="549c2-105">`true` Ve `false` işleçleri birbirini tamamlar için garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="549c2-105">The `true` and `false` operators are not guaranteed to complement each other.</span></span>

<span data-ttu-id="549c2-106">Her ikisi de tanımlar örneğin `true` ve `false` işleçleri görmek [false işleci](false-operator.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="549c2-106">For the example that defines both `true` and `false` operators, see the [false operator](false-operator.md) article.</span></span>

> [!TIP]
> <span data-ttu-id="549c2-107">Kullanım `bool?` türü üç değerli mantığı, örneğin,'i desteklemeniz gerekiyorsa çalışırken üç değerli mantıksal türünü destekleyen veritabanları ile.</span><span class="sxs-lookup"><span data-stu-id="549c2-107">Use the `bool?` type, if you need to support the three-valued logic, for example, when you work with databases that support a three-valued logical type.</span></span> <span data-ttu-id="549c2-108">Daha fazla bilgi için [bool? türü](../../programming-guide/nullable-types/using-nullable-types.md#the-bool-type) bölümünü [boş değer atanabilir türleri kullanma](../../programming-guide/nullable-types/using-nullable-types.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="549c2-108">For more information, see [The bool? type](../../programming-guide/nullable-types/using-nullable-types.md#the-bool-type) section of the [Using nullable types](../../programming-guide/nullable-types/using-nullable-types.md) article.</span></span>

<span data-ttu-id="549c2-109">Bir tür ederse ile tanımlanan `true` işleci [aşırı](operator.md) [mantıksal OR işlecinin](../operators/or-operator.md) `|` belirli bir şekilde [koşullu mantıksal OR işlecinin](../operators/conditional-or-operator.md) `||`, short-circuiting, olduğu değerlendirmesi yapılamıyor, o türündeki işlenenler için.</span><span class="sxs-lookup"><span data-stu-id="549c2-109">If a type with the defined `true` operator [overloads](operator.md) the [logical OR operator](../operators/or-operator.md) `|` in a certain way, the [conditional logical OR operator](../operators/conditional-or-operator.md) `||`, which is short-circuiting, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="549c2-110">Daha fazla bilgi için [kullanıcı tanımlı koşullu mantıksal işleçler](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) bölümünü [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="549c2-110">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

<span data-ttu-id="549c2-111">Tanımlanan bir türü `true` işleci denetleyen bir koşullu deyim sonucu türü olabilir [varsa](if-else.md), [yapmak](do.md), [sırada](while.md), ve [ için](for.md) deyimleri ve [koşullu işleç `?:` ](../operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="549c2-111">A type with the defined `true` operator can be the type of a result of a controlling conditional expression in the [if](if-else.md), [do](do.md), [while](while.md), and [for](for.md) statements and in the [conditional operator `?:`](../operators/conditional-operator.md).</span></span> <span data-ttu-id="549c2-112">Daha fazla bilgi için [Boolean ifadeler](~/_csharplang/spec/expressions.md#boolean-expressions) bölümünü [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="549c2-112">For more information, see the [Boolean expressions](~/_csharplang/spec/expressions.md#boolean-expressions) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="549c2-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="549c2-113">See also</span></span>

- [<span data-ttu-id="549c2-114">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="549c2-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="549c2-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="549c2-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="549c2-116">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="549c2-116">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="549c2-117">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="549c2-117">C# Operators</span></span>](../operators/index.md)
- [<span data-ttu-id="549c2-118">`true` değişmez değer</span><span class="sxs-lookup"><span data-stu-id="549c2-118">`true` literal</span></span>](true-literal.md)