---
title: "Temsilciler adlandırılmış vs ile. Anonim Yöntemler (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- delegates [C#], with named vs. anonymous methods
- methods [C#], in delegates
ms.assetid: 98fa8c61-66b6-4146-986c-3236c4045733
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 59317ad3cd9a5d360d0375bf46ff0c9f752a5944
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="delegates-with-named-vs-anonymous-methods-c-programming-guide"></a><span data-ttu-id="3d61b-102">Temsilciler adlandırılmış vs ile. Anonim Yöntemler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="3d61b-102">Delegates with Named vs. Anonymous Methods (C# Programming Guide)</span></span>
<span data-ttu-id="3d61b-103">A [temsilci](../../../csharp/language-reference/keywords/delegate.md) adlandırılmış bir yöntem ile ilişkili olabilir.</span><span class="sxs-lookup"><span data-stu-id="3d61b-103">A [delegate](../../../csharp/language-reference/keywords/delegate.md) can be associated with a named method.</span></span> <span data-ttu-id="3d61b-104">Adlandırılmış bir yöntemi kullanarak bir temsilci örneği, yöntemi bir parametre örneğin geçirilir:</span><span class="sxs-lookup"><span data-stu-id="3d61b-104">When you instantiate a delegate by using a named method, the method is passed as a parameter, for example:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#1](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_1.cs)]  
  
 <span data-ttu-id="3d61b-105">Bu, adlandırılmış bir yöntem kullanılarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="3d61b-105">This is called using a named method.</span></span> <span data-ttu-id="3d61b-106">Adlandırılmış bir yöntemle oluşturulan temsilcileri ya da kapsülleyen bir [statik](../../../csharp/language-reference/keywords/static.md) yöntemi veya örnek yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3d61b-106">Delegates constructed with a named method can encapsulate either a [static](../../../csharp/language-reference/keywords/static.md) method or an instance method.</span></span> <span data-ttu-id="3d61b-107">Adlandırılmış yöntemleri bir temsilci önceki sürümlerinde, C# örneği oluşturmak için tek yoludur.</span><span class="sxs-lookup"><span data-stu-id="3d61b-107">Named methods are the only way to instantiate a delegate in earlier versions of C#.</span></span> <span data-ttu-id="3d61b-108">Ancak, yeni bir yöntem oluşturma ek yükü istenmeyen olduğu bir durumda, C#, bir temsilci örneği ve onu çağrıldığında, temsilci işleyecek kod bloğu hemen belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="3d61b-108">However, in a situation where creating a new method is unwanted overhead, C# enables you to instantiate a delegate and immediately specify a code block that the delegate will process when it is called.</span></span> <span data-ttu-id="3d61b-109">Blok lambda ifadesi ya da anonim yöntemi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="3d61b-109">The block can contain either a lambda expression or an anonymous method.</span></span> <span data-ttu-id="3d61b-110">Daha fazla bilgi için bkz: [anonim işlevler](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span><span class="sxs-lookup"><span data-stu-id="3d61b-110">For more information, see [Anonymous Functions](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d61b-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3d61b-111">Remarks</span></span>  
 <span data-ttu-id="3d61b-112">Temsilci parametre olarak geçirmek yöntemi temsilci bildirimi olarak aynı imzaya sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3d61b-112">The method that you pass as a delegate parameter must have the same signature as the delegate declaration.</span></span>  
  
 <span data-ttu-id="3d61b-113">Bir temsilci örneği ya da statik kapsülleyen veya yöntemi örneği olabilir.</span><span class="sxs-lookup"><span data-stu-id="3d61b-113">A delegate instance may encapsulate either static or instance method.</span></span>  
  
 <span data-ttu-id="3d61b-114">Temsilci kullanabilirsiniz ancak bir [çıkışı](../../../csharp/language-reference/keywords/out.md) parametresi önerilmez kullanımı ile çok noktaya yayın olay temsilcileri hangi temsilcinin çağrılacağı bilemezsiniz olduğundan.</span><span class="sxs-lookup"><span data-stu-id="3d61b-114">Although the delegate can use an [out](../../../csharp/language-reference/keywords/out.md) parameter, we do not recommend its use with multicast event delegates because you cannot know which delegate will be called.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="3d61b-115">Örnek 1</span><span class="sxs-lookup"><span data-stu-id="3d61b-115">Example 1</span></span>  
 <span data-ttu-id="3d61b-116">Bildirme ve bir temsilci kullanarak basit bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3d61b-116">The following is a simple example of declaring and using a delegate.</span></span> <span data-ttu-id="3d61b-117">Dikkat hem temsilci `Del`ve ilişkili yöntemi `MultiplyNumbers`, aynı imzaya sahip</span><span class="sxs-lookup"><span data-stu-id="3d61b-117">Notice that both the delegate, `Del`, and the associated method, `MultiplyNumbers`, have the same signature</span></span>  
  
 [!code-csharp[csProgGuideDelegates#2](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_2.cs)]  
  
## <a name="example-2"></a><span data-ttu-id="3d61b-118">Örnek 2</span><span class="sxs-lookup"><span data-stu-id="3d61b-118">Example 2</span></span>  
 <span data-ttu-id="3d61b-119">Aşağıdaki örnekte, bir temsilci hem de statik olarak eşlenmiş ve örneği her belirli bilgiler yöntemleri ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="3d61b-119">In the following example, one delegate is mapped to both static and instance methods and returns specific information from each.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#3](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="3d61b-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3d61b-120">See Also</span></span>  
 [<span data-ttu-id="3d61b-121">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3d61b-121">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3d61b-122">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="3d61b-122">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="3d61b-123">Anonim yöntemler</span><span class="sxs-lookup"><span data-stu-id="3d61b-123">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
 [<span data-ttu-id="3d61b-124">Nasıl yapılır: temsilcileri (çok noktaya yayın temsilcileri) birleştirme</span><span class="sxs-lookup"><span data-stu-id="3d61b-124">How to: Combine Delegates (Multicast Delegates)</span></span>](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)  
 [<span data-ttu-id="3d61b-125">Olayları</span><span class="sxs-lookup"><span data-stu-id="3d61b-125">Events</span></span>](../../../csharp/programming-guide/events/index.md)
