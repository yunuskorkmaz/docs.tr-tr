---
title: Olay sırası
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], order of
- focus event order
- application shutdown event order
- sequence [Windows Forms], of events
- validation events [Windows Forms], order of
- application startup event order
ms.assetid: e81db09b-4453-437f-b78a-62d7cd5c9829
ms.openlocfilehash: 618ac5a6a6a32ae1a53fc60ac80700d7648c81a7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734864"
---
# <a name="order-of-events-in-windows-forms"></a><span data-ttu-id="f59ea-102">Windows Forms'ta Olayların Sırası</span><span class="sxs-lookup"><span data-stu-id="f59ea-102">Order of Events in Windows Forms</span></span>
<span data-ttu-id="f59ea-103">Windows Forms uygulamalarda olayların oluşturulduğu sıra, bu olayların her birini sırayla işlemeye yönelik geliştiriciler için özellikle ilgilenmektedir.</span><span class="sxs-lookup"><span data-stu-id="f59ea-103">The order in which events are raised in Windows Forms applications is of particular interest to developers concerned with handling each of these events in turn.</span></span> <span data-ttu-id="f59ea-104">Bir durum, olayların işlenmesini (örneğin, formun parçalarını yeniden çizerken) aradığında, olayların çalışma zamanında oluşturulduğu kesin sıra için bir tanıma gerekir.</span><span class="sxs-lookup"><span data-stu-id="f59ea-104">When a situation calls for meticulous handling of events, such as when you are redrawing parts of the form, an awareness of the precise order in which events are raised at run time is necessary.</span></span> <span data-ttu-id="f59ea-105">Bu konu, uygulama ve denetimlerin ömrü boyunca birkaç önemli aşamada olayların sırası hakkında bazı ayrıntılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="f59ea-105">This topic provides some details on the order of events during several important stages in the lifetime of applications and controls.</span></span> <span data-ttu-id="f59ea-106">Fare giriş olaylarının sırası hakkında ayrıntılı bilgi için [Windows Forms fare olayları](mouse-events-in-windows-forms.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="f59ea-106">For specific details about the order of mouse input events, see [Mouse Events in Windows Forms](mouse-events-in-windows-forms.md).</span></span> <span data-ttu-id="f59ea-107">Windows Forms olaylara genel bakış için bkz. [olaylara genel bakış](events-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="f59ea-107">For an overview of events in Windows Forms, see [Events Overview](events-overview-windows-forms.md).</span></span> <span data-ttu-id="f59ea-108">Olay işleyicilerinin makeof hakkında ayrıntılar için bkz. [olay Işleyicilerine genel bakış](event-handlers-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="f59ea-108">For details about the makeup of event handlers, see [Event Handlers Overview](event-handlers-overview-windows-forms.md).</span></span>  
  
## <a name="application-startup-and-shutdown-events"></a><span data-ttu-id="f59ea-109">Uygulama başlatma ve kapatması olayları</span><span class="sxs-lookup"><span data-stu-id="f59ea-109">Application Startup and Shutdown Events</span></span>  
 <span data-ttu-id="f59ea-110"><xref:System.Windows.Forms.Form> ve <xref:System.Windows.Forms.Control> sınıfları uygulama başlatma ve kapatmaya ilişkin bir olay kümesi sunar.</span><span class="sxs-lookup"><span data-stu-id="f59ea-110">The <xref:System.Windows.Forms.Form> and <xref:System.Windows.Forms.Control> classes expose a set of events related to application startup and shutdown.</span></span> <span data-ttu-id="f59ea-111">Windows Forms bir uygulama başlatıldığında, ana formun başlangıç olayları aşağıdaki sırayla oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="f59ea-111">When a Windows Forms application starts, the startup events of the main form are raised in the following order:</span></span>  
  
- <xref:System.Windows.Forms.Control.HandleCreated?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Control.BindingContextChanged?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Control.VisibleChanged?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Activated?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Shown?displayProperty=nameWithType>  
  
 <span data-ttu-id="f59ea-112">Bir uygulama kapandığında ana formun kapatma olayları aşağıdaki sırayla oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="f59ea-112">When an application closes, the shutdown events of the main form are raised in the following order:</span></span>  
  
- <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Closed?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.FormClosed?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Deactivate?displayProperty=nameWithType>  
  
 <span data-ttu-id="f59ea-113"><xref:System.Windows.Forms.Application> sınıfının <xref:System.Windows.Forms.Application.ApplicationExit> olayı, ana formun kapatılıyor olaylarından sonra tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="f59ea-113">The <xref:System.Windows.Forms.Application.ApplicationExit> event of the <xref:System.Windows.Forms.Application> class is raised after the shutdown events of the main form.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f59ea-114">Visual Basic 2005, <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup?displayProperty=nameWithType> ve <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown?displayProperty=nameWithType>gibi ek uygulama olaylarını içerir.</span><span class="sxs-lookup"><span data-stu-id="f59ea-114">Visual Basic 2005 includes additional application events, such as <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup?displayProperty=nameWithType> and <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown?displayProperty=nameWithType>.</span></span>  
  
## <a name="focus-and-validation-events"></a><span data-ttu-id="f59ea-115">Odak ve doğrulama olayları</span><span class="sxs-lookup"><span data-stu-id="f59ea-115">Focus and Validation Events</span></span>  
 <span data-ttu-id="f59ea-116">Klavyeyi kullanarak (TAB, SHIFT + TAB vb.), <xref:System.Windows.Forms.Control.Select%2A> veya <xref:System.Windows.Forms.Control.SelectNextControl%2A> yöntemleri çağırarak veya <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> özelliğini geçerli form olarak ayarlayarak odağı değiştirdiğinizde, <xref:System.Windows.Forms.Control> sınıfının odak olayları aşağıdaki sırayla gerçekleşir:</span><span class="sxs-lookup"><span data-stu-id="f59ea-116">When you change the focus by using the keyboard (TAB, SHIFT+TAB, and so on), by calling the <xref:System.Windows.Forms.Control.Select%2A> or <xref:System.Windows.Forms.Control.SelectNextControl%2A> methods, or by setting the <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> property to the current form, focus events of the <xref:System.Windows.Forms.Control> class occur in the following order:</span></span>  
  
- <xref:System.Windows.Forms.Control.Enter>  
  
- <xref:System.Windows.Forms.Control.GotFocus>  
  
- <xref:System.Windows.Forms.Control.Leave>  
  
- <xref:System.Windows.Forms.Control.Validating>  
  
- <xref:System.Windows.Forms.Control.Validated>  
  
- <xref:System.Windows.Forms.Control.LostFocus>  
  
 <span data-ttu-id="f59ea-117">Fareyi kullanarak veya <xref:System.Windows.Forms.Control.Focus%2A> yöntemini çağırarak odağı değiştirdiğinizde, <xref:System.Windows.Forms.Control> sınıfının odak olayları aşağıdaki sırayla gerçekleşir:</span><span class="sxs-lookup"><span data-stu-id="f59ea-117">When you change the focus by using the mouse or by calling the <xref:System.Windows.Forms.Control.Focus%2A> method, focus events of the <xref:System.Windows.Forms.Control> class occur in the following order:</span></span>  
  
- <xref:System.Windows.Forms.Control.Enter>  
  
- <xref:System.Windows.Forms.Control.GotFocus>  
  
- <xref:System.Windows.Forms.Control.LostFocus>  
  
- <xref:System.Windows.Forms.Control.Leave>  
  
- <xref:System.Windows.Forms.Control.Validating>  
  
- <xref:System.Windows.Forms.Control.Validated>  
  
## <a name="see-also"></a><span data-ttu-id="f59ea-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f59ea-118">See also</span></span>

- [<span data-ttu-id="f59ea-119">Windows Forms'ta Olay İşleyicileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f59ea-119">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
