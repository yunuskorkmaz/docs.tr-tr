---
title: Adlandırılmış ve anonim yöntemler- C# Programlama Kılavuzu ile Temsilciler
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], with named vs. anonymous methods
- methods [C#], in delegates
ms.assetid: 98fa8c61-66b6-4146-986c-3236c4045733
ms.openlocfilehash: 1ec366999ca6457471b705fa83f06fcde4293f4e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712383"
---
# <a name="delegates-with-named-vs-anonymous-methods-c-programming-guide"></a><span data-ttu-id="6ab3f-102">Adlandırılmış ve Anonim Yöntemler ile Temsilciler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="6ab3f-102">Delegates with Named vs. Anonymous Methods (C# Programming Guide)</span></span>
<span data-ttu-id="6ab3f-103">Bir [temsilci](../../language-reference/builtin-types/reference-types.md) , adlandırılmış bir yöntemle ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="6ab3f-103">A [delegate](../../language-reference/builtin-types/reference-types.md) can be associated with a named method.</span></span> <span data-ttu-id="6ab3f-104">Adlandırılmış bir yöntemi kullanarak bir temsilciyi örneklediğinizde, yöntemi parametre olarak geçirilir, örneğin:</span><span class="sxs-lookup"><span data-stu-id="6ab3f-104">When you instantiate a delegate by using a named method, the method is passed as a parameter, for example:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#1)]  
  
 <span data-ttu-id="6ab3f-105">Bu, adlandırılmış bir yöntem kullanılarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="6ab3f-105">This is called using a named method.</span></span> <span data-ttu-id="6ab3f-106">Adlandırılmış bir yöntemle oluşturulan temsilciler [statik](../../language-reference/keywords/static.md) bir yöntem veya örnek yöntemi kapsülleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ab3f-106">Delegates constructed with a named method can encapsulate either a [static](../../language-reference/keywords/static.md) method or an instance method.</span></span> <span data-ttu-id="6ab3f-107">Adlandırılmış Yöntemler, daha önceki sürümlerinde bir temsilci örneketmenin tek yoludur C#.</span><span class="sxs-lookup"><span data-stu-id="6ab3f-107">Named methods are the only way to instantiate a delegate in earlier versions of C#.</span></span> <span data-ttu-id="6ab3f-108">Bununla birlikte, yeni bir yöntemin oluşturulması istenmeyen ek yüktür bir durumda, C# bir temsilci örneklemenize ve her çağrıldığında temsilcinin işlemesini sağlayacak bir kod bloğunu hemen belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ab3f-108">However, in a situation where creating a new method is unwanted overhead, C# enables you to instantiate a delegate and immediately specify a code block that the delegate will process when it is called.</span></span> <span data-ttu-id="6ab3f-109">Blok bir lambda ifadesi veya anonim bir yöntem içerebilir.</span><span class="sxs-lookup"><span data-stu-id="6ab3f-109">The block can contain either a lambda expression or an anonymous method.</span></span> <span data-ttu-id="6ab3f-110">Daha fazla bilgi için bkz. [Anonim işlevler](../statements-expressions-operators/anonymous-functions.md).</span><span class="sxs-lookup"><span data-stu-id="6ab3f-110">For more information, see [Anonymous Functions](../statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6ab3f-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6ab3f-111">Remarks</span></span>  
 <span data-ttu-id="6ab3f-112">Temsilci parametresi olarak geçirdiğiniz yöntemin, temsilci bildirimiyle aynı imzaya sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6ab3f-112">The method that you pass as a delegate parameter must have the same signature as the delegate declaration.</span></span>  
  
 <span data-ttu-id="6ab3f-113">Bir temsilci örneği, statik veya örnek yöntemini kapsülleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ab3f-113">A delegate instance may encapsulate either static or instance method.</span></span>  
  
 <span data-ttu-id="6ab3f-114">Temsilci bir [Out](../../language-reference/keywords/out-parameter-modifier.md) parametresi kullanabilse de, hangi temsilcinin çağrlanmasını bilemediğinizde çok noktaya yayın olay temsilcilerle kullanımını önermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="6ab3f-114">Although the delegate can use an [out](../../language-reference/keywords/out-parameter-modifier.md) parameter, we do not recommend its use with multicast event delegates because you cannot know which delegate will be called.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="6ab3f-115">Örnek 1</span><span class="sxs-lookup"><span data-stu-id="6ab3f-115">Example 1</span></span>  
 <span data-ttu-id="6ab3f-116">Aşağıda, bir temsilciyi bildirme ve kullanma konusunda basit bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6ab3f-116">The following is a simple example of declaring and using a delegate.</span></span> <span data-ttu-id="6ab3f-117">Hem temsilci, `Del`hem de ilişkili Yöntem `MultiplyNumbers`aynı imzaya sahip olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="6ab3f-117">Notice that both the delegate, `Del`, and the associated method, `MultiplyNumbers`, have the same signature</span></span>  
  
 [!code-csharp[csProgGuideDelegates#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#2)]  
  
## <a name="example-2"></a><span data-ttu-id="6ab3f-118">Örnek 2</span><span class="sxs-lookup"><span data-stu-id="6ab3f-118">Example 2</span></span>  
 <span data-ttu-id="6ab3f-119">Aşağıdaki örnekte, bir temsilci hem statik hem de örnek yöntemlerine eşlenir ve her birinden belirli bilgileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="6ab3f-119">In the following example, one delegate is mapped to both static and instance methods and returns specific information from each.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#3)]  
  
## <a name="see-also"></a><span data-ttu-id="6ab3f-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6ab3f-120">See also</span></span>

- [<span data-ttu-id="6ab3f-121">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6ab3f-121">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="6ab3f-122">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="6ab3f-122">Delegates</span></span>](./index.md)
- [<span data-ttu-id="6ab3f-123">Temsilcileri birleştirme (çok noktaya yayın temsilcileri)</span><span class="sxs-lookup"><span data-stu-id="6ab3f-123">How to combine delegates (Multicast Delegates)</span></span>](./how-to-combine-delegates-multicast-delegates.md)
- [<span data-ttu-id="6ab3f-124">Olaylar</span><span class="sxs-lookup"><span data-stu-id="6ab3f-124">Events</span></span>](../events/index.md)
