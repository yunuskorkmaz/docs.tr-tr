---
title: '! (null-affgiving) operatörü - C# referans'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: a8b47e83ce9e999ea2afe94db0a21725abc2d327
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738564"
---
# <a name="-null-forgiving-operator-c-reference"></a><span data-ttu-id="21e84-103">!</span><span class="sxs-lookup"><span data-stu-id="21e84-103">!</span></span> <span data-ttu-id="21e84-104">(null-affgiving) işleci (C# referans)</span><span class="sxs-lookup"><span data-stu-id="21e84-104">(null-forgiving) operator (C# reference)</span></span>

<span data-ttu-id="21e84-105">C# 8.0 ve daha sonra mevcuttur, `!` unary postfix işleci null-affgiving işlecidir.</span><span class="sxs-lookup"><span data-stu-id="21e84-105">Available in C# 8.0 and later, the unary postfix `!` operator is the null-forgiving operator.</span></span> <span data-ttu-id="21e84-106">Etkin [bir geçersiz ek açıklama bağlamında,](../../nullable-references.md#nullable-annotation-context)bir başvuru türünün ifadesinin `x` şu olmadığını `null`bildirmek için `x!`null-affgiving işleci kullanırsınız: .</span><span class="sxs-lookup"><span data-stu-id="21e84-106">In an enabled [nullable annotation context](../../nullable-references.md#nullable-annotation-context), you use the null-forgiving operator to declare that expression `x` of a reference type isn't `null`: `x!`.</span></span> <span data-ttu-id="21e84-107">Unary önek `!` işleci [mantıksal olumsuzlama işlecidir.](boolean-logical-operators.md#logical-negation-operator-)</span><span class="sxs-lookup"><span data-stu-id="21e84-107">The unary prefix `!` operator is the [logical negation operator](boolean-logical-operators.md#logical-negation-operator-).</span></span>

<span data-ttu-id="21e84-108">Null-affgiving işleci çalışma zamanında hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="21e84-108">The null-forgiving operator has no effect at run time.</span></span> <span data-ttu-id="21e84-109">Yalnızca ifadenin null durumunu değiştirerek derleyicinin statik akış çözümlemesi etkiler.</span><span class="sxs-lookup"><span data-stu-id="21e84-109">It only affects the compiler's static flow analysis by changing the null state of the expression.</span></span> <span data-ttu-id="21e84-110">Çalışma zamanında, `x!` ifade altta yatan ifadenin `x`sonucunu değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="21e84-110">At run time, expression `x!` evaluates to the result of the underlying expression `x`.</span></span>

<span data-ttu-id="21e84-111">Nullable başvuru türleri özelliği hakkında daha fazla bilgi için, [Nullable başvuru türleri](../builtin-types/nullable-reference-types.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="21e84-111">For more information about the nullable reference types feature, see [Nullable reference types](../builtin-types/nullable-reference-types.md).</span></span>

## <a name="examples"></a><span data-ttu-id="21e84-112">Örnekler</span><span class="sxs-lookup"><span data-stu-id="21e84-112">Examples</span></span>

<span data-ttu-id="21e84-113">Null-affgiving işlecinin kullanım durumlardan biri bağımsız değişken doğrulama mantığını test etmektir.</span><span class="sxs-lookup"><span data-stu-id="21e84-113">One of the use cases of the null-forgiving operator is in testing the argument validation logic.</span></span> <span data-ttu-id="21e84-114">Örneğin, aşağıdaki sınıfı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="21e84-114">For example, consider the following class:</span></span>

[!code-csharp[Person class](snippets/NullForgivingOperator.cs#PersonClass)]

<span data-ttu-id="21e84-115">[MSTest test çerçevesini](../../../core/testing/unit-testing-with-mstest.md)kullanarak, oluşturucudaki doğrulama mantığı için aşağıdaki testi oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="21e84-115">Using the [MSTest test framework](../../../core/testing/unit-testing-with-mstest.md), you can create the following test for the validation logic in the constructor:</span></span>

[!code-csharp[Person test](snippets/NullForgivingOperator.cs#TestPerson)]

<span data-ttu-id="21e84-116">Null-affgiving işleci olmadan, derleyici önceki kod için aşağıdaki `Warning CS8625: Cannot convert null literal to non-nullable reference type`uyarıyı oluşturur: .</span><span class="sxs-lookup"><span data-stu-id="21e84-116">Without the null-forgiving operator, the compiler generates the following warning for the preceding code: `Warning CS8625: Cannot convert null literal to non-nullable reference type`.</span></span> <span data-ttu-id="21e84-117">Null-affgiving işleci kullanarak, derlemeye geçişin `null` beklendiğini ve bu konuda uyarılmaması gerektiğini bildirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21e84-117">By using the null-forgiving operator, you inform the compiler that passing `null` is expected and shouldn't be warned about.</span></span>

<span data-ttu-id="21e84-118">Bir ifadenin olamayacağını `null` ancak derleyicinin bunu fark edemediğini kesinlikle bildiğinizde, hükümsüz affedici işleci de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21e84-118">You can also use the null-forgiving operator when you definitely know that an expression cannot be `null` but the compiler doesn't manage to recognize that.</span></span> <span data-ttu-id="21e84-119">Aşağıdaki örnekte, `IsValid` yöntem dönerse, `true`bağımsız değişkeni değil `null` ve güvenli bir şekilde dereference olabilir:</span><span class="sxs-lookup"><span data-stu-id="21e84-119">In the following example, if the `IsValid` method returns `true`, its argument is not `null` and you can safely dereference it:</span></span>

[!code-csharp[Use null-forgiving operator](snippets/NullForgivingOperator.cs#UseNullForgiving)]

<span data-ttu-id="21e84-120">Null-affgiving işleci olmadan, derleyici `p.Name` kod için aşağıdaki `Warning CS8602: Dereference of a possibly null reference`uyarıyı oluşturur: .</span><span class="sxs-lookup"><span data-stu-id="21e84-120">Without the null-forgiving operator, the compiler generates the following warning for the `p.Name` code: `Warning CS8602: Dereference of a possibly null reference`.</span></span>

<span data-ttu-id="21e84-121">`IsValid` Yöntemi değiştirebilirseniz, derleyiciye `IsValid` yöntemin bir bağımsız değişkeninin yöntem döndürdüğünde `null` `true`olamayacağını bildirmek için [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) özniteliğini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="21e84-121">If you can modify the `IsValid` method, you can use the [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) attribute to inform the compiler that an argument of the `IsValid` method cannot be `null` when the method returns `true`:</span></span>

[!code-csharp[Use an attribute](snippets/NullForgivingOperator.cs#UseAttribute)]

<span data-ttu-id="21e84-122">Önceki örnekte, `p` `null` `if` derleyicideyimin içinde olamayacağını öğrenmek için yeterli bilgiye sahip olduğundan, geçersiz affedici işleci kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="21e84-122">In the preceding example, you don't need to use the null-forgiving operator because the compiler has enough information to find out that `p` cannot be `null` inside the `if` statement.</span></span> <span data-ttu-id="21e84-123">Bir değişkenin null durumu hakkında ek bilgi sağlamanıza olanak tanıyan öznitelikler hakkında daha fazla bilgi için, [null beklentilerini tanımlamak için öznitelikleri içeren Yükseltme API'lerine](../../nullable-attributes.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="21e84-123">For more information about the attributes that allow you to provide additional information about the null state of a variable, see [Upgrade APIs with attributes to define null expectations](../../nullable-attributes.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="21e84-124">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="21e84-124">C# language specification</span></span>

<span data-ttu-id="21e84-125">Daha fazla bilgi için, [nullable başvuru türleri belirtimi taslağının](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md) [null-affgiving işleç](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="21e84-125">For more information, see [The null-forgiving operator](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) section of the [draft of the nullable reference types specification](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="21e84-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21e84-126">See also</span></span>

- [<span data-ttu-id="21e84-127">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="21e84-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="21e84-128">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="21e84-128">C# operators</span></span>](index.md)
- [<span data-ttu-id="21e84-129">Öğretici: Nullable başvuru türleri ile tasarım</span><span class="sxs-lookup"><span data-stu-id="21e84-129">Tutorial: Design with nullable reference types</span></span>](../../tutorials/nullable-reference-types.md)
