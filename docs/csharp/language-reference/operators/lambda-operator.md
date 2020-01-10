---
title: = > operator- C# Reference
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: 61cc3c3ab4f0b22c4040a9b8a025c81071f4d942
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712708"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="5416c-102">= > işleci (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="5416c-102">=> operator (C# reference)</span></span>

<span data-ttu-id="5416c-103">`=>` belirteci iki biçimde desteklenir: [lambda işleci](#lambda-operator) , bir üye adı ve bir [ifade gövdesi tanımında](#expression-body-definition)üye uygulama için bir ayırıcı olarak.</span><span class="sxs-lookup"><span data-stu-id="5416c-103">The `=>` token is supported in two forms: as the [lambda operator](#lambda-operator) and as a separator of a member name and the member implementation in an [expression body definition](#expression-body-definition).</span></span>

## <a name="lambda-operator"></a><span data-ttu-id="5416c-104">Lambda işleci</span><span class="sxs-lookup"><span data-stu-id="5416c-104">Lambda operator</span></span>

<span data-ttu-id="5416c-105">[Lambda ifadelerinde](../../programming-guide/statements-expressions-operators/lambda-expressions.md)lambda işleci `=>` sol taraftaki giriş parametrelerini sağ taraftaki lambda gövdesinden ayırır.</span><span class="sxs-lookup"><span data-stu-id="5416c-105">In [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md), the lambda operator `=>` separates the input parameters on the left side from the lambda body on the right side.</span></span>

<span data-ttu-id="5416c-106">Aşağıdaki örnek, lambda ifadelerinin kullanımını göstermek için yöntem sözdizimi ile [LINQ](../../programming-guide/concepts/linq/index.md) özelliğini kullanır:</span><span class="sxs-lookup"><span data-stu-id="5416c-106">The following example uses the [LINQ](../../programming-guide/concepts/linq/index.md) feature with method syntax to demonstrate the usage of lambda expressions:</span></span>

[!code-csharp-interactive[infer types of input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#InferredTypes)]

<span data-ttu-id="5416c-107">Bir lambda ifadesinin giriş parametreleri derleme zamanında kesin olarak yazılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5416c-107">Input parameters of a lambda expression are strongly typed at compile time.</span></span> <span data-ttu-id="5416c-108">Derleyici, giriş parametrelerinin türlerini, önceki örnekte olduğu gibi çıkarsancan, tür bildirimlerini atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5416c-108">When the compiler can infer the types of input parameters, like in the preceding example, you may omit type declarations.</span></span> <span data-ttu-id="5416c-109">Giriş parametrelerinin türünü belirtmeniz gerekiyorsa, aşağıdaki örnekte gösterildiği gibi her bir parametre için bunu yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="5416c-109">If you need to specify the type of input parameters, you must do that for each parameter, as the following example shows:</span></span>

[!code-csharp-interactive[specify types of input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#ExplicitTypes)]

<span data-ttu-id="5416c-110">Aşağıdaki örnek, giriş parametreleri olmadan bir lambda ifadesinin nasıl tanımlanacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="5416c-110">The following example shows how to define a lambda expression without input parameters:</span></span>

[!code-csharp-interactive[without input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#WithoutInput)]

<span data-ttu-id="5416c-111">Daha fazla bilgi için bkz. [lambda ifadeleri](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="5416c-111">For more information, see [Lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>

## <a name="expression-body-definition"></a><span data-ttu-id="5416c-112">İfade gövdesi tanımı</span><span class="sxs-lookup"><span data-stu-id="5416c-112">Expression body definition</span></span>

<span data-ttu-id="5416c-113">Bir ifade gövdesi tanımında aşağıdaki genel sözdizimi vardır:</span><span class="sxs-lookup"><span data-stu-id="5416c-113">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="5416c-114">`expression` geçerli bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="5416c-114">where `expression` is a valid expression.</span></span> <span data-ttu-id="5416c-115">`expression` dönüş türü üyenin dönüş türüne örtük olarak dönüştürülebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5416c-115">The return type of `expression` must be implicitly convertible to the member's return type.</span></span> <span data-ttu-id="5416c-116">Üyenin dönüş türü `void` veya üye bir Oluşturucu, Sonlandırıcı veya özellik `set` erişimcisi ise, `expression` herhangi bir türde olabilen bir [*deyim ifadesi*](~/_csharplang/spec/statements.md#expression-statements)olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5416c-116">If the member's return type is `void` or if the member is a constructor, a finalizer, or a property `set` accessor, `expression` must be a [*statement expression*](~/_csharplang/spec/statements.md#expression-statements), which can be of any type.</span></span>

<span data-ttu-id="5416c-117">Aşağıdaki örnekte, bir `Person.ToString` yöntemi için bir ifade gövde tanımı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="5416c-117">The following example shows an expression body definition for a `Person.ToString` method:</span></span>

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

<span data-ttu-id="5416c-118">Bu, aşağıdaki yöntem tanımının bir toplu sürümüdür:</span><span class="sxs-lookup"><span data-stu-id="5416c-118">It's a shorthand version of the following method definition:</span></span>

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```

<span data-ttu-id="5416c-119">Yöntemler, işleçler ve salt okunurdur özellikleri için ifade gövdesi tanımları C# 6 ' dan başlayarak desteklenir.</span><span class="sxs-lookup"><span data-stu-id="5416c-119">Expression body definitions for methods, operators, and read-only properties are supported beginning with C# 6.</span></span> <span data-ttu-id="5416c-120">Oluşturucular, sonlandırıcılar ve özellik ve Dizin Oluşturucu erişimcileri için ifade gövdesi tanımları 7,0 ile C# başlayarak desteklenir.</span><span class="sxs-lookup"><span data-stu-id="5416c-120">Expression body definitions for constructors, finalizers, and property and indexer accessors are supported beginning with C# 7.0.</span></span>

<span data-ttu-id="5416c-121">Daha fazla bilgi için bkz. [Expression-Bodied Üyeler](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="5416c-121">For more information, see [Expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="5416c-122">Operatör overloadability</span><span class="sxs-lookup"><span data-stu-id="5416c-122">Operator overloadability</span></span>

<span data-ttu-id="5416c-123">`=>` işleci aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="5416c-123">The `=>` operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="5416c-124">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="5416c-124">C# language specification</span></span>

<span data-ttu-id="5416c-125">Lambda işleci hakkında daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [anonim işlev ifadeleri](~/_csharplang/spec/expressions.md#anonymous-function-expressions) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="5416c-125">For more information about the lambda operator, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5416c-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5416c-126">See also</span></span>

- [<span data-ttu-id="5416c-127">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="5416c-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="5416c-128">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="5416c-128">C# operators</span></span>](index.md)
