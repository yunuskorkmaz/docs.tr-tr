---
description: '! (null-forverme) işleci-C# başvurusu'
title: '! (null-forverme) işleci-C# başvurusu'
ms.date: 11/13/2020
f1_keywords:
- nullForgiving_CSharpKeyword
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: 14bc4501dfed515e162a6e30137c9def89bb3651
ms.sourcegitcommit: e16315d9f1ff355f55ff8ab84a28915be0a8e42b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105111081"
---
# <a name="-null-forgiving-operator-c-reference"></a><span data-ttu-id="83cd0-105">!</span><span class="sxs-lookup"><span data-stu-id="83cd0-105">!</span></span> <span data-ttu-id="83cd0-106">(null-forverme) işleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="83cd0-106">(null-forgiving) operator (C# reference)</span></span>

<span data-ttu-id="83cd0-107">C# 8,0 ve üzeri sürümlerde, birli sonek `!` operatörü null yasaklamaya veya null göstermeme, işleçtir.</span><span class="sxs-lookup"><span data-stu-id="83cd0-107">Available in C# 8.0 and later, the unary postfix `!` operator is the null-forgiving, or null-suppression, operator.</span></span> <span data-ttu-id="83cd0-108">Etkin bir [null yapılabilir ek açıklama bağlamında](../../nullable-references.md#nullable-annotation-context), bir başvuru türünün ifadesinin bu ifade olduğunu bildirmek için null-forverme işlecini kullanırsınız `x` `null` : `x!` .</span><span class="sxs-lookup"><span data-stu-id="83cd0-108">In an enabled [nullable annotation context](../../nullable-references.md#nullable-annotation-context), you use the null-forgiving operator to declare that expression `x` of a reference type isn't `null`: `x!`.</span></span> <span data-ttu-id="83cd0-109">Birli önek `!` işleci, [mantıksal değilleme işleçtir](boolean-logical-operators.md#logical-negation-operator-).</span><span class="sxs-lookup"><span data-stu-id="83cd0-109">The unary prefix `!` operator is the [logical negation operator](boolean-logical-operators.md#logical-negation-operator-).</span></span>

<span data-ttu-id="83cd0-110">Null-forverme işlecinin çalışma zamanında hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="83cd0-110">The null-forgiving operator has no effect at run time.</span></span> <span data-ttu-id="83cd0-111">Yalnızca ifadenin null durumunu değiştirerek derleyicinin statik akış analizini etkiler.</span><span class="sxs-lookup"><span data-stu-id="83cd0-111">It only affects the compiler's static flow analysis by changing the null state of the expression.</span></span> <span data-ttu-id="83cd0-112">Çalışma zamanında ifade, `x!` temel alınan ifadenin sonucu olarak değerlendirilir `x` .</span><span class="sxs-lookup"><span data-stu-id="83cd0-112">At run time, expression `x!` evaluates to the result of the underlying expression `x`.</span></span>

<span data-ttu-id="83cd0-113">Null yapılabilir başvuru türleri özelliği hakkında daha fazla bilgi için bkz. [Nullable başvuru türleri](../builtin-types/nullable-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="83cd0-113">For more information about the nullable reference types feature, see [Nullable reference types](../builtin-types/nullable-reference-types.md).</span></span>

## <a name="examples"></a><span data-ttu-id="83cd0-114">Örnekler</span><span class="sxs-lookup"><span data-stu-id="83cd0-114">Examples</span></span>

<span data-ttu-id="83cd0-115">Null-forverme işlecinin kullanım çalışmalarından biri bağımsız değişken doğrulama mantığını test ediyor.</span><span class="sxs-lookup"><span data-stu-id="83cd0-115">One of the use cases of the null-forgiving operator is in testing the argument validation logic.</span></span> <span data-ttu-id="83cd0-116">Örneğin, aşağıdaki sınıfı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="83cd0-116">For example, consider the following class:</span></span>

[!code-csharp[Person class](snippets/shared/NullForgivingOperator.cs#PersonClass)]

<span data-ttu-id="83cd0-117">[MSTest test çerçevesini](../../../core/testing/unit-testing-with-mstest.md)kullanarak, oluşturucuda doğrulama mantığı için aşağıdaki testi oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="83cd0-117">Using the [MSTest test framework](../../../core/testing/unit-testing-with-mstest.md), you can create the following test for the validation logic in the constructor:</span></span>

[!code-csharp[Person test](snippets/shared/NullForgivingOperator.cs#TestPerson)]

<span data-ttu-id="83cd0-118">Null-forverme işleci olmadan derleyici, önceki kod için aşağıdaki uyarıyı oluşturur: `Warning CS8625: Cannot convert null literal to non-nullable reference type` .</span><span class="sxs-lookup"><span data-stu-id="83cd0-118">Without the null-forgiving operator, the compiler generates the following warning for the preceding code: `Warning CS8625: Cannot convert null literal to non-nullable reference type`.</span></span> <span data-ttu-id="83cd0-119">Null-forverme işlecini kullanarak, derleyiciye iletme `null` beklendiğine ve hakkında uyarı olmaması gerektiğini bilgilendirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="83cd0-119">By using the null-forgiving operator, you inform the compiler that passing `null` is expected and shouldn't be warned about.</span></span>

<span data-ttu-id="83cd0-120">Ayrıca, bir ifadenin `null` olmadığını kesin olarak bildiğiniz ancak derleyici bunu tanımak için yönetmediğinden null-forverme işlecini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83cd0-120">You can also use the null-forgiving operator when you definitely know that an expression cannot be `null` but the compiler doesn't manage to recognize that.</span></span> <span data-ttu-id="83cd0-121">Aşağıdaki örnekte, `IsValid` yöntemi döndürürse `true` , bağımsız değişkeni değildir `null` ve güvenli bir şekilde başvurusu yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="83cd0-121">In the following example, if the `IsValid` method returns `true`, its argument is not `null` and you can safely dereference it:</span></span>

[!code-csharp[Use null-forgiving operator](snippets/shared/NullForgivingOperator.cs#UseNullForgiving)]

<span data-ttu-id="83cd0-122">Null-forverme işleci olmadan derleyici, kod için aşağıdaki uyarıyı oluşturur `p.Name` : `Warning CS8602: Dereference of a possibly null reference` .</span><span class="sxs-lookup"><span data-stu-id="83cd0-122">Without the null-forgiving operator, the compiler generates the following warning for the `p.Name` code: `Warning CS8602: Dereference of a possibly null reference`.</span></span>

<span data-ttu-id="83cd0-123">Yöntemi değiştirebiliyorsanız `IsValid` , derleyicinin yöntemin bir bağımsız değişkeninin yöntemin döndürdüğü zaman değiştiremediğini bildirmek Için [notnullıf](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) özniteliğini kullanabilirsiniz `IsValid` `null` `true` :</span><span class="sxs-lookup"><span data-stu-id="83cd0-123">If you can modify the `IsValid` method, you can use the [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) attribute to inform the compiler that an argument of the `IsValid` method cannot be `null` when the method returns `true`:</span></span>

[!code-csharp[Use an attribute](snippets/shared/NullForgivingOperator.cs#UseAttribute)]

<span data-ttu-id="83cd0-124">Önceki örnekte, derleyicinin, ifadenin içinde yer alamaz bilgi almak için yeterli bilgisi olduğundan, null-forverme işlecini kullanmanız gerekmez `p` `null` `if` .</span><span class="sxs-lookup"><span data-stu-id="83cd0-124">In the preceding example, you don't need to use the null-forgiving operator because the compiler has enough information to find out that `p` cannot be `null` inside the `if` statement.</span></span> <span data-ttu-id="83cd0-125">Bir değişkenin null durumu hakkında ek bilgi sağlamanıza olanak tanıyan öznitelikler hakkında daha fazla bilgi için bkz. [null beklentilerini tanımlamak Için API 'leri özniteliklerle yükseltme](../attributes/nullable-analysis.md).</span><span class="sxs-lookup"><span data-stu-id="83cd0-125">For more information about the attributes that allow you to provide additional information about the null state of a variable, see [Upgrade APIs with attributes to define null expectations](../attributes/nullable-analysis.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="83cd0-126">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="83cd0-126">C# language specification</span></span>

<span data-ttu-id="83cd0-127">Daha fazla bilgi için, [Nullable başvuru türleri belirtiminin taslağının](~/_csharplang/proposals/csharp-9.0/nullable-reference-types-specification.md) [null-forverme işleci](~/_csharplang/proposals/csharp-9.0/nullable-reference-types-specification.md#the-null-forgiving-operator) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="83cd0-127">For more information, see [The null-forgiving operator](~/_csharplang/proposals/csharp-9.0/nullable-reference-types-specification.md#the-null-forgiving-operator) section of the [draft of the nullable reference types specification](~/_csharplang/proposals/csharp-9.0/nullable-reference-types-specification.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="83cd0-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="83cd0-128">See also</span></span>

- [<span data-ttu-id="83cd0-129">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="83cd0-129">C# reference</span></span>](../index.md)
- [<span data-ttu-id="83cd0-130">C# işleçleri ve ifadeleri</span><span class="sxs-lookup"><span data-stu-id="83cd0-130">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="83cd0-131">Öğretici: null yapılabilir başvuru türleriyle tasarlayın</span><span class="sxs-lookup"><span data-stu-id="83cd0-131">Tutorial: Design with nullable reference types</span></span>](../../whats-new/tutorials/nullable-reference-types.md)
