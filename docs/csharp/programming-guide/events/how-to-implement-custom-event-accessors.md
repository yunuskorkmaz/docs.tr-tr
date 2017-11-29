---
title: "Nasıl yapılır: Özel Olay Erişimcilerini Uygulama (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
caps.latest.revision: "7"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3ff5fedeeaa427bb62991f9b406c167647dc376d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a><span data-ttu-id="d9b6c-102">Nasıl yapılır: Özel Olay Erişimcilerini Uygulama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="d9b6c-102">How to: Implement Custom Event Accessors (C# Programming Guide)</span></span>
<span data-ttu-id="d9b6c-103">Bir olay bir özel olarak bildirilen için yalnızca gelen sınıfı içinde çağrılabilir çok noktaya yayın temsilci türüdür.</span><span class="sxs-lookup"><span data-stu-id="d9b6c-103">An event is a special kind of multicast delegate that can only be invoked from within the class that  it is declared in.</span></span> <span data-ttu-id="d9b6c-104">İstemci kodu, olay başlatıldığında, çağrılması gereken bir yöntem başvuru sağlayarak olaya abone olur.</span><span class="sxs-lookup"><span data-stu-id="d9b6c-104">Client code subscribes to the event by providing a reference to a method that should be invoked when the event is fired.</span></span> <span data-ttu-id="d9b6c-105">Bu yöntemler olay erişimcileri adlı dışında bu özellik erişimcisi benzer olay erişimcileri aracılığıyla temsilcinin çağırma listesine eklenir `add` ve `remove`.</span><span class="sxs-lookup"><span data-stu-id="d9b6c-105">These methods are added to the delegate's invocation list through event accessors, which resemble property accessors, except that event accessors are named `add` and `remove`.</span></span> <span data-ttu-id="d9b6c-106">Çoğu durumda, özel olay erişimcilerini sağlamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="d9b6c-106">In most cases, you do not have to supply custom event accessors.</span></span> <span data-ttu-id="d9b6c-107">Derleyici hiçbir özel olay erişimcilerini kodunuzda sağlandığında, bunları otomatik olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="d9b6c-107">When no custom event accessors are supplied in your code, the compiler will add them automatically.</span></span> <span data-ttu-id="d9b6c-108">Ancak, bazı durumlarda özel davranışı sağlamak olabilir.</span><span class="sxs-lookup"><span data-stu-id="d9b6c-108">However, in some cases you may have to provide custom behavior.</span></span> <span data-ttu-id="d9b6c-109">Böyle bir durumda konusunda gösterilen [nasıl yapılır: arabirim olaylarını uygulama](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).</span><span class="sxs-lookup"><span data-stu-id="d9b6c-109">One such case is shown in the topic [How to:  Implement Interface Events](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9b6c-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="d9b6c-110">Example</span></span>  
 <span data-ttu-id="d9b6c-111">Aşağıdaki örnek, özel uygulamak gösterilmiştir ekleme ve kaldırma olay erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="d9b6c-111">The following example shows how to implement custom add and remove event accessors.</span></span> <span data-ttu-id="d9b6c-112">Erişimciler içinde herhangi bir kod yerine kullanabilirsiniz, ancak ekleyin veya yeni bir olay işleyicisi yöntemi kaldırmadan önce olay kilitlemek öneririz.</span><span class="sxs-lookup"><span data-stu-id="d9b6c-112">Although you can substitute any code inside the accessors, we recommend that you lock the event before you add or remove a new event handler method.</span></span>  
  
```  
event EventHandler IDrawingObject.OnDraw  
        {  
            add  
            {  
                lock (PreDrawEvent)  
                {  
                    PreDrawEvent += value;  
                }  
            }  
            remove  
            {  
                lock (PreDrawEvent)  
                {  
                    PreDrawEvent -= value;  
                }  
            }  
        }  
```  
  
## <a name="see-also"></a><span data-ttu-id="d9b6c-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d9b6c-113">See Also</span></span>  
 [<span data-ttu-id="d9b6c-114">Olayları</span><span class="sxs-lookup"><span data-stu-id="d9b6c-114">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
 [<span data-ttu-id="d9b6c-115">Olay</span><span class="sxs-lookup"><span data-stu-id="d9b6c-115">event</span></span>](../../../csharp/language-reference/keywords/event.md)
