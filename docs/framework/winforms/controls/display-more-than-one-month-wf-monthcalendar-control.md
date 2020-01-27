---
title: MonthCalendar denetiminde birden fazla ay görüntüleme
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
ms.openlocfilehash: 5d3925bc19ddcd67742f0ab8b5b2e45530820f38
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745891"
---
# <a name="how-to-display-more-than-one-month-in-the-windows-forms-monthcalendar-control"></a>Nasıl yapılır: Windows Forms MonthCalendar Denetiminde Birden Fazla Ay Görüntüleme
Windows Forms <xref:System.Windows.Forms.MonthCalendar> denetimi, her seferinde 12 aya kadar gösterebilir. Varsayılan olarak, denetim yalnızca bir ay görüntüler, ancak kaç ay görüntülendiğini ve denetimin içinde nasıl düzenlendiğini belirtebilirsiniz. Takvim boyutlarını değiştirdiğinizde denetim yeniden boyutlandırılır, bu nedenle formda yeni boyutlar için yeterli yer olduğundan emin olun.  
  
### <a name="to-display-multiple-months"></a>Birden çok ay görüntüleme  
  
- <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> özelliğini yatay ve dikey olarak görüntülenecek ay sayısı olarak ayarlayın.  
  
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
- [Nasıl yapılır: Windows Forms MonthCalendar Denetiminde Tarih Aralığı Seçme](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [Nasıl yapılır: Windows Forms MonthCalendar Denetiminin Görünüşünü Değiştirme](how-to-change-monthcalendar-control-appearance.md)
