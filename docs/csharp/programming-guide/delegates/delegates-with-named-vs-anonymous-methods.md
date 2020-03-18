---
title: Adlandırılmış ve Anonim Yöntemlerle Temsilciler - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], with named vs. anonymous methods
- methods [C#], in delegates
ms.assetid: 98fa8c61-66b6-4146-986c-3236c4045733
ms.openlocfilehash: 1ec366999ca6457471b705fa83f06fcde4293f4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712383"
---
# <a name="delegates-with-named-vs-anonymous-methods-c-programming-guide"></a><span data-ttu-id="df3fd-102">Adlandırılmış ve Anonim Yöntemler ile Temsilciler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="df3fd-102">Delegates with Named vs. Anonymous Methods (C# Programming Guide)</span></span>
<span data-ttu-id="df3fd-103">Bir [temsilci](../../language-reference/builtin-types/reference-types.md) adlı yöntemle ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="df3fd-103">A [delegate](../../language-reference/builtin-types/reference-types.md) can be associated with a named method.</span></span> <span data-ttu-id="df3fd-104">Adlandırılmış bir yöntem kullanarak bir temsilciyi anında kullandığınızda, yöntem parametre olarak geçirilir, örneğin:</span><span class="sxs-lookup"><span data-stu-id="df3fd-104">When you instantiate a delegate by using a named method, the method is passed as a parameter, for example:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#1)]  
  
 <span data-ttu-id="df3fd-105">Buna adlandırılmış bir yöntem kullanılarak denir.</span><span class="sxs-lookup"><span data-stu-id="df3fd-105">This is called using a named method.</span></span> <span data-ttu-id="df3fd-106">Adlandırılmış bir yöntemle oluşturulmuş temsilciler [statik](../../language-reference/keywords/static.md) bir yöntem veya örnek yöntemi kapsajene edebilir.</span><span class="sxs-lookup"><span data-stu-id="df3fd-106">Delegates constructed with a named method can encapsulate either a [static](../../language-reference/keywords/static.md) method or an instance method.</span></span> <span data-ttu-id="df3fd-107">Adlandırılmış yöntemler, C#'ın önceki sürümlerinde bir temsilciyi anında atanın tek yoludur.</span><span class="sxs-lookup"><span data-stu-id="df3fd-107">Named methods are the only way to instantiate a delegate in earlier versions of C#.</span></span> <span data-ttu-id="df3fd-108">Ancak, yeni bir yöntem oluşturmanın istenmeyen ek yükü olduğu bir durumda, C# bir temsilciyi anında oluşturmanızı ve çağrıldığında temsilcinin işleyecekleri bir kod bloğunu hemen belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="df3fd-108">However, in a situation where creating a new method is unwanted overhead, C# enables you to instantiate a delegate and immediately specify a code block that the delegate will process when it is called.</span></span> <span data-ttu-id="df3fd-109">Blok bir lambda ifadesi veya anonim bir yöntem içerebilir.</span><span class="sxs-lookup"><span data-stu-id="df3fd-109">The block can contain either a lambda expression or an anonymous method.</span></span> <span data-ttu-id="df3fd-110">Daha fazla bilgi için [Bkz. Anonim Fonksiyonlar.](../statements-expressions-operators/anonymous-functions.md)</span><span class="sxs-lookup"><span data-stu-id="df3fd-110">For more information, see [Anonymous Functions](../statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df3fd-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="df3fd-111">Remarks</span></span>  
 <span data-ttu-id="df3fd-112">Temsilci parametresi olarak geçtiğiniz yöntem, temsilci bildirimiyle aynı imzaya sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="df3fd-112">The method that you pass as a delegate parameter must have the same signature as the delegate declaration.</span></span>  
  
 <span data-ttu-id="df3fd-113">Bir temsilci örneği statik veya örnek yöntemini özetleyebilir.</span><span class="sxs-lookup"><span data-stu-id="df3fd-113">A delegate instance may encapsulate either static or instance method.</span></span>  
  
 <span data-ttu-id="df3fd-114">Temsilci [çıkış](../../language-reference/keywords/out-parameter-modifier.md) parametresi kullanabilse de, hangi temsilcinin aranacağını bilmediğiniz için çok noktaya yayın olay temsilcileriyle kullanılmasını önermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="df3fd-114">Although the delegate can use an [out](../../language-reference/keywords/out-parameter-modifier.md) parameter, we do not recommend its use with multicast event delegates because you cannot know which delegate will be called.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="df3fd-115">Örnek 1</span><span class="sxs-lookup"><span data-stu-id="df3fd-115">Example 1</span></span>  
 <span data-ttu-id="df3fd-116">Aşağıda, bir temsilciyi bildirme ve kullanmanın basit bir örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="df3fd-116">The following is a simple example of declaring and using a delegate.</span></span> <span data-ttu-id="df3fd-117">Hem temsilcinin `Del`hem de ilişkili yöntemin `MultiplyNumbers`aynı imzaya sahip olduğuna dikkat edin</span><span class="sxs-lookup"><span data-stu-id="df3fd-117">Notice that both the delegate, `Del`, and the associated method, `MultiplyNumbers`, have the same signature</span></span>  
  
 [!code-csharp[csProgGuideDelegates#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#2)]  
  
## <a name="example-2"></a><span data-ttu-id="df3fd-118">Örnek 2</span><span class="sxs-lookup"><span data-stu-id="df3fd-118">Example 2</span></span>  
 <span data-ttu-id="df3fd-119">Aşağıdaki örnekte, bir temsilci hem statik hem de örnek yöntemleriyle eşlenir ve her birinden belirli bilgileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="df3fd-119">In the following example, one delegate is mapped to both static and instance methods and returns specific information from each.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#3)]  
  
## <a name="see-also"></a><span data-ttu-id="df3fd-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="df3fd-120">See also</span></span>

- [<span data-ttu-id="df3fd-121">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="df3fd-121">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="df3fd-122">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="df3fd-122">Delegates</span></span>](./index.md)
- [<span data-ttu-id="df3fd-123">Temsilciler nasıl birleştirilir (Çok Noktaya Yayın Temsilcileri)</span><span class="sxs-lookup"><span data-stu-id="df3fd-123">How to combine delegates (Multicast Delegates)</span></span>](./how-to-combine-delegates-multicast-delegates.md)
- [<span data-ttu-id="df3fd-124">Olaylar</span><span class="sxs-lookup"><span data-stu-id="df3fd-124">Events</span></span>](../events/index.md)
