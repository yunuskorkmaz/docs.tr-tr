---
title: Windows Forms'ta Olayların Sırası
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], order of
- focus event order
- application shutdown event order
- sequence [Windows Forms], of events
- validation events [Windows Forms], order of
- application startup event order
ms.assetid: e81db09b-4453-437f-b78a-62d7cd5c9829
ms.openlocfilehash: 814c788285d974db5a8ef2bbaec1368a860c21d2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643968"
---
# <a name="order-of-events-in-windows-forms"></a><span data-ttu-id="104d3-102">Windows Forms'ta Olayların Sırası</span><span class="sxs-lookup"><span data-stu-id="104d3-102">Order of Events in Windows Forms</span></span>
<span data-ttu-id="104d3-103">Windows Forms uygulamalarında olayları ortaya çıkar geliştiriciler bu olayların her biri sırayla işleme ile ilgili belirli ilgilenilen sırasıdır.</span><span class="sxs-lookup"><span data-stu-id="104d3-103">The order in which events are raised in Windows Forms applications is of particular interest to developers concerned with handling each of these events in turn.</span></span> <span data-ttu-id="104d3-104">Bir durum için olayların ne zaman formun parçalarını yeniden gibi gözlemlemenize işleme çağırdığında bir farkındalık olaylar çalışma zamanında oluşturulur kesin siparişin gereklidir.</span><span class="sxs-lookup"><span data-stu-id="104d3-104">When a situation calls for meticulous handling of events, such as when you are redrawing parts of the form, an awareness of the precise order in which events are raised at run time is necessary.</span></span> <span data-ttu-id="104d3-105">Bu konu, uygulamalar ve denetimleri ömrünü birkaç önemli aşamaları sırasında olayları bazında bazı ayrıntılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="104d3-105">This topic provides some details on the order of events during several important stages in the lifetime of applications and controls.</span></span> <span data-ttu-id="104d3-106">Fare giriş olayları sırası hakkında belirli Ayrıntılar için bkz [Windows Forms'ta fare olayları](../../../docs/framework/winforms/mouse-events-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="104d3-106">For specific details about the order of mouse input events, see [Mouse Events in Windows Forms](../../../docs/framework/winforms/mouse-events-in-windows-forms.md).</span></span> <span data-ttu-id="104d3-107">Windows Forms'ta olayların genel bakış için bkz. [olaylara genel bakış](../../../docs/framework/winforms/events-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="104d3-107">For an overview of events in Windows Forms, see [Events Overview](../../../docs/framework/winforms/events-overview-windows-forms.md).</span></span> <span data-ttu-id="104d3-108">Olay işleyicileri düzenini hakkında daha fazla ayrıntı için bkz: [olay işleyicilerine genel bakış](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="104d3-108">For details about the makeup of event handlers, see [Event Handlers Overview](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).</span></span>  
  
## <a name="application-startup-and-shutdown-events"></a><span data-ttu-id="104d3-109">Uygulama başlatma ve kapatma olayları</span><span class="sxs-lookup"><span data-stu-id="104d3-109">Application Startup and Shutdown Events</span></span>  
 <span data-ttu-id="104d3-110"><xref:System.Windows.Forms.Form> Ve <xref:System.Windows.Forms.Control> sınıfları bir dizi uygulama başlatma ve kapatma ile ilgili olayları gösterir.</span><span class="sxs-lookup"><span data-stu-id="104d3-110">The <xref:System.Windows.Forms.Form> and <xref:System.Windows.Forms.Control> classes expose a set of events related to application startup and shutdown.</span></span> <span data-ttu-id="104d3-111">Bir Windows Forms uygulaması başladığında, ana formu başlangıç olayları aşağıdaki sırayla oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="104d3-111">When a Windows Forms application starts, the startup events of the main form are raised in the following order:</span></span>  
  
-   <xref:System.Windows.Forms.Control.HandleCreated?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Control.BindingContextChanged?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Control.VisibleChanged?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Activated?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Shown?displayProperty=nameWithType>  
  
 <span data-ttu-id="104d3-112">Bir uygulama kapandığında ana formu kapatma olayları aşağıdaki sırayla oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="104d3-112">When an application closes, the shutdown events of the main form are raised in the following order:</span></span>  
  
-   <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Closed?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.FormClosed?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Deactivate?displayProperty=nameWithType>  
  
 <span data-ttu-id="104d3-113"><xref:System.Windows.Forms.Application.ApplicationExit> Olayı <xref:System.Windows.Forms.Application> sınıfı, ana formu kapatma olaylarını sonra oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="104d3-113">The <xref:System.Windows.Forms.Application.ApplicationExit> event of the <xref:System.Windows.Forms.Application> class is raised after the shutdown events of the main form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="104d3-114">Visual Basic 2005 içeren ek uygulama olayları gibi <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup?displayProperty=nameWithType> ve <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="104d3-114">Visual Basic 2005 includes additional application events, such as <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup?displayProperty=nameWithType> and <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown?displayProperty=nameWithType>.</span></span>  
  
## <a name="focus-and-validation-events"></a><span data-ttu-id="104d3-115">Odak ve doğrulama olayları</span><span class="sxs-lookup"><span data-stu-id="104d3-115">Focus and Validation Events</span></span>  
 <span data-ttu-id="104d3-116">Klavye (SEKMESİ, SHIFT + TAB vb.) kullanarak çağırarak odağı değiştirdiğinizde <xref:System.Windows.Forms.Control.Select%2A> veya <xref:System.Windows.Forms.Control.SelectNextControl%2A> yöntemleri veya ayarlayarak <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> özelliğini geçerli biçime, odak olayları <xref:System.Windows.Forms.Control> sınıfı aşağıdaki sırayla gerçekleşir :</span><span class="sxs-lookup"><span data-stu-id="104d3-116">When you change the focus by using the keyboard (TAB, SHIFT+TAB, and so on), by calling the <xref:System.Windows.Forms.Control.Select%2A> or <xref:System.Windows.Forms.Control.SelectNextControl%2A> methods, or by setting the <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> property to the current form, focus events of the <xref:System.Windows.Forms.Control> class occur in the following order:</span></span>  
  
-   <xref:System.Windows.Forms.Control.Enter>  
  
-   <xref:System.Windows.Forms.Control.GotFocus>  
  
-   <xref:System.Windows.Forms.Control.Leave>  
  
-   <xref:System.Windows.Forms.Control.Validating>  
  
-   <xref:System.Windows.Forms.Control.Validated>  
  
-   <xref:System.Windows.Forms.Control.LostFocus>  
  
 <span data-ttu-id="104d3-117">Değiştirdiğinizde odak fareyi kullanarak veya çağırarak <xref:System.Windows.Forms.Control.Focus%2A> yöntemi, odak olayları <xref:System.Windows.Forms.Control> sınıfı aşağıdaki sırayla gerçekleşir:</span><span class="sxs-lookup"><span data-stu-id="104d3-117">When you change the focus by using the mouse or by calling the <xref:System.Windows.Forms.Control.Focus%2A> method, focus events of the <xref:System.Windows.Forms.Control> class occur in the following order:</span></span>  
  
-   <xref:System.Windows.Forms.Control.Enter>  
  
-   <xref:System.Windows.Forms.Control.GotFocus>  
  
-   <xref:System.Windows.Forms.Control.LostFocus>  
  
-   <xref:System.Windows.Forms.Control.Leave>  
  
-   <xref:System.Windows.Forms.Control.Validating>  
  
-   <xref:System.Windows.Forms.Control.Validated>  
  
## <a name="see-also"></a><span data-ttu-id="104d3-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="104d3-118">See also</span></span>
- [<span data-ttu-id="104d3-119">Windows Forms'ta Olay İşleyicileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="104d3-119">Creating Event Handlers in Windows Forms</span></span>](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)
