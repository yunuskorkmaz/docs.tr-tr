---
title: '! (null-forverme) işleci- C# başvuru'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: cf941e5e3fa3fc6313ef8b2ff5c176aec68c1e6b
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291727"
---
# <a name="-null-forgiving-operator-c-reference"></a><span data-ttu-id="7ce5c-103">!</span><span class="sxs-lookup"><span data-stu-id="7ce5c-103">!</span></span> <span data-ttu-id="7ce5c-104">(null-forverme) işleci (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="7ce5c-104">(null-forgiving) operator (C# reference)</span></span>

<span data-ttu-id="7ce5c-105">C# 8,0 ve üzeri sürümlerde bulunan birli sonek `!` işleci null-forverme işleçtir.</span><span class="sxs-lookup"><span data-stu-id="7ce5c-105">Available in C# 8.0 and later, the unary postfix `!` operator is the null-forgiving operator.</span></span> <span data-ttu-id="7ce5c-106">Etkin bir [null yapılabilir ek açıklama bağlamında](../../nullable-references.md#nullable-annotation-context), bir başvuru türünün `x` ' inin null olmadığını bildirmek için null-forverme işlecini kullanırsınız: `x!`.</span><span class="sxs-lookup"><span data-stu-id="7ce5c-106">In an enabled [nullable annotation context](../../nullable-references.md#nullable-annotation-context), you use the null-forgiving operator to declare that expression `x` of a reference type isn't null: `x!`.</span></span> <span data-ttu-id="7ce5c-107">Birli önek `!` işleci bir [mantıksal değilleme işleçtir](boolean-logical-operators.md#logical-negation-operator-).</span><span class="sxs-lookup"><span data-stu-id="7ce5c-107">The unary prefix `!` operator is a [logical negation operator](boolean-logical-operators.md#logical-negation-operator-).</span></span>

<span data-ttu-id="7ce5c-108">Null-forverme işlecinin çalışma zamanında hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="7ce5c-108">The null-forgiving operator has no effect at run time.</span></span> <span data-ttu-id="7ce5c-109">Yalnızca ifadenin null durumunu değiştirerek derleyicinin statik akış analizini etkiler.</span><span class="sxs-lookup"><span data-stu-id="7ce5c-109">It only affects the compiler's static flow analysis by changing the null state of the expression.</span></span> <span data-ttu-id="7ce5c-110">Çalışma zamanında, `x!` ifadesi temel alınan `x` ifadesinin sonucu olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="7ce5c-110">At run time, expression `x!` evaluates to the result of the underlying expression `x`.</span></span>

<span data-ttu-id="7ce5c-111">Null yapılabilir başvuru türleri özelliği hakkında daha fazla bilgi için bkz. [Nullable başvuru türleri](../../nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="7ce5c-111">For more information about the nullable reference types feature, see [Nullable reference types](../../nullable-references.md).</span></span>

## <a name="examples"></a><span data-ttu-id="7ce5c-112">Örnekler</span><span class="sxs-lookup"><span data-stu-id="7ce5c-112">Examples</span></span>

<span data-ttu-id="7ce5c-113">Null-forverme işlecinin kullanım çalışmalarından biri bağımsız değişken doğrulama mantığını test ediyor.</span><span class="sxs-lookup"><span data-stu-id="7ce5c-113">One of the use cases of the null-forgiving operator is in testing the argument validation logic.</span></span> <span data-ttu-id="7ce5c-114">Örneğin, aşağıdaki sınıfı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="7ce5c-114">For example, consider the following class:</span></span>

[!code-csharp[Person class](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#PersonClass)]

<span data-ttu-id="7ce5c-115">[MSTest test çerçevesini](../../../core/testing/unit-testing-with-mstest.md)kullanarak, oluşturucuda doğrulama mantığı için aşağıdaki testi oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7ce5c-115">Using the [MSTest test framework](../../../core/testing/unit-testing-with-mstest.md), you can create the following test for the validation logic in the constructor:</span></span>

[!code-csharp[Person test](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#TestPerson)]

<span data-ttu-id="7ce5c-116">Null-forverme işleci olmadan derleyici, önceki kod için şu uyarıyı üretir: `Warning CS8625: Cannot convert null literal to non-nullable reference type`.</span><span class="sxs-lookup"><span data-stu-id="7ce5c-116">Without the null-forgiving operator, the compiler generates the following warning for the preceding code: `Warning CS8625: Cannot convert null literal to non-nullable reference type`.</span></span> <span data-ttu-id="7ce5c-117">Null anlayalım işlecinin kullanımıyla, derleyicinin `null` ' ın geçtiğini ve hakkında uyarı olmaması gerektiğini bilmesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ce5c-117">With the use of the null-forgiving operator, you let the compiler know that passing `null` is expected and shouldn't be warned about.</span></span>

<span data-ttu-id="7ce5c-118">Ayrıca, bir ifadenin `null` olamaz, ancak derleyicinin bunu tanıması için yönetmediğini kesin bir şekilde öğrendiğinizde null-forverme işlecini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ce5c-118">You also can use the null-forgiving operator when you definitely know that an expression cannot be `null` but the compiler doesn't manage to recognize that.</span></span> <span data-ttu-id="7ce5c-119">Aşağıdaki örnekte, `IsValid` yöntemi `true` döndürürse, bağımsız değişkeni `null` ' dir ve güvenle başvuru yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7ce5c-119">In the following example, if the `IsValid` method returns `true`, its argument is not `null` and you can safely dereference it:</span></span>

[!code-csharp[Use null-forgiving operator](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#UseNullForgiving)]

<span data-ttu-id="7ce5c-120">Null-forverme işleci olmadan derleyici `p.Name` kodu için şu uyarıyı üretir: `Warning CS8602: Dereference of a possibly null reference.`.</span><span class="sxs-lookup"><span data-stu-id="7ce5c-120">Without the null-forgiving operator, the compiler generates the following warning for the `p.Name` code: `Warning CS8602: Dereference of a possibly null reference.`.</span></span>

<span data-ttu-id="7ce5c-121">@No__t-0 yöntemini değiştirebiliyorsanız, derleyicinin `IsValid` yönteminin bir bağımsız değişkeninin, yöntem `true` ' i döndürdüğünde `null` olmadığını bilmesini sağlamak için [Notnullıf](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) özniteliğini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7ce5c-121">If you can modify the `IsValid` method, you can use the [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) attribute to let the compiler know that an argument of the `IsValid` method cannot be `null` when the method returns `true`:</span></span>

[!code-csharp[Use an attribute](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#UseAttribute)]

<span data-ttu-id="7ce5c-122">Önceki örnekte, derleyicinin bu @no__t bulmak için yeterli bilgisi olduğundan, null-forverme işlecini kullanmanız gerekmez-0 ' ın `if` ifadesinde `null` olamaz.</span><span class="sxs-lookup"><span data-stu-id="7ce5c-122">In the preceding example, you don't need to use the null-forgiving operator because the compiler has enough information to find out that `p` cannot be `null` inside the `if` statement.</span></span> <span data-ttu-id="7ce5c-123">Bir değişkenin null durumu hakkında ek bilgi belirtmenize izin veren öznitelikler hakkında daha fazla bilgi için bkz. [null beklentilerini tanımlamak Için API 'leri özniteliklerle yükseltme](../../nullable-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="7ce5c-123">For more information about the attributes that allow you to specify additional information about the null state of a variable, see [Upgrade APIs with attributes to define null expectations](../../nullable-attributes.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7ce5c-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ce5c-124">See also</span></span>

- [<span data-ttu-id="7ce5c-125">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="7ce5c-125">C# reference</span></span>](../index.md)
- [<span data-ttu-id="7ce5c-126">C#işletmenlerinin</span><span class="sxs-lookup"><span data-stu-id="7ce5c-126">C# operators</span></span>](index.md)
- [<span data-ttu-id="7ce5c-127">Öğretici: null yapılabilir başvuru türleriyle tasarlayın</span><span class="sxs-lookup"><span data-stu-id="7ce5c-127">Tutorial: Design with nullable reference types</span></span>](../../tutorials/nullable-reference-types.md)
