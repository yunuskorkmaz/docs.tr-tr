---
title: Windows Forms'ta Olay İşleyicileri Oluşturma
ms.date: 03/30/2017
helpviewer_keywords:
- event handling [Windows Forms]
- Windows Forms controls, event handling
- Windows Forms, event handling
- events [Windows Forms], event handlers
- event handlers [Windows Forms]
ms.assetid: 6514e530-c6b8-489c-a8d2-eda7b7072701
ms.openlocfilehash: 96697fa54b569b6d1ce092ebfc76ef593f2ac66f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33539160"
---
# <a name="creating-event-handlers-in-windows-forms"></a><span data-ttu-id="b2d88-102">Windows Forms'ta Olay İşleyicileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b2d88-102">Creating Event Handlers in Windows Forms</span></span>
<span data-ttu-id="b2d88-103">Olay işleyici hangi eylemlerin bir ileti sırası bir ileti alır veya bir olay oluşur, kullanıcı bir düğmesine tıkladığında gibi gerçekleştirilir belirler, kodunuzda bir yordamdır.</span><span class="sxs-lookup"><span data-stu-id="b2d88-103">An event handler is a procedure in your code that determines what actions are performed when an event occurs, such as when the user clicks a button or a message queue receives a message.</span></span> <span data-ttu-id="b2d88-104">Bir olay oluşturulduğunda, olay işleyicisi veya olay alırsınız işleyicileri yürütülür.</span><span class="sxs-lookup"><span data-stu-id="b2d88-104">When an event is raised, the event handler or handlers that receive the event are executed.</span></span> <span data-ttu-id="b2d88-105">Olaylar için birden çok işleyici atanabilir ve belirli olayları işlemek yöntemleri dinamik olarak değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="b2d88-105">Events can be assigned to multiple handlers, and the methods that handle particular events can be changed dynamically.</span></span> <span data-ttu-id="b2d88-106">Windows Form Tasarımcısı, olay işleyicileri oluşturmak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2d88-106">You can also use the Windows Forms Designer to create event handlers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b2d88-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="b2d88-107">In This Section</span></span>  
 [<span data-ttu-id="b2d88-108">Olaylara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b2d88-108">Events Overview</span></span>](../../../docs/framework/winforms/events-overview-windows-forms.md)  
 <span data-ttu-id="b2d88-109">Olay modeli ve temsilciler rolünü açıklar.</span><span class="sxs-lookup"><span data-stu-id="b2d88-109">Explains the event model and the role of delegates.</span></span>  
  
 [<span data-ttu-id="b2d88-110">Olay İşleyicilerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b2d88-110">Event Handlers Overview</span></span>](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)  
 <span data-ttu-id="b2d88-111">Olayları işlemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="b2d88-111">Describes how to handle events.</span></span>  
  
 [<span data-ttu-id="b2d88-112">Nasıl yapılır: Windows Forms için Çalışma Zamanındaki Olay İşleyicileri</span><span class="sxs-lookup"><span data-stu-id="b2d88-112">How to: Create Event Handlers at Run Time for Windows Forms</span></span>](../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md)  
 <span data-ttu-id="b2d88-113">Dinamik olarak sistem veya kullanıcı olaylarına yanıt için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b2d88-113">Gives directions for responding to system or user events dynamically.</span></span>  
  
 [<span data-ttu-id="b2d88-114">Nasıl yapılır: Windows Forms'ta Tek Olay İşleyicisine Birden Fazla Olay Bağlama</span><span class="sxs-lookup"><span data-stu-id="b2d88-114">How to: Connect Multiple Events to a Single Event Handler in Windows Forms</span></span>](../../../docs/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)  
 <span data-ttu-id="b2d88-115">Birden çok denetim olaylar ile aynı işlevselliği atamak için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b2d88-115">Gives directions for assigning the same functionality to multiple controls through events.</span></span>  
  
 [<span data-ttu-id="b2d88-116">Windows Forms'ta Olayların Sırası</span><span class="sxs-lookup"><span data-stu-id="b2d88-116">Order of Events in Windows Forms</span></span>](../../../docs/framework/winforms/order-of-events-in-windows-forms.md)  
 <span data-ttu-id="b2d88-117">Windows Forms denetimlerindeki olaylar ortaya sırasını açıklar.</span><span class="sxs-lookup"><span data-stu-id="b2d88-117">Describes the order in which events are raised in Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="b2d88-118">Nasıl yapılır: Tasarımcı kullanarak olay işleyicileri oluşturma</span><span class="sxs-lookup"><span data-stu-id="b2d88-118">How to: Create Event Handlers Using the Designer</span></span>](http://msdn.microsoft.com/library/8461e9b8-14e8-406f-936e-3726732b23d2)  
 <span data-ttu-id="b2d88-119">Windows Form Tasarımcısı olay işleyicileri oluşturmak için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="b2d88-119">Describes how to use the Windows Forms Designer to create event handlers.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b2d88-120">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="b2d88-120">Related Sections</span></span>  
 [<span data-ttu-id="b2d88-121">Olaylar</span><span class="sxs-lookup"><span data-stu-id="b2d88-121">Events</span></span>](../../../docs/standard/events/index.md)  
 <span data-ttu-id="b2d88-122">Kullanarak olaylar oluşturma ve işleme üzerinde konulara bağlantılar sağlanır [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b2d88-122">Provides links to topics on handling and raising events using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span>  
  
 [<span data-ttu-id="b2d88-123">Devralınmış olay işleyicileri Visual Basic sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="b2d88-123">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 <span data-ttu-id="b2d88-124">Olay işleyicileri devralınan bileşenlerinde yazılımında ortak sorunları listeler.</span><span class="sxs-lookup"><span data-stu-id="b2d88-124">Lists common issues that occur with event handlers in inherited components.</span></span>
