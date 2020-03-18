---
title: => işleci - C# referansı
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: 15c02e11610866f359e3e3a7e2751ded918154b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846265"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="a7e70-102">=> işleci (C# referansı)</span><span class="sxs-lookup"><span data-stu-id="a7e70-102">=> operator (C# reference)</span></span>

<span data-ttu-id="a7e70-103">Belirteç `=>` iki şekilde desteklenir: [lambda operatörü](#lambda-operator) olarak ve bir üye adı ve bir [ifade gövdesi tanımında](#expression-body-definition)üye uygulaması ayırıcı olarak .</span><span class="sxs-lookup"><span data-stu-id="a7e70-103">The `=>` token is supported in two forms: as the [lambda operator](#lambda-operator) and as a separator of a member name and the member implementation in an [expression body definition](#expression-body-definition).</span></span>

## <a name="lambda-operator"></a><span data-ttu-id="a7e70-104">Lambda operatörü</span><span class="sxs-lookup"><span data-stu-id="a7e70-104">Lambda operator</span></span>

<span data-ttu-id="a7e70-105">[Lambda ifadelerinde lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md)operatörü `=>` sol taraftaki giriş parametrelerini sağ taraftaki lambda gövdesinden ayırır.</span><span class="sxs-lookup"><span data-stu-id="a7e70-105">In [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md), the lambda operator `=>` separates the input parameters on the left side from the lambda body on the right side.</span></span>

<span data-ttu-id="a7e70-106">Aşağıdaki örnek, lambda ifadelerinin kullanımını göstermek için yöntem sözdizimi ile [LINQ](../../programming-guide/concepts/linq/index.md) özelliğini kullanır:</span><span class="sxs-lookup"><span data-stu-id="a7e70-106">The following example uses the [LINQ](../../programming-guide/concepts/linq/index.md) feature with method syntax to demonstrate the usage of lambda expressions:</span></span>

[!code-csharp-interactive[infer types of input variables](snippets/LambdaOperator.cs#InferredTypes)]

<span data-ttu-id="a7e70-107">Lambda ifadesinin giriş parametreleri derleme zamanında güçlü bir şekilde yazılır.</span><span class="sxs-lookup"><span data-stu-id="a7e70-107">Input parameters of a lambda expression are strongly typed at compile time.</span></span> <span data-ttu-id="a7e70-108">Derleyici, önceki örnekte olduğu gibi giriş parametreleri türlerini çıkarabildiği zaman, tür bildirimlerini atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a7e70-108">When the compiler can infer the types of input parameters, like in the preceding example, you may omit type declarations.</span></span> <span data-ttu-id="a7e70-109">Giriş parametrelerinin türünü belirtmeniz gerekiyorsa, aşağıdaki örnekte görüldüğü gibi, bunu her parametre için yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="a7e70-109">If you need to specify the type of input parameters, you must do that for each parameter, as the following example shows:</span></span>

[!code-csharp-interactive[specify types of input variables](snippets/LambdaOperator.cs#ExplicitTypes)]

<span data-ttu-id="a7e70-110">Aşağıdaki örnek, giriş parametreleri olmadan bir lambda ifadesinin nasıl tanımlandığını gösterir:</span><span class="sxs-lookup"><span data-stu-id="a7e70-110">The following example shows how to define a lambda expression without input parameters:</span></span>

[!code-csharp-interactive[without input variables](snippets/LambdaOperator.cs#WithoutInput)]

<span data-ttu-id="a7e70-111">Daha fazla bilgi için [Lambda ifadeleri'ne](../../programming-guide/statements-expressions-operators/lambda-expressions.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="a7e70-111">For more information, see [Lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>

## <a name="expression-body-definition"></a><span data-ttu-id="a7e70-112">İfade gövdesi tanımı</span><span class="sxs-lookup"><span data-stu-id="a7e70-112">Expression body definition</span></span>

<span data-ttu-id="a7e70-113">Bir ifade gövdesi tanımı aşağıdaki genel sözdizimine sahiptir:</span><span class="sxs-lookup"><span data-stu-id="a7e70-113">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="a7e70-114">nerede `expression` geçerli bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="a7e70-114">where `expression` is a valid expression.</span></span> <span data-ttu-id="a7e70-115">İade türü, `expression` üyenin dönüş türüne dolaylı olarak dönüştürülebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a7e70-115">The return type of `expression` must be implicitly convertible to the member's return type.</span></span> <span data-ttu-id="a7e70-116">Üyenin dönüş türü veya `void` üye bir yapıcı, bir sonlandırıcı veya bir `set` özellik erişime sahip ise, `expression` herhangi bir türde olabilir bir ifade [*ifadesi*](~/_csharplang/spec/statements.md#expression-statements)olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a7e70-116">If the member's return type is `void` or if the member is a constructor, a finalizer, or a property `set` accessor, `expression` must be a [*statement expression*](~/_csharplang/spec/statements.md#expression-statements), which can be of any type.</span></span>

<span data-ttu-id="a7e70-117">Aşağıdaki örnekte bir `Person.ToString` yöntem için bir ifade gövdesi tanımı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="a7e70-117">The following example shows an expression body definition for a `Person.ToString` method:</span></span>

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

<span data-ttu-id="a7e70-118">Aşağıdaki yöntem tanımının kısaltmasıdır:</span><span class="sxs-lookup"><span data-stu-id="a7e70-118">It's a shorthand version of the following method definition:</span></span>

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```

<span data-ttu-id="a7e70-119">Yöntemler, işleçler ve salt okunur özellikler için ifade gövdesi tanımları C# 6 ile başlayarak desteklenir.</span><span class="sxs-lookup"><span data-stu-id="a7e70-119">Expression body definitions for methods, operators, and read-only properties are supported beginning with C# 6.</span></span> <span data-ttu-id="a7e70-120">Oluşturucular, sonlandırıcılar ve özellik ve dizinleyici eriştirenler için ifade gövdesi tanımları C# 7.0 ile başlayan desteklenir.</span><span class="sxs-lookup"><span data-stu-id="a7e70-120">Expression body definitions for constructors, finalizers, and property and indexer accessors are supported beginning with C# 7.0.</span></span>

<span data-ttu-id="a7e70-121">Daha fazla bilgi için Bkz. [Expression gövdeli üyeler.](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)</span><span class="sxs-lookup"><span data-stu-id="a7e70-121">For more information, see [Expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="a7e70-122">Operatör aşırı yüklenebilirlik</span><span class="sxs-lookup"><span data-stu-id="a7e70-122">Operator overloadability</span></span>

<span data-ttu-id="a7e70-123">Operatör `=>` aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="a7e70-123">The `=>` operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a7e70-124">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="a7e70-124">C# language specification</span></span>

<span data-ttu-id="a7e70-125">lambda işleci hakkında daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Anonim işlev ifadeleri](~/_csharplang/spec/expressions.md#anonymous-function-expressions) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="a7e70-125">For more information about the lambda operator, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a7e70-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7e70-126">See also</span></span>

- [<span data-ttu-id="a7e70-127">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="a7e70-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="a7e70-128">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="a7e70-128">C# operators</span></span>](index.md)
