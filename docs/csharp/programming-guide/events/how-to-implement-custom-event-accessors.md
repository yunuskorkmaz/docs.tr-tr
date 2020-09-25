---
title: Özel olay erişimcileri uygulama-C# Programlama Kılavuzu
description: Özel olay erişimcilerinin nasıl uygulanacağını öğrenin. Bir kod örneğine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 07/20/2015
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
ms.openlocfilehash: 41c9bd255bf66cd914982b6044c4acaef66b8fcf
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167567"
---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a><span data-ttu-id="1789f-104">Özel olay erişimcilerini uygulama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="1789f-104">How to implement custom event accessors (C# Programming Guide)</span></span>

<span data-ttu-id="1789f-105">Bir olay, yalnızca içinde bildirildiği sınıftan çağrılabilir olan özel bir çok noktaya yayın temsilcisi türüdür.</span><span class="sxs-lookup"><span data-stu-id="1789f-105">An event is a special kind of multicast delegate that can only be invoked from within the class that  it is declared in.</span></span> <span data-ttu-id="1789f-106">İstemci kodu olay harekete geçirildiğinde çağrılması gereken bir yönteme başvuru sağlayarak olaya abone olur.</span><span class="sxs-lookup"><span data-stu-id="1789f-106">Client code subscribes to the event by providing a reference to a method that should be invoked when the event is fired.</span></span> <span data-ttu-id="1789f-107">Bu yöntemler, olay erişimcileri, ve ' nin adlandırılmasının dışında, özellik erişimcilerine benzeyen, temsilcinin çağrı listesine eklenir `add` `remove` .</span><span class="sxs-lookup"><span data-stu-id="1789f-107">These methods are added to the delegate's invocation list through event accessors, which resemble property accessors, except that event accessors are named `add` and `remove`.</span></span> <span data-ttu-id="1789f-108">Çoğu durumda, özel olay erişimcileri sağlamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="1789f-108">In most cases, you do not have to supply custom event accessors.</span></span> <span data-ttu-id="1789f-109">Kodunuzda hiçbir özel olay erişimcisi sağlanmadığında, derleyici bunları otomatik olarak ekler.</span><span class="sxs-lookup"><span data-stu-id="1789f-109">When no custom event accessors are supplied in your code, the compiler will add them automatically.</span></span> <span data-ttu-id="1789f-110">Ancak, bazı durumlarda özel davranış sağlamanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="1789f-110">However, in some cases you may have to provide custom behavior.</span></span> <span data-ttu-id="1789f-111">Bu tür bir durum, [arabirim olaylarının nasıl uygulanacağı](./how-to-implement-interface-events.md)konusunda gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1789f-111">One such case is shown in the topic [How to implement interface events](./how-to-implement-interface-events.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="1789f-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="1789f-112">Example</span></span>  

 <span data-ttu-id="1789f-113">Aşağıdaki örnek, özel ekleme ve kaldırma olay erişimcilerinin nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1789f-113">The following example shows how to implement custom add and remove event accessors.</span></span> <span data-ttu-id="1789f-114">Erişimcilerinin içinde herhangi bir kodu değiştirebilseniz de, yeni bir olay işleyici yöntemi eklemeden veya kaldırmadan önce olayı kilitlemenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="1789f-114">Although you can substitute any code inside the accessors, we recommend that you lock the event before you add or remove a new event handler method.</span></span>  
  
[!code-csharp[IDrawingObject.OnDraw](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#IDrawingObjectOnDraw)]  
  
## <a name="see-also"></a><span data-ttu-id="1789f-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1789f-115">See also</span></span>

- [<span data-ttu-id="1789f-116">Olaylar</span><span class="sxs-lookup"><span data-stu-id="1789f-116">Events</span></span>](./index.md)
- [<span data-ttu-id="1789f-117">olay</span><span class="sxs-lookup"><span data-stu-id="1789f-117">event</span></span>](../../language-reference/keywords/event.md)
