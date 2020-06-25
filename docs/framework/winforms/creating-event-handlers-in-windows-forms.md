---
title: Olay Işleyicileri oluşturma
description: Windows Forms içindeki olayların birden çok işleyicilerine nasıl atanabileceğini ve belirli olayları işleyen yöntemlerin dinamik olarak nasıl değiştirilebileceğini öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- event handling [Windows Forms]
- Windows Forms controls, event handling
- Windows Forms, event handling
- events [Windows Forms], event handlers
- event handlers [Windows Forms]
ms.assetid: 6514e530-c6b8-489c-a8d2-eda7b7072701
ms.openlocfilehash: 4dca198be69c200ea8dfc741a43801bf8f631b9d
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85326015"
---
# <a name="creating-event-handlers-in-windows-forms"></a><span data-ttu-id="ca352-103">Windows Forms'ta Olay İşleyicileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ca352-103">Creating Event Handlers in Windows Forms</span></span>

<span data-ttu-id="ca352-104">Olay işleyicisi, bir olay gerçekleştiğinde, kullanıcının bir düğmeye tıkladığı veya ileti sırasının bir ileti aldığı durumlarda olduğu gibi, hangi eylemlerin gerçekleştirileceğini belirleyen kodunuzda bir yordamdır.</span><span class="sxs-lookup"><span data-stu-id="ca352-104">An event handler is a procedure in your code that determines what actions are performed when an event occurs, such as when the user clicks a button or a message queue receives a message.</span></span> <span data-ttu-id="ca352-105">Bir olay ortaya çıktığında olayı alan olay işleyicisi veya işleyiciler yürütülür.</span><span class="sxs-lookup"><span data-stu-id="ca352-105">When an event is raised, the event handler or handlers that receive the event are executed.</span></span> <span data-ttu-id="ca352-106">Olaylar birden çok işleyicilere atanabilir ve belirli olayları işleyen yöntemler dinamik olarak değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="ca352-106">Events can be assigned to multiple handlers, and the methods that handle particular events can be changed dynamically.</span></span> <span data-ttu-id="ca352-107">Olay işleyicileri oluşturmak için Visual Studio 'daki Windows Form Tasarımcısı de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca352-107">You can also use the Windows Forms Designer in Visual Studio to create event handlers.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="ca352-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="ca352-108">In This Section</span></span>

 <span data-ttu-id="ca352-109">[Olaylara genel bakış](events-overview-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="ca352-109">[Events Overview](events-overview-windows-forms.md)</span></span>\
 <span data-ttu-id="ca352-110">Olay modelini ve temsilcilerin rolünü açıklar.</span><span class="sxs-lookup"><span data-stu-id="ca352-110">Explains the event model and the role of delegates.</span></span>

 <span data-ttu-id="ca352-111">[Olay Işleyicilerine genel bakış](event-handlers-overview-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="ca352-111">[Event Handlers Overview](event-handlers-overview-windows-forms.md)</span></span>\
 <span data-ttu-id="ca352-112">Olayların nasıl işleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="ca352-112">Describes how to handle events.</span></span>

 <span data-ttu-id="ca352-113">[Nasıl yapılır: Windows Forms için çalışma zamanında olay Işleyicileri oluşturma](how-to-create-event-handlers-at-run-time-for-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="ca352-113">[How to: Create Event Handlers at Run Time for Windows Forms](how-to-create-event-handlers-at-run-time-for-windows-forms.md)</span></span>\
 <span data-ttu-id="ca352-114">Sistem veya Kullanıcı olaylarına dinamik olarak yanıt vermek için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ca352-114">Gives directions for responding to system or user events dynamically.</span></span>

 <span data-ttu-id="ca352-115">[Nasıl yapılır: Windows Forms 'de birden çok olayı tek bir olay Işleyicisine bağlama](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="ca352-115">[How to: Connect Multiple Events to a Single Event Handler in Windows Forms](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)</span></span>\
 <span data-ttu-id="ca352-116">Olaylar aracılığıyla birden çok denetime aynı işlevselliği atamaya yönelik yönergeler verir.</span><span class="sxs-lookup"><span data-stu-id="ca352-116">Gives directions for assigning the same functionality to multiple controls through events.</span></span>

 <span data-ttu-id="ca352-117">[Windows Forms olayların sırası](order-of-events-in-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="ca352-117">[Order of Events in Windows Forms](order-of-events-in-windows-forms.md)</span></span>\
 <span data-ttu-id="ca352-118">Windows Forms Denetimlerinde olayların oluşturulduğu sırayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="ca352-118">Describes the order in which events are raised in Windows Forms controls.</span></span>

 <span data-ttu-id="ca352-119">[Nasıl yapılır: tasarımcı kullanarak olay Işleyicileri oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)) Olay işleyicileri oluşturmak için Windows Form Tasarımcısı nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="ca352-119">[How to: Create Event Handlers Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)) Describes how to use the Windows Forms Designer to create event handlers.</span></span>

## <a name="related-sections"></a><span data-ttu-id="ca352-120">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="ca352-120">Related Sections</span></span>

 <span data-ttu-id="ca352-121">[Olayları](../../standard/events/index.md)</span><span class="sxs-lookup"><span data-stu-id="ca352-121">[Events](../../standard/events/index.md)</span></span>\
 <span data-ttu-id="ca352-122">.NET Framework kullanarak olayları işleme ve işlemeye yönelik konuların bağlantılarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="ca352-122">Provides links to topics on handling and raising events using the .NET Framework.</span></span>

 <span data-ttu-id="ca352-123">[Visual Basic devralınan olay Işleyicileriyle ilgili sorunları giderme](../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)</span><span class="sxs-lookup"><span data-stu-id="ca352-123">[Troubleshooting Inherited Event Handlers in Visual Basic](../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)</span></span>\
 <span data-ttu-id="ca352-124">Devralınan bileşenlerde olay işleyicileriyle gerçekleşen yaygın sorunları listeler.</span><span class="sxs-lookup"><span data-stu-id="ca352-124">Lists common issues that occur with event handlers in inherited components.</span></span>
