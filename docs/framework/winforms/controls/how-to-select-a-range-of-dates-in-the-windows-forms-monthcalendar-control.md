---
title: 'Nasıl yapılır: Windows Forms MonthCalendar denetiminde tarih aralığı seçin'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- dates [Windows Forms], selecting range in calendar controls
- examples [Windows Forms], calendar controls
- calendars [Windows Forms], selecting date range
- MonthCalendar control [Windows Forms], selecting date range
ms.assetid: 95d9ab95-b0f8-4c19-9f63-b5cd4593a5d0
ms.openlocfilehash: 4c7100f77c313d219cfd4cceff5ae3015eae4c18
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558455"
---
# <a name="how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control"></a>Nasıl yapılır: Windows Forms MonthCalendar denetiminde tarih aralığı seçin
Windows Forms ve önemli bir özelliği <xref:System.Windows.Forms.MonthCalendar> denetimi, kullanıcının bir tarih aralığını seçebilirsiniz. Bu özellik bir geliştirme Tarih Seçimi özelliğidir <xref:System.Windows.Forms.DateTimePicker> denetimi, yalnızca tek bir tarih/saat değeri seçmesini sağlar. Tarih aralığı ayarlayın veya alın özelliklerini kullanarak kullanıcı tarafından ayarlanan bir seçim aralığını <xref:System.Windows.Forms.MonthCalendar> denetimi. Aşağıdaki kod örneği, bir seçim aralığını ayarlamak gösterilmektedir.  
  
### <a name="to-select-a-range-of-dates"></a>Tarih aralığı seçin  
  
1.  Oluşturma <xref:System.DateTime> bir aralıktaki ilk ve son tarihleri temsil eden nesneleri.  
  
    ```vb  
    Dim projectStart As Date = New DateTime(2001, 2, 13)  
    Dim projectEnd As Date = New DateTime(2001, 2, 28)  
    ```  
  
    ```csharp  
    DateTime projectStart = new DateTime(2001, 2, 13);  
    DateTime projectEnd = new DateTime(2001, 2, 28);  
    ```  
  
    ```cpp  
    DateTime projectStart = DateTime(2001, 2, 13);  
    DateTime projectEnd = DateTime(2001, 2, 28);  
    ```  
  
2.  Ayarlama <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> özelliği.  
  
    ```vb  
    MonthCalendar1.SelectionRange = New SelectionRange(projectStart, projectEnd)  
    ```  
  
    ```csharp  
    monthCalendar1.SelectionRange = new SelectionRange(projectStart, projectEnd);  
    ```  
  
    ```cpp  
    monthCalendar1->SelectionRange = gcnew  
       SelectionRange(projectStart, projectEnd);  
    ```  
  
     – veya –  
  
     Ayarlama <xref:System.Windows.Forms.MonthCalendar.SelectionStart%2A> ve <xref:System.Windows.Forms.MonthCalendar.SelectionEnd%2A> özellikleri.  
  
    ```vb  
    MonthCalendar1.SelectionStart = projectStart  
    MonthCalendar1.SelectionEnd = projectEnd  
    ```  
  
    ```csharp  
    monthCalendar1.SelectionStart = projectStart;  
    monthCalendar1.SelectionEnd = projectEnd;  
    ```  
  
    ```cpp  
    monthCalendar1->SelectionStart = projectStart;  
    monthCalendar1->SelectionEnd = projectEnd;  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [MonthCalendar Denetimi](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)
- [Nasıl yapılır: Windows Forms MonthCalendar denetiminin görünüşünü değiştirme](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)
- [Nasıl yapılır: Windows ile belirli günleri kalın olarak görüntüleme Forms MonthCalendar denetimi](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md)
- [Nasıl yapılır: Windows Forms MonthCalendar denetiminde birden fazla ay görüntüleme](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)
