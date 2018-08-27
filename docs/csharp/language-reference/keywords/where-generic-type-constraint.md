---
title: where (genel tür kısıtlaması) (C# Başvurusu)
ms.date: 04/12/2018
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.openlocfilehash: 34246824fb8ff28e47ea424c78eca38e999a30b6
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42931882"
---
# <a name="where-generic-type-constraint-c-reference"></a><span data-ttu-id="726ed-102">where (genel tür kısıtlaması) (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="726ed-102">where (generic type constraint) (C# Reference)</span></span>

<span data-ttu-id="726ed-103">`where` Yan tümcesinde genel bir tanımı bir genel tür, yöntem, temsilci veya yerel işlev parametrelerinde türü bağımsız değişkenleri olarak kullanılan türler kısıtlamaları belirtir.</span><span class="sxs-lookup"><span data-stu-id="726ed-103">The `where` clause in a generic definition specifies constraints on the types that are used as arguments for type parameters in a generic type, method, delegate, or local function.</span></span> <span data-ttu-id="726ed-104">Kısıtlamaları, temel sınıfları, arabirimleri belirtin veya bir başvuru, değer veya yönetilmeyen tür için bir genel türü gerektirir.</span><span class="sxs-lookup"><span data-stu-id="726ed-104">Constraints can specify interfaces, base classes, or require a generic type to be a reference, value or unmanaged type.</span></span> <span data-ttu-id="726ed-105">Bunlar, tür bağımsız değişkeni sahip olması gereken özellikleri bildirin.</span><span class="sxs-lookup"><span data-stu-id="726ed-105">They declare capabilities that the type argument must possess.</span></span>

<span data-ttu-id="726ed-106">Örneğin, genel bir sınıf bildirebilirsiniz `MyGenericClass`gibi tür parametresi `T` uygulayan <xref:System.IComparable%601> arabirimi:</span><span class="sxs-lookup"><span data-stu-id="726ed-106">For example, you can declare a generic class, `MyGenericClass`, such that the type parameter `T` implements the <xref:System.IComparable%601> interface:</span></span>

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#1)]

> [!NOTE]
> <span data-ttu-id="726ed-107">Nerede hakkında daha fazla bilgi için bkz yan tümcesi bir sorgu ifadesinde [burada yan tümcesi](where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="726ed-107">For more information on the where clause in a query expression, see [where clause](where-clause.md).</span></span>

<span data-ttu-id="726ed-108">`where` Yan tümcesi, bir temel sınıf kısıtlaması de içerebilir.</span><span class="sxs-lookup"><span data-stu-id="726ed-108">The `where` clause can also include a base class constraint.</span></span> <span data-ttu-id="726ed-109">Temel sınıf kısıtlaması bir tür, genel tür için bir tür bağımsız değişkeni olarak kullanılacak bir temel sınıf olarak belirtilen sınıf olduğunu belirtir (veya temel sınıf olan), genel tür için bir tür bağımsız değişkeni olarak kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="726ed-109">The base class constraint states that a type to be used as a type argument for that generic type has the specified class as a base class (or is that base class) to be used as a type argument for that generic type.</span></span> <span data-ttu-id="726ed-110">Temel sınıf kısıtlaması kullandıysanız, bu tür parametresi üzerinde diğer kısıtlamalardan önce yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="726ed-110">If the base class constraint is used, it must appear before any other constraints on that type parameter.</span></span> <span data-ttu-id="726ed-111">Bazı türleri temel sınıf kısıtlama olarak izin verilmez: <xref:System.Object>, <xref:System.Array>, ve <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="726ed-111">Some types are disallowed as a base class constraint: <xref:System.Object>, <xref:System.Array>, and <xref:System.ValueType>.</span></span> <span data-ttu-id="726ed-112">C# 7.3 önce <xref:System.Enum>, <xref:System.Delegate>, ve <xref:System.MulticastDelegate> ayrıca temel sınıf kısıtlama olarak izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="726ed-112">Prior to C# 7.3, <xref:System.Enum>, <xref:System.Delegate>, and <xref:System.MulticastDelegate> were also disallowed as base class constraints.</span></span> <span data-ttu-id="726ed-113">Aşağıdaki örnek, artık temel sınıf olarak belirttiğiniz türlerini gösterir:</span><span class="sxs-lookup"><span data-stu-id="726ed-113">The following example shows the types that can now be specified as a base class:</span></span>

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#2)]

<span data-ttu-id="726ed-114">`where` Yan tümcesi, türü olduğunu belirtebilirsiniz bir `class` veya `struct`.</span><span class="sxs-lookup"><span data-stu-id="726ed-114">The `where` clause can specify that the type is a `class` or a `struct`.</span></span> <span data-ttu-id="726ed-115">`struct` Sınırlama bir temel sınıfı kısıtlamasını belirtmek için gereken kaldırır `System.ValueType`.</span><span class="sxs-lookup"><span data-stu-id="726ed-115">The `struct` constraint removes the need to specify a base class constraint of `System.ValueType`.</span></span> <span data-ttu-id="726ed-116">`System.ValueType` Türü temel sınıf kısıtlama olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="726ed-116">The `System.ValueType` type may not be used as a base class constraint.</span></span> <span data-ttu-id="726ed-117">Aşağıdaki örnek her ikisini de gösteren `class` ve `struct` kısıtlamaları:</span><span class="sxs-lookup"><span data-stu-id="726ed-117">The following example shows both the `class` and `struct` constraints:</span></span>

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#3)]

<span data-ttu-id="726ed-118">`where` Yan tümcesi de içerebilir bir `unmanaged` kısıtlaması.</span><span class="sxs-lookup"><span data-stu-id="726ed-118">The `where` clause may also include an `unmanaged` constraint.</span></span> <span data-ttu-id="726ed-119">`unmanaged` Sınırlar olarak bilinen türler için tür parametresi kısıtlaması **yönetilmeyen türleri**.</span><span class="sxs-lookup"><span data-stu-id="726ed-119">The `unmanaged` constraint limits the type parameter to types known as **unmanaged types**.</span></span> <span data-ttu-id="726ed-120">Bir **yönetilmeyen tür** , bir başvuru türü değil ve başvuru türü alanları iç içe geçme herhangi bir düzeyde içermeyen bir türdür.</span><span class="sxs-lookup"><span data-stu-id="726ed-120">An **unmanaged type** is a type that isn't a reference type and doesn't contain reference type fields at any level of nesting.</span></span> <span data-ttu-id="726ed-121">`unmanaged` Kısıtlaması alt düzey birlikte çalışma kodu C# ' ta yazmak kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="726ed-121">The `unmanaged` constraint makes it easier to write low-level interop code in C#.</span></span> <span data-ttu-id="726ed-122">Bu kısıtlama, yönetilmeyen tüm türleri arasında yeniden kullanılabilir yordamları sağlar.</span><span class="sxs-lookup"><span data-stu-id="726ed-122">This constraint enables reusable routines across all unmanaged types.</span></span> <span data-ttu-id="726ed-123">`unmanaged` Kısıtlaması ile birleştirilemez `class` veya `struct` kısıtlaması.</span><span class="sxs-lookup"><span data-stu-id="726ed-123">The `unmanaged` constraint can't be combined with the `class` or `struct` constraint.</span></span> <span data-ttu-id="726ed-124">`unmanaged` Kısıtlamayı zorlar türü olmalıdır bir `struct`:</span><span class="sxs-lookup"><span data-stu-id="726ed-124">The `unmanaged` constraint enforces that the type must be a `struct`:</span></span>

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#4)]

<span data-ttu-id="726ed-125">`where` Yan tümcesi bir oluşturucu kısıtlaması de içerebilir `new()`.</span><span class="sxs-lookup"><span data-stu-id="726ed-125">The `where` clause may also include a constructor constraint, `new()`.</span></span> <span data-ttu-id="726ed-126">Kısıtlaması, bir tür parametresini kullanarak bir örneğini oluşturmak mümkün kılar, `new` işleci.</span><span class="sxs-lookup"><span data-stu-id="726ed-126">That constraint makes it possible to create an instance of a type parameter using the `new` operator.</span></span> <span data-ttu-id="726ed-127">[New() kısıtlaması](new-constraint.md) sağlanan herhangi bir tür bağımsız değişkeni bir erişilebilir olması gerektiğini bilmeniz derleyici sağlar parametresiz--ya da varsayılan--oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="726ed-127">The [new() Constraint](new-constraint.md) lets the compiler know that any type argument supplied must have an accessible parameterless--or default-- constructor.</span></span> <span data-ttu-id="726ed-128">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="726ed-128">For example:</span></span>

[!code-csharp[using the new constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#5)]

<span data-ttu-id="726ed-129">`new()` Kısıtlaması, son görüntülenen `where` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="726ed-129">The `new()` constraint appears last in the `where` clause.</span></span> <span data-ttu-id="726ed-130">`new()` Kısıtlaması ile birleştirilemez `struct` veya `unmanaged` kısıtlamaları.</span><span class="sxs-lookup"><span data-stu-id="726ed-130">The `new()` constraint can't be combined with the `struct` or `unmanaged` constraints.</span></span> <span data-ttu-id="726ed-131">Kısıtlamalar, erişilebilir bir parametresiz oluşturucusu olmalıdır çağıran, yapmadan tüm türleri `new()` yedekli kısıtlaması.</span><span class="sxs-lookup"><span data-stu-id="726ed-131">All types satisfying those constraints must have an accessible parameterless constructor, making the `new()` constraint redundant.</span></span>

<span data-ttu-id="726ed-132">Birden çok tür parametreleriyle kullanın `where` yan tümcesi, örneğin her tür parametresi için:</span><span class="sxs-lookup"><span data-stu-id="726ed-132">With multiple type parameters, use one `where` clause for each type parameter, for example:</span></span>

[!code-csharp[using multiple where constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#6)]

<span data-ttu-id="726ed-133">Aşağıdaki örnekte gösterildiği gibi bazı sınırlamalar genel yöntemlerin parametreleri ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="726ed-133">You can also attach constraints to type parameters of generic methods, as shown in the following example:</span></span>

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#7)]

<span data-ttu-id="726ed-134">Temsilciler üzerinde tür parametresi kısıtlamaları tanımlamak için sözdizimi, yöntemlerin aynı olduğuna dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="726ed-134">Notice that the syntax to describe type parameter constraints on delegates is the same as that of methods:</span></span>

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#8)]

<span data-ttu-id="726ed-135">Genel temsilciler hakkında daha fazla bilgi için bkz: [genel temsilciler](../../../csharp/programming-guide/generics/generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="726ed-135">For information on generic delegates, see [Generic Delegates](../../../csharp/programming-guide/generics/generic-delegates.md).</span></span>

<span data-ttu-id="726ed-136">Söz dizimi ve kullanım kısıtlamaları hakkında daha fazla bilgi için bkz: [tür parametrelerindeki kısıtlamalar](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="726ed-136">For details on the syntax and use of constraints, see [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="726ed-137">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="726ed-137">C# language specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="726ed-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="726ed-138">See also</span></span>

- [<span data-ttu-id="726ed-139">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="726ed-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="726ed-140">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="726ed-140">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="726ed-141">Genel Türlere Giriş</span><span class="sxs-lookup"><span data-stu-id="726ed-141">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
- [<span data-ttu-id="726ed-142">new Kısıtlaması</span><span class="sxs-lookup"><span data-stu-id="726ed-142">new Constraint</span></span>](../../../csharp/language-reference/keywords/new-constraint.md)  
- [<span data-ttu-id="726ed-143">Tür Parametrelerindeki Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="726ed-143">Constraints on Type Parameters</span></span>](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
