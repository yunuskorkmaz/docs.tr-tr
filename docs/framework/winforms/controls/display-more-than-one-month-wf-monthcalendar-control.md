---
title: "Nasıl yapılır: Windows Forms MonthCalendar Denetiminde Birden Fazla Ay Görüntüleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- calendars [Windows Forms], formatting display
- examples [Windows Forms], calendar controls
- calendars [Windows Forms], multiple months
- MonthCalendar control [Windows Forms], formatting display
ms.assetid: d197caa2-38a5-4cb4-acc3-562130c2ace3
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 63cf236f93fa3352e536c71000f6bb110abf02fa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-more-than-one-month-in-the-windows-forms-monthcalendar-control"></a>Nasıl yapılır: Windows Forms MonthCalendar Denetiminde Birden Fazla Ay Görüntüleme
Windows Forms <xref:System.Windows.Forms.MonthCalendar> denetimi aynı anda en fazla 12 ay görüntüleyebilir. Varsayılan olarak, yalnızca bir ay denetimi görüntüler, ancak kaç ay görüntülenir ve denetim içinden nasıl düzenlenir belirtebilirsiniz. Takvim boyutları değiştirdiğinizde, denetimi boyutlandırılır, bu nedenle yeni boyutları için form üzerinde yeterli alan bulunduğundan emin olun.  
  
### <a name="to-display-multiple-months"></a>Birden fazla ay görüntülemek için  
  
-   Ayarlama <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> özelliğini yatay ve dikey olarak görüntülenecek ay sayısı.  
  
    ```vb  
    MonthCalendar1.CalendarDimensions = New System.Drawing.Size (3,2)  
    ```  
  
    ```csharp  
    monthCalendar1.CalendarDimensions = new System.Drawing.Size (3,2);  
    ```  
  
    ```cpp  
    monthCalendar1->CalendarDimensions = System::Drawing::Size (3,2);  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [MonthCalendar denetimi](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [Nasıl yapılır: Windows Forms MonthCalendar denetiminde tarih aralığı seçin](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)  
 [Nasıl yapılır: Windows Forms MonthCalendar denetiminin görünüşünü değiştirme](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)
