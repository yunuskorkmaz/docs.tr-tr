---
title: "Windows Forms'ta Olay İşleyicileri Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- event handling [Windows Forms]
- Windows Forms controls, event handling
- Windows Forms, event handling
- events [Windows Forms], event handlers
- event handlers [Windows Forms]
ms.assetid: 6514e530-c6b8-489c-a8d2-eda7b7072701
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0625d5272b4c3ae4f21793d0b0fc8645158e6a2c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="creating-event-handlers-in-windows-forms"></a><span data-ttu-id="ea7f1-102">Windows Forms'ta Olay İşleyicileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ea7f1-102">Creating Event Handlers in Windows Forms</span></span>
<span data-ttu-id="ea7f1-103">Olay işleyici hangi eylemlerin bir ileti sırası bir ileti alır veya bir olay oluşur, kullanıcı bir düğmesine tıkladığında gibi gerçekleştirilir belirler, kodunuzda bir yordamdır.</span><span class="sxs-lookup"><span data-stu-id="ea7f1-103">An event handler is a procedure in your code that determines what actions are performed when an event occurs, such as when the user clicks a button or a message queue receives a message.</span></span> <span data-ttu-id="ea7f1-104">Bir olay oluşturulduğunda, olay işleyicisi veya olay alırsınız işleyicileri yürütülür.</span><span class="sxs-lookup"><span data-stu-id="ea7f1-104">When an event is raised, the event handler or handlers that receive the event are executed.</span></span> <span data-ttu-id="ea7f1-105">Olaylar için birden çok işleyici atanabilir ve belirli olayları işlemek yöntemleri dinamik olarak değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="ea7f1-105">Events can be assigned to multiple handlers, and the methods that handle particular events can be changed dynamically.</span></span> <span data-ttu-id="ea7f1-106">Windows Form Tasarımcısı, olay işleyicileri oluşturmak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ea7f1-106">You can also use the Windows Forms Designer to create event handlers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ea7f1-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="ea7f1-107">In This Section</span></span>  
 [<span data-ttu-id="ea7f1-108">Olaylara genel bakış</span><span class="sxs-lookup"><span data-stu-id="ea7f1-108">Events Overview</span></span>](../../../docs/framework/winforms/events-overview-windows-forms.md)  
 <span data-ttu-id="ea7f1-109">Olay modeli ve temsilciler rolünü açıklar.</span><span class="sxs-lookup"><span data-stu-id="ea7f1-109">Explains the event model and the role of delegates.</span></span>  
  
 [<span data-ttu-id="ea7f1-110">Olay işleyicilerine genel bakış</span><span class="sxs-lookup"><span data-stu-id="ea7f1-110">Event Handlers Overview</span></span>](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)  
 <span data-ttu-id="ea7f1-111">Olayları işlemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="ea7f1-111">Describes how to handle events.</span></span>  
  
 [<span data-ttu-id="ea7f1-112">Nasıl yapılır: Windows Forms için çalışma zamanında olay işleyicileri oluşturma</span><span class="sxs-lookup"><span data-stu-id="ea7f1-112">How to: Create Event Handlers at Run Time for Windows Forms</span></span>](../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md)  
 <span data-ttu-id="ea7f1-113">Dinamik olarak sistem veya kullanıcı olaylarına yanıt için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ea7f1-113">Gives directions for responding to system or user events dynamically.</span></span>  
  
 [<span data-ttu-id="ea7f1-114">Nasıl yapılır: Windows Forms'ta tek olay işleyicisine birden çok olay bağlanma</span><span class="sxs-lookup"><span data-stu-id="ea7f1-114">How to: Connect Multiple Events to a Single Event Handler in Windows Forms</span></span>](../../../docs/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)  
 <span data-ttu-id="ea7f1-115">Birden çok denetim olaylar ile aynı işlevselliği atamak için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ea7f1-115">Gives directions for assigning the same functionality to multiple controls through events.</span></span>  
  
 [<span data-ttu-id="ea7f1-116">Windows Forms'ta olayların sırası</span><span class="sxs-lookup"><span data-stu-id="ea7f1-116">Order of Events in Windows Forms</span></span>](../../../docs/framework/winforms/order-of-events-in-windows-forms.md)  
 <span data-ttu-id="ea7f1-117">Windows Forms denetimlerindeki olaylar ortaya sırasını açıklar.</span><span class="sxs-lookup"><span data-stu-id="ea7f1-117">Describes the order in which events are raised in Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="ea7f1-118">Nasıl yapılır: Tasarımcı kullanarak olay işleyicileri oluşturma</span><span class="sxs-lookup"><span data-stu-id="ea7f1-118">How to: Create Event Handlers Using the Designer</span></span>](http://msdn.microsoft.com/en-us/8461e9b8-14e8-406f-936e-3726732b23d2)  
 <span data-ttu-id="ea7f1-119">Windows Form Tasarımcısı olay işleyicileri oluşturmak için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="ea7f1-119">Describes how to use the Windows Forms Designer to create event handlers.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ea7f1-120">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="ea7f1-120">Related Sections</span></span>  
 [<span data-ttu-id="ea7f1-121">Olayları</span><span class="sxs-lookup"><span data-stu-id="ea7f1-121">Events</span></span>](../../../docs/standard/events/index.md)  
 <span data-ttu-id="ea7f1-122">Kullanarak olaylar oluşturma ve işleme üzerinde konulara bağlantılar sağlanır [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ea7f1-122">Provides links to topics on handling and raising events using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span>  
  
 [<span data-ttu-id="ea7f1-123">Devralınmış olay işleyicileri Visual Basic sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="ea7f1-123">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 <span data-ttu-id="ea7f1-124">Olay işleyicileri devralınan bileşenlerinde yazılımında ortak sorunları listeler.</span><span class="sxs-lookup"><span data-stu-id="ea7f1-124">Lists common issues that occur with event handlers in inherited components.</span></span>
