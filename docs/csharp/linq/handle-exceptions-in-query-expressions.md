---
title: "Sorgu ifadelerinde özel durumları işleme"
description: "Sorgu ifadelerinde özel durumları nasıl ele alınacağını."
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 2bf0c397-13fb-4f68-bc2b-531c6c88a167
ms.openlocfilehash: 376bd461bfeb51653471fd374a2215aa15872976
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2017
---
# <a name="handle-exceptions-in-query-expressions"></a><span data-ttu-id="92143-104">Sorgu ifadelerinde özel durumları işleme</span><span class="sxs-lookup"><span data-stu-id="92143-104">Handle exceptions in query expressions</span></span>

<span data-ttu-id="92143-105">Bir sorgu ifadesi bağlamında herhangi bir yöntemini çağırmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="92143-105">It is possible to call any method in the context of a query expression.</span></span> <span data-ttu-id="92143-106">Ancak, veri kaynağı içeriğini değiştirme veya bir özel durum atma gibi bir yan etkisi oluşturabilirsiniz bir sorgu ifadesinde herhangi bir yöntemini çağırmadan kaçının öneririz.</span><span class="sxs-lookup"><span data-stu-id="92143-106">However, we recommend that you avoid calling any method in a query expression that can create a side effect such as modifying the contents of the data source or throwing an exception.</span></span> <span data-ttu-id="92143-107">Bu örnek, genel özel durum işleme .NET Framework yönergeleri ihlal etmeden sorgu ifadesinde yöntemlerini çağırdığınızda özel durumlarını oluşturma önlemek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="92143-107">This example shows how to avoid raising exceptions when you call methods in a query expression without violating the general .NET Framework guidelines on exception handling.</span></span> <span data-ttu-id="92143-108">Verilen bir bağlamda neden oluşturulacaktır anladığınızda, belirli bir özel durum yakalamak için kabul edilebilir bu yönergeleri durumu.</span><span class="sxs-lookup"><span data-stu-id="92143-108">Those guidelines state that it is acceptable to catch a specific exception when you understand why it will be thrown in a given context.</span></span> <span data-ttu-id="92143-109">Daha fazla bilgi için bkz: [özel durumlar için en iyi uygulamaları](../../standard/exceptions/best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="92143-109">For more information, see [Best Practices for Exceptions](../../standard/exceptions/best-practices-for-exceptions.md).</span></span>  
  
 <span data-ttu-id="92143-110">Son örnek bir sorgu yürütülmesi sırasında bir özel durum gerekir, bu gibi durumlarda nasıl ele alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="92143-110">The final example shows how to handle those cases when you must throw an exception during execution of a query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92143-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="92143-111">Example</span></span>  

 <span data-ttu-id="92143-112">Aşağıdaki örnek, özel durum kodu bir sorgu ifadesi dışında işleme taşımak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="92143-112">The following example shows how to move exception handling code outside a query expression.</span></span> <span data-ttu-id="92143-113">Yalnızca yöntemi değişkenlerin sorguya yerel dayanmayacak mümkün olur.</span><span class="sxs-lookup"><span data-stu-id="92143-113">This is only possible when the method does not depend on any variables local to the query.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#10](../../../samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="92143-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="92143-114">Example</span></span> 

 <span data-ttu-id="92143-115">Bazı durumlarda, sorgu yürütme hemen durdurmak için en iyi sorgu içinde oluşturulan bir özel durum yanıta olabilir.</span><span class="sxs-lookup"><span data-stu-id="92143-115">In some cases, the best response to an exception that is thrown from within a query might be to stop the query execution immediately.</span></span> <span data-ttu-id="92143-116">Aşağıdaki örnek alanından bir sorgu gövdesi içinde durum özel durumları işleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="92143-116">The following example shows how to handle exceptions that might be thrown from inside a query body.</span></span> <span data-ttu-id="92143-117">Varsayımında `SomeMethodThatMightThrow` durdurmak için sorgu yürütme gerektiren bir özel durum neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="92143-117">Assume that `SomeMethodThatMightThrow` can potentially cause an exception that requires the query execution to stop.</span></span>  
  
 <span data-ttu-id="92143-118">Unutmayın `try` blok barındırır `foreach` döngü ve sorgunun kendisini değil.</span><span class="sxs-lookup"><span data-stu-id="92143-118">Note that the `try` block encloses the `foreach` loop, and not the query itself.</span></span> <span data-ttu-id="92143-119">Bunun nedeni, `foreach` döngü başlayacağı sorgu gerçekte yürütüldüğünde noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="92143-119">This is because the `foreach` loop is the point at which the query is actually executed.</span></span> <span data-ttu-id="92143-120">Daha fazla bilgi için bkz: [LINQ sorgularına giriş](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="92143-120">For more information, see [Introduction to LINQ queries](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 [!code-csharp[csProgGuideLINQ#12](../../../samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_2.cs)]  
  

## <a name="see-also"></a><span data-ttu-id="92143-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="92143-121">See Also</span></span>  
 [<span data-ttu-id="92143-122">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="92143-122">LINQ query expressions</span></span>](index.md)
