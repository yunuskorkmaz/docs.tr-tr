---
title: 'Nasıl yapılır: Windows Forms MonthCalendar Denetiminde Birden Fazla Ay Görüntüleme'
ms.date: 03/30/2017
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
ms.openlocfilehash: a71f85af2d51faf37160aba7fa89a8421b4523d4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524879"
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
 [MonthCalendar Denetimi](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [Nasıl yapılır: Windows Forms MonthCalendar Denetiminde Tarih Aralığı Seçme](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)  
 [Nasıl yapılır: Windows Forms MonthCalendar Denetiminin Görünüşünü Değiştirme](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)
