---
title: 'Nasıl yapılır: Windows Forms MonthCalendar denetiminde birden fazla ay görüntüleme'
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
ms.openlocfilehash: febed820bae460f51bb19f08caa6027011abd55d
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57715353"
---
# <a name="how-to-display-more-than-one-month-in-the-windows-forms-monthcalendar-control"></a>Nasıl yapılır: Windows Forms MonthCalendar denetiminde birden fazla ay görüntüleme
Windows Forms <xref:System.Windows.Forms.MonthCalendar> denetimi, aynı anda en fazla 12 ay görüntüleyebilirsiniz. Varsayılan olarak, yalnızca bir ay denetim görüntüler, ancak kaç ay görüntülenir ve içindeki denetim nasıl düzenlenir belirtebilirsiniz. Takvim boyutları değiştirdiğinizde, denetimi yeniden boyutlandırıldı, bu nedenle yeni boyutlar için formda yetecek kadar yer olduğundan emin olun.  
  
### <a name="to-display-multiple-months"></a>Birden çok aya görüntülemek için  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.
- [MonthCalendar Denetimi](monthcalendar-control-windows-forms.md)
- [Nasıl yapılır: Windows Forms MonthCalendar denetiminde tarih aralığı seçin](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [Nasıl yapılır: Windows Forms MonthCalendar denetiminin görünüşünü değiştirme](how-to-change-monthcalendar-control-appearance.md)
