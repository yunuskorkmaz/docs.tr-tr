---
title: = > İşleci - C# başvurusu
ms.custom: seodec18
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: 0cded9d23d67e6afc8b01d6711e42759b4b51fab
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55275866"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="82fb2-102">= > işleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="82fb2-102">=> operator (C# Reference)</span></span>

<span data-ttu-id="82fb2-103">`=>` Belirteç iki biçimde desteklenir: lambda işlecini ve üyenin adını ve bir deyim gövdesi tanımına üye uygulamasında bir ayırıcı olarak.</span><span class="sxs-lookup"><span data-stu-id="82fb2-103">The `=>` token is supported in two forms: as the lambda operator and as a separator of a member name and the member implementation in an expression body definition.</span></span>

## <a name="lambda-operator"></a><span data-ttu-id="82fb2-104">Lambda işleci</span><span class="sxs-lookup"><span data-stu-id="82fb2-104">Lambda operator</span></span>

<span data-ttu-id="82fb2-105">İçinde [lambda ifadeleri](../../programming-guide/statements-expressions-operators/lambda-expressions.md), lambda işlecini `=>` işlecin sağ tarafındaki lambda gövdesinden sol tarafında giriş değişkenleri ayırır.</span><span class="sxs-lookup"><span data-stu-id="82fb2-105">In [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md), the lambda operator `=>` separates the input variables on the left side from the lambda body on the right side.</span></span>

<span data-ttu-id="82fb2-106">Aşağıdaki örnekte [LINQ](../../programming-guide/concepts/linq/index.md) özelliği ile yöntem sözdizimi lambda ifadeleri kullanımını göstermek için:</span><span class="sxs-lookup"><span data-stu-id="82fb2-106">The following example uses the [LINQ](../../programming-guide/concepts/linq/index.md) feature with method syntax to demonstrate the usage of lambda expressions:</span></span>

[!code-csharp-interactive[infer types of input variables](~/samples/snippets/csharp/language-reference/operators/LambdaOperatorExamples.cs#InferredTypes)]

<span data-ttu-id="82fb2-107">Lambda ifadeleri girdi değişkenleri, derleme zamanında kesin türlü yapılır.</span><span class="sxs-lookup"><span data-stu-id="82fb2-107">Input variables of lambda expressions are strongly typed at compile time.</span></span> <span data-ttu-id="82fb2-108">Derleyici giriş değişkenleri tür çıkarımını, gibi önceki örnekte, tür bildirimleri çıkarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82fb2-108">When the compiler can infer the types of input variables, like in the preceding example, you may omit type declarations.</span></span> <span data-ttu-id="82fb2-109">Girdi değişkeni türünü belirtmek gerekiyorsa, aşağıdaki örnekte gösterildiği gibi her bir değişken için yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="82fb2-109">If you need to specify the type of input variables, you must do that for each variable, as the following example shows:</span></span>

[!code-csharp-interactive[specify types of input variables](~/samples/snippets/csharp/language-reference/operators/LambdaOperatorExamples.cs#ExplicitTypes)]

<span data-ttu-id="82fb2-110">Aşağıdaki örnek nasıl tanımlanacağını girdi değişkenleri olmadan bir lambda ifadesi gösterir:</span><span class="sxs-lookup"><span data-stu-id="82fb2-110">The following example shows how to define a lambda expression without input variables:</span></span>

[!code-csharp-interactive[without input variables](~/samples/snippets/csharp/language-reference/operators/LambdaOperatorExamples.cs#WithoutInput)]

<span data-ttu-id="82fb2-111">Daha fazla bilgi için [Lambda ifadeleri](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="82fb2-111">For more information, see [Lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>

## <a name="expression-body-definition"></a><span data-ttu-id="82fb2-112">İfade gövdesi tanımı</span><span class="sxs-lookup"><span data-stu-id="82fb2-112">Expression body definition</span></span>

<span data-ttu-id="82fb2-113">Bir ifade gövdesi tanımına genel sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="82fb2-113">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="82fb2-114">Burada *ifade* geçerli bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="82fb2-114">where *expression* is a valid expression.</span></span> <span data-ttu-id="82fb2-115">Unutmayın *ifade* olabilir bir *deyim ifadesi* üyenin dönüş türü ise yalnızca `void`, veya üye bir oluşturucu, bir sonlandırıcı ya da bir özellik ise `set` erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="82fb2-115">Note that *expression* can be a *statement expression* only if the member's return type is `void`, or if the member is a constructor, a finalizer, or a property `set` accessor.</span></span>

<span data-ttu-id="82fb2-116">Aşağıdaki örnek bir ifade gövdesi tanımını gösterir bir `Person.ToString` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="82fb2-116">The following example shows an expression body definition for a `Person.ToString` method:</span></span>

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

<span data-ttu-id="82fb2-117">Aşağıdaki yöntem tanımının bir toplu sürümdür:</span><span class="sxs-lookup"><span data-stu-id="82fb2-117">It's a shorthand version of the following method definition:</span></span>

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```

<span data-ttu-id="82fb2-118">İfade gövdesi tanımlarında yöntemleri ve özellikleri salt okunur başlayarak desteklenir C# 6.</span><span class="sxs-lookup"><span data-stu-id="82fb2-118">Expression body definitions for methods and read-only properties are supported starting with C# 6.</span></span> <span data-ttu-id="82fb2-119">Oluşturucular, bir Sonlandırıcı, özellik erişimcileri ve dizin oluşturucular için ifade gövdesi tanımları sürümünden itibaren desteklenir C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="82fb2-119">Expression body definitions for constructors, finalizers, property accessors, and indexers are supported starting with C# 7.0.</span></span>

<span data-ttu-id="82fb2-120">Daha fazla bilgi için [ifade gövdeli üyeler](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="82fb2-120">For more information, see [Expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="82fb2-121">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="82fb2-121">Operator overloadability</span></span>

<span data-ttu-id="82fb2-122">`=>` İşleci aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="82fb2-122">The `=>` operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="82fb2-123">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="82fb2-123">C# language specification</span></span>

<span data-ttu-id="82fb2-124">Daha fazla bilgi için [anonim işlev ifadeleri](~/_csharplang/spec/expressions.md#anonymous-function-expressions) bölümünü [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="82fb2-124">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="82fb2-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82fb2-125">See also</span></span>

- [<span data-ttu-id="82fb2-126">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="82fb2-126">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="82fb2-127">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="82fb2-127">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="82fb2-128">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="82fb2-128">C# Operators</span></span>](index.md)
- [<span data-ttu-id="82fb2-129">Lambda ifadeleri</span><span class="sxs-lookup"><span data-stu-id="82fb2-129">Lambda expressions</span></span>](../../programming-guide/statements-expressions-operators/lambda-expressions.md)
- [<span data-ttu-id="82fb2-130">İfade gövdeli üyeler</span><span class="sxs-lookup"><span data-stu-id="82fb2-130">Expression-bodied members</span></span>](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)