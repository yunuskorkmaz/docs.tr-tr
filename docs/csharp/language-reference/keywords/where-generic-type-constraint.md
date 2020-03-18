---
title: where (genel tür kısıtlaması) - C# Reference
ms.date: 04/12/2018
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.openlocfilehash: d236420c5019f7529b729155b13df50807dc1dab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77626717"
---
# <a name="where-generic-type-constraint-c-reference"></a><span data-ttu-id="a6766-102">where (genel tür kısıtlaması) (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="a6766-102">where (generic type constraint) (C# Reference)</span></span>

<span data-ttu-id="a6766-103">Genel `where` bir tanımdaki yan tümce, genel bir tür, yöntem, temsilci veya yerel işlevdeki tür parametreleri için bağımsız değişken olarak kullanılan türler üzerindeki kısıtlamaları belirtir.</span><span class="sxs-lookup"><span data-stu-id="a6766-103">The `where` clause in a generic definition specifies constraints on the types that are used as arguments for type parameters in a generic type, method, delegate, or local function.</span></span> <span data-ttu-id="a6766-104">Kısıtlamalar arabirimleri, temel sınıfları belirtebilir veya başvuru, değer veya yönetilmeyen tür olması için genel bir tür gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="a6766-104">Constraints can specify interfaces, base classes, or require a generic type to be a reference, value, or unmanaged type.</span></span> <span data-ttu-id="a6766-105">Tür bağımsız değişkeninin sahip olması gereken yetenekleri bildirirler.</span><span class="sxs-lookup"><span data-stu-id="a6766-105">They declare capabilities that the type argument must possess.</span></span>

<span data-ttu-id="a6766-106">Örneğin, tür parametresi `MyGenericClass` `T` <xref:System.IComparable%601> arabirimi uygular gibi genel bir sınıf bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a6766-106">For example, you can declare a generic class, `MyGenericClass`, such that the type parameter `T` implements the <xref:System.IComparable%601> interface:</span></span>

[!code-csharp[using an interface constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#1)]

> [!NOTE]
> <span data-ttu-id="a6766-107">Sorgu ifadesinde yer yan tümcesi hakkında daha fazla bilgi için [bkz.](where-clause.md)</span><span class="sxs-lookup"><span data-stu-id="a6766-107">For more information on the where clause in a query expression, see [where clause](where-clause.md).</span></span>

<span data-ttu-id="a6766-108">Yan `where` tümce, taban sınıf kısıtlaması da içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a6766-108">The `where` clause can also include a base class constraint.</span></span> <span data-ttu-id="a6766-109">Taban sınıf kısıtlaması, bu genel tür için tür bağımsız değişkeni olarak kullanılacak bir türün, bu genel tür için tür bağımsız değişkeni olarak kullanılmak üzere taban sınıf (veya bu taban sınıf) olarak belirtilen sınıfa sahip olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="a6766-109">The base class constraint states that a type to be used as a type argument for that generic type has the specified class as a base class (or is that base class) to be used as a type argument for that generic type.</span></span> <span data-ttu-id="a6766-110">Taban sınıf kısıtlaması kullanılırsa, bu tür parametresindeki diğer kısıtlamalardan önce görünmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a6766-110">If the base class constraint is used, it must appear before any other constraints on that type parameter.</span></span> <span data-ttu-id="a6766-111">Bazı türler taban sınıf kısıtlaması olarak <xref:System.Object> <xref:System.Array>izin <xref:System.ValueType>verilmez: , ve .</span><span class="sxs-lookup"><span data-stu-id="a6766-111">Some types are disallowed as a base class constraint: <xref:System.Object>, <xref:System.Array>, and <xref:System.ValueType>.</span></span> <span data-ttu-id="a6766-112">Önce C # 7.3, <xref:System.Enum> <xref:System.Delegate> <xref:System.MulticastDelegate> ve aynı zamanda taban sınıf kısıtlamaları olarak izin verilmedi.</span><span class="sxs-lookup"><span data-stu-id="a6766-112">Prior to C# 7.3, <xref:System.Enum>, <xref:System.Delegate>, and <xref:System.MulticastDelegate> were also disallowed as base class constraints.</span></span> <span data-ttu-id="a6766-113">Aşağıdaki örnek, şimdi taban sınıf olarak belirtilebilen türleri gösterir:</span><span class="sxs-lookup"><span data-stu-id="a6766-113">The following example shows the types that can now be specified as a base class:</span></span>

[!code-csharp[using an interface constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#2)]

<span data-ttu-id="a6766-114">Yan `where` tümce, türün `class` a `struct`veya bir .</span><span class="sxs-lookup"><span data-stu-id="a6766-114">The `where` clause can specify that the type is a `class` or a `struct`.</span></span> <span data-ttu-id="a6766-115">Kısıtlama, `struct` bir taban sınıf kısıtlaması belirtme `System.ValueType`gereksinimini ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="a6766-115">The `struct` constraint removes the need to specify a base class constraint of `System.ValueType`.</span></span> <span data-ttu-id="a6766-116">Tür `System.ValueType` taban sınıf kısıtlaması olarak kullanılmayabilir.</span><span class="sxs-lookup"><span data-stu-id="a6766-116">The `System.ValueType` type may not be used as a base class constraint.</span></span> <span data-ttu-id="a6766-117">Aşağıdaki örnek, hem `class` `struct` kısıtlamaları hem de kısıtlamaları gösterir:</span><span class="sxs-lookup"><span data-stu-id="a6766-117">The following example shows both the `class` and `struct` constraints:</span></span>

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#3)]

<span data-ttu-id="a6766-118">Yan `where` tümce `notnull` kısıtlamayı içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a6766-118">The `where` clause may include the `notnull` constraint.</span></span> <span data-ttu-id="a6766-119">Kısıtlama, `notnull` tür parametresini nullable olmayan türlerle sınırlar.</span><span class="sxs-lookup"><span data-stu-id="a6766-119">The `notnull` constraint limits the type parameter to non-nullable types.</span></span> <span data-ttu-id="a6766-120">Bu tür bir [değer türü](../builtin-types/value-types.md) veya nullable olmayan bir başvuru türü olabilir.</span><span class="sxs-lookup"><span data-stu-id="a6766-120">That type may be a [value type](../builtin-types/value-types.md) or a non-nullable reference type.</span></span> <span data-ttu-id="a6766-121">Kısıtlama, `notnull` bir [ `nullable enable` bağlamda](../../nullable-references.md#nullable-contexts)derlenen kod için C# 8.0'dan başlayarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a6766-121">The `notnull` constraint is available starting in C# 8.0 for code compiled in a [`nullable enable` context](../../nullable-references.md#nullable-contexts).</span></span> <span data-ttu-id="a6766-122">Diğer kısıtlamaların aksine, bir tür `notnull` bağımsız değişkenkısıtlamayı ihlal ederse, derleyici hata yerine bir uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a6766-122">Unlike other constraints, if a type argument violates the `notnull` constraint, the compiler generates a warning instead of an error.</span></span> <span data-ttu-id="a6766-123">Uyarılar yalnızca bir `nullable enable` bağlamda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a6766-123">Warnings are only generated in a `nullable enable` context.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a6766-124">Kısıtlamayı `notnull` içeren genel bildirimler geçersiz bir ilgisiz bağlamda kullanılabilir, ancak derleyici kısıtlamayı zorlamaz.</span><span class="sxs-lookup"><span data-stu-id="a6766-124">Generic declarations that include the `notnull` constraint can be used in a nullable oblivious context, but compiler does not enforce the constraint.</span></span>

[!code-csharp[using the nonnull constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#NotNull)]

<span data-ttu-id="a6766-125">Yan `where` tümce, `unmanaged` bir kısıtlama da içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a6766-125">The `where` clause may also include an `unmanaged` constraint.</span></span> <span data-ttu-id="a6766-126">Kısıtlama, `unmanaged` tür parametresini [yönetilmeyen türler](../builtin-types/unmanaged-types.md)olarak bilinen türlerle sınırlar.</span><span class="sxs-lookup"><span data-stu-id="a6766-126">The `unmanaged` constraint limits the type parameter to types known as [unmanaged types](../builtin-types/unmanaged-types.md).</span></span> <span data-ttu-id="a6766-127">Kısıtlama, `unmanaged` c#'a düşük seviyeli interop kodu yazmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="a6766-127">The `unmanaged` constraint makes it easier to write low-level interop code in C#.</span></span> <span data-ttu-id="a6766-128">Bu kısıtlama, tüm yönetilmeyen türler arasında yeniden kullanılabilir yordamlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="a6766-128">This constraint enables reusable routines across all unmanaged types.</span></span> <span data-ttu-id="a6766-129">Kısıtlama `unmanaged` `class` veya `struct` kısıtlama ile birleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="a6766-129">The `unmanaged` constraint can't be combined with the `class` or `struct` constraint.</span></span> <span data-ttu-id="a6766-130">Kısıtlama, `unmanaged` türün aşağıdaki `struct`gibi olması gerektiğini zorlar:</span><span class="sxs-lookup"><span data-stu-id="a6766-130">The `unmanaged` constraint enforces that the type must be a `struct`:</span></span>

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#4)]

<span data-ttu-id="a6766-131">Yan `where` tümce, bir oluşturucu `new()`kısıtlama sıda içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a6766-131">The `where` clause may also include a constructor constraint, `new()`.</span></span> <span data-ttu-id="a6766-132">Bu kısıtlama, işleci kullanarak bir tür parametresi örneği oluşturmayı `new` mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="a6766-132">That constraint makes it possible to create an instance of a type parameter using the `new` operator.</span></span> <span data-ttu-id="a6766-133">[Yeni() Kısıtlama,](new-constraint.md) derleyiciye, sağlanan herhangi bir tür bağımsız değişkeninin erişilebilir bir parametresiz oluşturucuya sahip olması gerektiğini bilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a6766-133">The [new() Constraint](new-constraint.md) lets the compiler know that any type argument supplied must have an accessible parameterless constructor.</span></span> <span data-ttu-id="a6766-134">Örnek:</span><span class="sxs-lookup"><span data-stu-id="a6766-134">For example:</span></span>

[!code-csharp[using the new constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#5)]

<span data-ttu-id="a6766-135">Kısıtlama `new()` `where` yan tümcede son görünür.</span><span class="sxs-lookup"><span data-stu-id="a6766-135">The `new()` constraint appears last in the `where` clause.</span></span> <span data-ttu-id="a6766-136">Kısıtlama `new()` `struct` veya `unmanaged` kısıtlamalarla birleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="a6766-136">The `new()` constraint can't be combined with the `struct` or `unmanaged` constraints.</span></span> <span data-ttu-id="a6766-137">Bu kısıtlamaları karşılayan tüm türler, `new()` kısıtlamayı gereksiz hale getiren erişilebilir bir parametresiz oluşturucuya sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a6766-137">All types satisfying those constraints must have an accessible parameterless constructor, making the `new()` constraint redundant.</span></span>

<span data-ttu-id="a6766-138">Birden çok tür parametresi ile, örneğin, her tür parametresi için bir `where` yan tümce kullanın:</span><span class="sxs-lookup"><span data-stu-id="a6766-138">With multiple type parameters, use one `where` clause for each type parameter, for example:</span></span>

[!code-csharp[using multiple where constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#6)]

<span data-ttu-id="a6766-139">Aşağıdaki örnekte gösterildiği gibi, genel yöntemlerin parametrelerini yazına kısıtlamalar da ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a6766-139">You can also attach constraints to type parameters of generic methods, as shown in the following example:</span></span>

[!code-csharp[where constraints with generic methods](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#7)]

<span data-ttu-id="a6766-140">Temsilciler üzerindeki tür parametre kısıtlamalarını açıklayan sözdiziminin yöntemlerle aynı olduğuna dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="a6766-140">Notice that the syntax to describe type parameter constraints on delegates is the same as that of methods:</span></span>

[!code-csharp[where constraints with generic methods](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#8)]

<span data-ttu-id="a6766-141">Genel temsilciler hakkında bilgi için [Genel Temsilciler'e](../../programming-guide/generics/generic-delegates.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="a6766-141">For information on generic delegates, see [Generic Delegates](../../programming-guide/generics/generic-delegates.md).</span></span>

<span data-ttu-id="a6766-142">Sözdizimi ve kısıtlamaların kullanımı yla ilgili ayrıntılar için, [Tür Parametreleri üzerindeki Kısıtlamalar](../../programming-guide/generics/constraints-on-type-parameters.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="a6766-142">For details on the syntax and use of constraints, see [Constraints on Type Parameters](../../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a6766-143">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="a6766-143">C# language specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="a6766-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6766-144">See also</span></span>

- [<span data-ttu-id="a6766-145">C# Referans</span><span class="sxs-lookup"><span data-stu-id="a6766-145">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a6766-146">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a6766-146">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a6766-147">Genel Türlere Giriş</span><span class="sxs-lookup"><span data-stu-id="a6766-147">Introduction to Generics</span></span>](../../programming-guide/generics/index.md)
- [<span data-ttu-id="a6766-148">new Kısıtlaması</span><span class="sxs-lookup"><span data-stu-id="a6766-148">new Constraint</span></span>](./new-constraint.md)
- [<span data-ttu-id="a6766-149">Tür Parametrelerindeki Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="a6766-149">Constraints on Type Parameters</span></span>](../../programming-guide/generics/constraints-on-type-parameters.md)
