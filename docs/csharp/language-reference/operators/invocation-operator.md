---
title: () işleci - C# başvurusu
ms.custom: seodec18
ms.date: 01/15/2019
f1_keywords:
- ()_CSharpKeyword
helpviewer_keywords:
- type conversion [C#], () operator
- cast operator [C#]
- () operator [C#]
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
ms.openlocfilehash: 8f7382a49c81b6fd8e104b864ffc2f70db7fe4a6
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758117"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="7f0b2-102">() işleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="7f0b2-102">() operator (C# Reference)</span></span>

<span data-ttu-id="7f0b2-103">Parantez `()`, yöntem veya temsilci çağırma veya cast ifadeleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7f0b2-103">Parentheses, `()`, are typically used for method or delegate invocation or in cast expressions.</span></span>

<span data-ttu-id="7f0b2-104">Ayrıca bir ifade işlemlerinde değerlendirilecek sırayı belirtmek için parantez kullanın.</span><span class="sxs-lookup"><span data-stu-id="7f0b2-104">You also use parentheses to specify the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="7f0b2-105">Daha fazla bilgi için [ayraç ekleme](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) bölümünü [işleçleri](../../programming-guide/statements-expressions-operators/operators.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="7f0b2-105">For more information, see the [Adding parentheses](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) section of the [Operators](../../programming-guide/statements-expressions-operators/operators.md) article.</span></span> <span data-ttu-id="7f0b2-106">İşleçler, öncelik düzeyine göre sıralı listesi için bkz. [ C# işleçleri](index.md).</span><span class="sxs-lookup"><span data-stu-id="7f0b2-106">For the list of operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="method-invocation"></a><span data-ttu-id="7f0b2-107">Yöntem çağırma</span><span class="sxs-lookup"><span data-stu-id="7f0b2-107">Method invocation</span></span>

<span data-ttu-id="7f0b2-108">Aşağıdaki örnek, dolgulu veya bağımsız değişkenleri, bir temsilci yöntemi çağırma gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7f0b2-108">The following example demonstrates how to invoke a method, with or without arguments, and a delegate:</span></span>

[!code-csharp-interactive[use for invocation](~/samples/csharp/language-reference/operators/InvocationOperatorExamples.cs#Invocation)]

<span data-ttu-id="7f0b2-109">Çağırdığınızda parantez de kullanmak bir [Oluşturucusu](../../programming-guide/classes-and-structs/constructors.md) ile bir [ `new` ](../keywords/new-operator.md) işleci.</span><span class="sxs-lookup"><span data-stu-id="7f0b2-109">You also use parentheses when you invoke a [constructor](../../programming-guide/classes-and-structs/constructors.md) with a [`new`](../keywords/new-operator.md) operator.</span></span>

<span data-ttu-id="7f0b2-110">Yöntemleri hakkında daha fazla bilgi için bkz. [yöntemleri](../../programming-guide/classes-and-structs/methods.md).</span><span class="sxs-lookup"><span data-stu-id="7f0b2-110">For more information about methods, see [Methods](../../programming-guide/classes-and-structs/methods.md).</span></span> <span data-ttu-id="7f0b2-111">Temsilciler hakkında daha fazla bilgi için bkz. [Temsilciler](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="7f0b2-111">For more information about delegates, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="cast-expression"></a><span data-ttu-id="7f0b2-112">Cast ifadesi</span><span class="sxs-lookup"><span data-stu-id="7f0b2-112">Cast expression</span></span>

<span data-ttu-id="7f0b2-113">Atama ifadesi formun `(T)E` ifadenin değerine dönüştürmek için bir dönüştürme operatörünün çağırır `E` türüne `T`.</span><span class="sxs-lookup"><span data-stu-id="7f0b2-113">A cast expression of the form `(T)E` invokes a conversion operator to convert the value of expression `E` to type `T`.</span></span> <span data-ttu-id="7f0b2-114">Açık bir dönüştürme türünden varsa `E` türüne `T`, bir derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="7f0b2-114">If no explicit conversion exists from the type of `E` to type `T`, a compile-time error occurs.</span></span> <span data-ttu-id="7f0b2-115">Bir dönüşüm işleci tanımlama hakkında daha fazla bilgi için bkz: [açık](../keywords/explicit.md) ve [örtük](../keywords/implicit.md) anahtar sözcüğü makaleler.</span><span class="sxs-lookup"><span data-stu-id="7f0b2-115">For information about how to define a conversion operator, see the [explicit](../keywords/explicit.md) and [implicit](../keywords/implicit.md) keyword articles.</span></span>

<span data-ttu-id="7f0b2-116">Aşağıdaki örnek, sayısal türler arasında tür dönüştürme gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7f0b2-116">The following example demonstrates type conversion between numeric types:</span></span>

[!code-csharp-interactive[use for cast](~/samples/csharp/language-reference/operators/InvocationOperatorExamples.cs#Cast)]

<span data-ttu-id="7f0b2-117">Sayısal türler arasında önceden tanımlanmış açık dönüştürmeler hakkında daha fazla bilgi için bkz: [açık sayısal dönüşümler tablosu](../keywords/explicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="7f0b2-117">For more information about predefined explicit conversions between numeric types, see [Explicit numeric conversions table](../keywords/explicit-numeric-conversions-table.md).</span></span>

<span data-ttu-id="7f0b2-118">Daha fazla bilgi için [atama ve tür dönüştürmeleri](../../programming-guide/types/casting-and-type-conversions.md) ve [dönüştürme işleçleri](../../programming-guide/statements-expressions-operators/conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="7f0b2-118">For more information, see [Casting and type conversions](../../programming-guide/types/casting-and-type-conversions.md) and [Conversion operators](../../programming-guide/statements-expressions-operators/conversion-operators.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="7f0b2-119">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="7f0b2-119">Operator overloadability</span></span>

<span data-ttu-id="7f0b2-120">İşleç `()` aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="7f0b2-120">The operator `()` cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="7f0b2-121">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="7f0b2-121">C# language specification</span></span>

<span data-ttu-id="7f0b2-122">Daha fazla bilgi için [çağrı ifadeleri](~/_csharplang/spec/expressions.md#invocation-expressions) ve [Cast ifadeleri](~/_csharplang/spec/expressions.md#cast-expressions) bölümlerini [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="7f0b2-122">For more information, see the [Invocation expressions](~/_csharplang/spec/expressions.md#invocation-expressions) and [Cast expressions](~/_csharplang/spec/expressions.md#cast-expressions) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7f0b2-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f0b2-123">See also</span></span>

- [<span data-ttu-id="7f0b2-124">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="7f0b2-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7f0b2-125">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7f0b2-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7f0b2-126">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="7f0b2-126">C# Operators</span></span>](index.md)
