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
ms.openlocfilehash: 329060e0c53178a9320be9a7cdff492d69917782
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211241"
---
# <a name="creating-event-handlers-in-windows-forms"></a><span data-ttu-id="c0039-102">Windows Forms'ta Olay İşleyicileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c0039-102">Creating Event Handlers in Windows Forms</span></span>

<span data-ttu-id="c0039-103">Bir olay işleyicisi, hangi eylemlerin bir ileti kuyruğu bir ileti alır ya da kullanıcı bir düğmeyi tıkladığında gibi bir olay meydana gerçekleştirilen belirler, kodunuzda bir yordamdır.</span><span class="sxs-lookup"><span data-stu-id="c0039-103">An event handler is a procedure in your code that determines what actions are performed when an event occurs, such as when the user clicks a button or a message queue receives a message.</span></span> <span data-ttu-id="c0039-104">Bir olay oluştuğunda, olay işleyicisi veya etkinliğin işleyicisi yürütülür.</span><span class="sxs-lookup"><span data-stu-id="c0039-104">When an event is raised, the event handler or handlers that receive the event are executed.</span></span> <span data-ttu-id="c0039-105">Olaylar için birden fazla işleyici atanabilir ve belirli olayları işleyen yöntemleri dinamik olarak değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c0039-105">Events can be assigned to multiple handlers, and the methods that handle particular events can be changed dynamically.</span></span> <span data-ttu-id="c0039-106">Olay işleyicilerini oluşturma Visual Studio'da Windows Form Tasarımcısı ' de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c0039-106">You can also use the Windows Forms Designer in Visual Studio to create event handlers.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="c0039-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="c0039-107">In This Section</span></span>

 <span data-ttu-id="c0039-108">[Olaylara genel bakış](events-overview-windows-forms.md)\\</span><span class="sxs-lookup"><span data-stu-id="c0039-108">[Events Overview](events-overview-windows-forms.md)\\</span></span>
 <span data-ttu-id="c0039-109">Olay modeli ve temsilciler rolünü açıklar.</span><span class="sxs-lookup"><span data-stu-id="c0039-109">Explains the event model and the role of delegates.</span></span>

 <span data-ttu-id="c0039-110">[Olay işleyicilerine genel bakış](event-handlers-overview-windows-forms.md)\\</span><span class="sxs-lookup"><span data-stu-id="c0039-110">[Event Handlers Overview](event-handlers-overview-windows-forms.md)\\</span></span>
 <span data-ttu-id="c0039-111">Olayların nasıl işleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="c0039-111">Describes how to handle events.</span></span>

 <span data-ttu-id="c0039-112">[Nasıl yapılır: Windows Forms için çalışma zamanında olay işleyicileri oluşturma](how-to-create-event-handlers-at-run-time-for-windows-forms.md)\\</span><span class="sxs-lookup"><span data-stu-id="c0039-112">[How to: Create Event Handlers at Run Time for Windows Forms](how-to-create-event-handlers-at-run-time-for-windows-forms.md)\\</span></span>
 <span data-ttu-id="c0039-113">Dinamik olarak sistem veya kullanıcı olaylarına yanıt için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c0039-113">Gives directions for responding to system or user events dynamically.</span></span>

 <span data-ttu-id="c0039-114">[Nasıl yapılır: Windows Forms'ta tek olay işleyicisine birden fazla olay bağlama](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)\\</span><span class="sxs-lookup"><span data-stu-id="c0039-114">[How to: Connect Multiple Events to a Single Event Handler in Windows Forms](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)\\</span></span>
 <span data-ttu-id="c0039-115">Olaylar ile birden çok denetim aynı işlevselliği atamak için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c0039-115">Gives directions for assigning the same functionality to multiple controls through events.</span></span>

 <span data-ttu-id="c0039-116">[Windows Forms'ta olayların sırası](order-of-events-in-windows-forms.md)\\</span><span class="sxs-lookup"><span data-stu-id="c0039-116">[Order of Events in Windows Forms](order-of-events-in-windows-forms.md)\\</span></span>
 <span data-ttu-id="c0039-117">Windows Forms denetimlerinde olay oluşturulan sırasını anlatır.</span><span class="sxs-lookup"><span data-stu-id="c0039-117">Describes the order in which events are raised in Windows Forms controls.</span></span>

 <span data-ttu-id="c0039-118">[Nasıl yapılır: Tasarımcıyı kullanarak olay işleyicileri oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)) olay işleyicilerini oluşturma Windows Form Tasarımcısı'nı kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="c0039-118">[How to: Create Event Handlers Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)) Describes how to use the Windows Forms Designer to create event handlers.</span></span>

## <a name="related-sections"></a><span data-ttu-id="c0039-119">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="c0039-119">Related Sections</span></span>

 <span data-ttu-id="c0039-120">[Olayları](../../standard/events/index.md)\\</span><span class="sxs-lookup"><span data-stu-id="c0039-120">[Events](../../standard/events/index.md)\\</span></span>
 <span data-ttu-id="c0039-121">Kullanarak olaylar oluşturma ve işleme hakkında konulara bağlantılar sağlar [!INCLUDE [dnprdnshort](../../../includes/dnprdnshort-md.md)\].</span><span class="sxs-lookup"><span data-stu-id="c0039-121">Provides links to topics on handling and raising events using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)\].</span></span>

 <span data-ttu-id="c0039-122">[Basic'de devralınmış olay işleyicileri Visual Basic sorunlarını giderme](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)\\</span><span class="sxs-lookup"><span data-stu-id="c0039-122">[Troubleshooting Inherited Event Handlers in Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)\\</span></span>
 <span data-ttu-id="c0039-123">Devralınan bileşenler olay işleyicileri ile oluşabilecek genel sorunları listeler.</span><span class="sxs-lookup"><span data-stu-id="c0039-123">Lists common issues that occur with event handlers in inherited components.</span></span>
