---
title: WHERE (genel tür kısıtlaması)- C# başvuru
ms.custom: seodec18
ms.date: 04/12/2018
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.openlocfilehash: 4e51c5dd226533e7d1ce79a136dba19cbb252f92
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253909"
---
# <a name="where-generic-type-constraint-c-reference"></a><span data-ttu-id="77738-102">where (genel tür kısıtlaması) (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="77738-102">where (generic type constraint) (C# Reference)</span></span>

<span data-ttu-id="77738-103">Genel tanımda yer alan yantümce,genelbirtür,metot,temsilciveyayerelişlevdetürparametreleriiçinbağımsızdeğişkenolarakkullanılantürlerdekısıtlamalarbelirtir.`where`</span><span class="sxs-lookup"><span data-stu-id="77738-103">The `where` clause in a generic definition specifies constraints on the types that are used as arguments for type parameters in a generic type, method, delegate, or local function.</span></span> <span data-ttu-id="77738-104">Kısıtlamalar, arabirimler, temel sınıflar veya bir genel türün bir başvuru, değer veya yönetilmeyen tür olmasını gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="77738-104">Constraints can specify interfaces, base classes, or require a generic type to be a reference, value, or unmanaged type.</span></span> <span data-ttu-id="77738-105">Bunlar, tür bağımsız değişkeninin sahip olması gereken özellikleri bildirir.</span><span class="sxs-lookup"><span data-stu-id="77738-105">They declare capabilities that the type argument must possess.</span></span>

<span data-ttu-id="77738-106">Örneğin, tür parametresi `MyGenericClass` `T` <xref:System.IComparable%601> arabirimini uygulayan genel bir sınıf bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="77738-106">For example, you can declare a generic class, `MyGenericClass`, such that the type parameter `T` implements the <xref:System.IComparable%601> interface:</span></span>

[!code-csharp[using an interface constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#1)]

> [!NOTE]
> <span data-ttu-id="77738-107">Bir sorgu ifadesindeki WHERE yan tümcesi hakkında daha fazla bilgi için bkz. [WHERE yan tümcesi](where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="77738-107">For more information on the where clause in a query expression, see [where clause](where-clause.md).</span></span>

<span data-ttu-id="77738-108">`where` Yan tümce bir temel sınıf kısıtlaması de içerebilir.</span><span class="sxs-lookup"><span data-stu-id="77738-108">The `where` clause can also include a base class constraint.</span></span> <span data-ttu-id="77738-109">Temel sınıf kısıtlaması, bu genel türün tür bağımsız değişkeni olarak kullanılacak bir türün, bu genel tür için bir tür bağımsız değişkeni olarak kullanılacak bir temel sınıf (veya temel sınıf) olarak belirtilen sınıfa sahip olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="77738-109">The base class constraint states that a type to be used as a type argument for that generic type has the specified class as a base class (or is that base class) to be used as a type argument for that generic type.</span></span> <span data-ttu-id="77738-110">Temel sınıf kısıtlaması kullanılırsa, bu tür parametresindeki diğer kısıtlamaların önüne gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="77738-110">If the base class constraint is used, it must appear before any other constraints on that type parameter.</span></span> <span data-ttu-id="77738-111">Bir temel sınıf kısıtlaması olarak bazı türlere izin verilmez: <xref:System.Object>, <xref:System.Array>ve <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="77738-111">Some types are disallowed as a base class constraint: <xref:System.Object>, <xref:System.Array>, and <xref:System.ValueType>.</span></span> <span data-ttu-id="77738-112">C# 7,3, <xref:System.Enum>, <xref:System.Delegate>ve 'denöncetemelsınıfkısıtlamalarıolarakdaizinverilmedi.<xref:System.MulticastDelegate></span><span class="sxs-lookup"><span data-stu-id="77738-112">Prior to C# 7.3, <xref:System.Enum>, <xref:System.Delegate>, and <xref:System.MulticastDelegate> were also disallowed as base class constraints.</span></span> <span data-ttu-id="77738-113">Aşağıdaki örnek, artık temel sınıf olarak belirtime türleri göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="77738-113">The following example shows the types that can now be specified as a base class:</span></span>

[!code-csharp[using an interface constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#2)]

<span data-ttu-id="77738-114">Yan tümce türün bir `class` veya bir `struct`olduğunu belirtebilir. `where`</span><span class="sxs-lookup"><span data-stu-id="77738-114">The `where` clause can specify that the type is a `class` or a `struct`.</span></span> <span data-ttu-id="77738-115">Kısıtlama, öğesinin `System.ValueType`temel sınıf kısıtlamasını belirtme gereksinimini ortadan kaldırır. `struct`</span><span class="sxs-lookup"><span data-stu-id="77738-115">The `struct` constraint removes the need to specify a base class constraint of `System.ValueType`.</span></span> <span data-ttu-id="77738-116">Tür `System.ValueType` , temel sınıf kısıtlaması olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="77738-116">The `System.ValueType` type may not be used as a base class constraint.</span></span> <span data-ttu-id="77738-117">Aşağıdaki örnek, `class` ve `struct` kısıtlamalarını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="77738-117">The following example shows both the `class` and `struct` constraints:</span></span>

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#3)]

<span data-ttu-id="77738-118">Yan tümce `notnull` kısıtlaması içerebilir. `where`</span><span class="sxs-lookup"><span data-stu-id="77738-118">The `where` clause may include the `notnull` constraint.</span></span> <span data-ttu-id="77738-119">`notnull` Kısıtlama, tür parametresini null yapılamayan türler ile sınırlandırır.</span><span class="sxs-lookup"><span data-stu-id="77738-119">The `notnull` constraint limits the type parameter to non-nullable types.</span></span> <span data-ttu-id="77738-120">Bu tür bir [değer türü](struct.md) veya null yapılamayan bir başvuru türü olabilir.</span><span class="sxs-lookup"><span data-stu-id="77738-120">That type may be a [value type](struct.md) or a non-nullable reference type.</span></span> <span data-ttu-id="77738-121">Kısıtlama `notnull` , C# [ bir`nullable enable` bağlamda](../../nullable-references.md#nullable-contexts)derlenen kod için 8,0 'den başlayarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="77738-121">The `notnull` constraint is available starting in C# 8.0 for code compiled in a [`nullable enable` context](../../nullable-references.md#nullable-contexts).</span></span> <span data-ttu-id="77738-122">Diğer kısıtlamaların aksine, bir tür bağımsız değişkeni `notnull` kısıtlamayı ihlal ederse, derleyici hata yerine bir uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="77738-122">Unlike other constraints, if a type argument violates the `notnull` constraint, the compiler generates a warning instead of an error.</span></span> <span data-ttu-id="77738-123">Uyarılar yalnızca bir `nullable enable` bağlamda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="77738-123">Warnings are only generated in a `nullable enable` context.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="77738-124">`notnull` Kısıtlamayı içeren genel bildirimler, null yapılabilir bir zorunluluvou bağlamında kullanılabilir, ancak derleyici kısıtlamayı zorlamaz.</span><span class="sxs-lookup"><span data-stu-id="77738-124">Generic declarations that include the `notnull` constraint can be used in a nullable oblivious context, but compiler does not enforce the constraint.</span></span>

[!code-csharp[using the nonnull constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#NotNull)]

<span data-ttu-id="77738-125">Yan tümce de bir `unmanaged` kısıtlama içerebilir. `where`</span><span class="sxs-lookup"><span data-stu-id="77738-125">The `where` clause may also include an `unmanaged` constraint.</span></span> <span data-ttu-id="77738-126">Kısıtlama, tür parametresini [yönetilmeyen türler](../builtin-types/unmanaged-types.md)olarak bilinen türlerle sınırlandırır. `unmanaged`</span><span class="sxs-lookup"><span data-stu-id="77738-126">The `unmanaged` constraint limits the type parameter to types known as [unmanaged types](../builtin-types/unmanaged-types.md).</span></span> <span data-ttu-id="77738-127">Kısıtlama `unmanaged` , içinde C#alt düzey birlikte çalışma kodu yazmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="77738-127">The `unmanaged` constraint makes it easier to write low-level interop code in C#.</span></span> <span data-ttu-id="77738-128">Bu kısıtlama, tüm yönetilmeyen türler arasında yeniden kullanılabilir yordamlar sunar.</span><span class="sxs-lookup"><span data-stu-id="77738-128">This constraint enables reusable routines across all unmanaged types.</span></span> <span data-ttu-id="77738-129">Kısıtlama, `class` veya`struct` kısıtlaması ile birleştirilemez. `unmanaged`</span><span class="sxs-lookup"><span data-stu-id="77738-129">The `unmanaged` constraint can't be combined with the `class` or `struct` constraint.</span></span> <span data-ttu-id="77738-130">Kısıtlama, türün bir `struct`olması için şunu uygular: `unmanaged`</span><span class="sxs-lookup"><span data-stu-id="77738-130">The `unmanaged` constraint enforces that the type must be a `struct`:</span></span>

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#4)]

<span data-ttu-id="77738-131">Yan tümce bir Oluşturucu `new()`kısıtlaması de içerebilir. `where`</span><span class="sxs-lookup"><span data-stu-id="77738-131">The `where` clause may also include a constructor constraint, `new()`.</span></span> <span data-ttu-id="77738-132">Bu kısıtlama `new` işleci kullanarak bir tür parametresinin örneğini oluşturmayı mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="77738-132">That constraint makes it possible to create an instance of a type parameter using the `new` operator.</span></span> <span data-ttu-id="77738-133">[New () kısıtlaması](new-constraint.md) , derleyicinin sağlanan herhangi bir tür bağımsız değişkeninin erişilebilir bir parametresiz-veya varsayılan--oluşturucusu olması gerektiğini bilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="77738-133">The [new() Constraint](new-constraint.md) lets the compiler know that any type argument supplied must have an accessible parameterless--or default-- constructor.</span></span> <span data-ttu-id="77738-134">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="77738-134">For example:</span></span>

[!code-csharp[using the new constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#5)]

<span data-ttu-id="77738-135">`new()` Kısıtlama `where` yan tümcesinde en son görünür.</span><span class="sxs-lookup"><span data-stu-id="77738-135">The `new()` constraint appears last in the `where` clause.</span></span> <span data-ttu-id="77738-136">`new()` `struct` Kısıtlama veya`unmanaged` kısıtlamalarıyla birleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="77738-136">The `new()` constraint can't be combined with the `struct` or `unmanaged` constraints.</span></span> <span data-ttu-id="77738-137">Bu kısıtlamaların karşılankarşılayan tüm türlerin erişilebilir bir parametresiz oluşturucusu olması gerekir ve `new()` kısıtlama gereksiz hale getirir.</span><span class="sxs-lookup"><span data-stu-id="77738-137">All types satisfying those constraints must have an accessible parameterless constructor, making the `new()` constraint redundant.</span></span>

<span data-ttu-id="77738-138">Birden çok tür parametresiyle, her tür `where` parametresi için bir yan tümce kullanın, örneğin:</span><span class="sxs-lookup"><span data-stu-id="77738-138">With multiple type parameters, use one `where` clause for each type parameter, for example:</span></span>

[!code-csharp[using multiple where constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#6)]

<span data-ttu-id="77738-139">Ayrıca, aşağıdaki örnekte gösterildiği gibi genel yöntemlerin tür parametrelerine kısıtlamalar ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="77738-139">You can also attach constraints to type parameters of generic methods, as shown in the following example:</span></span>

[!code-csharp[where constraints with generic methods](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#7)]

<span data-ttu-id="77738-140">Temsilcilerle ilgili tür parametresi kısıtlamalarını betimleyen sözdiziminin, metodların türüyle aynı olduğunu unutmayın:</span><span class="sxs-lookup"><span data-stu-id="77738-140">Notice that the syntax to describe type parameter constraints on delegates is the same as that of methods:</span></span>

[!code-csharp[where constraints with generic methods](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#8)]

<span data-ttu-id="77738-141">Genel Temsilciler hakkında daha fazla bilgi için bkz. [Genel Temsilciler](../../programming-guide/generics/generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="77738-141">For information on generic delegates, see [Generic Delegates](../../programming-guide/generics/generic-delegates.md).</span></span>

<span data-ttu-id="77738-142">Kısıtlamaların sözdizimi ve kullanımı hakkında ayrıntılı bilgi için bkz. [tür parametrelerindeki kısıtlamalar](../../programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="77738-142">For details on the syntax and use of constraints, see [Constraints on Type Parameters](../../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="77738-143">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="77738-143">C# language specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="77738-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77738-144">See also</span></span>

- [<span data-ttu-id="77738-145">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="77738-145">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="77738-146">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="77738-146">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="77738-147">Genel Türlere Giriş</span><span class="sxs-lookup"><span data-stu-id="77738-147">Introduction to Generics</span></span>](../../programming-guide/generics/index.md)
- [<span data-ttu-id="77738-148">new Kısıtlaması</span><span class="sxs-lookup"><span data-stu-id="77738-148">new Constraint</span></span>](./new-constraint.md)
- [<span data-ttu-id="77738-149">Tür Parametrelerindeki Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="77738-149">Constraints on Type Parameters</span></span>](../../programming-guide/generics/constraints-on-type-parameters.md)
