---
description: '! (null-forverme) işleci-C# başvurusu'
title: '! (null-forverme) işleci-C# başvurusu'
ms.date: 10/11/2019
f1_keywords:
- nullForgiving_CSharpKeyword
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: f2eb57bba462d471a041c17024fa7031c2c7f87d
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830590"
---
# <a name="-null-forgiving-operator-c-reference"></a><span data-ttu-id="f9bdf-105">!</span><span class="sxs-lookup"><span data-stu-id="f9bdf-105">!</span></span> <span data-ttu-id="f9bdf-106">(null-forverme) işleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f9bdf-106">(null-forgiving) operator (C# reference)</span></span>

<span data-ttu-id="f9bdf-107">C# 8,0 ve üzeri sürümlerde, birli sonek `!` operatörü null-forverme işleçtir.</span><span class="sxs-lookup"><span data-stu-id="f9bdf-107">Available in C# 8.0 and later, the unary postfix `!` operator is the null-forgiving operator.</span></span> <span data-ttu-id="f9bdf-108">Etkin bir [null yapılabilir ek açıklama bağlamında](../../nullable-references.md#nullable-annotation-context), bir başvuru türünün ifadesinin bu ifade olduğunu bildirmek için null-forverme işlecini kullanırsınız `x` `null` : `x!` .</span><span class="sxs-lookup"><span data-stu-id="f9bdf-108">In an enabled [nullable annotation context](../../nullable-references.md#nullable-annotation-context), you use the null-forgiving operator to declare that expression `x` of a reference type isn't `null`: `x!`.</span></span> <span data-ttu-id="f9bdf-109">Birli önek `!` işleci, [mantıksal değilleme işleçtir](boolean-logical-operators.md#logical-negation-operator-).</span><span class="sxs-lookup"><span data-stu-id="f9bdf-109">The unary prefix `!` operator is the [logical negation operator](boolean-logical-operators.md#logical-negation-operator-).</span></span>

<span data-ttu-id="f9bdf-110">Null-forverme işlecinin çalışma zamanında hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="f9bdf-110">The null-forgiving operator has no effect at run time.</span></span> <span data-ttu-id="f9bdf-111">Yalnızca ifadenin null durumunu değiştirerek derleyicinin statik akış analizini etkiler.</span><span class="sxs-lookup"><span data-stu-id="f9bdf-111">It only affects the compiler's static flow analysis by changing the null state of the expression.</span></span> <span data-ttu-id="f9bdf-112">Çalışma zamanında ifade, `x!` temel alınan ifadenin sonucu olarak değerlendirilir `x` .</span><span class="sxs-lookup"><span data-stu-id="f9bdf-112">At run time, expression `x!` evaluates to the result of the underlying expression `x`.</span></span>

> [!NOTE]
> <span data-ttu-id="f9bdf-113">C# 8 ' de, null-forverme işleci önceki [null koşullu](member-access-operators.md#null-conditional-operators--and-) işlemlerin listesini sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="f9bdf-113">In C# 8, the null-forgiving operator terminates the list of preceding [null-conditional](member-access-operators.md#null-conditional-operators--and-) operations.</span></span> <span data-ttu-id="f9bdf-114">Örneğin, ifadesi `x?.y!.z` olarak ayrıştırılır `(x?.y)!.z` .</span><span class="sxs-lookup"><span data-stu-id="f9bdf-114">For example, the expression `x?.y!.z` is parsed as `(x?.y)!.z`.</span></span> <span data-ttu-id="f9bdf-115">Bu yorum nedeniyle,, `z` olsa bile değerlendirilir, bu da `x` `null` bir ile sonuçlanabilir <xref:System.NullReferenceException> .</span><span class="sxs-lookup"><span data-stu-id="f9bdf-115">Due to this interpretation, `z` is evaluated even if `x` is `null`, which may result in a <xref:System.NullReferenceException>.</span></span>

<span data-ttu-id="f9bdf-116">Null yapılabilir başvuru türleri özelliği hakkında daha fazla bilgi için bkz. [Nullable başvuru türleri](../builtin-types/nullable-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="f9bdf-116">For more information about the nullable reference types feature, see [Nullable reference types](../builtin-types/nullable-reference-types.md).</span></span>

## <a name="examples"></a><span data-ttu-id="f9bdf-117">Örnekler</span><span class="sxs-lookup"><span data-stu-id="f9bdf-117">Examples</span></span>

<span data-ttu-id="f9bdf-118">Null-forverme işlecinin kullanım çalışmalarından biri bağımsız değişken doğrulama mantığını test ediyor.</span><span class="sxs-lookup"><span data-stu-id="f9bdf-118">One of the use cases of the null-forgiving operator is in testing the argument validation logic.</span></span> <span data-ttu-id="f9bdf-119">Örneğin, aşağıdaki sınıfı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="f9bdf-119">For example, consider the following class:</span></span>

[!code-csharp[Person class](snippets/shared/NullForgivingOperator.cs#PersonClass)]

<span data-ttu-id="f9bdf-120">[MSTest test çerçevesini](../../../core/testing/unit-testing-with-mstest.md)kullanarak, oluşturucuda doğrulama mantığı için aşağıdaki testi oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f9bdf-120">Using the [MSTest test framework](../../../core/testing/unit-testing-with-mstest.md), you can create the following test for the validation logic in the constructor:</span></span>

[!code-csharp[Person test](snippets/shared/NullForgivingOperator.cs#TestPerson)]

<span data-ttu-id="f9bdf-121">Null-forverme işleci olmadan derleyici, önceki kod için aşağıdaki uyarıyı oluşturur: `Warning CS8625: Cannot convert null literal to non-nullable reference type` .</span><span class="sxs-lookup"><span data-stu-id="f9bdf-121">Without the null-forgiving operator, the compiler generates the following warning for the preceding code: `Warning CS8625: Cannot convert null literal to non-nullable reference type`.</span></span> <span data-ttu-id="f9bdf-122">Null-forverme işlecini kullanarak, derleyiciye iletme `null` beklendiğine ve hakkında uyarı olmaması gerektiğini bilgilendirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="f9bdf-122">By using the null-forgiving operator, you inform the compiler that passing `null` is expected and shouldn't be warned about.</span></span>

<span data-ttu-id="f9bdf-123">Ayrıca, bir ifadenin `null` olmadığını kesin olarak bildiğiniz ancak derleyici bunu tanımak için yönetmediğinden null-forverme işlecini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f9bdf-123">You can also use the null-forgiving operator when you definitely know that an expression cannot be `null` but the compiler doesn't manage to recognize that.</span></span> <span data-ttu-id="f9bdf-124">Aşağıdaki örnekte, `IsValid` yöntemi döndürürse `true` , bağımsız değişkeni değildir `null` ve güvenli bir şekilde başvurusu yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f9bdf-124">In the following example, if the `IsValid` method returns `true`, its argument is not `null` and you can safely dereference it:</span></span>

[!code-csharp[Use null-forgiving operator](snippets/shared/NullForgivingOperator.cs#UseNullForgiving)]

<span data-ttu-id="f9bdf-125">Null-forverme işleci olmadan derleyici, kod için aşağıdaki uyarıyı oluşturur `p.Name` : `Warning CS8602: Dereference of a possibly null reference` .</span><span class="sxs-lookup"><span data-stu-id="f9bdf-125">Without the null-forgiving operator, the compiler generates the following warning for the `p.Name` code: `Warning CS8602: Dereference of a possibly null reference`.</span></span>

<span data-ttu-id="f9bdf-126">Yöntemi değiştirebiliyorsanız `IsValid` , derleyicinin yöntemin bir bağımsız değişkeninin yöntemin döndürdüğü zaman değiştiremediğini bildirmek Için [notnullıf](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) özniteliğini kullanabilirsiniz `IsValid` `null` `true` :</span><span class="sxs-lookup"><span data-stu-id="f9bdf-126">If you can modify the `IsValid` method, you can use the [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) attribute to inform the compiler that an argument of the `IsValid` method cannot be `null` when the method returns `true`:</span></span>

[!code-csharp[Use an attribute](snippets/shared/NullForgivingOperator.cs#UseAttribute)]

<span data-ttu-id="f9bdf-127">Önceki örnekte, derleyicinin, ifadenin içinde yer alamaz bilgi almak için yeterli bilgisi olduğundan, null-forverme işlecini kullanmanız gerekmez `p` `null` `if` .</span><span class="sxs-lookup"><span data-stu-id="f9bdf-127">In the preceding example, you don't need to use the null-forgiving operator because the compiler has enough information to find out that `p` cannot be `null` inside the `if` statement.</span></span> <span data-ttu-id="f9bdf-128">Bir değişkenin null durumu hakkında ek bilgi sağlamanıza olanak tanıyan öznitelikler hakkında daha fazla bilgi için bkz. [null beklentilerini tanımlamak Için API 'leri özniteliklerle yükseltme](../attributes/nullable-analysis.md).</span><span class="sxs-lookup"><span data-stu-id="f9bdf-128">For more information about the attributes that allow you to provide additional information about the null state of a variable, see [Upgrade APIs with attributes to define null expectations](../attributes/nullable-analysis.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f9bdf-129">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="f9bdf-129">C# language specification</span></span>

<span data-ttu-id="f9bdf-130">Daha fazla bilgi için, [Nullable başvuru türleri belirtiminin taslağının](~/_csharplang/proposals/csharp-9.0/nullable-reference-types-specification.md) [null-forverme işleci](~/_csharplang/proposals/csharp-9.0/nullable-reference-types-specification.md#the-null-forgiving-operator) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="f9bdf-130">For more information, see [The null-forgiving operator](~/_csharplang/proposals/csharp-9.0/nullable-reference-types-specification.md#the-null-forgiving-operator) section of the [draft of the nullable reference types specification](~/_csharplang/proposals/csharp-9.0/nullable-reference-types-specification.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f9bdf-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9bdf-131">See also</span></span>

- [<span data-ttu-id="f9bdf-132">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="f9bdf-132">C# reference</span></span>](../index.md)
- [<span data-ttu-id="f9bdf-133">C# işleçleri ve ifadeleri</span><span class="sxs-lookup"><span data-stu-id="f9bdf-133">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="f9bdf-134">Öğretici: null yapılabilir başvuru türleriyle tasarlayın</span><span class="sxs-lookup"><span data-stu-id="f9bdf-134">Tutorial: Design with nullable reference types</span></span>](../../tutorials/nullable-reference-types.md)
