---
title: WHERE (genel tür kısıtlaması)- C# başvuru
ms.custom: seodec18
ms.date: 04/12/2018
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.openlocfilehash: bccc22f5362b22540dadf08e6b21a07cbc578327
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433860"
---
# <a name="where-generic-type-constraint-c-reference"></a><span data-ttu-id="69c39-102">where (genel tür kısıtlaması) (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="69c39-102">where (generic type constraint) (C# Reference)</span></span>

<span data-ttu-id="69c39-103">Genel tanımda yer alan yantümce,genelbirtür,metot,temsilciveyayerelişlevdetürparametreleriiçinbağımsızdeğişkenolarakkullanılantürlerdekısıtlamalarbelirtir.`where`</span><span class="sxs-lookup"><span data-stu-id="69c39-103">The `where` clause in a generic definition specifies constraints on the types that are used as arguments for type parameters in a generic type, method, delegate, or local function.</span></span> <span data-ttu-id="69c39-104">Kısıtlamalar, arabirimler, temel sınıflar veya bir genel türün bir başvuru, değer veya yönetilmeyen tür olmasını gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="69c39-104">Constraints can specify interfaces, base classes, or require a generic type to be a reference, value or unmanaged type.</span></span> <span data-ttu-id="69c39-105">Bunlar, tür bağımsız değişkeninin sahip olması gereken özellikleri bildirir.</span><span class="sxs-lookup"><span data-stu-id="69c39-105">They declare capabilities that the type argument must possess.</span></span>

<span data-ttu-id="69c39-106">Örneğin, tür parametresi `MyGenericClass` `T` <xref:System.IComparable%601> arabirimini uygulayan genel bir sınıf bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="69c39-106">For example, you can declare a generic class, `MyGenericClass`, such that the type parameter `T` implements the <xref:System.IComparable%601> interface:</span></span>

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#1)]

> [!NOTE]
> <span data-ttu-id="69c39-107">Bir sorgu ifadesindeki WHERE yan tümcesi hakkında daha fazla bilgi için bkz. [WHERE yan tümcesi](where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="69c39-107">For more information on the where clause in a query expression, see [where clause](where-clause.md).</span></span>

<span data-ttu-id="69c39-108">`where` Yan tümce bir temel sınıf kısıtlaması de içerebilir.</span><span class="sxs-lookup"><span data-stu-id="69c39-108">The `where` clause can also include a base class constraint.</span></span> <span data-ttu-id="69c39-109">Temel sınıf kısıtlaması, bu genel türün tür bağımsız değişkeni olarak kullanılacak bir türün, bu genel tür için bir tür bağımsız değişkeni olarak kullanılacak bir temel sınıf (veya temel sınıf) olarak belirtilen sınıfa sahip olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="69c39-109">The base class constraint states that a type to be used as a type argument for that generic type has the specified class as a base class (or is that base class) to be used as a type argument for that generic type.</span></span> <span data-ttu-id="69c39-110">Temel sınıf kısıtlaması kullanılırsa, bu tür parametresindeki diğer kısıtlamaların önüne gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="69c39-110">If the base class constraint is used, it must appear before any other constraints on that type parameter.</span></span> <span data-ttu-id="69c39-111">Bir temel sınıf kısıtlaması olarak bazı türlere izin verilmez: <xref:System.Object>, <xref:System.Array>ve <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="69c39-111">Some types are disallowed as a base class constraint: <xref:System.Object>, <xref:System.Array>, and <xref:System.ValueType>.</span></span> <span data-ttu-id="69c39-112">C# 7,3, <xref:System.Enum>, <xref:System.Delegate>ve 'denöncetemelsınıfkısıtlamalarıolarakdaizinverilmedi.<xref:System.MulticastDelegate></span><span class="sxs-lookup"><span data-stu-id="69c39-112">Prior to C# 7.3, <xref:System.Enum>, <xref:System.Delegate>, and <xref:System.MulticastDelegate> were also disallowed as base class constraints.</span></span> <span data-ttu-id="69c39-113">Aşağıdaki örnek, artık temel sınıf olarak belirtime türleri göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="69c39-113">The following example shows the types that can now be specified as a base class:</span></span>

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#2)]

<span data-ttu-id="69c39-114">Yan tümce türün bir `class` veya bir `struct`olduğunu belirtebilir. `where`</span><span class="sxs-lookup"><span data-stu-id="69c39-114">The `where` clause can specify that the type is a `class` or a `struct`.</span></span> <span data-ttu-id="69c39-115">Kısıtlama, öğesinin `System.ValueType`temel sınıf kısıtlamasını belirtme gereksinimini ortadan kaldırır. `struct`</span><span class="sxs-lookup"><span data-stu-id="69c39-115">The `struct` constraint removes the need to specify a base class constraint of `System.ValueType`.</span></span> <span data-ttu-id="69c39-116">Tür `System.ValueType` , temel sınıf kısıtlaması olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="69c39-116">The `System.ValueType` type may not be used as a base class constraint.</span></span> <span data-ttu-id="69c39-117">Aşağıdaki örnek, `class` ve `struct` kısıtlamalarını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="69c39-117">The following example shows both the `class` and `struct` constraints:</span></span>

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#3)]

<span data-ttu-id="69c39-118">Yan tümce de bir `unmanaged` kısıtlama içerebilir. `where`</span><span class="sxs-lookup"><span data-stu-id="69c39-118">The `where` clause may also include an `unmanaged` constraint.</span></span> <span data-ttu-id="69c39-119">Kısıtlama, tür parametresini [yönetilmeyen türler](../builtin-types/unmanaged-types.md)olarak bilinen türlerle sınırlandırır. `unmanaged`</span><span class="sxs-lookup"><span data-stu-id="69c39-119">The `unmanaged` constraint limits the type parameter to types known as [unmanaged types](../builtin-types/unmanaged-types.md).</span></span> <span data-ttu-id="69c39-120">Kısıtlama `unmanaged` , içinde C#alt düzey birlikte çalışma kodu yazmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="69c39-120">The `unmanaged` constraint makes it easier to write low-level interop code in C#.</span></span> <span data-ttu-id="69c39-121">Bu kısıtlama, tüm yönetilmeyen türler arasında yeniden kullanılabilir yordamlar sunar.</span><span class="sxs-lookup"><span data-stu-id="69c39-121">This constraint enables reusable routines across all unmanaged types.</span></span> <span data-ttu-id="69c39-122">Kısıtlama, `class` veya`struct` kısıtlaması ile birleştirilemez. `unmanaged`</span><span class="sxs-lookup"><span data-stu-id="69c39-122">The `unmanaged` constraint can't be combined with the `class` or `struct` constraint.</span></span> <span data-ttu-id="69c39-123">Kısıtlama, türün bir `struct`olması için şunu uygular: `unmanaged`</span><span class="sxs-lookup"><span data-stu-id="69c39-123">The `unmanaged` constraint enforces that the type must be a `struct`:</span></span>

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#4)]

<span data-ttu-id="69c39-124">Yan tümce bir Oluşturucu `new()`kısıtlaması de içerebilir. `where`</span><span class="sxs-lookup"><span data-stu-id="69c39-124">The `where` clause may also include a constructor constraint, `new()`.</span></span> <span data-ttu-id="69c39-125">Bu kısıtlama `new` işleci kullanarak bir tür parametresinin örneğini oluşturmayı mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="69c39-125">That constraint makes it possible to create an instance of a type parameter using the `new` operator.</span></span> <span data-ttu-id="69c39-126">[New () kısıtlaması](new-constraint.md) , derleyicinin sağlanan herhangi bir tür bağımsız değişkeninin erişilebilir bir parametresiz-veya varsayılan--oluşturucusu olması gerektiğini bilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="69c39-126">The [new() Constraint](new-constraint.md) lets the compiler know that any type argument supplied must have an accessible parameterless--or default-- constructor.</span></span> <span data-ttu-id="69c39-127">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="69c39-127">For example:</span></span>

[!code-csharp[using the new constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#5)]

<span data-ttu-id="69c39-128">`new()` Kısıtlama `where` yan tümcesinde en son görünür.</span><span class="sxs-lookup"><span data-stu-id="69c39-128">The `new()` constraint appears last in the `where` clause.</span></span> <span data-ttu-id="69c39-129">`new()` `struct` Kısıtlama veya`unmanaged` kısıtlamalarıyla birleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="69c39-129">The `new()` constraint can't be combined with the `struct` or `unmanaged` constraints.</span></span> <span data-ttu-id="69c39-130">Bu kısıtlamaların karşılankarşılayan tüm türlerin erişilebilir bir parametresiz oluşturucusu olması gerekir ve `new()` kısıtlama gereksiz hale getirir.</span><span class="sxs-lookup"><span data-stu-id="69c39-130">All types satisfying those constraints must have an accessible parameterless constructor, making the `new()` constraint redundant.</span></span>

<span data-ttu-id="69c39-131">Birden çok tür parametresiyle, her tür `where` parametresi için bir yan tümce kullanın, örneğin:</span><span class="sxs-lookup"><span data-stu-id="69c39-131">With multiple type parameters, use one `where` clause for each type parameter, for example:</span></span>

[!code-csharp[using multiple where constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#6)]

<span data-ttu-id="69c39-132">Ayrıca, aşağıdaki örnekte gösterildiği gibi genel yöntemlerin tür parametrelerine kısıtlamalar ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="69c39-132">You can also attach constraints to type parameters of generic methods, as shown in the following example:</span></span>

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#7)]

<span data-ttu-id="69c39-133">Temsilcilerle ilgili tür parametresi kısıtlamalarını betimleyen sözdiziminin, metodların türüyle aynı olduğunu unutmayın:</span><span class="sxs-lookup"><span data-stu-id="69c39-133">Notice that the syntax to describe type parameter constraints on delegates is the same as that of methods:</span></span>

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#8)]

<span data-ttu-id="69c39-134">Genel Temsilciler hakkında daha fazla bilgi için bkz. [Genel Temsilciler](../../../csharp/programming-guide/generics/generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="69c39-134">For information on generic delegates, see [Generic Delegates](../../../csharp/programming-guide/generics/generic-delegates.md).</span></span>

<span data-ttu-id="69c39-135">Kısıtlamaların sözdizimi ve kullanımı hakkında ayrıntılı bilgi için bkz. [tür parametrelerindeki kısıtlamalar](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="69c39-135">For details on the syntax and use of constraints, see [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="69c39-136">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="69c39-136">C# language specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="69c39-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69c39-137">See also</span></span>

- [<span data-ttu-id="69c39-138">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="69c39-138">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="69c39-139">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="69c39-139">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="69c39-140">Genel Türlere Giriş</span><span class="sxs-lookup"><span data-stu-id="69c39-140">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
- [<span data-ttu-id="69c39-141">new Kısıtlaması</span><span class="sxs-lookup"><span data-stu-id="69c39-141">new Constraint</span></span>](../../../csharp/language-reference/keywords/new-constraint.md)
- [<span data-ttu-id="69c39-142">Tür Parametrelerindeki Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="69c39-142">Constraints on Type Parameters</span></span>](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)
