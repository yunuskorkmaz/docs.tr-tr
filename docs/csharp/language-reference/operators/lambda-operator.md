---
title: = > operator- C# Reference
ms.custom: seodec18
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: 3b3a5c2e96e92271da66cbd8f1039a9ec97544fa
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971226"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="6c47a-102">= > işleci (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="6c47a-102">=> operator (C# reference)</span></span>

<span data-ttu-id="6c47a-103">`=>` Belirteç iki biçimde desteklenir: lambda işleci, bir üye adı ayırıcı olarak ve bir ifade gövdesi tanımında üye uygulama.</span><span class="sxs-lookup"><span data-stu-id="6c47a-103">The `=>` token is supported in two forms: as the lambda operator and as a separator of a member name and the member implementation in an expression body definition.</span></span>

## <a name="lambda-operator"></a><span data-ttu-id="6c47a-104">Lambda işleci</span><span class="sxs-lookup"><span data-stu-id="6c47a-104">Lambda operator</span></span>

<span data-ttu-id="6c47a-105">[Lambda ifadelerinde](../../programming-guide/statements-expressions-operators/lambda-expressions.md)lambda işleci `=>` , sol taraftaki giriş değişkenlerini sağ taraftaki lambda gövdesinden ayırır.</span><span class="sxs-lookup"><span data-stu-id="6c47a-105">In [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md), the lambda operator `=>` separates the input variables on the left side from the lambda body on the right side.</span></span>

<span data-ttu-id="6c47a-106">Aşağıdaki örnek, lambda ifadelerinin kullanımını göstermek için yöntem sözdizimi ile [LINQ](../../programming-guide/concepts/linq/index.md) özelliğini kullanır:</span><span class="sxs-lookup"><span data-stu-id="6c47a-106">The following example uses the [LINQ](../../programming-guide/concepts/linq/index.md) feature with method syntax to demonstrate the usage of lambda expressions:</span></span>

[!code-csharp-interactive[infer types of input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#InferredTypes)]

<span data-ttu-id="6c47a-107">Lambda ifadelerinin giriş değişkenleri, derleme zamanında kesin olarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="6c47a-107">Input variables of lambda expressions are strongly typed at compile time.</span></span> <span data-ttu-id="6c47a-108">Derleyici, giriş değişkenlerinin türlerini, önceki örnekte olduğu gibi çıkarsancan tür bildirimlerini atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c47a-108">When the compiler can infer the types of input variables, like in the preceding example, you may omit type declarations.</span></span> <span data-ttu-id="6c47a-109">Giriş değişkenlerinin türünü belirtmeniz gerekiyorsa, aşağıdaki örnekte gösterildiği gibi her bir değişken için bunu yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="6c47a-109">If you need to specify the type of input variables, you must do that for each variable, as the following example shows:</span></span>

[!code-csharp-interactive[specify types of input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#ExplicitTypes)]

<span data-ttu-id="6c47a-110">Aşağıdaki örnek, giriş değişkenleri olmadan bir lambda ifadesinin nasıl tanımlanacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="6c47a-110">The following example shows how to define a lambda expression without input variables:</span></span>

[!code-csharp-interactive[without input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#WithoutInput)]

<span data-ttu-id="6c47a-111">Daha fazla bilgi için bkz. [lambda ifadeleri](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="6c47a-111">For more information, see [Lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>

## <a name="expression-body-definition"></a><span data-ttu-id="6c47a-112">İfade gövdesi tanımı</span><span class="sxs-lookup"><span data-stu-id="6c47a-112">Expression body definition</span></span>

<span data-ttu-id="6c47a-113">Bir ifade gövdesi tanımında aşağıdaki genel sözdizimi vardır:</span><span class="sxs-lookup"><span data-stu-id="6c47a-113">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="6c47a-114">Burada `expression` geçerli bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="6c47a-114">where `expression` is a valid expression.</span></span> <span data-ttu-id="6c47a-115">Dönüş türü `expression` üyenin dönüş türüne örtük olarak dönüştürülebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6c47a-115">The return type of `expression` must be implicitly convertible to the member's return type.</span></span> <span data-ttu-id="6c47a-116">Üyenin `void` dönüş türü ise veya üye bir Oluşturucu, Sonlandırıcı veya özellik `set` erişimcisi `expression` ise [*deyim ifadesi*](~/_csharplang/spec/statements.md#expression-statements)olmalıdır; daha sonra herhangi bir türde olabilir.</span><span class="sxs-lookup"><span data-stu-id="6c47a-116">If the member's return type is `void` or if the member is a constructor, a finalizer, or a property `set` accessor, `expression` must be a [*statement expression*](~/_csharplang/spec/statements.md#expression-statements); it can be of any type then.</span></span>

<span data-ttu-id="6c47a-117">Aşağıdaki örnek bir `Person.ToString` Yöntem için bir ifade gövdesi tanımı gösterir:</span><span class="sxs-lookup"><span data-stu-id="6c47a-117">The following example shows an expression body definition for a `Person.ToString` method:</span></span>

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

<span data-ttu-id="6c47a-118">Bu, aşağıdaki yöntem tanımının bir toplu sürümüdür:</span><span class="sxs-lookup"><span data-stu-id="6c47a-118">It's a shorthand version of the following method definition:</span></span>

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```

<span data-ttu-id="6c47a-119">Yöntemler ve salt okunurdur özellikleri için ifade gövdesi tanımları C# 6 ' dan başlayarak desteklenir.</span><span class="sxs-lookup"><span data-stu-id="6c47a-119">Expression body definitions for methods and read-only properties are supported starting with C# 6.</span></span> <span data-ttu-id="6c47a-120">Oluşturucular, sonlandırıcılar, özellik erişimcileri ve Dizin oluşturucular için ifade gövdesi tanımları 7,0 ile C# başlayarak desteklenir.</span><span class="sxs-lookup"><span data-stu-id="6c47a-120">Expression body definitions for constructors, finalizers, property accessors, and indexers are supported starting with C# 7.0.</span></span>

<span data-ttu-id="6c47a-121">Daha fazla bilgi için bkz. [Expression-Bodied Üyeler](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="6c47a-121">For more information, see [Expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="6c47a-122">Operatör overloadability</span><span class="sxs-lookup"><span data-stu-id="6c47a-122">Operator overloadability</span></span>

<span data-ttu-id="6c47a-123">`=>` İşleç aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="6c47a-123">The `=>` operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="6c47a-124">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="6c47a-124">C# language specification</span></span>

<span data-ttu-id="6c47a-125">Daha fazla bilgi için, [ C# dil belirtiminin](../language-specification/index.md) [anonim işlev ifadeleri](~/_csharplang/spec/expressions.md#anonymous-function-expressions) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="6c47a-125">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6c47a-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c47a-126">See also</span></span>

- [<span data-ttu-id="6c47a-127">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="6c47a-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="6c47a-128">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="6c47a-128">C# operators</span></span>](index.md)
- [<span data-ttu-id="6c47a-129">Lambda ifadeleri</span><span class="sxs-lookup"><span data-stu-id="6c47a-129">Lambda expressions</span></span>](../../programming-guide/statements-expressions-operators/lambda-expressions.md)
- [<span data-ttu-id="6c47a-130">İfade gövdeli üyeler</span><span class="sxs-lookup"><span data-stu-id="6c47a-130">Expression-bodied members</span></span>](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)
