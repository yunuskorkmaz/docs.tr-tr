---
title: Windows Forms Denetimlerindeki Olaylar
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- events [Windows Forms], custom controls (using code)
- custom controls [Windows Forms], events overview (using code)
ms.assetid: 7e3d1379-87aa-437c-afce-c99454eff30e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e568dd7fadea8af399a63aa95347f368b4e13a54
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="events-in-windows-forms-controls"></a>Windows Forms Denetimlerindeki Olaylar
Bir Windows Forms denetimi birden fazla altmış olaylarından devralır <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. Bunlar <xref:System.Windows.Forms.Control.Paint> çizilecek denetim neden olan olay, bir pencere gibi görüntüleme için ilgili olayları <xref:System.Windows.Forms.Control.Resize> ve <xref:System.Windows.Forms.Control.Layout> olayları ve alt düzey fare ve klavye olayları. Alt düzey bazı olaylar tarafından oluşturulan <xref:System.Windows.Forms.Control> anlamsal olayları gibi içine <xref:System.Windows.Forms.Control.Click> ve <xref:System.Windows.Forms.Control.DoubleClick>. Devralınan olaylar hakkında daha fazla ayrıntı için bkz: <xref:System.Windows.Forms.Control>.  
  
 Özel denetim devralınmış olay işlevi geçersiz kılması gerekiyorsa, devralınan geçersiz kılma `On` *EventName* temsilci ekleme yerine yöntemi. .NET Framework olay modelinde alışık değilseniz bkz [oluşturma olayları bir bileşenin](http://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [OnPaint yöntemini geçersiz kılma](../../../../docs/framework/winforms/controls/overriding-the-onpaint-method.md)  
 [Kullanıcı girişini işleme](../../../../docs/framework/winforms/controls/handling-user-input.md)  
 [Olay tanımlama](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)  
 [Olayları](../../../../docs/standard/events/index.md)
