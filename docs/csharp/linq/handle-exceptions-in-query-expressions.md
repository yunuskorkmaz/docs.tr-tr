---
title: Sorgu ifadelerinde özel durumları işleme
description: Sorgu ifadelerinde özel durumları nasıl ele alınacağını.
ms.date: 12/1/2016
ms.assetid: 2bf0c397-13fb-4f68-bc2b-531c6c88a167
ms.openlocfilehash: 691373fabeb3934ecc454cbc3b36a5f7bf477bee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33284857"
---
# <a name="handle-exceptions-in-query-expressions"></a><span data-ttu-id="f886f-103">Sorgu ifadelerinde özel durumları işleme</span><span class="sxs-lookup"><span data-stu-id="f886f-103">Handle exceptions in query expressions</span></span>

<span data-ttu-id="f886f-104">Bir sorgu ifadesi bağlamında herhangi bir yöntemini çağırmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="f886f-104">It is possible to call any method in the context of a query expression.</span></span> <span data-ttu-id="f886f-105">Ancak, veri kaynağı içeriğini değiştirme veya bir özel durum atma gibi bir yan etkisi oluşturabilirsiniz bir sorgu ifadesinde herhangi bir yöntemini çağırmadan kaçının öneririz.</span><span class="sxs-lookup"><span data-stu-id="f886f-105">However, we recommend that you avoid calling any method in a query expression that can create a side effect such as modifying the contents of the data source or throwing an exception.</span></span> <span data-ttu-id="f886f-106">Bu örnek, genel özel durum işleme .NET Framework yönergeleri ihlal etmeden sorgu ifadesinde yöntemlerini çağırdığınızda özel durumlarını oluşturma önlemek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f886f-106">This example shows how to avoid raising exceptions when you call methods in a query expression without violating the general .NET Framework guidelines on exception handling.</span></span> <span data-ttu-id="f886f-107">Verilen bir bağlamda neden oluşturulacaktır anladığınızda, belirli bir özel durum yakalamak için kabul edilebilir bu yönergeleri durumu.</span><span class="sxs-lookup"><span data-stu-id="f886f-107">Those guidelines state that it is acceptable to catch a specific exception when you understand why it will be thrown in a given context.</span></span> <span data-ttu-id="f886f-108">Daha fazla bilgi için bkz: [özel durumlar için en iyi uygulamaları](../../standard/exceptions/best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="f886f-108">For more information, see [Best Practices for Exceptions](../../standard/exceptions/best-practices-for-exceptions.md).</span></span>  
  
 <span data-ttu-id="f886f-109">Son örnek bir sorgu yürütülmesi sırasında bir özel durum gerekir, bu gibi durumlarda nasıl ele alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f886f-109">The final example shows how to handle those cases when you must throw an exception during execution of a query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f886f-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="f886f-110">Example</span></span>  

 <span data-ttu-id="f886f-111">Aşağıdaki örnek, özel durum kodu bir sorgu ifadesi dışında işleme taşımak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f886f-111">The following example shows how to move exception handling code outside a query expression.</span></span> <span data-ttu-id="f886f-112">Yalnızca yöntemi değişkenlerin sorguya yerel dayanmayacak mümkün olur.</span><span class="sxs-lookup"><span data-stu-id="f886f-112">This is only possible when the method does not depend on any variables local to the query.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#10](../../../samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="f886f-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="f886f-113">Example</span></span> 

 <span data-ttu-id="f886f-114">Bazı durumlarda, sorgu yürütme hemen durdurmak için en iyi sorgu içinde oluşturulan bir özel durum yanıta olabilir.</span><span class="sxs-lookup"><span data-stu-id="f886f-114">In some cases, the best response to an exception that is thrown from within a query might be to stop the query execution immediately.</span></span> <span data-ttu-id="f886f-115">Aşağıdaki örnek alanından bir sorgu gövdesi içinde durum özel durumları işleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="f886f-115">The following example shows how to handle exceptions that might be thrown from inside a query body.</span></span> <span data-ttu-id="f886f-116">Varsayımında `SomeMethodThatMightThrow` durdurmak için sorgu yürütme gerektiren bir özel durum neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="f886f-116">Assume that `SomeMethodThatMightThrow` can potentially cause an exception that requires the query execution to stop.</span></span>  
  
 <span data-ttu-id="f886f-117">Unutmayın `try` blok barındırır `foreach` döngü ve sorgunun kendisini değil.</span><span class="sxs-lookup"><span data-stu-id="f886f-117">Note that the `try` block encloses the `foreach` loop, and not the query itself.</span></span> <span data-ttu-id="f886f-118">Bunun nedeni, `foreach` döngü başlayacağı sorgu gerçekte yürütüldüğünde noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="f886f-118">This is because the `foreach` loop is the point at which the query is actually executed.</span></span> <span data-ttu-id="f886f-119">Daha fazla bilgi için bkz: [LINQ sorgularına giriş](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="f886f-119">For more information, see [Introduction to LINQ queries](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 [!code-csharp[csProgGuideLINQ#12](../../../samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_2.cs)]  
  

## <a name="see-also"></a><span data-ttu-id="f886f-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f886f-120">See Also</span></span>  
 [<span data-ttu-id="f886f-121">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="f886f-121">LINQ query expressions</span></span>](index.md)
