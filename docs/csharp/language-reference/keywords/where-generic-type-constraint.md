---
title: where (genel tür kısıtlaması) (C# Başvurusu)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.assetid: d7aa871b-0714-416a-bab2-96f87ada4310
caps.latest.revision: 10
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f2b7b159689aa771d3f9d59e3b1dd340c85b1d79
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="where-generic-type-constraint-c-reference"></a><span data-ttu-id="afc21-102">where (genel tür kısıtlaması) (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="afc21-102">where (generic type constraint) (C# Reference)</span></span>
<span data-ttu-id="afc21-103">Genel tür tanımında `where` yan tümcesi genel bildiriminde tanımlanan bir tür parametresi için bağımsız değişken olarak kullanılan türleri kısıtlamaları belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="afc21-103">In a generic type definition, the `where` clause is used to specify constraints on the types that can be used as arguments for a type parameter defined in a generic declaration.</span></span> <span data-ttu-id="afc21-104">Örneğin, genel bir sınıf bildirebilir `MyGenericClass`gibi tür parametresi `T` uygulayan <xref:System.IComparable%601> arabirimi:</span><span class="sxs-lookup"><span data-stu-id="afc21-104">For example, you can declare a generic class, `MyGenericClass`, such that the type parameter `T` implements the <xref:System.IComparable%601> interface:</span></span>  
  
```csharp  
public class MyGenericClass<T> where T:IComparable { }  
```  
  
> [!NOTE]
>  <span data-ttu-id="afc21-105">Daha fazla bilgi için bir sorgu ifadesinde yan tümcesine bakın [burada yan tümcesi](../../../csharp/language-reference/keywords/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="afc21-105">For more information on the where clause in a query expression, see [where clause](../../../csharp/language-reference/keywords/where-clause.md).</span></span>  
  
 <span data-ttu-id="afc21-106">Arabirim kısıtlamaları yanı sıra bir `where` yan tümcesi bir türü belirtilen sınıf bir temel sınıf olarak (veya bu sınıfı) sahip belirten bir temel sınıf kısıtlaması içerebilir genel türü için tür bağımsız değişkeni olarak kullanılması için.</span><span class="sxs-lookup"><span data-stu-id="afc21-106">In addition to interface constraints, a `where` clause can include a base class constraint, which states that a type must have the specified class as a base class (or be that class itself) in order to be used as a type argument for that generic type.</span></span> <span data-ttu-id="afc21-107">Böyle bir kısıtlama kullanılırsa, bu tür parametre diğer kısıtlamalar önce görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="afc21-107">If such a constraint is used, it must appear before any other constraints on that type parameter.</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_1.cs)]  
  
 <span data-ttu-id="afc21-108">`where` Yan tümcesi Oluşturucusu kısıtlaması de içerebilir.</span><span class="sxs-lookup"><span data-stu-id="afc21-108">The `where` clause may also include a constructor constraint.</span></span> <span data-ttu-id="afc21-109">Yeni işlecini kullanan bir tür parametresi bir örneğini oluşturmak mümkündür; Ancak, bunu yapmak için tür parametresi gerekir kısıtlı Oluşturucusu kısıtlaması tarafından `new()`.</span><span class="sxs-lookup"><span data-stu-id="afc21-109">It is possible to create an instance of a type parameter using the new operator; however, in order to do so the type parameter must be constrained by the constructor constraint, `new()`.</span></span> <span data-ttu-id="afc21-110">[New() kısıtlaması](../../../csharp/language-reference/keywords/new-constraint.md) sağlanan herhangi bir tür bağımsız değişkeni bir erişilebilir olması gerektiğini biliyor derleyici sağlar parametresiz--veya varsayılan--oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="afc21-110">The [new() Constraint](../../../csharp/language-reference/keywords/new-constraint.md) lets the compiler know that any type argument supplied must have an accessible parameterless--or default-- constructor.</span></span> <span data-ttu-id="afc21-111">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="afc21-111">For example:</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_2.cs)]  
  
 <span data-ttu-id="afc21-112">`new()` Kısıtlaması görünür içinde son `where` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="afc21-112">The `new()` constraint appears last in the `where` clause.</span></span>  
  
 <span data-ttu-id="afc21-113">Birden çok tür parametreleri ile kullanmayı `where` yan tümcesi örneğin her tür parametresi için:</span><span class="sxs-lookup"><span data-stu-id="afc21-113">With multiple type parameters, use one `where` clause for each type parameter, for example:</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_3.cs)]  
  
 <span data-ttu-id="afc21-114">Tür parametreleri bu gibi genel yöntemlerin kısıtlamaları da ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="afc21-114">You can also attach constraints to type parameters of generic methods, like this:</span></span>  
  
```csharp  
public bool MyMethod<T>(T t) where T : IMyInterface { }  
```  
  
 <span data-ttu-id="afc21-115">Temsilciler üzerinde türü parametresi kısıtlamaları tanımlamak üzere sözdizimini aynı yöntemleri olduğuna dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="afc21-115">Notice that the syntax to describe type parameter constraints on delegates is the same as that of methods:</span></span>  
  
```csharp  
delegate T MyDelegate<T>() where T : new()  
```  
  
 <span data-ttu-id="afc21-116">Genel temsilciler hakkında daha fazla bilgi için bkz: [genel temsilciler](../../../csharp/programming-guide/generics/generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="afc21-116">For information on generic delegates, see [Generic Delegates](../../../csharp/programming-guide/generics/generic-delegates.md).</span></span>  
  
 <span data-ttu-id="afc21-117">Söz dizimi ve kullanım kısıtlamaları hakkında daha fazla bilgi için bkz: [tür parametrelerindeki kısıtlamalar](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="afc21-117">For details on the syntax and use of constraints, see [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="afc21-118">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="afc21-118">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="afc21-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="afc21-119">See Also</span></span>  
 [<span data-ttu-id="afc21-120">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="afc21-120">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="afc21-121">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="afc21-121">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="afc21-122">Genel türlere giriş</span><span class="sxs-lookup"><span data-stu-id="afc21-122">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [<span data-ttu-id="afc21-123">New kısıtlaması</span><span class="sxs-lookup"><span data-stu-id="afc21-123">new Constraint</span></span>](../../../csharp/language-reference/keywords/new-constraint.md)  
 [<span data-ttu-id="afc21-124">Tür parametrelerindeki kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="afc21-124">Constraints on Type Parameters</span></span>](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)
