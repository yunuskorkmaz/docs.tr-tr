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
ms.openlocfilehash: 6b1d146dfd9d51641bc9eb5d8be4cd2508c223a1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963487"
---
# <a name="creating-event-handlers-in-windows-forms"></a><span data-ttu-id="ac297-102">Windows Forms'ta Olay İşleyicileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ac297-102">Creating Event Handlers in Windows Forms</span></span>

<span data-ttu-id="ac297-103">Olay işleyicisi, bir olay gerçekleştiğinde, kullanıcının bir düğmeye tıkladığı veya ileti sırasının bir ileti aldığı durumlarda olduğu gibi, hangi eylemlerin gerçekleştirileceğini belirleyen kodunuzda bir yordamdır.</span><span class="sxs-lookup"><span data-stu-id="ac297-103">An event handler is a procedure in your code that determines what actions are performed when an event occurs, such as when the user clicks a button or a message queue receives a message.</span></span> <span data-ttu-id="ac297-104">Bir olay ortaya çıktığında olayı alan olay işleyicisi veya işleyiciler yürütülür.</span><span class="sxs-lookup"><span data-stu-id="ac297-104">When an event is raised, the event handler or handlers that receive the event are executed.</span></span> <span data-ttu-id="ac297-105">Olaylar birden çok işleyicilere atanabilir ve belirli olayları işleyen yöntemler dinamik olarak değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="ac297-105">Events can be assigned to multiple handlers, and the methods that handle particular events can be changed dynamically.</span></span> <span data-ttu-id="ac297-106">Olay işleyicileri oluşturmak için Visual Studio 'daki Windows Form Tasarımcısı de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac297-106">You can also use the Windows Forms Designer in Visual Studio to create event handlers.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="ac297-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="ac297-107">In This Section</span></span>

 <span data-ttu-id="ac297-108">[Olaylara genel bakış](events-overview-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="ac297-108">[Events Overview](events-overview-windows-forms.md)</span></span>\
 <span data-ttu-id="ac297-109">Olay modelini ve temsilcilerin rolünü açıklar.</span><span class="sxs-lookup"><span data-stu-id="ac297-109">Explains the event model and the role of delegates.</span></span>

 <span data-ttu-id="ac297-110">[Olay Işleyicilerine genel bakış](event-handlers-overview-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="ac297-110">[Event Handlers Overview](event-handlers-overview-windows-forms.md)</span></span>\
 <span data-ttu-id="ac297-111">Olayların nasıl işleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="ac297-111">Describes how to handle events.</span></span>

 <span data-ttu-id="ac297-112">[Nasıl yapılır: Windows Forms için çalışma zamanında olay Işleyicileri oluştur](how-to-create-event-handlers-at-run-time-for-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="ac297-112">[How to: Create Event Handlers at Run Time for Windows Forms](how-to-create-event-handlers-at-run-time-for-windows-forms.md)</span></span>\
 <span data-ttu-id="ac297-113">Sistem veya Kullanıcı olaylarına dinamik olarak yanıt vermek için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac297-113">Gives directions for responding to system or user events dynamically.</span></span>

 <span data-ttu-id="ac297-114">[Nasıl yapılır: Birden çok olayı Windows Forms bir tek olay Işleyicisine bağlama](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="ac297-114">[How to: Connect Multiple Events to a Single Event Handler in Windows Forms](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)</span></span>\
 <span data-ttu-id="ac297-115">Olaylar aracılığıyla birden çok denetime aynı işlevselliği atamaya yönelik yönergeler verir.</span><span class="sxs-lookup"><span data-stu-id="ac297-115">Gives directions for assigning the same functionality to multiple controls through events.</span></span>

 <span data-ttu-id="ac297-116">[Windows Forms olayların sırası](order-of-events-in-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="ac297-116">[Order of Events in Windows Forms](order-of-events-in-windows-forms.md)</span></span>\
 <span data-ttu-id="ac297-117">Windows Forms Denetimlerinde olayların oluşturulduğu sırayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="ac297-117">Describes the order in which events are raised in Windows Forms controls.</span></span>

 <span data-ttu-id="ac297-118">[Nasıl yapılır: Tasarımcı](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)) kullanarak olay işleyicileri oluşturma Windows Form Tasarımcısı olay işleyicileri oluşturmak için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="ac297-118">[How to: Create Event Handlers Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)) Describes how to use the Windows Forms Designer to create event handlers.</span></span>

## <a name="related-sections"></a><span data-ttu-id="ac297-119">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="ac297-119">Related Sections</span></span>

 <span data-ttu-id="ac297-120">[Olayları](../../standard/events/index.md)</span><span class="sxs-lookup"><span data-stu-id="ac297-120">[Events](../../standard/events/index.md)</span></span>\
 <span data-ttu-id="ac297-121">.NET Framework kullanarak olayları işleme ve işlemeye yönelik konuların bağlantılarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac297-121">Provides links to topics on handling and raising events using the .NET Framework.</span></span>

 <span data-ttu-id="ac297-122">[Visual Basic devralınan olay Işleyicileriyle ilgili sorunları giderme](../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)</span><span class="sxs-lookup"><span data-stu-id="ac297-122">[Troubleshooting Inherited Event Handlers in Visual Basic](../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)</span></span>\
 <span data-ttu-id="ac297-123">Devralınan bileşenlerde olay işleyicileriyle gerçekleşen yaygın sorunları listeler.</span><span class="sxs-lookup"><span data-stu-id="ac297-123">Lists common issues that occur with event handlers in inherited components.</span></span>
