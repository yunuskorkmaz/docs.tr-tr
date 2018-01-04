---
title: "Windows Forms'ta Olayların Sırası"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- events [Windows Forms], order of
- focus event order
- application shutdown event order
- sequence [Windows Forms], of events
- validation events [Windows Forms], order of
- application startup event order
ms.assetid: e81db09b-4453-437f-b78a-62d7cd5c9829
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 03d2661752e5c0acb36fe76a8fa72b0638b4ad54
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="order-of-events-in-windows-forms"></a>Windows Forms'ta Olayların Sırası
Windows Forms uygulamalarında olayları ortaya geliştiricilere bu olayların her biri sırayla işleme ile ilgili belirli ilgi sırasıdır. Bir durum olayların ne zaman formun bölümleri yeniden gibi ince işleme çağırdığında bir tanıma olaylar çalışma zamanında oluşturulur kesin siparişi gereklidir. Bu konu, uygulamalar ve denetimleri ömrü içinde birkaç önemli aşamaları sırasında olayları terabayt bazı ayrıntılar sağlar. Fare giriş olayların sırası hakkında belirli Ayrıntılar için bkz: [Windows Forms'ta fare olayları](../../../docs/framework/winforms/mouse-events-in-windows-forms.md). Windows Forms'ta olayların genel bakış için bkz: [olaylara genel bakış](../../../docs/framework/winforms/events-overview-windows-forms.md). Olay işleyicileri yapısıyla hakkında daha fazla ayrıntı için bkz: [olay işleyicilerine genel bakış](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).  
  
## <a name="application-startup-and-shutdown-events"></a>Uygulama başlatma ve kapatma olayları  
 <xref:System.Windows.Forms.Form> Ve <xref:System.Windows.Forms.Control> sınıfları bir dizi uygulama başlatma ve kapatma ilgili olayları gösterir. Bir Windows Forms uygulaması başlatıldığında, ana formun başlangıç olaylar aşağıdaki sırayla oluşturulur:  
  
-   <xref:System.Windows.Forms.Control.HandleCreated?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Control.BindingContextChanged?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Control.VisibleChanged?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Activated?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Shown?displayProperty=nameWithType>  
  
 Bir uygulama kapandığında ana formun kapatma olayları aşağıdaki sırayla oluşturulur:  
  
-   <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Closed?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.FormClosed?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Deactivate?displayProperty=nameWithType>  
  
 <xref:System.Windows.Forms.Application.ApplicationExit> Olayı <xref:System.Windows.Forms.Application> sınıfı, ana formu kapatma olayları sonra oluşturulur.  
  
> [!NOTE]
>  Visual Basic 2005 içeren ek uygulama olayları gibi <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup?displayProperty=nameWithType> ve <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown?displayProperty=nameWithType>.  
  
## <a name="focus-and-validation-events"></a>Odak ve doğrulama olayları  
 Çağırarak (SEKMESİ, üst karakter + sekme ve benzeri) klavyeyi kullanarak odağı değiştirdiğinizde <xref:System.Windows.Forms.Control.Select%2A> veya <xref:System.Windows.Forms.Control.SelectNextControl%2A> yöntemleri veya ayarlayarak <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> geçerli formun, odak olayları özelliğine <xref:System.Windows.Forms.Control> sınıfı ortaya aşağıdaki sırayla :  
  
-   <xref:System.Windows.Forms.Control.Enter>  
  
-   <xref:System.Windows.Forms.Control.GotFocus>  
  
-   <xref:System.Windows.Forms.Control.Leave>  
  
-   <xref:System.Windows.Forms.Control.Validating>  
  
-   <xref:System.Windows.Forms.Control.Validated>  
  
-   <xref:System.Windows.Forms.Control.LostFocus>  
  
 Değiştirdiğinizde odağı fare kullanarak veya çağırarak <xref:System.Windows.Forms.Control.Focus%2A> yöntemi, odak olayları <xref:System.Windows.Forms.Control> sınıfı aşağıdaki sırayla oluşur:  
  
-   <xref:System.Windows.Forms.Control.Enter>  
  
-   <xref:System.Windows.Forms.Control.GotFocus>  
  
-   <xref:System.Windows.Forms.Control.LostFocus>  
  
-   <xref:System.Windows.Forms.Control.Leave>  
  
-   <xref:System.Windows.Forms.Control.Validating>  
  
-   <xref:System.Windows.Forms.Control.Validated>  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms'ta Olay İşleyicileri Oluşturma](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)
