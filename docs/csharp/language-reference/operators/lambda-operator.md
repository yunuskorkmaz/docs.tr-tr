---
title: => işleci-C# başvurusu
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: b72b058c1709e7a643a70233cc3289d5d9165ca4
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916809"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="cac69-102">=> işleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="cac69-102">=> operator (C# reference)</span></span>

<span data-ttu-id="cac69-103">`=>`Belirteç iki biçimde desteklenir: [lambda işleci](#lambda-operator) , bir üye adı ayırıcı olarak ve bir [ifade gövdesi tanımında](#expression-body-definition)üye uygulama.</span><span class="sxs-lookup"><span data-stu-id="cac69-103">The `=>` token is supported in two forms: as the [lambda operator](#lambda-operator) and as a separator of a member name and the member implementation in an [expression body definition](#expression-body-definition).</span></span>

## <a name="lambda-operator"></a><span data-ttu-id="cac69-104">Lambda işleci</span><span class="sxs-lookup"><span data-stu-id="cac69-104">Lambda operator</span></span>

<span data-ttu-id="cac69-105">[Lambda ifadelerinde](../../programming-guide/statements-expressions-operators/lambda-expressions.md)lambda işleci, `=>` sol taraftaki giriş parametrelerini sağ taraftaki lambda gövdesinden ayırır.</span><span class="sxs-lookup"><span data-stu-id="cac69-105">In [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md), the lambda operator `=>` separates the input parameters on the left side from the lambda body on the right side.</span></span>

<span data-ttu-id="cac69-106">Aşağıdaki örnek, lambda ifadelerinin kullanımını göstermek için yöntem sözdizimi ile [LINQ](../../programming-guide/concepts/linq/index.md) özelliğini kullanır:</span><span class="sxs-lookup"><span data-stu-id="cac69-106">The following example uses the [LINQ](../../programming-guide/concepts/linq/index.md) feature with method syntax to demonstrate the usage of lambda expressions:</span></span>

[!code-csharp-interactive[infer types of input variables](snippets/shared/LambdaOperator.cs#InferredTypes)]

<span data-ttu-id="cac69-107">Bir lambda ifadesinin giriş parametreleri derleme zamanında kesin olarak yazılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cac69-107">Input parameters of a lambda expression are strongly typed at compile time.</span></span> <span data-ttu-id="cac69-108">Derleyici, giriş parametrelerinin türlerini, önceki örnekte olduğu gibi çıkarsancan, tür bildirimlerini atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cac69-108">When the compiler can infer the types of input parameters, like in the preceding example, you may omit type declarations.</span></span> <span data-ttu-id="cac69-109">Giriş parametrelerinin türünü belirtmeniz gerekiyorsa, aşağıdaki örnekte gösterildiği gibi her bir parametre için bunu yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="cac69-109">If you need to specify the type of input parameters, you must do that for each parameter, as the following example shows:</span></span>

[!code-csharp-interactive[specify types of input variables](snippets/shared/LambdaOperator.cs#ExplicitTypes)]

<span data-ttu-id="cac69-110">Aşağıdaki örnek, giriş parametreleri olmadan bir lambda ifadesinin nasıl tanımlanacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="cac69-110">The following example shows how to define a lambda expression without input parameters:</span></span>

[!code-csharp-interactive[without input variables](snippets/shared/LambdaOperator.cs#WithoutInput)]

<span data-ttu-id="cac69-111">Daha fazla bilgi için bkz. [lambda ifadeleri](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="cac69-111">For more information, see [Lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>

## <a name="expression-body-definition"></a><span data-ttu-id="cac69-112">İfade gövdesi tanımı</span><span class="sxs-lookup"><span data-stu-id="cac69-112">Expression body definition</span></span>

<span data-ttu-id="cac69-113">Bir ifade gövdesi tanımında aşağıdaki genel sözdizimi vardır:</span><span class="sxs-lookup"><span data-stu-id="cac69-113">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="cac69-114">Burada `expression` geçerli bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="cac69-114">where `expression` is a valid expression.</span></span> <span data-ttu-id="cac69-115">Dönüş türü `expression` üyenin dönüş türüne örtük olarak dönüştürülebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cac69-115">The return type of `expression` must be implicitly convertible to the member's return type.</span></span> <span data-ttu-id="cac69-116">Üyenin dönüş türü `void` veya üye bir Oluşturucu, Sonlandırıcı veya özellik ya da Dizin Oluşturucu erişimcisi ise, `set` `expression` bir [*deyim ifadesi*](~/_csharplang/spec/statements.md#expression-statements)olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cac69-116">If the member's return type is `void` or if the member is a constructor, a finalizer, or a property or indexer `set` accessor, `expression` must be a [*statement expression*](~/_csharplang/spec/statements.md#expression-statements).</span></span> <span data-ttu-id="cac69-117">İfadenin sonucu atıldığından, bu ifadenin dönüş türü herhangi bir tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="cac69-117">Because the expression's result is discarded, the return type of that expression can be any type.</span></span>

<span data-ttu-id="cac69-118">Aşağıdaki örnek bir yöntem için bir ifade gövdesi tanımı gösterir `Person.ToString` :</span><span class="sxs-lookup"><span data-stu-id="cac69-118">The following example shows an expression body definition for a `Person.ToString` method:</span></span>

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

<span data-ttu-id="cac69-119">Bu, aşağıdaki yöntem tanımının bir toplu sürümüdür:</span><span class="sxs-lookup"><span data-stu-id="cac69-119">It's a shorthand version of the following method definition:</span></span>

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```

<span data-ttu-id="cac69-120">Yöntemler, işleçler ve salt okunurdur özellikleri için ifade gövdesi tanımları C# 6 ' dan başlayarak desteklenir.</span><span class="sxs-lookup"><span data-stu-id="cac69-120">Expression body definitions for methods, operators, and read-only properties are supported beginning with C# 6.</span></span> <span data-ttu-id="cac69-121">Oluşturucular, sonlandırıcılar ve özellik ve Dizin Oluşturucu erişimcileri için ifade gövdesi tanımları C# 7,0 ile başlayarak desteklenir.</span><span class="sxs-lookup"><span data-stu-id="cac69-121">Expression body definitions for constructors, finalizers, and property and indexer accessors are supported beginning with C# 7.0.</span></span>

<span data-ttu-id="cac69-122">Daha fazla bilgi için bkz. [Expression-Bodied Üyeler](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="cac69-122">For more information, see [Expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="cac69-123">Operatör overloadability</span><span class="sxs-lookup"><span data-stu-id="cac69-123">Operator overloadability</span></span>

<span data-ttu-id="cac69-124">`=>`İşleç aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="cac69-124">The `=>` operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="cac69-125">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="cac69-125">C# language specification</span></span>

<span data-ttu-id="cac69-126">Lambda işleci hakkında daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [anonim işlev ifadeleri](~/_csharplang/spec/expressions.md#anonymous-function-expressions) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="cac69-126">For more information about the lambda operator, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cac69-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cac69-127">See also</span></span>

- [<span data-ttu-id="cac69-128">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="cac69-128">C# reference</span></span>](../index.md)
- [<span data-ttu-id="cac69-129">C# işleçleri ve ifadeleri</span><span class="sxs-lookup"><span data-stu-id="cac69-129">C# operators and expressions</span></span>](index.md)
