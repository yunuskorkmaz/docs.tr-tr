---
title: '! (null-forverme) işleci-C# başvurusu'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: 772f37f1fc7446eae66f0cd0f12adb5e2e41997d
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595955"
---
# <a name="-null-forgiving-operator-c-reference"></a><span data-ttu-id="99759-103">!</span><span class="sxs-lookup"><span data-stu-id="99759-103">!</span></span> <span data-ttu-id="99759-104">(null-forverme) işleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="99759-104">(null-forgiving) operator (C# reference)</span></span>

<span data-ttu-id="99759-105">C# 8,0 ve üzeri sürümlerde, birli sonek `!` operatörü null-forverme işleçtir.</span><span class="sxs-lookup"><span data-stu-id="99759-105">Available in C# 8.0 and later, the unary postfix `!` operator is the null-forgiving operator.</span></span> <span data-ttu-id="99759-106">Etkin bir [null yapılabilir ek açıklama bağlamında](../../nullable-references.md#nullable-annotation-context), bir başvuru türünün ifadesinin bu ifade `x` olduğunu bildirmek için null-forverme işlecini kullanırsınız `null`:. `x!`</span><span class="sxs-lookup"><span data-stu-id="99759-106">In an enabled [nullable annotation context](../../nullable-references.md#nullable-annotation-context), you use the null-forgiving operator to declare that expression `x` of a reference type isn't `null`: `x!`.</span></span> <span data-ttu-id="99759-107">Birli önek `!` işleci, [mantıksal değilleme işleçtir](boolean-logical-operators.md#logical-negation-operator-).</span><span class="sxs-lookup"><span data-stu-id="99759-107">The unary prefix `!` operator is the [logical negation operator](boolean-logical-operators.md#logical-negation-operator-).</span></span>

<span data-ttu-id="99759-108">Null-forverme işlecinin çalışma zamanında hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="99759-108">The null-forgiving operator has no effect at run time.</span></span> <span data-ttu-id="99759-109">Yalnızca ifadenin null durumunu değiştirerek derleyicinin statik akış analizini etkiler.</span><span class="sxs-lookup"><span data-stu-id="99759-109">It only affects the compiler's static flow analysis by changing the null state of the expression.</span></span> <span data-ttu-id="99759-110">Çalışma zamanında ifade `x!` , temel alınan ifadenin `x`sonucu olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="99759-110">At run time, expression `x!` evaluates to the result of the underlying expression `x`.</span></span>

> [!NOTE]
> <span data-ttu-id="99759-111">C# 8 ' de null-forverme işleci, [null koşullu işleçlerle](member-access-operators.md#null-conditional-operators--and-) beklenmedik şekilde etkileşime girer.</span><span class="sxs-lookup"><span data-stu-id="99759-111">In C# 8 the null-forgiving operator interacts with the [null-conditional operators](member-access-operators.md#null-conditional-operators--and-) in an unexpected way.</span></span> <span data-ttu-id="99759-112">İfade `x?.y!.z` olarak `(x?.y)!.z`ayrıştırılır.</span><span class="sxs-lookup"><span data-stu-id="99759-112">The expression `x?.y!.z` is parsed as `(x?.y)!.z`.</span></span> <span data-ttu-id="99759-113">Bu yorum `z` nedeniyle `x` , `null`olsa bile değerlendirilir, bu da bir <xref:System.NullReferenceException>ile sonuçlanabilir.</span><span class="sxs-lookup"><span data-stu-id="99759-113">Due to this interpretation `z` is evaluated even if `x` is `null`, which may result in a <xref:System.NullReferenceException>.</span></span>

<span data-ttu-id="99759-114">Null yapılabilir başvuru türleri özelliği hakkında daha fazla bilgi için bkz. [Nullable başvuru türleri](../builtin-types/nullable-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="99759-114">For more information about the nullable reference types feature, see [Nullable reference types](../builtin-types/nullable-reference-types.md).</span></span>

## <a name="examples"></a><span data-ttu-id="99759-115">Örnekler</span><span class="sxs-lookup"><span data-stu-id="99759-115">Examples</span></span>

<span data-ttu-id="99759-116">Null-forverme işlecinin kullanım çalışmalarından biri bağımsız değişken doğrulama mantığını test ediyor.</span><span class="sxs-lookup"><span data-stu-id="99759-116">One of the use cases of the null-forgiving operator is in testing the argument validation logic.</span></span> <span data-ttu-id="99759-117">Örneğin, aşağıdaki sınıfı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="99759-117">For example, consider the following class:</span></span>

[!code-csharp[Person class](snippets/NullForgivingOperator.cs#PersonClass)]

<span data-ttu-id="99759-118">[MSTest test çerçevesini](../../../core/testing/unit-testing-with-mstest.md)kullanarak, oluşturucuda doğrulama mantığı için aşağıdaki testi oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="99759-118">Using the [MSTest test framework](../../../core/testing/unit-testing-with-mstest.md), you can create the following test for the validation logic in the constructor:</span></span>

[!code-csharp[Person test](snippets/NullForgivingOperator.cs#TestPerson)]

<span data-ttu-id="99759-119">Null-forverme işleci olmadan derleyici, önceki kod için aşağıdaki uyarıyı oluşturur: `Warning CS8625: Cannot convert null literal to non-nullable reference type`.</span><span class="sxs-lookup"><span data-stu-id="99759-119">Without the null-forgiving operator, the compiler generates the following warning for the preceding code: `Warning CS8625: Cannot convert null literal to non-nullable reference type`.</span></span> <span data-ttu-id="99759-120">Null-forverme işlecini kullanarak, derleyiciye iletme `null` beklendiğine ve hakkında uyarı olmaması gerektiğini bilgilendirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="99759-120">By using the null-forgiving operator, you inform the compiler that passing `null` is expected and shouldn't be warned about.</span></span>

<span data-ttu-id="99759-121">Ayrıca, bir ifadenin olmadığını kesin olarak bildiğiniz `null` ancak derleyici bunu tanımak için yönetmediğinden null-forverme işlecini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99759-121">You can also use the null-forgiving operator when you definitely know that an expression cannot be `null` but the compiler doesn't manage to recognize that.</span></span> <span data-ttu-id="99759-122">Aşağıdaki örnekte, `IsValid` yöntemi döndürürse `true`, bağımsız değişkeni değildir `null` ve güvenli bir şekilde başvurusu yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="99759-122">In the following example, if the `IsValid` method returns `true`, its argument is not `null` and you can safely dereference it:</span></span>

[!code-csharp[Use null-forgiving operator](snippets/NullForgivingOperator.cs#UseNullForgiving)]

<span data-ttu-id="99759-123">Null-forverme işleci olmadan derleyici, `p.Name` kod için aşağıdaki uyarıyı oluşturur:. `Warning CS8602: Dereference of a possibly null reference`</span><span class="sxs-lookup"><span data-stu-id="99759-123">Without the null-forgiving operator, the compiler generates the following warning for the `p.Name` code: `Warning CS8602: Dereference of a possibly null reference`.</span></span>

<span data-ttu-id="99759-124">`IsValid` Yöntemi değiştirebiliyorsanız, derleyicinin yöntemin bir bağımsız değişkeninin `IsValid` yöntemin döndürdüğü `null` `true`zaman değiştiremediğini bildirmek için [notnullıf](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) özniteliğini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="99759-124">If you can modify the `IsValid` method, you can use the [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) attribute to inform the compiler that an argument of the `IsValid` method cannot be `null` when the method returns `true`:</span></span>

[!code-csharp[Use an attribute](snippets/NullForgivingOperator.cs#UseAttribute)]

<span data-ttu-id="99759-125">Önceki örnekte, derleyicinin, `p` `null` `if` ifadenin içinde yer alamaz bilgi almak için yeterli bilgisi olduğundan, null-forverme işlecini kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="99759-125">In the preceding example, you don't need to use the null-forgiving operator because the compiler has enough information to find out that `p` cannot be `null` inside the `if` statement.</span></span> <span data-ttu-id="99759-126">Bir değişkenin null durumu hakkında ek bilgi sağlamanıza olanak tanıyan öznitelikler hakkında daha fazla bilgi için bkz. [null beklentilerini tanımlamak Için API 'leri özniteliklerle yükseltme](../attributes/nullable-analysis.md).</span><span class="sxs-lookup"><span data-stu-id="99759-126">For more information about the attributes that allow you to provide additional information about the null state of a variable, see [Upgrade APIs with attributes to define null expectations](../attributes/nullable-analysis.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="99759-127">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="99759-127">C# language specification</span></span>

<span data-ttu-id="99759-128">Daha fazla bilgi için, [Nullable başvuru türleri belirtiminin taslağının](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md) [null-forverme işleci](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="99759-128">For more information, see [The null-forgiving operator](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) section of the [draft of the nullable reference types specification](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="99759-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99759-129">See also</span></span>

- [<span data-ttu-id="99759-130">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="99759-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="99759-131">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="99759-131">C# operators</span></span>](index.md)
- [<span data-ttu-id="99759-132">Öğretici: null yapılabilir başvuru türleriyle tasarlayın</span><span class="sxs-lookup"><span data-stu-id="99759-132">Tutorial: Design with nullable reference types</span></span>](../../tutorials/nullable-reference-types.md)
