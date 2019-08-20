---
title: 'Nasıl yapılır: Özel olay erişimcileri uygulama- C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
ms.openlocfilehash: 4eaf8b4c3038d07d5b0fc021e21c7f1a2de85d74
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590534"
---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a><span data-ttu-id="e1d52-102">Nasıl yapılır: Özel olay erişimcileri uygulama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="e1d52-102">How to: Implement Custom Event Accessors (C# Programming Guide)</span></span>
<span data-ttu-id="e1d52-103">Bir olay, yalnızca içinde bildirildiği sınıftan çağrılabilir olan özel bir çok noktaya yayın temsilcisi türüdür.</span><span class="sxs-lookup"><span data-stu-id="e1d52-103">An event is a special kind of multicast delegate that can only be invoked from within the class that  it is declared in.</span></span> <span data-ttu-id="e1d52-104">İstemci kodu olay harekete geçirildiğinde çağrılması gereken bir yönteme başvuru sağlayarak olaya abone olur.</span><span class="sxs-lookup"><span data-stu-id="e1d52-104">Client code subscribes to the event by providing a reference to a method that should be invoked when the event is fired.</span></span> <span data-ttu-id="e1d52-105">Bu yöntemler, olay erişimcileri, ve `add` `remove`' nin adlandırılmasının dışında, özellik erişimcilerine benzeyen, temsilcinin çağrı listesine eklenir.</span><span class="sxs-lookup"><span data-stu-id="e1d52-105">These methods are added to the delegate's invocation list through event accessors, which resemble property accessors, except that event accessors are named `add` and `remove`.</span></span> <span data-ttu-id="e1d52-106">Çoğu durumda, özel olay erişimcileri sağlamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="e1d52-106">In most cases, you do not have to supply custom event accessors.</span></span> <span data-ttu-id="e1d52-107">Kodunuzda hiçbir özel olay erişimcisi sağlanmadığında, derleyici bunları otomatik olarak ekler.</span><span class="sxs-lookup"><span data-stu-id="e1d52-107">When no custom event accessors are supplied in your code, the compiler will add them automatically.</span></span> <span data-ttu-id="e1d52-108">Ancak, bazı durumlarda özel davranış sağlamanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="e1d52-108">However, in some cases you may have to provide custom behavior.</span></span> <span data-ttu-id="e1d52-109">Böyle bir durum söz konusu [şekilde gösterilmiştir:  Arabirim olaylarını](./how-to-implement-interface-events.md)uygulayın.</span><span class="sxs-lookup"><span data-stu-id="e1d52-109">One such case is shown in the topic [How to:  Implement Interface Events](./how-to-implement-interface-events.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1d52-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="e1d52-110">Example</span></span>  
 <span data-ttu-id="e1d52-111">Aşağıdaki örnek, özel ekleme ve kaldırma olay erişimcilerinin nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e1d52-111">The following example shows how to implement custom add and remove event accessors.</span></span> <span data-ttu-id="e1d52-112">Erişimcilerinin içinde herhangi bir kodu değiştirebilseniz de, yeni bir olay işleyici yöntemi eklemeden veya kaldırmadan önce olayı kilitlemenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="e1d52-112">Although you can substitute any code inside the accessors, we recommend that you lock the event before you add or remove a new event handler method.</span></span>  
  
[!code-csharp[IDrawingObject.OnDraw](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#IDrawingObjectOnDraw)]  
  
## <a name="see-also"></a><span data-ttu-id="e1d52-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1d52-113">See also</span></span>

- [<span data-ttu-id="e1d52-114">Olaylar</span><span class="sxs-lookup"><span data-stu-id="e1d52-114">Events</span></span>](./index.md)
- [<span data-ttu-id="e1d52-115">event</span><span class="sxs-lookup"><span data-stu-id="e1d52-115">event</span></span>](../../language-reference/keywords/event.md)
