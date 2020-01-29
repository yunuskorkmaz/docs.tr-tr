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
# <a name="order-of-events-in-windows-forms"></a>Windows Forms'ta Olayların Sırası
Windows Forms uygulamalarda olayların oluşturulduğu sıra, bu olayların her birini sırayla işlemeye yönelik geliştiriciler için özellikle ilgilenmektedir. Bir durum, olayların işlenmesini (örneğin, formun parçalarını yeniden çizerken) aradığında, olayların çalışma zamanında oluşturulduğu kesin sıra için bir tanıma gerekir. Bu konu, uygulama ve denetimlerin ömrü boyunca birkaç önemli aşamada olayların sırası hakkında bazı ayrıntılar sağlar. Fare giriş olaylarının sırası hakkında ayrıntılı bilgi için [Windows Forms fare olayları](mouse-events-in-windows-forms.md)bölümüne bakın. Windows Forms olaylara genel bakış için bkz. [olaylara genel bakış](events-overview-windows-forms.md). Olay işleyicilerinin makeof hakkında ayrıntılar için bkz. [olay Işleyicilerine genel bakış](event-handlers-overview-windows-forms.md).  
  
## <a name="application-startup-and-shutdown-events"></a>Uygulama başlatma ve kapatması olayları  
 <xref:System.Windows.Forms.Form> ve <xref:System.Windows.Forms.Control> sınıfları uygulama başlatma ve kapatmaya ilişkin bir olay kümesi sunar. Windows Forms bir uygulama başlatıldığında, ana formun başlangıç olayları aşağıdaki sırayla oluşturulur:  
  
- <xref:System.Windows.Forms.Control.HandleCreated?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Control.BindingContextChanged?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Control.VisibleChanged?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Activated?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Shown?displayProperty=nameWithType>  
  
 Bir uygulama kapandığında ana formun kapatma olayları aşağıdaki sırayla oluşturulur:  
  
- <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Closed?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.FormClosed?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Deactivate?displayProperty=nameWithType>  
  
 <xref:System.Windows.Forms.Application> sınıfının <xref:System.Windows.Forms.Application.ApplicationExit> olayı, ana formun kapatılıyor olaylarından sonra tetiklenir.  
  
> [!NOTE]
> Visual Basic 2005, <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup?displayProperty=nameWithType> ve <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown?displayProperty=nameWithType>gibi ek uygulama olaylarını içerir.  
  
## <a name="focus-and-validation-events"></a>Odak ve doğrulama olayları  
 Klavyeyi kullanarak (TAB, SHIFT + TAB vb.), <xref:System.Windows.Forms.Control.Select%2A> veya <xref:System.Windows.Forms.Control.SelectNextControl%2A> yöntemleri çağırarak veya <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> özelliğini geçerli form olarak ayarlayarak odağı değiştirdiğinizde, <xref:System.Windows.Forms.Control> sınıfının odak olayları aşağıdaki sırayla gerçekleşir:  
  
- <xref:System.Windows.Forms.Control.Enter>  
  
- <xref:System.Windows.Forms.Control.GotFocus>  
  
- <xref:System.Windows.Forms.Control.Leave>  
  
- <xref:System.Windows.Forms.Control.Validating>  
  
- <xref:System.Windows.Forms.Control.Validated>  
  
- <xref:System.Windows.Forms.Control.LostFocus>  
  
 Fareyi kullanarak veya <xref:System.Windows.Forms.Control.Focus%2A> yöntemini çağırarak odağı değiştirdiğinizde, <xref:System.Windows.Forms.Control> sınıfının odak olayları aşağıdaki sırayla gerçekleşir:  
  
- <xref:System.Windows.Forms.Control.Enter>  
  
- <xref:System.Windows.Forms.Control.GotFocus>  
  
- <xref:System.Windows.Forms.Control.LostFocus>  
  
- <xref:System.Windows.Forms.Control.Leave>  
  
- <xref:System.Windows.Forms.Control.Validating>  
  
- <xref:System.Windows.Forms.Control.Validated>  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms'ta Olay İşleyicileri Oluşturma](creating-event-handlers-in-windows-forms.md)
