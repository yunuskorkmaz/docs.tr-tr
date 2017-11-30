---
title: "NotifyIcon Bileşenine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: NotifyIcon
helpviewer_keywords:
- NotifyIcon component [Windows Forms], about NotifyIcon component
- system tray icons [Windows Forms], about system tray icons
- system tray icons [Windows Forms], using in Windows Forms
ms.assetid: 5b9189fa-d4ae-41a6-9b97-eb1f44bb1a69
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d951d45232437026cc41d8e40284207ea1c64ab9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="notifyicon-component-overview-windows-forms"></a>NotifyIcon Bileşenine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.NotifyIcon> bileşen arka planda çalışır ve bir kullanıcı gösterme işlemlerin çoğu zaman arabirim simgelerini görüntülemek için genellikle kullanılır. Bir örnek, bir görev durumu bildirim alanı simgesini tıklatarak erişilebilir bir virüsten koruma yazılımı olabilir.  
  
## <a name="key-properties-of-notifyicons"></a>NotifyIcons temel özellikleri  
 Her <xref:System.Windows.Forms.NotifyIcon> bileşen durum alanında tek bir simge görüntüler. Üç arka plan işlemleri ve her biri için bir simge görüntülemek istediğiniz varsa, üç eklemelisiniz <xref:System.Windows.Forms.NotifyIcon> forma bileşenleri. Anahtar özelliklerini <xref:System.Windows.Forms.NotifyIcon> bileşeni olan <xref:System.Windows.Forms.NotifyIcon.Icon%2A> ve <xref:System.Windows.Forms.NotifyIcon.Visible%2A>. <xref:System.Windows.Forms.NotifyIcon.Icon%2A> Özelliği durum alanında görüntülenen simgesi ayarlar. Görünmesi simge sırayla <xref:System.Windows.Forms.NotifyIcon.Visible%2A> özelliği ayarlanmalıdır `true`.  
  
 Kullanıyorsanız [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], büyük bir kitaplığı ile birlikte kullanabileceğiniz standart görüntülerinin erişimi <xref:System.Windows.Forms.NotifyIcon> denetim.  
  
## <a name="notifyicons-options"></a>NotifyIcons seçenekleri  
 Balon ipuçları, kısayol menüleri ve araç ipuçları ile ilişkilendirebilirsiniz bir <xref:System.Windows.Forms.NotifyIcon> kullanıcı yardımcı olmak için.  
  
 Balon ipuçlarını görüntüleyebilirsiniz bir <xref:System.Windows.Forms.NotifyIcon> çağırarak <xref:System.Windows.Forms.NotifyIcon.ShowBalloonTip%2A> yöntemi zaman aralığı belirtmek istiyorsanız balon ipucu'nu görüntülemek için. Metin, simge ve balon ucuyla başlığı da belirtebilirsiniz <xref:System.Windows.Forms.NotifyIcon.BalloonTipText%2A>, <xref:System.Windows.Forms.NotifyIcon.BalloonTipIcon%2A> ve <xref:System.Windows.Forms.NotifyIcon.BalloonTipTitle%2A>sırasıyla. <xref:System.Windows.Forms.NotifyIcon>bileşenleri araç ipuçları ve kısayol menüleri ilişkili sahip. Daha fazla bilgi için bkz: [ToolTip bileşenine genel bakış](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md) ve [ContextMenu bileşenine genel bakış](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.NotifyIcon>  
 [Notifyıcon bileşeni](../../../../docs/framework/winforms/controls/notifyicon-component-windows-forms.md)
