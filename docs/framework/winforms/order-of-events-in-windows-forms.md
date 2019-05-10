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
ms.openlocfilehash: f581ca5ee1376251a593e7b8813ef4b0e0f41b64
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64655593"
---
# <a name="order-of-events-in-windows-forms"></a>Windows Forms'ta Olayların Sırası
Windows Forms uygulamalarında olayları ortaya çıkar geliştiriciler bu olayların her biri sırayla işleme ile ilgili belirli ilgilenilen sırasıdır. Bir durum için olayların ne zaman formun parçalarını yeniden gibi gözlemlemenize işleme çağırdığında bir farkındalık olaylar çalışma zamanında oluşturulur kesin siparişin gereklidir. Bu konu, uygulamalar ve denetimleri ömrünü birkaç önemli aşamaları sırasında olayları bazında bazı ayrıntılar sağlar. Fare giriş olayları sırası hakkında belirli Ayrıntılar için bkz [Windows Forms'ta fare olayları](mouse-events-in-windows-forms.md). Windows Forms'ta olayların genel bakış için bkz. [olaylara genel bakış](events-overview-windows-forms.md). Olay işleyicileri düzenini hakkında daha fazla ayrıntı için bkz: [olay işleyicilerine genel bakış](event-handlers-overview-windows-forms.md).  
  
## <a name="application-startup-and-shutdown-events"></a>Uygulama başlatma ve kapatma olayları  
 <xref:System.Windows.Forms.Form> Ve <xref:System.Windows.Forms.Control> sınıfları bir dizi uygulama başlatma ve kapatma ile ilgili olayları gösterir. Bir Windows Forms uygulaması başladığında, ana formu başlangıç olayları aşağıdaki sırayla oluşturulur:  
  
- <xref:System.Windows.Forms.Control.HandleCreated?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Control.BindingContextChanged?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Control.VisibleChanged?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Activated?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Shown?displayProperty=nameWithType>  
  
 Bir uygulama kapandığında ana formu kapatma olayları aşağıdaki sırayla oluşturulur:  
  
- <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Closed?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.FormClosed?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Deactivate?displayProperty=nameWithType>  
  
 <xref:System.Windows.Forms.Application.ApplicationExit> Olayı <xref:System.Windows.Forms.Application> sınıfı, ana formu kapatma olaylarını sonra oluşturulur.  
  
> [!NOTE]
>  Visual Basic 2005 içeren ek uygulama olayları gibi <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup?displayProperty=nameWithType> ve <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown?displayProperty=nameWithType>.  
  
## <a name="focus-and-validation-events"></a>Odak ve doğrulama olayları  
 Klavye (SEKMESİ, SHIFT + TAB vb.) kullanarak çağırarak odağı değiştirdiğinizde <xref:System.Windows.Forms.Control.Select%2A> veya <xref:System.Windows.Forms.Control.SelectNextControl%2A> yöntemleri veya ayarlayarak <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> özelliğini geçerli biçime, odak olayları <xref:System.Windows.Forms.Control> sınıfı aşağıdaki sırayla gerçekleşir :  
  
- <xref:System.Windows.Forms.Control.Enter>  
  
- <xref:System.Windows.Forms.Control.GotFocus>  
  
- <xref:System.Windows.Forms.Control.Leave>  
  
- <xref:System.Windows.Forms.Control.Validating>  
  
- <xref:System.Windows.Forms.Control.Validated>  
  
- <xref:System.Windows.Forms.Control.LostFocus>  
  
 Değiştirdiğinizde odak fareyi kullanarak veya çağırarak <xref:System.Windows.Forms.Control.Focus%2A> yöntemi, odak olayları <xref:System.Windows.Forms.Control> sınıfı aşağıdaki sırayla gerçekleşir:  
  
- <xref:System.Windows.Forms.Control.Enter>  
  
- <xref:System.Windows.Forms.Control.GotFocus>  
  
- <xref:System.Windows.Forms.Control.LostFocus>  
  
- <xref:System.Windows.Forms.Control.Leave>  
  
- <xref:System.Windows.Forms.Control.Validating>  
  
- <xref:System.Windows.Forms.Control.Validated>  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms'ta Olay İşleyicileri Oluşturma](creating-event-handlers-in-windows-forms.md)
