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
ms.openlocfilehash: f969769725ae099ddf477fd11efb03277a555fa6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967108"
---
# <a name="creating-event-handlers-in-windows-forms"></a><span data-ttu-id="b9204-102">Windows Forms'ta Olay İşleyicileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b9204-102">Creating Event Handlers in Windows Forms</span></span>
<span data-ttu-id="b9204-103">Bir olay işleyicisi, hangi eylemlerin bir ileti kuyruğu bir ileti alır ya da kullanıcı bir düğmeyi tıkladığında gibi bir olay meydana gerçekleştirilen belirler, kodunuzda bir yordamdır.</span><span class="sxs-lookup"><span data-stu-id="b9204-103">An event handler is a procedure in your code that determines what actions are performed when an event occurs, such as when the user clicks a button or a message queue receives a message.</span></span> <span data-ttu-id="b9204-104">Bir olay oluştuğunda, olay işleyicisi veya etkinliğin işleyicisi yürütülür.</span><span class="sxs-lookup"><span data-stu-id="b9204-104">When an event is raised, the event handler or handlers that receive the event are executed.</span></span> <span data-ttu-id="b9204-105">Olaylar için birden fazla işleyici atanabilir ve belirli olayları işleyen yöntemleri dinamik olarak değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="b9204-105">Events can be assigned to multiple handlers, and the methods that handle particular events can be changed dynamically.</span></span> <span data-ttu-id="b9204-106">Windows Form Tasarımcısı, olay işleyicileri oluşturma için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b9204-106">You can also use the Windows Forms Designer to create event handlers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b9204-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="b9204-107">In This Section</span></span>  
 [<span data-ttu-id="b9204-108">Olaylara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b9204-108">Events Overview</span></span>](events-overview-windows-forms.md)  
 <span data-ttu-id="b9204-109">Olay modeli ve temsilciler rolünü açıklar.</span><span class="sxs-lookup"><span data-stu-id="b9204-109">Explains the event model and the role of delegates.</span></span>  
  
 [<span data-ttu-id="b9204-110">Olay İşleyicilerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b9204-110">Event Handlers Overview</span></span>](event-handlers-overview-windows-forms.md)  
 <span data-ttu-id="b9204-111">Olayların nasıl işleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b9204-111">Describes how to handle events.</span></span>  
  
 [<span data-ttu-id="b9204-112">Nasıl yapılır: Windows Forms için çalışma zamanında olay işleyicileri oluşturma</span><span class="sxs-lookup"><span data-stu-id="b9204-112">How to: Create Event Handlers at Run Time for Windows Forms</span></span>](how-to-create-event-handlers-at-run-time-for-windows-forms.md)  
 <span data-ttu-id="b9204-113">Dinamik olarak sistem veya kullanıcı olaylarına yanıt için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b9204-113">Gives directions for responding to system or user events dynamically.</span></span>  
  
 [<span data-ttu-id="b9204-114">Nasıl yapılır: Windows Forms'ta tek olay işleyicisine birden fazla olay bağlama</span><span class="sxs-lookup"><span data-stu-id="b9204-114">How to: Connect Multiple Events to a Single Event Handler in Windows Forms</span></span>](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)  
 <span data-ttu-id="b9204-115">Olaylar ile birden çok denetim aynı işlevselliği atamak için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b9204-115">Gives directions for assigning the same functionality to multiple controls through events.</span></span>  
  
 [<span data-ttu-id="b9204-116">Windows Forms'ta Olayların Sırası</span><span class="sxs-lookup"><span data-stu-id="b9204-116">Order of Events in Windows Forms</span></span>](order-of-events-in-windows-forms.md)  
 <span data-ttu-id="b9204-117">Windows Forms denetimlerinde olay oluşturulan sırasını anlatır.</span><span class="sxs-lookup"><span data-stu-id="b9204-117">Describes the order in which events are raised in Windows Forms controls.</span></span>  
  
 <span data-ttu-id="b9204-118">[Nasıl yapılır: Tasarımcıyı kullanarak olay işleyicileri oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b9204-118">[How to: Create Event Handlers Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100))</span></span>  
 <span data-ttu-id="b9204-119">Olay işleyicilerini oluşturma Windows Form Tasarımcısı'nı kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="b9204-119">Describes how to use the Windows Forms Designer to create event handlers.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b9204-120">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="b9204-120">Related Sections</span></span>  
 [<span data-ttu-id="b9204-121">Olaylar</span><span class="sxs-lookup"><span data-stu-id="b9204-121">Events</span></span>](../../standard/events/index.md)  
 <span data-ttu-id="b9204-122">Kullanarak olaylar oluşturma ve işleme hakkında konulara bağlantılar sağlar [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b9204-122">Provides links to topics on handling and raising events using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span>  
  
 [<span data-ttu-id="b9204-123">Basic'de devralınmış olay işleyicileri Visual Basic sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="b9204-123">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 <span data-ttu-id="b9204-124">Devralınan bileşenler olay işleyicileri ile oluşabilecek genel sorunları listeler.</span><span class="sxs-lookup"><span data-stu-id="b9204-124">Lists common issues that occur with event handlers in inherited components.</span></span>
