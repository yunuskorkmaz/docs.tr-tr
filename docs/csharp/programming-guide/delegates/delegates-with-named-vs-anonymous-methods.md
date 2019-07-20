---
title: Temsilcilerin Adlandırılmış ve Anonim yöntemler- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], with named vs. anonymous methods
- methods [C#], in delegates
ms.assetid: 98fa8c61-66b6-4146-986c-3236c4045733
ms.openlocfilehash: 68428c097b4fc43617834c684ec6dc9705512597
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363937"
---
# <a name="delegates-with-named-vs-anonymous-methods-c-programming-guide"></a><span data-ttu-id="c3d5f-102">Temsilcilerin Adlandırılmış ve Anonim Yöntemler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="c3d5f-102">Delegates with Named vs. Anonymous Methods (C# Programming Guide)</span></span>
<span data-ttu-id="c3d5f-103">Bir [temsilci](../../../csharp/language-reference/keywords/delegate.md) , adlandırılmış bir yöntemle ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c3d5f-103">A [delegate](../../../csharp/language-reference/keywords/delegate.md) can be associated with a named method.</span></span> <span data-ttu-id="c3d5f-104">Adlandırılmış bir yöntemi kullanarak bir temsilciyi örneklediğinizde, yöntemi parametre olarak geçirilir, örneğin:</span><span class="sxs-lookup"><span data-stu-id="c3d5f-104">When you instantiate a delegate by using a named method, the method is passed as a parameter, for example:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#1)]  
  
 <span data-ttu-id="c3d5f-105">Bu, adlandırılmış bir yöntem kullanılarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="c3d5f-105">This is called using a named method.</span></span> <span data-ttu-id="c3d5f-106">Adlandırılmış bir yöntemle oluşturulan temsilciler [statik](../../../csharp/language-reference/keywords/static.md) bir yöntem veya örnek yöntemi kapsülleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c3d5f-106">Delegates constructed with a named method can encapsulate either a [static](../../../csharp/language-reference/keywords/static.md) method or an instance method.</span></span> <span data-ttu-id="c3d5f-107">Adlandırılmış Yöntemler, daha önceki sürümlerinde bir temsilci örneketmenin tek yoludur C#.</span><span class="sxs-lookup"><span data-stu-id="c3d5f-107">Named methods are the only way to instantiate a delegate in earlier versions of C#.</span></span> <span data-ttu-id="c3d5f-108">Bununla birlikte, yeni bir yöntemin oluşturulması istenmeyen ek yüktür bir durumda, C# bir temsilci örneklemenize ve her çağrıldığında temsilcinin işlemesini sağlayacak bir kod bloğunu hemen belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3d5f-108">However, in a situation where creating a new method is unwanted overhead, C# enables you to instantiate a delegate and immediately specify a code block that the delegate will process when it is called.</span></span> <span data-ttu-id="c3d5f-109">Blok bir lambda ifadesi veya anonim bir yöntem içerebilir.</span><span class="sxs-lookup"><span data-stu-id="c3d5f-109">The block can contain either a lambda expression or an anonymous method.</span></span> <span data-ttu-id="c3d5f-110">Daha fazla bilgi için bkz. [Anonim işlevler](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span><span class="sxs-lookup"><span data-stu-id="c3d5f-110">For more information, see [Anonymous Functions](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3d5f-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c3d5f-111">Remarks</span></span>  
 <span data-ttu-id="c3d5f-112">Temsilci parametresi olarak geçirdiğiniz yöntemin, temsilci bildirimiyle aynı imzaya sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c3d5f-112">The method that you pass as a delegate parameter must have the same signature as the delegate declaration.</span></span>  
  
 <span data-ttu-id="c3d5f-113">Bir temsilci örneği, statik veya örnek yöntemini kapsülleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c3d5f-113">A delegate instance may encapsulate either static or instance method.</span></span>  
  
 <span data-ttu-id="c3d5f-114">Temsilci bir [Out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametresi kullanabilse de, hangi temsilcinin çağrlanmasını bilemediğinizde çok noktaya yayın olay temsilcilerle kullanımını önermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="c3d5f-114">Although the delegate can use an [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter, we do not recommend its use with multicast event delegates because you cannot know which delegate will be called.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="c3d5f-115">Örnek 1</span><span class="sxs-lookup"><span data-stu-id="c3d5f-115">Example 1</span></span>  
 <span data-ttu-id="c3d5f-116">Aşağıda, bir temsilciyi bildirme ve kullanma konusunda basit bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c3d5f-116">The following is a simple example of declaring and using a delegate.</span></span> <span data-ttu-id="c3d5f-117">Hem temsilcinin `Del`hem de ilişkili `MultiplyNumbers`yöntemin aynı imzaya sahip olduğuna dikkat edin</span><span class="sxs-lookup"><span data-stu-id="c3d5f-117">Notice that both the delegate, `Del`, and the associated method, `MultiplyNumbers`, have the same signature</span></span>  
  
 [!code-csharp[csProgGuideDelegates#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#2)]  
  
## <a name="example-2"></a><span data-ttu-id="c3d5f-118">Örnek 2</span><span class="sxs-lookup"><span data-stu-id="c3d5f-118">Example 2</span></span>  
 <span data-ttu-id="c3d5f-119">Aşağıdaki örnekte, bir temsilci hem statik hem de örnek yöntemlerine eşlenir ve her birinden belirli bilgileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="c3d5f-119">In the following example, one delegate is mapped to both static and instance methods and returns specific information from each.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#3)]  
  
## <a name="see-also"></a><span data-ttu-id="c3d5f-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3d5f-120">See also</span></span>

- [<span data-ttu-id="c3d5f-121">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c3d5f-121">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="c3d5f-122">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="c3d5f-122">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
- [<span data-ttu-id="c3d5f-123">Nasıl yapılır: Temsilcileri birleştirme (çok noktaya yayın temsilcileri)</span><span class="sxs-lookup"><span data-stu-id="c3d5f-123">How to: Combine Delegates (Multicast Delegates)</span></span>](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)
- [<span data-ttu-id="c3d5f-124">Olaylar</span><span class="sxs-lookup"><span data-stu-id="c3d5f-124">Events</span></span>](../../../csharp/programming-guide/events/index.md)
