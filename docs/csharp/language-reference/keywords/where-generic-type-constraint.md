---
title: where (genel tür kısıtlaması) (C# Başvurusu)
ms.date: 04/12/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 16be19e342016becd100e2c21434393c3f36f815
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="where-generic-type-constraint-c-reference"></a><span data-ttu-id="cd510-102">where (genel tür kısıtlaması) (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="cd510-102">where (generic type constraint) (C# Reference)</span></span>

<span data-ttu-id="cd510-103">`where` Yan tümcesi genel tanımında tür parametrelerinde genel tür, yöntem, temsilci veya yerel bir işlev bağımsız değişkenleri olarak kullanılan türleri kısıtlamaları belirtir.</span><span class="sxs-lookup"><span data-stu-id="cd510-103">The `where` clause in a generic definition specifies constraints on the types that are used as arguments for type parameters in a generic type, method, delegate, or local function.</span></span> <span data-ttu-id="cd510-104">Kısıtlamaları arabirimleri, temel sınıflar belirtin veya bir başvuru, değeri veya yönetilmeyen tür genel bir tür gerektirir.</span><span class="sxs-lookup"><span data-stu-id="cd510-104">Constraints can specify interfaces, base classes, or require a generic type to be a reference, value or unmanaged type.</span></span> <span data-ttu-id="cd510-105">Bunlar, tür bağımsız değişkeni sahip olması gerekir yetenekleri bildirin.</span><span class="sxs-lookup"><span data-stu-id="cd510-105">They declare capabilities that the type argument must possess.</span></span>

<span data-ttu-id="cd510-106">Örneğin, genel bir sınıf bildirebilir `MyGenericClass`gibi tür parametresi `T` uygulayan <xref:System.IComparable%601> arabirimi:</span><span class="sxs-lookup"><span data-stu-id="cd510-106">For example, you can declare a generic class, `MyGenericClass`, such that the type parameter `T` implements the <xref:System.IComparable%601> interface:</span></span>

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#1)]

> [!NOTE]
> <span data-ttu-id="cd510-107">Daha fazla bilgi için bir sorgu ifadesinde yan tümcesine bakın [burada yan tümcesi](where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="cd510-107">For more information on the where clause in a query expression, see [where clause](where-clause.md).</span></span>

<span data-ttu-id="cd510-108">`where` Yan tümcesi de bir taban sınıf kısıtlaması içerir.</span><span class="sxs-lookup"><span data-stu-id="cd510-108">The `where` clause can also include a base class constraint.</span></span> <span data-ttu-id="cd510-109">Taban sınıf kısıtlaması genel türü için tür bağımsız değişkeni olarak kullanılacak bir türü belirtilen sınıfın temel sınıf olarak olduğunu bildiren (veya temel sınıfı olan), genel tür için tür bağımsız değişkeni olarak kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="cd510-109">The base class constraint states that a type to be used as a type argument for that generic type has the specified class as a base class (or is that base class) to be used as a type argument for that generic type.</span></span> <span data-ttu-id="cd510-110">Taban sınıf kısıtlaması kullanılırsa, bu tür parametre diğer kısıtlamalar önce görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="cd510-110">If the base class constraint is used, it must appear before any other constraints on that type parameter.</span></span> <span data-ttu-id="cd510-111">Bazı türleri bir temel sınıf kısıtlaması izin verilmez: <xref:System.Object>, <xref:System.Array>, ve <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="cd510-111">Some types are disallowed as a base class constraint: <xref:System.Object>, <xref:System.Array>, and <xref:System.ValueType>.</span></span> <span data-ttu-id="cd510-112">C# 7.3 önce <xref:System.Enum>, <xref:System.Delegate>, ve <xref:System.MulticastDelegate> da temel sınıf kısıtlamaları olarak izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="cd510-112">Prior to C# 7.3, <xref:System.Enum>, <xref:System.Delegate>, and <xref:System.MulticastDelegate> were also disallowed as base class constraints.</span></span> <span data-ttu-id="cd510-113">Aşağıdaki örnek, artık bir temel sınıf olarak belirttiğiniz türlerini gösterir:</span><span class="sxs-lookup"><span data-stu-id="cd510-113">The following example shows the types that can now be specified as a base class:</span></span>

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#2)]

<span data-ttu-id="cd510-114">`where` Yan tümcesi türü olduğunu belirtebilirsiniz bir `class` veya `struct`.</span><span class="sxs-lookup"><span data-stu-id="cd510-114">The `where` clause can specify that the type is a `class` or a `struct`.</span></span> <span data-ttu-id="cd510-115">`struct` Kısıtlamayı kaldırır bir temel sınıf kısıtlaması belirtme ihtiyacını `System.ValueType`.</span><span class="sxs-lookup"><span data-stu-id="cd510-115">The `struct` constraint removes the need to specify a base class constraint of `System.ValueType`.</span></span> <span data-ttu-id="cd510-116">`System.ValueType` Türü bir temel sınıf kısıtlama olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="cd510-116">The `System.ValueType` type may not be used as a base class constraint.</span></span> <span data-ttu-id="cd510-117">Aşağıdaki örnek, her ikisi de gösterir `class` ve `struct` kısıtlamalar:</span><span class="sxs-lookup"><span data-stu-id="cd510-117">The following example shows both the `class` and `struct` constraints:</span></span>

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#3)]

<span data-ttu-id="cd510-118">`where` Yan tümcesi de içerebilir bir `unmanaged` kısıtlaması.</span><span class="sxs-lookup"><span data-stu-id="cd510-118">The `where` clause may also include an `unmanaged` constraint.</span></span> <span data-ttu-id="cd510-119">`unmanaged` Kısıtlaması sınırlar olarak bilinen türleri için tür parametre **yönetilmeyen türleri**.</span><span class="sxs-lookup"><span data-stu-id="cd510-119">The `unmanaged` constraint limits the type parameter to types known as **unmanaged types**.</span></span> <span data-ttu-id="cd510-120">Bir **yönetilmeyen türü** bir başvuru türü değil ve tüm iç içe geçme düzeyini başvuru türü alanlarını içermiyor. bir tür.</span><span class="sxs-lookup"><span data-stu-id="cd510-120">An **unmanaged type** is a type that isn't a reference type and doesn't contain reference type fields at any level of nesting.</span></span> <span data-ttu-id="cd510-121">`unmanaged` Kısıtlaması alt düzey birlikte çalışma kod C# ' ta yazmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="cd510-121">The `unmanaged` constraint makes it easier to write low-level interop code in C#.</span></span> <span data-ttu-id="cd510-122">Bu sınırlama tüm yönetilmeyen türlerine yeniden kullanılabilir yordamlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="cd510-122">This constraint enables reusable routines across all unmanaged types.</span></span> <span data-ttu-id="cd510-123">`unmanaged` Kısıtlaması ile ilişkilendirilemez `class` veya `struct` kısıtlaması.</span><span class="sxs-lookup"><span data-stu-id="cd510-123">The `unmanaged` constraint can't be combined with the `class` or `struct` constraint.</span></span> <span data-ttu-id="cd510-124">`unmanaged` Kısıtlamayı zorlar türü olmalıdır bir `struct`:</span><span class="sxs-lookup"><span data-stu-id="cd510-124">The `unmanaged` constraint enforces that the type must be a `struct`:</span></span>

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#4)]

<span data-ttu-id="cd510-125">`where` Yan tümcesi Oluşturucusu kısıtlaması de içerebilir `new()`.</span><span class="sxs-lookup"><span data-stu-id="cd510-125">The `where` clause may also include a constructor constraint, `new()`.</span></span> <span data-ttu-id="cd510-126">Kısıtlaması, bir tür parametresini kullanarak bir örneğini oluşturmak mümkün kılar, `new` işleci.</span><span class="sxs-lookup"><span data-stu-id="cd510-126">That constraint makes it possible to create an instance of a type parameter using the `new` operator.</span></span> <span data-ttu-id="cd510-127">[New() kısıtlaması](new-constraint.md) sağlanan herhangi bir tür bağımsız değişkeni bir erişilebilir olması gerektiğini biliyor derleyici sağlar parametresiz--veya varsayılan--oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="cd510-127">The [new() Constraint](new-constraint.md) lets the compiler know that any type argument supplied must have an accessible parameterless--or default-- constructor.</span></span> <span data-ttu-id="cd510-128">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="cd510-128">For example:</span></span>

[!code-csharp[using the new constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#5)]

<span data-ttu-id="cd510-129">`new()` Kısıtlaması görünür içinde son `where` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="cd510-129">The `new()` constraint appears last in the `where` clause.</span></span> <span data-ttu-id="cd510-130">`new()` Kısıtlaması ile ilişkilendirilemez `struct` veya `unmanaged` kısıtlamaları.</span><span class="sxs-lookup"><span data-stu-id="cd510-130">The `new()` constraint can't be combined with the `struct` or `unmanaged` constraints.</span></span> <span data-ttu-id="cd510-131">Bu kısıtlamalar erişilebilir bir parametresiz oluşturucuya sahip olmalıdır çağıran, yapmadan tüm türleri `new()` kısıtlaması gereksiz.</span><span class="sxs-lookup"><span data-stu-id="cd510-131">All types satisfying those constraints must have an accessible parameterless constructor, making the `new()` constraint redundant.</span></span>

<span data-ttu-id="cd510-132">Birden çok tür parametreleri ile kullanmayı `where` yan tümcesi örneğin her tür parametresi için:</span><span class="sxs-lookup"><span data-stu-id="cd510-132">With multiple type parameters, use one `where` clause for each type parameter, for example:</span></span>

[!code-csharp[using multiple where constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#6)]

<span data-ttu-id="cd510-133">Tür parametreleri genel yöntemlerin kısıtlamaları aşağıdaki örnekte gösterildiği gibi ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="cd510-133">You can also attach constraints to type parameters of generic methods, as shown in the following example:</span></span>

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#7)]

<span data-ttu-id="cd510-134">Temsilciler üzerinde türü parametresi kısıtlamaları tanımlamak üzere sözdizimini aynı yöntemleri olduğuna dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="cd510-134">Notice that the syntax to describe type parameter constraints on delegates is the same as that of methods:</span></span>

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#8)]

<span data-ttu-id="cd510-135">Genel temsilciler hakkında daha fazla bilgi için bkz: [genel temsilciler](../../../csharp/programming-guide/generics/generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="cd510-135">For information on generic delegates, see [Generic Delegates](../../../csharp/programming-guide/generics/generic-delegates.md).</span></span>

<span data-ttu-id="cd510-136">Söz dizimi ve kullanım kısıtlamaları hakkında daha fazla bilgi için bkz: [tür parametrelerindeki kısıtlamalar](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="cd510-136">For details on the syntax and use of constraints, see [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="cd510-137">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="cd510-137">C# language specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="cd510-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd510-138">See also</span></span>

 [<span data-ttu-id="cd510-139">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="cd510-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="cd510-140">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="cd510-140">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="cd510-141">Genel Türlere Giriş</span><span class="sxs-lookup"><span data-stu-id="cd510-141">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [<span data-ttu-id="cd510-142">new Kısıtlaması</span><span class="sxs-lookup"><span data-stu-id="cd510-142">new Constraint</span></span>](../../../csharp/language-reference/keywords/new-constraint.md)  
 [<span data-ttu-id="cd510-143">Tür Parametrelerindeki Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="cd510-143">Constraints on Type Parameters</span></span>](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
