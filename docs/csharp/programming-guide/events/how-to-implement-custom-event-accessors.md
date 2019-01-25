---
title: 'Nasıl yapılır: -Özel olay erişimcilerini uygulama C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
ms.openlocfilehash: cdae5222cfe435142d93f222d140bd41ecf2c5c1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643487"
---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a><span data-ttu-id="5627d-102">Nasıl yapılır: Özel olay erişimcilerini uygulama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="5627d-102">How to: Implement Custom Event Accessors (C# Programming Guide)</span></span>
<span data-ttu-id="5627d-103">Özel bir tür içinde bildirildiği için yalnızca gelen sınıfın içinden çağrılabilen çok noktaya yayın temsilci bir olaydır.</span><span class="sxs-lookup"><span data-stu-id="5627d-103">An event is a special kind of multicast delegate that can only be invoked from within the class that  it is declared in.</span></span> <span data-ttu-id="5627d-104">İstemci kodu, olay başlatıldığında, çağrılması gereken bir yönteme başvuru sağlayarak olaya abone olur.</span><span class="sxs-lookup"><span data-stu-id="5627d-104">Client code subscribes to the event by providing a reference to a method that should be invoked when the event is fired.</span></span> <span data-ttu-id="5627d-105">Bu yöntemler, olay erişimcileri adlı dışında özellik erişimcileri, benzer olay erişimcileri aracılığıyla temsilcinin çağırma listesine eklenir `add` ve `remove`.</span><span class="sxs-lookup"><span data-stu-id="5627d-105">These methods are added to the delegate's invocation list through event accessors, which resemble property accessors, except that event accessors are named `add` and `remove`.</span></span> <span data-ttu-id="5627d-106">Çoğu durumda, özel olay erişimcilerini sağlamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="5627d-106">In most cases, you do not have to supply custom event accessors.</span></span> <span data-ttu-id="5627d-107">Derleyici, kodunuzda hiçbir özel olay erişimcilerini sağlandığında, bunları otomatik olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="5627d-107">When no custom event accessors are supplied in your code, the compiler will add them automatically.</span></span> <span data-ttu-id="5627d-108">Ancak, bazı durumlarda özel davranış sağlamanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="5627d-108">However, in some cases you may have to provide custom behavior.</span></span> <span data-ttu-id="5627d-109">Böyle bir durumda konu başlığında gösterilen [nasıl yapılır:  Arabirim olaylarını uygulama](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).</span><span class="sxs-lookup"><span data-stu-id="5627d-109">One such case is shown in the topic [How to:  Implement Interface Events](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5627d-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="5627d-110">Example</span></span>  
 <span data-ttu-id="5627d-111">Aşağıdaki örnek, özel uygulamak gösterilmektedir ekleme ve kaldırma olay erişimcileri.</span><span class="sxs-lookup"><span data-stu-id="5627d-111">The following example shows how to implement custom add and remove event accessors.</span></span> <span data-ttu-id="5627d-112">Erişimciler içinde herhangi bir kod birbirinin yerine kullanabilir, ancak olayı ekleyin veya yeni bir olay işleyicisi yöntemi'ı kaldırmadan önce kilit öneririz.</span><span class="sxs-lookup"><span data-stu-id="5627d-112">Although you can substitute any code inside the accessors, we recommend that you lock the event before you add or remove a new event handler method.</span></span>  
  
[!code-csharp[IDrawingObject.OnDraw](codesnippet/CSharp/how-to-implement-interface-events_1.cs#IDrawingObjectOnDraw)]  
  
## <a name="see-also"></a><span data-ttu-id="5627d-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5627d-113">See also</span></span>

- [<span data-ttu-id="5627d-114">Olaylar</span><span class="sxs-lookup"><span data-stu-id="5627d-114">Events</span></span>](../../../csharp/programming-guide/events/index.md)
- [<span data-ttu-id="5627d-115">event</span><span class="sxs-lookup"><span data-stu-id="5627d-115">event</span></span>](../../../csharp/language-reference/keywords/event.md)
